---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-07"

subcollection: vmwaresolutions


---

# VMware NSX-T design
{: #nsx-t-design}

Unlike NSX-V (NSX on vSphere), VMware NSX-T is designed to address application frameworks and architectures that have heterogeneous endpoints and technology stacks. In addition to vSphere, these
environments can include other hypervisors, KVM, containers, and bare metal. VMware NSX is designed to span a software defined network and security infrastructure across platforms other than just vSphere alone. While it is possible to deploy NSX-T components without needing vSphere, this design focuses on NSX-T and its integration primarily within a vCenter Server vSphere automated deployment.

There are many advanced features within NSX-T such as firewall policies, inclusion of guest introspection within firewall policies, and advanced netflow tracking. Describing these features is beyond the scope of this document. See the VMware documentation for NSX-T. In this design, the NSX-T Management Infrastructure is deployed during the initial vCenter Server cluster deployment in place of NSX-V.

## NSX-T vs NSX-V
{: #nsx-t-design-nsx-t-nsx-v}

For vSphere Network NSX (NSX-V), review the following more well-known NSX-T objects with similar function to their NSX-V counterparts. Limitations and differences within a vSphere environment are also be discussed. Here is a table of typically used functions between T and V that correspond.

| NSX-V or vSphere native | NSX-T |
|:----------------------- |:----- |
| **Virtual Distributed Switch** | NSX Virtual Distributed Switch (N-VDS) |
| **NSX Transport zone** | Transport zone (overlay or VLAN-backed) |
| **Logical Switches** | Segments |
| **VXLAN (L2 encapsulation)** | GENEVE (L2 encapsulation) |
| **Edge Gateway** | Tier-0 (T0) Gateway[^gateway1] |
| **Distributed Logical Router** | Tier-1 (T1) Gateway[^gateway2] |
| **ESXi Server** | Transport Node (ESXi, KVM, bare metal T0 Gateway) |
{: caption="Table 1. NSX-V to NSX-T terminology" caption-side="bottom"}

With NSX-T, you have Tier-0 (T0) Gateways and Tier-1 (T1) Gateways. While in the previous section they're shown as being equivalent to a T0 Gateway and T1 Gateway respectively, that's not accurate.

[^gateway1]: A T0 Gateway is similar to an ESG. It provides north-south connectivity between physical and logical networks, it supports dynamic routing (BGP), ECMP, and stateful services such as Firewall, NAT, and Load Balancing. It also provides distributed services for east-west routing.

[^gateway2]: A T1 Gateway is like a T0 Gateway, but it does not contain uplinks for connecting to a physical network. Its uplink connects it to an auto-plumbed overlay segment with the T0 Gateway. A T1 supports static routes, NAT, Load Balancing, and IPSec VPN.

For NSX-T, there are two new concepts: Distributed Router (DR) and Service Router (SR).

| Router Type  | Capabilities |
|:------------ |:------------ |
| **Distributed Router** | Provides basic packet forwarding and distributed east-west routing functions<br>Spans all transport nodes<br>On ESXi runs as kernel module |
| **Service Router** | Provides gateway services<br>- NAT<br>- Load Balancer<br>- Gateway firewall<br>- North-south routing<br>- VPN<br>- DNS Forwarding<br>- DHCP |
{: caption="Table 2. NSX-T Distributer and Service Routers" caption-side="bottom"}

There are key NSX-T concepts that do not correspond to NSX-V function that need to be understood for this design’s implementation of NSX-T.

- An edge cluster is one or more VMs or physical machines that participate in an NSX-T virtual fabric. They are endpoints for the overlay network transport zones and VLAN backed transport zones. An edge cluster can support a single T-0 gateway instance.
- A T-0 gateway is a virtual router instance, but not a VM. Multiple T-0 gateway instances can run within an edge cluster each with its own routing table and functions. An edge cluster must exist before you can create a T-0 router instance.
- A transport zone can span endpoints across different platforms and multiple vSphere vCenter instances. No cross vCenter linked NSX is required. Transport zones can be excluded from specific endpoints. An N-VDS can be correlated with one Overlay Transport Zone and many VLAN transport zones. N-VDS can be created as part of Transport Zone creation.
- Uplink failover order is created independent of a particular logical switch as they are created in profiles as “Uplink Profiles” and are applied to a particular logical switch based on VLAN. It's possible to need a differing failover order or load balancing of physical uplinks for the same VLAN. Therefore, the uplink profile for a particular VLAN can contain multiple entries for “Teaming” with different a failover order and load balancing. When you assign the uplink profile to a logical switch, the specific teaming profile is chosen.
- As of NSX-T 2.4, the manager VM and the controller VM function are combined, which results in three NSX-T manager VMs being deployed. If on the same subnet, they use an internal network load balancer. If across different subnets, an external load balancer is required.

## Resource requirements

{: #nsx-t-design-resource-req}

In this design, the NSX-T controller Manager VMs are deployed on the management cluster. Additionally, each controller manager is assigned a VLAN–backed IP address from the private portable address block. The address block is designated for management components and configured with the DNS and NTP servers that are discussed in section 0. A summary of the NSX Manager installation is shown in following table.

The VMware Identity Manager appliance must be deployed by the customer manually if required for basic RBAC/AD integration. It can also provide multi-factor authentication (MFA), conditional access, and single sign-on (SSO) services. For more information, see [VMware Identity Manager](/docs/vmwaresolutions?topic=vmwaresolutions-nsx-t-idm).

| Attribute | Specification |
|:--------- |:------------- |
| **NSX Managers** | Three Virtual Appliances |
| **Number of vCPUs** | 6 |
| **Memory** |  24 GB |
| **Disk** | 200 GB |
| **Disk type** | Thin provisioned |
| **NetworkPrivate A** | Private A |
{: caption="Table 3. NSX-T Manager - controller specifications" caption-side="bottom"}

The following figure shows the placement of the NSX Managers in relation to the other components in this architecture.

![NSX-T Manager network overview](../../images/vcsv4radiagrams-ra-vcs-nsxt-overview.svg "NSX-T Manager network overview"){: caption="Figure 1. NSX-T Manager network overview" caption-side="bottom"}

## Deployment considerations
{: #nsx-t-design-deployment}

With NSX-T on vSphere, the N-VDS must be assigned the physical adapters within the hosts. An N-VDS can be configured only within NSX-T Manager. Therefore, for redundancy to be maintained, no physical adapters are available for native local switch or vDS assignment in a cluster that houses both the NSX-T components and the associated overlay network components.

After initial deployment, the {{site.data.keyword.cloud}} automation deploys three NSX-T Manager virtual appliances within the management cluster. The controllers are assigned a VLAN–backed IP address from the Private A portable subnet that is designated for management components. Additionally, VM–VM anti–affinity rules are created such that controllers are separated among the hosts in the cluster.

You must deploy the management cluster with a minimum of three nodes to ensure high availability for the Manager / Controllers. In addition to the managers, the {{site.data.keyword.cloud_notm}} automation prepares the deployed workload cluster as NSX-T transport nodes. The ESXi transport nodes are assigned a VLAN–backed IP address from the Private A portable IP address range that is specified by an NSX IP pool ranged derived from the VLAN and Subnet Summary. Transport node traffic resides on the untagged VLAN and is assigned to the private NSX-T virtual distributed switch (N-VDS).

Depending on the customer chosen NSX-T topology to be deployed, an NSX-T Edge Cluster is either deployed as a pair of VM or as software deployed on bare metal cluster nodes. Regardless of if the cluster pair is virtual or physical, uplinks are configured to N-VDS switches for both {{site.data.keyword.cloud_notm}} public and private networks.

The VMware Identity Manager appliance needs to be deployed by the customer manually and provides Active Directory Authentication, multi-factor authentication (MFA), conditional access, and single sign-on (SSO) services.

The following table summarizes the requirements for a medium size environment, which is the recommended starting size for production workloads.

| Resources | Manager x3 | Edge cluster x4 | Bare Metal Edge |
|:--------- |:---------- |:--------------- |:--------------- |
| **Medium size** | Virtual appliance | Virtual appliance | Physical Server |
| **Number of vCPUs** | 6 | 4 | 8 |
| **Memory** | 24 GB | 8 GB | 8 GB |
| **Disk** | 200 GB vSAN/management NFS | 200 GB vSAN/management NFS | 200 GB |
| **Disk type** | Thin provisioned | Thin provisioned | Physical |
| **Network** | Private A | Private A | Private A |
{: caption="Table 4. NSX-T component specification" caption-side="bottom"}

## Distributed switch design
{: #nsx-t-design-distr-switch}

The design uses a minimum number of vDS Switches. The hosts in the management cluster are connected to the public and private networks. The hosts are configured with two distributed virtual switches. The use of two switches follows the practice of {{site.data.keyword.cloud_notm}} network that separates the public and private networks. The hosts in the workload cluster are connected to the public and private networks. The hosts are configured with two NSX-T distributed virtual switches (N-VDS). The following diagram shows the vDS and N-VDS design.

![Distributed switch design](../../images/vcsv4radiagrams-nsx-t-distributed-switch-design.svg "Distributed switch design"){: caption="Figure 2. NSX-T Distributed switch design" caption-side="bottom"}

VLANs are used to segment physical network functions. This design uses three VLANs: two for private network traffic and one for public network traffic. The following table shows the traffic separation.

| VLAN  | Designation | Traffic type |
|:----- |:----------- |:------------ |
| VLAN 1 | Private A   | ESXi management, management, ESXi (TEP) |
| VLAN 2 | Private B   | vSAN, NFS, NSX-T Edge (TEP), and vMotion|
| VLAN 3 | Public      | Available for internet access |
{: caption="Table 5. VLAN mapping to traffic types" caption-side="bottom"}

## Naming conventions
{: #nsx-t-design-naming}

The following naming conventions are used for deployment. For readability, only the specific naming is used. For example, "instance-name"-"dcname"-"clustername"-tz-edge-private is referred to as tz-edge-private.

| Description | Naming Standard |
|:----------- |:--------------- |
| **Management VMs** | "instancename"-nsxt-ctrlmgr0<br>"instancename”-nsxt-ctrlmgr1<br>"instancename”-nsxt-ctrlmgr2 |
| **Uplink profiles** | "instancename”-esxi-private-profile<br>"instancename”-esxi-public-profile<br>"instancename”-edge-private-profile<br>"instancename”-edge-public-profile<br>"instancename”-edge-tep-profile |
| **NIOC profiles** | "instancename”-“clustername”-nioc-vsan-private-profile<br>"instancename”-“clustername”-nioc-iscsi-private-profile<br>"instancename”-“clustername”-nioc-nfs-private-profile<br>“instancename”-"clustername”-nioc-public-profile |
| **Edge cluster profiles** | "instancename”-"dcname”-“clustername”-edge-cluster-profile |
| **Transport zones** | "instancename”-tz-esxi-private<br>"instancename”-tz-esxi-public<br>"instancename”-tz-vm-overlay<br>"instancename”-tz-edge-private<br>"instancename”-tz-edge-public |
| **N-VDS names** | "instancename”-nvds-private<br>"instancename”-nvds-public<br>"instancename”-nvds-edge-private<br>"instancename”-nvds-edge-public |
| **Segments** |  "instancename”-mgmt<br>"instancename”-"dcname”-nfs<br>"instancename”-"dcname”-vsan<br>"instancename”-"dcname”-vmotion<br>"instancename”-"dcname”-iscsi-a<br>"instancename”-"dcname”-iscsi-b<br>"instancename”-"dcname”-edge-mgmt<br>"instancename”-edge-private-trunk<br>"instancename”-edge-public-trunk<br>"instancename”-"dcname”-edge-tep-trunk<br>"instancename”-"dcname”-customer-t0-private<br>"instancename”-"dcname”-customer-to-public<br>"instancename”-customer-workload |
| **IP address pools** | "instancename”-"dcname”-“clustername”-“primary-vlan-id”-esxi-tep-pool<br>"instancename”-"dcname”-“clustername”-“secondary-vlan-id”-edge-tep-pool<br>|
| **Transport nodes profiles** | "instancename”-"dcname”-“clustername”-esxi-tpn-profile|
| **Tier-0 and Tier-1 gateways** | "instancename”-"dcname”-“clustername”-T0-xxx (specific to the function, such as: workload, OpenShift, HCX)<br>"instancename”-"dcname”-“clustername”-T1-xxx |
{: caption="Table 6. NSX-T design naming convention" caption-side="bottom"}

## Transport zones and N-VDS
{: #nsx-t-design-transport-zones}

Transport zones dictate which hosts and which VMs can participate in the use of a particular network. A transport zone limits the hosts that can "see" a logical switch and therefore, the VMs can be attached to the logical switch. A transport zone can span one or more host clusters. This design calls for transport zones to be created as in the following table:

| Transport zone name | VLAN/Geneve | N-VDS name | Uplink teaming policy |
|:------------------- |:----------- |:---------- |:--------------------- |
| **tz-vm-overlay** | Geneve | nvds-private | Default |
| **tz-edge-public** | VLAN | nvds-edge-public | Default |
| **tz-esxi-public** | VLAN | nvds-public | Default |
| **tz-esxi-private** | VLAN | nvds-private | NFS, vSAN, iSCSI-A&B Default |
| **tz-edge-private** | VLAN | nvds-edge-private | Default |
{: caption="Table 7. NSX-T transport zones and N-VDS" caption-side="bottom"}

## Transport nodes
{: #nsx-t-design-transport-nodes}

Transport nodes define the physical server objects or VMs that participate in the virtual network fabric. Review the following table to understand the design.

| Transport node type | N-VDS Names  | Uplink profile | IP assignment |
|:------------------- |:------------ |:-------------- |:------------- |
| **ESXi** | nvds-private<br>nvds-public | esxi-private-profile<br>esxi-public-profile | esxi-tep-pool |
| **Edge Cluster** | nvds-edge-private<br>nvds-edge-public<br>nvds-private | edge-private-profile<br>edge-public-profile<br>edge-tep-profile | edge-tep-pool |
{: caption="Table 8. NSX-T transport nodes" caption-side="bottom"}

## Uplink profiles and teaming
{: #nsx-t-design-uplink-profiles}

An uplink profile defines policies for the links from hypervisor hosts to NSX-T logical switches or from NSX Edge nodes to top-of-rack switches.

| Uplink profile name | VLAN | Teaming policy | Active uplinks | Standby links | MTU |
|:------------------- |:---- |:-------------- |:-------------- |:------------- |:--- |
| **edge-private-profile** | default | Default<br>Failover Order | uplink-1 | uplink-2|9000 |
| **esxi-public-profile**  | default | Default<br>Loadbalance Source | uplink-1<br>uplink-2 |   | 1500 |
| **esxi-private-profile** | Default | Default<br>Loadbalance Source | uplink-1<br>uplink-2 |   | 9000 |
| **esxi-private-profile** | default | Management<br>Failover Order | uplink-1|uplink-2 | 9000 |
| **esxi-private-profile** | default | vsan<br>Failover order | uplink-2|uplink-1 | 9000 |
| **esxi-private-profile** | default | nfs<br>Failover order | uplink-2|uplink-1 | 9000 |
| **esxi-private-profile** | default | vmotion<br>Failover order|uplink-1|uplink-2 | 9000 |
| **esxi-private-profile** | default | iscsi-a<br>Failover order|uplink-1 |   | 9000 |
| **esxi-private-profile** | default | iscsi-b<br>Failover order|Uplink-2 |   | 9000 |
| **edge-public-profile**  | default | Load Balance source | uplink-1|uplink-2 | 1500 |
| **edge-tep-profile**     | Storage VLAN | Failover order | uplink-1 |   | 9000 |
{: caption="Table 9. NSX-T uplink profiles" caption-side="bottom"}

## VNI pools
{: #nsx-t-design-vni-pools}

Virtual Network Identifiers (VNIs) are similar to VLANs to a physical network. They are automatically created when a logical switch is created from a pool or range of IDs. This design uses the default VNI pool that is deployed with NSX-T.

## Segments
{: #nsx-t-design-logical-switches}

An NSX-T segment reproduces switching functions, broadcast, unknown unicast, multicast (BUM) traffic, in a virtual environment that is decoupled from the underlying hardware.

| Segment name | VLAN |Transport zone | Uplink teaming policy |
|:------------ |:---- |:------------- |:--------------------- |
| Mgmt | default | tz-esxi-private | mgmt |
| NFS|Tagged storage vlan| tz-esxi-private | NFS |
| vMotion|Tagged storage vlan | tz-esxi-private | vMotion |
| vSAN | Tagged storage vlan| tz-esxi-private | vSAN |
| iSCSI-A| Tagged storage vlan | tz-esxi-private| iSCSI-A |
| iSCSi-B| Tagged storage vlan | tz-esxi-private | iSCSi-B |
| edge-mgmt | Tagged storage vlan | tz-esxi-private | Default<br>failover order<br>uplink-1 |
| edge-private-trunk | 0-4094 | tz-esxi-private | Default<br>failover order<br>uplink-1 |
| edge-public-trunk | 0-4094 | tz-esxi-public | Default<br>loadbalance source |
| edge-tep | Tagged storage vlan | tz-esxi-private | TEP |
| T0-public | Default | tz-edge-public |
| T0-private | Default | tz-edge-private |
| customer-workload  |   | tz-vm-overlay |
{: caption="Table 10. NSX-T logical switches" caption-side="bottom"}

### Edge cluster
{: #nsx-t-design-edge-cluster}

Within this design, two virtual edge node clusters are provisioned, one for use by management and the other for customer workloads. There is a limitation of one T0 per Edge Transport Node, which means that a single Edge Node Cluster can support one T0 Gateway (in either Active/Standby or Active/Active). See the following figure which diagrams the functional components of an NSX-T edge cluster.

![NSX-T Edge cluster example of T0 to T1 scale](../../images/vcsv4radiagrams-ra-nsx-t-edge-cluster-t0-to-t1-scale.svg "NSX-T Edge cluster example of T0 to T1 scale"){: caption="Figure 3. NSX-T Edge cluster example of T0 to T1 scale" caption-side="bottom"}

![Management T0 Gateway](../../images/vcsv4radiagrams-topology-0.svg "Management T0 Gateway"){: caption="Figure 4. Management T0 gateway" caption-side="bottom"}

#### Tier 0 logical gateway
{: #nsx-t-design-tier-0}

An NSX-T Tier-0 logical router provides an on and off gateway service between the logical and physical network. For this design, multiple T-0 gateways are deployed for the needs of management, add-on products, and optionally for customer chosen topologies.

#### Tier 1 logical gateway
{: #nsx-t-design-tier-1}

An NSX-T Tier-1 logical gateway has downlink ports to connect to NSX-T data center logical switches and uplink ports to connect to NSX-T data center tier-0 logical routers only. They run in the kernel level of the hypervisor they are configured for and not as a virtual or physical machine. For this design, one or more T-1 logical gateways are created for the needs of customer chosen topologies, although a T-1 logical gateway is not always needed, segments can be attached directly to a T-0.

#### Tier 1 to Tier 0 route advertisement
{: #nsx-t-design-tier-1-tier-0}

To provide Layer 3 connectivity between VMs connected to logical switches that are attached to different tier-1 logical gateways, it is necessary to enable tier-1 route advertisement towards tier-0. No need to configure a routing protocol or static routes between tier-1 and tier-0 logical routers. NSX-T creates static routes automatically when you enable route advertisement. For this design, route advertisement is always enabled for any IBM Cloud for VMware Solutions automation created T-1 gateways.

### Preconfigured topologies
{: #nsx-t-design-preconfig-topo}

Workload to T1 to T0 gateway – virtual edge cluster

![NSX-T deployed topology virtual T0 Edge Gateway](../../images/vcsv4radiagrams-topology-1.svg "NSX-T deployed topology virtual T0 Edge Gateway"){: caption="Figure 5. NSX-T deployed topology virtual T0 Edge Gateway" caption-side="bottom"}

Topology 1 is basically the same topology that is deployed with NSX-V DLR and Edge gateways. With NSX-T, no dynamic routing protocol configuration between T1 and T0. RFC-1891 IP address space is used for the workload overlay network and transit overlay network. A customer private and public portable IP space is assigned for customer use. A customer designated {{site.data.keyword.cloud_notm}} private and public portable IP space is assigned to the T0 for customer use.

**Next topic:** [VMware Identity Manager](/docs/vmwaresolutions?topic=vmwaresolutions-nsx-t-idm)
