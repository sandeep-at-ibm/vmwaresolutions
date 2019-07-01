---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Zerto on IBM Cloud
{: #zerto_ordering}

You can order the Zerto on {{site.data.keyword.cloud}} service when you order a new instance with the service included or by adding the service to your existing instance.

## Billing for Zerto replication
{: #zerto_ordering-billing}

VMs that are replicated by using Zerto are metered by Zerto and {{site.data.keyword.cloud_notm}}. Your bill for this usage is charged through an {{site.data.keyword.cloud_notm}} billable account instead of an {{site.data.keyword.cloud_notm}} infrastructure account.

Before you order Zerto on {{site.data.keyword.cloud_notm}}, ensure that your {{site.data.keyword.cloud_notm}} account is a billable account, and that it is linked to the same {{site.data.keyword.cloud_notm}} infrastructure account where your instance is deployed.

If you have a Zerto on {{site.data.keyword.cloud_notm}} installation from V3.0 or earlier, your VM replication costs are still being billed by using {{site.data.keyword.cloud_notm}} infrastructure billing. If your accounts and billing settings meet the requirements that are listed previously, you can convert your Zerto billing method to billable.

On the {{site.data.keyword.vmwaresolutions_short}} console, you are prompted to convert from the {{site.data.keyword.cloud_notm}} infrastructure plan to a billable plan and to upgrade your {{site.data.keyword.cloud_notm}} account to a billable account, if needed.

* For information about free and billable accounts, see [Account types](/docs/account?topic=account-accounts).
* For information about upgrading to a billable account, see [Upgrading your account](/docs/account?topic=account-upgrading-account).
* For information about linking your {{site.data.keyword.cloud_notm}} and your {{site.data.keyword.cloud_notm}} infrastructure accounts, see [Switching to IBMid and linking accounts](/docs/account?topic=account-unifyingaccounts).

## Ordering Zerto on IBM Cloud for a new instance
{: #zerto_ordering-new}

You can order a new instance with Zerto on {{site.data.keyword.cloud_notm}} by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, select **Zerto on IBM Cloud** in the **Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click the **Zerto on IBM Cloud** card in the **VMware Services** section. Specify the service settings and select **Add to New Instance**.

## Ordering Zerto on IBM Cloud for an existing instance
{: #zerto_ordering-existing}

You can add the Zerto on {{site.data.keyword.cloud_notm}} service to an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service to, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click the **Zerto on IBM Cloud** card in the **VMware Services** section. Specify the service settings and select **Add to Existing Instance**.

If you add Zerto on {{site.data.keyword.cloud_notm}} to a vCenter Server instance that has an ESXi server that is in maintenance mode, you must use the Zerto Virtual Manager (ZVM) console and the pre-populated Zerto Virtual Replication Appliance (VRA) IP address to manually deploy the VRA virtual machine (VM).
{:note}

## Ordering Zerto on IBM Cloud for private-only instances
{: #zerto_ordering-private-only}

If you want to add Zerto on {{site.data.keyword.cloud_notm}} to a private-only instance, ensure that the following requirements are met:
* You are responsible for setting up your own proxy server to connect to the internet. For more information, see [Public network connectivity](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* You must also configure the Call Home feature for Zerto. For more information about Zerto Call Home, see [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:external}.

## Related links
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Managing Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Managed Services for Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com website](https://www.zerto.com){:external}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:external}
