---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

{:tip: .tip}

# Ordering new vSphere clusters

To deploy a highly customizable VMware virtualized platform, order VMware vSphere on {{site.data.keyword.cloud}}. Use this procedure to define a new VMware vSphere cluster.

This workflow will guide you through VMware component, {{site.data.keyword.cloud_notm}} Bare Metal Server, and networking choices, to create a new cluster. After you place the order, the cluster configuration is captured so that you can come back and continue to scale out the cluster as needed. Once the order is completed, you can manually build the VMware cluster based on your requirements.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](../vmonic/useraccount.html).
*  You meet the requirements and you reviewed the considerations in [Requirements and planning for vSphere clusters](vs_planning.html).

## Main settings

When you order a new vSphere cluster, you must specify the following settings.

<!--**Important: Do not modify any values that are set during ordering and cluster deployment. Doing so can result in your cluster becoming unusable.**-->

### Cluster Configurations

Ensure that **New cluster** is selected in the **Cluster Configurations** list when you configure a new cluster.

### Cluster Name

The cluster name must be unique within your account.

### Domain Name

The domain name is used for all {{site.data.keyword.baremetal_short}} and must meet the following requirements:
* The name must consist of two or more strings that are separated by period (.)
* Only alphanumeric and dash (-) characters are allowed.
* Each string must start with an alphabetic character and end with an alphanumeric character, and the last string can contain only alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.
* The length of other strings must be in the range 1 - 63 characters.
* The maximum length of the domain name is 189 characters.

### Subdomain Label

The subdomain label must meet the following requirements:
*  Only alphanumeric and dash (-) characters are allowed.
*  The subdomain label must start and end with an alphanumeric character.
*  The maximum length of the subdomain label is 10 characters.
*  The subdomain label must be unique within your account.

### Host Name Prefix

The host name is used for all bare metal server orders. It is recommended to use the host name for all management virtual machines, such as vCenter Server, NSX, and so on.

The host name prefix must meet the following requirements:
* The name must start and end with an alphanumeric character.
* Only alphanumeric and dash (-) characters are allowed.
* The maximum length is 10 characters.

## VMware Components

Select VMware components to be ordered with your cluster.

### Component bundles

Business Partner users can now select from four component license bundles when ordering a new vSphere cluster. Select one of the following bundles:

Table 1. Business Partner component bundles for vSphere clusters

| Bundle | Components                   |
|:-------------------------|:-----------------------|
| Basic                    | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise                 |
| Advanced                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Advanced with Networking | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Enterprise               | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, NSX Enterprise |

You can also include the following additional VMware components to your order:
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

**Note:** Business Partner users do not have the option to Bring Your Own License. The **I will provide the license** option is not available when completing your order.

### Individual components

You can select the following VMware components to order with your cluster:
* VMware vSphere Enterprise Plus
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

**Note:** The VMware vSAN component is not available when you order VMware vSphere Enterprise Plus 6.0. If you plan to use your own license for VMware vSphere Enterprise Plus 6.0, an {{site.data.keyword.cloud_notm}} infrastructure ticket will be opened on your behalf requesting that the vSphere licenses of the ordered {{site.data.keyword.baremetal_short}} are replaced with your provided licenses.

You have the following options for licensing the selected VMware components:
* **Include license with purchase**: In this case, a new license for the VMware component is purchased on your behalf. A combined VMware license is generated to match the cluster size of the order.
* **I will provide the license**: In this case, you will use your own license for the VMware component.

If you choose to purchase any license, except for vSphere Enterprise Plus and vCenter Server, and you order multiple ESXi servers, an {{site.data.keyword.cloud_notm}} ticket is opened automatically on your behalf to combine license keys. You are responsible to follow up with the ticket to ensure that you use only the license keys that the DevOps team generates.

**Important**: Using individual license keys together with the combined license keys does not meet the payment requirements for the licenses you will need.

## Bare Metal Servers

Review the following details about your order, depending on whether you want to order the **VMware vSAN** component or not:
* For orders without vSAN, ESXi servers are ordered with a 12-disk chassis, with two disks for the ESXi operating system (OS).
* For orders with vSAN, ESXi servers are ordered with a 12-disk chassis and four disks ordered: two for the ESXi OS and two reserved for caching. These settings are configured by default and cannot be changed. You can order more capacity disks by selecting the **Number of vSAN Capacity Disks** in the **{{site.data.keyword.baremetal_short}}** section.
* For additional information about storage calculations depending on your other selections, see the details displayed under **vSAN Summary** on the console.

### IBM Cloud Data Center Location

Select the {{site.data.keyword.CloudDataCent_notm}} where the cluster is to be hosted.

**Note:** If you select a vSAN component, the location list is filtered by SSD availablity.

### Number of vSAN Capacity Disks

The number of disk drive values are displayed only for the VMware vSAN component. The disk quantity options include 2, 4, 6, and 8.

**Note:** This option applies only to the VMware vSAN component.

### Disk Type and Size for vSAN Capacity Disks

The following disk types are available for {{site.data.keyword.baremetal_short}}:
* 960 GB SSD SED
* 1.9 TB SSD SED
* 3.8 TB SSD SED

