---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Ordering vCenter Server instances

To deploy a flexible and customizable VMware virtualized platform that best fits your workload needs, order a VMware vCenter Server instance. During the initial order, you can also add services, such as [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) for disaster recovery.

## Requirements

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](../vmonic/useraccount.html).
* You reviewed the information in [Requirements and planning for vCenter Server instances](vc_planning.html).
* You reviewed the instance and domain name format. The domain name and subdomain label are used to generate the user name and server names of the instance.

Table 1. Value format for instance and domain names

| Name        | Value Format      |
  |:------------- |:------------- |
  | Domain name | `<root_domain>` |  
  | vCenter Server login user name | `<user_id>@<root_domain>` (Microsoft Active Directory user) or `administrator@vsphere.local` |
  | vCenter Server FQDN | `vcenter.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |
  | Single Sign-On (SSO) site name | `<subdomain_label>` |
  | Fully qualified ESXi server name | `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `<n>` is the sequence of the ESXi server. The maximum length is 50 characters. |  
  | PSC FQDN | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |

**Important**: Do not modify any values that are set during ordering and instance deployment. Doing so can result in your instance becoming unusable. For example, public networking may shut down, servers and Virtual Server Instances (VSIs) may move behind a Vyatta mid-provision, or the IBM CloudBuilder VSI may stop or be deleted.

## System settings

You must specify the following system settings when ordering a vCenter Server instance.

### Instance name

The instance name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The instance name must start and end with an alphanumeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Primary or secondary

Select whether to order a new primary instance or a secondary instance for an existing primary instance.

## Licensing settings

Specify the licensing options for the following VMware components in the instance:
* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.3

For Business Partner users, the vCenter Server license (Standard edition), the vSphere license (Enterprise Plus edition), and the NSX license are included and purchased on your behalf. However, you must specify the edition for the NSX license.

For non-Business Partner users, you can use the IBM-provided VMware licenses for these components by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license keys.

**Attention**:
* A license with a minimum of 8 CPUs is required, which is for 4 servers with 2 CPUs per server. The license choice for each VMware component applies to the base instance and to any ESXi servers that you add to the instance later. Therefore, you must ensure that your license supports future capacity expansion in your infrastructure.
* The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want. You are responsible to ensure that the license key provided is correct for each VMware component selected.
* For vSphere, a license charge will be incurred at time of order, but the license charge will subsequently be credited to your account.
* You can change any licenses that you have provided by using the VMware vSphere Web Client after the instance deployment is completed.
* Support for the VMware components that you provide licenses for will be directly provided by VMware, not by IBM Support.

## Bare Metal Server settings

Bare Metal settings are based on your data center selection and whether you choose a preconfigured or customized configuration.

### Data center location

Select the {{site.data.keyword.CloudDataCent_notm}} where the instance is to be hosted.<!-- Only the {{site.data.keyword.CloudDataCents_notm}} that meet the {{site.data.keyword.baremetal_long}} specification you selected previously are displayed.-->

### Preconfigured

When you select **Preconfigured**, you cannot alter the CPU or RAM settings.

Based on your requirements, select a Bare Metal Server configuration:
  * Small (Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz / 128 GB RAM / 2 drives)
  * Medium (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz / 256 GB RAM / 2 drives)
  * Large (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz / 512 GB RAM / 2 drives)

### Customized

When you select **Customized**, you can choose the CPU and RAM combination according to your needs.

Select the CPU model and RAM for the Bare Metal Server.

Table 2. Options for customized {{site.data.keyword.baremetal_short}}

| CPU options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

### Number of Bare Metal Servers

For the initial cluster in the instance, you can configure the number of ESXi servers as follows:
* If you selected **Preconfigured**, you can configure the number of ESXi servers in the range 2 - 10.
* If you selected **Customized**, you can configure the number of ESXi servers in the range 2 - 20.

All ESXi servers share the same configuration. After initial deployment, you can add four more clusters. If you selected the **Customized** configuration for vSAN, 4 ESXi servers are required for both the initial and post-deployment clusters. For more information about minimum of ESXi servers, see [Is a two-node vCenter Server instance highly available](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-).

