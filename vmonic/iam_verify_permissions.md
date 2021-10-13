---

copyright:

  years:  2019, 2021

lastupdated: "2021-09-10"

keywords: IAM user, user role, user permission, IAM account administrator

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Locating an IAM account administrator
{: #iam_verify_permissions}

Use {{site.data.keyword.cloud}} Identity and Access Management (IAM) to define users for platform services and to control user access to resources across {{site.data.keyword.cloud_notm}}. For more information about user roles (Viewer, Editor, Operator, and Administrator), see the table that shows roles and actions in [Platform management roles and permissions](/docs/vmwaresolutions?topic=vmwaresolutions-iam#iam-roles).

You must have an IAM account administrator role to complete various tasks. For example, setting account credentials and granting platform access to users.

If you do not have an administrator role and you want to complete a task that requires the administrator role, you can locate someone with that role. That person can then assign access. For more information about what an account administrator can do, see [IAM access](/docs/account?topic=account-userroles#userroles).

## Locating an account owner with the administrator role
{: #iam_verify_permissions-locate-admin}

To identify an account owner who has the administrator role, complete the following steps:

1. Log in to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com).
2. On the upper right of the window, select the {{site.data.keyword.cloud_notm}} account that you want to use.
3. Click **Manage** > **Access (IAM)** > **Users**.
4. Scroll down through the list until you find a name with an oval icon to the right with the word **Owner**, which indicates that the user is an account administrator.
5. Write down the name of this user.

If the owner you identified is not available or has left the company, find one or more other users with the administrator role. Consider who might be assigned the role, for example, a manager, team lead, or someone who works directly with {{site.data.keyword.cloud_notm}} customers.

To locate a user with an administrator role, click the name link and review the information on the **Access policies** tab. Look for the following values:
* Role - Administrator
* Access Type - Service
* Policy Details - All VMware® Solutions resources

## Assigning access
{: #iam_verify_permissions-assign-access}

After you find the account owner or another user with an administrator role, that person must perform the following steps to assign access:

1. Log in to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com) as the {{site.data.keyword.cloud_notm}} account owner.
2. On the upper right of the window, select the {{site.data.keyword.cloud_notm}} account that you want to use.
3. At the right side of the banner, click **Manage** > **Access (IAM)**.
4. From the left navigation pane, click **Users**.
5. In the row for the user that you want to assign access, click the vertical overflow menu next to the **Status** column, and then click **Assign access**.
6. Expand the **Assign users additional access** pane, and then click the **IAM services** card.
7. Under **What type of access do you want to assign**, select **VMware Solutions** from the list of services, and then select **Account** as the access policy scope.
8. Under **VMware Instances**, select the **string equals** operator, and then select **All instances**.
9. Under **Platform access**, select **Administrator**.
10. Click **Add > Assign**.

## Related links
{: #iam_verify_permissions-related}

* [What is {{site.data.keyword.cloud_notm}} IAM](/docs/account?topic=account-iamoverview)
* [Managing access to resources](/docs/account?topic=account-assign-access-resources)
