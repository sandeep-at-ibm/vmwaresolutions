---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-17"

---

# Adding and viewing clusters for Cloud Foundation instances

You can add clusters to your VMware Cloud Foundation instances to expand the compute and storage capacity. Within a cluster, you can manage ESXi servers for better resource allocation and high availability. Use this procedure to add or view clusters for the Cloud Foundation instances that you ordered.

**Note**: This feature is available only to instances that are deployed in V2.0 and later releases.

## Before you begin

The ESXi servers that you configured when you ordered an instance are grouped as **SDDC-Cluster** by default. You can add up to five clusters to an instance.

When you add a cluster for a Cloud Foundation instance, you must specify or review the following settings.

## System settings

### Cluster Name

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the Cloud Foundation instance.

### Bare Metal Server Configuration

The Bare Metal Server configuration options available to you depend on the data center selected for deployment. Therefore, the Bare Metal Server cofiguration options available to you by default include only the ones that are supported by the cluster's default data center which is automatically filled in. You must select **Select a different location** under **Data Center Location** to display all the Bare Metal Server configuration options, including:
* Small (Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz / 128 GB RAM / 12 disks)
* Large (Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz / 512 GB RAM / 12 disks)
* User customized

You can select a Bare Metal Server configuration that is different from the configuration of the default instance. If you select **User customized**, you must specify the CPU model and RAM for the bare metal server.

Table 1. CPU and RAM options

| Item        | Options       |
|:------------- |:------------- |
| CPU | <ul><li>Dual Intel Xeon E5-2620 v4 / 16 cores total, 2.10 GHz</li><li>Dual Intel Xeon E5-2650 v4 / 24 cores total, 2.20 GHz</li><li>Dual Intel Xeon E5-2690 v4 / 28 cores total, 2.60 GHz</li></ul>|
| RAM | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1.5 TB|   

### Number of Bare Metal Servers

A minimum of 2 bare metal servers is required for a cluster and you can add up to 32 bare metal servers, which will share the same configuration.

The number of the bare metal servers that you can add at a time is as follows:
* For the **Small**, **Medium**, and **Large** configurations, you can add 1 - 10 ESXi servers at a time.
* For the **User customized** configuration, you can add 1 - 20 ESXi servers at a time. After deployment, you can create up to four more clusters.

### Data Center Location

The data center of the cluster is set to the data center of the Cloud Foundation instance by default. You can deploy the cluster to a different data center than the deployed instance, but you must ensure that the network latency between the two data centers is less than 150 ms. To check the network latency, you can use a tool such as [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

The data centers available to you depend on the Bare Metal Server configuration selected for deployment. If you selected the user-customized Bare Metal Server configuration, you can also deploy the cluster to a different {{site.data.keyword.cloud}} infrastructure pod for data centers containing additional pods. This is useful when the default {{site.data.keyword.cloud_notm}} infrastructure pod where the initial instance is deployed has reached capacity.

**Note**: Pre-built, standardized **Small** and **Large** Bare Metal Server configurations use a default pod that cannot be changed.

If you deploy the cluster to a different data center or pod, three additional VLANs are ordered for use with the ordered bare metal servers.

## Storage settings

The storage settings for the **Small** and **Large** standardized Bare Metal Server configurations cannot be changed:
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
   1. Enter the cluster name.
   2. Select **Select a different location** under **Data center location** to ensure that all the **Bare Metal Server Configuration** options are available to you, and then select the Bare Metal Server configuration.
   3. If you selected the **User customized** Bare Metal Server configuration, select the CPU and RAM specifications based on your requirements.
   4. Select the data center where the cluster is to be deployed.
   5. If you want to deploy the cluster to a different pod when you selected a user-customized bare metal server configuration and the selected data center contains additional pods, select **Deploy to a non-default pod**.
   6. If you selected the **User customized** Bare Metal Server configuration, select the number of disk drives, and the disk type and capacity under **vSAN Storage**.
   7. Click **Calculate Price** under **Estimated Cost** to get the pricing of your order.
   8. Review the estimated cost of the cluster by clicking the price link under **Estimated Cost**. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   9. Click **Add**.

5. After the cluster is ready to use, you can click the cluster name to view its details, which includes the list of ESXi servers with their details:

    * **Name**: The name of the ESXi server is in the format `<host_prefix><n>.<subdomain_prefix>.<root_domain>`, where:

      `host_prefix` is the host name prefix,
      `n` is the sequence of the ESXi server,
      `subdomain_prefix` is the subdomain prefix, and
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
