---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-25"

---

# Ordering vCenter Server instances

To deploy a flexible and customizable VMware virtualized platform that best fits your workload needs, order a VMware vCenter Server instance. During the initial order, you can also add services, such as [Zerto on IBM Cloud](../services/addingzertodr.html).

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](../vmonic/useraccount.html).
*  You meet the requirements and you reviewed the considerations in [vCenter Server requirements](vc_planning.html).

**Important: Do not modify any values that are set during ordering and instance deployment. Doing so can result in your instance becoming unusable. For example, public networking may shut down, servers and Virtual Server Instances (VSIs) may move behind a Vyatta mid-provision, or the IBM CloudBuilder VSI may stop or be deleted.**

## System settings

When you order a vCenter Server instance, you must specify the following settings under **System**.

### Instance type

You can deploy the instance as a primary (single) instance in your environment, or deploy the instance in a multi-site configuration by linking it with an existing primary instance for high availability. For more information, see [Multi-site configuration for vCenter Server instances](vc_multisite.html).

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

### Host name prefix

The host name prefix must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The host name prefix must start and end with an alphanumeric character.
*  The maximum length of the host name prefix is 10 characters.

### Instance and domain name format

The vCenter Server instance name and the root domain name use the format in the following table.

Table 1. Value format for instance and domain names

| Name        | Value Format      |
  |:------------- |:------------- |
  | Domain name | `<root_domain>` |  
  | vCenter Server login user name | `<user_id>@<root_domain>` (Microsoft Active Directory user) or `administrator@vsphere.local` |
  | vCenter Server FQDN | `vcenter.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |
  | Single Sign-On (SSO) site name | `<subdomain_label>` |
  | Fully qualified ESXi server name | `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `<n>` is the sequence of the ESXi server. The maximum length is 50 characters. |  
  | PSC FQDN | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |

### Bare Metal Server configuration

You can select a Bare Metal Server configuration depending on your requirements:
* Small (Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz / 128 GB RAM / 2 disks)
* Medium (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz / 256 GB RAM / 2 disks)
* Large (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz / 512 GB RAM / 2 disks)
* User customized: you can specify the CPU model and RAM for the Bare Metal Server

Table 2. Dual Intel Xeon CPU and RAM options for the user-customized configuration

| Item          | Options       |
|:------------- |:------------- |
| CPU | <ul><li>Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz</li><li>Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz</li><li>Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz</li></ul>|
| RAM | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1.5 TB|

Table 3. Dual Intel Xeon Gold CPU and RAM options for the user-customized configuration

| Item        | Options       |
|:------------- |:------------- |
| CPU | Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz|
| RAM | 96 GB, 192 GB, 384 GB, 768 GB, 1.5 TB|

