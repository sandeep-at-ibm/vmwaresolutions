---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

# System context

Figure 1. System context diagram
![System context diagram - VCS ICP CAM](vcsicp-syscontext-vcs-icp-cam.svg)

The four core components are as follows:

- **On-premises virtualization** – This component is a VMware environment hosted on the client’s premises or a third-party location and currently hosts the VMs running the applications to be modernized. It is the source environment for VM migrations and is loosely coupled to an IBM Cloud instance via VMware Hybridity (HCX).
- **vCenter Server** – VMware vCenter Server on IBM Cloud (VCS) is an IBM Cloud for VMware Services instance that is the target for migrated VMs from the on-premises environment. Together with the on-premises virtualized environment it forms a hybrid environment enabling VMs to move from one site to the other.
- **IBM Cloud Kubernetes Service** - IKS leverages Kubernetes as the container orchestration solution. IBM operates and manages the Kubernetes master node while the worker nodes are deployed to customer-managed infrastructure. IBM provides management tools for operating system patch deployment, Docker engine upgrades, and new Kubernetes versions. IKS provides an isolated and secure platform for managing containers that is portable, extensible, and self-healing in case of failovers.
- **IBM Cloud Private** - ICP is an application platform for developing and managing containerized applications. It is an integrated environment that includes the container orchestrator Kubernetes, a private image repository, a management console, monitoring frameworks and a graphical user interface, which provides a centralized location from where you can deploy, manage, monitor, and scale applications.
- **IBM Cloud Automation Manager** – CAM, is an enterprise ready infrastructure as code (IaC) platform that provides a single pane of glass to provision VMware based workloads alongside Kubernetes based workloads. Automation of workload provisioning, whether virtual machines and/or containers and their infrastructure prerequisites are enabled via CAM.
- **IBM Multi Cloud Manager** – MCM provides user visibility, application-centric management (policy, deployments, health, operations), and policy-based compliance across clouds and clusters. With MCM, you have control of your Kubernetes clusters.
- **IBM Cloud Services** – IBM Cloud Services are a wide range of consumable services available including analytics, AI, and IoT offerings.

## Actors

Table 1. Actors

Actor  | Description
--|--
System Administrator | VMware vSphere skilled resource who uses vCenter Server to manage the on-premises virtualization and the VCS instance.
Developer | Container skilled resource who uses the CAM console to create and manage containers. They create the new services as part of application modernization. Using CAM the developer provisions workloads on VCS, ICP or IKS, composes and orchestrates services that are built with VMs and containers, and integrates DevOps toolchains and day-2 ITSM solutions.
Customer | External actor who consumes services from the enterprise. For Acme Skateboards, the customer is a skater who wants to purchase skateboarding products. The customer requires secure internet access to the catalog.
IBM IKS | IBM resource managing the IKS Master Node for the service.

## Systems

Table 2. Systems

Actor  | Description
--|--
vCenter Server | Primary interface the system administrator uses to manage both the on-premises VMs and the IBM Cloud VMs in the VCS instance.
On-premise VMs| Virtualized servers hosting the applications targeted for migration into IBM cloud. Initially migrated as VMs and refactored from VMs to containers for application modernization.
IBM Cloud VMs |  Virtualized servers hosting the applications migrated from the on-premises data center. In the case of this reference architecture and for Acme Skateboards, one of the IBM Cloud VMs is a database server, which is part of the online presence workload.
Enterprise Content catalog | Centralized location from which you can browse for and install packages in your cluster. The catalog contains a number of IBM packages that are used to create containers as well as access to Helm charts. Helm is a tool for managing Kubernetes charts. Charts are packages of preconfigured Kubernetes resources that makes it easy to version, package, release, deploy, delete, upgrade and even rollback container deployments. Helm is the Kubernetes native package management system, and is used for application management inside an ICP cluster.
Core Operational Services |  ICP includes a number of tools to collect, store, and query logs and metrics. These tools provide a centralized store for all logs and metrics and deliver improved performance and increased stability when accessing and querying logs and metrics.
Management Console |  The ICP management console allows you to manage, monitor, and troubleshoot your applications and cluster from a single, centralized, and secure management console.
Terraform |  Handles the provisioning of cloud and infrastructure resources using providers such as VMware vSphere, IBM Cloud, Microsoft Azure, Amazon Web Services, Google Cloud Platform, and OpenStack.
HELM |  Package manager for Kubernetes. Helm charts are used to define Kubernetes resources and deploy applications.
Chef |  Responsible for configuration management and compliance automation. Chef deploys and configures middleware and applications after Terraform has completed initial provisioning.
Services |  Represents the Service Composer, which is where administrators author, compose and design services constructed from Kubernetes resources and one or more VMs.
Containerized applications |  Applications that completed the application modernization journey and are now running as containers. In the case of this reference architecture and for Acme Skateboards, one of the containerized applications is a web server, which is part of the online presence workload.
Watson |  In the case of this reference architecture and Acme Skateboards, Watson represents the AI service used in the “Concept Car” architecture.

Application migration, networking, and security often are the most challenging aspects of application modernization. VMware vCenter Server on IBM Cloud, VMware Hybridity, VMware NSX, IBM Cloud Private, and the IBM Cloud Kubernetes Service address these challenges and enable you to build resilient, secure, and robust modern applications.

### Related links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
