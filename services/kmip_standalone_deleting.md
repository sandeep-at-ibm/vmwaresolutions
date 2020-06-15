---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-05"

keywords: KMIP for VMware, remove KMIP stand-alone, delete KMIP for VMware

subcollection: vmwaresolutions

---

{:note: .note}

# Deleting KMIP for VMware instances
{: #kmip_standalone_deleting}

Use this procedure to delete the KMIP for VMware instances that you ordered for stand-alone use.

## Before you begin
{: #kmip_standalone_deleting-req}

You must remove encryption and configuration in the following sequence:
1. Decrypt all virtual machines or vSAN datastores that are protected by this KMIP for VMware instance.
2. Remove the Key Management Server (KMS) configuration for all vCenter Server instances that are connected to this KMIP for VMware instance.
3. Remove the KMIP for VMware instance.
4. Remove all standard keys in your Key Protect or Hyper Protect Crypto Services (HPCS) instance that were in use by this KMIP for VMware instance.
5. If wanted, remove the customer root key (CRK) in your Key Protect or HPCS service instance that was in use by this KMIP for VMware instance. First, ensure that there are no other users of this CRK.
6. If wanted, remove the Key Protect or HPCS service instance that was in use by this KMIP for VMware instance. First, ensure that there are no other users of this Key Protect or HPCS service instance.

## Procedure to delete KMIP for VMware instances
{: #kmip_standalone_deleting-procedure}

1. Click **Resources** from the left navigation pane.
2. Scroll down to the **KMIP for VMware Instances** table and find the instance to delete.
3. In the **Actions** column, click the delete icon.
4. In the **Delete Instance** window, click **OK**.

   The status of the instance is changed to **Removing**. When the instance deletion is completed, the instance is no longer available in the **KMIP for VMware Instances** table.

## Related links
{: #kmip_standalone_deleting-related}

* [Ordering KMIP for VMware instances](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_ordering)
* [Adding, viewing, and deleting certificates for KMIP for VMware instances](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_addingdeletingcert)
* [Viewing KMIP for VMware instances](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_viewing)
* [KMIP for VMware solution architecture](/docs/vmwaresolutions?topic=vmwaresolutions-kmip-overview)
* [Activity Tracker events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events)
