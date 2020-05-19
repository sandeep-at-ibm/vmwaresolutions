---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-15"

keywords: vSphere order cluster, order vSphere, order vSphere cluster

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering new vSphere clusters
{: #vs_orderinginstances}

To deploy a highly customizable VMware virtualized platform, order a VMware vSphere cluster.

This procedure guides you through the selection of VMware components, {{site.data.keyword.cloud}} bare metal server settings, storage settings, and networking choices, to create a new cluster. After you place the order, the cluster configuration is captured so that you can come back and continue to scale out the cluster as needed. After the order is completed, you can manually configure the VMware vSphere cluster based on your requirements.

## Requirements
{: #vs_orderinginstances-req}

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount).
*  You reviewed the requirements and considerations in [Requirements and planning for vSphere clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_planning).

## System settings
{: #vs_orderinginstances-sys-settings}

You must specify the following system settings when you order a new vSphere cluster.

### Cluster name
{: #vs_orderinginstances-cluster-name}

The cluster name is set to **vss-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify a cluster name that meets the following requirements:
* Only alphanumeric characters are allowed.
* The maximum length of the cluster name is 128 characters.

## Licensing settings
{: #vs_orderinginstances-licensing-settings}

Select the VMware components to be ordered with your cluster and specify the licensing option for the components.

### Component bundles for IBM Business Partner users
{: #vs_orderinginstances-component-bundles-for-bp-users}

If you are an IBM Business Partner user, you can select a component license bundle when you order a new vSphere cluster. The following bundles are available:

| Bundle | Components                   |
|:------------------------- |:----------------------- |
| Standard with Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Advanced                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Advanced with Networking | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Advanced with Networking and Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |
{: caption="Table 1. IBM Business Partner component bundles for vSphere clusters" caption-side="top"}

You can also include the following VMware components in your order:
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

For IBM Business Partner users, the Bring Your Own License (BYOL) option is not available.
{:note}

### Individual components for non-Business Partner users
{: #vs_orderinginstances-individual-components-for-non-bp-users}

If you're a non-Business Partner, you can select the following components for your vSphere cluster:
* VMware vSphere Enterprise Plus 6.7 U2, or 6.5 U2
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

The VMware vSAN component is not available when you order VMware vSphere Enterprise Plus 6.0. If you plan to use your own license for VMware vSphere Enterprise Plus 6.0, an {{site.data.keyword.cloud_notm}} infrastructure ticket is opened on your behalf. The ticket requests that the vSphere licenses of the ordered {{site.data.keyword.cloud_notm}} bare metal servers are replaced with your provided licenses.
{:note}

### Licensing options
{: #vs_orderinginstances-licensing-options}

You have the following options for licensing the selected VMware components:
* **Include license with purchase**: In this case, a new license for the VMware component is purchased on your behalf. A combined VMware license is generated to match the cluster size of the order.
* **I will provide the license**: In this case, you use your own license for the VMware component.

If you choose to purchase any license, except for vSphere Enterprise Plus and vCenter Server, and you order multiple ESXi servers, an {{site.data.keyword.cloud_notm}} ticket is opened automatically on your behalf to combine license keys. You are responsible to follow up with the ticket to ensure that you use only the license keys that the DevOps team generates.

Using individual license keys together with the combined license keys does not meet the payment requirements for the licenses you will need.
{:important}

## Bare metal server settings
{: #vs_orderinginstances-bare-metal-settings}

When you size the capacity of your servers, consider your current requirements and include extra capacity to accommodate anticipated growth. For more information about sizing properly, see [Exporting VMware inventory](/docs/vmwaresolutions?topic=vmwaresolutions-vmware-inventory-export).

### Data center location
{: #vs_orderinginstances-dc-location}

Select the {{site.data.keyword.cloud_notm}} data center where the cluster is to be hosted.

#### Notes
{: #vs_orderinginstances-notes}

* If you select a vSAN component, the location list is filtered by SSD availability.
* Broadwell bare metal servers are not available for the **FRA05 - Frankfurt** data center location.
* SAP-certified and Broadwell bare metal servers are not available for the **LON05 - London** data center location.

### Skylake
{: #vs_orderinginstances-skylake}

When you select **Skylake**, you can choose the CPU and RAM combination for the bare metal server according to your needs. Options available depend on whether you selected the VMware vSAN component.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Options for Skylake bare metal servers" caption-side="top"}

### Cascade Lake
{: #vs_orderinginstance-cascade}

For the **Cascade Lake** setting, you have options for the **CPU Model** and **RAM**.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4210 Processor / 20 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 Processor / 32 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 Processor / 40 cores total, 2.5 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Gold 6248 Processor[^vsphere] / 80 cores total, 2.5 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
{: caption="Table 3. Options for Cascade Lake bare metal servers" caption-side="top"}
[^vsphere]: If you use vSAN storage, the 4-CPU Intel Cascade Lake server Quad Intel Xeon Gold 6248 does not currently support the High Performance Intel Optane option.

### SAP-certified
{: #vs_orderinginstances-sap}

The **SAP-certified** tab is not available if you selected VMware vSAN previously. When you select **SAP-certified**, you cannot alter the CPU or RAM settings.

Based on your requirements, select a bare metal server configuration:

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Gold 5218 Processor / 32 cores total, 2.3 GHz | 192 GB, 384 GB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 192 GB, 384 GB, 768 GB |
| Dual Intel Xeon Gold 6248 Processor / 40 cores total, 2.5 GHz | 768 GB |
| Dual Intel Xeon Platinum 8280M Processor / 56 cores total, 2.7 GHz | 1.5 TB, 3 TB |
| Quad Intel Xeon E7-8890 v4 Processor / 96 cores total, 2.2 GHz | 1 TB, 2 TB, 4 TB |
{: caption="Table 4. Options for SAP-certified bare metal servers" caption-side="top"}

### Broadwell
{: #vs_orderinginstances-broadwell}

When you select **Broadwell**, you can choose the CPU and RAM combination for the bare metal server according to your needs. Options available depend on whether you selected the VMware vSAN component.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 cores total, 2.0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Table 5. Options for Broadwell bare metal servers" caption-side="top"}

### Number of bare metal servers
{: #vs_orderinginstances-bare-metal-number}

The number of ESXi servers that you want add to the vSphere cluster. All the ESXi servers have the same configuration.
* If you selected the VMware NSX component, a minimum of three servers is required.
* If you selected the VMware vSAN component, a minimum of four servers is required.

## Storage settings
{: #vs_orderinginstances-storage-settings}

For orders without vSAN, ESXi servers are ordered with a 12-disk chassis, with two disks for the ESXi operating system (OS).

For orders with vSAN, ESXi servers are ordered with a 12-disk chassis and two disks ordered for caching. The ESXi OS is placed on a single M.2 solid state drive that does not consume a disk bay. These settings are configured by default and cannot be changed. You can order more capacity disks by selecting **Disk Type and Size for vSAN Capacity Disks** and **Number of vSAN Capacity Disks**.

If you select the VMware vSAN component for the cluster, specify the following settings:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add more capacity disks, select the **High Performance with Intel Optane** check box. This option provides two extra capacity disk bays, which is useful for workloads that require less latency and higher IOPS throughput.

  The **High Performance with Intel Optane** option is available only for the Skylake and Cascade Lake CPU models.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you selected the **High Performance with Intel Optane** check box.

## Network interface settings
{: #vs_orderinginstances-network-interface-settings}

You must specify the following network interface settings when you order a new vSphere cluster.

### Host name prefix
{: #vs_orderinginstances-host-name-prefix}

The host name is used for all {{site.data.keyword.cloud_notm}} bare metal server orders. It is recommended to use the host name for all management virtual machines, such as vCenter Server and NSX.

The host name prefix must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The host name prefix must start with a lowercase alphabetic character.
* The host name prefix must end with a lowercase alphabetic or numeric character.
* The maximum length of the host name prefix is 10 characters.

### Subdomain label
{: #vs_orderinginstances-subdomain-label}

The subdomain label must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The subdomain label must start with a lowercase alphabetic character.
* The subdomain label must end with a lowercase alphabetic or numeric character.
* The maximum length of the subdomain label is 10 characters.

### Domain name
{: #vs_orderinginstances-domain-name}

The domain name is used for all {{site.data.keyword.cloud_notm}} bare metal servers and must meet the following requirements:
* The domain name must consist of two or more strings that are separated by period (.)
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* Each string must start with a lowercase alphabetic character and end with a lowercase alphabetic or numeric character.
* The last string can contain only lowercase alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.
* The length of the other strings must be in the range 1 - 63 characters.
* The maximum length of the domain name is 189 characters.

### Public or private network
{: #vs_orderinginstances-public-private-network}

Network interface card (NIC) enablement settings are based on your selection of either **Public and Private Network** or **Private Network Only**.

### VLANs
{: #vs_orderinginstances-vlans}

Network settings are based on your selection of either **Order New VLANs** or **Select Existing VLANs**.

#### Order New VLANs
{: #vs_orderinginstances-new-vlans}

If you are ordering for a public and private network, one public VLAN and two private VLANs are required for your cluster order. The two private VLANs are trunked into each bare metal server.

If you are ordering for a private network, two private VLANs are only required for your cluster order.

#### Select Existing VLANs
{: #vs_orderinginstances-existing-vlans}

Depending on the {{site.data.keyword.cloud_notm}} data center that you selected, existing public and private VLANs might be available.

When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
* **Public VLAN** is for public network access. If you select the **Allocate a new one** option for **Public VLAN**, a new primary public subnet is allocated automatically and cannot be modified.
* **Public Primary Subnet** is assigned to physical hosts for public network access.
* **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}. If you select the **Allocate a new one** option for **Private VLAN**, a new private primary subnet is allocated automatically and cannot be modified.
* **Private Primary Subnet** is assigned to physical hosts for management traffic.
* **Secondary Private VLAN** is for VMware features such as vSAN. You can select an existing secondary private VLAN or select to allocate a new one.

##### Important
{: #vs_orderinginstances-important}

* Ensure that the firewall configuration on the selected VLANs does not block the management data traffic.
* Ensure that all VLANs that you select are in the same pod. ESXi servers cannot be provisioned on mixed-pod VLANs.

#### FortiGate Physical Appliance 300 Series HA Pair
{: #vs_orderinginstances-fortigate-physical-appliance}

You can also select whether to include the FortiGate Physical Appliance 300 Series HA Pair to secure your cloud environment. For more information, see [FortiGate Virtual Appliance overview](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations).

This option is only available for an order with both a public and private network.
{:note}

## Order summary
{: #vs_orderinginstances-order-summary}

Based on your selected configuration, the estimated cost is instantly generated and displayed in the **Order Summary** right pane. Click **Pricing details** to generate a PDF document with the cost summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the cost of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to order vSphere clusters
{: #vs_orderinginstances-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
1. In the **Start Provisioning** section, click the **VMware Solutions Dedicated** card.
1. On the **VMware Solutions Dedicated** page, click the **VMware vSphere** card. Ensure that you are on the **Create New** tab and that **New cluster** is displayed in the **Cluster Configurations** list.
1. Enter the cluster name.
1. Select the VMware components:
  * If you are an IBM Business Partner, select a license bundle and any additional available VMware components.
  * If you are a non-Business Partner, select the component, edition if any, and specify the licensing option.
  When you choose to Bring Your Own License (BYOL) for VMware vSphere Enterprise Plus, an {{site.data.keyword.cloud_notm}} ticket is opened automatically on your behalf to request the default vSphere licenses on your ordered bare metal servers to be replaced with your provided licenses.   

    **Important:** You are responsible to track the ticket so that you replace the vSphere license on the newly ordered ESXi servers. This way the {{site.data.keyword.cloud_notm}} infrastructure grants the cancellation of the initially provided {{site.data.keyword.cloud_notm}} infrastructure vSphere license charge. To replace your ESXi vSphere license, see [Configure License Settings for an ESXi Host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:external}.
1. Complete the bare metal server settings:
   1. Select the {{site.data.keyword.cloud_notm}} data center to host the cluster.
   1. Select the bare metal server configuration.
      * When you select **Skylake**, **Cascade Lake**, or **Broadwell**, specify the CPU model and the RAM size.
      * When you select **SAP-certified**, choose one of the preset configurations.
   1. Specify the number of bare metal servers.
1. If you selected the **VMware vSAN** component, complete the vSAN storage configuration. Specify the disk types for the capacity and cache disks, and the number of disks. If you want more storage, select the **High Performance with Intel Optane** check box.
1. Complete the network interface settings:
   1. Enter the host name prefix, subdomain label, and domain name.
   1. Select the network setting of either **Public and Private Network** or **Private Network Only**.
   1. Select the network interface that you want to use.
    * If you want to order new public and private VLANs, click **Order New VLANs**.
    * If you want to reuse the existing public and private VLANs when they are available, click **Select Existing VLANs** and specify the VLANs and optionally the subnets.
    1. If you are ordering public VLANS, specify whether to apply the FortiGate Physical Appliance 300 Series HA Pair to secure your cloud environment.
1. In the **Order Summary** pane, verify the cluster configuration and the estimated cost.
   * To save the configuration as a template without placing an order, click **Save Configuration**.
   * To place the order, ensure that the account to be charged is correct, review and accept the terms, and then click **Provision**.

   Only the {{site.data.keyword.cloud_notm}} bare metal servers are installed. You are responsible for installing and configuring various components after cluster deployment, such as VMware vCenter, VMware NSX, VMware vSAN.
   {:note}

### Results after you order vSphere clusters
{: #vs_orderinginstances-results}

If you saved the cluster configuration as a template, you get a console notification that the configuration is saved successfully, and then you can find the template in the **Cluster Configurations** list.

If you placed an order, the deployment of the cluster starts automatically, and you receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

The vSphere clusters, unlike the vCenter Server instances, are not displayed on the **Resources** page.
{:note}

## Related links
{: #vs_orderinginstances-related}

* [Ordering vSphere clusters based on existing configurations](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderingbasedonexistingconfig)
* [Scaling existing clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_scalingexistingclusters)
* [Scaling clusters created outside of the console](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderingforclustersoutside)
