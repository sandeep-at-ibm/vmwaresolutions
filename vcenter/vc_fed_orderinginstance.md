---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-07"

---

# Ordering a VMware Federal instance

To deploy a flexible and customizable VMware virtualized platform that best fits your workload needs, order a VMware instance that enables you to disconnect the open management connection and secure your deployed instance.

**Note:** Only vCenter Server instances support VMware Federal on {{site.data.keyword.cloud}} at this time.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](../vmonic/useraccount.html).
*  You meet the requirements and you reviewed the considerations in [vCenter Server requirements](vc_planning.html).

**Important: Do not modify any values that are set during ordering and instance deployment. Doing so can result in your instance becoming unusable. For example, public networking may shut down, servers and Virtual Server Instances (VSIs) may move behind a Vyatta mid-provision, or the IBM CloudBuilder VSI may stop or be deleted.**

## System settings

When you order a VMware Federal instance, you must specify the following settings under **System**.

### Instance name

The instance name must meet the following requirements:
* Only alphanumeric characters are allowed.
* The instance name must start and end with an alphanumeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Domain name

The root domain name must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The name must consist of two or more strings that are separated by period (.)
*  Each string must start with an alphabetic character and end with an alphanumeric character, and the last string can contain only alphabetic characters.
*  The length of the last string must be in the range 2 - 24 characters.

**Note:** The maximum length of the FQDN (Fully Qualified Domain Name) for hosts and VMs (virtual machines) is 50 characters. Domain names must accomodate for this maximum length.

### Subdomain label

The subdomain label must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The subdomain label must start and end with an alphanumeric character.
*  The maximum length of the subdomain label is 10 characters.
*  The subdomain label must be unique within your account.

### Instance and domain name format

The VMware Federal instance name and the root domain name use the format in the following table.

Table 1. Value format for instance and domain names

| Name        | Value Format      |
  |:------------- |:------------- |
  | Domain name | `<root_domain>` |  
  | vCenter Server login user name | `<user_id>@<root_domain>` (Microsoft Active Directory user) or `administrator@vsphere.local` |
  | vCenter Server FQDN | `vcenter.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |
  | Single Sign-On (SSO) site name | `<subdomain_label>` |
  | Fully qualified ESXi server name | `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `<n>` is the sequence of the ESXi server. The maximum length is 50 characters. |  
  | PSC FQDN | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |

### Host name prefix

  The host name prefix must meet the following requirements:
  *  Only alphanumeric and dash (-) characters are allowed.
  *  The host name prefix must start and end with an alphanumeric character.
  *  The maximum length of the host name prefix is 10 characters.

### IBM Cloud Data Center location

Only the WDC03 - Washington, DC {{site.data.keyword.CloudDataCent_notm}} is currently available for VMware Federal instances. This setting is automatically set to the default and disabled.

## Bare Metal settings

Bare Metal settings are based on your customized configuration. The option to select a preconfigured configuration is not supported at this time.

