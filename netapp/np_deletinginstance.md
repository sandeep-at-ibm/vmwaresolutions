---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-10"

---

# Deleting NetApp ONTAP Select instances

To release the components that you ordered in a NetApp ONTAP Select instance, delete the instance.

When you delete a NetApp ONTAP Select instance, the following components are released sequentially:
1. The deployed NetApp ONTAP Select clustered VMs (virtual machines) and the NetApp ONTAP Select Deploy VM
2. Support and Services fee
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by {{site.data.keyword.cloud}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} billing cycle. At the end of the billing cycle, which is typically 30 days, the subnets and VLANs are reclaimed and the instance deletion is completed.

**Attention:** You are billed until the end of the billing cycle for the deleted instance.

## Procedure

To delete a NetApp ONTAP Select instance from the **Deployed Instances** page, use the following procedure:
   1. Click **Deployed Instances** from the left navigation pane.
   2. In the **NetApp ONTAP Select Instances** table, locate the instance to delete.
   3. In the **Actions** column, click the delete icon. The status of the instance is changed to **Deleting**.
   4. When the instance is deleted successfully and its status is changed to **Deleted**, click the delete icon in the **Actions**
   column again.
   5. In the **Delete Instance** window, click **OK** to remove the instance from the {{site.data.keyword.vmwaresolutions_full}}
   console.

To delete a NetApp ONTAP Select instance from the instance details page, use the following procedure:
   1. Click **Deployed Instances** from the left navigation pane.
   2. In the **NetApp ONTAP Select Instances** table, click the instance to delete.
   3. Click the overflow menu icon to the right of **NetApp console**.
   4. Click **Delete Instance**.

## Related links

* [Ordering NetApp ONTAP Select instances](np_orderinginstances.html)
* [Viewing NetApp ONTAP Select instances](np_viewinginstances.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
