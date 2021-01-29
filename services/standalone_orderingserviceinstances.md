---

copyright:

  years:  2016, 2021

lastupdated: "2021-01-27"

keywords: VMware HCX standalone, HCX on-premises, order HCX

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:note: .note}

# Ordering on-premises VMware HCX instances
{: #standalone_orderingserviceinstances}

You can order an on-premises VMware HCX® instance without associating it to any VMware vCenter Server® instance for licensing and activation of your on-premises HCX installation.

## Before you begin
{: #standalone_orderingserviceinstances-reqs}

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount).
*  You reviewed all the considerations in [Considerations when installing on-premises HCX instances](/docs/vmwaresolutions?topic=vmwaresolutions-standalone_considerations).

## Procedure to order on-premises VMware HCX instances
{: #standalone_orderingserviceinstances-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll down to the **On-premises HCX activation keys** table and click **Provision new**.
3. Specify the resource group.

   If **No resource group available** is displayed in this field, you currently do not have the permission to add the instance to any resource group in this account. Contact the account owner to be assigned an Editor or Administrator role on a resource group in the account. For more information, see [IAM access](/docs/account?topic=account-userroles).
   {:note}

4. Specify a new on-premises instance name, or use the default one **hcx-_xx_** where _xx_ represents two randomly generated alphabetic characters.
5. Click the link or links of the terms that apply to your order, and ensure that you agree with these terms before you order the instance.
6. Click **Provision**.

## Results
{: #standalone_orderingserviceinstances-results}

The ordering of the service activation key starts automatically. You receive confirmation that the order is being processed and you can check the status of the order by viewing the instance details.

When the activation key is ready to use, the status of the instance is changed to **Installed** and you receive a notification by email.

## What to do next
{: #standalone_orderingserviceinstances-next}

View and manage the on-premises HCX instance that you ordered.

## Related links
{: #standalone_orderingserviceinstances-related}

* [Viewing on-premises HCX instances](/docs/vmwaresolutions?topic=vmwaresolutions-standalone_viewingserviceinstances)
* [Deleting on-premises HCX instances](/docs/vmwaresolutions?topic=vmwaresolutions-standalone_deletingserviceinstances)
* [Glossary of HCX terms](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_glossary)
* [VMware Hybrid Cloud Extension documentation](https://cloud.vmware.com/vmware-hcx/resources){:external}