<!-- For guidance on what Bare Metal Server configuration to choose, see the _Bill of Materials_ document on the [Virtualization reference architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page. -->

### Customized

Specify the **CPU Model** and **RAM** for the Bare Metal Server.

Table 2. Options for customized {{site.data.keyword.baremetal_short}}

| CPU options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz | 64 GB, 128 GB, 256 GB, 512 GB |

### Number of Bare Metal Servers

You can configure the number of ESXi servers in the range 2 - 20.

All ESXi servers share the same configuration.

**Note:** For vSAN storage settings, 4 ESXi servers are required. For more information about minimum of ESXi servers, see [Is a two-node vCenter Server instance highly available](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-).

## Storage settings

Storage settings are based on your selection of either **vSAN** or **NFS**.

### vSAN

Specify the following storage options:

* **Number of vSAN Capacity Disks**: Specify the number of disks for the vSAN shared storage that you want to add. The disk quantities must be 2, 4, 6, or 8.
* **Disk Type and Size for vSAN Capacity Disks**: Select the capacity that meets your shared storage needs.

### NFS

For NFS, you can add file-level shared storage for your instance. Specify the following storage options:

* **File Shares**: Specify the number of file shares for the NFS shared storage that you want to add. The number of file shares must be in the range of 1 to 32.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements. The performance levels available to you depend on the VMware that you select.
* **Configure shares individually**: Optionally select to complete individual file share configuration.
* **Add NFS**: Optionally select if you are configuring your file shares individually and need to add additional file shares.

Table 3. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |

<!--### NFS version
NFS (Network File System) v3 is set by default and you cannot change it. NFS v3 supports SDRS (Storage Distributed Resource Scheduler) and SIOC (Storage I/O Control), and it does not include NFS multipathing.-->

## Licenses

Select IBM-provided VMware licenses for the following:

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.3
* VMware vSAN (Advanced or Enterprise) 6.6

## Estimated Cost

You can calculate an estimated cost and generate a detailed PDF from each panel as you provide details for your instance order. Complete the fields on the panel and click **Calculate Cost** at the bottom of the panel to generate a cost estimate. Additionally, click the calculated cost estimate link to generate a PDF that provides the estimate details.

**Note:** The estimated cost displayed on the panel and the cost estimate details provided in the PDF are only for the items that you have completed on your order. The cost increases as you complete each panel for your instance order.

## Procedure

1. Click **Getting Started** on the left navigation pane.
2. On the **VMware vCenter Server on IBM Cloud** card, click **Order Instance**.
3. On the **Order a vCenter Server Instance** page, select **Primary** and click **Next**.
   **Note:** Deploying a secondary instance for high availability is not supported at this time.
4. On the **System** page, provide the following information:

    1. Enter the instance name, root domain name, subdomain label, and host name prefix.
    2. Select the Bare Metal configuration:
       Specify the **CPU Model**, the amount of **RAM**, and the **Number of {{site.data.keyword.baremetal_short}}**.
    3. Select the storage configuration.
       * If you selected **vSAN**, specify the **Number of vSAN Capacity Disks** and **Disk Type and Size for vSAN Capacity Disks**.
       * If you selected **NFS**, specify the **File Shares**, **Size**, and **Performance**. Optionally select **Configure shares individually** to complete individual file configuration. Use the **Add NFS** option to add additional file shares, if necessary.
    4. Click **Next**.
5. On the **License** page, specify the license edition for the VMware NSX license and VMware vSAN (if you selected vSAN storage) and then click **Next**.

   **Attention**:

   * The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want. You are responsible to ensure that the license key provided is correct for each VMware component selected.
   * For vSphere, a license charge will be incurred at time of order, but the license charge will subsequently be credited to your account.

6. On the **Summary** page, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Click the link or links of the terms that apply to your order, and ensure that you agree with these terms before you order the instance.
   3. Review the estimated cost of the instance by clicking the cost link under **Estimated Cost**. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   4. Click **Create**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in [vCenter Server instance components](../vcenter/vc_vcenterserveroverview.html#vcenter-server-instance-components) are installed on your VMware virtual platform. The ESXi servers that you ordered are grouped as **cluster1** by default.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

## What to do next

View and secure the VMware Federal instance that you ordered.

For more information, see:

* [Viewing VMware Federal instances](vc_fed_viewinginstance.html)
* [Securing VMware Federal instances](vc_fed_securinginstance.html)

<!--**Important:**

After selecting the secure option, all management functions are disabled except for a full instance delete.

You must manage the {{site.data.keyword.vmwaresolutions_full}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the 	{{site.data.keyword.slportal}} or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.

**CAUTION:** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through removing ESXi servers
*  Powering off components

   Exceptions to these activities include managing the shared storage file shares from the 	{{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.-->

## Related links

* [Signing up for an {{site.data.keyword.cloud_notm}} account](../vmonic/signing_softlayer_account.html)
* [VMware Federal on IBM Cloud overview](vc_fed_overview.html)
* [Deleting VMware Federal instances](vc_fed_deletinginstance.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