## Storage settings

Storage settings are based on your selection of Bare Metal Server configuration and the storage type.

### vSAN storage

vSAN is available only when you select the **Customized** Bare Metal configuration. Specify the following vSAN options:

* **Number of vSAN Capacity Disks**: Specify the number of disks for the vSAN shared storage that you want to add. The disk quantities must be 2, 4, 6, or 8.
* **Disk Type and Size for vSAN Capacity Disks**: Select the capacity that meets your shared storage needs.
* **vSAN License**: Use the IBM-provided VMware license for the vSAN component by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

### NFS storage

When you select **NFS Storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. Specify the following NFS options:

**Note:** The number of file shares must be in the range of 1 to 32.

* **Configure shares individually**: Select to specify different configuration settings for each file share.
* **Number of Shares**: When using the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
* **ADD NFS**: Select to add individual file shares that use different configuration settings.

Table 3. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |

## Network interface settings

You must specify the following network interface settings when ordering a vCenter Server instance.

### Host name prefix

The host name prefix must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The host name prefix must start and end with an alphanumeric character.
*  The maximum length of the host name prefix is 10 characters.

### Subdomain label

The subdomain label must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The subdomain label must start and end with an alphanumeric character.
*  The maximum length of the subdomain label is 10 characters.
*  The subdomain label must be unique within your account.

### Domain name

The root domain name must meet the following requirements:
* The domain name must consist of two or more strings that are separated by period (.)
* The first string must start with an alphabetic character and end with an alphanumeric character.
* All strings, except for the last one, can contain only alphanumeric and dash (-) characters.
* The last string can contain only alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

**Note:** The maximum length of the Fully Qualified Domain Name (FQDN) for hosts and VMs is 50 characters. Domain names must accommodate for this maximum length.

### VLANs

Network settings are based on your selection of either **Order New VLANs** or **Select Existing VLANs**.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each Bare Metal Server.

**Order New VLANs**  
Select to order one new public VLAN and two new private VLANs.

**Select Existing VLANs**  
Depending on the {{site.data.keyword.CloudDataCent_notm}} that you selected, existing public and private VLANs might be available.

When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
* **Public VLAN** is for public network access.
* **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}.
* **Secondary private VLAN** is for VMware features such as vSAN.
* **Primary Subnet** is assigned to physical hosts for public network access.
* **Primary Private Subnet** is assigned to physical hosts for management traffic.

**Important:**
* Ensure that the firewall configuration on the selected VLANs does not block the management data traffic.
* Ensure that all of the VLANs you select are in the same pod, because ESXi servers cannot be provisioned on mixed-pod VLANs.

### DNS configuration

Select the Domain Name System (DNS) configuration for your instance:

* **Single Public Windows VSI for Active Directory/DNS**: A single Microsoft Windows Server VSI for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and VMs are registered, is deployed and can be looked up. This option has been deployed by default for V1.9 and later instances.
* **Two highly available dedicated Windows Server VMs on the management cluster**: Two Microsoft Windows VMs are deployed, helping enhance security and robustness.

**Important:** You must provide two Microsoft Windows Server 2012 R2 licenses if you configure your instance to use the two Microsoft Windows VMs. Use the Microsoft Windows Server 2012 R2 Standard edition license, or the Microsoft Windows Server 2012 R2 Datacenter edition license, or both.

Each license can be assigned only to one single physical server and covers up to two physical processors. One Standard edition license is capable of running two virtualized Microsoft Windows VMs per 2-processor server. Therefore, two licenses are required since two Microsoft Windows VMs are deployed in two different hosts.

You have 30 days to activate the VMs.

