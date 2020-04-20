---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-31"

keywords: vCenter Server delete instance, delete vCenter Server, remove vCenter Server

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Deleting vCenter Server instances
{: #vc_deletinginstance}

To release the components that you ordered in a VMware vCenter Server instance, delete the instance.

When you delete a vCenter Server instance, the following components are released sequentially:
1. All deployed services
2. The Support and Services fee for NSX-V instances or the Support fee for NSX-V instances.
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by {{site.data.keyword.cloud}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle. At the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted instance.
{:note}

## Procedure to delete instances from the Resources page
{: #vc_deletinginstance-procedure1}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, find the instance to delete.
3. In the **Actions** column, click the Delete icon.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. In the **Actions** column, click the Delete icon again.
   2. In the **Delete Instance** window, click **OK**.

## Procedure to delete instances from the instance details page
{: #vc_deletinginstance-procedure2}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to delete.
3. Click the overflow menu icon next to **vCenter console** and click **Delete Instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click the overflow menu icon next to **vCenter console** again and click **Delete Instance**.
   2. In the **Delete Instance** window, click **OK**.

## Related links
{: #vc_deletinginstance-related}

* [Deleting vCenter Server instances in a multi-site configuration](/docs/vmwaresolutions?topic=vmware-solutions-vc_deletinginstance_multi)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Viewing vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers)
* [Canceling virtual servers](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmware-solutions-trbl_support)
