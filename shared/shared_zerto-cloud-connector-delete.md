---

copyright:

  years:  2021

lastupdated: "2021-09-23"

keywords: zerto, delete zerto cloud connector

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Deleting Zerto Cloud Connector
{: #shared_zerto-cc-delete}

You can delete the Zerto Cloud Connector (ZCC) when it is no longer needed.

## Before you begin
{: #shared_zerto-cc-delete-prereq}

* Review the following considerations before you delete Zerto Cloud Connector:
   * The on-premises site is unpaired from the {{site.data.keyword.cloud_notm}} site and all workloads that are moved from the on-premises site are deleted.
   * All Virtual Protection Groups and the VMs replicated from the on-premises site to the {{site.data.keyword.cloud_notm}} site are deleted.
* When you delete the ZCC, you unpair the on-premises workloads from {{site.data.keyword.cloud_notm}}.

## Procedure to delete Zerto Cloud Connector
{: #shared_zerto-cc-delete-procedure}

1. Under the **Enabled services** on the virtual data center details page, click **Delete ZCC** in the Zerto Cloud Connector details table.
2. In the **Delete Zerto Cloud Connector** window, review and accept the delete confirmation and click **Delete**. The status of the ZCC is changed to **Deleting**. When the ZCC is deleted successfully, the status is changed to **Deleted**.

## Related links
{: #shared_zerto-cc-delete-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [Ordering virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [Accessing the Zerto Self-Service Portal](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-portal)
* [Ordering a Zerto Cloud Connector](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-cc-order)
* [Viewing Zerto Cloud Connector details](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-cc-view)
* [Zerto Installation Guide for VMware vSphere Environments & Microsoft Hyper-V Environments](https://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Installation%20Guide%20for%20vSphere%20and%20Hyper-V.pdf){: external}
* [Zerto Support and Service](https://www.zerto.com/company/support-and-service/){: external}
