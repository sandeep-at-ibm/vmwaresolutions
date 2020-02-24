---

copyright:

  years:  2019, 2020

lastupdated: "2020-02-05"

keywords: VMware Mission Critical, request Mission Critical, tech specs Mission Critical, Mission Critical Workloads

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Expanding and contracting capacity for multi-zone stretched clusters
{: #mcv_addingremovingservers}

You can expand or contract the capacity of your mult-zone stretched mcv_viewingclusters according to your business needs. You can add or remove ESXi servers to witness, management, and stretched vSAN clusters. You can add or remove network file system (NFS) storage to witness and management clusters.

## Adding ESXi servers to multi-zone stretched clusters
{: #mcv_addingremovingservers-adding}

You can add ESXi servers to your witness, management, or stretched vSAN cluster.

ESXi servers for stretched vSAN clusters are added in pairs.
{:note}

### Procedure to add ESXi servers
{: #mcv_addingremovingservers-adding-procedure}

1. From the {{site.data.keyword.vmwaresolutions_full}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the applicable cluster table, click the cluster to which you want to add ESXi servers.
5. In the **ESXi Servers** section, click **Add**.
6. In the **Add Server** window, select the number of servers that you want to add.
7. Optionally, select the checkbox to add servers during maintenance mode. The checkbox is selected by default.

   When you provision the new ESXi server, virtual machines (VMs) are immediately migrated to the new servers if you do not select the **Maintenance Mode** checkbox. You do not receive a confirmation message before the migration begins.
   {:important}

8. Review the estimated cost and click **Provision**.

### Results after you add ESXi servers
{: #mcv_addingremovingservers-adding-results}

1. You might experience a slight delay on the console while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to add ESXi servers is being processed. On the console, the status of the cluster that is associated with the ESXi servers is changed to **Modifying**.
3. If you do not see the new ESXi servers added to the list in the cluster, check the email or console notifications to find more details about the failure.

   If you are adding ESXi servers during maintenance mode, VMs are not migrated to the new servers until you remove maintenance mode.
   {:important}

## Removing ESXi servers from multi-zone stretched clusters
{: #mcv_addingremovingservers-removing}

### Before you remove ESXi servers
{: #mcv_addingremovingservers-removing-prereq}

* Whenever possible, remove ESXi servers by using the {{site.data.keyword.vmwaresolutions_short}} console, because changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. Therefore, remove ESXi servers from vCenter Server only for on-premises ESXi servers or ESXi servers that you can't or won't manage in the {{site.data.keyword.vmwaresolutions_short}} console.
* When you remove ESXi servers, the servers are placed in maintenance mode, and after that, all the VMs running on the servers are migrated before they are removed from vCenter Server. For maximum of control over the relocation of VMs, it is recommended that you place the ESXi servers to be removed in maintenance mode and migrate the VMs running on them manually using the VMware vSphere Web Client. After that, remove the ESXi servers by using the {{site.data.keyword.vmwaresolutions_short}} console.

### Procedure to remove ESXi servers
{: #mcv_addingremovingservers-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to contract capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the applicable cluster table, click the cluster from which you want to remove ESXi servers.
5. In the **ESXi Servers** section, select the servers that you want to remove and click **Delete**.
6. Click **Delete** in the **Remove ESXi server** window.

### Results after you remove ESXi servers
{: #mcv_addingremovingservers-removing-results}

1. You might experience a slight delay on the console, while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to remove ESXi servers is being processed. On the console, the status of the cluster that is associated with the ESXi servers is changed to **Modifying**.
3. The ESXi servers are fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

   You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed ESXi servers.
   {:note}

## Adding NFS storage to multi-zone stretched clusters
{: #mcv_addingremovingservers-adding-nfs-storage}

You can add NFS storage to witness and management clusters.

### Before you add NFS storage
{: #mcv_addingremovingservers-adding-nfs-storage-prereq}

Do not add NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. IBM will not manage NFS file shares that you manually add to an instance.

### Procedure to add NFS storage
{: #mcv_addingremovingservers-adding-nfs-storage-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the applicable cluster table, click the cluster to which you want to add NFS storage.
5. In the **Storage** section, click **Add**.
6. In the **Storage** window, complete the storage configuration.
   * If you want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Performance**, and **Size (GB)**.
   * If you want to add and configure file shares individually, select **Configure shares individually**, then click the **+** icon next to the **Add Shared Storage** label and select the **Performance** and **Size (GB)** for each individual file share. You must select at least one file share.
7. Review the estimated cost and click **Provision**.

### Results after you add NFS storage
{: #mcv_addingremovingservers-adding-nfs-storage-results}

1. You might experience a slight delay on the console while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to add NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. If you do not see the new NFS storage added to the list in the cluster, check the email or console notifications to find more details about the failure.

## Removing NFS storage from multi-zone stretched clusters
{: #mcv_addingremovingservers-removing-nfs-storage}

### Before you remove NFS storage
{: #mcv_addingremovingservers-removing-nfs-storage-prereq}

* Do not remove NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.
* Before you remove the NFS storage, ensure that you removed all the VMs that reside on the storage.
* Ensure that the shares you plan to remove are associated with the correct multi-zone stretched cluster.
* The cluster must be in **Ready to Use** status.

### Procedure to remove NFS storage
{: #mcv_addingremovingservers-removing-nfs-storage-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to contract capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the applicable cluster table, click the cluster from which you want to remove NFS storage.
5. In the **Storage** section, select the storage share that you want to remove and click **Delete**.
6. Click **Delete** in the **Remove Storage** window.

### Results after you remove NFS storage
{: #mcv_addingremovingservers-removing-nfs-storage-results}

1. You might experience a slight delay on the console, while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to remove NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. The NFS storage is fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

   You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed NFS storage.
   {:note}

## Related links
{: #mcv_addingremovingservers-related}

* [IBM Cloud for VMware Mission Critical Workloads overview](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv_overview)
* [Ordering multi-zone stretch clusters](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv_ordering)
* [Requesting managed IBM Cloud for VMware Mission Critical Workloads](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv_ordering-managed)
* [Viewing IBM Cloud for VMware Mission Critical Workload clusters](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv_viewingclusters)
* [{{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads overview](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv-archi-overview)
