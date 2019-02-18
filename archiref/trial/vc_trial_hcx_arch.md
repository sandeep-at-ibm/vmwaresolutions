---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HCX on IBM Cloud architecture design for the Single-node Trial for vCenter Server on IBM Cloud
{: #vc_trial_hcx_arch}

The VMware HCX on {{site.data.keyword.cloud}} with Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}} is a new offering that enables seamless connection between {{site.data.keyword.vmwaresolutions_short}} instances and an on-premises VMware virtualized datacenter. While the recommendation for vCenter Server is a minimum of three nodes, the single-node trial provides a low-cost path to test and experience the benefits of a hybrid cloud implementation.

{{site.data.keyword.vmwaresolutions_short}} includes fully automated, rapid deployments of vCenter Server configurations in the {{site.data.keyword.cloud_notm}}. The Single-node Trial for vCenter Server offering complements the on-premises infrastructure and allows existing and future workloads to run in the {{site.data.keyword.cloud_notm}} without conversion. The offering uses the same tools, skills, and processes used on-premises. For more information about {{site.data.keyword.vmwaresolutions_short}} offerings, see the [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture).

The HCX on {{site.data.keyword.cloud_notm}} service blends vCenter Server instances with existing on-premises virtualized datacenters by enabling the creation of seamless network extensions and bidirectional migration of workloads. HCX on IBM Cloud components, which are deployed as virtual machines (VMs) in the {{site.data.keyword.cloud_notm}} VMware target site, enable the establishment of a connection with the HCX on {{site.data.keyword.cloud_notm}} components that are installed in the peer on-premises source site.

Figure 1. HCX architecture

![HCX architecture](hcx-architecture.svg "HCX architecture")

The following information provides the design of the HCX on {{site.data.keyword.cloud_notm}} service implementation. It includes both the components on the target side {{site.data.keyword.vmwaresolutions_short}} instance and the components that are deployed on the source, on-premises.

