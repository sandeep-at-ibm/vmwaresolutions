---

copyright:

  years:  2020, 2021

lastupdated: "2021-10-21"

keywords: Caveonix license, Caveonix order license, Caveonix BYOL license

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Ordering Caveonix RiskForesight licenses
{: #caveonix_license_ordering}

This information applies to VMware vCenter Server® instances only. It does not apply to VMware® Regulated Workloads or Security and Compliance Readiness Bundle instances.
{: note}

You can order a Caveonix RiskForesight™ license without associating it to any VMware vCenter Server instance for licensing and activation of your on-premises workloads.

## Before you begin
{: #caveonix_license_ordering-reqs}

Ensure that you configured the {{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount).

## Procedure to order Caveonix RiskForesight licenses
{: #caveonix_license_ordering-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll to the **Caveonix RiskForesight licenses** table and click **Provision new**.
3. Specify the resource group.

   If **No resource group available** is displayed in this field, you currently do not have the permission to add the instance to any resource group in this account. Contact the account owner to be assigned an Editor or Administrator role on a resource group in the account. For more information, see [IAM access](/docs/account?topic=account-userroles).
   {: note}

4. Specify a new license name, or use the default one **cav-_xx_** where _xx_ represents two randomly generated alphabetic characters. The name must be unique across all Caveonix service instances and all instances in the {{site.data.keyword.cloud_notm}} account.
5. In the **License notes** field, optionally enter a note. For example, you can enter a note to help you identify associated instances.
6. Specify the number of virtual machines (VMs) you want to license.
7. Click the link or links of the terms that apply to your order. Ensure that you agree with these terms before you order the license.
8. Click **Add to estimate** or **Create**.

## Results
{: #caveonix_license_ordering-results}

The ordering of the Caveonix RiskForesight license starts automatically. You receive confirmation that the order is being processed and you can check the status of the order by viewing the license details.

When the license is ready to use, the status of the license is changed to **Installed** and you receive a notification by email.

## Related links
{: #caveonix_license_ordering-related}

* [Managing Caveonix RiskForesight licenses](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_license_managing)
