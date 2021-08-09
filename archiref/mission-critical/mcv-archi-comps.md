---

copyright:

  years:  2019, 2021

lastupdated: "2021-07-14"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# VMware multizone components
{: #mcv-archi-comp}

## VMware vSphere configuration
{: #mcv-archi-comp-vsphere}

The following information describes the configuration design for enabling VMware® multizone instances.

1. High Availability and host monitoring is enabled.
  * Host failure response - Restart VMs
  * Host isolation - Power off and restart VMs
  * Default VM Restart Priority - Highest
2. Distributed Resource Scheduler - Fully automated.
3. Resource Cluster (vSAN Stretched Cluster) Admission Control
  * Reserved CPU capacity - 50%
  * Reserved Memory capacity - 50%
  * Performance degradation VMs tolerate - 100%
4. Resource Cluster (vSAN Stretched Cluster) Host Groups and VM Groups
  * Create a Host Group for Site A and a host group for Site B. Add the correct hosts into each group.
  * Create a VM Group for Site A and a VM Group for Site B. Add the correct VMs into each group.
  * With a ‘Should’ Rule, pin a VM Group to a Host Group to avoid VMs moving between sites under normal circumstances.
5. Isolation address for vSAN Stretched Cluster
  * das.usedefaultisolationaddress – set to false
  * das.isolationaddress0 - IP address on vSAN network on Site A.
    Use another IP on the same subnet as the vSAN VMK; preferably the vSAN VMK default gateway in Site A.
  * das.isolationaddress1 - IP address on vSAN network on Site B.
    Use another IP on the same subnet as the vSAN VMK; preferably the vSAN VMK default gateway in Site B.
   * das.isolationaddress[2–5] – HSRP IP addresses on vSAN network on Site A and Site B
6. Network I/O Control
  * Management traffic - 20 shares
  * Virtual machine traffic - 30 shares
  * vMotion traffic - 50 shares
  * vSAN traffic - 100 shares
  * All other unused services must be set to *Low* or *0 shares*
7. Performance Profile for the system hardware is set to Max Performance.

## vCenter High Availability
{: #mcv-archi-comp-HA}

The VMware multizone instance is configured with vCenter High Availability (HA) enabled during provisioning. Automated failover is managed and performed by vCenter.

Investigation is underway for automation of the reassignment of the vCenter IP address in DNS. Otherwise, you must manually reassign the IP address upon vCenter failover or contact IBM Global Technology Services (GTS) for assistance.

### Network design
{: #mcv-archi-comp-ha-network}

New private subnets are provisioned for the VCHA network traffic when you provision the instance. This range is a /29 (8 IP address range) on each portable private VLAN provisioned for the hosts.

A new Distributed Virtual Switch (DVS) is created for the VCHA with a new port group for each site.

The following figure shows vmk1 added for VCHA network traffic with IP from the new subnet range.

![Network design](../../images/mcv-network-design.svg "Network design"){: caption="Figure 1. Network design" caption-side="bottom"}

vCenter Server access is done through a fully qualified domain name (FQDN) that has an A record to the IP address of the vCenter in Site A. During a Site A failure, that DNS A record is modified by using automation that runs in the witness site.

## vSAN stretched cluster
{: #mcv-archi-comp-vsan}

All of the hosts in the resource layer contribute all of their disks to the vSAN stretched cluster. The following flow describes the cluster configuration:

1. Hosts that are part of the Resource Cluster (vSAN Stretched Cluster) are part of a single Management Port Group.
2. For the Resource Cluster (vSAN Stretched Cluster), a separate Port Group per site exists for vSAN and vMotion.
  * vSAN Site A Port Group
  * vSAN Site B Port Group
  * vMotion Site A Port Group
  * vMotion Site B Port Group
3. For the Witness Appliance, two interfaces exist - one for management and one for vSAN traffic.
  * Management (vmk0)
  * vSAN/Witness (vmk1)
4. All ESXi hosts require static routes for the vSAN VMK to all other ESXi hosts vSAN VMK and the Witness.
  * `esxcli network IP route ipv4 add -n <target IP> -g <vSAN gateway>`
5. Witness appliance requires static routes to all ESXi hosts vSAN VMKs.
  * `esxcli network IP route ipv4 add -n <target IP> -g <vSAN gateway>`
6. Specify vMotion Gateway per site in vMotion TCP/IP Stack on an individual ESXi host basis.
  * Site A vMotion Gateway
  * Site B vMotion Gateway
7. Configure a vSAN Storage Policy with the following settings:
  * Primary Failures to Tolerate (PFTT) = 1
  * Secondary Failures to Tolerate (SFTT) = 1 (minimum)
  * Failure Tolerance Method (FTM) = RAID 5/6
  * FTT and RAID settings are set based on number of hosts ordered. You can change this setting.
8. When you configure a vSAN stretched cluster, specify the following settings to create two failure domains:
  * Hosts that are in Site A are part of the primary site
  * Hosts that are in Site B are part of the secondary site

### Known issue with the default storage policy
{: #mcv-archi-comp-storage}

For a vCenter Server instance with vSAN stretched cluster and a cluster size of only six hosts, the default storage policy is not usable. This problem occurs because the default vSAN storage policy is configured with the setting **Failures to tolerate 1 failure - RAID-5 (Erasure Coding)**, which cannot be achieved with the minimum vSAN stretched cluster size of six hosts.

During installation, a new storage policy that is named `IC4v Minimal vsan policy` is created. This storage policy can be used for deployments into the vSAN stretched cluster.

## VMware NSX
{: #mcv-archi-comp-nsx}

### NSX–T Management Edge
{: #mcv-archi-comp-nsx-nsxv}

The management edge is preconfigured to allow outbound access to the public internet.

### NSX Manager/Controller
{: #mcv-archi-comp-nsx-mgr-controller}

Three manager/controller appliances are deployed across the three availability zones and pinned to their respective clusters. These appliances are deployed in the following way: one in **Mgmt-A**, one in **Mgmt-B**, and one in the witness cluster.

If an availability zone failure or failover occurs, use vCenter Server to determine the IP address of an alternative NSX Manager/Controller and connect to it by using the credentials in the VMware Solutions console.
{:note}

### NSX Edge configuration
{: #mcv-archi-comp-nsx-config}

No additional NSX configuration is performed other than allowing outbound traffic for the management cluster. It is your responsibility to provide and manage any other needed NSX configurations.

## Support
{: #mcv-archi-comp-support}

As with vCenter Server instance orders, IBM Support provides provisioning support for stretched cluster orders.

It is your responsibility to perform patching and ongoing maintenance of the stretched cluster or to contact IBM GTS for assistance.

## Related links
{: #mcv-archi-comps-related}

* [VMware multizone introduction](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-overview)
* [VMware multizone architecture design](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-design)
* [VMware multizone BOM](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-bom)
