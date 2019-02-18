---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Deleting VMware Federal instances
{: #vc_fed_deletinginstance}

To release the components that you ordered in a VMware Federal instance, delete the instance.

When you delete a VMware Federal instance, the following components are released sequentially:

1. Support and service fees
2. VMware product licenses
3. ESXi servers
4. Subnets

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets cannot be deleted until the ESXi servers are fully reclaimed by {{site.data.keyword.cloud}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle. At the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days, the subnets are deleted and the instance deletion is completed.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted instance.
{:note}

## Procedure to delete instances from the Deployed Instances page
{: #vc_fed_deletinginstance-procedure1}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, find the instance to delete.
3. In the **Actions** column, click the Delete icon.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. In the **Actions** column, click the Delete icon again.
   2. In the **Delete Instance** window, click **OK**.

## Procedure to delete instances from the instance details page
{: #vc_fed_deletinginstance-procedure2}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to delete.
3. Click the overflow menu icon next to **vCenter console** and click **Delete Instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click the overflow menu icon next to **vCenter console** again and click **Delete Instance**.
   2. In the **Delete Instance** window, click **OK**.

## Related links
{: #vc_fed_deletinginstance-related}

* [VMware Federal on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/vcenter/vc_fed_overview.html)
* [Ordering VMware Federal instances](/docs/services/vmwaresolutions/vcenter/vc_fed_orderinginstance.html)
* [Securing VMware Federal instances](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html)
* [Viewing VMware Federal instances](/docs/services/vmwaresolutions/vcenter/vc_fed_viewinginstance.html)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
