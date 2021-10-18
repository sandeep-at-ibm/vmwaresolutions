---

copyright:

  years:  2021

lastupdated: "2021-10-13"

keywords: vCenter Server add clusters, add cluster, vCenter Server cluster

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Adding clusters to vCenter Server single-zone instances
{: #vc_addingclusters}

You can add clusters to VMware vCenter Server® instances to expand the compute and storage capacity. Within a cluster, you can manage VMware ESXi™ servers for better resource allocation and high availability.

## Before you add clusters to vCenter Server single-zone instances
{: #vc_addingclusters-before}

* Adding clusters to vCenter Server instances with VMware vSphere® 6.5 is not supported.
* Whenever possible, add clusters by using the VMware Solutions console. Changes that you make on the VMware vSphere Web Client are not synchronized with the VMware Solutions console. Therefore, add clusters to vCenter Server only for on-premises clusters or clusters that you cannot or do not plan to manage in the VMware Solutions console.
* The number of clusters, hosts, and virtual machines (VMs) determines the maximum limit for the number of clusters you can add. You must remain within the VMware® sizing guidelines and limits for your deployment. For more information about maximum limits, see [VMware configuration maximums](https://configmax.vmware.com/home){: external}.
* You cannot add multiple edge services clusters in the same data center pod. If you add more than one edge services clusters in the same pod, the clusters share a transit VLAN, which might cause subsequent issues with the Juniper® vSRX installation. For more information, see [Edge services cluster](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-edge-services-cluster).
* You can add or delete a cluster while another cluster is being created or deleted.

## System settings
{: #vc_addingclusters-sys-settings}

When you add a cluster to a vCenter Server instance, you must specify the following settings.

### Cluster name
{: #vc_addingclusters-cluster-name}

The cluster name is set to **vcs-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify a new cluster name that meets the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The cluster name must start with a lowercase alphabetic character.
* The cluster name must end with a lowercase alphabetic or numeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server instance.

## Licensing settings
{: #vc_addingclusters-licensing-settings}

Review the following information and specify the licensing setting for the VMware vSphere component in the cluster:
* For Business Partner users, the vSphere license (Enterprise Plus edition) is included and purchased on your behalf.
* For users who are not Business Partners, you can use the IBM-provided VMware licenses for this component by selecting **Include with purchase**. Or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

### VMware Subscription Purchasing Program (SPP)
{: #vc_addingclusters-lic-spp}

The **Use VMware Subscription Purchasing Program** option is available only to users who are billed in the US.
{: note}

If you select the **Use VMware Subscription Purchasing Program** option when you order your cluster, the option **Include with purchase** for all licenses will be set automatically and the **I will provide** (BYOL) option is not available.

## Bare metal server settings
{: #vc_addingclusters-bare-metal-settings}

Options might differ depending on the version that your instance was initially deployed in. You can choose between the following server types: **Skylake**, **Cascade Lake**, or **SAP-certified**.

### Data center location
{: #vc_addingclusters-dc-location}

The {{site.data.keyword.cloud_notm}} data center location of the cluster is set to the {{site.data.keyword.cloud_notm}} data center of the vCenter Server instance by default. You can deploy the cluster to a different {{site.data.keyword.cloud_notm}} data center than the deployed instance, but you must ensure that the network latency between the two {{site.data.keyword.cloud_notm}} data centers is less than 150 ms. To check the network latency, you can use a tool such as [Looking Glass](http://lg.softlayer.com/){: external}.

If you deploy the cluster to a different {{site.data.keyword.cloud_notm}} data center or {{site.data.keyword.cloud_notm}} infrastructure pod, three extra VLANs are ordered for use with the ordered {{site.data.keyword.cloud_notm}} bare metal servers.

### Skylake
{: #vc_addingclusters-skylake}

For **Skylake** servers, you can choose the following CPU models and a supported RAM size, which depends on the NSX networking solution. Available options might differ depending on the version that your instance was initially deployed in.

Skylake servers are not supported for vSphere Enterprise Plus 7.0u1 instances.
{: note}

| CPU model | RAM options for NSX-V | RAM options for NSX-T |
|:--------- |:--------------------- |:--------------------- |
| Dual Intel® Xeon® Silver 4110 processor / 16 cores total, 2.10 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 processor / 28 cores total, 2.20 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.30 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 1. Options for Skylake bare metal servers" caption-side="top"}

### Cascade Lake
{: #vc_addingclusters-cascade}

For **Cascade Lake** servers, you can choose the following CPU models and a supported RAM size, which depends on the NSX networking solution.

| CPU model | RAM sizes for NSX-V | RAM sizes for NSX-T |
|:--------- |:------------------- |:------------------- |
| Dual Intel Xeon Silver 4210 processor / 20 cores total, 2.20 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 processor / 32 cores total, 2.30 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 processor / 40 cores total, 2.50 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Platinum 8260 processor / 48 cores total, 2.40 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Gold 6248 processor / 80 cores total, 2.50 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB | 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8260 processor / 96 cores total, 2.40 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB | 384 GB, 768 GB, 1.5 TB, 3 TB |
{: caption="Table 2. Options for Cascade Lake bare metal servers" caption-side="top"}

### SAP-certified
{: #vc_addingclusters-sap}

For **SAP-certified** servers, you have the following options:
* **NetWeaver**, for which the CPU and RAM size are preset.
* **HANA**, for which you can choose the CPU model and a supported RAM size, which depends on the NSX networking solution.

| CPU model     | RAM sizes   |
|:------------- |:----------- |
| Dual Intel Xeon Gold 5218 processor (Cascade Lake, BI.S4.NW192) / 32 cores total, 2.30 GHz | 192 GB |
| Dual Intel Xeon Gold 5218 processor (Cascade Lake, BI.S4.NW384) / 32 cores total, 2.30 GHz | 384 GB |
| Dual Intel Xeon Gold 6248 processor (Cascade Lake, BI.S4.NW768) / 40 cores total, 2.50 GHz | 768 GB |
| Dual Intel Xeon Platinum 8280M processor (Cascade Lake, BI.S4.NW1500) / 56 cores total, 2.70 GHz | 1.5 TB |
| Dual Intel Xeon Platinum 8280M processor (Cascade Lake, BI.S4.NW3000) / 56 cores total, 2.70 GHz | 3 TB |
{: caption="Table 3. Options for SAP-certified bare metal servers - NetWeaver" caption-side="top"}
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
{: caption="Table 3. Options for SAP-certified bare metal servers - HANA" caption-side="top"}
{: #simpletabtable2}
{: tab-title="HANA"}
{: tab-group="SAP-certified Intel servers"}
{: class="simple-tab-table"}

### Number of bare metal servers
{: #vc_addingclusters-bare-metal-number}

* All servers that you order have the same configuration.
* For vSAN™ storage, you can order in the range 4 - 59 servers.
* For NFS storage, you can order between 1 (for NSX-V) or 2 (for NSX-T™) and 59 servers. However, for production workloads, a minimum of two servers is recommended. For more information, see [Is a two-node vCenter Server instance highly available?](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions#is-a-two-node-vcenter-server-instance-highly-available)

## Storage settings
{: #vc_addingclusters-storage-settings}

Storage settings are based on your selection of {{site.data.keyword.cloud_notm}} bare metal server configuration and the storage type.

You can add NFS storage shares to an existing vSAN or NFS cluster. For more information, see [Adding NFS storage to vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingnfs).
{: note}

### vSAN storage
{: #vc_addingclusters-vsan-storage}

Specify the following vSAN options.

#### Size for vSAN capacity disks
{: #vc_addingclusters-vsan-storage-typesize-capdisks}

Select an option for the capacity disks that you need.

#### Number of vSAN capacity disks
{: #vc_addingclusters-vsan-storage-number-capdisks}

Specify the number of capacity disks that you want to add.

If you want to add more capacity disks, select the **High performance with Intel Optane** checkbox. This option provides two extra capacity disk bays, which are useful for workloads that require less latency and higher IOPS throughput.

The **High performance with Intel Optane** option is available only for vSphere 6 instances.
{: note}

#### Size for vSAN cache disks
{: #vc_addingclusters-vsan-storage-size-cachedisks}

Review the **Size for vSAN cache disks** value. The value depends on whether you checked the **High performance with Intel Optane** box.

#### Number of vSAN cache disks
{: #vc_addingclusters-vsan-storage-number-cachedisks}

Review **Number of vSAN cache disks**. The value depends on whether you checked the **High performance with Intel Optane** box.

#### Enable vSAN deduplication and compression
{: #vc_addingclusters-vsan-storage-enable-comp}

vSAN storage depends on the number of servers and your total disk capacity, and the use of deduplication and compression.

The amount of storage reduction from deduplication and compression depends on many factors, including the type of data stored and the number of duplicate blocks. Larger disk groups tend to provide a higher deduplication ratio. For more information, see [Using deduplication and compression](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vsan.doc/GUID-3D2D80CC-444E-454E-9B8B-25C3F620EFED.html){: external}.
{: note}

#### vSAN license
{: #vc_addingclusters-vsan-storage-lic}

Use the IBM-provided VMware license for the vSAN component by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

If your initial cluster was a vSAN cluster, any additional vSAN clusters use the same vSAN license and have the same configuration as the initial one. This is also true if any cluster (initial or additional) in the instance has vSAN chosen to be deployed on it. The first time you're prompted for the vSAN license (BYOL or purchased) and the edition. The next time that you select vSAN for a new cluster, the license that is chosen initially is reused.

### NFS storage
{: #vc_addingclusters-nfs-storage}

When you select **NFS storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. The number of file shares must be in the range of 1 to 100.

Specify the following NFS options:
* **Configure shares individually**: Select to specify different configuration settings for each file share.
* **Number of shares**: When want to use the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size (GB)**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (input/output operations per second) per GB based on your workload requirements.
* **Add shared storage icon**: Select to add individual file shares with different configuration settings.

Performance level details:

| Option        | Details       |
|:------------- |:------------- |
| 0.25 IOPS/GB | This option is designed for workloads that are not used often. Example applications include: vaulted data, hosting large databases with legacy data, or virtual disk images of virtual memory system as backup. |
| 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or VM disk images for a hypervisor. |
| 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
| 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |
{: caption="Table 4. NFS performance level options" caption-side="top"}

### Local disks (NSX-V SAP-certified HANA only)
{: #vc_addingclusters-local-disks}

The **Local disks** option is enabled for the **SAP-certified** - **HANA** CPU generation only. If you selected the **Use VMware Subscription Purchasing Program** option, the **Local disks** option is disabled.
{: note}

Specify the following settings:
* **Local disk count**: Select the number of disks that you want to add. The first two disks are reserved, so a minimum of four disks is required.
* **Local disk type**: Select an option for the disk type that you need.

## Network interface settings
{: #vc_addingclusters-network-interface-settings}

When you add a cluster for a vCenter Server instance, you must specify the following network interface settings.

### Hostname prefix
{: #vc_addingclusters-host-name}

You can use the default hostname prefix or specify a new one. When you specify a new hostname prefix, the hostname prefix must meet the following requirements:
- Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
- The hostname prefix must start with a lowercase alphabetic character.
- The hostname prefix must end with a lowercase alphabetic or numeric character.
- The maximum length of the hostname prefix is 10 characters.

### Networking type
{: #vc_addingclusters-network}

Network interface card (NIC) enablement settings are based on your selection of either **Public and private network** or **Private network only**.

For NSX-V, the following add-on services require public NICs and are not available if you select the private option:
* F5® BIG-IP®
* FortiGate® Virtual Appliance

### Uplink speed
{: #vc_addingclusters-uplink}

The **Uplink speed** option is not available to edge services clusters.
{: note}

The uplink speed provides two options:
* 10 Gb, which is selected by default.
* 25 Gb, which is available only for **Cascade Lake** and **SAP-certified** bare metal servers and for specific locations. The following table shows the available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:-------------------------------------------- |:------ |
| Dallas 10   \n Dallas 12  \n Dallas 13 | NA South |
| Frankfurt 02   \n Frankfurt 05   \n London 06   \n Paris 04   \n Paris 05   \n Paris 06 | Europe |
| Sydney 04   \n Sydney 05   \n Tokyo 02   \n Tokyo 04   \n Tokyo 05 | Asia-Pacific |
| Toronto 04   \n Washington DC 04   \n Washington DC 06   \n Washington DC 07 | NA East |
{: caption="Table 5. Available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed" caption-side="top"}

### VLANs
{: #vc_addingclusters-vlans}

Network settings are based on your selection of either **Order new VLANs** or **Select existing VLANs**.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each {{site.data.keyword.cloud_notm}} bare metal server.

#### Order new VLANs
{: #vc_addingclusters-new-vlans}

Select to order one new public VLAN and two new private VLANs.

#### Select existing VLANs
{: #vc_addingclusters-existing-vlans}

Depending on the {{site.data.keyword.cloud_notm}} data center that you selected, existing public and private VLANs might be available.

When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
* **Public VLAN** is for public network access. If you select the **Allocate a new one** option for this field, a new public VLAN is allocated automatically. This field is only available on the **Public and private network** tab.
* **Public primary subnet** is assigned to physical hosts for public network access. If you select the **Auto assigned** option for this field, a new public primary subnet is selected automatically and a new one is created if necessary. This field is only available on the **Public and private network** tab.
* **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}. If you select the **Allocate a new one** option for this field, a new private VLAN is allocated automatically.
* **Private primary subnet** is assigned to physical hosts for management traffic. If you select the **Auto assigned** option for this field, a new private primary subnet is selected automatically and a new one is created if necessary.
* **Secondary private VLAN** is for VMware features such as vSAN. You can select an existing secondary private VLAN or select to allocate a new one.

Ensure that the firewall configuration on the selected VLANs does not block the management data traffic. Also, ensure that all the VLANs that you select are in the same pod. ESXi servers cannot be provisioned on mixed-pod VLANs.
{: important}

Optionally, use **Advanced settings** to configure portable subnets for VLANs.

Use the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** tabs to specify the **Portable subnet** for each applicable purpose. If you select the **Allocate a new one** option for this field, a new portable subnet is allocated automatically.
**Notes**
* You must complete the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** settings before you can configure portable subnets.
* The number of portable subnets is displayed on the **Advanced settings** button after you save the portable subnet settings. Click **Portable subnets settings** to edit the settings.
* The saved portable subnet settings are cleared if you change the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** settings.

{{site.data.keyword.vmwaresolutions_short}} takes control of the entire subnet and you can't use any IP addresses in the subnet.
{: important}

## Summary
{: #vc_addingclusters-order-summary}

Based on your selected configuration for the cluster, the estimated price is instantly generated and displayed in the **Summary** right pane. Click **Pricing details** to generate a PDF document with the price summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to add clusters to vCenter Server single-zone instances
{: #vc_addingclusters-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance that you want to add clusters to.

   Ensure that the instance is in the **Ready to use** status. Otherwise, you cannot add clusters to the instance.
   {: note}

3. Click **Infrastructure** on the left navigation pane and click **Add** on the upper right of the **Clusters** table.
4. On the **Cluster** page, select the cluster type and billing option, and then enter the cluster name.
5. If you want to host the cluster in a different {{site.data.keyword.cloud_notm}} data center than the one that the instance is hosted in, under **Bare metal server**, select the **Select a different location** checkbox and choose the {{site.data.keyword.cloud_notm}} data center to host the instance.
6. Complete the bare metal configuration.
   * If you selected **Skylake** or **Cascade Lake**, specify the **CPU model**, the amount of **RAM**, and the **Number of bare metal servers**.
   * If you selected **SAP-certified** NetWeaver, select one of the preset configurations. If you selected **SAP-certified** HANA, specify the **CPU model** and **RAM**.
7. Complete the storage configuration.
   * If you select **vSAN storage**, specify the following values:
      * Size for the vSAN capacity disks
      * Number of vSAN capacity disks
      * Size for vSAN cache disks
      * Number of vSAN cache disks
      * vSAN license edition

      If you want more storage, check the **High performance with Intel Optane** box.

      By default, the **Enable vSAN deduplication and compression** box is selected. If you do not want to enable vSAN deduplication and compression, clear the checkbox.

   * If you select **NFS storage** and want to add and configure the same settings to all file shares, specify the **Number of shares**, **Size (GB)**, and **Performance**.
   * If you select **NFS storage** and want to add and configure file shares individually, select **Configure shares individually**. Then, click the **+** icon next to the **Add shared storage** label and select the **Size (GB)** and **Performance** for each file share. You must select at least one file share.
   * (NSX-V only) If you select **Local disks**, specify the local disk count and local disk type.
8. Complete the network interface settings.
9. Specify how the vSphere license key is provided:
   * For Business Partner users, the vSphere license (Enterprise Plus edition) is included and purchased on your behalf.
   * For users who are not Business Partners, you can select one of the following options:
      * If you want new licenses to be purchased on your behalf, select **Include with purchase** for the component.
      * If you want to use your own VMware license for the component, select **I will provide** and enter your license key.
10. Select the network setting of either **Public and private network** or **Private network only**.
11. On the **Summary** pane, verify the cluster configuration before you add the cluster.
    1. Review the settings for the cluster.
    2. Review the estimated price of the cluster. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
    3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you add the cluster.
    4. Click **Create**.

## Results after you add clusters to vCenter Server single-zone instances
{: #vc_addingclusters-results}

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** page of the instance.
2. When the cluster is ready to use, its status changes to **Ready to use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.
{: important}

## Related links
{: #vc_addingclusters-related}

* [Viewing vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservers)
