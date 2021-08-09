---

copyright:

  years:  2021

lastupdated: "2021-08-05"

keywords: zerto, zerto install, tech specs zerto

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing Zerto for VMware Solutions Shared
{: #shared_zerto}

The Zerto service is available and ready-to-use in all virtual data centers. As an enhancement to the Zerto service, you can optionally order the Zerto Cloud Connector (ZCC) service as a day-two operation. These services seamlessly integrate as a managed solution to help your enterprise achieve virtual machine (VM) replication and disaster recovery.

Service charges are incurred only if you choose to use the services.
{:note}

## Zerto
{: #shared_zerto-portal}

Use Zerto as a service to replicate your VMs between your {{site.data.keyword.cloud}} data centers to {{site.data.keyword.cloud_notm}}. The Zerto service is enabled by default.

You can access the Zerto portal on the virtual data center details page when the virtual data center is in the **Ready to use** state. For more information, see [Procedure to view virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_managing#shared_managing-viewing).

### Limitations for Zerto
{: #shared_zerto-portal-limitations}

- The current version of Zerto is v8.5 u2 and is only compatible with the N-1 and N+1 level of Zerto on your on-premises site.
- Currently, Zerto does not support the replication of stand-alone VMs but only vApps with VMs inside them. IBM is working with Zerto to resolve this limitation.

### Procedure to access the Zerto Self-Service Portal from the virtual data center
{: #shared_zerto-portal-proc-access}

You must reset the zOrg administrator password before you can log in to the Zerto portal.

1. Under **Recommended services** on the virtual data center details page, click **Reset ZORG password**.
2. In the **Reset ZORG password** window, click **Reset password**.
3. Click **Zerto portal** and login to the self-service portal.

After you reset your password on a virtual data center, you have access to the Zerto portal from all virtual data centers in your account. You can now manage VMs across all of your virtual data centers.
{:note}

For more information about using the Zerto Self-Service Portal to create Virtual Protection Groups, see [Zerto Virtual Manager Administration Guide - VMware vSphere Environment](https://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Manager%20vSphere%20Administration%20Guide.pdf){:external}.

### Licenses and fees for Zerto
{: #shared_zerto-portal-fees}

Zerto usage incurs charges on demand. For more information, see [VMware Solutions Shared pricing](/docs/vmwaresolutions?topic=vmwaresolutions-shared_pricing).

## Zerto Cloud Connector
{: #shared_zerto-cloud-connector}

Optionally order Zerto Cloud Connector (ZCC) as an enhanced Zerto option to link on-premises workloads to {{site.data.keyword.cloud_notm}} and replicate on-premises VMs to {{site.data.keyword.cloud_notm}}. You can order one ZCC per virtual data center.

### Limitations for Zerto Cloud Connector
{: #shared_zerto-cloud-limitations}

The following limitations currently exist for Zerto Cloud Connector.

- You can create a ZCC only if you have a network that is created in VMware® Cloud Director. You must ensure that you do not delete that network, either while the ZCC order is in progress or later.
- You cannot use the ``172.16.3.x.``, ``172.16.7.x``, or ``10.0.0.0/8`` subnets for your on-premises Virtual Replication Appliance or Zerto Virtual Manager deployments if you are ordering a Zerto Cloud Connector.

### Procedure to order a Zerto Cloud Connector from the virtual data center
{: #shared_zerto-cloud-connector-order}

You must create Organization networks before you order a ZCC. For more information, see [Creating a network](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-create-network).
{:note}

1. Under **Enabled services** on the virtual data center details page, click **Order a Zerto Cloud Connector**.
2. Select an organization network and enter the IP address for the new VM to deploy to that network.
3. Review the hourly price and click **Order**. The **Zerto Cloud Connector (ZCC)** table displays on the virtual data center details page and the status changes to **Creating**.

You must pair the on-premises workloads to {{site.data.keyword.cloud_notm}} before you can use ZCC. Generate a pairing token when the ZCC status changes to **Ready to use**.

### Viewing Zerto Cloud Connector details and generating a pairing token
{: #shared_zerto-view-pair}

In the **Zerto Cloud Connector (ZCC)** table, view the ZCC details.

| Item | Description |
|:---- |:----------- |
| ZCC VM Name | The name of the ZCC virtual machine. |
| IP address | The IP address of the VM deployed into the organization network. |
| Network (CIDR) | The organization network. |
| Status | The status of the ZCC. |
{: caption="Table 1. Zerto Cloud Connector details" caption-side="top"}

The ZCC can have different statuses.

| Status | Description |
|:------ |:----------- |
| Creating | The ZCC is being created. |
| Ready to use | The ZCC is ready to use. |
| Deleting | The ZCC is being deleted. |
| Deleted | The ZCC is deleted. |
{: caption="Table 2. Status descriptions for Zerto Cloud Connector" caption-side="top"}

Before the ZCC can operate, you must pair the on-premises workloads to {{site.data.keyword.cloud_notm}}.

1. In the **Zerto Cloud Connector (ZCC)** table, expand **Pairing token**.
2. Click **Generate token**. The generated token link expires in 48 hours and a new token is generated.
3. Click the **Copy** icon to copy the pairing token key.
3. From the on-premises site, use the pairing token key to link the on-premises virtual data centers to {{site.data.keyword.cloud_notm}}. For more information, see [Pairing Sites to Enable Replicating From One Site to Another Site](https://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Zerto%20Cloud%20Manager%20%28ZCM%29%20Online%20Help/content/zvr_quick_start_vc/pairing_sites_to_enable_replicating_from.htm){:external}.

## Deleting Zerto backups
{: #shared_zerto-delete}

### Considerations when you delete Zerto Cloud Connector
{: #shared_zerto-delete-considerations}

Review the following considerations before you delete Zerto Cloud Connector:

* The on-premises site is unpaired from the {{site.data.keyword.cloud_notm}} site and all workloads that are moved from the on-premises site are deleted.
* All Virtual Protection Groups and the VMs replicated from the on-premises site to the {{site.data.keyword.cloud_notm}} site are deleted.

### Procedure to delete Zerto Cloud Connector
{: #shared_zerto-delete-procedure}

When you delete the ZCC, you unpair the on-premises workloads from {{site.data.keyword.cloud_notm}}.

1. Under the **Enabled services** on the virtual data center details page, click **Delete ZCC** in the Zerto Cloud Connector details table.
2. In the **Delete Zerto Cloud Connector** window, review and accept the delete confirmation and click **Delete**. The status of the ZCC is changed to **Deleting**. When the ZCC is deleted successfully, the status is changed to **Deleted**.

## Related links
{: #shared_zerto-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [Ordering virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [Zerto Installation Guide for VMware vSphere Environments & Microsoft Hyper-V Environments](https://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Installation%20Guide%20for%20vSphere%20and%20Hyper-V.pdf){:external}
* [Zerto Support and Service](https://www.zerto.com/company/support-and-service/){:external}
