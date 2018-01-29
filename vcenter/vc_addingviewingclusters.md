---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-26"

---

# Adding and viewing clusters for vCenter Server instances

You can add clusters to your VMware vCenter Server instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. Use this procedure to add or view clusters for the vCenter Server instances that you ordered.

## Before you begin

The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default. You can add up to five clusters to an instance.

When you add a cluster for a vCenter Server instance, you must specify or review the following settings.

## System settings

### Cluster Name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server instance.

### Bare Metal Server Configuration

You can select a Bare Metal Server configuration that is different than the configuration of the default cluster. If you select **User customized**, you must specify the CPU model and RAM for the bare metal server.

Table 1. Dual Intel Xeon CPU and RAM options

| Item        | Options       |
|:------------- |:------------- |
| CPU | <ul><li>Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz</li><li>Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz</li><li>Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz</li></ul>|
| RAM | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1.5 TB|  

Table 2. Dual Intel Xeon Gold CPU and RAM options

| Item        | Options       |
|:------------- |:------------- |
| CPU | Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz|
| RAM | 96 GB, 192 GB, 384 GB, 768 GB, 1.5 TB|

### Number of Bare Metal Servers

A minimum of 2 {{site.data.keyword.baremetal_short}} is required for a cluster.

For vCenter Server instances that are deployed in V2.1 or later, you can add up to 59 {{site.data.keyword.baremetal_short}} for a cluster, and you can add 1 - 59 ESXi servers at a time.

For vCenter Server instances that were deployed in V2.0 or earlier, you can add up to 32 {{site.data.keyword.baremetal_short}} for a cluster. The number of the {{site.data.keyword.baremetal_short}} that you can add at a time is as follows:
* For the **Small**, **Medium**, and **Large** Bare Metal Server configurations, you can add 1 - 10 ESXi servers at a time.
* For the **User customized** Bare Metal Server configuration, you can add 1 - 20 ESXi servers at a time.

After deployment, you can create up to four more clusters. If you select the **User customized** Bare Metal Server configuration with VMware vSAN storage, 4 servers are required for both the initial cluster and post-deployment clusters.

When there are more than 51 ESXi servers in the initial cluster of an instance, the HCX on {{site.data.keyword.cloud}} service cannot be installed into the instance. Because the HCX service requires 8 IPs in the vMotion subnet from the initial cluster, if the number of ESXi servers exceeds 51, no IPs in the vMotion subnet can be available for HCX service.

### Data Center Location

