---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Application modernization overview

The following diagram shows the application modernization reference architecture that Acme Skateboards deploy and is described in depth in this series of documents.

Figure 1. Architecture overview
![Architecture overview diagram](vcsnsxt-aod.svg)

This hybrid architecture allows Acme Skateboards to:
- Migrate VMware VMs from on-premises to IBM Cloud with little or no downtime and no application reconfiguration.
-	Enable them to start the application modernization journey by allowing them to focus on containerizing the simpler web interfaces and middleware while allowing more complex databases to remain as VMs.
-	Leverage Cloud Automation Manager (CAM) to script Infrastructure as code (IaC) to compose and orchestrate services that are made from both VMs and containers, to integrate with their DevOps toolchains and their ITSM solution.

Focusing on the network architecture, the reference architecture has the following key components:
- **On-premise virtualization** – This is a VMware cluster that currently hosts the Acme Skateboards VMs. It is these VMs that are currently hosting the applications that will be modernized. This cluster is required to meet the prerequisites as documented in the [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) document so that it can run HCX. HCX extends the on-premises networks into the IBM Cloud allowing customers to migrate VMs into the VCS instance running on IBM Cloud, and back if required.
- **VMware vCenter Server on IBM Cloud** – VCS provides the fundamental VMware building blocks: vSphere, vCenter Server, NSX-V, and storage options including vSAN or IBM Cloud Endurance storage, needed to automatically deploy a VMware Software Defined Data Center (SDDC) solution. This VMware cluster is the target of the migrated VMs as well as some of the modernized applications in containers hosted in ICP.

  Key components of the architecture are:
 - **NSX-V** - NSX-V provides the network virtualization layer in VCS that provides a network overlay for Acme Skateboards VMs. NSX-V enables BYOIP and isolates the workload networks from the IBM Cloud networks. NSX-V is programmed by HCX to create the networks that Acme Skateboards will extend from on-premises.
 - **IBM Cloud Private** - ICP is an application platform for developing and managing containerized applications. It is an integrated environment that includes the container orchestrator Kubernetes, a private image repository, a management console, monitoring frameworks and a graphical user interface that provides a centralized location from where Acme Skateboards can deploy, manage, monitor, and scale their applications. The VCS instance hosts the ICP components, master nodes, worker nodes and so on, running them as VMs.
  -	**IBM Cloud Automation Manager** – CAM is an enterprise ready infrastructure as code (IaC) platform that provides a single pane of glass to provision virtual machine-based workloads alongside Kubernetes based workloads by simply using templates. CAM is a Dockerized application that runs on top of ICP and is tightly integrated for authorization, RBAC, and other functions.
  - **IBM Kubernetes Service** – IKS enables Acme Skateboards to deploy their modernized applications in Docker containers that run in Kubernetes clusters. The master modes are fully managed by IBM while the worker nodes in the worker pool are deployed into the same IBM Cloud account as their VCS instance. Worker nodes are bare metal, public, or dedicated virtual server instances. Calico is installed and configured automatically in IKS. Calico provides secure network connectivity for containers and is configured in IKS to use IP-in-IP encapsulation to encapsulate packets traveling across subnets and uses NAT for outgoing connections from the containers.
  - **Direct Link** – IBM Cloud Direct Link uses Acme Skateboard’s WAN provider to connect their data center to IBM Cloud providing a reliable, low latency, secure network connection. This connection provides:
      - Access to the cloud hosted applications from your Enterprise users.
      - Inter VM traffic between on-premises VMs and cloud VMs.
      - Traffic between legacy systems in the on-premises data center and cloud VMs.

## Key benefits to Acme Skateboards

-	Accelerated delivery of IT projects to developers and lines of business by reducing the time that it takes for procurement, architecture, implementation, and deployment of resources from weeks or even months, to hours. Waiting on networking or security teams to provision services like load balancers, firewalls, switches, and routers decrease their time to value.
-	Enhanced security with dedicated bare metal servers in a hosted private cloud, including private endpoint deployment to IBM Cloud services such as IKS and KMIP.
-	Consistent management and governance of the deployed hybrid cloud by providing full administrative access to virtualization management, thus preserving your existing VMware tools, scripts, and investments in training.
-	VMware expertise at global scale with IBM Professional and Managed Services spanning 30+ IBM Cloud data centers worldwide.

Customers moving toward cloud native application platforms such as ICP and IKS are focused on speed and innovation and don’t always have security and networking in mind. This reference architecture shows how VCS, ICP, and IKS securely move Acme Skateboards along the application modernization journey.

## Related Links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
