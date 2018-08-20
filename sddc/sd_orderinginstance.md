---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Ordering Cloud Foundation instances

To deploy a unified software-defined data center (SDDC) platform with standard compute, storage, and network configuration, order a VMware Cloud Foundation instance. During the initial order, you can also add services, such as [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) for disaster recovery.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](../vmonic/useraccount.html).
*  You reviewed the requirements and considerations in [Requirements and planning for Cloud Foundation instances](sd_planning.html).

**Important:** Do not modify any values that are set during ordering and instance deployment. Doing so can result in your instance becoming unusable. In addition, do not change the instance name, root domain name, subdomain label, or host name prefix, after the instance is deployed.

## System settings

You must specify the following system settings when ordering a Cloud Foundation instance.

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
* vCenter Server License - Standard
* vSphere License - Enterprise Plus
* NSX License - Enterprise
* vSAN License: select the Advanced or Enterprise edition

For Business Partner users, the vCenter Server license (Standard edition), the vSphere license (Enterprise Plus edition), the NSX license, and the vSAN license are included and purchased on your behalf. However, you must specify the edition for the vSAN license.

For non-Business Partner users, you can use the IBM-provided VMware licenses for these components by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license keys.

## Bare Metal Server settings

### Data center location

Select the {{site.data.keyword.CloudDataCent_notm}} where the instance is to be hosted.

### Preconfigured

When you select **Preconfigured**, you cannot change the CPU or RAM settings.

Based on your requirements, select a Bare Metal Server configuration:
  * Small (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz / 128 GB RAM / 12 drives)
  * Large (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz / 512 GB RAM / 12 drives)

### Customized

When you select **Customized**, you can choose the CPU and RAM combination according to your needs.

Select the CPU model and RAM for the Bare Metal Server.

Table 1. Options for customized {{site.data.keyword.baremetal_short}}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

### Number of Bare Metal Servers

A Cloud Foundation instance comprises four Bare Metal Severs at the initial deployment. You cannot change the number of Bare Metal Servers when you place the order.

## Storage settings

The Cloud Foundation instances support only the vSAN storage.
* When you select **Preconfigured** Bare Metal Server configuration, the storage settings are standardized and cannot be changed:
  * For the **Small** Bare Metal Server configuration, 2 disk drives of 1.9 TB SSD SED are ordered.
  * For the **Large** Bare Metal Server configuration, 4 disk drives of 3.8 TB SSD SED are ordered.
* When you select the **Customized** Bare Metal Server configuration, you can customize the VMware vSAN storage for your instance by specifying the following settings under **vSAN Storage**:
  * **Disk Type and Size for vSAN Capacity Disks**: Select the capacity that meets your shared storage needs.
  * **Number of vSAN Capacity Disks**: Specify the number of disks for the vSAN shared storage that you want to add. The disk quantities must be 2, 4, 6, or 8.

## Network interface settings

You must specify the following network interface settings when ordering a Cloud Foundation instance.

### Hostname prefix

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

### Value format for network settings

The domain name and subdomain label are used to generate the user name and server names of the instance, as shown in the following table.

Table 2. Value format for user names, domain names, and server names

