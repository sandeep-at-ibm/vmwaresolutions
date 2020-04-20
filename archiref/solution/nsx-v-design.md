---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-14"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware NSX-V design
{: #nsx-v-design}

Network virtualization provides a network overlay that exists within the virtual layer. Network virtualization provides the architecture with features such as rapid provisioning, deployment, reconfiguration, and destruction of on-demand virtual networks. This design uses the vDS and VMware NSX for vSphere to implement virtual networking.

In this design, the NSX Manager is deployed in the initial cluster. The NSX Manager is assigned a VLAN-backed IP address from the private portable address block, which is designated for management components and configured with the DNS and NTP servers that are presented in [Common services design](/docs/vmwaresolutions?topic=vmware-solutions-design_commonservice).

The following figure shows the placement of the NSX Manager in relation to other components in the architecture.

![NSX Manager network overview](../../images/vcsv4radiagrams-ra-vcs-nsx-overview.svg "NSX Manager in relation to the other components in the architecture"){: caption="Figure 1. NSX Manager network overview" caption-side="bottom"}

After initial deployment, the {{site.data.keyword.cloud_notm}} automation deploys three NSX controllers within the initial cluster. Each of the controllers is assigned a VLAN-backed IP address from the **Private A** portable subnet that is designated for management components. Additionally, the design creates VM-VM anti-affinity rules to separate the controllers among the hosts in the cluster. The initial cluster must contain a minimum of three nodes to ensure high availability for the controllers.

In addition to the controllers, the {{site.data.keyword.cloud_notm}} automation prepares the deployed vSphere hosts with NSX VIBS to enable the use of a virtualized network through VXLAN Tunnel Endpoints (VTEPs). The VTEPs are assigned a VLAN-backed IP address from the **Private A** portable IP address range that is specified for VTEPs as listed in [VLANs](/docs/vmwaresolutions?topic=vmware-solutions-design_physicalinfrastructure#design_physicalinfrastructure-vlans). The VXLAN traffic resides on the untagged VLAN and is assigned to the private vDS.

Then, a segment ID pool is assigned and the hosts in the cluster are added to the transport zone. Only unicast is used in the transport zone because Internet Group Management Protocol (IGMP) snooping is not configured within the {{site.data.keyword.cloud_notm}}. Two VTEP kernel ports are configured per host on the same VTEP dedicated subnet per VMWare best practice.

After that, if the instance has public network interfaces, two NSX Edge Services Gateway pairs are deployed. One gateway pair is used for outbound traffic from automation components that reside in the private network. A second gateway that is known as the customer-managed edge, is deployed and configured with an uplink to the public network and an interface that is assigned to the private network. For more information about the NSX Edge Services Gateways that are deployed as part of the solution, see [NSX Edge Services Gateway solution architecture](/docs/vmwaresolutions?topic=vmware-solutions-nsx_overview#nsx_overview).

Cloud administrators can configure any required NSX components, such as Distributed Logical Router (DLR), logical switches, and firewalls. The available NSX features depend on the NSX license edition that you choose when you order the instance. For more information, see [VMware NSX edition comparison](/docs/vmwaresolutions?topic=vmware-solutions-solution-appendix#solution-appendix-nsx-editions).

The NSX Manager is installed with the specifications that are listed in the following table.

| Attribute       | Specification |
|:--------------- |:------------- |
| NSX Manager     | Virtual appliance |
| Number of vCPUs | 4 |
| Memory          | 16 GB |
| Disk            | 60 GB on the management NFS share |
| Disk type       | Thin-provisioned |
| Network         | **Private A** portable designated for management components |
{: caption="Table 1. NSX Manager requirements" caption-side="bottom"}

## Distributed switch design
{: #nsx-v-design-distr-switch}

The design uses a minimum number of vDS Switches. The hosts in the cluster are connected to the public and private networks. The hosts are configured with two distributed virtual switches. The use of two switches follows the practice of {{site.data.keyword.cloud_notm}} network that separates the public and private networks. The following diagram shows the vDS design.

![Distributed switch design](../../images/vcsv4radiagrams-distributed-switch-design.svg "Distributed switch design"){: caption="Figure 2. Distributed switch design" caption-side="bottom"}

As shown in the previous figure, one vDS is configured for public network connectivity (SDDC-Dswitch-Public) and the other vDS is configured for private network connectivity (SDDC-Dswitch-Private). Separating different types of traffic is required to reduce contention and latency and increase security.

VLANs are used to segment physical network functions. This design uses three VLANs: two for private network traffic and one for public network traffic. The following table shows the traffic separation.

| VLAN  | Designation | Traffic type |
|:----- |:----------- |:------------ |
| VLAN 1 | Private A   | ESXi management, management, VXLAN (VTEP) |
| VLAN 2 | Private B   | vSAN, NFS, and vMotion|
| VLAN 3 | Public      | Available for internet access |
{: caption="Table 2. VLAN mapping to traffic types" caption-side="bottom"}

Traffic from workloads will travel on VXLAN­-backed logical switches.

The vSphere cluster uses two virtual Distributed Switches that are configured as in the following tables.

| vSphere Distributed<br>Switch Name | Function | Network<br>I/O Control | Load Balancing<br>Mode | Physical NIC<br>Ports | MTU |
|:------------- |:------------- |:------------- |:------------- |:------------- |:------------- |
| SDDC-Dswitch-Private | ESXi management, vSAN, vSphere vMotion, VXLAN tunnel endpoint, NFS (VTEP) | Enabled | Route based on explicit failover (vSAN, vMotion) originating virtual port (all else) | 2 | 9,000<br>(Jumbo frames) |
| SDDC-Dswitch-Public | External management traffic (north-south) | Enabled | Route based on originating virtual port | 2 | 1,500<br>(default) |
{: caption="Table 3. Converged cluster distributed switches" caption-side="bottom"}

The names, number, and ordering of the host NICs might vary depending on the {{site.data.keyword.cloud_notm}} data center and your host hardware selection.
{:note}

| Parameter          | Setting       |
|:------------------ |:------------- |
| Load balancing     | Route based on the originating virtual port \* |
| Failover detection | Link status only |
| Notify switches    | Enabled |
| Failback           | No |
| Failover order     | Active uplinks: Uplink1, Uplink2 \* |
{: caption="Table 4. Converged cluster distributed switch port group configuration settings" caption-side="bottom"}

\* The vSAN port group uses explicit failover with active or standby because it does not support load balancing of vSAN storage traffic.
{:note}

Port Group|Teaming|Uplinks|VLAN ID
---|---|---|--
SDDC-DPortGroup-Mgmt|Originating virtual port|Active: 0, 1|VLAN 1
SDDC-DPortGroup-vMotion|Use explicit failover order|Active: 0, 1|VLAN 2
SDDC-DPortGroup-VSAN|Route based on originating virtual port|Active: 0, Standby: 1|VLAN 2
SDDC-DPortGroup-NFS|Originating virtual port|Active: 0, 1|VLAN 2
NSX generated|Originating virtual port|Active: 0, 1|VLAN 1
SDDC-DPortGroup-External|Originating virtual port|Active: 0, 1|VLAN 3
{: caption="Table 5. Converged cluster virtual switch port groups and VLANs, Distributed switch SDDC-Dswitch-Private" caption-side="bottom"}

Purpose|Connected port group|Enabled services|MTU
--|---|---|---
Management|SDDC-DPortGroup-Mgmt|Management Traffic|1500 (default)
vMotion|SDDC-DPortGroup-vMotion|vMotion Traffic|9000
VTEP|NSX generated|-|9000
vSAN|SDDC-DPortGroup-VSAN|vSAN|9000
NAS|SDDC-DPortGroup-NFS|NAS|9000
{: caption="Table 6. Converged cluster VMkernel adapters, Distributed switch SDDC-Dswitch-Private" caption-side="bottom"}

## NSX configuration
{: #nsx-v-design-nsx-config}

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

![Deployed Example Customer NSX topology](../../images/vcsv4radiagrams-ra-vcs-nsx-topology-customer-example.svg "Deployed Example Customer NSX topology"){: caption="Figure 3. Deployed example customer NSX topology" caption-side="bottom"}

## Public network connectivity
{: #nsx-v-design-pub-net-config}

There are various reasons that you may need public network connectivity for your instance. This can include access to public update services or other public services for your workload such as geolocation databases or weather data. Your virtualization management and add-on services might also require or benefit from public connectivity. For example, vCenter can update its HCL database and obtain [VMware Update Manager (VUM)](/docs/vmwaresolutions?topic=vmware-solutions-vum-intro) updates over the public network. Zerto, Veeam, VMware HCX, F5 BIG-IP, and FortiGate-VM all use public network connectivity for some part of their product licensing, activation, or usage reporting. On top of this, you might use tunnels over the public network for connectivity to your on-premises data center for replication purposes.

Typically these communications are selectively routed and NATed to the public network through the management or customer edge services gateway (ESG). However, you might have more security requirements, or might prefer to use a proxy to simplify the path of communication. Additionally, if you deployed your instance with public interfaces disabled, you will not be able to use ESGs to route to the public network.

This architecture allows for the following options for routing or proxying your traffic to the public network:

Method|Description|Limitations
--|--|--
Virtualized gateway|Deploy a virtualized gateway (for example, NSX ESG, F5 BIG-IP, FortiGate-VM, or a virtual appliance of your choosing) crossing the private and public network. Configure routing on the source system (for example, vCenter, Zerto, your workload) to direct only public network traffic to the gateway, and configure the gateway according to your needs.|Applicable only to instances with public interfaces enabled. This configuration allows for both outbound and inbound traffic patterns.
Virtualized gateway with proxy|Deploy a virtualized gateway as above. Behind this gateway, [deploy a proxy server](/docs/vmwaresolutions?topic=vmware-solutions-vum-init-config#vum-init-config), and configure your services and applications to connect to the public network through this proxy.|Applicable only to instances with public interfaces enabled. Outbound traffic patterns can use the proxy but inbound traffic patterns must be managed at the gateway.
Hardware gateway|Deploy a [hardware gateway appliance](https://cloud.ibm.com/catalog/infrastructure/gateway-appliance) to your management VLAN. Configure the gateway to NAT outbound to the public network according to your needs.|Applicable to all instances, with or without public interfaces enabled. This configuration allows for both outbound and inbound traffic patterns.
Hardware gateway with proxy|Deploy a gateway appliance as above. Behind this gateway, [deploy a proxy server](/docs/vmwaresolutions?topic=vmware-solutions-vum-init-config#vum-init-config), and configure your services and applications to connect to the public network through this proxy.|Applicable to all instances, with or without public interfaces enabled. Outbound traffic patterns can use the proxy but inbound traffic patterns must be managed by the gateway.
Load balancer|IBM Cloud offers several [load balancer services](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group) that you can use to provide inbound network access to your applications.|Applicable to all instances, but limited to inbound traffic patterns.
{: caption="Table 7. Options for routing or proxying your traffic to the public network" caption-side="bottom"}

**Next topic:** [VMware NSX-T design](/docs/vmwaresolutions?topic=vmware-solutions-nsx-t-design)

## Related links
{: #nsx-v-design-related}

* [{{site.data.keyword.cloud_notm}} running VMware clusters solution architecture](https://www.ibm.com/cloud/garage/files/IBM-Cloud-for-VMware-Solutions-Multicluster-Architecture.pdf)
* [NSX Edge Services Gateway solution architecture](/docs/vmwaresolutions?topic=vmware-solutions-nsx_overview#nsx_overview)
