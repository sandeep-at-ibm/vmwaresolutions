---

copyright:

  years:  2021

lastupdated: "2021-09-23"

keywords: zerto, zerto self-service portal, zerto portal access procedure

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Accessing the Zerto Self-Service Portal
{: #shared_zerto-portal}

The Zerto service is available and ready-to-use in all virtual data centers. Use Zerto as a service to replicate your VMs between your {{site.data.keyword.cloud}} data centers to {{site.data.keyword.cloud_notm}}. The Zerto service is enabled by default.

You can access the Zerto portal on the virtual data center details page when the virtual data center is in the **Ready to use** state. For more information, see [Procedure to view the virtual data center summary](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-summary#shared_viewing-vdc-summary-procedure) or [Procedure to view virtual data center details](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-details#shared_viewing-vdc-details-procedure).

Service charges are incurred only if you choose to use the services.
{: note}

## Before you begin
{: #shared_zerto-portal-prereq}

- Review the following limitations for Zerto:
   - The current version of Zerto is v8.5 u2 and is only compatible with the N-1 and N+1 level of Zerto on your on-premises site.
   - Currently, Zerto does not support the replication of stand-alone VMs but only vApps with VMs inside them. IBM is working with Zerto to resolve this limitation.
- You must reset the zOrg administrator password before you can log in to the Zerto portal.

## Procedure to access the Zerto Self-Service Portal from the virtual data center
{: #shared_zerto-portal-procedure}

1. Under **Recommended services** on the virtual data center details page, click **Reset ZORG password**.
2. In the **Reset ZORG password** window, click **Reset password**.
3. Click **Zerto portal** and login to the self-service portal.

After you reset your password on a virtual data center, you have access to the Zerto portal from all virtual data centers in your account. You can now manage VMs across all of your virtual data centers.
{: note}

For more information about using the Zerto Self-Service Portal to create Virtual Protection Groups, see [Zerto Virtual Manager Administration Guide - VMware vSphere Environment](https://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Manager%20vSphere%20Administration%20Guide.pdf){: external}.

## Licenses and fees for Zerto
{: #shared_zerto-portal-fees}

Zerto usage incurs charges on demand. For more information, see [VMware Solutions Shared pricing](/docs/vmwaresolutions?topic=vmwaresolutions-shared_pricing).

## Related links
{: #shared_zerto-portal-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [Ordering virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [Ordering a Zerto Cloud Connector](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-cc-order)
* [Viewing Zerto Cloud Connector details](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-cc-view)
* [Deleting Zerto Cloud Connector](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-cc-delete)
* [Zerto Installation Guide for VMware vSphere Environments & Microsoft Hyper-V Environments](https://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Installation%20Guide%20for%20vSphere%20and%20Hyper-V.pdf){: external}
* [Zerto Support and Service](https://www.zerto.com/company/support-and-service/){: external}
