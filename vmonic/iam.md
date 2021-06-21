---

copyright:

  years:  2016, 2021

lastupdated: "2021-06-10"

keywords: IAM user, user role, user permission

subcollection: vmwaresolutions


---

# Managing access for VMware Solutions
{: #iam}

Access to {{site.data.keyword.cloud}} for VMware® Solutions service instances for the users in your account is controlled by {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Every user that accesses the {{site.data.keyword.vmwaresolutions_short}} services in your account must be assigned an access policy with an IAM user role defined.

The access policy determines the actions that the user can take within the context of the service or the instance that you select. The allowable actions are customized and defined by the {{site.data.keyword.cloud_notm}} service as operations that can be applied to the service. The actions are then mapped to IAM user roles.

Policies enable access to be granted at different levels. Some of the options include the following accesses:

* Access across all service instances in your account
* Access to an individual service instance in your account
* Access to a specific resource within an instance
* Access to all IAM-enabled services in your account

After you define the scope of the access policy, you assign a role.

Review the following information, which outlines the actions that each role allows within the {{site.data.keyword.vmwaresolutions_short}} service.

## Platform management roles and permissions for IBM Cloud for VMware Solutions
{: #iam-roles}

Platform management roles enable users to complete tasks on service resources at the platform level. For example, assign user access to the service, create or delete service IDs, create instances, and bind instances to applications.

The following table provides information about the actions that are mapped to platform management roles for {{site.data.keyword.vmwaresolutions_short}}.

| Platform management role | Actions | Example actions |
|:----------------- |:----------------- |:----------------- |
| Viewer | Read-only actions | View the summary of instances<br>View the details of an instance |
| Editor | Update a specific instance | Add or remove VMware ESXi™ servers<br>Add or remove clusters<br>Add or remove services<br>Upgrade an instance to a higher version |
| Operator | Read-only actions | List instances<br>View the details of an instance |
| Administrator | Full management access | Create new instances<br>Delete instances<br>Grant platform access to other users|
{: caption="Table 1. Platform management roles and allowed actions for {{site.data.keyword.vmwaresolutions_short}}" caption-side="top"}

For {{site.data.keyword.vmwaresolutions_short}}, the following actions exist:

| Action | Operation on service | Role |
|:------ |:-------------------- |:---- |
| `vmware-solutions.instances.create` | Create new instances | Administrator |
| `vmware-solutions.instances.delete` | Delete instances | Administrator |
| `vmware-solutions.instances.view` | List instances<br>View the detail of an instance | Viewer, Operator, Editor, and Administrator |
| `vmware-solutions.instances.update` | Add or remove ESXi servers<br>Add or remove clusters<br>Add or remove services<br>Upgrade an instance to a higher version | Editor and Administrator |
| `vmware-solutions.account.update` | Update account settings | Administrator |
{: caption="Table 2. Action descriptions and required roles" caption-side="top"}

## Platform management roles and permissions for IBM Cloud for VMware Solutions Shared
{: #iam-roles-shared}

Review the following procedures for details on assigning access roles and scope for {{site.data.keyword.vmwaresolutions_short}} Shared users.

### Assigning All Resources access
{: #iam-roles-shared-user-access-all-}

All resources access would grant users access to all service resource created in all resource groups within the account.

#### Procedure to grant user access with all resources scope for VMware Solutions Shared
{: #iam-roles-shared-user-access-all-procedure}

1. In the console, go to **Manage > Access(IAM) > Users**.
2. From the row for the user that you want to assign access, select the **Actions** menu, and click **Assign access**.
3. Select **VMware Solutions**.
4. Click **All resources**.
5. Using the following table, select any combination of roles or permissions to define the scope of access and click **Add**.
6. Click **Assign**.

| Platform management role | Actions | Example actions |
|:----------------- |:----------------- |:----------------- |
| Viewer | Read-only actions | View instances<br>View instance services |
| Operator | Read-only actions | View instances<br>View instance services |
| Editor | Update a specific instance | View instances<br>Update an instance<br>View instance services<br>Update instance services |
| Administrator | Full management access | View instances<br>Update an instance<br>Delete an instance<br>Create new instances<br>Update VDC organization password<br>Create instance services<br>Update instance services<br>Delete instance services<br>View instance services |
{: caption="Table 3. Platform management roles with all resources scope and allowed actions for VMware Solutions Shared" caption-side="top"}

To grant user permission to create new instances, you must also assign Resource Group access policies. For more information, see [Giving access to resources in resource groups](/docs/account?topic=account-rgs_manage_access) and [Ordering virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering).
{:note}

### Assigning Resource Group access
{: #iam-roles-shared-resource-group}

You can organize your account resources in customizable groupings so that you can quickly assign individual or groups of users access to more than one resource at a time. For more information, see [Managing resource groups](/docs/account?topic=account-rgs).

#### Procedure grant user access with Resource Groups scope
{: #iam-roles-shared-resource-group-procedure}

1. In the console, go to **Manage > Access(IAM) > Users**.
2. From the row for the user that you want to assign access, select the **Actions** menu, and click **Assign access**.
3. Select **VMware Solutions**.
4. Click **Resources based on selected attributes**.
5. Check **Resource Group** and select a resource group.
6. For Resource Group access, select any combination of roles or permissions to define the scope of access based on your needs. **Viewer** is selected by default. 
7. For Platform access, use the following table to select any combination of roles or permissions to define the scope of access and click **Add**.
8. Click **Assign**.

| Platform management role | Actions | Example actions |
|:----------------- |:----------------- |:----------------- |
| Viewer | Read-only actions | View instances in resource group<br>View instance services in resource group |
| Operator | Read-only actions | View instances in resource group<br>View instance services in resource group |
| Editor | Update a specific instance | View instances in resource group<br>Update an instance in resource group<br>View instance's services in resource group<br>Update instance's services in resource group |
| Administrator | Partial management access | View instances in resource group<br>Update an instance in resource group<br>Delete an instance in resource group<br>Create instance services in resource group<br>Update instance services in resource group<br>Delete instance services in resource group<br>View instance services in resource group |
{: caption="Table 4. Platform management roles with resource group scope and allowed actions for VMware Solutions Shared" caption-side="top"}

### Assigning Resource Instance access
{: #iam-roles-shared-resource-instance}

Each {{site.data.keyword.cloud_notm}} service in your account is a resource that has instances. By default, resources belong to the default resource group in your account. You can assign users an access role to a resource instance to grant permissions.

#### Procedure grant user access with VMware Instance scope
{: #iam-roles-shared-resource-instance-procedure}

1. In the console, go to **Manage > Access(IAM) > Users**.
2. From the row for the user that you want to assign access, select the **Actions** menu, and click **Assign access**.
3. Select **VMware Solutions**.
4. Click **Resources based on selected attributes**.
5. Check **VMware Instance** and select the instance. 
6. Use the following table to select any combination of roles or permissions to define the scope of access and click **Add**.
7. Click **Assign**.

| Platform management role | Actions | Example actions |
|:----------------- |:----------------- |:----------------- |
| Viewer | Read-only actions | View instances<br>View instance services |
| Operator | Read-only actions | View instance<br>View instance services |
| Editor | Update a specific instance | View instances<br>Update an instance<br>View instance services<br>Update instance services |
| Administrator | Partial management access | View instances<br>Update an instance<br>Delete an instance<br>Create instance services<br>Update instance services<br>Delete instance services<br>View instance services |
{: caption="Table 5. Platform management roles with instance scope and allowed actions for VMware Solutions Shared" caption-side="top"}

## Managing access for users
{: #iam-users}

You can add new users to the {{site.data.keyword.cloud_notm}} account so that these users can share the services and resources that are provisioned for the account. For more information, see [Inviting users to access services and resources](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount#useraccount-iamuserinv).

You can also manage the access for existing users, including modifying existing access, assigning new access, and reviewing assigned access. To manage access for users, you must be the account owner or you must have the **Administrator** platform management role. For more information, see [Managing access to resources](/docs/account?topic=account-assign-access-resources).

## Migrating existing instances to IBM Cloud accounts
{: #iam-migrate}

Because of the integration of {{site.data.keyword.vmwaresolutions_short}} with IAM, instances that are deployed in V2.5 and later releases in your {{site.data.keyword.cloud_notm}} account are automatically added to your account and are managed by IAM.

For your existing instances that were deployed in V2.4 and earlier releases, you can migrate them to specified {{site.data.keyword.cloud_notm}} accounts for IAM-enabled management. For more information, see [Migrating pre-V2.5 vCenter Server instances to IBM Cloud accounts](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addinstancetousraccount).

## Related links
{: #iam-related}

* [Setting up user access](/docs/account?topic=account-access-getstarted)
* [Inviting users to an account](/docs/account?topic=account-iamuserinv)
* [What is {{site.data.keyword.cloud_notm}} IAM](/docs/account?topic=account-iamoverview)
* [Locating an IAM account administrator](/docs/vmwaresolutions?topic=vmwaresolutions-iam_verify_permissions)
