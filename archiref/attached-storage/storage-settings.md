---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-17"

---

# Storage settings

This design supports the attachment of shared storage via NFS v3 and NFS v4.1 (NFS v4 is not supported). After you order VMware vCenter Server on {{site.data.keyword.cloud}}, you determine which NFS version to use for the environment.

While NFS v4.1 introduces better performance and availability through load balancing and multipathing, it does restrict the utilization of vSphere features including Storage DRS, Storage I/O Control, and use of Site Recovery Manager.

The following table lists the NFS protocols and support for vSphere features when using vSphere 6.0.

Table 1. NFS protocols and vSphere features

| vSphere Feature | NFS v3 | NFS v4.1 |
|:--------------- |:------ |:-------- |
| vMotion and Storage vMotion | Yes | Yes |
| High Availability (HA) | Yes | Yes |
| Fault Tolerance (FT) | Yes | Yes |
| Distributed Resource Scheduler (DRS) | Yes | Yes |
| Host Profiles | Yes | Yes |
| Storage DRS | Yes | No |
| Storage I/O Control (SIOC) | Yes | No |
| Site Recovery Manager | Yes | No |
| Virtual Volumes | Yes | No |

**Note**: All of the attached storage for this design is limited to the {{site.data.keyword.cloud_notm}} storage available in the same {{site.data.keyword.CloudDataCent_notm}} as the vCenter Server solution. Additionally, the NFS v3 and 4.1 datastores are mounted by using the same NFS version on all hosts and all virtual disks that are stored to the datastore are thin-provisioned by default.

## Using NFS v3 for attached storage

When NFS v3 is chosen as the preferred method to attach the NFS share, the architecture is such that it uses a single IP address from {{site.data.keyword.cloud_notm}} storage to connect to the share. In addition, the NFS share is attached to all hosts in the vCenter Server cluster and placed into a datastore cluster with storage DRS enabled.

### vSphere Storage Distributed Resource Scheduler (Storage DRS)

Storage DRS allows you to manage the aggregated resources of a datastore cluster. When Storage DRS is enabled, it provides recommendations for virtual machine (VM) disk placement and migration to balance space and I/O resources across the datastores in the datastore cluster.

The following features are available when storage DRS is turned on:
* Space load balancing among datastores within a datastore cluster
* I/O load balancing among datastores within a datastore cluster
* Initial place for virtual disks based on space and I/O workload.

In this design, Storage DRS is enabled with the automation level set to “Fully Automated”. As a result, files are not migrated automatically to optimize resource usage on the data cluster. Note that all other Storage DRS options are set to “Use cluster settings” since the cluster is fully automated.

### Storage DRS runtime settings for NFS v3

The aggressiveness of Storage DRS is determined by specifying thresholds for space that is used and I/O latency. Storage DRS collects resource usage information for the datastores in a datastore cluster. vCenter Server uses this information to generate recommendations for placement of virtual disks on datastores.

When low aggressiveness level is set for a datastore cluster, Storage DRS recommends Storage vMotion migrations only when necessary, for example, if I/O load, space utilization, or their imbalance is high. When high aggressiveness level is set for a datastore cluster, Storage DRS recommends migrations whenever the datastore cluster can benefit from space or I/O load balancing.

The following threshold categories are available in the datastore cluster:

* Space Utilization: Storage DRS generates recommendations or performs migrations when the percentage of space utilization on the datastore is greater than the threshold you set in the vSphere Web Client.
* I/O Latency: Storage DRS generates recommendations or performs migrations when the 90th percentile I/O latency measured over a day for the datastore is greater than the threshold.

In this design, the Storage DRS Runtime Settings are enabled and thresholds are kept to their respective default values. It is highly recommended to change these values based on the workload I/O requirements and latency sensitivity.

The following table shows the settings in the VMware vSphere Web Client.

Table 2. Storage DRS runtime settings

| Setting       | Value  |
|:--------------- |:------ |
| Enable I/O metric for SDRS recommendations | Selected |
| Utilized space | Selected, set to 80% |
| I/O latency threshold | 15 ms |

For more information about configuring these settings in the vSphere Web Client, see [Set Storage DRS Runtime Rules in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

### Storage I/O Control for NFS v3

When SIOC is enabled in the environment, it changes the device queue length for the single VM. The change to the device queue length reduces the storage array queue for all VMs to an equal share and throttle of the storage queue. SIOC engages only if resources are constrained and the storage I/O latency is above a defined threshold.

In order for SIOC to determine when a storage device is congested or constrained, it requires a defined threshold. The congestion threshold latency is different for different storage types. This design recommends and implements a threshold latency of 10 milliseconds.

You can also limit individual virtual disks for individual VMs or grant them different shares with SIOC. The limiting of disks and granting different shares allows you to match and align the environment to the workload with the acquired file storage volume IOPS number. The limit is set by IOPS and it is possible to set a different weight or "Shares."

Virtual disks shares set to "High" (2,000 shares) receive twice as much as I/O as a disk set to "Normal" (1,000 shares) and four times as much as one set to "Low" (500 shares). Normal is the default value for all the VMs, so you need to adjust the values above or below "Normal" for the VMs that require it.

### Additional storage for NFS v3

When the need arises to add additional storage to the environment due to insufficient space or high latency, you can order another NFS share from the console. After the share is ordered, the automation attaches the export to the vSphere ESXi hosts in the cluster and places it into the previously mentioned storage cluster. Placing the new NFS share in the storage cluster effectively and seamlessly scales out the storage that is associated with the environment without burdening you with storage-level migrations.

## Using NFV v4.1 for attached storage

When NFS v4.1 is chosen as the preferred method to attach the NFS share, the architecture is such that it uses multiple IP addresses from {{site.data.keyword.cloud_notm}} storage to connect to the share. While the share is attached to all hosts in the vCenter Server cluster, it is not placed into a datastore cluster due to the vSphere limitation of using Storage DRS with NFS v4.1.

**Note**: NFS 4.1 with vSphere 6.0 does not support hardware acceleration. This limitation does not allow the creation of thick virtual disks on NFS v4.1 datastores.

### Additional Storage for NFV v4.1

When the need arises to add additional storage to the environment due to insufficient space or high latency, you can order another NFS share from the console. After the share is ordered, the automation attaches the export to the vSphere ESXi hosts in the cluster. You then must migrate VMs and load balance the datastores so that space is properly used and latency requirements are met.

## Advanced configuration parameters

Regardless of whether you choose NFS v3 or NFS v4.1, this design adds advanced configuration parameters that are recommended by {{site.data.keyword.cloud_notm}}. As a result, the following parameters are set on each vSphere ESXi host that is attached to the {{site.data.keyword.cloud_notm}} NFS share.

Table 3. NFS advanced configuration parameters

| Parameter       | Value  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MazQueueDepth | 64 |

### Related links

* [Solution overview](../solution/solution_overview.html)
