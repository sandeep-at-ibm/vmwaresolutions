---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-18"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Expanding and contracting capacity for vCenter Server with NSX-T instances
{: #vc_nsx-t_addingremovingservers}

You can expand or contract the capacity of your VMware vCenter Server with NSX-T instance according to your business needs, by adding or removing ESXi servers or network file system (NFS) storage.

you can add new ESXi servers to a cluster while the cluster is in maintenance mode. Additionally, you can simultaneously add or remove ESXi servers across multiple clusters. The following simultaneous operations are available:

* Add hosts to a cluster and add hosts to additional clusters.
* Remove hosts from a cluster and remove hosts from additional clusters.
* Add hosts to a cluster and remove hosts from additional clusters.
* Remove hosts from a cluster and add hosts to additional clusters.https://github.ibm.com/tornado/tracker/issues/14183

You can add or remove NFS storage shares to or from an existing NFS or vSAN vCenter Server wiht NSX-T cluster.
{:note}

If your initial cluster has vSAN as its storage, adding one or more ESXi servers after deployment can increase the cluster storage capacity.

## Adding ESXi servers to vCenter Server with NSX-T instances
{: #vc_nsx-t_addingremovingservers-adding}

### Before you add ESXi servers
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* Do not add ESXi servers from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_full}} console.
* A vCenter Server with NSX-T instance with NFS storage must have at least 3 ESXi servers. You can expand the default cluster to have up to 51 ESXi servers. Each of the non-default clusters can be expanded to have up to 59 ESXi servers.
* A vCenter Server with NSX-T instance with vSAN storage must have at least 4 ESXi servers.

### Procedure to add ESXi servers
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **CLUSTERS** table, click the cluster to which you want to add ESXi servers.
5. In the **ESXi Servers** section, click **Add**.
6. In the **Add Server** window, enter the number of servers that you want to add.
7. Optionally, select the checkbox to add servers during maintenance mode.
8. Review the estimated cost and click **Add**.

### Results after you add ESXi servers
{: #vc_nsx-t_addingremovingservers-adding-results}

1. You might experience a slight delay on the console while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to add ESXi servers is being processed. On the console, the status of the cluster that is associated with the ESXi servers is changed to **Modifying**.
3. If you do not see the new ESXi servers added to the list in the cluster, check the email or console notifications to find more details about the failure.

If you are adding ESXi servers during maintenance mode, virtual machines (VMs) are not migrated to the new servers until you remove the cluster from maintenance mode.   
{:important}

## Removing ESXi servers from vCenter Server with NSX-T instances
{: #vc_nsx-t_addingremovingservers-removing}

### Before you remove ESXi servers
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* Do not remove ESXi servers from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.
* A vCenter Server with NSX-T instance with NFS storage must have at least 3 ESXi servers and a vCenter Server instance with NSX-T with vSAN storage must have at least 4 ESXi servers.
* When you remove ESXi servers, the servers are placed in maintenance mode, and after that, all the VMs running on the servers are migrated before they are removed from vCenter Server. For maximum of control over the relocation of VMs, it is recommended that you place the ESXi servers to be removed in maintenance mode and migrate the VMs running on them manually using the VMware vSphere Web Client. After that, remove the ESXi servers by using the {{site.data.keyword.vmwaresolutions_short}} console.

### Procedure to remove ESXi servers
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to contract capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **CLUSTERS** table, click the cluster from which you want to remove ESXi servers.
5. In the **ESXi Servers** section, select the servers that you want to remove and click **Remove**.

### Results after you remove ESXi servers
{: #vc_nsx-t_addingremovingservers-removing-results}

1. You might experience a slight delay on the console, while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to remove ESXi servers is being processed. On the console, the status of the cluster that is associated with the ESXi servers is changed to **Modifying**.
3. The ESXi servers are fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

   You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed ESXi servers.
   {:note}

## Adding NFS storage to vCenter Server with NSX-T instances
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### Before you add NFS storage
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

Do not add NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. IBM will not manage NFS file shares that you manually add to an instance.

### Procedure to add NFS storage
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **CLUSTERS** table, click the cluster to which you want to add NFS storage.
5. In the **Storage** section, click **Add**.
6. In the **Storage** window, complete the storage configuration.
   * If you want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Performance**, and **Size (GB)**.
   * If you want to add and configure file shares individually, select **Configure shares individually**, then click the **+** icon next to the **Add Shared Storage** label and select the **Performance** and **Size (GB)** for each individual file share. You must select at least one file share.
7. Click **Add NFS Storage**.

### Results after you add NFS storage
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. You might experience a slight delay on the console while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to add NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. If you do not see the new NFS storage added to the list in the cluster, check the email or console notifications to find more details about the failure.

## Removing NFS storage from vCenter Server with NSX-T instances
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### Before you remove NFS storage
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* Do not remove NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.
* Before you remove the NFS storage, ensure that you removed all the VMs that reside on the storage.
* Ensure that the shares you plan to remove are associated with the correct vCenter Server instance.
* The cluster must be in **Ready to Use** status.

### Procedure to remove NFS storage
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to contract capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **CLUSTERS** table, click the cluster from which you want to remove NFS storage.
5. In the **Storage** section, select the storage share that you want to remove and click **Delete**.
6. Click **Remove** in the **Remove Storage** window.

### Results after you remove NFS storage
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. You might experience a slight delay on the console, while the instance status changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to remove NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. The NFS storage is fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

   You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed NFS storage.
   {:note}

## Related links
{: #vc_nsx-t_addingremovingservers-related}

* [vCenter Server Bill of Materials](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requirements and planning for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Ordering vCenter Server with NSX-T instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [Adding, viewing, and deleting clusters for vCenter Server with NSX-T instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
