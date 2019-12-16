---

copyright:

  years:  2016, 2019

lastupdated: "2019-12-13"

keywords: vCenter Server Hybridity add cluster, view cluster vCenter Server Hybridity, delete cluster vCenter Server Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Adding, viewing, and deleting clusters for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingviewingclusters}

The ESXi servers that you configured when you ordered an instance are grouped as **cluster1** by default.

You can add clusters to your vCenter Server with Hybridity Bundle instance to expand the compute and storage capacity. Within a cluster, manage the ESXi servers for better resource allocation and high availability. When no longer needed, delete the added clusters from your instance.

## Adding clusters to vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingviewingclusters-adding}

### Before you add clusters
{: #vc_hybrid_addingviewingclusters-before-add}

* Whenever possible, add clusters by using the {{site.data.keyword.vmwaresolutions_short}} console, because changes that you make on the VMware vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. Therefore, add clusters to vCenter Server only for on-premises clusters or clusters that you cannot or will not manage in the {{site.data.keyword.vmwaresolutions_short}} console.
* For instances that were deployed in (or upgraded to) V2.5 and later, the number of clusters, hosts, and VMs determines the maximum limit for the number of clusters you can add. You must remain within the VMware sizing guidelines and limits for your deployment. For more information about maximum limits, see [VMware Configuration Maximums](https://configmax.vmware.com/home){:external}.
* For instances that were deployed in (or upgraded to) V2.3 and V2.4, you can add up to 10 clusters.

### System settings
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

When you add a cluster for a vCenter Server with Hybridity Bundle instance, you must specify the following settings.

#### Cluster name
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

The cluster name must meet the following requirements:
* Only alphanumeric and dash (-) characters are allowed.
* The cluster name must start and end with an alphanumeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server with Hybridity Bundle instance.

#### Data center location
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

The {{site.data.keyword.CloudDataCent_notm}} location of the cluster is set to the {{site.data.keyword.CloudDataCent_notm}} of the vCenter Server instance by default. You can deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} than the deployed instance, but you must ensure that the network latency between the two {{site.data.keyword.CloudDataCents_notm}} is less than 150 ms. To check the network latency, use a tool such as [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass).

If you deploy the cluster to a different {{site.data.keyword.CloudDataCent_notm}} or {{site.data.keyword.cloud_notm}} infrastructure pod, three more VLANs are ordered for use with the ordered {{site.data.keyword.baremetal_short}}.

### Bare Metal Server settings
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

You can choose **Skylake**, **Cascade Lake**, or **Broadwell**. Options might differ depending on the version that your instance was initially deployed in.

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

When you select **Skylake**, you can choose the CPU and RAM combination according to your needs.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 1. Options for Skylake Bare Metal Servers" caption-side="top"}

#### Cascade Lake
{: #vc_hybrid_addingviewingclusters-adding-cascade}

For the **Cascade Lake** setting, you have options for the **CPU Model** and **RAM**.

Cascade Lake {{site.data.keyword.baremetal_short}} are available only for VMware vSphere Enterprise Plus 6.7 U2 instances.
{:note}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Gold 5218 Processor / 32 cores total, 2.3 GHz | 32 GB, 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 Processor / 40 cores total, 2.5 GHz | 32 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Options for Cascade Lake {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

When you select **Broadwell**, you can choose the CPU and RAM combination according to your needs.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 cores total, 1.9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Table 3. Options for Broadwell Bare Metal Servers" caption-side="top"}

#### Number of Bare Metal Servers
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

* All servers that you order have the same configuration.
* You can order between 4 and 59 servers.

### vSAN storage settings
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

VMware vSAN 6.6 is included with your vCenter Server with Hybridity Bundle instance order. Specify the following vSAN options:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity disks over the limit of 10, check the **High-Performance Intel Optane** box. This option provides two extra capacity disk bays for a total of 12 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

  The **High-Performance Intel Optane** option is available only for the Skylake CPU models.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you checked the **High-Performance Intel Optane** box.
* **vSAN License**: Select the VMware vSAN 6.6 license edition (Advanced or Enterprise).

### Licensing settings
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

IBM-provided licenses for the following VMware components:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Advanced or Enterprise edition)

### Network interface settings
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

Network interface card (NIC) settings are based on your selection of either **Public and Private Network** or **Private Network Only**. The following add-on services require public NICs and aren't available with the private option:

* F5 BIG-IP
* Fortigate Security Appliance
* Fortigate Virtual Appliance

### Order summary
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

Based on your selected configuration for the cluster, the estimated cost is instantly generated and displayed in the **Order Summary** right pane. Click **Pricing details** to generate a PDF document with the cost summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the cost of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to add clusters to vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to view the clusters in it.

   Ensure that the instance status is **Ready to Use**. Otherwise, you can't add clusters to the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane and click **Add** at the upper-right corner of the **CLUSTERS** table.
4. On the **Add Cluster** page, enter the cluster name.
5. You can host the cluster in a different {{site.data.keyword.CloudDataCent_notm}} than the one that the instance is hosted in. To do so, under **Bare Metal Server**, check the **Select a different location** check box and choose the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
6. Select the **CPU Model**, the amount of **RAM**, and the **Number of Bare Metal Servers** for the Bare Metal configuration.
7.  Select **vSAN Storage** and specify the disk types for the capacity and cache disks and the number of disks. If you want more storage, check the **High-Performance Intel Optane** box.
8. Select the license edition for VMware vSAN for the license configuration.
9. Select the network setting of either **Public and Private Network** or **Private Network Only**.
10. On the **Order Summary** pane, verify the cluster configuration before you add the cluster.
   1. Review the settings for the cluster.
   2. Review the estimated cost of the cluster. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you add the cluster.
   4. Click **Provision**.

### Results after you add clusters to vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingviewingclusters-adding-results}

1. The deployment of the cluster starts automatically and the status of the cluster is changed to **Initializing**. You can check the status of the deployment by viewing the deployment history on the **Summary** page of the instance.
2. When the cluster is ready to use, its status changes to **Ready to Use**. The newly added cluster is enabled with vSphere High Availability (HA) and vSphere Distributed Resource Scheduler (DRS).

You can't change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.
{:important}

## Procedure to view clusters in vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to view the clusters in it.
3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, view the summary about the clusters:
  * **Name**: The name of the cluster.
  * **ESXi Servers**: The number of ESXi servers in the cluster.
  * **CPU**: The CPU specification of the ESXi servers in the cluster.
  * **Customized vSAN Disks**: The number of vSAN disks in the cluster, including the disk type and capacity.
  * **Memory**: The total memory size of the ESXi servers in the cluster.
  * **Data Center Location**: The {{site.data.keyword.CloudDataCent_notm}} where the cluster is hosted.
  * **Pod**: The pod where the cluster is deployed.
  * **Status**: The status of the cluster. The status can have one of the following values:
    * Initializing: The cluster is being created and configured.
    * Modifying: The cluster is being modified.
    * Ready to Use: The cluster is ready to use.
    * Deleting: The cluster is being deleted.
    * Deleted: The cluster is deleted.
4. Click a cluster name to view the ESXi servers, storage, and network interface details:

  * ESXi servers details:
     * **Name**: The name of the ESXi server is in the format `<host_prefix><n>.<subdomain_label>.<root_domain>`, where:

       `host_prefix` is the host name prefix,

       `n` is the sequence of the server,

       `subdomain_label` is the subdomain label, and

       `root_domain` is the root domain name.

     * **Version**: The version of the ESXi server.
     * **Credentials**: The user name and password to access the ESXi server.
     * **Private IP**: The private IP address of the ESXi server.
     * **Status**: The status of the ESXi server, which can be one of the following values:
       * Added: The ESXi server is added and is ready for use.
       * Adding: The ESXi server is being added.
       * Deleting: The ESXi server is being deleted.

  * Storage details:
    * **Name**: The data store name.
    * **Size**: The capacity of the storage.
    * **IOPS/GB**: The performance level of the storage.
    * **NFS Protocol**: The NFS version of the storage.
  * Network Interface - VLAN details:
    * **VLAN Number**: The unique VLAN number.
    * **Description**: The description of the VLAN.
    * **Location**: The data center location.
    * **Primary Route**: The primary route of the VLAN.
    Click **View Resource** to access the VLAN details.
  * Network Interface - Subnet details:
    * **Name**: The subnet name. Click the name to access the subnet details.
    * **Type**: The type of subnet: primary or portable.
    * **Description**: The description of the subnet.
  * Network Interface - IP details:
    * **IP**: The IP address.
    * **Status**: The status of the IP address.
    * **Description**: The description of the IP address.

## Deleting clusters from vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingviewingclusters-deleting}

You might want to delete a cluster from an instance when it's no longer needed.

### Before you delete
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* Whenever possible, delete clusters by using the {{site.data.keyword.vmwaresolutions_short}} console, because changes that you make on the VMware vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. Therefore, delete clusters from vCenter Server only for on-premises clusters or clusters that you can't or won't manage in the {{site.data.keyword.vmwaresolutions_short}} console.
* You can delete a single cluster at a time. To delete multiple clusters, you must do it in sequence; waiting for the previous cluster to be deleted before you delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before you delete the cluster.
* When you delete a cluster, all VMs (virtual machines) from the cluster are also deleted and they can't be recovered. If you want to keep the VMs, migrate them to other clusters.
* The default cluster can't be deleted.

## Procedure to delete clusters from vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance that you want to delete clusters from.

   Ensure that the instance is in the **Ready to Use** status. Otherwise, you cannot remove clusters from the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane. In the **CLUSTERS** table, locate the cluster that you want to delete and click the **Delete** icon in the **Actions** column.

## Related links
{: #vc_hybrid_addingviewingclusters-related}

* [Viewing vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_addingremovingservers)
