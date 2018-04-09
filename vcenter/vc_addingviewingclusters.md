---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-06"

---

# Adding and viewing clusters for vCenter Server instances

You can add clusters to your VMware vCenter Server instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. Use this procedure to add or view clusters for the vCenter Server instances that you ordered.

## Before you begin

The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default. You can add up to 10 clusters to instances that are deployed in or upgraded to V2.2. and later releases. Instances deployed prior to V2.2 can add up to 5 clusters.

When you add a cluster for a vCenter Server instance, you must specify or review the following settings.

## System settings

Specify the following settings under **System**.

### Cluster Name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server instance.

### Data Center Location

The {{site.data.keyword.CloudDataCent}} location of the cluster is set to the {{site.data.keyword.CloudDataCent_notm}} of the vCenter Server instance by default. You can deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} than the deployed instance, but you must ensure that the network latency between the two {{site.data.keyword.CloudDataCents_notm}} is less than 150 ms. To check the network latency, you can use a tool such as [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

If you deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} or {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) pod, three additional VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

## Bare Metal settings

Bare Metal settings are based on your selection of either **Customized** or **Preconfigured**.

### Customized

Specify the **CPU Model**, **RAM** for the Bare Metal Server.

Table 1. Options for customized Bare Metal Servers

| CPU options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 96 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |

### Preconfigured

Based on your requirements, select a **Bare Metal Server Configuration** from the drop down box:
* Small (Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz / 128 GB RAM / 2 disks)
* Medium (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz / 256 GB RAM / 2 disks)
* Large (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz / 512 GB RAM / 2 disks)

### Number of Bare Metal Servers

A minimum of 2 {{site.data.keyword.baremetal_short}} is required for a cluster.

For vCenter Server instances that are deployed in V2.1 or later, you can add up to 59 {{site.data.keyword.baremetal_short}} for a cluster, and you can add 1 - 59 ESXi servers at a time.

For vCenter Server instances that were deployed in V2.0 or earlier, you can add up to 32 {{site.data.keyword.baremetal_short}} for a cluster. The number of the {{site.data.keyword.baremetal_short}} that you can add at a time is as follows:
* For the **Small**, **Medium**, and **Large** Bare Metal Server configurations, you can add 1 - 10 ESXi servers at a time.
* For the **Customized** Bare Metal Server configuration, you can add 1 - 20 ESXi servers at a time.

After deployment, you can create up to four more clusters. If you select the **Customized** Bare Metal Server configuration with VMware vSAN storage, 4 servers are required for both the initial cluster and post-deployment clusters.

When there are more than 51 ESXi servers in the initial cluster of an instance, the HCX on {{site.data.keyword.cloud_notm}} service cannot be installed into the instance. Because the HCX service requires 8 IPs in the vMotion subnet from the initial cluster, if the number of ESXi servers exceeds 51, no IPs in the vMotion subnet can be available for HCX service.

## Storage settings

Storage settings are based on your selection of either **vSAN** or **NFS**.

### vSAN

vSAN is available only if you select the **Customized** Bare Metal configuration. Specify the following storage options:

* **Number of vSAN Capacity Disks**: Specify the number of disks for the vSAN shared storage that you want to add. The disk quantities must be 2, 4, 6, or 8.
* **Disk Type and Size for vSAN Capacity Disks**: Select the capacity that meets your shared storage needs.

If your initial cluster was vSAN, any additional vSAN clusters uses the same vSAN license and have the same configuration as the initial vSAN cluster. This is also true if any cluster in the instance has vSAN chosen to be deployed on it (initial or additional). The first time you are prompted for the vSAN license (BYOL or purchased) and the edition. The next time you select vSAN for an additional cluster, whatever you chose initially is reused.

### NFS

For NFS, you can add file-level shared storage for your instance. Specify the following storage options:

* **File Shares**: Specify the number of file shares for the NFS shared storage that you want to add. The number of file shares must be in the range of 1 to 32.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements. The performance levels available to you depend on the {{site.data.keyword.CloudDataCent_notm}} that you select.
* **Configure shares individually**: Optionally select to complete individual file share configuration.
* **Add NFS**: Optionally select if you are configuring your file shares individually and need to add additional file shares.

