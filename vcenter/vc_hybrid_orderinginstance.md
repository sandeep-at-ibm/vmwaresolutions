---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-24"

---

# Ordering vCenter Server with Hybridity Bundle instances

To deploy a flexible and customizable VMware virtualized platform that best fits your workload needs, order a VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instance. Your vCenter Server with Hybridity Bundle instance order includes the VMware Hybrid Cloud Extension (HCX) licensing and entitles you to the VMware HCX on IBM Cloud service. You can also add services, such as [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) for disaster recovery.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](../vmonic/useraccount.html).
*  You reviewed the information in [Requirements and planning for vCenter Server with Hybridity Bundle](vc_hybrid_planning.html).
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

You must specify the following system settings when ordering a vCenter Server with Hybridity Bundle instance.

### Instance name

The instance name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The instance name must start and end with an alphanumeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Primary or secondary

Select whether to order a new primary instance or a secondary instance for an existing primary instance.

## Licensing settings

The following licenses are included with your vCenter Server with Hybridity Bundle instance order. You must specify either **Advanced** or **Enterprise** for the NSX license editions.

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Advanced or Enterprise) 6.3
* VMware vSAN 6.6 license edition (Advanced or Enterprise).

**Attention:**
* vCenter Server with Hybridity Bundle instances do not support Bring Your Own License.
* The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want.

## Bare Metal Server settings

Bare Metal settings are based on your {{site.data.keyword.CloudDataCent_notm}} and customized configuration.

Four ESXi servers are required for both the initial and post-deployment clusters for vSAN configurations. All ESXi servers share the same configuration. In post-deployment, you can add four more clusters.

### Data center location

Select the {{site.data.keyword.CloudDataCent_notm}} where the instance is to be hosted.

### Customized

Specify the CPU model and the amount of RAM for the customized Bare Metal Server.

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

Four ESXi servers are selected by default and cannot be changed.

## Storage settings

VMware vSAN 6.6 is included with your vCenter Server with Hybridity Bundle instance order. You must specify the following storage settings when ordering the instance:

* **Disk Type and Size for vSAN Capacity Disks**: Select the capacity that meets your shared storage needs.
* **Number of vSAN Capacity Disks**: Select the number of disks for the vSAN shared storage that you want to add. The disk quantities must be 2, 4, 6, or 8.

## Network interface settings

You must specify the following network interface settings when ordering a vCenter Server with Hybridity Bundle instance.

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

**Note:** The maximum length of the FQDN (Fully Qualified Domain Name) for hosts and VMs (virtual machines) is 50 characters. Domain names must accommodate for this maximum length.

### Order New VLANs

Select **Order New VLANs** to order one new public VLAN and two new private VLANs.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each Bare Metal Server.

### Select Existing VLANs

Depending on the {{site.data.keyword.CloudDataCent_notm}} that you selected, existing public and private VLANs might be available.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each Bare Metal Server.

Select **Select Existing VLANs** to reuse existing public and private VLANs and choose from the available VLANs and subnets.

**Important:**
* Ensure that the firewall configuration on the selected VLANs does not block the management data traffic.
* Ensure that all of the VLANs you select are in the same pod, because ESXi servers cannot be provisioned on mixed-pod VLANs.

### DNS configuration

Select the Domain Name System (DNS) configuration for your instance:

* **Single Public Windows VSI for Active Directory/DNS**: A single Microsoft Windows Server VSI for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and VMs are registered, is deployed and can be looked up.
* **Two highly available dedicated Windows Server VMs on the management cluster**: Two Microsoft Windows VMs are deployed, helping enhance security and robustness.

**Important:** You must provide two Microsoft Windows Server 2012 R2 licenses if you configure your instance to use the two Microsoft Windows VMs. Use the Microsoft Windows Server 2012 R2 Standard edition license, or the Microsoft Windows Server 2012 R2 Datacenter edition license, or both.

