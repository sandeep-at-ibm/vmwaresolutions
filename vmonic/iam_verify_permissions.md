---

copyright:

  years:  2019, 2020

lastupdated: "2020-06-05"

keywords: IAM user, user role, user permission, IAM account administrator

subcollection: vmwaresolutions

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Locating an IAM account administrator
{: #iam_verify_permissions}

You use {{site.data.keyword.cloud}} Identity and Access Management (IAM) to define users for platform services and to control user access to resources across {{site.data.keyword.cloud_notm}}. For information about user roles (Viewer, Editor, Operator, and Administrator), see the table that shows roles and actions in
[Platform management roles and permissions](/docs/vmwaresolutions?topic=vmwaresolutions-iam#iam-roles).

You must have an IAM account administrator role to complete various tasks, such as:
* Set account credentials
* Grant platform access to users

For more information about what an account administrator can do, see [IAM Access](/docs/iam?topic=iam-userroles#userroles).

If you do not have an administrator role and you want to complete a task that requires the administrator role, you can locate someone with that role. That person can then assign access.
{: tsSymptoms}

## Locating an account owner with the administrator role
{: #iam_verify_permissions-locate-admin}
{: troubleshoot}

To identify an account owner who has the administrator role, complete the following steps:
{: tsResolve}

1. Log in to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com).
2. On the upper right corner, select the **IBM Cloud account** you want to use.
3. Click **Manage** > **Access (IAM)** > **Users**.
4. Scroll down through the list until you find a name with an oval icon to the right with the word **Owner**, which indicates that the user is an account administrator.
5. Write down the name of this user.

If the owner who you identified is not available or has left the company, find one or more other users with
the administrator role. Consider who might have been assigned the role, for example, a manager, team lead, or someone who works directly with {{site.data.keyword.cloud_notm}} customers.

To locate a user with an administrator role, click on the name link and review the information on
the **Access policies** tab. Look for the following values:

  * Role: Administrator
  * Access Type: Service
  * Policy Details: All VMware Solutions resources

## Assigning access
{: #iam_verify_permissions-assign-access}
{: troubleshoot}

After you find the account owner or another user with an administrator role, that person must perform the following steps to assign access:
{: tsResolve}

1. Log in to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com) as the {{site.data.keyword.cloud_notm}} account owner.
2. On the upper right corner, select the **IBM Cloud account** you want to use.
3. Click **Manage** > **Access (IAM)** > **Users**.
4. Click the **Access policies** tab. Then, click **Assign access**.
5. On the Choose Access page, click **Assign access to resources**.
6. On the Assign resources access page, select:
  * VMware Solutions from the Services choice list.
  * All regions for the Region choice list.
  * All service instances for the Service instance choice list. If needed, you can select a specific instance, which you can change later.
  * The appropriate role, as needed.
7. Click **Save credentials**.

## Related links
{: #iam_verify_permissions-related}

* [What is {{site.data.keyword.cloud_notm}} Identity and Access Management?](/docs/iam?topic=iam-iamoverview)
* [Managing access to resources](/docs/iam?topic=iam-iammanidaccser)
