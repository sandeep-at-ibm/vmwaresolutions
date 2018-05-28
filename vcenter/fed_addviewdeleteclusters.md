---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Adding, viewing, and deleting clusters for VMware Federal instances

The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default.

You can add clusters to your VMware Federal instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. When no longer needed, you can delete the added clusters from your instances.

**Availability**: The adding and deleting clusters feature is available only to instances that were deployed in (or upgraded to) V2.3 and later releases.

## Adding clusters to VMware Federal instances

You can add up to 10 clusters to an instance. When you add a cluster for a VMware Federal instance, you must specify the following settings.

### System settings
When you add a cluster for a VMware Federal instance, you must specify the following settings.

**Cluster name**

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the VMware Federal instance.

**Data center location**

The data center of the cluster is set to the data center of the VMware Federal instance by default.

**Note:** Only the WDC03 - Washington, DC {{site.data.keyword.CloudDataCent_notm}} is currently available for VMware Federal instances. This setting is automatically set to the default and disabled.

### Bare Metal settings

**Customized**

Specify the CPU model and RAM for the Bare Metal Server.

Table 1. Options for customized {{site.data.keyword.baremetal_short}}

| CPU options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.1 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.2 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.6 GHz | 64 GB, 128 GB, 256 GB, 512 GB |

**Number of Bare Metal Servers**

A minimum of 2 {{site.data.keyword.baremetal_short}} is required for a cluster.

For VMware Federal instances that are deployed in V2.3 or later, you can add up to 59 {{site.data.keyword.baremetal_short}} for a cluster, and you can add 1 - 59 ESXi servers at a time.

After deployment, you can create up to four more clusters. For vSAN storage settings, 4 servers are required for both the initial cluster and post-deployment clusters.

<!--When there are more than 51 ESXi servers in the initial cluster of an instance, the HCX on {{site.data.keyword.cloud_notm}} service cannot be installed into the instance. Because the HCX service requires 8 IPs in the vMotion subnet from the initial cluster, if the number of ESXi servers exceeds 51, no IPs in the vMotion subnet can be available for HCX service.-->

### Storage settings

Storage settings are based on your selection of vSAN, NFS, or custom NFS storage.

**vSAN storage**

For vSAN, specify the following storage options:

* **Disk Type and Size for vSAN Capacity Disks**: Select the capacity that meets your shared storage needs.
* **Number of vSAN Capacity Disks**: Select the number of disks for the vSAN shared storage that you want to add. The disk quantities must be 2, 4, 6, or 8.
* Select the VMware vSAN 6.6 license edition (Advanced or Enterprise).

If your initial cluster was vSAN, any additional vSAN clusters uses the same vSAN license and have the same configuration as the initial vSAN cluster. This is also true if any cluster in the instance has vSAN chosen to be deployed on it (initial or additional). The first time you are prompted for the vSAN license and the edition. The next time you select vSAN for an additional cluster, whatever you chose initially is reused.

**NFS storage**

For NFS, you can add file-level shared storage for your instance. Specify the following storage options:

* **Number of Shares**: Select the number of file shares for the NFS shared storage that you want to add. The number of file shares must be in the range of 1 to 32.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements. The performance levels available to you depend on the VMware that you select.

**Custom NFS storage**

For custom NFS storage, you can specify the settings for each individual share of the file-level shared storage. Specify the following options:

* **Add NFS**: Select for each file shares that you want to configure individually.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS per GB based on your workload requirements. The performance levels available to you depend on the VMware that you select.

Table 2. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share, and it is supported only for the following {{site.data.keyword.CloudDataCents_notm}}: AMS03, DAL09, DAL10, DAL12, DAL13, FRA02, HKG01, LON02, LON04, LON06, MEL01, MEX01, MON01, OSL01, PAR01, SJC03, SJC04, SYD01, TOK02, TOR01, WDC04, WDC06, and WDC07. |

### License settings

IBM-provided VMware licenses for the following:
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.3

## Procedure to add clusters to VMware Federal instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instance** table, click the instance that you want to add clusters to.

   **Note**: Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.

3. Click the **Infrastructure** tab and click **Add** at the upper-right corner of the **CLUSTERS** table.
4. Enter the cluster name.
5. Select the **CPU Model**, the amount of **RAM**, and the **Number of Bare Metal Servers** for the Bare Metal configuration.
6. Complete the storage configuration.
  * If you selected **vSAN Storage**, select the **Disk Type and Size for vSAN Capacity Disks**, the **Number of vSAN Capacity Disks**, and VMware vSAN license edition.
  * If you selected **NFS Storage**, select the **Number of Shares**, **Size**, and **Performance**.
  * If you selected **Custom NFS Storage**, click the **+** icon next to **Add NFS** for each file share that you want to configure individually and select the **Size** and **Performance** for each file share.
7. Select the license edition for VMware vSAN for the license configuration.
8. Click **Calculate Cost** and review the estimated cost of the cluster. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
9. Click **Add** to add your cluster.

