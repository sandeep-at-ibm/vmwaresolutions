---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-23"

---

# Deleting vCenter Server with Hybridity Bundle instances

To release the components that you ordered in a VMware vCenter Server with Hybridity Bundle instance, delete the instance.

When you delete a vCenter Server with Hybridity Bundle instance, the following components are released sequentially:
1. All deployed services
2. Support and Services fee
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by {{site.data.keyword.cloud}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle. At the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

**Attention:** You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted instance.

## Deleting instances from the Deployed Instances page

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, find the instance to delete.
3. In the **Actions** column, click the Delete icon.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. In the **Actions** column, click the Delete icon again.
   2. In the **Delete Instance** window, click **OK**.

## Deleting instances from the instance details page

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to delete.
3. Click the overflow menu icon to the right of **vCenter console** and click **Delete Instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click the overflow menu icon to the right of **vCenter console** again and click **Delete Instance**.
   2. In the **Delete Instance** window, click **OK**.

## Related links

* [Deleting vCenter Server with Hybridity Bundle instances in a multi-site configuration](vc_hybrid_deletinginstance_multi.html)
* [Ordering vCenter Server with Hybridity Bundle instances](vc_hybrid_orderinginstance.html)
* [Viewing vCenter Server with Hybridity Bundle instances](vc_hybrid_viewinginstances.html)
* [Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances](vc_hybrid_addingremovingservers.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
