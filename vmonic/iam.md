---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-02"

keywords: IAM user, user role, user permission

subcollection: vmware-solutions


---

# Managing user access with Identity and Access Management
{: #iam}

Access to {{site.data.keyword.vmwaresolutions_full}} service instances for the users in your account is controlled by {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Every user that accesses the {{site.data.keyword.vmwaresolutions_short}} services in your account must be assigned an access policy with an IAM user role defined.

The access policy determines the actions that the user can take within the context of the service or the instance that you select. The allowable actions are customized and defined by the {{site.data.keyword.cloud_notm}} service as operations that can be applied to the service. The actions are then mapped to IAM user roles.

Policies enable access to be granted at different levels. Some of the options include the following accesses:

* Access across all service instances in your account
* Access to an individual service instance in your account
* Access to a specific resource within an instance
* Access to all IAM-enabled services in your account

After you define the scope of the access policy, you assign a role.

Review the following information, which outlines the actions that each role allows within the {{site.data.keyword.vmwaresolutions_short}} service.

## Platform management roles and permissions
{: #iam-roles}

Platform management roles enable users to complete tasks on service resources at the platform level. For example, assign user access to the service, create or delete service IDs, create instances, and bind instances to applications.

The following table provides information about the actions that are mapped to platform management roles.

| Platform management role | Actions | Example actions |
|:----------------- |:----------------- |:----------------- |
| Viewer | Read-only actions | View the summary of instances<br>View the details of an instance |
| Editor | Update a specific instance | Add or remove ESXi servers<br>Add or remove clusters<br>Add or remove services<br>Upgrade an instance to a higher version |
| Operator | Read-only actions | List instances<br>View the details of an instance |
| Administrator | Full management access | Create new instances<br>Delete instances<br>Grant platform access to other users|
{: caption="Table 1. Platform management roles and allowed actions" caption-side="top"}

For {{site.data.keyword.vmwaresolutions_short}}, the following actions exist:

| Action | Operation on service | Role |
|:------ |:-------------------- |:---- |
| `vmware-solutions.instances.create` | Create new instances | Administrator |
| `vmware-solutions.instances.delete` | Delete instances | Administrator |
| `vmware-solutions.instances.view` | List instances<br>View the detail of an instance | Viewer, Operator, Editor, and Administrator |
| `vmware-solutions.instances.update` | Add or remove ESXi servers<br>Add or remove clusters<br>Add or remove services<br>Upgrade an instance to a higher version | Editor and Administrator |
| `vmware-solutions.account.update` | Update account settings | Administrator |
{: caption="Table 2. Action descriptions and required roles" caption-side="top"}

## Managing access for users
{: #iam-users}

You can add new users to the {{site.data.keyword.cloud_notm}} account so that these users can share the services and resources that are provisioned for the account. For more information, see [Inviting users to access services and resources](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite).

You can also manage the access for existing users, including modifying existing access, assigning new access, and reviewing assigned access. To manage access for users, you must be the account owner or you must have the **Administrator** platform management role. For more information, see [Managing access to resources](/docs/iam?topic=iam-iammanidaccser).

## Migrating existing instances to IBM Cloud accounts
{: #iam-migrate}

Because of the integration of {{site.data.keyword.vmwaresolutions_short}} with IAM, instances that are deployed in V2.5 and later releases in your {{site.data.keyword.cloud_notm}} account are automatically added to your account and are managed by IAM.

For your existing instances that were deployed in V2.4 and earlier releases, you can migrate them to specified {{site.data.keyword.cloud_notm}} accounts for IAM-enabled management. For more information, see [Migrating pre-V2.5 vCenter Server instances to IBM Cloud accounts](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount).

## Related links
{: #iam-related}

* [Getting started with IAM tutorial](/docs/iam?topic=iam-getstarted)
* [Inviting users to an account](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [What is IBM Cloud Identity and Access Management?](/docs/iam?topic=iam-iamoverview)
* [Locating an IAM account administrator](/docs/services/vmwaresolutions?topic=vmware-solutions-iam_verify_permissions)