The data center location of the cluster is set to the data center of the vCenter Server instance by default. You can deploy the cluster to a different data center than the deployed instance, but you must ensure that the network latency between the two data centers is less than 150 ms. To check the network latency, you can use a tool such as [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

If you deploy the cluster to a different data center or {{site.data.keyword.cloud}} infrastructure (SoftLayer) pod, three additional VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

## Storage settings

Storage settings are based on your selection of either vSAN or NFS.

### VMware vSAN

For vSAN, you select the **User customized** Bare Metal Server configuration and you can customize the vSAN storage for your instance by specifying the following settings under **Storage**:

* **Number of vSAN Capacity Disks**: Specify the number of disks for the vSAN shared storage that you want to add. The disk quantity must be 2, 4, 6, or 8.
* **Disk Type and Size for vSAN Capacity Disks**: Select the capacity that meets your shared storage needs. Depending on the data center selected, the capacity choices are: 960 GB, 1.9 TB and 3.8 TB. Two cache disks of 960 GB are ordered per ESXi server.

If adding clusters and your initial cluster was vSAN, any additional vSAN clusters will use the same vSAN license and have the same configuration as the initial vSAN cluster. This is also true if any cluster in the instance has vSAN chosen to be deployed on it (initial or additional). The first time you are prompted for the vSAN license (BYOL or purchased) and the edition. The next time you select vSAN for an additional cluster, whatever you chose initially is reused.

### NFS

You can add file-level shared storage for the cluster and specify the following settings.

* **Number of File Shares**: Specify the number of file shares for the shared storage that you want to add. The number of file shares must be in the range 1 - 32.
* **Size**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (Input/output Operations Per Second) per GB based on your workload requirements. The performance levels available to you depend on the size you selected and the data center location.

<!--### NFS Version

NFS (Network File System) v3 is set by default and you cannot change it. NFS v3 supports SDRS (Storage Distributed Resource Scheduler) and SIOC (Storage I/O Control), but does not include NFS multipathing.-->

## Procedure

1. Click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to view the clusters in it or to add clusters to it.

   **Note**: If you want to add clusters to this instance, ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.
3. Click the **Infrastructure** tab. View the summary about the clusters:
   * **Name**: The name of the cluster.
   * **ESXi servers**: The number of ESXi servers in the cluster.
   * **CPU**: The CPU specification of the ESXi servers in the cluster.
   * **Memory**: The total memory size of the ESXi servers in the cluster.
   * **Data center location**: The data center where the cluster is hosted.
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
5. If you select a **user customized** configuration, in the **Add Cluster** area, complete the following steps:

      1. Enter the cluster name.
      2. Select the bare metal server configuration.
      3. Select the CPU and RAM specifications based on your requirements.
      4. Specify the number of {{site.data.keyword.baremetal_short}}.
      5. Review the data center location that is automatically filled in. You can select a different data center other than the data center where the instance is deployed. If you select a user-customized {{site.data.keyword.baremetal_short}} configuration, you can deploy the cluster to a different  {{site.data.keyword.cloud_notm}} infrastructure pod for data centers containing additional pods. This is useful when the default pod where the initial instance is deployed has reached capacity.
      6. Select either vSAN or NFS under **Storage**.
      7. For vSAN storage, specify the required settings for disk type and capacity. Under **Licenses**, indicate how your license key is provided:

        * If you select **vSphere License - Enterprise Plus** to include with purchase, continue to the next license key.
        * If you select **vSAN License** to include with purchase, pick the Advanced or Enterprise license edition from the drop down list.
        * If you indicate you will provide the license key, enter your license key.

      8. For **NFS** storage, specify the required settings for the file shares. To configure shares individually, select that check box and configure the size and performance of each share.
      Under **Licenses**, indicate how your license key is provided. You can either include the **vSphere License - Enterprise Plus** license with your purchase or provide your own license by entering the license key.

6. If you select a user **Preconfigured** configuration, in the **Add Cluster** area, complete the following steps:
      1. Enter the cluster name.
      2. Select the the standardized **Small**, **Medium**, or **Large** {{site.data.keyword.baremetal_short}} configuration.
      3. Specify the number of {{site.data.keyword.baremetal_short}}.
      4. Review the data center location that is automatically filled in. Pre-built, standardized **Small**, **Medium**, and **Large** bare metal server options use a default pod that cannot be changed.
      5. Under Storage, specify the **Number of File Shares**, **Size**, and **Performance**.
      **Note**: NFS is the default under **Storage**.
      6. To configure shares individually, select that check box and configure the size and performance of each share.
      7. Under **Licenses**, indicate how your license key is provided. You can either include the **vSphere License - Enterprise Plus** license with purchase or provide your own license by entering the license key.  
7. Click **Calculate Price** under **Estimated Cost** to get the pricing of your order.
8. Review the **Estimated Cost** of the cluster by clicking the **Calculate Cost** link. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
9. Click **Add** to add your cluster.
10. After the cluster is ready to use, you can click the cluster name to view its details:

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
     * **NFS protocol**: The NFS version of the storage.

## Results

The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** tab on the instance details page. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

**Important**: You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.

## Removing clusters

**Important**: You cannot remove a cluster from the instance it was added to. To remove clusters, you must delete the vCenter Server instance in which they are located.

## Related links

* [Viewing vCenter Server instances](vc_viewinginstances.html)
* [Expanding and contracting capacity for vCenter Server instances](vc_addingremovingservers.html)
