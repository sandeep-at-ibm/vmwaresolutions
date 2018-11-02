---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Architecture overview

This section provides more details about the network architecture that is used in this reference architecture. It consists of the following sections:
* **VCS overview** – This section describes the highlights of the VCS platform.
* **Network overview** – These sections provide information on the network components that are used in this reference architecture:
  - **IBM Cloud networking** – IBM Cloud provides the physical network and is fully managed by IBM Cloud. This network has some key characteristics that need to be understood to understand network flows between on and off premise and between workloads that are hosted in different services.
  - **NSX-V** – VCS networking builds upon the IBM Cloud network with an overlay that is provided by VMware NSX-V. This overlay segments traffic from the IBM Cloud underlay network allowing greater control and configurability including BYOIP.
  - **IBM Kubernetes Service** - IKS uses Calico as its Container Network Interface plug-in.
  - **IBM Cloud Private** - ICP uses Calico as its Container Network Interface plug-in.

* **Integration** – This section describes the architecture of the networking components to allow the required network traffic flows and addressing:
  - IP address allocation
  - Network traffic flows

## VCS overview

VMware vCenter Server on IBM Cloud with Hybridity Bundle (VCS) is a hosted private cloud that helps you to quickly and easily extend your on-premises infrastructure into the cloud for secure and seamless infrastructure hybridity and true application mobility.

The VCS Hybridity Bundle is deployed on top of a minimum of four IBM Cloud Bare Metal Servers, offers dedicated storage via a virtual storage area network (VSAN), and includes the automatic deployment and configuration of an easy-to-manage software-defined networking infrastructure (NSX-V). The VCS Hybridity Bundle is a reference architecture that is deployed via automation, which ensures consistency, performance, and compliance. In many cases, the entire environment can be provisioned in less than a day and the bare metal infrastructure can rapidly and elastically scale the compute and storage capacity up and down as needed.

Many options are available to enhance and extend the VCS Hybridity Bundle. IBM Cloud service offerings not only include add on storage options and various public and private WAN connectivity options, but also cover areas from platform security, network security, traffic load balancing to back up and disaster recovery.

Platform security services include HyTrust CloudControl on IBM Cloud, which provides automated security and compliance support, enabling better visibility and control over your cloud environment and administrators. HyTrust DataControl on IBM Cloud delivers data protection with powerful encryption and scalable key management to secure your workloads throughout their lifecycles. IBM Cloud Secure Virtualization simplifies compliance and protects your data with encryption, geo-fencing policies and role-based access controls, while KMIP for VMware on IBM Cloud an encryption key lifecycle management offering manages the encryption keys used by IBM Cloud services or customer built-in applications.

Network security options are the FortiGate Security Appliance on IBM Cloud that provisions a highly available pair of FortiGate Security Appliance devices to analyze network traffic and protect your virtual infrastructure and the FortiGate Virtual Appliance on IBM Cloud, which deploys a high availability pair of FortiGate VMs on IBM Cloud to reduce risk by implementing critical security controls within your virtual infrastructure. Additional network security offerings are in development.

The F5 on IBM Cloud network load balancer service offering optimizes performance and ensures the availability and security of your most critical applications with the F5 BIG-IP suite.

Back up and disaster recovery offerings from IBM, Veeam, and Zerto deliver peace of mind and operational continuity if disaster occurs. IBM Spectrum Protect Plus on IBM Cloud is a data protection and availability solution for virtual environments. Veeam on IBM Cloud enables availability for the Always-On Enterprise™ with integrated backup, recovery and replication on IBM Cloud. Zerto on IBM Cloud provides on-premises and IBM Cloud customers with a secure, flexible, and scalable Disaster Recovery solution.

IBM Cloud VCS Hybridity Bundle is not a managed service, though you can add IBM-Managed Services to offload the day-to-day operations and maintenance of the virtualization, guest OS or application layers. The IBM Cloud Professional Services team is also available to help you accelerate your journey to the cloud with migration, implementation, planning, and onboarding services.

Platform integration options of the VCS Hybridity Bundle are not limited to options available from VMware such as vRealize Suite or vSphere with Operations Management, but span multiple IBM Cloud service offerings such as [vCenter Server and IBM Kubernetes](../vcsiks/vcsiks-intro.html) and [vCenter Server and IBM Cloud Private](../vcsicp/vcsicp-intro.html), which use open source Terraform to manage and deliver infrastructure as code.

The extensive portfolio of services and multi-offering integration options available for the VCS Hybridity Bundle deliver a truly hybrid platform making Hybridity as a Service possible.

### Related Links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
