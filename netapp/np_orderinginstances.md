---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-28"

---

# Ordering NetApp ONTAP Select instances

To deploy a VMware virtualized platform with a dedicated and highly available software-define storage appliance, order a NetApp ONTAP Select instance.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](../vmonic/useraccount.html).
*  You meet the requirements and you reviewed the considerations in [Requirements and planning for NetApp ONTAP Select instances](np_planning.html).

**Important: Do not modify any values that are set during ordering and instance deployment. Doing so can result in your instance becoming unusable.**

## System settings

When you order a NetApp ONTAP Select instance, you must specify the following settings under **System**.

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
*  Only alphanumeric characters are allowed.
*  Each string must start with an alphabetic character and end with an alphanumeric character, and the last string can contain only alphabetic characters.
*  The length of the last string must be in the range 2 - 24 characters.

**Note:** The maximum length of the FQDN (Fully Qualified Domain Name) for hosts and VMs (virtual machines) is 50 characters. Domain names must accomodate for this maximum length.

### Subdomain prefix

The subdomain prefix must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The subdomain prefix must start and end with an alphanumeric character.
*  The maximum length of the subdomain prefix is 10 characters.
*  The subdomain prefix must be unique within your account.

### Host name prefix

The host name prefix must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The host name prefix must start and end with an alphanumeric character.
*  The maximum length of the host name prefix is 10 characters.

### Bare metal server configuration

You can select a bare metal server configuration depending on your requirements:
* **High Performance (Medium)** – Premium license / Dual Intel Xeon E5-2650 v4 (24 cores total, 2.2 GHz) / 128 GB RAM / Twenty Two 1.9 TB SSD drives capacity per node / Effective capacity of a 4-node cluster – 59 TB
* **High Performance (Large)** – Premium license / Dual Intel Xeon E5-2650 v4 (24 cores total, 2.2 GHz) / 128 GB RAM / Twenty Two 3.8 TB SSD drives capacity per node / Effective capacity of a 4-node cluster – 118 TB
* **High Capacity** – Standard license / Dual Intel Xeon E5-2650 v4 (24 cores total, 2.10 GHz) / 64 GB RAM / Ten 4 TB SATA drives capacity per node / Effective capacity of a 4-node cluster – 60 TB

**Note:** 3.8 TB SSD drives will be supported when they are made generally available in a data center.

<!--For guidance on what bare metal server configuration to choose, see the _Bill of Materials_ document in the [Architecture Center](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture/virtualizationRefArch){:new_window}.-->

### Number of bare metal servers

The number of ESXi servers of a NetApp ONTAP Select instance is 4 by default. You cannot change it. All the ESXi servers share the same configuration.

### Data center location

You must select the IBM Cloud data center where the instance is to be hosted. Only the data centers that meet the bare metal server specification you selected previously are displayed.

## Licensing settings

You must upload four NetApp licensing files, because each of the four bare metal servers requires one license. Contact your NetApp sales team to procure the appropriate licensing for your high performance or high capacity deployment.

## Procedure

1. Click **Getting Started** or **Order Instance** from the left navigation pane.
2. On the **NetApp ONTAP Select** card, click **Order Instance**.
3. On the **Basics** page under **System**, provide the following information:
   1. Enter the instance name.
   2. Enter the root domain name, subdomain prefix, and host name prefix.
   3. Select the bare metal server configuration.
   4. Review the number of bare metal servers, that is 4.
   5. Select the IBM Cloud data center to host the instance.
4. On the **Basics** page under **Licensing**, click **Add files** to upload four NetApp license files that are required by the four bare metal servers.  Click **Next**.
5. On the **Summary** page, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Click the link or links of the terms that apply to your order, and ensure that you agree with these terms before you order the instance.
   3. Review the estimated cost of the instance by clicking the price link under **Estimated Cost**. To save or print your order
   summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   4. Click **Place Order**.

## Results

The deployment of the instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the deployment by viewing the instance details.

When the instance is successfully deployed, the components that are described in [NetApp ONTAP Select instance components](../netapp/np_netappoverview.html#netapp-ontap-select-instance-components) are installed on your VMware virtual platform.

When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.

## What to do next

View and manage the NetApp ONTAP Select instance that you ordered.

**Important**: You must manage the {{site.data.keyword.vmwaresolutions_full}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the {{site.data.keyword.slportal}} or any other means outside of the console. If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.

**CAUTION**: Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Powering off components

   Exceptions to these activities include managing the shared storage file shares from the {{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

## Related links

* [Viewing NetApp ONTAP Select instances](np_viewinginstances.html)
* [Deleting NetApp ONTAP Select instances](np_deletinginstance.html)
* [NetApp ONTAP Documentation Center](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html){:new_window}
