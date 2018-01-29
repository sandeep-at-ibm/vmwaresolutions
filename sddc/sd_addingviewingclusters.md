---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-09"

---

# Adding and viewing clusters for Cloud Foundation instances

You can add clusters to your VMware Cloud Foundation instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. Use this procedure to add or view clusters for the Cloud Foundation instances that you ordered.

**Note**: This feature is available only to instances that are deployed in V2.0 and later releases.

## Before you begin

The ESXi servers that you configured when you ordered an instance are grouped under a default cluster. The default cluster name is:
* For instances that are deployed in V2.1 or later: **MGMT-Cluster-<subdomain_label>**
* For instances that are deployed in V2.0 or earlier: **SDDC-Cluster**

You can add up to five clusters to an instance. When you add a cluster for a Cloud Foundation instance, you must specify or review the following settings.

## System settings

### Cluster Name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the Cloud Foundation instance.

### Bare Metal Server Configuration

The Bare Metal Server configuration options available to you depend on the data center selected for deployment. The  default data center for the cluster is automatically filled in.

To display all the Bare Metal Server configuration options, click **Select a different location** under **Data Center Location**. The configuration options include:
* Small (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz / 128 GB RAM / 12 disks)
* Large (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz / 512 GB RAM / 12 disks)
* User customized. If you select **User customized**, you must specify the CPU model and RAM for the bare metal server.

Table 1. CPU and RAM options

| Item        | Options       |
|:------------- |:------------- |
| CPU | <ul><li>Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz</li><li>Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz</li><li>Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz</li></ul>|
| RAM | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1.5 TB|   

### Data Center Location

The data center of the cluster is set to the data center of the Cloud Foundation instance by default. You can deploy the cluster to a different data center than the deployed instance, but you must ensure that the network latency between the two data centers is less than 150 ms. To check the network latency, you can use a tool such as [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

The data centers available to you depend on the Bare Metal Server configuration selected for deployment. If you selected the **User customized** configuration, you can also deploy the cluster to a different {{site.data.keyword.cloud}} infrastructure pod, fi the selected data center contains additional pods. This is useful when the default {{site.data.keyword.cloud_notm}} infrastructure pod where the initial instance is deployed has reached its maximum capacity.

**Note**: The standardized **Small** and **Large** Bare Metal Server configurations use a default pod that cannot be changed.

If you deploy the cluster to a different data center or pod, three additional VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

## Storage settings

The storage settings for the **Small** and **Large** Bare Metal Server configurations cannot be changed:
* For the **Small** Bare Metal Server configuration, two disk drives of 1.9 TB SSD SED are ordered.
* For the **Large** Bare Metal Server configuration, four disk drives of 3.8 TB SSD SED are ordered.

If you selected the **User customized** Bare Metal Server configuration, you can customize the VMware vSAN storage for your instance by specifying the following settings under **vSAN Storage**:

### Number of vSAN Capacity Disks

Specify the number of disk drives for the storage that you want to add.

### Disk Type and Size for vSAN Capacity Disks

Select the type and capacity that meets your storage needs.

## Procedure

1. Click **Deployed Instances** from the left navigation pane.
2. In the **Cloud Foundation instances** table, click the instance to view the clusters in it or to add clusters to it.

   **Note**: If you want to add clusters to this instance, ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot add clusters to the instance.
3. Click the **Infrastructure** tab. In the **CLUSTERS** table, view the summary about the clusters:
   * **Name**: The name of the cluster.
   * **ESXi servers**: The number of ESXi servers in the cluster.
   * **CPU**: The CPU specification of the ESXi servers in the cluster.
   * **Disks**: The number of disk drives in the cluster, and the disk type and capacity.
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
4. To add a cluster, click **Add** at the upper-right corner of the **CLUSTERS** table, and then complete the following steps in the **Add Cluster** area:
   1. Enter the **Cluster Name**.
   2. If you selected the **User customized** Bare Metal Server configuration, select the **CPU Model** and **RAM** specifications based on your requirements.
   3. Select **Select a different location** under **Data center location** to ensure that all the **Bare Metal Server Configuration** options are available to you and select the data center where the cluster is to be deployed.
   4. Review the data center location that is automatically filled in. You can select a different data center other than the data center where the instance is deployed. If you select a user-customized {{site.data.keyword.baremetal_short}} configuration and the selected data center contains additional pods, select **Deploy to a non-default pod**. You can deploy the cluster to a different  {{site.data.keyword.cloud_notm}} infrastructure pod for data centers containing additional pods. This is useful when the default pod where the initial instance is deployed has reached capacity.
   5. Select the **Number of Bare Metal Servers**.
   6. Select either **vSAN** or **NFS** under **Storage**.
   7. For **vSAN** storage, specify the **Number of vSAN Capacity Disks** and **Disk Type and Size for vSAN Capacity Disks** from the dropdown menus. Under **Licenses**, indicate how your license keys are provided:

     * If you select **vSphere License - Enterprise Plus** to include with purchase, continue to the next license key.
     * If you select **vSAN License** to include with purchase, pick the Advanced or Enterprise license edition from the drop down list.
     * If you indicate you will provide the license key, enter your license key.

   8. For **NFS** storage, specify the required settings for the file shares. To configure shares individually, select that check box and configure the size and performance of each share.
   Under **Licenses**, indicate how your license key is provided. You can either include the **vSphere License - Enterprise Plus** license with your purchase or provide your own license by entering the license key.
   9. Review the **Estimated Cost** of the cluster by clicking the **Calculate Cost** link. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   10. Click **Add** to add your cluster.

5. After the cluster is ready to use, you can click the cluster name to view its details, which includes the list of ESXi servers with their details:

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

## Results

The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history from the **Summary** tab on the instance details page. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

**Important**: You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.

## Removing clusters

**Important**: You cannot remove a cluster from the instance it was added to. To remove clusters, you must delete the Cloud Foundation instance in which they are located.

## Related links

* [Viewing Cloud Foundation instances](sd_viewinginstances.html)
* [Expanding and contracting capacity for Cloud Foundation instances](sd_addingremovingservers.html)
