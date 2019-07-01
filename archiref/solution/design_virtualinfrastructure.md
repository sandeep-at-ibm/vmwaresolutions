---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Virtual infrastructure design
{: #design_virtualinfrastructure}

The virtual infrastructure layer includes the VMware software components that virtualize the compute, storage, and network resources provided in the physical infrastructure layer: VMware vSphere ESXi, VMware NSX-V or NSX-T, and optionally VMware vSAN.

![Virtual infrastructure](../../images/vcsv4radiagrams-ra-virtinfra.svg "Virtual infrastructure"){: caption="Figure 1. Virtual infrastructure" caption-side="bottom"}

## VMware vSphere design
{: #design_virtualinfrastructure-vsphere-design}

The vSphere ESXi configuration consists of the following aspects:
* Boot configuration
* Time synchronization
* Host access
* User access
* DNS configuration

The following table outlines the specifications for each aspect. After the configuration and installation of ESXi, the host is added to a VMware vCenter Server and is managed from there.

With this design, you can access the virtual hosts through Direct Console User Interface (DCUI) and vSphere Web Client. Secure Shell (SSH) and ESXi Shell are disabled after provisioning as a best practice.

By default, the only users who can log in directly are the _root_ and _ibmvmadmin_ users for the physical machine of the host. The administrator can add users from the Microsoft Active Directory (MSAD) domain to enable user access to the host. All hosts in the vCenter Server solution design are configured to synchronize with a central NTP server.

Table 1. vSphere ESXi configuration

| Attribute              | Configuration parameter |
|:---------------------- |:----------------------- |
| ESXi boot location     | Uses local disks that are configured in RAID-1 |
| Time synchronization   | Uses {{site.data.keyword.cloud}} NTP server |
| Host access            | Supports DCUI. SSH and ESXi Shell are supported but not enabled by default |
| User access            | Local authentication and MSAD |
| Domain name resolution | Uses DNS as described in [Common services design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice). |
| EVC Mode | Skylake (only for “greenfield” vSphere 6.7 deployments) |

The vSphere cluster houses the virtual machines (VMs) that manage the vCenter Server instance as well as compute resources for user workloads.

* When a vCenter Server instance uses vSAN, the minimum number of ESXi hosts at initial deployment is 4.
* When a vCenter Server instance uses shared file–level or block-level storage, the minimum number of ESXi hosts at initial deployment is 3.

You can scale up to a maximum of 59 ESXi hosts during or post initial deployment.

To support more user workloads, you can scale the environment by:  
* Deploying more compute hosts in existing clusters
* Deploying more clusters that are managed by the same vCenter Server Appliance
* Deploying new vCenter Server instances with their own vCenter Server Appliance

For more information about clusters, see [{{site.data.keyword.cloud_notm}} running VMware clusters solution architecture](https://www.ibm.com/cloud/garage/files/IBM-Cloud-for-VMware-Solutions-Multicluster-Architecture.pdf).

## VMware vSAN design
{: #design_virtualinfrastructure-vsan-design}

In this design, VMware vSAN storage is employed in vCenter Server instances to provide shared storage for the vSphere hosts.

As shown in the following figure, vSAN aggregates the local storage across multiple ESXi hosts within a vSphere cluster and manages the aggregated storage as a single VM datastore. Within this design, the compute nodes contain local disk drives for the ESXi Operating System (OS) and the vSAN datastore. Regardless of which cluster a node belongs to, two OS drives are included in each node to house the ESXi installation.

![vSAN concept](../../images/vcsv4radiagrams-ra-vsan.svg "vSAN aggregates the local storage across multiple ESXi hosts within a vSphere cluster and manages the aggregated storage as a single VM datastore"){: caption="Figure 2. vSAN concept" caption-side="bottom"}

vSAN employs the following components:
* Two-disk group vSAN design; each disk group with two or more disks. One SSD or NVMe drive of the smallest size in the group serves as the cache tier and the remaining SSDs serve as the capacity tier.
* The onboard RAID controller is configured in a RAID-0 array for each drive except for the two OS drives.
* A single vSAN datastore is created from all storage.

The available vSAN features depend on the license edition that you select when you order the instance. For more information, see [VMware vSAN edition comparison](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix#vmware-vsan-edition-comparison).

### Virtual network setup for vSAN
{: #design_virtualinfrastructure-net-setup}

For this design, the vSAN traffic traverses between ESXi hosts on a dedicated private VLAN. The two network adapters attached to the private network switch are configured within vSphere as a vSphere Distributed Switch (vDS) with both network adapters as uplinks. A dedicated vSAN kernel port group that is configured for the vSAN VLAN resides within the vDS. Jumbo frames (MTU 9000) are enabled for the private vDS.

vSAN does not load balance traffic across uplinks. As a result, one adapter is active while the other is in standby to support high availability (HA). The network failover policy for vSAN is configured as **Explicit Failover** between physical network ports.

For more information about physical NIC connections, see [Physical host NIC connections](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_physicalinfrastructure#design_physicalinfrastructure-host-connect).

### vSAN policy design
{: #design_virtualinfrastructure-storage-policy}

When vSAN is enabled and configured, storage policies are configured to define the VM storage characteristics. Storage characteristics specify different levels of service for different VMs.

The default storage policy in this design tolerates a single failure. The default policy is configured with erasure coding, with **Failure tolerance method** set to **RAID-5/6 (Erasure Coding) - Capacity** and **Primary level of failures** set to 1. The RAID 5 configuration requires a minimum of four hosts.

Alternatively, you can choose the RAID 6 configuration with **Failure tolerance method** set to **RAID-5/6 (Erasure Coding) - Capacity** and **Primary level of failures** set to 2. The RAID 6 configuration requires a minimum of six hosts. **Duplication** and **compression** are also enabled in the default storage policy.

An instance uses the default policy unless otherwise specified from the vSphere console. When a custom policy is configured, vSAN will guarantee it when possible. However, if the policy can't be guaranteed, it's not possible to provision a VM that uses the policy unless it is enabled to force provisioning.

Storage policies must be reapplied after addition of new ESXi hosts or patching of the ESXi hosts.

### vSAN settings
{: #design_virtualinfrastructure-vsan-sett}

vSAN settings are configured based on best practices for deploying VMware solutions within {{site.data.keyword.cloud_notm}}. The vSAN settings include SIOC settings, explicit failover settings port group, and disk cache settings.
* SSD cache policy settings: No **Read Ahead**, **Write Through**, **Direct** (NRWTD)
* Network I/O control settings
   * Management - 20 shares
   * Virtual machine - 30 shares
   * vMotion - 50 shares
   * vSAN - 100 shares
* vSAN kernel ports: **Explicit Failover**

## NFS attached storage
{: #design_virtualinfrastructure-nfs-storage}

When using NFS network-attached storage, this architecture prescribes the use of NFS v3 rather than NFS v4.1, because NFS server LIF migrations might cause excessive latency when using NFS v4.1. Each vSphere host is connected to the NFS storage by using its host name.

One 2-TB NFS data store is attached to a cluster for use by management components with a performance tier of 4 IOPS/GB. More data stores can be attached to a cluster for workload use, at various sizes and performance tiers.

Additionally, this architecture requires that all hosts have a subnet route created for the subnet where the NFS storage resides. The purpose of this subnet route is to direct all NFS traffic to use the port group, subnet, and VLAN designated for NFS traffic by this design. If multiple NFS data stores are attached, multiple routes might be required to be configured since those data stores might be located in different remote subnets.

Management virtual machines can be located on an NFS data store. This creates a bootstrapping problem since some of the management machines might be responsible for DNS services, which are used to resolve the NFS host name. Therefore, this architecture specifies that at least one of the IP addresses for the management data store to be hardcoded in `/etc/hosts` on each of the hosts.

## VMware NSX-V design
{: #design_virtualinfrastructure-nsx-design}

Network virtualization provides a network overlay that exists within the virtual layer. Network virtualization provides the architecture with features such as rapid provisioning, deployment, reconfiguration, and destruction of on-demand virtual networks. This design uses the vDS and VMware NSX for vSphere to implement virtual networking.

In this design, the NSX Manager is deployed in the initial cluster. The NSX Manager is assigned a VLAN-backed IP address from the private portable address block, which is designated for management components and configured with the DNS and NTP servers that are presented in [Common services design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice).

The following figure shows the placement of the NSX Manager in relation to other components in the architecture.

![NSX Manager network overview](../../images/vcsv4radiagrams-ra-vcs-nsx-overview.svg "NSX Manager in relation to the other components in the architecture"){: caption="Figure 3. NSX Manager network overview" caption-side="bottom"}

After initial deployment, the {{site.data.keyword.cloud_notm}} automation deploys three NSX controllers within the initial cluster. Each of the controllers is assigned a VLAN-backed IP address from the **Private A** portable subnet that is designated for management components. Additionally, the design creates VM-VM anti-affinity rules to separate the controllers among the hosts in the cluster. The initial cluster must contain a minimum of three nodes to ensure high availability for the controllers.

In addition to the controllers, the {{site.data.keyword.cloud_notm}} automation prepares the deployed vSphere hosts with NSX VIBS to enable the use of a virtualized network through VXLAN Tunnel Endpoints (VTEPs). The VTEPs are assigned a VLAN-backed IP address from the **Private A** portable IP address range that is specified for VTEPs as listed in [VLANs](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_physicalinfrastructure#design_physicalinfrastructure-vlans). The VXLAN traffic resides on the untagged VLAN and is assigned to the private vDS.

Then, a segment ID pool is assigned and the hosts in the cluster are added to the transport zone. Only unicast is used in the transport zone because Internet Group Management Protocol (IGMP) snooping is not configured within the {{site.data.keyword.cloud_notm}}. Two VTEP kernel ports are configured per host on the same VTEP dedicated subnet per VMW best practice.

After that, if the instance has public network interfaces, two NSX Edge Services Gateway pairs are deployed. One gateway pair is used for outbound traffic from automation components that reside in the private network. A second gateway that is known as the customer-managed edge, is deployed and configured with an uplink to the public network and an interface that is assigned to the private network. For more information about the NSX Edge Services Gateways that are deployed as part of the solution, see [NSX Edge Services Gateway solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-nsx_overview#nsx_overview).

Cloud administrators can configure any required NSX components, such as Distributed Logical Router (DLR), logical switches, and firewalls. The available NSX features depend on the NSX license edition that you choose when you order the instance. For more information, see [VMware NSX edition comparison](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix#vmware-nsx-edition-comparison).

The NSX Manager is installed with the specifications that are listed in the following table.

Table 3. NSX Manager requirements

| Attribute       | Specification |
|:--------------- |:------------- |
| NSX Manager     | Virtual appliance |
| Number of vCPUs | 4 |
| Memory          | 16 GB |
| Disk            | 60 GB on the management NFS share |
| Disk type       | Thin-provisioned |
| Network         | **Private A** portable designated for management components |

### Distributed switch design
{: #design_virtualinfrastructure-distr-switch}

The design uses a minimum number of vDS Switches. The hosts in the cluster are connected to the public and private networks. The hosts are configured with two distributed virtual switches. The use of two switches follows the practice of {{site.data.keyword.cloud_notm}} network that separates the public and private networks. The following diagram shows the vDS design.

![Distributed switch design](../../images/vcsv4radiagrams-distributed-switch-design.svg "Distributed switch design"){: caption="Figure 4. Distributed switch design" caption-side="bottom"}

As shown in the previous figure, one vDS is configured for public network connectivity (SDDC-Dswitch-Public) and the other vDS is configured for private network connectivity (SDDC-Dswitch-Private). Separating different types of traffic is required to reduce contention and latency and increase security.

VLANs are used to segment physical network functions. This design uses three VLANs: two for private network traffic and one for public network traffic. The following table shows the traffic separation.

Table 4. VLAN mapping to traffic types

| VLAN  | Designation | Traffic type |
|:----- |:----------- |:------------ |
| VLAN 1 | Private A   | ESXi management, management, VXLAN (VTEP) |
| VLAN 2 | Private B   | vSAN, NFS, and vMotion|
| VLAN 3 | Public      | Available for internet access |

Traffic from workloads will travel on VXLAN­-backed logical switches.

The vSphere cluster uses two vSphere Distributed Switches that are configured as in the following tables. 

Table 5. Converged cluster distributed switches

| vSphere Distributed<br>Switch Name | Function | Network<br>I/O Control | Load Balancing<br>Mode | Physical NIC<br>Ports | MTU |
|:------------- |:------------- |:------------- |:------------- |:------------- |:------------- |
| SDDC-Dswitch-Private | ESXi management, vSAN, vSphere vMotion, VXLAN tunnel endpoint, NFS (VTEP) | Enabled | Route based on explicit failover (vSAN, vMotion) originating virtual port (all else) | 2 | 9,000<br>(Jumbo frames) |
| SDDC-Dswitch-Public | External management traffic (north-south) | Enabled | Route based on originating virtual port | 2 | 1,500<br>(default) |

The names, number, and ordering of the host NICs might vary depending on the {{site.data.keyword.CloudDataCent_notm}} and your host hardware selection.
{:note}

Table 6. Converged cluster distributed switch port group configuration settings

| Parameter          | Setting       |
|:------------------ |:------------- |
| Load balancing     | Route based on the originating virtual port \* |
| Failover detection | Link status only |
| Notify switches    | Enabled |
| Failback           | No |
| Failover order     | Active uplinks: Uplink1, Uplink2 \* |

\* The vSAN port group uses explicit failover with active or standby because it does not support load balancing of vSAN storage traffic.
{:note}

Table 7. Converged cluster virtual switch port groups and VLANs, Distributed switch **SDDC-Dswitch-Private**

Port Group|Teaming|Uplinks|VLAN ID
---|---|---|--
SDDC-DPortGroup-Mgmt|Originating virtual port|Active: 0, 1|VLAN 1
SDDC-DPortGroup-vMotion|Originating virtual port|Active: 0, 1|VLAN 2
SDDC-DPortGroup-VSAN|Explicit failover|Active: 0, Standby: 1|VLAN 2
SDDC-DPortGroup-NFS|Originating virtual port|Active: 0, 1|VLAN 2
NSX generated|Originating virtual port|Active: 0, 1|VLAN 1
SDDC-DPortGroup-External|Originating virtual port|Active: 0, 1|VLAN 3

Table 8. Converged cluster VMkernel adapters, Distributed switch **SDDC-Dswitch-Private**

Purpose|Connected port group|Enabled services|MTU
--|---|---|---|--
Management|SDDC-DPortGroup-Mgmt|Management Traffic|1500 (default)
vMotion|SDDC-DPortGroup-vMotion|vMotion Traffic|9000
VTEP|NSX generated|-|9000
vSAN|SDDC-DPortGroup-VSAN|vSAN|9000
NAS|SDDC-DPortGroup-NFS|NAS|9000

### NSX configuration
{: #design_virtualinfrastructure-nsx-config}

This design specifies the configuration of NSX components but does not apply any network overlay component configuration. You can design the network overlay based on your needs.

The following aspects are preconfigured:
* Management servers and controllers are installed and integrated into the vCenter web UI
* ESXi agents are installed and VTEP IP addresses are configured per ESXi host
* VTEP configuration, controller configuration, and VXLAN configuration (transport zone)
* NSX Edge Services Gateway appliances for use by management components
* NSX Edge Services Gateway appliances for customer use
* NSX VXLAN work customer workloads attached to a distributed local router (DLR) with a transit VXLAN between the DLR and the customer ESG.
* RFC 1918 address space for the VXLANs and IBM Cloud private and public portable IP space for use as egress network on the customer ESG.

The following aspects are not configured:
* Micro segmentation
* Linked NSX Management to other VMware instances

![Deployed Example Customer NSX topology](../../images/vcsv4radiagrams-ra-vcs-nsx-topology-customer-example.svg "Deployed Example Customer NSX topology"){: caption="Figure 5. Deployed example customer NSX topology" caption-side="bottom"}

## Public network connectivity

There are various reasons that you may need public network connectivity for your instance. This can include access to public update services or other public services for your workload such as geolocation databases or weather data. Your virtualization management and add-on services might also require or benefit from public connectivity. For example, vCenter can update its HCL database and obtain [VMware Update Manager (VUM)](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro) updates over the public network. Zerto, Veeam, VMware HCX, F5 BIG-IP, and FortiGate-VM all use public network connectivity for some part of their product licensing, activation, or usage reporting. On top of this, you might use tunnels over the public network for connectivity to your on-premises data center for replication purposes.

Typically these communications are selectively routed and NATed to the public network through the management or customer edge services gateway (ESG). However, you might have more security requirements, or might prefer to use a proxy to simplify the path of communication. Additionally, if you deployed your instance with public interfaces disabled, you will not be able to use ESGs to route to the public network.

This architecture allows for the following options for routing or proxying your traffic to the public network:

Method|Description|Limitations
--|--|--
Virtualized gateway|Deploy a virtualized gateway (for example, NSX ESG, F5 BIG-IP, FortiGate-VM, or a virtual appliance of your choosing) crossing the private and public network. Configure routing on the source system (for example, vCenter, Zerto, your workload) to direct only public network traffic to the gateway, and configure the gateway according to your needs.|Applicable only to instances with public interfaces enabled. This configuration allows for both outbound and inbound traffic patterns.
Virtualized gateway with proxy|Deploy a virtualized gateway as above. Behind this gateway, [deploy a proxy server](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config#vum-init-config), and configure your services and applications to connect to the public network through this proxy.|Applicable only to instances with public interfaces enabled. Outbound traffic patterns can use the proxy but inbound traffic patterns must be managed at the gateway.
Hardware gateway|Deploy a [hardware gateway appliance](https://cloud.ibm.com/catalog/infrastructure/gateway-appliance) to your management VLAN. Configure the gateway to NAT outbound to the public network according to your needs.|Applicable to all instances, with or without public interfaces enabled. This configuration allows for both outbound and inbound traffic patterns.
Hardware gateway with proxy|Deploy a gateway appliance as above. Behind this gateway, [deploy a proxy server](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config#vum-init-config), and configure your services and applications to connect to the public network through this proxy.|Applicable to all instances, with or without public interfaces enabled. Outbound traffic patterns can use the proxy but inbound traffic patterns must be managed by the gateway.
Load balancer|IBM Cloud offers several [load balancer services](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group) that you can use to provide inbound network access to your applications.|Applicable to all instances, but limited to inbound traffic patterns.

## Related links
{: #design_virtualinfrastructure-related}

* [{{site.data.keyword.cloud_notm}} running VMware clusters solution architecture](https://www.ibm.com/cloud/garage/files/IBM-Cloud-for-VMware-Solutions-Multicluster-Architecture.pdf)
* [NSX Edge Services Gateway solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-nsx_overview#nsx_overview)