For more information about Windows licensing, see [Windows Server 2012 R2 documentation](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Services settings

When you order a vCenter Server instance, you can also order additional services. For more information about the services, see [Available services for vCenter Server instances](vc_addingremovingservices.html#available-services-for-vcenter-server-instances).

## Order summary

Based on your selected configuration for the instance and add-on services, the estimated cost is instantly generated and displayed in the **Order Summary** section on the right pane. Click **Pricing details** at the bottom of the right pane to generate a PDF document that provides the estimate details.

## Procedure

1. From the {{site.data.keyword.cloud_notm}} Catalog, click **VMware** from the left navigation pane and then click **vCenter Server** in the **Virtual Data Centers** section.
2. On the **VMware vCenter Server on IBM Cloud** page, click the **vCenter Server** card and click **Create**.
3. On the **vCenter Server** page, enter the instance name.
4. Select the instance type:
   * Click **Primary Instance** to deploy a single instance in the environment or to deploy the first instance in a multi-site topology.
   * Click **Secondary Instance** to connect the instance with an existing (primary) instance in the environment for high availability and complete the following steps:
     1. Select the primary instance that you want the secondary instance to be connected with.
     2. Enter the PSC administrator password for the primary instance.
5. Complete the license settings for the instance components.  
   *  To use IBM-provided licenses, select **Include with purchase** and select the license edition, if necessary.
   *  To use your own license, select **I will provide** and enter the license key.
6. Complete the Bare Metal Server settings.
    1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
    2. Select the Bare Metal Server configuration.
       * When you select **Preconfigured**, choose **Small**, **Medium**, or **Large** for the configuration.
       * When you select **Customized**, specify the CPU model and the RAM size.
    3. Specify the number of {{site.data.keyword.baremetal_short}}. If you are planning to use vSAN as your storage solution, note that a minimum of 4 {{site.data.keyword.baremetal_short}} are needed.  

7. Complete the storage settings:
  * When you select **vSAN Storage**, specify the **Disk Type and Size for vSAN Capacity Disks**, **Number of vSAN Capacity Disks**, and how the **vSAN License** is to be provided.
  * When you select **NFS Storage** and want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Size**, and **Performance**.
  * When you select **NFS Storage** and want to add and configure file shares individually, select **Configure shares individually**, then click the **+** icon beside the **Add NFS** label and select the **Size** and **Performance** for each individual file share. You must select at least one file share.

8. Complete the network interface settings.
   1. Enter the host name prefix, subdomain label, and root domain name. For a secondary instance, the domain name is automatically filled in.
   2. Select the VLAN settings:
      * If you want to order new public and private VLANs, click **Order New VLANs**.
      * If you want to reuse the existing public and private VLANs when they are available, click **Select Existing VLANs** and  specify the VLANs and the subnets.
   3. Specify the DNS configuration.

9. Select the add-on services to deploy into the instance by clicking the corresponding service card. If a service requires configuration, complete the service-specific settings and click **Add Service** on the card.
For information about how to provide settings for a service, see the corresponding service ordering topic.

10. On the **Order Summary** pane, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you order the instance.
   4. Click **Provision**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in the _vCenter Server technical specifications_ section in [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html) are installed on your VMware virtual platform. The ESXi servers that you ordered are grouped as **cluster1** by default. If you ordered additional services, the deployment of the services starts after your order is completed.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.

## What to do next

View and manage the vCenter Server instance that you ordered.

**Important**: You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account	 only from the {{site.data.keyword.vmwaresolutions_short}} console, not the 	{{site.data.keyword.slportal}} or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.

**CAUTION**: Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account	 when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

   Exceptions to these activities include managing the shared storage file shares from the 	{{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

## Related links

* [Signing up for an {{site.data.keyword.cloud_notm}} account](../vmonic/signing_softlayer_account.html)
* [Viewing vCenter Server instances](vc_viewinginstances.html)
* [Multi-site configuration for vCenter Server instances](vc_multisite.html)
* [Adding, viewing, and deleting clusters for vCenter Server instances](vc_addingviewingclusters.html)
* [Expanding and contracting capacity for vCenter Server instances](vc_addingremovingservers.html)
* [Ordering, viewing, and removing services for vCenter Server instances](vc_addingremovingservices.html)
* [Deleting vCenter Server instances](vc_deletinginstance.html)
