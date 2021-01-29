---

copyright:

  years:  2016, 2021

lastupdated: "2021-01-22"

keywords: vCenter Server delete instance, delete vCenter Server, remove vCenter Server

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
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

Any VLANs that have your own resources added to them, such as gateways, Veeam servers, and so on, will not be deleted. In addition, any existing VLANs that you own, outside of {{site.data.keyword.vmwaresolutions_full}}, will not be deleted.
{:note}

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by the {{site.data.keyword.cloud}} infrastructure, which happens at the end of the billing cycle. At the end of the billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted instance.
{:important}

## Procedure to delete instances from the Resources page
{: #vc_deletinginstance-procedure1}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, find the instance to delete.
3. Click the vertical overflow menu next to the **Status** column, and then click **Delete instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to delete the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click the vertical overflow menu next to the **Status** column, and then click **Delete from the console**.
   2. In the **Delete instance** window, click **Delete**.

## Procedure to delete instances from the instance details page
{: #vc_deletinginstance-procedure2}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance to delete.
3. Click **Actions** next to **vCenter console**, and then click **Delete instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to delete the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click **Actions** again and then click **Delete instance**.
   2. In the **Delete instance** window, click **Delete**.

## Related links
{: #vc_deletinginstance-related}

* [Deleting vCenter Server instances in a multi-site configuration](/docs/vmwaresolutions?topic=vmwaresolutions-vc_deletinginstance_multi)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
* [Viewing vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservers)
* [Managing virtual servers](/docs/virtual-servers?topic=virtual-servers-managing-virtual-servers)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