## HCX on IBM Cloud overview
{: #vc_trial_hcx_arch-ovw}

{{site.data.keyword.cloud_notm}} seamlessly integrates on-premises vSphere vCenter networks into {{site.data.keyword.vmwaresolutions_short}} deployments. Hybrid networking extends on-premises vSphere vCenter networks into the {{site.data.keyword.cloud_notm}}, supporting bidirectional VM mobility.

HCX owns the source and destination encryption and decryption processes, which ensures consistent security and provides admission for hybrid workflows such as VM migration and network extension. This offering creates an optimized, software-defined wide area network (WAN) to increase stretched network performance, enabling performance approaching local area network (LAN) speed. HCX enables bidirectional workload and VMware NSX security policy migration to the {{site.data.keyword.cloud_notm}}, integrates with vSphere vCenter, and is managed from the vSphere Web Client.

### Layer 2 network extension
{: #vc_trial_hcx_arch-layer-2-extension}

HCX allows an existing on-premises vSphere estate to securely stretch a network from its on-premises vCenter to an {{site.data.keyword.CloudDataCent_notm}} running VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} or vCenter Server. The following items enable this feature:

* HCX provides an appliance that is called a Layer 2 Concentrator (L2C).
* Extended networks link to {{site.data.keyword.cloud_notm}} NSX Edge appliances deployed on vCenter Server.
* The ability to deploy more than one standard Layer 2 concentrators to achieve scalability and increase throughput from the on-premises vCenter.
* VMs are migrated through the Cloud Gateway and over stretched Layer 2 can retain their IP and MAC addresses.

### Virtual machine migration
{: #vc_trial_hcx_arch-vm-mig}

HCX provides the following three methods of VM movement:

* Low-downtime migration
* vSphere vMotion migration
* Cold migration

#### Low-downtime migration
{: #vc_trial_hcx_arch-low-downtime-mig}

Low-downtime migration relies on vSphere Replication, which is a distributed technology that is implemented in the VMware ESX or VMware ESXi hypervisor. The on-premises HCX deployment creates a replica of a live VM in the {{site.data.keyword.cloud_notm}}, performs a switchover to power off the source VM, and power on the migrated VM. The migration path is always through the Cloud Gateway. The transport can be the internet, a Layer 2 stretched network, or a Direct Connect line. You can migrate a VM more than one time in either direction.

#### vSphere vMotion migration
{: #vc_trial_hcx_arch-vmotion-mig}

You can transfer live VMs by using vSphere vMotion migration across a network that is stretched to the {{site.data.keyword.cloud_notm}}. vMotion migration is also called zero downtime migration, or cross-cloud vMotion.

#### Cold migration
{: #vc_trial_hcx_arch-cold-mig}

Cold migration provides the ability to transfer a powered-off VM to the {{site.data.keyword.cloud_notm}} over a stretched network created via the Layer 2 Concentrator.

#### Common migration features
{: #vc_trial_hcx_arch-common-feat}

The following features are available across all three types of migration:

* Software-defined WAN optimization that increases migration throughput and speed.
* Schedule your migration for a specified time.
* Keep the host name, VM name, or both.

### Networking
{: #vc_trial_hcx_arch-network}

The following networking features are built into the Cloud Gateway and the Layer 2 Concentrators.

#### Intelligent flow routing
{: #vc_trial_hcx_arch-intel-flow}

Intelligent flow routing automatically selects the best connection based on the internet path, efficiently flooding the entire connection so that workloads are moved as fast as possible. When larger flows, such as backup or replication, cause CPU contention, smaller flows are routed to less busy CPUs, improving performance of interactive traffic.

#### Proximity routing
{: #vc_trial_hcx_arch-prox-routing}

Proximity routing ensures that forwarding between VMs connected to stretched and routed networks, both on-premises and in the cloud, is symmetrical. This feature requires Advanced Networks Services with Dynamic Routing that is configured between the customer premises and the cloud.

When users extend their networks to the cloud, Layer 2 connectivity is stretched onto {{site.data.keyword.cloud_notm}} networks. However, without route optimization, Layer 3 communication requests must return to the on-premises network origin to be routed. This return trip is called "tromboning" or "hairpinning." Tromboning is inefficient because packets must travel back and forth between the network origin and the cloud, even when both source and destination VMs reside in the cloud.

If the forwarding path includes stateful firewalls or other inline equipment that must see both sides of the connection, communication might fail. VM communication, without route optimization, failure occurs when the egress path that is exiting the cloud is either the stretched Layer 2 network or the Organization Routed Network. The on-premises network doesn't know about the stretched network "shortcut." This problem is called asymmetric routing. The solution is to enable proximity routing so the on-premises network can learn the routes from the {{site.data.keyword.cloud_notm}}.

The Cloud Gateway maintains an inventory of VMs in the cloud. It also understands the following VM states:

* Transferred to the {{site.data.keyword.cloud_notm}} with vMotion (zero-downtime migration)
* Migrated to the cloud by using host-based replication (low-downtime migration)
* Created in the cloud (on a stretched network)

#### Security
{: #vc_trial_hcx_arch-sec}

The Cloud Gateway offers Suite B-compliant AES-GCM with IKEv2, AES-NI offload, and flow-based admission control. HCX also owns the source and destination encryption and decryption process, ensuring consistent security and administration for hybrid workflows such as VM migration and network extension. You can migrate security policies that are defined and assigned to a VM on-premises with the VM into the {{site.data.keyword.cloud_notm}}.

The following conditions are required for policy migration:

* The on-premises data center is running NSX V6.2.2 or greater.
* In vSphere, the security policy is a single NSX Section that can have many rules.
* You can name a set of IP addresses or MAC addresses to participate in the policy.
* The name of the MAC Set or IP Set can't exceed 218 characters.
* Supported rules specify Layer 3 IP addresses or IP Sets, or Layer 2 MAC addresses or MAC Sets as the source or destination.

### HCX components
{: #vc_trial_hcx_arch-hcx-comp}

The HCX on {{site.data.keyword.cloud_notm}} service deploys four virtual appliances that are installed and configured on both the on-premises datacenter and the IBM Cloud target. The following information describes each of the four required virtual appliances. Optionally, edge devices might be required depending on the implementation design.

#### HCX Manager
{: #vc_trial_hcx_arch-hcx-manager}

The HCX Manager virtual appliance is an extension to the on-premises vCenter. The appliance is deployed as a VM and its file structure contains the other hybrid service virtual appliances. The HCX Manager oversees the deployment and configuration of the Cloud Gateway, the Layer 2 Concentrators, and WAN Optimization virtual appliance both on-premises and within the {{site.data.keyword.cloud_notm}}.

#### Hybrid Cloud Gateway
{: #vc_trial_hcx_arch-hcg}

The Hybrid Cloud Gateway (CGW) maintains a secure channel between the on-premises vSphere estate and the {{site.data.keyword.cloud_notm}}. HCX uses strong encryption to bootstrap a site-to-site connection to the {{site.data.keyword.cloud_notm}}. The secure channel between vSphere and the {{site.data.keyword.cloud_notm}} prevents networking "middle mile" security problems. The Cloud Gateway also incorporates vSphere replication technology to perform bidirectional migration.

#### WAN Optimization
{: #vc_trial_hcx_arch-wan-opt}

The WAN Optimization appliance is the component that performs WAN conditioning to reduce effects of latency. It also incorporates Forward Error Correction to negate packet loss scenarios, and deduplication of redundant traffic patterns. Altogether, these reduce bandwidth use and ensure the best use of available network capacity to expedite data transfer to and from the {{site.data.keyword.cloud_notm}}.

VM migration relies on the combination of Cloud Gateway and the WAN Optimization appliance to achieve unparalleled mobility between vSphere on-premises and the {{site.data.keyword.cloud_notm}}. Additionally, Layer 2 extension benefits from WAN optimization when the data path is routed through the Cloud Gateway.
{:important}

#### Layer 2 Concentrators
{: #vc_trial_hcx_arch-layer-2-conc}

The Layer 2 Concentrators (L2C) appliances allow the extension of a Layer 2 network from the on-premises vSphere data center to the {{site.data.keyword.cloud_notm}}.

The Layer 2 Concentrators have the following interfaces:

* **Internal trunk interface** This interface handles VM traffic on-premises for the extended networks by using a translational bridge mapping to a corresponding stretched network in {{site.data.keyword.cloud_notm}}.
* **Uplink interface** HCX uses this interface to send encapsulated overlay traffic to and from {{site.data.keyword.cloud_notm}}. Application data travels through the Uplink interface.

### Deployment architecture
{: #vc_trial_hcx_arch-deployment}

For information about HCX on {{site.data.keyword.cloud_notm}} deployment, see [VMware HCX on {{site.data.keyword.cloud_notm}}
Deployment and Operations](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf).
