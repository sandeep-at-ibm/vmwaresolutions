---

copyright:

  years:  2016, 2020

lastupdated: "2020-10-19"

keywords: vCenter Server add cluster, view cluster vCenter Server, delete cluster vCenter Server

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Adding, viewing, and deleting clusters for vCenter Server instances
{: #vc_addingviewingclusters}

You can add your own clusters to VMware vCenter Server instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. When no longer needed, delete the added clusters from your instances.

Starting with the V3.4 release, you can simultaneously add or delete a cluster while another cluster is being created or deleted.
{:note}

## Before you add clusters
{: #vc_addingviewingclusters-before-add}

* Whenever possible, add clusters by using the {{site.data.keyword.vmwaresolutions_full}} console. Changes that you make on the VMware vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. Therefore, add clusters to vCenter Server only for on-premises clusters or clusters that you cannot or do not plan to manage in the {{site.data.keyword.vmwaresolutions_short}} console.
* The number of clusters, hosts, and virtual machines (VMs) determines the maximum limit for the number of clusters you can add. You must remain within the VMware sizing guidelines and limits for your deployment. For more information about maximum limits, see [VMware Configuration Maximums](https://configmax.vmware.com/home){:external}.
* Ensure that you reviewed the [Edge services cluster](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-edge-services-cluster) section. In addition, for the edge services cluster, you cannot add more than one cluster in the same data center pod. If you are adding multiple edge services clusters in the same pod, the clusters would share a transit VLAN, which might cause subsequent issues with the Juniper vSRX installation.

## System settings
{: #vc_addingviewingclusters-adding-sys-settings}

When you add a cluster for a vCenter Server instance, you must specify the following settings.

### Cluster name
{: #vc_addingviewingclusters-adding-cluster-name}

The cluster name is set to **vcs-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify a new cluster name that meets the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The cluster name must start with a lowercase alphabetic character.
* The cluster name must end with a lowercase alphabetic or numeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server instance.

## Licensing settings
{: #vc_addingviewingclusters-adding-licensing-settings}

Review the following information and specify the licensing setting for the VMware vSphere component in the cluster:
* For Business Partner users, the vSphere license (Enterprise Plus edition) is included and purchased on your behalf.
* For users who are not Business Partners, you can use the IBM-provided VMware licenses for this component by selecting **Include with purchase**. Or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

### VMware Subscription Purchasing Program (SPP)
{: #vc_addingviewingclusters-lic-spp}

The **Use VMware Subscription Purchasing Program** option is available only to users who are billed in the US.
{:note}

If you select the **Use VMware Subscription Purchasing Program** option when you order your cluster, the option **Include with purchase** for all licenses will be set automatically and the **I will provide** (BYOL) option is not available.

## Bare metal server settings
{: #vc_addingviewingclusters-bare-metal-settings}

Options might differ depending on the version that your instance was initially deployed in. You can choose between the following server types: **Skylake**, **Cascade Lake**, or **SAP-certified**.

### Data center location
{: #vc_addingviewingclusters-adding-dc-location}

The {{site.data.keyword.cloud_notm}} data center location of the cluster is set to the {{site.data.keyword.cloud_notm}} data center of the vCenter Server instance by default. You can deploy the cluster to a different {{site.data.keyword.cloud_notm}} data center than the deployed instance, but you must ensure that the network latency between the two {{site.data.keyword.cloud_notm}} data centers is less than 150 ms. To check the network latency, you can use a tool such as [Looking Glass](http://lg.softlayer.com/){:external}.

If you deploy the cluster to a different {{site.data.keyword.cloud_notm}} data center or {{site.data.keyword.cloud_notm}} infrastructure pod, three extra VLANs are ordered for use with the ordered {{site.data.keyword.cloud_notm}} bare metal servers.

### Skylake
{: #vc_addingviewingclusters-adding-skylake}

For the **Skylake** setting, you have options for the **CPU model** and **RAM**. Available options might differ depending on the version that your instance was initially deployed in.

| CPU model options | RAM options for NSX-V | RAM options for NSX-T |
|:----------------- |:--------------------- |:--------------------- |
| Dual Intel Xeon Silver 4110 processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 1. Options for Skylake bare metal servers" caption-side="top"}

### Cascade Lake
{: #vc_addingviewingclusters-adding-cascade}

For the **Cascade Lake** setting, you have options for the **CPU model** and **RAM**.

| CPU model options | RAM options |
|:----------------- |:----------- |
| Dual Intel Xeon Silver 4210 processor / 20 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 processor / 32 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 processor / 40 cores total, 2.5 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Platinum 8260 processor / 48 cores total, 2.4 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Gold 6248 processor / 80 cores total, 2.5 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8260 processor / 96 cores total, 2.4 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
{: caption="Table 2. Options for Cascade Lake bare metal servers" caption-side="top"}

### SAP-certified
{: #vc_addingviewingclusters-adding-sap}

When you select **SAP-certified**, you cannot alter the CPU or RAM settings. For NSX-T SAP-certified, only Cascade Lake servers are supported.

Based on your requirements, select a bare metal server configuration from the following table:

| CPU model     | RAM options   |  
|:------------- |:------------- |
| Dual Intel Xeon Gold 6140 processor (Skylake) / 36 cores total, 2.3 GHz | 192 GB, 384 GB, 768 GB |
| Dual Intel Xeon Gold 5218 processor (Cascade, BI.S4.NW192) / 32 cores total, 2.3 GHz | 192 GB, 384 GB |
| Dual Intel Xeon Gold 6248 processor (Cascade, BI.S4.NW768) / 40 cores total, 2.5 GHz | 768 GB |
| Dual Intel Xeon Platinum 8280M processor (Cascade, BI.S4.NW1500) / 56 cores total, 2.70 GHz| 1.5 TB |
| Dual Intel Xeon Platinum 8280M processor (Cascade, BI.S4.NW3000) / 56 cores total, 2.70 GHz| 3 TB |
{: caption="Table 3. Options for SAP-certified bare metal servers - NetWeaver" caption-side="top"}
{: class="simple-tab-table"}
{: #simpletabtable1}
{: tab-title="NetWeaver"}
{: tab-group="SAP-certified Intel servers"}

| CPU model     | RAM options |  
|:------------- |:------------- |
| Dual Intel Xeon Gold 5218 processor (Cascade) / 32 cores total, 2.3 GHz | 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Dual Intel Xeon Gold 6248 processor (Cascade) / 40 cores total, 2.5 GHz| 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Dual Intel Xeon Platinum 8280M processor (Cascade) / 56 cores total, 2.70 GHz| 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8280M processor (Cascade) / 112 cores total, 2.70 GHz| 3 TB, 6 TB |
{: caption="Table 3. Options for SAP-certified bare metal servers - HANA" caption-side="top"}
{: #simpletabtable2}
{: tab-title="HANA"}
{: tab-group="SAP-certified Intel servers"}
{: class="simple-tab-table"}

### Number of bare metal servers
{: #vc_addingviewingclusters-adding-bare-metal-number}

* All servers that you order have the same configuration.
* For vSAN storage, you can order in the range 4 - 59 servers.
* For NFS storage, you can order between 1 (for NSX-V) or 2 (for NSX-T) and 59 servers. However, for production workloads, a minimum of two (for NSX-V) and three (for NSX-T) servers is recommended. For more information, see [Is a two-node vCenter Server instance highly available?](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions#is-a-two-node-vcenter-server-instance-highly-available)

## Storage settings
{: #vc_addingviewingclusters-adding-storage-settings}

Storage settings are based on your selection of {{site.data.keyword.cloud_notm}} bare metal server configuration and the storage type.

You can add NFS storage shares to an existing vSAN or NFS cluster. For more information, see [Adding NFS storage to vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances).
{:note}

### vSAN storage
{: #vc_addingviewingclusters-adding-vsan-storage}

If you are using vSAN storage, even though vSphere 6.7u3 might be selected, vSphere ESXi 6.7u2 will be installed.
{: note}

Specify the following vSAN options:

#### Disk type and size for vSAN capacity disks
{: #vc_addingviewingclusters-adding-vsan-storage-typesize-capdisks}

Select an option for the capacity disks that you need.

#### Number of vSAN capacity disks
{: #vc_addingviewingclusters-adding-vsan-storage-number-capdisks}

Specify the number of capacity disks that you want to add.

If you want to add more capacity disks, check the **High performance with Intel Optane** box. This option provides two extra capacity disk bays, which are useful for workloads that require less latency and higher IOPS throughput.

The **High performance with Intel Optane** option is available only for the Skylake and Cascade Lake CPU models.
{:note}

#### Disk size for vSAN cache disks
{: #vc_addingviewingclusters-adding-vsan-storage-size-cachedisks}

Review the **Disk size for vSAN cache disks** value. The value depends on whether you checked the **High performance with Intel Optane** box.

#### Number of vSAN cache disks
{: #vc_addingviewingclusters-adding-vsan-storage-number-cachedisks}

Review **Number of vSAN cache disks**. The value depends on whether you checked the **High performance with Intel Optane** box.

#### Enable vSAN deduplication and compression
{: #vc_addingviewingclusters-adding-vsan-storage-enable-comp}

vSAN storage depends on the number of servers and your total disk capacity.

If vSAN deduplication and compression are enabled (the default setting), a ratio of 3.5 is assumed. For example, 1 TB of data uses only 1/3.5 TB. Therefore, the **Total estimated usable storage** is greater than the **Total raw storage**.

The following table shows the values for **Total raw storage** and **Total estimated usable storage** when you enable vSAN deduplication and compression and when you do not enable it.

| Selected values      | If compression is enabled | If compression is not enabled |
|:-------------------- |:------------------------- |:----------------------------- |
| Number of bare metal servers: 4</br>Disk type and size for vSAN capacity disks: 1.9 TB SSD SED</br>Number of vSAN cache disks: 4 | Total raw storage: 30.40 TB</br>Total estimated usable storage: 55.52 TB | Total raw storage: 30.40 TB</br>Total estimated usable storage: 15.52 TB |
{: caption="Table 4. vSAN Storage values when vSAN deduplication and compression is enabled and not enabled" caption-side="top"}

#### vSAN license
{: #vc_addingviewingclusters-adding-vsan-storage-license}

Use the IBM-provided VMware license for the vSAN component by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

If your initial cluster was a vSAN cluster, any additional vSAN clusters use the same vSAN license and have the same configuration as the initial one. This is also true if any cluster (initial or additional) in the instance has vSAN chosen to be deployed on it. The first time you're prompted for the vSAN license (BYOL or purchased) and the edition. The next time that you select vSAN for a new cluster, the license that is chosen initially is reused.

### NFS storage
{: #vc_addingviewingclusters-adding-nfs-storage}

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
{: caption="Table 5. NFS performance level options" caption-side="top"}

### Local disks (NSX-V SAP-certified HANA only)
{: #vc_addingviewingclusters-adding-local-disks}

The **Local disks** option is enabled for the **SAP-certified** - **HANA** CPU generation only. If you selected the **Use VMware Subscription Purchasing Program** option, the **Local disks** option is disabled.
{:note}

Specify the following settings:
* **Local disk count**: Select the number of disks that you want to add. The first two disks are reserved, so a minimum of four disks is required.
* **Local disk type**: Select an option for the disk type that you need.

## Network interface settings
{: #vc_addingviewingclusters-adding-network-interface-settings}

When you add a cluster for a vCenter Server instance, you must specify the following network interface settings.

### Hostname prefix
{: #vc_addingviewingclusters-host-name}

You can use the default hostname prefix or specify a new one. When you specify a new hostname prefix, the hostname prefix must meet the following requirements:
- Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
- The hostname prefix must start with a lowercase alphabetic character.
- The hostname prefix must end with a lowercase alphabetic or numeric character.
- The maximum length of the hostname prefix is 10 characters.

### Enable private NICs only
{: #vc_addingviewingclusters-network}

Network interface card (NIC) enablement settings are based on your selection of either **Public and private network** or **Private network only**.

For NSX-V, the following add-on services require public NICs and are not available if you select the private option:
* F5 BIG-IP
* FortiGate Virtual Appliance

### Uplink speed
{: #vc_addingviewingclusters-uplink}

The **Uplink speed** option is not available to edge services clusters.
{:note}

The following options are provided for uplink speed:
* 10 GB: this option is selected by default.
* 25 GB: this option is available only when the vCenter Server instance meets the following requirements:
   * The vSphere version is 6.7.
   * The bare metal server is Cascade Lake.
   * The data center is DAL10 or WDC04.

### VLANs
{: #vc_addingviewingclusters-vlans}

Network settings are based on your selection of either **Order new VLANs** or **Select existing VLANs**.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each {{site.data.keyword.cloud_notm}} bare metal server.

#### Order new VLANs
{: #vc_addingviewingclusters-new-vlans}

Select to order one new public VLAN and two new private VLANs.

#### Select existing VLANs
{: #vc_addingviewingclusters-existing-vlans}

Depending on the {{site.data.keyword.cloud_notm}} data center that you selected, existing public and private VLANs might be available.

When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
* **Public VLAN** is for public network access. If you select the **Allocate a new one** option for this field, a new public VLAN is allocated automatically. This field is only available on the **Public and private network** tab.
* **Public primary subnet** is assigned to physical hosts for public network access. If you select the **Auto assigned** option for this field, a new public primary subnet is selected automatically and a new one is created if necessary. This field is only available on the **Public and private network** tab.
* **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}. If you select the **Allocate a new one** option for this field, a new private VLAN is allocated automatically.
* **Private primary subnet** is assigned to physical hosts for management traffic. If you select the **Auto assigned** option for this field, a new private primary subnet is selected automatically and a new one is created if necessary.
* **Secondary private VLAN** is for VMware features such as vSAN. You can select an existing secondary private VLAN or select to allocate a new one.

Ensure that the firewall configuration on the selected VLANs does not block the management data traffic. Also, ensure that all the VLANs that you select are in the same pod. ESXi servers cannot be provisioned on mixed-pod VLANs.
{:important}

Optionally, use **Advanced settings** to configure portable subnets for VLANs.

Use the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** tabs to specify the **Portable subnet** for each applicable purpose. If you select the **Allocate a new one** option for this field, a new portable subnet is allocated automatically.

**Notes**:
* You must complete the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** settings before you can configure portable subnets.
* The number of portable subnets is displayed on the **Advanced settings** button after you save the portable subnet settings. Click **Portable subnets settings** to edit the settings.
* The saved portable subnet settings are cleared if you change the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** settings.

{{site.data.keyword.vmwaresolutions_short}} takes control of the entire subnet and you can't use any IP addresses in the subnet.
{:important}

## Summary
{: #vc_addingviewingclusters-adding-order-summary}

Based on your selected configuration for the cluster, the estimated price is instantly generated and displayed in the **Summary** right pane. Click **Pricing details** to generate a PDF document with the price summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to add clusters to vCenter Server instances
{: #vc_addingviewingclusters-adding-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance that you want to add clusters to.

   Ensure that the instance is in the **Ready to use** status. Otherwise, you cannot add clusters to the instance.
   {:note}
3. Click **Infrastructure** on the left navigation pane and click **Add** on the upper-right corner of the **Clusters** table.
4. On the **Cluster** page, select the cluster type and billing option, and then enter the cluster name.
5. If you want to host the cluster in a different {{site.data.keyword.cloud_notm}} data center than the one that the instance is hosted in, under **Bare metal server**, select the **Select a different location** checkbox and choose the {{site.data.keyword.cloud_notm}} data center to host the instance.
6. Complete the bare metal configuration.
   * If you selected **Skylake** or **Cascade Lake**, specify the **CPU model**, the amount of **RAM**, and the **Number of bare metal servers**.
   * If you selected **SAP-certified** NetWeaver, select one of the preset configurations. If you selected **SAP-certified** HANA, specify the **CPU model** and **RAM**.
7. Complete the storage configuration.
  * If you select **vSAN storage**, specify the following values:
    * Disk type and size for the vSAN capacity disks
    * Number of vSAN capacity disks
    * Disk size for vSAN cache disks
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

### Results after you add clusters to vCenter Server instances
{: #vc_addingviewingclusters-adding-results}

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** page of the instance.
2. When the cluster is ready to use, its status changes to **Ready to use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.
{:important}

## Procedure to view clusters in vCenter Server instances
{: #vc_addingviewingclusters-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click an instance to view the clusters in it.
3. Click **Infrastructure** on the left navigation pane. In the **Clusters** table, view the summary about the clusters:
  * **Cluster name/type**: The name and type of the cluster.
  * **ESXi servers**: The number of ESXi servers in the cluster.
  * **Storage**: The type of storage that the cluster uses.
  * **Data center location**: The {{site.data.keyword.cloud_notm}} data center where the cluster is hosted.
  * **Pod**: The pod where the cluster is deployed.
  * **Networking**: Whether **Public and private network** or **Private network only**.
  * **Uplink speed**: Whether 10 GB or 25 GB.
  * **Status**: The status of the cluster. The status can have one of the following values:
     * Initializing: The cluster is being created and configured.
     * Modifying: The cluster is being modified.
     * Ready to use: The cluster is ready to use.
     * Deleting: The cluster is being deleted.
     * Deleted: The cluster is deleted.
  * **Actions**: Click the **Delete** icon to delete the cluster.
4. Click a cluster name to view the ESXi server, storage, and network interface details.

| Item | Description |
|:---- |:----------- |
| Name | The name of the ESXi server is in the following format: `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `n` is the sequence of the ESXi server. |
| Hardware | The hardware specification. |
| Credentials | The user name and password to access the ESXi server. |
| Private IP | The private IP address of the ESXi server. |
| Status | The status of the ESXi server, which can be one of the following values:<br> **Added** The ESXi server is added and is ready for use.<br> **Adding** The ESXi server is being added.<br> **Deleting** The ESXi server is being deleted. |
{: caption="Table 6. ESXi server details" caption-side="top"}
{: class="simple-tab-table"}
{: #table1}
{: tab-title="ESXi server details"}
{: tab-group="Cluster details"}

| Item | Description |
|:---- |:----------- |
| CPU | The CPU specification of the ESXi servers in the cluster. |
| Memory | The total memory size of the ESXi servers in the cluster. |
| Customized vSAN disks | The number of vSAN disks in the cluster, including the disk type and capacity. |
| vSAN cache disks | The type and number of vSAN cache disks. |
| Networking |The network interface card (NIC) enablement settings of either Public and Private Network or Private Network Only. |
{: caption="Table 6. Additional ESXi server details" caption-side="top"}
{: class="simple-tab-table"}
{: #table2}
{: tab-title="Additional ESXi server details"}
{: tab-group="Cluster details"}

| Item | Description |
|:---- |:----------- |
| Name | The data store name. |
| Size | The capacity of the storage. |
| IOPS/GB | The performance level of the storage. |
| NFS protocol | The NFS version of the storage. |
| Status | The storage status, which can be one of the following values:<br> **Added** The storage is added and is ready for use.<br> **Adding** The storage is being added.<br> **Deleting** The storage is being deleted. |
{: caption="Table 6. Storage details" caption-side="top"}
{: class="simple-tab-table"}
{: #table3}
{: tab-title="Storage details"}
{: tab-group="Cluster details"}

| Item | Description |
|:---- |:----------- |
| VLAN number | The unique VLAN number.  |
| Description | The description of the VLAN.  |
| Location | The data center location. |
| Primary route | The primary route of the VLAN. |
{: caption="Table 6. Network interface - VLAN details" caption-side="top"}
{: class="simple-tab-table"}
{: #table4}
{: tab-title="Network interface details"}
{: tab-group="Cluster details"}

Click **View resource** to access the VLAN details, including the subnet details and IP details.

| Item | Description |
|:---- |:----------- |
| Name | The subnet name. Click the name to access the subnet details. |
| Type | The type of subnet: primary or portable. |
| Description | The description of the subnet. |
{: caption="Table 7. Network interface - Subnet details" caption-side="top"}
{: class="simple-tab-table"}
{: #vlan-table1}
{: tab-title="Subnet details"}
{: tab-group="Network interface VLAN details"}

| Item | Description |
|:---- |:----------- |
| IP | The IP address. |
| Status | The status of the IP address. |
| Description |The description of the IP address.  |
{: caption="Table 7. Network interface - IP details" caption-side="top"}
{: class="simple-tab-table"}
{: #vlan-table2}
{: tab-title="IP details"}
{: tab-group="Network interface VLAN details"}

## Deleting clusters from vCenter Server instances
{: #vc_addingviewingclusters-deleting}

You might want to delete a cluster from an instance when it's no longer needed.

### Before you delete clusters
{: #vc_addingviewingclusters-deleting-prereq}

* Whenever possible, delete clusters by using the {{site.data.keyword.vmwaresolutions_short}} console because changes that you make on the VMware vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. Therefore, delete clusters from vCenter Server only for on-premises clusters or clusters that you can't or don't plan to manage in the {{site.data.keyword.vmwaresolutions_short}} console.
* You can delete only clusters that are added as part of day 2 operations. Clusters that are created during initial deployment can't be deleted.
* You can delete a single cluster at a time. To delete more than one cluster, you must do it in sequence. Wait for the previous cluster to be deleted before you delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before you delete the cluster.
* When you delete a cluster, all VMs from the cluster are also deleted and they can't be recovered. If you want to keep the VMs, migrate them to other clusters.
* You do not have to delete any services that are installed on the cluster, including services on an edge services cluster. The services are automatically deleted when you delete the cluster.

A 12-month commitment is required when you order the VMware HCX service. Your account continues to be charged for the HCX components if you delete a cluster before the end of 12-month commitment period. The 12-month commitment expiration date is available on the HCX details page. For more information about viewing service details, see [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:important}

### Procedure to delete clusters from vCenter Server instances
{: #vc_addingviewingclusters-deleting-procedure}
{: help}
{: support}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance that you want to delete clusters from.

   Ensure that the instance is in the **Ready to use** status. Otherwise, you can't delete clusters from the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane. In the **Clusters** table, locate the cluster that you want to delete and click the **Delete** icon next to the **Status** column.
4. In the **Delete cluster** window, confirm that you completed the migration of VMs to other clusters, if needed, and that you want to delete the cluster. Click **Delete**.

## Related links
{: #vc_addingviewingclusters-related}

* [Viewing vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservers)
