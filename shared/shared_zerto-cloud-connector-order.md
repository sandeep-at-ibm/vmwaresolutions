---

copyright:

  years:  2021

lastupdated: "2021-11-09"

keywords: zerto, order zerto cloud connector

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Ordering a Zerto Cloud Connector
{: #shared_zerto-cc-order}

Optionally order Zerto Cloud Connector (ZCC) as an enhanced Zerto option to link on-premises workloads to {{site.data.keyword.cloud_notm}} and replicate on-premises virtual machines (VMs) to {{site.data.keyword.cloud_notm}}. The Zerto and ZCC services seamlessly integrate as a managed solution to help your enterprise achieve virtual machine (VM) replication and disaster recovery. You can order one ZCC per virtual data center.

## Before you begin
{: #shared_zerto-cc-order-prereq}

- Review the following limitations that currently exist for Zerto Cloud Connector:
   - You can create a ZCC only if you have a network that is created in VMware® Cloud Director. You must ensure that you do not delete that network, either while the ZCC order is in progress or later.
   - You cannot use the ``172.16.3.x.``, ``172.16.7.x``, or ``10.0.0.0/8`` subnets for your on-premises Virtual Replication Appliance or Zerto Virtual Manager deployments if you are ordering a Zerto Cloud Connector.
- You must create Organization networks before you order a ZCC. For more information, see [Creating a network](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-create-network).

## Procedure to order a Zerto Cloud Connector from the virtual data center
{: #shared_zerto-cc-order-procedure}

1. Under **Enabled services** on the virtual data center details page, click **Order a Zerto Cloud Connector**.
2. Select an organization network and enter the IP address for the new VM to deploy to that network.
3. Review the hourly price and click **Order**. The **Zerto Cloud Connector (ZCC)** table displays on the virtual data center details page and the status changes to **Creating**.
4. You must pair the on-premises workloads to {{site.data.keyword.cloud_notm}} before you can use ZCC. Generate a pairing token when the ZCC status changes to **Ready to use**.
   1. In the **Zerto Cloud Connector (ZCC)** table, expand **Pairing token**.
   2. Click **Generate token**. The generated token link expires in 48 hours and a new token is generated.
   3. Click the **Copy** icon ![Copy icon](../../icons/copy.svg "Copy") to copy the pairing token key.
   4. From the on-premises site, use the pairing token key to link the on-premises virtual data centers to {{site.data.keyword.cloud_notm}}. For more information, see [Pairing Sites to Enable Replicating From One Site to Another Site](https://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Zerto%20Cloud%20Manager%20%28ZCM%29%20Online%20Help/content/zvr_quick_start_vc/pairing_sites_to_enable_replicating_from.htm){: external}.

## Related links
{: #shared_zerto-cc-order-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [Ordering virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [Accessing the Zerto Self-Service Portal](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-portal)
* [Viewing Zerto Cloud Connector details](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-cc-view)
* [Deleting Zerto Cloud Connector](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-cc-delete)
* [Zerto Installation Guide for VMware vSphere Environments & Microsoft Hyper-V Environments](https://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Installation%20Guide%20for%20vSphere%20and%20Hyper-V.pdf){: external}
* [Zerto Support and Service](https://www.zerto.com/company/support-and-service/){: external}
