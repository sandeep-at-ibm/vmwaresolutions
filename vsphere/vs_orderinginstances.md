---

copyright:

  years:  2016, 2021

lastupdated: "2021-11-22"

keywords: vSphere order cluster, order vSphere, order vSphere cluster

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Ordering new vSphere clusters
{: #vs_orderinginstances}

To deploy a highly customizable VMware® virtualized platform, order a VMware vSphere® cluster.

This procedure guides you through the selection of VMware components, {{site.data.keyword.cloud}} bare metal server settings, storage settings, and networking choices, to create a new cluster. After you place the order, the cluster configuration is captured so that you can come back and continue to scale out the cluster as needed. After the order is completed, you can manually configure the VMware vSphere cluster based on your requirements.

## Requirements for vSphere clusters
{: #vs_orderinginstances-req}

Ensure that you complete the following tasks:
* If you are ordering an instance for the first time, complete the tasks in the **Before you begin** section on the ordering page. For more information, see [Setting up your environment for your first order](/docs/vmwaresolutions?topic=vmwaresolutions-completing_checklist).
* Review the requirements and considerations in [Requirements and planning for vSphere clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_planning).

## System settings
{: #vs_orderinginstances-sys-settings}

You must specify the following system settings when you order a new vSphere cluster.

### Cluster name
{: #vs_orderinginstances-cluster-name}

The cluster name is set to **vss-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify a cluster name with a maximum length of 30 characters.

## Licensing settings
{: #vs_orderinginstances-licensing-settings}

Select the VMware components to be ordered with your cluster and specify the licensing option for the components.

### Component bundles for IBM Business Partner users
{: #vs_orderinginstances-component-bundles-for-bp-users}

If you are an IBM Business Partner user, you can select a component license bundle when you order a new vSphere cluster. The following bundles are available:

| Bundle | Components |
|:------ |:---------- |
| Standard with Management | vSphere Enterprise Plus, VMware vCenter Server® Standard, vRealize® Log Insight™, vRealize Operations™ Enterprise |
| Advanced                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Advanced with Networking | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Advanced with Networking and Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX® Enterprise |
{: caption="Table 1. IBM Business Partner component bundles for vSphere clusters" caption-side="top"}

You can also include the following VMware components in your order:
* VMware vSAN™
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

For IBM Business Partner users, the Bring Your Own License (BYOL) option is not available.
{: note}

### Individual components for non-Business Partner users
{: #vs_orderinginstances-individual-components-for-non-bp-users}

If you're a non-Business Partner, you can select the following components for your vSphere cluster:
* VMware vSphere Enterprise Plus 7.0u2 or 6.7u3
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

The VMware vSAN component is not available when you order VMware vSphere Enterprise Plus 6. If you plan to use your own license for VMware vSphere Enterprise Plus 6, an {{site.data.keyword.cloud_notm}} infrastructure ticket is opened on your behalf. The ticket requests that the vSphere licenses of the ordered {{site.data.keyword.cloud_notm}} bare metal servers are replaced with your provided licenses.
{: note}

### Licensing options
{: #vs_orderinginstances-licensing-options}

Using individual license keys together with the combined license keys does not meet the payment requirements for the licenses you need.
{: important}

You have the following options for licensing the selected VMware components:
* **Include license with purchase**: In this case, a new license for the VMware component is purchased on your behalf. A combined VMware license is generated to match the cluster size of the order.

   If you choose to purchase any license, except for vSphere Enterprise Plus and vCenter Server, and you order multiple VMware ESXi™ servers, an {{site.data.keyword.cloud_notm}} ticket is opened automatically on your behalf to combine license keys. You are responsible to follow up with the ticket to ensure that you use only the license keys that the VMware Solutions Support team generates.

* **I will provide the license**: In this case, you use your own license (BYOL) for the VMware component. You do not enter your BYOL licenses when you create your order for the first time, but you do it later when the vSphere cluster is created.

## Bare metal server settings
{: #vs_orderinginstances-bare-metal-settings}

When you size the capacity of your servers, consider your current requirements and include extra capacity to accommodate anticipated growth. For more information about sizing properly, see [Exporting VMware inventory](/docs/vmwaresolutions?topic=vmwaresolutions-vmware-inventory-export).

### Data center location
{: #vs_orderinginstances-dc-location}

Select the {{site.data.keyword.cloud_notm}} data center where the cluster is to be hosted. If you select a vSAN component, the location list is filtered by SSD availability.

### Skylake
{: #vs_orderinginstances-skylake}

For **Skylake** servers, you can choose the following CPU models and a supported RAM size. Options available depend on whether you selected the VMware vSAN component.

Skylake servers are not supported for vSphere Enterprise Plus 7.0 instances.
{: note}

| CPU model     | RAM sizes     |
|:------------- |:------------- |
| Dual Intel® Xeon® Silver 4110 processor / 16 cores total, 2.10 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 processor / 28 cores total, 2.20 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.30 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Options for Skylake bare metal servers" caption-side="top"}

### Cascade Lake
{: #vs_orderinginstance-cascade}

For **Cascade Lake** servers, you can choose the following CPU models and a supported RAM size.

| CPU model     | RAM sizes     |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4210 processor / 20 cores total, 2.20 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 processor / 32 cores total, 2.30 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 processor / 40 cores total, 2.50 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Platinum 8260 processor / 48 cores total, 2.40 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Gold 6248 processor / 80 cores total, 2.50 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8260 processor / 96 cores total, 2.40 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
{: caption="Table 3. Options for Cascade Lake bare metal servers" caption-side="top"}

### SAP-certified
{: #vs_orderinginstances-sap}

The **SAP-certified** servers are not available if you selected VMware vSAN previously.
{: note}

For **SAP-certified** servers, you have the following options:
* **NetWeaver**, for which the CPU and RAM size are preset.
* **HANA**, for which you can choose the CPU model and a supported RAM size.

| CPU model     | RAM sizes |
|:------------- |:--------- |
| Dual Intel Xeon Gold 5218 processor (Cascade Lake, BI.S4.NW192) / 32 cores total, 2.30 GHz | 192 GB |
| Dual Intel Xeon Gold 5218 processor (Cascade Lake, BI.S4.NW384) / 32 cores total, 2.30 GHz | 384 GB |
| Dual Intel Xeon Gold 6248 processor (Cascade Lake, BI.S4.NW768) / 40 cores total, 2.50 GHz | 768 GB |
| Dual Intel Xeon Platinum 8280M processor (Cascade Lake, BI.S4.NW1500) / 56 cores total, 2.70 GHz | 1.5 TB |
| Dual Intel Xeon Platinum 8280M processor (Cascade Lake, BI.S4.NW3000) / 56 cores total, 2.70 GHz | 3 TB |
{: caption="Table 4. Options for SAP-certified bare metal servers - NetWeaver" caption-side="top"}
{: class="simple-tab-table"}
{: #simpletabtable1}
{: tab-title="NetWeaver"}
{: tab-group="SAP-certified Intel servers"}

| CPU model     | RAM sizes |
|:------------- |:--------- |
| Dual Intel Xeon Gold 5218 processor (Cascade Lake) / 32 cores total, 2.30 GHz | 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Dual Intel Xeon Gold 6248 processor (Cascade Lake) / 40 cores total, 2.50 GHz| 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Dual Intel Xeon Platinum 8280M processor (Cascade Lake) / 56 cores total, 2.70 GHz | 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8280M processor (Cascade Lake) / 112 cores total, 2.70 GHz | 3 TB, 6 TB |
{: caption="Table 4. Options for SAP-certified bare metal servers - HANA" caption-side="top"}
{: #simpletabtable2}
{: tab-title="HANA"}
{: tab-group="SAP-certified Intel servers"}
{: class="simple-tab-table"}

### Number of bare metal servers
{: #vs_orderinginstances-bare-metal-number}

The number of ESXi servers that you want add to the vSphere cluster. All the ESXi servers have the same configuration.

## Storage settings
{: #vs_orderinginstances-storage-settings}

For orders without vSAN, ESXi servers are ordered with a 12-disk chassis, with two disks for the ESXi operating system (OS).

For orders with vSAN, ESXi servers are ordered with a 12-disk chassis and two disks are ordered for caching. The ESXi OS is placed on a single M.2 solid-state drive that does not use a disk bay. These settings are configured by default and cannot be changed. You can order more capacity disks by selecting **Size for vSAN capacity disks** and **Number of vSAN capacity disks**.

If you select the VMware vSAN component for the cluster, specify the following settings:
* **Size for vSAN capacity disks** - Select an option for the capacity disks that you need.
* **Number of vSAN capacity disks** - Specify the number of capacity disks that you want to add.
* If you want to add more capacity disks, select the **High performance with Intel Optane** checkbox. This option provides two extra capacity disk bays, which are useful for workloads that require less latency and higher IOPS throughput.

   The **High performance with Intel Optane** option is available only for vSphere 6 instances, and for Skylake and dual-processor Cascade Lake CPU models.
   {: note}

* Review the **Size for vSAN cache disks** and **Number of vSAN cache disks** values. These values depend on whether you selected the **High performance with Intel Optane** checkbox.

### Enable vSAN deduplication and compression
{: #vs_orderinginstance-storage-enable-comp}

vSAN storage depends on the number of servers and your total disk capacity, and the use of deduplication and compression.

The amount of storage reduction from deduplication and compression depends on many factors, including the type of data stored and the number of duplicate blocks. Larger disk groups tend to provide a higher deduplication ratio. For more information, see [Using deduplication and compression](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vsan.doc/GUID-3D2D80CC-444E-454E-9B8B-25C3F620EFED.html){: external}.
{: note}

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

The subdomain label is not used for vSphere 7.0 instances.
{: note}

### Domain name
{: #vs_orderinginstances-domain-name}

The domain name is used for all {{site.data.keyword.cloud_notm}} bare metal servers and must meet the following requirements:
* For vSphere 7.0 instances, the domain name must consist of three or more strings that are separated by a period (.)
* For vSphere 6.7 instances, the domain name must consist of two or more strings that are separated by a period (.)
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* Each string must start with a lowercase alphabetic character and end with a lowercase alphabetic or numeric character.
* The last string can contain only lowercase alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.
* The length of the other strings must be in the range 1 - 63 characters.
* The maximum length of the domain name is 189 characters.

### Networking type
{: #vs_orderinginstances-public-private-network}

Network interface card (NIC) enablement settings are based on your selection of either **Public and private network** or **Private network only**.

### Uplink speed
{: #vs_orderinginstances-uplink}

The uplink speed provides two options:
* 10 Gb, which is selected by default.
* 25 Gb, which is available only for **Cascade Lake** and **SAP-certified** bare metal servers and for specific locations. The following table shows the available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:-------------------------------------------- |:------ |
| Dallas 10 \n Dallas 12 \n Dallas 13 | NA South |
| Frankfurt 02 \n Frankfurt 05 \n London 06 | Europe |
| Sydney 04 \n Sydney 05 \n Tokyo 02 \n Tokyo 04 \n Tokyo 05 | Asia-Pacific |
| Toronto 04 \n Washington DC 04 \n Washington DC 06 \n Washington DC 07 | NA East |
{: caption="Table 5. Available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed" caption-side="top"}

### VLANs
{: #vs_orderinginstances-vlans}

Network settings are based on your selection of either **Order new VLANs** or **Select existing VLANs**.

#### Order new VLANs
{: #vs_orderinginstances-new-vlans}

If you are ordering for a public and private network, one public VLAN and two private VLANs are required for your cluster order. The two private VLANs are trunked into each bare metal server.

If you are ordering for a private network, two private VLANs are only required for your cluster order.

#### Select existing VLANs
{: #vs_orderinginstances-existing-vlans}

Depending on the {{site.data.keyword.cloud_notm}} data center that you selected, existing public and private VLANs might be available.

When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
* **Public VLAN** is for public network access. If you select the **Allocate a new one** option for **Public VLAN**, a new primary public subnet is allocated automatically and cannot be modified.
* **Public primary subnet** is assigned to physical hosts for public network access.
* **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}. If you select the **Allocate a new one** option for **Private VLAN**, a new private primary subnet is allocated automatically and cannot be modified.
* **Private primary subnet** is assigned to physical hosts for management traffic.
* **Secondary private VLAN** is for VMware features such as vSAN. You can select an existing secondary private VLAN or select to allocate a new one.

##### Important
{: #vs_orderinginstances-important}

* Ensure that the firewall configuration on the selected VLANs does not block the management data traffic.
* Ensure that all VLANs that you select are in the same pod. ESXi servers cannot be provisioned on mixed-pod VLANs.

#### FortiGate Physical Appliance 300 Series HA Pair
{: #vs_orderinginstances-fortigate-physical-appliance}

You can also select whether to include the FortiGate Physical Appliance 300 Series HA Pair to secure your cloud environment. For more information, see [FortiGate Virtual Appliance overview](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations).

This option is only available for an order with both a public and private network.
{: note}

## Summary
{: #vs_orderinginstances-order-summary}

Based on your selected configuration, the estimated price is instantly generated and displayed in the **Summary** right pane. Click **Pricing details** to generate a PDF document with the price summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to order vSphere clusters
{: #vs_orderinginstances-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click the **VMware Solutions Dedicated** card in the **IaaS platforms** section.
2. On the **VMware Solutions Dedicated** page, click the **VMware vSphere** card. Ensure that you are on the **Create new** tab and that **New cluster** is displayed in the **Cluster configurations** list.
3. Enter the cluster name.
4. Select the VMware components:
   * If you are an IBM Business Partner, select a license bundle and any additional available VMware components.
   * If you are a non-Business Partner, select the component, edition if any, and specify the licensing option.

   When you choose to Bring Your Own License (BYOL) for VMware vSphere Enterprise Plus, an {{site.data.keyword.cloud_notm}} ticket is opened automatically on your behalf to request the default vSphere licenses on your ordered bare metal servers to be replaced with your provided licenses.   

       You are responsible to track the ticket so that you replace the vSphere license on the newly ordered ESXi servers. This way the {{site.data.keyword.cloud_notm}} infrastructure grants the cancellation of the initially provided {{site.data.keyword.cloud_notm}} infrastructure vSphere license charge. To replace your ESXi vSphere license, see [Configure license settings for an ESXi host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){: external}.
       {: important}
       
5. Complete the bare metal server settings:
   1. Select the {{site.data.keyword.cloud_notm}} data center to host the cluster.
   2. Select the bare metal server CPU generation.
      * For **Skylake**, **Cascade Lake**, or **SAP-certified** - **HANA** servers, specify the CPU model and the RAM size.
      * For **SAP-certified** - **NetWeaver** server, choose one of the preset configurations.
   3. Specify the number of bare metal servers.
6. If you selected the **VMware vSAN** component, complete the vSAN storage configuration.
   * If you want more storage, select the **High performance with Intel Optane** checkbox.
   * Specify the disk types for the capacity and cache disks, and the number of disks.
   * By default, the **Enable vSAN deduplication and compression** checkbox is selected. If you do not want to enable vSAN deduplication and compression, clear the checkbox.
7. Complete the network interface settings:
   1. Enter the host name prefix, subdomain label (vSphere 6.7u3 instances only), and domain name.
   2. Select the network setting of either **Public and private network** or **Private network only**.
   3. Select the uplink speed. The 25 Gb option is available for Cascade Lake servers and for specific data centers only.
   4. Select the network interface that you want to use.
      * If you want to order new public and private VLANs, click **Order new VLANs**.
      * If you want to reuse the existing public and private VLANs when they are available, click **Select existing VLANs** and specify the VLANs and optionally the subnets.
   5. If you are ordering public VLANs, specify whether to apply the FortiGate Physical Appliance 300 Series HA Pair to secure your cloud environment.
8. In the **Summary** pane, verify the cluster configuration and the estimated price.
   * To save the configuration as a template without placing an order, click **Save configuration**.
   * To place the order, ensure that the account to be charged is correct, review and accept the terms, and then click **Create**.

   Only the {{site.data.keyword.cloud_notm}} bare metal servers are installed. You are responsible for installing and configuring various components after cluster deployment, such as VMware vCenter, VMware NSX, VMware vSAN.
   {: note}

### Results after you order vSphere clusters
{: #vs_orderinginstances-results}

If you saved the cluster configuration as a template, you get a console notification that the configuration is saved successfully, and then you can find the template in the **Cluster configurations** list.

If you placed an order, the deployment of the cluster starts automatically, and you receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

The vSphere clusters, unlike the vCenter Server instances, are not displayed on the **Resources** page.
{: note}

## Related links
{: #vs_orderinginstances-related}

* [Ordering vSphere clusters based on existing configurations](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderingbasedonexistingconfig)
* [Scaling existing clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_scalingexistingclusters)
* [Scaling clusters created outside of the console](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderingforclustersoutside)
