---

copyright:

  years:  2021

lastupdated: "2021-03-30"

keywords: VMware Mission Critical, request Mission Critical, tech specs Mission Critical, Mission Critical Workloads

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}

# Adding, viewing, and deleting clusters for vCenter Server multizone instances
{: #mcv_addviewdeleteclusters}

You can add workload and edge services clusters to VMware vCenter Server® multizone instances. When no longer needed, delete the clusters from your instance.

## Procedure to add a workload cluster
{: #mcv_addviewdeleteclusters-workload-procedure}

1. From the {{site.data.keyword.vmwaresolutions_full}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the multizone instance that you want to add the edge services cluster to.
3. Click **Infrastructure** on the left navigation pane and click **Add** on the upper right of the **Workload cluster** table.
4. On the **Cluster** page, enter the cluster name.
5. Select the **CPU model**, the amount of **RAM**, and the **Number of bare metal servers**.
6. Specify the vSAN storage settings. Specify the disk types for the capacity and cache disks and the number of disks. Optionally, select the **Enable vSAN deduplication and compression** checkbox. For more information, see [Enable vSAN deduplication and compression](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingviewingclusters#vc_addingviewingclusters-adding-vsan-storage-enable-comp).
7. On the **Summary** pane, review the instance settings and the estimated price.
      * To save the settings as a new configuration template without placing an order, click **Save configuration**, enter a name for the configuration, and click **Continue**.
      * To save the updates to a saved configuration, click **Save configuration**, select **Modify current configuration**, and click **Continue**.
      * To save the updates to a new saved configuration, click **Save configuration**, select **Create new configuration**, enter a new name for the configuration, and click **Continue**.
8. To place the order, ensure that the account to be charged is correct, review and accept the terms, and click **Create**.

## Procedure to add an edge services cluster
{: #mcv_addviewdeleteclusters-edge-procedure}

You can add edge services clusters to your vCenter Server multizone instance if you did not select to optionally enable during your initial order. When you add edge services clusters, you must add each cluster one at a time.

You cannot add more than one cluster in the same data center pod.

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the multizone instance that you want to add the edge services cluster to.
3. Click **Infrastructure** on the left navigation pane and click **Add** on the **Edge services cluster** table.
4. On the **Cluster** page, select the data center to host the cluster and then enter the cluster name.
5. Select the amount of **RAM** and the **Number of bare metal servers**.
6. On the **Summary** pane, verify the cluster configuration before you add the cluster.
   1. Review the settings for the cluster.
   2. Review the estimated price of the cluster. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you add the cluster.
   4. Click **Create**.

## Procedure to view a cluster in a multizone instance
{: #mcv_addviewdeleteclusters-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the stretch cluster instance.
3. Click **Infrastructure** on the left navigation pane. In the **Witness cluster**, **Consolidated cluster**, **Workload cluster**, and **Edge services cluster** table, view the summary about the clusters:
  * **Cluster name/type**: The name and type of the cluster. Types include witness, consolidated, workload, and edge services.  
  * **ESXi servers**: The number of VMware ESXi™ servers in the cluster.
  * **Storage**: The type of storage that the cluster uses.
  * **Data center location**: The {{site.data.keyword.cloud_notm}} data center where the cluster is hosted.
  * **Pod**: The pod where the cluster is deployed.
  * **Networking**: The type of network settings of public and private or private only.
  * **Uplink speed**: The uplink speed of 10 Gb or 25 Gb.
  * **Status**: The status of the cluster. The status can have one of the following values:
     * Initializing: The cluster is being created and configured.
     * Modifying: The cluster is being modified.
     * Ready to use: The cluster is ready to use.
     * Deleting: The cluster is being deleted.
     * Deleted: The cluster is deleted.

4. Click a cluster name to view the ESXi server, storage, and network interface details.

View ESXi server details for witness, consolidated, additional workload, and edge services clusters:

| Item        | Description       |  
|:------------- |:------------- |
| Name | The name of the ESXi server is in the following format: `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `n` is the sequence of the ESXi server. |
| Hardware | The CPU model and RAM settings. |
| Credentials | The user name and password to access the ESXi server. |
| Private IP | The private IP address of the ESXi server. |
| Status | The status of the ESXi server, which can be one of the following values:<br> **Added** The ESXi server is added and is ready for use.<br> **Adding** The ESXi server is being added.<br> **Deleting** The ESXi server is being deleted. |
{: caption="Table 5. ESXi server details for a multizone instance" caption-side="top"}

View storage details for witness clusters:

| Item        | Description       |  
|:------------- |:------------- |
| Name | The data store name. |
| Size | The capacity of the storage. |
| IOPS/GB | The performance level of the storage. |
| NFS protocol | The NFS version of the storage. |
| Status | The status of the storage, which can be one of the following values:<br> **Added** The storage is added and is ready for use.<br> **Adding** The storage is being added.<br> **Deleting** The storage is being deleted. |
{: caption="Table 6. Storage details for witness clusters" caption-side="top"}

View network interface details for witness, consolidated, workload, and edge services clusters. Expand the two private VLANs and one public VLAN for the following details:

| Item        | Description       |  
|:------------- |:------------- |
| VLAN number | The unique VLAN number.  |
| Description | The description of the VLAN.  |
| Location | The data center location. |
| Primary route | The primary route of the VLAN. |
{: caption="Table 7. Network interface - VLAN details for a multizone instance" caption-side="top"}

Click **View Resource** to access the VLAN details.

## Procedure to delete workload or edge services clusters from a multizone instance
{: #mcv_addviewdeleteclusters-delete-procedure}

You can delete a workload or edge services cluster from an instance when it's no longer needed.

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the multizone instance that you want to delete clusters from.

   Ensure that the instance is in the **Ready to use** status. Otherwise, you can't delete clusters from the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane. In the **Clusters** table, locate the cluster that you want to delete and click the **Delete** icon next to the **Status** column.
4. In the **Delete cluster** window, confirm that you want to delete the cluster. Click **Delete**.

## Related links
{: #mcv_addviewdeleteclusters-related}

* [IBM Cloud for VMware Mission Critical Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_overview)
* [Ordering vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_ordering)
* [Requesting managed IBM Cloud for VMware Mission Critical Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_ordering-managed)
* [Expanding and contracting capacity for vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_addingremovingservers)
