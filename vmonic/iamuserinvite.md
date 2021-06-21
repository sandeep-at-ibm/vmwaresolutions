---

copyright:

  years:  2016, 2021

lastupdated: "2021-04-16"

keywords: IAM user, invite user, service access

subcollection: vmwaresolutions

---

# Inviting users to access services and resources
{: #iamuserinvite}

{{site.data.keyword.cloud}} for VMware® Solutions is integrated with {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) for collaboration among multiple users. After you sign up for an {{site.data.keyword.cloud_notm}} account and log in to the {{site.data.keyword.vmwaresolutions_short}} console, you can add users to the {{site.data.keyword.cloud_notm}} account. These added users can share the services and resources that are provisioned for the account.

## Before you begin
{: #iamuserinvite-reqs}

* Ensure that you are the account owner or that your platform management role for the **VMware Solutions** service is **Administrator**.
* Ensure that you reviewed the user roles and permissions in [Managing user access with Identity and Access Management](/docs/vmwaresolutions?topic=vmwaresolutions-iam#iam).

## Procedure to invite users to access services and resources
{: #iamuserinvite-procedure}

1. At the right side of the banner, click **Manage > Access (IAM)**.
2. From the left navigation pane, click **Users**, and then click **Invite users** on the **Users** page.
3. On the **Invite users** page, in the **Users** section, enter the email addresses of the users that you want to invite in the **Email address** field.
4. In the **Access** section, expand **Services**, and then complete the following tasks:
   1. Select **Resource** from the **Assign access to** list.
   2. Select **VMware Solutions** from the **Services** list.
   3. Select the platform access role that you want to assign to the users. It can be **Administrator**, **Editor**, **Operator**, or **Viewer**.
5. Click **Invite users**.

## Results
{: #iamuserinvite-results}

After the added users accept your invitation, they can log in to the {{site.data.keyword.vmwaresolutions_short}} console and switch to your account. To do so, in their profile settings, users click their user account icon from the {{site.data.keyword.vmwaresolutions_short}} console banner. Then, the added users can collaborate and share the services and resources available in your specified account.

## Related links
{: #iamuserinvite-related}

* [Inviting users to an account](/docs/account?topic=account-iamuserinv)
* [Setting up user access](/docs/account?topic=account-access-getstarted)
* [What is {{site.data.keyword.cloud_notm}} IAM](/docs/account?topic=account-iamoverview)
* [Migrating pre-V2.5 vCenter Server instances to {{site.data.keyword.cloud_notm}} accounts](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addinstancetousraccount)
