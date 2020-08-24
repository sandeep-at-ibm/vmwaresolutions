---

copyright:

  years:  2020

lastupdated: "2020-08-21"

keywords: ordering prerequisites, before you order, pre-order checklist, before first order

subcollection: vmwaresolutions

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Setting up your environment for your first order
{: #completing_checklist}

When you order your instance for the first time, ensure that your environment is ready for your order. Follow the instructions in the **Before you begin** section at the top of the ordering page. The instructions might vary depending on the instance type that you select.

## Procedure to set up your environment for your first order
{: #completing_checklist-procedure}
{: help}
{: support}

1. [Upgrade your account to a Pay-As-You-Go account](/docs/account?topic=account-upgrading-account#upgrade-paygo).
2. [Create a classic infrastructure API key](/docs/account?topic=account-classic_keys#create-classic-infrastructure-key).
3. Retrieve API key and user name by clicking **Retrieve credentials**.
4. Review the user name and API key that are automatically entered and then click **Save credentials**. If you receive a message that administrator access is required, you can locate an account administrator by using the steps in [Locating an IAM account administrator](/docs/vmwaresolutions?topic=vmwaresolutions-iam_verify_permissions).
5. Verify or update the [permissions](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req) for your {{site.data.keyword.cloud}} infrastructure account.
6. Convert your {{site.data.keyword.cloud_notm}} infrastructure account to a [virtual routing and forwarding (VRF) account](/docs/direct-link?topic=direct-link-what-happens-during-the-account-conversion-process).
7. Enable [service endpoints](/docs/account?topic=account-vrf-service-endpoint#service-endpoint) to connect to certain services over the {{site.data.keyword.cloud_notm}} private network rather than the public network.

## Results
{: #completing_checklist-results}

* The {{site.data.keyword.cloud_notm}} infrastructure credentials are stored in the {{site.data.keyword.vmwaresolutions_short}} console after the first order. Future orders use the stored credentials by default.
* After you complete the checklist instructions, the checklist disappears next time when you are on the ordering page. You can update the credentials on the **Settings** page later on.
* If the API key for your {{site.data.keyword.cloud_notm}} infrastructure account changes, you must update the key on the **Settings** page in the {{site.data.keyword.vmwaresolutions_short}} console.

## Related links
{: #completing_checklist-related}

* [Managing user accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
