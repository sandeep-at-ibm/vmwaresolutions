---

copyright:

  years:  2016, 2021

lastupdated: "2021-04-01"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}

# VMware NSX-T design
{: #nsx-t-design}

VMware NSX-T is designed to address application frameworks and architectures that have heterogeneous endpoints and technology stacks. In addition to vSphere, these environments can include other hypervisors, KVM, containers, and bare metal servers. VMware NSX-T is designed to span a software defined network and security infrastructure across platforms other than just vSphere alone. While it is possible to deploy NSX-T components without needing vSphere, this design focuses on NSX-T and its integration primarily within a vCenter Server vSphere automated deployment.

As of version 3, NSX-T now has the capability to run on the vSphere VDS switch version 7.0. All new deployments of NSX and vSphere will use NSX-T on VDS; N-VDS is no longer used. Going forward, the plan is to converge NSX-T and ESXi host switches. As of NSX-T 2.4, the manager VM and the controller VM function are combined. This results in three controller/manager VMs being deployed. If on the same subnet, they use an internal network load balancer. If across different subnets, an external load balancer is required.

There are many advanced features within NSX-T such as firewall policies, inclusion of guest introspection within firewall policies, and advanced netflow tracking. Describing these features is beyond the scope of this document. See the VMware documentation for NSX-T. In this design, the NSX-T Management Infrastructure is deployed during the initial vCenter Server cluster deployment in place of NSX-V.

## NSX-T vs NSX-V
{: #nsx-t-design-nsx-t-nsx-v}

For vSphere Network NSX (NSX-V), review the following more well-known NSX-T objects with similar function to their NSX-V counterparts. Limitations and differences within a vSphere environment are also be discussed. Here is a table of typically used functions between T and V that correspond.

| NSX-V or vSphere native | NSX-T |
|:----------------------- |:----- |
| **NSX Transport zone** | Transport zone (overlay or VLAN-backed) |
| **Port groups (vDS) ** | Segments or Logical Switch |
| **VXLAN (L2 encapsulation)** | GENEVE (L2 encapsulation) |
| **Edge Gateway** | Tier-0 (T0) Gateway[^gateway1] |
| **Distributed Logical Router** | Tier-1 (T1) Gateway[^gateway2] |
| **ESXi Server** | Transport Node (ESXi, KVM, bare metal T0 Gateway) |
{: caption="Table 1. NSX-V to NSX-T terminology" caption-side="top"}

With NSX-T, you have Tier-0 (T0) Gateways and Tier-1 (T1) Gateways. While in the previous section they're shown as being equivalent to an NSX-V edge services gateway (ESG) and Distributed Logical Router (DLR) respectively, that's not entirely accurate.

[^gateway1]: A T0 Gateway is similar to an ESG. It provides north-south connectivity between physical and logical networks, it supports dynamic routing (BGP), ECMP, and stateful services such as Firewall, NAT, and Load Balancing. It also provides distributed services for east-west routing.

[^gateway2]: A T1 Gateway is like a T0 Gateway, but it does not contain uplinks for connecting to a physical network. Its uplink connects it to an auto-plumbed overlay segment with the T0 Gateway. A T1 supports static routes, NAT, Load Balancing, and IPSec VPN.

For NSX-T, there are two new concepts: Distributed Router (DR) and Service Router (SR).

| Router Type  | Capabilities |
|:------------ |:------------ |
| **Distributed Router** | Provides basic packet forwarding and distributed east-west routing functions<br>Spans all transport nodes<br>On ESXi runs as kernel module |
| **Service Router** | Provides gateway services<br>- NAT<br>- Load Balancer<br>- Gateway firewall<br>- North-south routing<br>- VPN<br>- DNS Forwarding<br>- DHCP |
{: caption="Table 2. NSX-T Distributer and Service Routers" caption-side="top"}

There are key NSX-T concepts that do not correspond to NSX-V function that need to be understood for this design’s implementation of NSX-T.

- An edge services cluster is one or more VMs or physical machines that participate in an NSX-T virtual fabric. They are endpoints for the overlay network transport zones and VLAN backed transport zones. An edge services cluster can support a single T-0 gateway instance.
- A T-0 gateway is a virtual router instance, but not a VM. Multiple T-0 gateway instances can run within an edge services cluster each with its own routing table and functions. An edge services cluster must exist before you can create a T-0 router instance.
- A transport zone can span endpoints across different platforms and multiple vSphere vCenter instances. No cross vCenter linked NSX is required. Transport zones can be excluded from specific endpoints.
- Uplink failover order is created independent of a particular logical switch as they are created in profiles as “Uplink Profiles” and are applied to a particular logical switch based on VLAN. It's possible to need a differing failover order or load balancing of physical uplinks for the same VLAN. Therefore, the uplink profile for a particular VLAN can contain multiple entries for “Teaming” with different a failover order and load balancing. When you assign the uplink profile to a logical switch, the specific teaming profile is chosen.
- The manager VM and the controller VM function are combined, which results in three NSX-T manager VMs being deployed. If on the same subnet, they use an internal network load balancer. If across different subnets, an external load balancer is required.

## Resource requirements

{: #nsx-t-design-resource-req}

In this design, the NSX-T controller Manager VMs are deployed on the management cluster. Additionally, each controller manager is assigned a VLAN–backed IP address from the private portable address block. The address block is designated for management components and configured with the DNS and NTP servers that are discussed in section 0. A summary of the NSX Manager installation is shown in following table.

| Attribute | Specification |
|:--------- |:------------- |
| **NSX managers / Controllers** | Three Virtual Appliances |
| **Number of vCPUs** | 6 |
| **Memory** |  24 GB |
| **Disk** | 300 GB |
| **Disk type** | Thin provisioned |
| **NetworkPrivate A** | Private A |
{: caption="Table 3. NSX-T Manager - controller specifications" caption-side="top"}

The following figure shows the placement of the NSX managers in relation to the other components in this architecture.

![NSX-T Manager network overview](../../images/nsx-t-3-ra-diagrams-overview-vcs-v7-t3.svg "NSX-T Manager network overview"){: caption="Figure 1. NSX-T Manager network overview" caption-side="bottom"}

## Deployment considerations
{: #nsx-t-design-deployment}

With NSX-T v3.x on vSphere VDS switch version 7.0, N-VDS are no longer required on the ESXi hosts. When configured as transport nodes, you can use the v7 VDS, which makes the consolidated cluster a more optimal design.

After initial deployment, the {{site.data.keyword.cloud}} automation deploys three NSX-T Manager virtual appliances within the management cluster. The controllers are assigned a VLAN–backed IP address from the Private A portable subnet that is designated for management components. Additionally, VM–VM anti–affinity rules are created such that controllers are separated among the hosts in the cluster.

You must deploy the management cluster with a minimum of three nodes to ensure high availability for the Manager / Controllers. In addition to the managers, the {{site.data.keyword.cloud_notm}} automation prepares the deployed workload cluster as NSX-T transport nodes. The ESXi transport nodes are assigned a VLAN–backed IP address from the Private A portable IP address range that is specified by an NSX IP pool ranged derived from the VLAN and Subnet Summary. Transport node traffic resides on the untagged VLAN and is assigned to the private NSX-T virtual distributed switch (VDS).

Depending on the customer chosen NSX-T topology to be deployed, an NSX-T Edge Cluster is either deployed as a pair of VM or as software deployed on bare metal cluster nodes. Regardless of if the cluster pair is virtual or physical, uplinks are configured to VDS switches for both {{site.data.keyword.cloud_notm}} public and private networks.

The VMware Identity Manager appliance needs to be deployed by the customer manually and provides Active Directory Authentication, multi-factor authentication (MFA), conditional access, and single sign-on (SSO) services.

The following table summarizes the requirements for a medium size environment, which is the recommended starting size for production workloads.

| Resources | Manager x3 | Edge cluster x4 |
|:--------- |:---------- |:--------------- |
| Medium size | Virtual appliance | Virtual appliance |
| Number of vCPUs | 6 | 4 |
| Memory | 24 GB | 8 GB |
| Disk | 300 GB vSAN/management NFS | 200 GB vSAN/management NFS |
| Disk type | Thin provisioned | Thin provisioned |
| Network | Private A | Private A |
{: caption="Table 4. NSX-T component specification" caption-side="top"}

## Distributed switch design
{: #nsx-t-design-distr-switch}

The design uses a minimum number of vDS Switches. The hosts in the management cluster are connected to the public and private networks. The hosts are configured with two distributed virtual switches. The use of two switches follows the practice of {{site.data.keyword.cloud_notm}} network that separates the public and private networks. All new deployments of NSX and vSphere will take advantage of running the vSphere VDS  switch version 7.0. which allows for a converged NSX-T architecture.

![Distributed switch design Private ](../../images/nsx-t-3-ra-diagrams-v7-vds-private.svg "Distributed switch design Private"){: caption="Figure 2. NSX-T Distributed switch design Private" caption-side="bottom"}

![Distributed switch design Public](../../images/nsx-t-3-ra-diagrams-v7-vds-public.svg "Distributed switch design Public"){: caption="Figure 3. NSX-T Distributed switch design Public" caption-side="bottom"}

As shown in the previous diagrams, the vDS `SDDC-Dswitch-Public` is configured for public network connectivity and the vDS `SDDC-Dswitch-Private` is configured for private network connectivity. Separating different types of traffic is required to reduce contention and latency and increase security.

VLANs are used to segment physical network functions. This design uses three VLANs: two for private network traffic and one for public network traffic. The following table shows the traffic separation.

| VLAN  | Designation | Traffic type |
|:----- |:----------- |:------------ |
| VLAN 1 | Private A   | ESXi management, management, Geneve (TEP), edge uplinks |
| VLAN 2 | Private B   | vSAN, NFS and vMotion|
| VLAN 3 | Public      | Available for internet access |
{: caption="Table 5. VLAN mapping to traffic types" caption-side="top"}

For the optional two host gateway clusters, this design uses two VLANs: one for  private network traffic and one for public network traffic. Note that this cluster type uses local disks as data store, and therefore no need for separate storage traffic.  Also the NSX-T Geneve (TEP) traffic is left out as per design. The following table shows the  traffic separation between VLANs for this cluster type.

| VLAN   | Designation       | Traffic type                                       |
|:------|:------------------|:--------------------------------------------------|
| VLAN 1 | Private Transit   | Private transit VLAN, ESXi management and vMotion  |
| VLAN 2 | Public Transit    | Public transit VLAN                                |
{: caption="Table 6. VLAN mapping to Gateway traffic types" caption-side="top"}

## Naming conventions
{: #nsx-t-design-naming}

The following naming conventions are used for deployment. For readability, only the specific naming is used. For example, "instance-name"-"dcname"-"clustername"-tz-edge-private is referred to as tz-edge-private.

| Description | Naming Standard |
|:----------- |:--------------- |
| **Management VMs** | "instancename"-nsxt-ctrlmgr0<br>"instancename”-nsxt-ctrlmgr1<br>"instancename”-nsxt-ctrlmgr2 |
| **Uplink profiles** | "instancename”-esxi-private-profile<br>"instancename”-esxi-public-profile<br>"instancename”-edge-private-profile<br>"instancename”-edge-public-profile<br>"instancename”-edge-tep-profile<br>"instancename”-edge-mgmt-tep-profile |
| **NIOC profiles** | "instancename”-“clustername”-nioc-vsan-private-profile<br>"instancename”-“clustername”-nioc-nfs-private-profile<br>“instancename”-"clustername”-nioc-public-profile |
| **Edge cluster profiles** | "instancename”-"dcname”-“clustername”-edge-cluster-profile |
| **Transport zones** | "instancename”-tz-esxi-private<br>"instancename”-tz-esxi-public<br>"instancename”-tz-vm-overlay<br>"instancename”-tz-edge-private<br>"instancename”-tz-edge-public |
| **Segments** |  "instancename”-edge-private-trunk<br>"instancename”-edge-public-trunk<br>"instancename”-"dcname”-edge-tep-trunk<br>"instancename”-"dcname”-customer-t0-private<br>"instancename”-"dcname”-customer-to-public<br>"instancename”-customer-workload |
| **IP address pools** | "instancename”-"dcname”-“clustername”-“primary-vlan-id”-esxi-tep-pool|
| **Transport nodes profiles** | "instancename”-"dcname”-“clustername”-esxi-tpn-profile|
| **Tier-0 and Tier-1 gateways** | "instancename”-"dcname”-“clustername”-T0-xxx (specific to the function, such as: services, workload, OpenShift)<br>"instancename”-"dcname”-“clustername”-T1-xxx |
{: caption="Table 7. NSX-T design naming convention" caption-side="top"}

## Transport nodes
{: #nsx-t-design-transport-nodes}

Transport nodes define the physical server objects or VMs that participate in the virtual network fabric. Review the following table to understand the design.

| Transport node type   | Uplink profile | IP assignment |
|:-------------------  |:-------------- |:------------- |
| **ESXi** | esxi-private-profile<br>esxi-public-profile | esxi-tep-pool |
| **Edge Cluster**  | edge-private-profile<br>edge-public-profile<br>edge-tep-profile | edge-tep-pool |
{: caption="Table 8. NSX-T transport nodes" caption-side="top"}

## Uplink profiles and teaming
{: #nsx-t-design-uplink-profiles}

An uplink profile defines policies for the links from hypervisor hosts to NSX-T logical switches or from NSX Edge nodes to top-of-rack switches.

| Uplink profile name | VLAN | Teaming policy | Active uplinks | Standby links | MTU |
|:------------------- |:---- |:-------------- |:-------------- |:------------- |:--- |
| **edge-private-profile** | default | Default<br>Failover Order | uplink-1 | uplink-2|9000 |
| **esxi-public-profile**  | default | Default<br>Loadbalance Source | uplink-1<br>uplink-2 |   | 1500 |
| **esxi-private-profile** | Default | Default<br>Loadbalance Source | uplink-1<br>uplink-2 |   | 9000 |
| **esxi-private-profile** | default | iscsi-a<br>Failover order|uplink-1 |   | 9000 |
| **esxi-private-profile** | default | iscsi-b<br>Failover order|Uplink-2 |   | 9000 |
| **edge-public-profile**  | default | Load Balance source | uplink-1|uplink-2 | 1500 |
| **edge-tep-profile**     | Storage VLAN | Failover order | uplink-1 |   | 9000 |
{: caption="Table 9. NSX-T uplink profiles" caption-side="top"}

## VNI pools
{: #nsx-t-design-vni-pools}

Virtual Network Identifiers (VNIs) are similar to VLANs to a physical network. They are automatically created when a logical switch is created from a pool or range of IDs. This design uses the default VNI pool that is deployed with NSX-T.

## Segments
{: #nsx-t-design-logical-switches}

An NSX-T segment reproduces switching functions, broadcast, unknown unicast, multicast (BUM) traffic, in a virtual environment that is decoupled from the underlying hardware.

| Segment name | VLAN |Transport zone | Uplink teaming policy |
|:------------ |:---- |:------------- |:--------------------- |
| edge-mgmt | Tagged storage vlan | tz-esxi-private | Default<br>failover order<br>uplink-1 |
| edge-private-trunk | 0-4094 | tz-esxi-private | Default<br>failover order<br>uplink-1 |
| edge-public-trunk | 0-4094 | tz-esxi-public | Default<br>loadbalance source |
| edge-tep | Tagged storage vlan | tz-esxi-private | TEP |
| T0-public | Default | tz-edge-public |
| T0-private | Default | tz-edge-private |
| customer-workload  |   | tz-vm-overlay |
{: caption="Table 10. NSX-T logical switches" caption-side="top"}

### Edge cluster
{: #nsx-t-design-edge-cluster}

Within this design, two virtual edge node clusters are provisioned, one for use by management and the other for customer workloads. There is a limitation of one T0 per Edge Transport Node, which means that a single Edge Node Cluster can support one T0 Gateway (in either Active/Standby or Active/Active). See the following figure which diagrams the functional components of an NSX-T edge services cluster.

![Customer Edge Cluster Topology](../../images/nsx-t-3-ra-diagrams-customer-edge-cluster-t0-t1.svg "Customer Edge Cluster Topology"){: caption="Figure 4. Customer Edge Cluster Topology" caption-side="bottom"}

![Services Edge Cluster Topology](../../images/nsx-t-3-ra-diagrams-management-edge-cluster-t0.svg "Services Edge Cluster Topology"){: caption="Figure 5. Services Edge Cluster Topology" caption-side="bottom"}

#### Tier 0 logical gateway
{: #nsx-t-design-tier-0}

An NSX-T Tier-0 logical gateway provides a gateway service between the logical and physical networks (for north-south traffic). In this design, two highly available T0 gateways are deployed in two separate NSX-T edge clusters, one for customer and one services/managment needs. Addional services and products are optional for customer chosen topologies and they will use the services T0 for their inbound or outbound connectivity needs. Each T0 logical gateway is configured with two uplinks for private and two for public, additionally VIPs are assigned to both public and private uplinks.

#### Tier 1 logical gateway
{: #nsx-t-design-tier-1}

An NSX-T Tier-1 logical gateway has downlink ports to connect to NSX-T Data Center logical switches and uplink ports to connect to NSX-T Data Center Tier-0 logical gateways. They run in the kernel level of the hypervisor they are configured for, and they are virtual router instances (vrf) of the NSX-T edge cluster.  In this design, one or more T1 logical gateways can be created for the needs of customer chosen topologies.

#### Tier 1 to Tier 0 route advertisement
{: #nsx-t-design-tier-1-tier-0}

To provide Layer 3 connectivity between VMs connected to logical switches that are attached to different tier-1 logical gateways, it is necessary to enable tier-1 route advertisement towards tier-0. No need to configure a routing protocol or static routes between tier-1 and tier-0 logical routers. NSX-T creates static routes automatically when you enable route advertisement. For this design, route advertisement is always enabled for any {{site.data.keyword.vmwaresolutions_full}} automation created T-1 gateways.

### Preconfigured topologies
{: #nsx-t-design-preconfig-topo}

Workload to T1 to T0 gateway – virtual edge services cluster

![NSX-T deployed topology virtual T0 Edge Gateway](../../images/nsx-t-3-ra-diagrams-preconfigured-topology.svg "NSX-T deployed topology virtual T0 Edge Gateway"){: caption="Figure 6. NSX-T deployed topology virtual T0 Edge Gateway" caption-side="bottom"}

Topology 1 is basically the same topology that is deployed with NSX-V DLR and Edge gateways. With NSX-T, no dynamic routing protocol configuration between T1 and T0. RFC-1891 IP address space is used for the workload overlay network and transit overlay network. A customer private and public portable IP space is assigned for customer use. A customer designated {{site.data.keyword.cloud_notm}} private and public portable IP space is assigned to the T0 for customer use.

**Next topic:** [VMware Identity Manager](/docs/vmwaresolutions?topic=vmwaresolutions-nsx-t-idm)
