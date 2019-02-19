---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Deleting Cloud Foundation instances
{: #sd_deletinginstance}

To release the components that you ordered in a VMware Cloud Foundation instance, delete the instance.

When you delete a Cloud Foundation instance, the following components are released sequentially:
1. All deployed services
2. Support and Services fee
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by the {{site.data.keyword.cloud}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} billing cycle. At the end of the {{site.data.keyword.cloud_notm}} billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

You are billed until the end of the {{site.data.keyword.cloud_notm}} billing cycle for the deleted instance.
{:note}

## Procedure to delete instances from the Deployed Instances page
{: #sd_deletinginstance-procedure1}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation Instances** table, find the instance to delete.
3. In the **Actions** column, click the Delete icon.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. In the **Actions** column, click the Delete icon again.
   2. In the **Delete Instance** window, click **OK**.

## Procedure to delete instances from the instance details page
{: #sd_deletinginstance-procedure2}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation Instances** table, click the instance to delete.
3. Click the overflow menu icon next to **vCenter console** and click **Delete Instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click the overflow menu icon next to **vCenter console** again and click **Delete Instance**.
   2. In the **Delete Instance** window, click **OK**.

## Related links
{: #sd_deletinginstance-related}

* [Deleting Cloud Foundation instances in a multi-site configuration](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)
* [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Viewing Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [Expanding and contracting capacity for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Deleting multi-site configurations](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
