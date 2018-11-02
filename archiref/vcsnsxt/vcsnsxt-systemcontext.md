---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# System context
The system context diagram defines the key elements of a system, the boundary of the system and the entities that interact with it along with the interactions. It is a high-level diagram that provides the reader with an initial view of the system.

Figure 1. System context
![System context diagram](vcsnsxt-networking.svg)

The four core components, from a network perspective, are as follows:
- **On-premises virtualization** - a VMware environment that is hosted on the client’s premises or a third party and currently hosts the VMs running the applications to be modernized. It is the source environment for VM migrations and is loosely coupled to IBM Cloud via VMware HCX.
- **vCenter Server** – an IBM Cloud for VMware Solutions instance that is the target for migrated VMs from the on-premises environment. Together with the on-premises virtualization it forms a hybrid environment that allows VMs to move seamlessly from one environment to the other.
- **IBM Cloud Kubernetes Service** - it uses Kubernetes as the container orchestration solution. IBM operates and manages the Kubernetes master node while the worker nodes are deployed to customer-managed infrastructure. IBM provides management tools for operating system patch deployment, Docker engine upgrades, and new Kubernetes versions. The IBM Kubernetes Service provides an isolated and secure platform for managing containers that is portable, extensible, and self-healing in case of failovers.
- **IBM Cloud Private** - an application platform for developing and managing containerized applications. It is an integrated environment that includes the container orchestrator Kubernetes, a private image repository, a management console, monitoring frameworks and a graphical user interface, which provides a centralized location from where you can deploy, manage, monitor, and scale applications.
-	**IBM Cloud Services** - a wide range of services available from IBM Cloud that are consumable. Service options include analytics, AI, and IoT as examples.

## Actors

The system context diagram identifies the following actors.

Table 1. Actors

Actor  |  Description
---|---
System Administrator |The system administrators are the enterprise VMware resources who use vCenter and the HCX plug-in. They identify candidates for migration, stretch networks, migrate VMs and manage NSX-V. They use the IBM Cloud console to provision VCS instances and to scale capacity.
Developer	| The developers are the enterprise skilled container resources who use the IKS/ICP/CAM consoles and APIs to create and manage containers. They create the new services as part of application modernization.
Enterprise User | This enterprise resource requires network access to the applications to carry out business processes such as updating content.
Customer | The customer is an external actor who wants to consume services from the enterprise. In the case of Acme Skateboards, it is a skater who wants to purchase skating products. The Customer requires secure internet access to the catalog.
IBM IKS | This is an IBM resource who manages the IKS Master Node of the service.

## Systems

The system context diagram identifies the following systems.

Table 2. Systems

Actor | Description
---|---
vCenter | The vCenter is the primary interface for the system administrator to manage the on-premises VMs and access the HCX plug-in to stretch networks and migrate VMs. With vCenter Server with Hybridity Bundle the systems administrator can seamlessly integrate on-premises vSphere networks into the VCS instance running on IBM Cloud. Hybrid networking extends the on-premises networks into the IBM Cloud allowing customers to migrate their applications into a VCS instance running on IBM Cloud and back to on-premises if required. For more details on the vCenter Server with Hybridity Bundle refer to the [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) document.
On-premise VMs | The on-premises VMs host the applications migrating to the cloud. Initially, they are migrated as VMs and then via the application modernization journey migrated from VMs to containers.
On cloud VMs | On cloud VMs host applications that were migrated from on-premises. They communicate with on-premises applications via the stretched L2 network. In the case of this reference architecture and in this example for Acme Skateboards, one of the on cloud VMs is a database server, which is part of the online presence workload.
NSX-V | NSX-V on VCS provides the software defined overlay network that is managed by the system administrator. The overlay network is the target for HCX stretched networks as handles traffic from the VMs for ICP. NSX-V provides the reference architecture with features such as deployment, reconfiguration, and destruction of on-demand virtual networks and micro-segmentation services within VMware using vSphere distributed switches (vDS). For more information, see [NSX–V overview](vcsnsxt-overview-ic4vnsxv.html).
CAM | IBM Cloud Automation Manager (CAM) runs on ICP and provides a single pane of glass to provision VM-based workloads alongside Kubernetes based workloads by simply using templates. CAM allows the developer to: <br> - Provision workloads on VCS, ICP, or IKS.<br> - Compose and orchestrate services that are made out of both VMs and containers. <br> - Integrate their DevOps toolchains and day-2 ITSM solution.
Containerized Applications | These are the apps that went through the application modernization journey and are now running as containers. In the case of this reference architecture and in this example for Acme Skateboards, one of the containerized apps is a web server, which is part of the online presence workload.
Watson | In the case of this reference architecture and in this example for Acme Skateboards, Watson represents the AI service that is used in the “Concept Car” architecture.

### Related Links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