For guidance on what Bare Metal Server configuration to choose, see the _Bill of Materials_ document in the [Architecture Center](https://www.ibm.com/devops/method/content/architecture/virtVCenterServerPlatform){:new_window}.

### Number of Bare Metal Servers

For the initial cluster in the instance, you can configure the number of ESXi servers as follows:
* If you selected **Small**, **Medium**, or **Large** Bare Metal Server configuration, you can configure the number of ESXi servers in the range 2 - 10.
* If you selected **User customized** Bare Metal Server configuration, you can configure the number of ESXi servers in the range 2 - 20.

All ESXi servers share the same configuration. In post-deployment, you can add four more clusters. If you selected the **User customized** configuration for vSAN, 4 ESXi servers are required for both the initial and post-deployment clusters. For more information about minimum of ESXi servers, see [Is a two-node vCenter Server instance highly available](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-).

### Data center location

You must select the IBM Cloud data center where the instance is to be hosted. Only the data centers that meet the bare metal server specification you selected previously are displayed.

## Storage settings

Storage settings are based on your selection of either vSAN or NFS.

### vSAN

For vSAN, you select the User customized Bare Metal Server configuration and you can customize the VMware vSAN storage for your instance by specifying the following settings under **Storage**:

* **Number of vSAN Capacity Disks**: Specify the number of disks for the vSAN shared storage that you want to add. The disk quantities must be 2, 4, 6, or 8.
* **Disk Type and Size for vSAN Capacity Disks**: Select the capacity that meets your shared storage needs.

### NFS

For NFS, you can add file-level shared storage for your instance. Specify the following settings under **Storage**:

* **File Shares**: Specify the number of file shares for the NFS shared storage that you want to add. The number of file shares must be in the range of 1 to 32.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements. The performance levels available to you depend on the data center that you select.
* **Configure file shares individually**: Optionally select to complete individual file share configuration.
* **Add NFS**: Optionally select if you are configuring your file shares individually and need to add additional file shares.

Table 3. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share, and it is supported only for the following IBM Cloud Data Centers: AMS03, DAL09, DAL10, DAL12, DAL13, FRA02, HKG01, LON02, LON04, LON06, MEL01, MEX01, MON01, OSL01, PAR01, SJC03, SJC04, SYD01, TOK02, TOR01, WDC04, WDC06, and WDC07. |

<!--### NFS version
NFS (Network File System) v3 is set by default and you cannot change it. NFS v3 supports SDRS (Storage Distributed Resource Scheduler) and SIOC (Storage I/O Control), and it does not include NFS multipathing.-->

## Services

When you order a vCenter Server instance, you can also order additional services. For more information about the available services, see [Services for vCenter Server instances](vc_planning.html#services-for-vcenter-server-instances).

## Estimated Cost

You can calculate an estimated cost and generate a detailed PDF from each panel as you provide details for your instance order. Complete the fields on the panel and click **Calculate Cost** at the bottom of the panel to generate a cost estimate. Additionally, click the calculated cost estimate link to generate a PDF that provides the estimate details.

**Note:** The estimated cost displayed on the panel and the cost estimate details provided in the PDF are only for the items that you have completed on your order. The cost increases as you complete each panel for your instance order.

## Procedure

1. Click **Getting Started** on the left navigation pane.
2. On the **VMware vCenter Server on IBM Cloud** card, click **Order Instance**.
3. On the **Order a vCenter Server Instance** page, select the instance type:
   *  To deploy a single instance in the environment or to deploy the first instance in a multi-site topology, ensure that **Primary** is selected and click **Next**.
   *  To connect the instance with an existing (primary) instance in the environment for high availability, select  **Secondary** and click **Next**.
4. On the **Basics** page, specify the required information based on the instance type you selected.

   If you selected the **Primary** instance type, provide the following information:

    1. Enter the root domain name, subdomain label, instance name, and data center location.
    2. Select your Bare Metal Server configuration.
       * If you selected **Custom**, specify the **CPU Model** and the amount of **RAM**.
       * If you selected **Preconfigured**, specify the **Bare Metal Server Configuration**.
    3. Specify the number of {{site.data.keyword.baremetal_short}}. vSAN will always use 4 {{site.data.keyword.baremetal_short}}.
    4. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
    5. Select vSAN or NFS for **Storage**.
       * If you selected vSAN, specify the **Number of vSAN Capacity Disks** and **Disk Type and Size for vSAN Capacity Disks**.
       * If you selected NFS, specify the **File Shares**, **Size**, and **Performance**. Optionally select **Configure shares individually** to complete individual file configuration. Use the **Add NFS** option to add additional file shares, if necessary.
    6. Click **Next**.

   If you selected the **Secondary** instance type, provide the following information:

    1. Enter the secondary instance name.
    2. Select the primary instance that you want the secondary instance to be connected with.
    3. Review the root domain name that is automatically filled in.
    4. Enter the subdomain label and host name prefix.
    5. Select the Bare Metal Server configuration.
    6. If you selected **User customized** for the Bare Metal Server configuration, specify the **CPU Model** and the amount of **RAM**.
    7. Specify the number of {{site.data.keyword.baremetal_short}}.
    8. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
    9. Select vSAN or NFS for **Storage**.
       * If you selected vSAN, specify the **Number of vSAN Capacity Disks** and **Disk Type and Size for vSAN Capacity Disks**.
       * If you selected NFS, specify the **File Shares**, **Size**, and **Performance**. Optionally select **Configure shares individually** to complete individual file configuration. Use the **Add NFS** option to add additional file shares, if necessary.  
    10. Click **Next**.

5. If you selected the **Secondary** instance type, review the following information on the **Authentication** page:

    1. In the **Primary Instance PSC Administrator Password** field, the Platform Services Controller (PSC) password of the selected primary instance is automatically filled in.
    2. Click **Next** to verify the password.
    3. If the password validation fails, enter the correct PSC password, and click **Next** again.

6. On the **Licensing** page, specify the licensing choice for each of the VMware components in the instance, including VMware vCenter Server, VMware vSphere, VMware NSX, and VMware vSAN (if you selected vSAN storage) and then click **Next**.
   * If you want new licenses to be purchased on your behalf, select **Include with purchase** for the components. For VMware NSX and vSAN, also select the license edition.
   * If you want to use your own VMware license for a component, select **I will provide** and enter the license key for the component.

   **Attention**:
   * Only one license choice is supported for each VMware component. Both purchasing and providing licenses for the same VMware component is not supported. The license choice selected for a VMware component applies for the life of the instance.
   * A license with a minimum of 8 CPUs is required, which is for 4 servers with 2 CPUs per server. The license choice for each VMware component applies to the base instance and to any ESXi servers that you add to the instance later. Therefore, you must ensure that your license supports future capacity expansion in your infrastructure.
   * The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want. You are responsible to ensure that the license key provided is correct for each VMware component selected.
   * For vSphere, a license charge will be incurred at time of order, but the license charge will subsequently be credited to your account.
   * You can change any licenses that you have provided by using the VMware vSphere Web Client after the instance deployment is completed.
   * Support for the VMware components that you provide licenses for will be directly provided by VMware, not by IBM Support.

7. On the **Add Service** page, complete the following steps:

   1. To deploy a service into your instance, click **Select Service** on the corresponding service card.
   2. If you accepted the default selection for Veeam on {{site.data.keyword.cloud_notm}}, specify the following settings in the **Configure Veeam on IBM Cloud** area:
      * **Number of VMs to License**: A minimum of 4 VMs for licenses is required for management.
      * **Storage Size**: The capacity that meets your storage needs. A minimum of 2,000 GB of storage is required for management. For considerations when estimating storage size, see [Estimating Repository Capacity](https://bp.veeam.expert/resource_planning/repository_planning_sizing.html).
      * **Storage Performance**: The IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
   3. If you want to install F5 on {{site.data.keyword.cloud_notm}}, specify the following settings in the **Configure F5 on IBM Cloud** area:
      * **Name**: Specify a unique name for the service instance to distinguish it from the additional service instances that you might install later.
      * **License Model**: Select **Good**, **Better**, or **Best** according to your requirements. For more information about what is provided for each license option, click **Learn More** on the **F5 on IBM Cloud** service card.
      * **Maximum Bandwidth**: Select the maximum data transfer rate for the network connection.
   4. If you want to install FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, specify the following settings in the **Configure FortiGate Virtual Appliance on IBM Cloud** area:
      * **Name**: Specify a unique name for the service instance to distinguish it from the additional service instances that you might install later.
      * **Deployment Size**: Select **Small**, **Medium**, or **Large** with different CPU and RAM specifications for the FortiGate Virtual Appliances.
      * **Monthly Subscription License Model**: Select **Standard FW**, **Standard FW + UTM**, or **Standard FW + Enterprise** according to your requirements. For more information about what is provided in each license option, click **Learn More** on the **FortiGate Virtual Appliance on IBM Cloud** service card.
   5. If you want to install HCX on {{site.data.keyword.cloud_notm}}, select the **Public endpoint certificate type** in the **Configure HCX on IBM Cloud** area. If you select **CA Certificate**, sepecify the following settings:
      * **Certificate Contents**: Enter the contents of the CA certificate.
      * **Private Key**: Enter the private key of the CA certificate.
      * (Optional) **Password**: Enter the password for the private key if it is encrypted.
      * (Optional) **Reenter Password**: Enter the password for the private key again.
      * (Optional) **Hostname**: Enter the host name to be mapped to the common name (CN) of the CA certificate. HCX requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
   6. Select any other services that you want to install, or, to proceed without deploying any service, including Veeam on {{site.data.keyword.cloud_notm}}, click **Selected Service** on the service card. Click **Next**.

8. On the **Summary** page, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Click the link or links of the terms that apply to your order, and ensure that you agree with these terms before you order the instance.
   3. Review the estimated cost of the instance by clicking the cost link under **Estimated Cost**. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   4. Click **Create**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in [vCenter Server instance components](../vcenter/vc_vcenterserveroverview.html#vcenter-server-instance-components) are installed on your VMware virtual platform. The ESXi servers that you ordered are grouped as **cluster1** by default. If you ordered additional services, the deployment of the services starts after your order is completed.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.

## What to do next

View and manage the vCenter Server instance that you ordered.

**Important**: You must manage the {{site.data.keyword.vmwaresolutions_full}} components that are created in your {{site.data.keyword.cloud_notm}} account	 only from the {{site.data.keyword.vmwaresolutions_short}} console, not the 	{{site.data.keyword.slportal}} or any other means outside of the console.
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
* [Adding and viewing clusters for vCenter Server instances](vc_addingviewingclusters.html)
* [Expanding and contracting capacity for vCenter Server instances](vc_addingremovingservers.html)
* [Ordering and removing services for vCenter Server instances](vc_addingremovingservices.html)
* [Deleting vCenter Server instances](vc_deletinginstance.html)
