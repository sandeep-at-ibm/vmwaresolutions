---

copyright:

  years:  2016, 2021

lastupdated: "2021-11-29"

keywords: vCenter Server delete instance, delete vCenter Server, remove vCenter Server, vmware multizone, vcenter server multizone, delete vCenter Server multizone

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Deleting vCenter Server instances
{: #vc_deletinginstance}

To release the components that you ordered in a VMware vCenter Server® instance, delete the instance.

When you delete a vCenter Server instance, the following components are released sequentially:
1. All deployed services
2. The Support and Services fee for NSX-V instances or the Support fee for NSX-V instances.
3. VMware® product licenses
4. VMware ESXi™ servers
5. Subnets
6. VLANs

Any VLANs that have your own resources added to them, such as gateways, Veeam® servers, and so on, will not be deleted. In addition, any existing VLANs that you own, outside of {{site.data.keyword.vmwaresolutions_full}}, will not be deleted.
{: note}

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by the {{site.data.keyword.cloud_notm}} infrastructure at the end of the billing cycle. You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted instance.

The instance remains in **Deleting** status and the monthly ESXi servers are available for the remainder of the account monthly billing cycle. After the billing cycle ends, the status of the device changes from **ACTIVE** to **RECLAIM** until the reclaim process completes which can take days or weeks into the following month.

After the ESXi server reclaim process completes, the subnets and VLANs are deleted and the instance deletion is completed.

You can review the next account invoice to confirm that you are no longer billed for this instance. From the {{site.data.keyword.cloud_notm}} console, click **Manage > Billing and usage**, then click **Invoices**.

## Procedure to delete vCenter Server instances from the Resources page
{: #vc_deletinginstance-procedure1}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, find the instance to delete.
3. Click the vertical overflow menu next to the **Status** column, and then click **Delete instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to delete the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click the vertical overflow menu next to the **Status** column, and then click **Delete from the console**.
   2. In the **Delete instance** window, click **Delete**.

## Procedure to delete vCenter Server instances from the instance details page
{: #vc_deletinginstance-procedure2}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance to delete.
3. Click **Actions** next to **vCenter console**, and then click **Delete instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to delete the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click **Actions** again and then click **Delete from the console**.
   2. In the **Delete instance** window, click **Delete**.

## Related links
{: #vc_deletinginstance-related}

* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
* [Viewing vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservers)
* [Managing virtual servers](/docs/virtual-servers?topic=virtual-servers-managing-virtual-servers)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
