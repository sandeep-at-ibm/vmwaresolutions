---

copyright:

  years:  2019

lastupdated: "2019-10-18"

subcollection: vmware-solutions


---

# VMware Hybrid Cloud migrations
{: #hcxclient-migrations}

After the HCX Service Mesh and Network Extensions are provisioned and extended, the next step is the migration of VMs.

There are three types of migrations:
  - vMotion
  - Bulk Migration
  - Cold Migration

## Operation
{: #hcxclient-migrations-operation}

Use the HCX web UI snap-in portal or the vSphere web client contextual extension menus to initiate a cross cloud vMotion. In either case, the same migration wizard comes up. For the contextual menus, only a single VM is selected for migration operations. For the portal, multiple VMs can be selected.

Reverse migrating VMs is only possible from the web UI portal that uses the **Reverse migration** check box in the HCX Migration wizard.

## vMotion
{: #hcxclient-migrations-vmotion}

The vMotion capability within HCX extends the vSphere vMotion capability to work across differing versions of vSphere, separate SSO domains, and various types of network connectivity across the internet. HCX assumes that the network used to connect across is not secure and it always moves traffic through encrypted tunnels regardless of the type of connectivity.

### Concepts and best practices for vMotion
{: #hcxclient-migrations-best-practices-vmotion}

HCX is essentially a vMotion two-way proxy. Each instance of HCX emulates a single ESXi host within the vSphere data center, outside any clusters that is itself a “front” for the cloud gateway fleet component (CGW). A proxy host appears for each HCX site that is linked to the currently viewed site. When a vMotion is initiated to a remote host, the local ESXi host will migrate that VM to the local proxy ESXi host that fronts the CGW that also is maintaining an encrypted tunnel with the CGW on the remote side.

A vMotion migration is initiated from the remote ESXi proxy host to the destination vSphere physical ESXi host, while it receives data from the source CGW across the tunnel. When vMotion is employed, unlike the bulk migration option, only a single VM migration operation runs at a time. Because of this, for many VMs to be migrated, it's recommended to use vMotion only when downtime is not an option or if there is a risk in rebooting the VM. However, like standard vMotion, the VM can be live during the process.

It has been observed that a single vMotion will top out at around 1.7 Gbps on the LAN and 300 - 400 Mbps on the WAN through the WAN Optimizer. This does not mean that 1.7 Gbps on the LAN equals to 400 Mbps on the WAN through the WAN Optimizer, but rather that these maximums were observed on specific environments. Such an environment consisted of 10 GB LAN vMotion Network and 1 GB internet uplink, which is shared with production web traffic.

Use vMotion when:
- The VM is troublesome to shut down, start, or uptime can be long and would introduce risk by shutting it down.
- For any cluster type application that requires disk UUIDs, such as Oracle RAC clusters. Note that vMotion does not changed the disk UUIDs on the destination.
- You want to move a single VM as quickly as possible.
- Scheduled migration is not required.

## Bulk migration
{: #hcxclient-migrations-bulk-mig}

### Concepts and best practices for bulk migration
{: #hcxclient-migrations-best-practices-bulk-mig}

The bulk migration capability of HCX uses vSphere replication to migrate disk data while re-creating the VM on the destination vSphere HCX instance. A migration of a VM incurs the following workflow:
- Creation of a new VM on the destination side and its corresponding virtual disks.
- Replication of VM data to the new VM. Replication starts as soon as the wizard is completed regardless of switch over scheduling.
- Power down of the original VM.
- During the power off period, final replication of any data changes occurs.
- Powering on the new VM on the destination side.
- Rename and move of the original VM to the cloud folder to which it was moved.

The following are advantages of bulk migration over vMotion:
- Migration of multiple VMs concurrently.
- More consistent bandwidth use. vMotion can generate fluctuations in bandwidth use that would be visible as peaks and valleys within network monitoring tools or the WAN Opt UI.
- Use bulk migration to obtain higher overall use of a network bandwidth capability than a single vMotion is capable of.
- Schedule bulk migration to switch to the newly migrated VMs during a scheduled outage window.
- Allow migration of VMs that are currently using virtual CPU features, which differ from the cloud side. vMotion migration might fail in these cases.

The following are disadvantages of bulk migration over vMotion:
- Individual VMs migrate much more slowly than with vMotion.
- The VM incurs downtime briefly as the new clone VM is brought up on the destination side.
- VMs that depend on disk ordering and disk UUIDs (Oracle RAC) can have issues and have disks that show up differently as the UUIDs are changed, which might change the OS paths to the virtual disk devices.

## Migration type best practices
{: #hcxclient-migrations-mig-type-best-practices}

### Shared disk clusters
{: #hcxclient-migrations-shared-disk-clusters}

Oracle RAC, MS Exchange, and MS-SQL clusters are examples of applications where two or more VMs participate in a cluster that requires shared disk across all VMs or cluster nodes. The VMware multi-writer flag needs to be enabled on all of the VM nodes for disks that are part of the application cluster (non-OS virtual disks). VMs with the multi-writer flag enabled for any virtual disk are not supported.

Migrating a multi-writer virtual disk enabled cluster:
- Uses vMotion as the original VM disk and UUID mappings are maintained.
- The cluster remains up in a degraded state (single node) during migration.
- The cluster incurs downtime before the start of the migration and after the migration is complete to reassemble the multi-writer configuration across cluster VMs.

Complete the following steps to migrate a multi-writer disk enabled cluster:
1. Power off the cluster and all nodes per the application best practice.
2. Take note of the disk order, if the application requires it, in each node VM for the multi-writer configured virtual disks.
3. For Oracle and any other application that uses the virtual disk UUID feature, login to a particular ESXi host and run the `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` command to get the UUID of each virtual disk file that requires the multi-writer flag set for
the cluster.
  This is necessary if best practice aligns disk orders with how the path displays in the operating system. vMotion can reorder the disks (disk1, disk2, disk3) but the UUIDs remain the same.
  When the migration completes, use the noted UUID to map the disk information, to re-create the disk naming order, and the SCSI ID, if necessary. The application should function either way. This is used where an Oracle instance has many virtual disks that are mapped for troubleshooting of the application.
4. Remove the virtual disks from all cluster VMs except the one deemed primary.
5. Remove the multi writer-flag from the primary cluster VM that should be the only one owning the cluster disks currently.
6. Power on the primary cluster, if required for minimal downtime.
7. Migrate all cluster nodes with vMotion. Migrate the primary cluster first. Migrate all other nodes after they are powered off.
8. When the primary disk owning node completes migration, power it off.
9. If required, remap the disk order with the proper disk UUID and scsi ID. Remapping is not required for the application to function.
10. Re-enable the multi-writer flag on the primary node.
11. Start the primary node and verify operation.
12. Map disk / enable multi-writer flag on all other cluster VMs and power them on.
13. Verify other cluster operation.

### General VMs
{: #hcxclient-migrations-general-vms}

After confidence is built around the function of HCX, bulk migration must be employed. Bulk migration is necessary for redundant applications. For example, web servers and where many 100s or 1000s of VMs are to be migrated.

### VMs that use direct attached NAS
{: #hcxclient-migrations-vms-direct-nas}

NFS is typically employed for use to share data across many servers, such as web server content. iSCSI can be employed across VM nodes that consist of an application cluster such as email or RDBMS and is typically more latency sensitive than NFS.

In either case, if latency can be kept low to the {{site.data.keyword.CloudDataCent_notm}} (< ~7 ms for iSCSI and whatever the application tolerates for NFS) and allowing that the application can operate with bandwidth of ~1 Gbps or less, then the NAS network can be stretched with HCX into an {{site.data.keyword.cloud_notm}} location. After this is done, the VMs can be migrated or vMotioned with HCX.

Post migration, iSCSI volumes can be mirrored with the OS to another local cloud storage solution and NFS data can be replicated to any cloud solution. The considerations are:
- Latency (iSCSI or application tolerance for NFS)
- Bandwidth (~1 Gbps per stretched network)
- Underlay link bandwidth

After the migration lifecycle, test Development or staging applications before attempting on production. QoS can be employed for the underlay tunnel traffic (UDP 500/4500) between the L2C HCX appliances that support latency sensitive stretched L2 networks.

## Network swing
{: #hcxclient-migrations-network-swing}

If the goal is data center evacuation into the {{site.data.keyword.cloud_notm}}, then the next to last step before HCX removal is the network swing. Network swing achieves a migration of the network subnet that houses the migrated VMs from the source data center to an NSX overlay network within the {{site.data.keyword.cloud_notm}}.

Swinging the network involves the following steps:
- Verify that the network is evacuated of all workloads and any non-VM networked devices are either moved to another network, functionally migrated to cloud, or deprecated.
- Verify any NSX topology or {{site.data.keyword.cloud_notm}} supporting network topology is completed to support the network swing. For example, dynamic routing protocols and firewalls.
- Run an HCX unstretch network workflow in the UI and select the appropriate routing NSX device to take control of the default gateway of the unstretched network.
- Run any external routing changes, which can include: insert changed routing for networks that were migrated, remove routes to source site from the migrated network, and ensure that routing to the migrated subnet across the WAN still works for applications that were not migrated.
- Application owner testing of migrated applications from all possible access points: internet, intranet, and VPN.

Let's say you want to network swing a particular application that has all VMs migrated to cloud. For example:
- You are using a vyatta on the private network side to insert routes into your MPLS cloud and to tunnel to the edge routing devices on the MPLS so you can avoid the {{site.data.keyword.cloud_notm}} IP space.
- You have your account set with an {{site.data.keyword.cloud_notm}} VRF.
- Some applications are behind a network load balanced virtual IP (vIP). Those vIPs are on your owned subnet that resides on a virtual F5 behind the vyatta.

While adding more specific routing into the MPLS for networks that are swung over to {{site.data.keyword.cloud_notm}} through HCX works fine for other networks, it does not work for the individual vIPs because a /32 route is being added.

Solution: It is common for WAN providers to filter out /32 routes that are added. Work with the WAN vendor to allow.

The following are considerations and implications:
- Applications that share subnet, vLAN, and VXLAN need to move together.
- Applications behind a load balancer that uses an internal routable IP can require routing changes if they cannot be moved together or it is not desirable to do so. For example, if there is too much perceived risk by involving too many applications in one swing.
- VMware admins, network admins (including customers and WAN vendors), and application owners need to be involved, even if there's no planned impact on a particular system or network equipment.

**Next topic:** [Monitoring parameters and components](/docs/services/vmwaresolutions?topic=vmware-solutions-hcxclient-monitoring)

## Related links
{: #hcxclient-migrations-related}

* [Glossary of HCX components and terms](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparing the installation environment](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX Client deployment](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX on-premises Service Mesh](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [HCX troubleshooting](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