| Name        | Value Format      |
  |:------------- |:------------- |
  | Domain name | `<root_domain>` |  
  | Fully qualified ESXi server name | `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `<n>` is the sequence of the ESXi server. The maximum length is 50 characters. |   
  | vCenter Server login user name | `<user_id>@<root_domain>` (Microsoft Active Directory user) or `administrator@vsphere.local` |
  | vCenter Server FQDN | `vcenter-1.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |  
  | SDDC Manager FQDN | `sddcmanager.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |
  | Single Sign-On (SSO) site name | `<subdomain_label>`
  | PSC FQDN | `PSC-<subdomain_label>.<subdomain_label>.<root_domain>`. The maximum length is 50 characters. |  

  The SDDC Manager FQDN cannot be publicly resolvable. Otherwise, the Cloud Foundation instance configuration might fail and is not recoverable. Before you specify a domain name, review [Considerations when choosing a root domain name](../vmonic/trbl_limitations.html#considerations-when-choosing-a-root-domain-name-for-cloud-foundation-instances).

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
  * **Secondary Private VLAN** is for VMware features such as vSAN.
  * **Primary Subnet** is assigned to physical hosts for public network access.
  * **Private Primary Subnet** is assigned to physical hosts for management traffic.

**Important:**
* Ensure that the firewall configuration on the selected VLANs does not block the management data traffic.
* Ensure that all of the VLANs you select are in the same pod, because ESXi servers cannot be provisioned on mixed-pod VLANs.

## Services

When you order a Cloud Foundation instance, you can also order additional services. For more information about the available services, see [Services for Cloud Foundation instances](sd_planning.html#services-for-cloud-foundation-instances).

## Order summary

Based on your selected configuration for the instance and add-on services, the estimated cost is instantly generated and displayed in the right pane. Click **Pricing details** at the bottom of the right pane to generate a PDF document that provides the estimate details.

## Procedure

1. From the {{site.data.keyword.cloud_notm}} Catalog, click **VMware** from the left navigation pane and then click **Cloud Foundation** in the **Virtual Data Centers** section.
2. On the **VMware Cloud Foundation on IBM Cloud** page, click **Create**.
3. On the **Cloud Foundation** page, enter the instance name.
4. Select the instance type:
   * Click **Primary Instance** to deploy a single instance in the environment or to deploy the first instance in a multi-site topology.
   * Click **Secondary Instance** to connect the instance with an existing (primary) instance in the environment for high availability and complete the following steps:
     1. Select the primary instance that you want the secondary instance to be connected with.
     2. If the primary instance that you selected is upgraded to the V2.5 release, or the primary instance is deployed in or upgraded to V2.4 and previous releases, check the prefilled **Administrator Password for the Primary Instance PSC** to ensure that it is correct.
     
         **Note:** The **Administrator Password for the Primary Instance PSC** field is not available to primary instances that are 
       deployed in V2.5 and later releases.     
5. Complete the license settings for the instance components:
   *  To use IBM-provided licenses, select **Include with purchase**.
   *  To use your own license, select **I will provide** and enter the license key.  
6. Complete the Bare Metal Server settings:
   1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
   2. Select the Bare Metal Server configuration.
      * When you select **Preconfigured**, choose a configuration from **Small** and **Large**.
      * When you select **Customized**, specify the CPU model and the RAM size.
7. Complete the storage settings:
   * If you selected **Preconfigured** for the Bare Metal configuration, note that the storage settings for the **Small** and **Large** standardized Bare Metal Server configurations cannot be changed.
   * If you selected **Customized** for the Bare Metal configuration, specify the **Disk Type and Size for vSAN Capacity Disks** and **Number of vSAN Capacity Disks**.
8. Complete the network interface settings:
   1. Enter the host name prefix, subdomain label, and root domain name. For a secondary instance, the domain name is automatically filled in.
   2. Select the VLAN settings:
      * If you want to order new public and private VLANs, click **Order New VLANs**.
      * If you want to reuse the existing public and private VLANs when they are available, click **Select Existing VLANs** and specify the VLANs and the subnets.

9. Select the add-on services to deploy into the instance by clicking the corresponding service card. If a service requires configuration, complete the service-specific settings and click **Add Service** in the pop-up configuration window. For information about how to provide settings for a service, see the corresponding service ordering topic.

10. On the **Order Summary** pane, verify the instance configuration before you place the order.
    1. Review the settings for the instance.
    2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
    3. Ensure that the account to be charged is correct and then select the **I understand that the account listed below will be charged** check box.
    4. Click the link or links of the terms that apply to your order. Ensure that you agree with these terms and then select the **I have read and agreed to the Third-Party Service Agreements listed below** check box.
    5. Click **Provision**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in [Technical specifications for Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances) are installed on your VMware virtual platform. The ESXi servers that you ordered are grouped as **SDDC-Cluster** by default. If you ordered additional services, the deployment of the services starts after your order is completed.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.

## What to do next

View and manage the Cloud Foundation instance that you ordered.

**Important**: You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the {{site.data.keyword.slportal}} or any other means outside of the console. If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.

**CAUTION**: Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:

*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

   Exceptions to these activities include managing the shared storage file shares from the {{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

### Related links

* [Signing up for an {{site.data.keyword.cloud_notm}} account](../vmonic/signing_softlayer_account.html)
* [Viewing Cloud Foundation instances](sd_viewinginstances.html)
* [Adding, viewing, and deleting clusters for Cloud Foundation instances](sd_addingviewingclusters.html)
* [Expanding and contracting capacity for Cloud Foundation instances](sd_addingremovingservers.html)
* [Ordering, viewing, and removing services for Cloud Foundation instances](sd_addingremovingservices.html)
* [Deleting Cloud Foundation instances](sd_deletinginstance.html)
* [FAQ about BYOL](../vmonic/faq_byol.html)
