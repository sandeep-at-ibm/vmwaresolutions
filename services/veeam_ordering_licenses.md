---

copyright:

  years:  2020, 2021

lastupdated: "2021-09-23"

keywords: Veeam, Veeam license, order Veeam license, Veeam 10

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# Ordering Veeam licenses
{: #veeam_ordering_licenses}

You can order a Veeam® license without associating it to any VMware® vCenter Server® instance for licensing and activation of your on-premises workloads.

## Before you begin
{: #veeam_ordering_licenses-before-begin}

Ensure that you configured the {{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount).

## Procedure to order Veeam licenses
{: #veeam_ordering_licenses_ordering-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll down to the **Veeam licenses** table and click **Provision new**.
3. Specify the resource group.

   If **No resource group available** is displayed in this field, you currently do not have the permission to add the instance to any resource group in this account. Contact the account owner to be assigned an Editor or Administrator role on a resource group in the account. For more information, see [IAM access](/docs/account?topic=account-userroles).
   {: note}

4. Specify a new license name or use the default name **veeam-_xx_** where _xx_ represents two randomly generated alphabetic characters.
5. In the **License note** field, enter a note. For example, you can enter a note to help you identify associated instances.
6. Specify the number of virtual machines (VMs) you want to license.
7. Click the link or links of the terms that apply to your order. Ensure that you agree with these terms before you order the license.
8. Click **Add to estimate** or **Create**.

## Results
{: #veeam_ordering_licenses-results}

The ordering of the Veeam license starts automatically. You receive confirmation that the order is being processed and you can check the status of the order by viewing the license details.

When the license is ready to use, the status of the license is changed to **Installed** and you receive a notification by email.

## Related links
{: #veeam_ordering_licenses-related}

* [Veeam v9.5 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations)
* [Veeam v11 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Ordering Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering)
* [Managing Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-managingveeam)
* [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses)
* [Ordering and configuring IBM Cloud Object Storage with Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-icos_ordering)
