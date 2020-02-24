---

copyright:

  years:  2016, 2020

lastupdated: "2020-02-21"

keywords: single-node trial, migration app modernization, tech specs migration app modernization

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial for Migration and App Modernization overview
{: #cloud_modern_bundle_overview}

The Single-node Trial for Migration and App Modernization provides the option to test drive {{site.data.keyword.cloud}} to migrate VMware workloads to the {{site.data.keyword.cloud_notm}} and then modernize simple workloads by using containers. This offering is a trial version of Red Hat OpenShift for VMware. It provides the Kubernetes management platform for containers and the single-tenant VMware platform, which you can manage by using the same tools as in on-premises environments. You can take advantage of the speed and scale of the cloud while you maintain the same level of control and visibility that is provided on-premises.
{: shortdesc}

The trial is designed for migration of up to 20 simple development or test workloads by using vCenter Server and containerization of those workloads with the Kubernetes-based OpenShift application development platform. Automation installs and configures VMware HCX in the {{site.data.keyword.cloud_notm}}, provides an on-premises HCX activation key, and installs and configures a small development and test topology of Red Hat OpenShift in a matter of hours.

The Single-node Trial for Migration and App Modernization is for proof of concept (POC) only. Do not run production workloads on this environment. Management functions such as adding and removing hosts and clusters, ordering add-on services, and applying updates are not supported.
{:important}

To get the most out of the Single-node Trial instance, you can use on demand consulting and expert services to help you migrate your VMware workloads to the {{site.data.keyword.cloud_notm}}. For more information, see:

* [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:external}
* [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:external}

Additionally, [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:external} can help you accelerate application modernization through the latest cloud native practices.

This trial is intended for use up to 90 days. When you are finished with the trial, you can delete this environment and provision a new environment that meets your capacity needs.
{:note}

## Technical specifications for Single-node Trial for Migration and App Modernization instances
{: #cloud_modern_bundle_overview-tech-specs}

The following components are included in your Single-node Trial for Migration and App Modernization instance.

The availability and pricing of standardized hardware configurations might vary based on the {{site.data.keyword.CloudDataCent_notm}} that is selected for deployment.
{:note}

### Bare Metal Server
{: #cloud_modern_bundle_overview-bare-metal}

Dual Intel Xeon Gold 5120 processor / 28 cores total, 2.2 GHz with 384 GB RAM) for up to about 20 virtual machines (VMs).

#### CPU over-commits
{: #cloud_modern_bundle_overview-cpu}

* 16:1 CPU over-commits for vCenter Server management, HCX, and 20 customer workload VMs
* 3:1 CPU over-commits for Red Hat OpenShift

#### RAM over-commits
{: #cloud_modern_bundle_overview-ram}

* 1.22:1 RAM over-commits for a customer deployment of 20 workload VMs with 8 GB each
* 1:1 (no over-commit) for a customer deployment of nine workload VMs with 8 GB each

### NFS storage
{: #cloud_modern_bundle_overview-nfs-storage}

* 2 TB for management
* 1 TB for customer workload (for 20 customer VMs)
* 2 TB for Red Hat OpenShift

### Networking specifications for Single-node Trial for Migration and App Modernization instances
{: #cloud_modern_bundle_overview-networking-specs}

The following networking components are ordered:
*  10 Gbps dual public and private network uplinks
*  Three VLANs (Virtual LANs): one public VLAN and two private VLANs
*  One VXLAN (Virtual eXtensible LAN) with DLR (Distributed Logical Router) for potential east-west communication between local workloads that are connected to layer 2 (L2) networks. The VXLAN is deployed as a sample routing topology, which you can modify, build on it, or remove it. You can also add security zones by attaching more VXLANs to new logical interfaces on the DLR.
*  Two VMware NSX Edge Services Gateways:
  * A secure management services VMware NSX Edge Services Gateway (ESG) for outbound HTTPS management traffic, which is deployed by IBM as part of the management networking typology. This ESG is used by the IBM management VMs to communicate with specific external IBM management components that are related to automation.

    This ESG is not accessible to you and you cannot use it. If you modify it, you might not be able to manage the Single-node Trial for Migration and App Modernization instance from the {{site.data.keyword.vmwaresolutions_short}} console. In addition, by using a firewall or disabling the ESG communications to the external IBM management components cause {{site.data.keyword.vmwaresolutions_short}} to become unusable.
    {:important}
  * A secure customer-managed VMware NSX Edge Services Gateway (ESG) for outbound and inbound HTTPS workload traffic. The ESG is deployed by IBM as a template that you can modify to provide VPN access or public access.

### Virtual Server Instances
{: #cloud_modern_bundle_overview-vsi}

The following virtual server instances (VSIs) are ordered:

* A VSI for IBM CloudBuilder, which is cancelled after the instance deployment is completed.
* A Microsoft Windows Server VSI for Microsoft Active Directory (AD) is deployed and can be looked up. The VSI functions as the DNS for the instance where the hosts and VMs are registered.

### IBM-provided licenses and fees
{: #cloud_modern_bundle_overview-license-and-fee}

The following licenses are included with your Single-node Trial for Migration and App Modernization instance order:

* VMware vSphere Enterprise Plus 6.7u2
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4
* Red Hat OpenShift for VMware 4.2

Single-node Trial for Migration and App Modernization instances do not support Bring Your Own License (BYOL).
{:note}

## Technical specifications for HCX
{: #cloud_modern_bundle_overview-hcx-tech-specs}

The Single-node Trial for Migration and App Modernization includes HCX. The following components are ordered and included in the HCX service.

On-premises HCX instances include only licensing and activation.
{:note}

### An active-passive pair of VMware NSX Edge Services Gateways for HCX Management
{: #cloud_modern_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Disk: 3 GB VMDK

### HCX Management Appliance - virtual machine
{: #cloud_modern_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Disk: 60 GB VMDK

More HCX appliances are deployed during configuration as necessary for L2 connectivity, WAN optimization, and gateway connections.

### Networking specifications for HCX
{: #cloud_modern_bundle_overview-hcx-networking-specs}

* One public portable subnet with 16 IP addresses
* Two private portable subnets with 64 IP addresses
* Eight IP addresses from private portable vMotion subnet

## Technical specifications for Red Hat OpenShift
{: #cloud_modern_bundle_overview-icp-tech-specs}

Red Hat OpenShift for VMware 4.2 is installed by using the Development and Test topology on all Single-node Trial for Migration and App Modernization instances. For more information about Red Hat OpenShift, see [Red Hat OpenShift for VMware overview](/docs/services/vmwaresolutions?topic=vmware-solutions-ocp_overview).

## Related links
{: #cloud_modern_bundle_overview-related}

* [VMware HCX resources](https://hcx.vmware.com/#/docs){:external}
* [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
