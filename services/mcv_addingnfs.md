---

copyright:

  years:  2019, 2021

lastupdated: "2021-07-20"

keywords: multizone add storage

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}

# Adding NFS storage to vCenter Server multizone instances
{: #mcv_addingnfs-storage}

You can add NFS storage to the witness and management clusters.

## Before you add NFS storage to vCenter Server multizone instances
{: #mcv_addingnfs-storage-prereq}

Do not add NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. IBM will not manage NFS file shares that you manually add to an instance.

## Procedure to add NFS storage to vCenter Server multizone instances
{: #mcv_addingnfs-storage-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the applicable cluster table, click the cluster to which you want to add NFS storage.
5. In the **Storage** section, click **Add**.
6. In the **Storage** window, complete the storage configuration.
   * If you want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Performance**, and **Size (GB)**.
   * If you want to add and configure file shares individually, select **Configure shares individually**, then click the **+** icon next to the **Add shared storage** label and select the **Performance** and **Size (GB)** for each individual file share. You must select at least one file share.
7. Review the estimated price and click **Provision**.

## Results after you add NFS storage to vCenter Server multizone instances
{: #mcv_addingnfs-storage-results}

1. You might experience a slight delay on the console while the instance status changes from **Ready to use** to **Modifying**. Allow the operation to complete before you make more changes to the instance.
2. You are notified by email that your request to add NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. If you do not see the new NFS storage added to the list in the cluster, check the email or console notifications to find more details about the failure.

## Related links
{: #mcv_addingnfs-related}

* [Viewing vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances)
