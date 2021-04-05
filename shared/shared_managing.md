---

copyright:

  years:  2020, 2021

lastupdated: "2021-03-16"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Viewing and managing virtual data center instances
{: #shared_managing}

View the summary and detailed information of the {{site.data.keyword.vmwaresolutions_full}} Shared virtual data center instance and set the **admin** password to access the vCloud Director Management console.

## Procedure to view virtual data center instance summary
{: #shared_managing-viewing}

To view a summary of all the VMware® Solutions Shared virtual data center instances that are provisioned for a user account, complete the following steps:

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. From the console banner, click your user account icon, and then click the **Account** field to select the user account that you want to check instances for.  
3. In the **VMware Solutions Shared** table, view the list of instances that are provisioned in the selected user account.

| Item | Description |
|:---- |:----------- |
| Name | The name of the instance. |
| Type | The type of the virtual data center. |
| Location | The {{site.data.keyword.cloud_notm}} data center where the instance is hosted. |  
| Creation time | The date and time when the instance was created. |
| Status | The status of the instance. |
{: caption="Table 1. Virtual data center instance summary" caption-side="top"}

The instance can have different statuses.

| Status | Description |
|:------ |:----------- |
| Creating | The instance is being created. |
| Ready to use | The instance is ready to use. |
| Modifying | The instance is being modified. |
| Deleting | The instance is being deleted. |
{: caption="Table 2. Status descriptions for virtual data center instances" caption-side="top"}

## Procedure to view virtual data center instance details
{: #shared_managing-procedure-view-vdc-details}

The instance details include property, operating system, resource reservation, private network endpoint, and recommended services that are enabled or available for the instance.

Use the following steps to view the property details of an instance.

1. In the **VMware Solutions Shared** table, click an instance name.
2. Under **Properties**, view the details for the instance.

| Property        | Description       |
|:------------- |:------------- |
| Name | The name of the instance. |
| Type | The virtual data center type. |
| Region | The {{site.data.keyword.cloud_notm}} data center region where your organization is created and the organization password is maintained. |
| Location | The {{site.data.keyword.cloud_notm}} data center where the instance is hosted. |
| ID | The ID of the instance. |
| Creation time | The date and time when the instance was created, which is also when billing starts. |
| Public IP | Every virtual data center comes with five public IP addresses that can be used to connect virtual applications (vApps) and VMs to the internet. |
| Red Hat activation key | The activation key that you use to register the Red Hat virtual machine (VM). |
{: caption="Table 3. Virtual data center instance property details" caption-side="top"}

You can open an {{site.data.keyword.cloud_notm}} Support ticket to request five additional public IP addresses or an entire subnet for your virtual data center. Include the following details in your support ticket:

* Instance region and location
* Organization ID
* Virtual data center name
* Number of additional IPs required

For more information about opening a support ticket, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).

To view virtual data center instance resource reservation details:

Under **Resource Reservation**, view the total reserved virtual CPU (vCPU) and RAM for the instance.

| Resource        | Description       |
|:------------- |:------------- |
| vCPU limit | The limit or reserved amount of vCPU that can be used at any time by the virtual data center.  |
| RAM limit | The limit or reserved amount of memory that can be used at any time by the virtual data center.  |
{: caption="Table 4. Virtual data center instance resource reservation details" caption-side="top"}

To view virtual data center instance private network endpoint details:

For information about private network endpoint details, see [Procedure to view a private network endpoint for virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_creatingendpoints#shared_creatingendpoints-view-procedure).

To view virtual data center instance recommended services details:

For more information about recommended services details, see [Managing Veeam for VMware Solutions Shared instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_veeam) and [Managing Zerto for VMware Solutions Shared instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto).

## Procedure to access the vCloud Director Management console
{: #shared_managing-accessing}

Use the vCloud Director Management console to manage the virtual data center. You can access the vCloud Director console from the virtual data center details page.

The first time that you access the vCloud Director console for the virtual data center region, you must set the **admin** credentials to generate an initial, complex, and random password. After the first **admin** password is generated, the **vCloud Director console** option is enabled on the virtual data center instance details page.

You do not need to generate an **admin** password for each virtual data center. Reuse the same password for all virtual data centers in the same region.

{{site.data.keyword.vmwaresolutions_short}} does not store the **admin** password. After a password is generated, you must capture it. If the password is lost or you get locked out of your account, you can generate a new password at any time.
{:note}

1. From the **Properties** pane on the virtual data center instance details page, click **Set Organization Admin Password** to generate a random password.
2. On the upper right of the virtual data center instance details page, click **vCloud Director console** to access the console.
3. Use the ** admin** username and password to log in to the vCloud Director console.

After the **admin** is logged in to the vCloud Director console, you can create additional users who have roles that allow them to access the vCloud Director console.

All virtual data centers in the same region have the same **admin** password. Resetting the password on a virtual data center instance resets the **admin** password for accessing the vCloud Director Management console for all virtual data center instances in the same region.
{:important}

## Related links
{: #shared_managing-related}

* [Resizing virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_resize)
* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [Deleting VMware Solutions Shared instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_deletinginstance)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
