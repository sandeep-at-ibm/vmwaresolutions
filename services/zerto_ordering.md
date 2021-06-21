---

copyright:

  years:  2016, 2021

lastupdated: "2021-05-05"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Zerto
{: #zerto_ordering}

You can include the Zerto service with a new VMware® vCenter Server® instance or add the service to your existing vCenter Server instance.

## Billing for Zerto replication
{: #zerto_ordering-billing}

VMs that are replicated by using Zerto are metered by Zerto and {{site.data.keyword.cloud}}. Your bill for this usage is charged through an {{site.data.keyword.cloud_notm}} billable account instead of an {{site.data.keyword.cloud_notm}} infrastructure account.

Before you order Zerto, ensure that your {{site.data.keyword.cloud_notm}} account is a billable account, and that it is linked to the same {{site.data.keyword.cloud_notm}} infrastructure account where your instance is deployed.

### Viewing Zerto charges
{: #zerto_ordering-view-charge}

To view your Zerto usage charges, follow these steps:

1. Go to the [IBM Cloud Billing and Usage](https://cloud.ibm.com/billing/usage) page.
2. From the **Filter by group** list, select **VMware Solutions**.

### Zerto installations from V3.0 or earlier
{: #zerto_ordering-30-install}

If you have a Zerto installation from V3.0 or earlier, your VM replication costs are still being billed by using {{site.data.keyword.cloud_notm}} infrastructure billing. If your accounts and billing settings meet the requirements that are listed previously, you can convert your Zerto billing method to billable.

On the {{site.data.keyword.vmwaresolutions_short}} console, you are prompted to convert from the {{site.data.keyword.cloud_notm}} infrastructure plan to a billable plan and to upgrade your {{site.data.keyword.cloud_notm}} account to a billable account, if needed.

* For more information about free and billable accounts, see [Account types](/docs/account?topic=account-accounts).
* For more information about upgrading to a billable account, see [Upgrading your account](/docs/account?topic=account-upgrading-account).
* For more information about linking your {{site.data.keyword.cloud_notm}} and your {{site.data.keyword.cloud_notm}} infrastructure accounts, see [Requiring MFA for users in your account](/docs/account?topic=account-enablemfa).

## Ordering Zerto for a new instance
{: #zerto_ordering-new}

When you [order the instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the services section and click **Zerto** in the **Business continuity and migration** category. Follow the steps to add the service to your instance.

## Ordering Zerto for an existing instance
{: #zerto_ordering-existing}

1. On the instance details page, click **Services** on the left navigation pane.
2. Click **Add** to add the service.
3. On the **Services** page, locate the **Zerto** service and toggle its switch on.
4. Follow the steps to configure and add the service to your instance.

If you add Zerto to a vCenter Server instance that has a VMware ESXi™ server that is in maintenance mode, you must use the Zerto Virtual Manager (ZVM) console. Use the pre-populated Zerto Virtual Replication Appliance (VRA) IP address to manually deploy the VRA virtual machine (VM).
{:note}

## Ordering Zerto for private-only instances
{: #zerto_ordering-private-only}

If you want to add Zerto to a private-only instance, ensure that the following requirements are met:
* You are responsible for setting up your own proxy server to connect to the internet.
* You must also configure the Call Home feature for Zerto. For more information about Zerto Call Home, see [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:external}.

## Related links
{: #zerto_ordering-related}

* [Zerto overview](/docs/vmwaresolutions?topic=vmwaresolutions-addingzertodr)
* [Managing Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-managingzertodr)
* [Managed Disaster Recovery Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_zerto_services)
* [Zerto](https://www.zerto.com){:external}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:external}