**Notes:**
* This option applies only to the VMware vSAN component.
* 3.8 TB SSD SED drives will be supported when they are made generally available in a data center.

### CPU Model

The following CPU models are available for {{site.data.keyword.baremetal_short}}:
* Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz
* Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz
* Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz

### RAM

The RAM options include 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1 TB, and 1.5 TB. Options available depend on whether you selected the VMware vSAN component.

### Number of Bare Metal Servers

The number of ESXi servers that you want add to the vSphere cluster. All the ESXi servers share the same configuration.
* If you selected the VMware NSX component, a minimum of 3 servers is required.
* If you selected the VMware vSAN component, a minimum of 4 servers is required.

## Network Details

Network settings are based on your selection of either **Order New VLANs** or **Select Existing VLANs**.

One public VLAN and two private VLANs are required for your cluster order. The two private VLANs are trunked into each Bare Metal Server.

### Order New VLANs

Select to order one new public VLAN and two new private VLANs.

### Select Existing VLANs

Depending on the {{site.data.keyword.CloudDataCent_notm}} that you selected, existing public and private VLANs might be available.

Select to reuse existing public and private VLANs and choose from the available VLANs and subnets.

**Important:**
* Ensure that the firewall configuration on the selected VLANs does not block the management data traffic.
* Ensure that all of the VLANs you select are in the same pod, because ESXi servers cannot be provisioned on mixed-pod VLANs.

You can also select whether to include the FortiGate Physical Appliance 300 Series HA Pair in your cluster.

## Procedure

1. Click **Getting Started** on the left navigation pane.
2. On the **VMware vSphere on IBM Cloud** card, click **Order Instance**.
   Ensure that you are on the **Create new cluster** tab and that **(New cluster)** is displayed in the **Cluster Configurations** list.
3. Enter the cluster name.
4. Enter the root domain name.
5. Enter the subdomain label.
6. Enter the ESXi server name prefix.
7. Select the VMware components.
   * Business Partner users only, select a license bundle and any additional available VMware components.
   * Other users, select the VMware vSphere version from the **VMware vSphere Enterprise Plus** list, and then specify the licensing option for it
    as follows:
      * If you want new licenses for this VMware component to be purchased on your behalf, select **Include license with purchase**.
      * If you want to use your own VMware licenses for this VMware component, select **I will provide the license**. An {{site.data.keyword.cloud_notm}} ticket is opened automatically on your behalf to request the default vSphere licenses on your ordered {{site.data.keyword.baremetal_short}} to be replaced with your provided licenses.
      **Note:** This option is not available to Business Partner users.

      **Important**: You are responsible to follow up with the ticket to ensure that you replace the vSphere license on the newly ordered ESXi servers so that the {{site.data.keyword.cloud_notm}} infrastructure grants the cancellation of the initially provided {{site.data.keyword.cloud_notm}} infrastructure vSphere license charge. To replace your ESXi vSphere license, see [Configure License Settings for an ESXi Host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}.

   3. Select other VMware components that you want to integrate with your cluster, specify the licensing options for them as
    follows, and select the edition for them if the option list is available:
      * If you want a new license to be purchased on your behalf for a component, select **Include license with purchase**.
      * If you want to use your own VMware license for a component, select **I will provide the license**.
8. Complete the Bare Metal Server configuration:
   1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the cluster.
   2. If you selected the VMware vSAN component, select the number of disk drives and the disk type.
   3. Select the CPU model.
   4. Select the RAM size.
   5. Select the number of {{site.data.keyword.baremetal_short}} to add to the cluster.
9. Complete the network configuration.
   1. If you want to reuse the existing public and private VLANs when they are available, click **Select Existing Public and Private VLANs**, and then select the public VLAN, the primary subnet, the private VLAN, the primary private subnet, and the secondary private VLAN.
   2. If you want new public and private VLANs to be provisioned, do not click **Select Existing Public and Private VLANs**.
   3. If you want a FortiGate high availability (HA) appliance to be installed on the public VLAN, select **Include with purchase** under
   **FortiGate Physical Appliance 300 Series HA Pair**.
10. Click **Next**.
11. On the **Summary** page, verify the cluster configuration before you place the order.
   1. Review the settings for the cluster.
   2. Click the link or links of the terms that apply to your order, and ensure that you agree with these terms before you continue.
   3. Review the estimated cost of the cluster by clicking the price link under **Estimated Cost**. To save or print your order
   summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   4. To save the cluster configuration as a template without placing an order, click **Save Configuration**.
   5. To place the order, click **Create**.

## Results

If you saved the cluster configuration as a template, you get a console notification that the configuration is saved successfully, and then you can find the template in the **Cluster Configurations** list on the **Basics** page.

If you placed an order, the deployment of the cluster starts automatically, and you receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

**Note**: Only the {{site.data.keyword.baremetal_short}} are ordered. You are responsible for installing and configuring various components after cluster deployment, such as VMware vCenter, VMware NSX, VMware vSAN.

## Related links

* [Ordering vSphere clusters based on existing configurations](vs_orderingbasedonexistingconfig.html)
* [Scaling existing clusters](vs_scalingexistingclusters.html)
* [Scaling clusters created outside of the console](vs_orderingforclustersoutside.html)