Each license can be assigned only to one single physical server and covers up to two physical processors. One Standard edition license is capable of running two virtualized Microsoft Windows VMs per 2-processor server. Therefore, two licenses are required since two Microsoft Windows VMs are deployed in two different hosts.

You have 30 days to activate the VMs.

For more information on ordering Windows licensing, see [Windows Server 2012 R2 documentation](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Services settings

When you order a vCenter Server with Hybridity Bundle instance, you can also order additional services. For more information about the available services, see [Services for vCenter Server with Hybridity Bundle  instances](vc_hybrid_planning.html#services-for-vcenter-server-with-hybridity-instances).

## Order summary

Based on your selected configuration for the instance and add-on services, the estimated cost is instantly generated and displayed in the right pane. Click **Pricing details** at the bottom of the right pane to generate a PDF document that provides the estimate details.

## Procedure

1. From the IBM Cloud Catalog, click **VMware** from the left navigation pane and then click **vCenter Server** in the **Virtual Data Centers** section.
2. On the **VMware vCenter Server on IBM Cloud** page, click the **vCenter Server with Hybridity Bundle** card and click **Create**.
3. On the **vCenter Server** page, enter the instance name.
4. Select the instance type:
   * Click **Primary Instance** to deploy a single instance in the environment or to deploy the first instance in a multi-site topology.
   * Click **Secondary Instance** to connect the instance with an existing (primary) instance in the environment for high availability and complete the following steps:
     1. Select the primary instance that you want the secondary instance to be connected with.
     2. Enter the PSC administrator password for the primary instance.
5. Select the NSX license edition and the vSAN license edition.
6. Complete the Bare Metal Server settings.
  1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
  2. Select the **Customized** CPU model and the amount of **RAM**.

  **Note:** The **Number of Bare Metal Servers** is set to four by default and cannot be changed.

7. Complete the storage configuration.
  1. Select the **Disk Type and Size for vSAN Capacity Disks**.
  2. Select the **Number of vSAN Capacity Disks**.
8. Complete the network interface configuration.
  1. Enter the host name prefix, subdomain label, and root domain name.
  2. Select the VLAN configuration.
     *  If you want to order new public and private VLANs, click **Order New VLANs**.
     *  If you want to reuse the existing public and private VLANs when they are available, click **Select Existing VLANs**, and then select the public VLAN, the primary subnet, the private VLAN, the private primary subnet, and the secondary private VLAN.
  3. Select the DNS configuration.
9. Select the add-on services to deploy into the instance by clicking the corresponding service card. If a service requires configuration, complete the service-specific settings and click **Add Service** on the card.
  * To install IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} (preselected by default), specify the following settings in the **IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}** window:
    1. **Number of Storage Volumes**: Select the number of volumes that meet your storage needs.
    2. **Storage Size per Volume**: Select the storage capacity per volume. A minimum of 500 GB per volume is required for management.
    3. **Storage Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
  * To install Veeam on {{site.data.keyword.cloud_notm}}, specify the following settings in the **Veeam on {{site.data.keyword.cloud_notm}}** window:
    1. **Number of VMs to License**: Select the number of virtual machines. A minimum of 4 virtual machines for licenses is required for management.
    2. **Storage Size**: Select the capacity that meets your storage needs. A minimum of 2,000 GB of storage is required for management. For considerations when estimating storage size, see [Estimating Repository Capacity](https://bp.veeam.expert/resource_planning/repository_planning_sizing.html).
    3. **Storage Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
  * To install Zerto on {{site.data.keyword.cloud_notm}}, click the service card. If you want it installed as a managed service, select the **Managed Service by IBM Resiliency Services (Priced Separately)** check box in the **Zerto on {{site.data.keyword.cloud_notm}}** window.
  * To install HCX on {{site.data.keyword.cloud_notm}}, specify one of the following settings in the **HCX on {{site.data.keyword.cloud_notm}}** window:
    1. Select **Self-Signed Certificate** for the public endpoint certificate type.
    2. Select **CA Certificate** and specify the following settings:
      * **Certificate Contents**: Enter the contents of the CA certificate.
      * **Private Key**: Enter the private key of the CA certificate.
      * (Optional) **Password**: Enter the password for the private key if it is encrypted.
      * (Optional) **Reenter Password**: Enter the password for the private key again.
      * (Optional) **Hostname**: Enter the host name to be mapped to the common name (CN) of the CA certificate. HCX on {{site.data.keyword.cloud_notm}} requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
  * To install F5 on {{site.data.keyword.cloud_notm}}, specify the following settings in the **F5 on {{site.data.keyword.cloud_notm}}** window:
    1. **Name**: Enter a unique name for the service instance to distinguish it from the additional service instances that you might install later.
    2. **Maximum Bandwidth**: Select the maximum data transfer rate for the network connection.
    3. Select **Good**, **Better**, or **Best** according to your requirements. For more information about what is provided for each license option, click **Learn More** on the **F5 on {{site.data.keyword.cloud_notm}}** service card.
  * To install FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, specify the following settings in the **FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}** window:
    1. **Name**: Enter a unique name for the service instance to distinguish it from the additional service instances that you might install later.
    2. **Deployment Size**: Select **Small (2 vCPUs / 4 GB RAM)**, **Medium (4 vCPUs / 6 GB RAM)**, or **Large (8 vCPU / 12 GB RAM)** for the FortiGate Virtual Appliances.
    3. Select the **Good**, **Better**, or **Best** monthly subscription license model according to your requirements. For more information about what is provided in each license option, click **Learn More** on the **FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}** service card.
  * To install KMIP for VMware on {{site.data.keyword.cloud_notm}}, specify the following settings in the **KMIP for VMware on {{site.data.keyword.cloud_notm}}** window:
    1. **Service Region**: Select the {{site.data.keyword.cloud_notm}} region where your KMIP for VMware {{site.data.keyword.cloud_notm}} service instance is to be hosted.
    2. **Client SSL Certificate**: This field is optional at the time of initial configuration. Leave this field blank if the client certificate of the Key Management Server (KMS) in vCenter Server is not known until after your instance is deployed. However, you must enter the certificate after your instance is deployed so that your vCenter Server connection to the KMS can be completed successfully.
    3. **API Key for Service ID**: Enter the API key for the {{site.data.keyword.cloud_notm}} Service ID that is used to access the IBM Key Protect Service instances.
    4. **Key Protect Instance**: Click **Retrieve Instances** to get a list of all available IBM Key Protect Service instances and then select the one that is used for key management.
    5. **Customer Root Key**: Click **Retrieve Keys** to get the customer root key that is stored in the IBM Key Protect instance selected above.

8. On the **Order Summary** pane, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you order the instance.
   4. Click **Provision**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in the _vCenter Server with Hybridity Bundle technical specifications_ section in the [vCenter Server with Hybridity Bundle overview](vc_hybrid_overview.html) are installed on your VMware virtual platform. The ESXi servers that you ordered are grouped as **cluster1** by default. If you ordered additional services, the deployment of the services starts after your order is completed.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.

## What to do next

View and manage the vCenter Server with Hybridity Bundle instance that you ordered.

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
* [Viewing vCenter Server with Hybridity Bundle instances](vc_hybrid_viewinginstances.html)
* [Multi-site configuration for vCenter Server with Hybridity Bundle instances](vc_hybrid_multisite.html)
* [Adding and viewing clusters for vCenter Server with Hybridity Bundle instances](vc_hybrid_addingviewingclusters.html)
* [Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances](vc_hybrid_addingremovingservers.html)
* [Ordering and removing services for vCenter Server with Hybridity Bundle instances](vc_hybrid_addingremovingservices.html)
* [Deleting vCenter Server with Hybridity Bundle instances](vc_hybrid_deletinginstance.html)
