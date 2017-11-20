---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-09"

---

# Deleting Cloud Foundation instances

To release the components that you ordered in a VMware Cloud Foundation instance, you can delete the instance.

When you delete a Cloud Foundation instance, the following components are released sequentially:
1. All deployed services
2. Support and Services fee
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by the {{site.data.keyword.cloud}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} billing cycle. At the end of the {{site.data.keyword.cloud_notm}} billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

**Attention**: You are billed until the end of the {{site.data.keyword.cloud_notm}} billing cycle for the deleted instance.

## Procedure

### Deleting from the Deployed Instances page

1. Click **Deployed Instances** from the left navigation pane and locate the instance to delete.
2. In the **Actions** column, click the delete icon. The status of the instance is changed to **Deleting**.
3. When the instance is deleted successfully and its status is changed to **Deleted**, click the delete icon in the **Actions** column again.
4. In the **Delete Instance** window, click **OK** to remove the instance from the {{site.data.keyword.vmwaresolutions_short}} console.

### Deleting from the instance detail page

1. Click **Deployed Instances** from the left navigation pane.
2. Click the instance to delete.
3. Click the overflow menu icon to the right of **vCenter console**.
4. Click **Delete Instance**.

## Related links

* [Ordering Cloud Foundation instances](sd_orderinginstance.html)
* [Viewing Cloud Foundation instances](sd_viewinginstances.html)
* [Expanding and contracting capacity for Cloud Foundation instances](sd_addingremovingservers.html)
* [Deleting multi-site configurations](sd_deletinginstance_multi.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
