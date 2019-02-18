---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Deleting NetApp ONTAP Select instances
{: #np_deletinginstance}

If you delete a NetApp ONTAP Select instance, the following components are released sequentially:
1. The deployed NetApp ONTAP Select clustered VMs (virtual machines) and the NetApp ONTAP Select Deploy VM
2. Support and Services fee
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by {{site.data.keyword.cloud}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} billing cycle. At the end of the billing cycle, which is typically 30 days, the subnets and VLANs are reclaimed and the instance deletion is completed.

You are billed until the end of the billing cycle for the deleted instance.
{:note}

## Procedure to delete instances from the Deployed Instances page
{: #np_deletinginstance-procedure1}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **NetApp ONTAP Select Instances** table, find the instance to delete.
3. In the **Actions** column, click the Delete icon.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully and its status is changed to **Deleted**, click the delete icon in the **Actions** column again.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. In the **Actions** column, click the Delete icon again.
   2. In the **Delete Instance** window, click **OK**.

## Procedure to delete instances from the instance details page
{: #np_deletinginstance-procedure2}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **NetApp ONTAP Select Instances** table, click the instance to delete.
3. Click the overflow menu icon next to **NetApp console**, and click **Delete Instance**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. Click the overflow menu icon next to **vCenter console** again and click **Delete Instance**.
   2. In the **Delete Instance** window, click **OK**.

## Related links
{: #np_deletinginstance-related}

* [Ordering NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp/np_orderinginstances.html)
* [Viewing NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp/np_viewinginstances.html)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
