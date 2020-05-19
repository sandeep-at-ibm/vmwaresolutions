---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-29"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud for VMware Solutions and Red Hat OpenShift overview
{: #openshift-runbook-runbook-intro}

The {{site.data.keyword.vmwaresolutions_full}} offering includes fully automated, rapid deployments of VMware vCenter Server in the IBM Cloud. These offerings complement the on-premises infrastructure and allow existing and future workloads to run in the IBM Cloud without conversion by using the same tools, skills, and processes they use on-premises. For more information, see [Virtualization for extending virtualized private cloud](https://www.ibm.com/cloud/architecture/architectures/virtualizationArchitecture){:external}.

Red Hat OpenShift for VMware Solutions is a reference architecture and a manual build process to deploy a Red Hat OpenShift Cluster 4.2 on to an existing vCenter Server instance. The components of Red Hat OpenShift Cluster are deployed as virtual machines and appliances by using NSX software defined networking.

* Reference Architecture - [VMware vCenter Server and Red Hat OpenShift architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-vcs-openshift-intro)
* Build Process - This document. The process and steps that are needed to install Red Hat OpenShift 4.2 on to an existing vCenter Server instance.

![IBM Cloud for VMware Solutions and Red Hat OpenShift](../../images/openshift-sddc.svg "IBM Cloud for VMware Solutions and Red Hat OpenShift"){: caption="Figure 1. IBM Cloud for VMware Solutions and OpenShift" caption-side="bottom"}

## Red Hat OpenShift overview
{: #openshift-runbook-runbook-intro-rhos-overview}

The Red Hat Open Shift platform is a platform that is designed to orchestrate containerized workloads across a cluster of nodes. The platform uses Kubernetes as the core container orchestration engine, which manages the Docker container images and their lifecycle.

The nodes operating system is Red Hat Enterprise Linux CoreOS, which is the container host version of Red Hat Enterprise Linux (RHEL) and features a RHEL kernel with SELinux enabled by default. RHEL CoreOS includes; kubelet, which is the Kubernetes node agent, and the CRI-O container runtime, which is optimized for Kubernetes. In v4.2, you must use RHEL CoreOS for all control plane machines, but you can use Red Hat Enterprise Linux (RHEL) as the operating system for compute, or worker machines. If you choose to use RHEL workers, you must perform more system maintenance than if you use RHEL CoreOS for all of the cluster machines. The reference architecture and this build process use RHEL CoreOS. The nodes must have direct internet access to:

* Access the OpenShift Infrastructure Providers page to download the installation program.
* Access quay.io to obtain the packages that are required to install the cluster.
* Obtain the packages that are required to perform cluster updates.
* Access Red Hat’s software as a service page to perform subscription management.

In the reference architecture, there are the following components that are installed and configured in this build process:

* Bastion node - This RHEL VM acts as a "jump-server" on the overlay network to enable the build process. It is accessed via SSH via the private network. It also hosts a webserver to help the build process of the cluster.
* Bootstrap node - As each node in the cluster requires information about the cluster when it is provisioned, a temporary bootstrap node is used. The bootstrap node creates the master nodes that make up the control plane. The control plane nodes then create the worker nodes. After the cluster initializes, the bootstrap node can be destroyed.
* Control-plane nodes - These nodes run services that are required to control the Kubernetes cluster. They contain more than just the Kubernetes services for managing the cluster. The terms "master" and "control-plane" are used interchangeably.
* Compute nodes - In a Kubernetes cluster, the compute nodes are where the workloads are run. The compute nodes advertise their capacity to the control-plane nodes.
* DNS - A correct DNS setup is imperative for a functioning OpenShift cluster. The vCenter Server instance AD DNS server to host the required DNS records.
* Load-balancer - An NSX ESG load-balancer service is used to front end the Red OpenShift APIs, both internal and external, and the OpenShift router. The load balancer is configured so that Port 6443 and 22623 point to the bootstrap and master nodes, while ports 80 and 443 are configured to point to the worker nodes.
* Webserver - A web server is needed to hold the ignition configurations and installation images for the installation of RHEL CoreOS. NGINX is installed on the bastion node to provide this function.
* Persistent Storage - To support the persistent storage requirements the vSphere Cloud Provider is used to provide storage volumes up to the OpenShift platform backed by any supported vSphere datastore that is, VMware vSAN, NFS, or iSCSI. While there are two ways to deliver storage to OpenShift - static provisioning or dynamic provisioning, the preferred method is to use dynamic provisioning. Dynamic provisioning automatically triggers the creation of the persistent volume and its backend VMDK file. For dynamic provisioning a default StorageClass for the OpenShift cluster is defined and a PersistentVolumeClaim in Kubernetes is created.

Access to the environment for this build process is via a "jump-server" or remote device:
* You can have a Microsoft Windows or Linux Virtual Server Instance (VSI) installed alongside your vCenter Server instance to provide administrative access to the environment. This VSI has internet access for the remote connection to the server and for downloading files. It also has private network access for connecting to vCenter and to the bastion node.
* You can have a remote device, laptop/desktop, connected via the IBM Cloud SSL VPN to the IBM Cloud Private network. This remote device has access to the internet to download the required files and can connect to vCenter and the bastion node via the SSL VPN.

## Scripts overview
{: #openshift-runbook-runbook-intro-scripts-overview}

This build process uses the following scripting tools and scripts:

* govc -  govc is a vSphere CLI and pre-compiled for Linux, OSX, and Windows. It is useful to complete various vCenter/vSphere operations from the command line interface. It is used in this process to:
  * Upload the ISO and OVA files to a vSphere datastore.
  * Create a persistent volume for the Red Hat OpenShift cluster to use.
* Red Hat Installer - the installer creates the Ignition files that are used by terraform. Ignition is a first boot installer and configuration tool that is designed specifically for CoreOS Container Linux to partition disks, format partitions, writing files and configuring users. On first boot, Ignition reads its configuration from a remote URL and applies the configuration to the VM.
* Terraform - Terraform is a tool that codifies APIs into declarative configuration files. It uses a "provider" to interact with the infrastructure. A `.tf` file is used to describe the infrastructure as code. A .tvars file is used to store the variables for the deployment. The main.tf file holds the build instructions.
* PowerShell is used on the AD DNS server to create the DNS entries.
* PowerShell Core is available for Windows, Linux, and macOS systems. Review the information at [PowerShell Core](https://github.com/PowerShell/PowerShell){:external} for further information. This is an optional tool that is used on the jump-server or remote device to enable the use of PowerCLI.
* PowerCLI - PowerCLI is a PowerShell interface for managing VMware vSphere that lets you automate all aspects of vSphere management, including network, storage, VMs, and guest OS. Review [Install PowerCLI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.install.doc/GUID-F02D0C2D-B226-4908-9E5C-2E783D41FE2D.html){:external} to understand how to install this tool. This is an optional tool that is used on the jump-server or remote device to help the preparation of the vCenter Server instance. These steps can be done manually via the GUI.
* PowerNSX - PowerNSX is a PowerShell module that abstracts the VMware NSX API to a set of easily used PowerShell functions. Review the documentation at [PowerNSX](https://github.com/vmware/powernsx){:external} for further information. This is an optional tool that is used on the jump-server or remote device to help the preparation of NSX on the vCenter Server instance. These steps can be done manually via the GUI.

## Build process overview
{: #openshift-runbook-runbook-intro-build-process-overview}

This documentation describes the process to install Red Hat OpenShift v4.2 on to an existing vCenter Server instance. The process installs and configures:

* One bastion node.
* One bootstrap node.
* Three control plane nodes.
* Three worker nodes.

The deployment approach is best described in the following phases:

* Phase 1 - vCenter Server instance preparation:
  * Using the IBM Cloud for VMware Solutions console, [order a vCenter Server instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance), which can include NFS storage or vSAN. If you have an existing instance with enough capacity, this can be used. This step is not described in this document.
  * Using the IBM Cloud console, [order more private and public subnets](/docs/subnets?topic=subnets-getting-started#ordering-subnets) to be used by the OpenShift cluster
  * Download RHEL 7.6 ISO for the OS of the bastion/deployment node and the Red Hat Enterprise Linux CoreOS (RHCOS) OVA image. This step is described in [Prerequisites for installation](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-prereq-intro).
  * Using govc, the OVA and ISO are uploaded to a datastore on the vCenter Server instance. This step is described in [Prerequisites for installation](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-prereq-intro).
  * Add logical switches - Two logical switches are created; OpenShift-LS the network the OpenShift VMs are deployed onto and OpenShift-DLR-Transit, the uplink between the DLR and the Edge.
  * Add an ESG - An external services gateway (ESG) is a virtual appliance that provides North-South routing, and other network functions. In this architecture, the ESG is used for; routing, NAT, firewall, and load-balancing. As the ESGs are configured as active/passive pair, DRS anti-affinity rules are used to ensure that NSX Edges do not run on the same host. Static routes are used to direct traffic to either the internet or the IBM private Network. This step is described in [OpenShift NSX Edge configuration](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-nsxedge-intro).
  * Add a DLR - A distributed logical router (DLR) is a virtual appliance that contains the routing control plane, while distributing the data plane in kernel modules to each hypervisor host. The DLR provides East-West distributed routing and is the default gateway for the OpenShift VMs that will be installed on the OpenShift logical switch. The NSX DLR virtual machines are configured as an Active/Passive pair, and vSphere Distributed Resource Scheduler (DRS) anti-affinity rules are created to ensure that the DLR VMs do not run on the same host. This step is described in [OpenShift NSX DLR configuration](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-nsxdlr-intro).
  * Update DNS - The infrastructure DNS, provisioned with the vCS instance is updated with the names and IP addresses for the OpenShift components by using a PowerShell script. This step is described in [IBM Cloud for VMware Solutions DNS configuration](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-dns-intro).
* Phase 2 - Red Hat OpenShift installation. These steps are described in [Red Hat OpenShift 4.2 user provider infrastructure installation](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-install-intro).
  * A Red Hat virtual machine, the bastion node, is provisioned to run the OpenShift installer and to host an HTTP Server. It is registered with Red Hat by using your subscription, and the OpenShift installer is downloaded.
  * On the bastion node, the install-config.yaml is populated with the required OpenShift parameters and OpenShift Ignition is used to generate a number of files used for the installation of the bootstrap, master, and worker machines.
  * Terraform, on the bastion node, uses the files that are created by Ignition to create the OpenShift VMs.
* Phase 3 - Post deployment activities:
  * Configure a persistent volume for use by the OpenShift cluster. This step is described in [Red Hat OpenShift 4.2 additional configuration](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-config-intro).

**Next topic:** [Prerequisites for installation](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-prereq-intro)

## Related links
{: #vcs-openshift-runbook-intro-related}

* [An overview of the basics of Red Hat OpenShift](https://www.ibm.com/cloud/blog/new-builders/what-is-openshift){:external}
* [OpenShift 4 User Provisioned Infrastructure with VMware vSphere](https://www.youtube.com/watch?v=TsAJEEDv-gg){:external}
* [OpenShift 4 Release Update](https://www.youtube.com/watch?v=YJvTu8jC6CU){:external}
* [Installing a cluster on vSphere](https://docs.openshift.com/container-platform/4.2/installing/installing_vsphere/installing-vsphere.html#installation-dns-user-infra_installing-vsphere){:external}
* [IBM Cloud VPN getting started](/docs/iaas-vpn?topic=iaas-vpn-getting-started)
* [OpenShift cheat sheet](https://cheatsheet.dennyzhang.com/cheatsheet-openshift-a4){:external}
