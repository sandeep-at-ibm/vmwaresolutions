---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# VMware Federal on IBM Cloud overview

VMware Federal on {{site.data.keyword.cloud}} provides support for ordering a base vCenter Server instance in addition to providing US Federal Government agencies with the option to secure the deployed vCenter Server instances. Selecting the option to secure the deployed instances removes sensitive information stored about the instance and removes the open management connection for ongoing access to the instance for management functions, such as adding and removing hosts and clusters. After selecting the secure option, all management functions are disabled except for a full instance delete.

For more information about vCenter Server on {{site.data.keyword.cloud_notm}} and the vCenter Server architecture, see [vCenter Server overview](vc_vcenterserveroverview.html).

**Attention:** VMware Federal on {{site.data.keyword.cloud_notm}} offers only a subset of the vCenter Server offerings. Multi-site configuration, preconfigured {{site.data.keyword.cloud_notm}} Bare Metal Servers, Bring Your Own License, and the option to order additional services are not supported.

## Technical specifications for VMware Federal on IBM Cloud instances

The following components are included:

### Bare Metal Server

You can order two or more customized {{site.data.keyword.baremetal_short}} with one of the following configurations:

* 2-CPU Intel Broadwell generation (Intel Xeon E5-2600 v4 series)
* 2-CPU Intel Skylake generation (Intel Xeon 4100/5100/6100 series)

For NFS storage configuration, the recommended number of {{site.data.keyword.baremetal_short}} is set to the default of three.

**Note:** If you select vSAN storage, the configuration requires four {{site.data.keyword.baremetal_short}}.

### Networking

The following networking components are ordered:
*  Three VLANs (Virtual LANs): one public VLAN and two private VLANs
*  One VXLAN (Virtual eXtensible LAN) with DLR (Distributed Logical Router) for potential east-west communication between local workloads that are connected to layer 2 (L2) networks. The VXLAN is deployed as a sample routing topology, which you can modify, build on it, or remove it. You can also add security zones by attaching additional VXLANs to new logical interfaces on the DLR.
*  Two VMware NSX Edge Services Gateways:
  * A secure management services VMware NSX Edge Services Gateway (ESG) for outbound HTTPS management traffic, which is deployed by IBM as part of the management networking typology. This ESG is used by the IBM management virtual machines to communicate with specific external IBM management components that are related to automation. For more information, see [Configuring your network to use the customer-managed ESG](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    **Important**: This ESG is not accessible to you and you cannot use it. If you modify it, you might not be able to manage the vCenter Server instance from the {{site.data.keyword.vmwaresolutions_short}} console. In addition, note that using a firewall or disabling the ESG communications to the external IBM management components will cause {{site.data.keyword.vmwaresolutions_short}} to become unusable.
  * A secure customer-managed VMware NSX Edge Services Gateway for outbound and inbound HTTPS workload traffic, which is deployed by IBM as a template that can be modified by you to provide VPN access or public access. For more information, see [Does the customer-managed NSX Edge pose a security risk](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-).

  **Note**: The VMware NSX Edge Services (ESG) for outbound HTTPS management traffic is removed as part of the action to secure your deployed VMware Federal instance. For more information, see [Securing VMware Federal instances](vc_fed_securinginstance.html).

### Virtual Server Instances

The following VSIs (Virtual Server Instances) are ordered:
* A VSI for IBM CloudBuilder, which is shut down after the instance deployment is completed.
* (For instances V2.3 and later) You can choose to deploy a single Microsoft Windows Server VSI for Microsoft Active Directory (AD) or two high availability Microsoft Windows VMs in the management cluster to help enhance security and robustness.
* (For V2.2 instances) A Microsoft Windows Server VSI for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and virtual machines are registered, is deployed and can be looked up.

### Storage

During initial deployment, you can choose between vSAN and NFS storage options.

The vSAN option offers customized configurations, with various options for disk type and quantity:
* Disk quantity: 2, 4, 6, or 8.
* Storage disk: 960 GB SSD SED, 1.9 TB SSD SED, or 3.8 TB SSD SED.

  In addition, 2 cache disks of 960 GB are also ordered per host.

The NFS option offers customized shared file-level storage for workloads with various options for size and performance:
* Size: 1, 2, 4, 8, or 12 TB.
* Performance: 2, 4, or 10 IOPS/GB.
* Individually configure file shares.

If you choose the NFS option, one 2 TB, 4 IOPS/GB file share for management components is ordered.

### IBM-provided licenses and fees

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.4
* (For vSAN clusters) VMware vSAN Advanced or Enterprise 6.6

## Technical specifications for VMware Federal on IBM Cloud expansion nodes

Each vCenter Server expansion node will deploy and incur charges for the following components in your {{site.data.keyword.cloud_notm}} account.

### Hardware for expansion nodes

One Bare Metal Server with the configuration presented in [Technical specifications for VMware Federal on {{site.data.keyword.cloud_notm}} instances](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances).

### Licenses and fees for expansion nodes

* One VMware vSphere Enterprise Plus 6.5u1
* One VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.4
* (For vSAN clusters) VMware vSAN Advanced or Enterprise 6.6

**Important**: You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the {{site.data.keyword.slportal}} or any other means outside of the console. If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.

**CAUTION**: Managing any {{site.data.keyword.vmwaresolutions_short}} components, which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance, from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components

   Exceptions to these activities include managing the shared storage file shares from the {{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

### Related links

* [vCenter Server Software Bill of Materials](vc_bom.html)
* [Requirements and planning for VMware Federal instances](vc_fed_planning.html)
* [Ordering VMware Federal instances](vc_fed_orderinginstance.html)
* [Securing VMware Federal instances](vc_fed_securinginstance.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [{{site.data.keyword.cloud_notm}} file and block storage](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