## Results after adding clusters to VMware Federal instances

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** tab on the instance details page.
2. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

**Important**: You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.

## Viewing clusters in VMware Federal instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click an instance to view the clusters in it.
3. Click the **Infrastructure** tab. In the **CLUSTERS** table, view the summary about the clusters:
   * **Name**: The name of the cluster.
   * **ESXi Server**: The number of ESXi servers in the cluster.
   * **CPU**: The CPU specification of the ESXi servers in the cluster.
   * **Customized vSAN Disks**: The number of vSAN disks in the cluster, including the disk type and capacity.
   * **Memory**: The total memory size of the ESXi servers in the cluster.
   * **Data Center Location**: The data center where the cluster is hosted.
   * **Pod**: The pod where the cluster is deployed.
   * **Status**: The status of the cluster. The status can have one of the following values:
     <dl class="dl">
         <dt class="dt dlterm">Initializing</dt>
         <dd class="dd">The cluster is being created and configured.</dd>
         <dt class="dt dlterm">Modifying</dt>
         <dd class="dd">The cluster is being modified.</dd>
         <dt class="dt dlterm">Ready to Use</dt>
         <dd class="dd">The cluster is ready to use.</dd>
         <dt class="dt dlterm">Deleting</dt>
         <dd class="dd">The cluster is being deleted.</dd>
         <dt class="dt dlterm">Deleted</dt>
         <dd class="dd">The cluster is deleted.</dd>
     </dl>
   * **Actions**: Click the Delete icon to delete the cluster.
4. Click a cluster name to view the ESXi server, storage, and license details:

   **ESXi servers**

   * **Name**: The name of the ESXi server is in the format `<host_prefix><n>.<subdomain_label>.<root_domain>`, where:

      `host_prefix` is the host name prefix,
      `n` is the sequence of the ESXi server,
      `subdomain_label` is the subdomain label, and
      `root_domain` is the root domain name.

   * **Version**: The version of the ESXi server.
   * **Credentials**: The user name and password to access the ESXi server.
   * **Private IP**: The private IP address of the ESXi server.
   * **Status**: The status of the ESXi server, which can be one of the following values:
        <dl class="dl">
        <dt class="dt dlterm">Added</dt>
        <dd class="dd">The ESXi server is added and is ready for use. </dd>
        <dt class="dt dlterm">Adding</dt>
        <dd class="dd">The ESXi server is being added. </dd>
        <dt class="dt dlterm">Deleting</dt>
        <dd class="dd">The ESXi server is being deleted.</dd>
        </dl>

    **Storage**

    * **Name**: The data store name.
    * **Size**: The capacity of the storage.
    * **IOPS/GB**: The performance level of the storage.
    * **NFS/Portal**: The NFS version of the storage.
    * **Status**: The status of the storage, which can be one of the following values:
          <dl class="dl">
          <dt class="dt dlterm">Added</dt>
          <dd class="dd">The ESXi server is added and is ready for use. </dd>
          <dt class="dt dlterm">Adding</dt>
          <dd class="dd">The ESXi server is being added. </dd>
          <dt class="dt dlterm">Deleting</dt>
          <dd class="dd">The ESXi server is being deleted.</dd>
          </dl>

   **Licenses**

   * **License**: The license type.
   * **Order Type**: The license was IBM-provided or user-provided.
   * **License Edition**: The version and edition of the license.
   * **License Key**: The license key.
   * **Total Capacity (CPU)**: The total amount of CPU capacity for the license.
   * **Free Capacity (CPU)**: The amount of free CPU capacity for the license.


## Deleting clusters from VMware Federal instances

You might want to delete a cluster from an instance when it is no longer needed.

**Note**: Use this procedure to remove clusters from instances that are deployed in (or upgraded to) V2.3 and later releases.

### Before you delete

* Use this procedure to delete clusters from instances that are deployed in V2.3 or later releases.
* For clusters deployed in V2.2 or earlier instances, you must upgrade the instance to V2.3 to be able to delete the clusters that you added to the instance.
* You can delete a single cluster at a time. To delete multiple clusters, you must do it in sequence; waiting for the previous cluster to be deleted before you attempt to delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before deleting the cluster.
* When you delete a cluster, all VMs (virtual machines) from the cluster will also be deleted and they cannot be recovered. If you want to keep the VMs, migrate them to other clusters.
* The default cluster cannot be deleted.

## Procedure to delete clusters from VMware Federal instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance that you want to delete clusters from.

   **Note**: Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot remove clusters from the instance.

3. Click the **Infrastructure** tab. In the **CLUSTERS** table, locate the cluster that you want to delete and click the **Delete** icon.

## Related links

* [Viewing VMware Federal instances](vc_fed_viewinginstance.html)
* [Expanding and contracting capacity for VMware Federal instances](vc_fed_addingremovingservers.html)
