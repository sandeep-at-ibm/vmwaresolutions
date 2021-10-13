---

copyright:

  years:  2021

lastupdated: "2021-09-22"

keywords: vCenter Server add NFS storage

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Adding NFS storage to vCenter Server single-zone instances
{: #vc_addingnfs}

You can expand the capacity of your VMware vCenter Server® instance according to your business needs by adding Network File System (NFS) storage.

## Before you add NFS storage to vCenter Server single-zone instances
{: #vc_addingnfs-prereq}

* Adding NFS storage to vCenter Server instances with VMware vSphere® 6.5 is not supported.
* Do not add NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. 
* IBM will not manage NFS file shares that you manually add to an instance.
* You can add or remove NFS storage shares to or from an existing NFS or vSAN cluster.

## Procedure to add NFS storage to vCenter Server single-zone instances
{: #vc_addingnfs-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **Clusters** table, click the cluster to which you want to add NFS storage.
5. In the **Storage** section, click **Add**.
6. In the **Storage** window, complete the storage configuration.
   * If you want to add and configure the same settings to all file shares, specify the **Number of shares**, **Performance**, and **Size (GB)**.
   * If you want to add and configure file shares individually, select **Configure shares individually**, then click the **+** icon next to the **Add shared storage** label and select the **Performance** and **Size (GB)** for each individual file share. You must select at least one file share. For information about the available options, see [NFS storage](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-nfs-storage).
7. Review the estimated price and click **Add NFS storage**.

   You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Results after you add NFS storage to vCenter Server single-zone instances
{: #vc_addingnfs-results}

1. You might experience a slight delay on the console while the instance status changes from **Ready to use** to **Modifying**. Allow the operation to complete before you make more changes to the instance.
2. You are notified by email that your request to add NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. If you do not see the new NFS storage added to the list in the cluster, check the email or console notifications to find more details about the failure.

## Related links
{: #vc_addingnfs-related}

* [vCenter Server Bill of Materials](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom)
* [Requirements and planning for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
* [Adding clusters to vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingclusters)
* [Place a host in maintenance mode](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){: external}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){: external}
