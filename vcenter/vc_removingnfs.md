---

copyright:

  years:  2021

lastupdated: "2021-05-14"

keywords: vCenter Server remove NFS storage

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Removing NFS storage from vCenter Server instances
{: #vc_removingnfs}

You can contract the capacity of your VMware vCenter Server® instance according to your business needs by removing Network File System (NFS) storage.

* If your initial cluster has vSAN® storage, adding one or more ESXi servers after deployment can increase the cluster storage capacity.
* You can add or remove NFS storage shares to or from an existing NFS or vSAN cluster.

## Before you remove NFS storage
{: #vc_removingnfs-prereq}

* Do not remove NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.
* Before you remove the NFS storage, ensure that you removed all the VMs that reside on the storage.
* Ensure that the shares you plan to remove are associated with the correct vCenter Server instance.
* The cluster must be in **Ready to use** status.

## Procedure to remove NFS storage from vCenter Server instances
{: #vc_removingnfs-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to contract capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **Clusters** table, click the cluster from which you want to remove NFS storage.
5. In the **Storage** section, select the storage share that you want to remove and click **Delete**.
6. Click **Remove** in the **Remove storage** window.

## Results after you remove NFS storage
{: #vc_removingnfs-results}

1. You might experience a slight delay on the console, while the instance status changes from **Ready to use** to **Modifying**. Allow the operation to complete before you make more changes to the instance.
2. You are notified by email that your request to remove NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. The NFS storage is fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

   You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed NFS storage.
   {:note}

## Related links
{: #vc_removingnfs-related}

* [vCenter Server Bill of Materials](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom)
* [Requirements and planning for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
* [Deleting clusters from vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_deletingclusters)
* [Place a host in maintenance mode](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:external}