Table 2. NFS performance level options

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
  | 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
  | 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share, and it is supported only for the following {{site.data.keyword.CloudDataCents_notm}}: AMS03, DAL09, DAL10, DAL12, DAL13, FRA02, HKG01, LON02, LON04, LON06, MEL01, MEX01, MON01, OSL01, PAR01, SJC03, SJC04, SYD01, TOK02, TOR01, WDC04, WDC06, and WDC07. |

<!--### NFS Version

NFS (Network File System) v3 is set by default and you cannot change it. NFS v3 supports SDRS (Storage Distributed Resource Scheduler) and SIOC (Storage I/O Control), but does not include NFS multipathing.-->

## License settings

You can choose to use the IBM-provided VMware licenses or Bring Your Own License (BYOL) for the following:

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced, or Enterprise) 6.3
* Optional license: VMware vSAN (Advanced or Enterprise) 6.6

## Procedure

1. Click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to view the clusters in it or to add clusters to it.

   **Note**: If you want to add clusters to this instance, ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.
3. Click the **Infrastructure** tab. View the summary about the clusters:
   * **Name**: The name of the cluster.
   * **ESXi Servers**: The number of ESXi servers in the cluster.
   * **CPU**: The CPU specification of the ESXi servers in the cluster.
   * **Customized vSAN Disks**: The number of vSAN disks in the cluster, including the disk type and capacity.
   * **Memory**: The total memory size of the ESXi servers in the cluster.
   * **Data Center Location**: The {{site.data.keyword.CloudDataCent_notm}} where the cluster is hosted.
   * **Pod**: The pod where the cluster is deployed.
   * **Status**: The status of the cluster. The status can have one of the following values:
     <dl class="dl">
         <dt class="dt dlterm">Initializing</dt>
         <dd class="dd">The cluster is being created and configured.</dd>
         <dt class="dt dlterm">Modifying</dt>
         <dd class="dd">The cluster is being modified.</dd>
         <dt class="dt dlterm">Ready to Use</dt>
         <dd class="dd">The cluster is ready to use.</dd>
     </dl>
4. To add a cluster, click **Add** at the upper-right corner of the **CLUSTERS** table.
5. Enter the cluster name.
6. Optionally, select **Select a different location** and select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
7. Select the Bare Metal configuration.
   * If you selected **Customized**, specify the **CPU Model**, the amount of **RAM**, and the **Number of {{site.data.keyword.baremetal_short}}**.
   * If you selected **Preconfigured**, specify the **Bare Metal Server Configuration**, and the **Number of {{site.data.keyword.baremetal_short}}**. If you are planning to use vSAN as your storage solution, note that a minimum of 4 {{site.data.keyword.baremetal_short}} are needed.
8. Select the storage configuration.
   * If you selected **vSAN**, specify the **Number of vSAN Capacity Disks** and **Disk Type and Size for vSAN Capacity Disks**.
   * If you selected **NFS**, specify the **File Shares**, **Size**, and **Performance**. Optionally select **Configure shares individually** to complete individual file configuration. Use the **Add NFS** option to add additional file shares, if necessary.
9. Indicate how your license keys are provided:
  * If you want new licenses to be purchased on your behalf, select **Include with purchase** for the components. For VMware NSX and vSAN, also select the license edition.
  * If you want to use your own VMware license for a component, select **I will provide** and enter the license key for the component.
10. Click **Calculate Cost** and review the estimated cost of the cluster. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
11. Click **Add** to add your cluster.
12. After the cluster is ready to use, you can click the cluster name to view its details:

   * The list of ESXi servers with their details:
     * **Name**: The name of the ESXi server is in the format `<host_prefix><n>.<subdomain_label>.<root_domain>`, where:

       `host_prefix` is the host name prefix,
       `n` is the sequence of the server,
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
   * The storage details:
     * **Name**: The data store name.
     * **Size**: The capacity of the storage.
     * **IOPS/GB**: The performance level of the storage.
     * **NFS Protocol**: The NFS version of the storage.

## Results

The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** tab on the instance details page. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

**Important**: You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.

## Removing clusters

**Important**: You cannot remove a cluster from the instance it was added to. To remove clusters, you must delete the vCenter Server instance in which they are located.

## Related links

* [Viewing vCenter Server instances](vc_viewinginstances.html)
* [Expanding and contracting capacity for vCenter Server instances](vc_addingremovingservers.html)
