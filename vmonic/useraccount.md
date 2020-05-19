---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-16"

keywords: set credentials, user credentials, set notifications

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Managing user accounts and settings
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} communicates with the {{site.data.keyword.cloud_notm}} infrastructure through {{site.data.keyword.slapi_short}} calls. To access the {{site.data.keyword.slapi_short}} securely, you must link the credentials of your {{site.data.keyword.cloud_notm}} infrastructure account to your {{site.data.keyword.cloud_notm}} account.

You can also specify whether you want to receive email and console notifications for various events.

## Before you begin
{: #useraccount-reqs}

* You can link only one {{site.data.keyword.cloud_notm}} infrastructure account to one {{site.data.keyword.cloud_notm}} user account.
* The {{site.data.keyword.cloud_notm}} infrastructure account that you're using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} infrastructure account requirements](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).
* If the API key for your {{site.data.keyword.cloud_notm}} infrastructure account changes, you must update the key on the **Settings** page in the {{site.data.keyword.vmwaresolutions_short}} console.

   It is your responsibility to ensure that the API key that is saved on the **Settings** page is correct and up-to-date. Otherwise, operations that require API key validation might fail.
   {:important}

## Procedure to set user account credentials
{: #useraccount-set-cred}
{: help}
{: support}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Settings** from the left navigation pane.
2. In the **IBM Cloud Infrastructure Credentials** area, review the information for the steps that you need to take.
3. If you have both an {{site.data.keyword.cloud_notm}} infrastructure account and an {{site.data.keyword.cloud_notm}} account that are linked, click **Retrieve** to complete the credentials automatically.
4. If you have both an {{site.data.keyword.cloud_notm}} infrastructure account and an {{site.data.keyword.cloud_notm}} account that are not linked, you must link them. Follow the instructions in [Upgrading your account](/docs/account?topic=account-upgrading-account), then click **Retrieve** to complete the credentials automatically.
5. If you do not have an {{site.data.keyword.cloud_notm}} infrastructure account, and you do not have a billable  {{site.data.keyword.cloud_notm}} account, first [upgrade your account](/docs/account?topic=account-upgrading-account) and then [create a classic infrastructure API key](/docs/iam?topic=iam-classic_keys#create-classic-infrastructure-key).
6. Click **Save Credentials**. If you receive a message that administrator access is required, you can locate an account administrator using the steps in [Locating an IAM account administrator](/docs/vmwaresolutions?topic=vmwaresolutions-iam_verify_permissions).

## Procedure to set notifications
{: #useraccount-set-notif}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Settings** from the left navigation pane.
2. If you want to be notified by email when events occur, click **Enable email notifications**.
3. If you want to be notified in the console when events occur, click **Enable console notifications**.

## Results
{: #useraccount-results}

After the {{site.data.keyword.cloud_notm}} account and the {{site.data.keyword.cloud_notm}} infrastructure account are linked, the console automatically retrieves the {{site.data.keyword.cloud_notm}} infrastructure account credentials to communicate with your VMware environment on {{site.data.keyword.cloud_notm}}.

The stored {{site.data.keyword.cloud_notm}} infrastructure account credentials are used in future operations that require interaction with the {{site.data.keyword.cloud_notm}} infrastructure.

If email or console notifications are enabled for certain instance events, you're notified by email or console messages when these events occur.

## Related links
{: #useraccount-related}

* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
* [Notifications](/docs/vmwaresolutions?topic=vmwaresolutions-notifications)
* [SoftLayer API](/docs/customer-portal?topic=customer-portal-customerportal_api)
* [Locating an IAM account administrator](/docs/vmwaresolutions?topic=vmwaresolutions-iam_verify_permissions)
