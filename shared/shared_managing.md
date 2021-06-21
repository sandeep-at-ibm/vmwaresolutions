---

copyright:

  years:  2020, 2021

lastupdated: "2021-06-03"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Viewing and managing virtual data centers
{: #shared_managing}

View the summary and detailed information of the {{site.data.keyword.cloud}} for VMware® Solutions Shared virtual data center and set the **admin** password to access the vCloud Director Management console.

## Procedure to view the virtual data center summary
{: #shared_managing-viewing}

To view a summary of all the VMware Solutions Shared virtual data centers that are provisioned for a user account, complete the following steps:

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. From the console banner, click your user account icon, and then click the **Account** field to select the user account where you want to view virtual data centers.  
3. In the **VMware Solutions Shared** table, view the list of virtual data centers that are provisioned in the selected user account.

| Item | Description |
|:---- |:----------- |
| Name | The name of the virtual data center. |
| Type | The type of the virtual data center. |
| Location | The {{site.data.keyword.cloud_notm}} data center where the virtual data center is hosted. |  
| Creation time | The date and time when the virtual data center was created. |
| Status | The status of the virtual data center. |
{: caption="Table 1. Virtual data center summary" caption-side="top"}

The virtual data center can have different statuses.

| Status | Description |
|:------ |:----------- |
| Creating | The virtual data center is being created. |
| Ready to use | The virtual data center is ready to use. |
| Modifying | The virtual data center is being modified. |
| Deleting | The virtual data center is being deleted. |
{: caption="Table 2. Status descriptions for virtual data centers" caption-side="top"}

## Procedure to view virtual data center details
{: #shared_managing-procedure-view-vdc-details}

The virtual data center details include property, operating system, resource reservation, private network endpoint, and recommended services that are enabled or available for the virtual data center.

Use the following steps to view the property details of a virtual data center.

1. In the **VMware Solutions Shared** table, click an virtual data center name.
2. Under **Properties**, view the details for the virtual data center.

| Property        | Description       |
|:------------- |:------------- |
| Name | The name of the virtual data center. |
| Type | The virtual data center type. |
| Region | The {{site.data.keyword.cloud_notm}} data center region where your organization is created and the organization password is maintained. |
| Location | The {{site.data.keyword.cloud_notm}} data center where the virtual data center is hosted. |
| ID | The ID of the virtual data center. |
| Creation time | The date and time when the virtual data center was created, which is also when billing starts. |
| Red Hat activation key | The activation key that you use to register the Red Hat virtual machine (VM). |
| Public IP | Every virtual data center comes with five public IP addresses that can be used to connect virtual applications (vApps) and VMs to the internet. |
{: caption="Table 3. Virtual data center property details" caption-side="top"}

You can open an {{site.data.keyword.cloud_notm}} Support ticket to request five additional public IP addresses or an entire subnet for your virtual data center. Include the following details in your support ticket:

* Virtual data center region and location
* Organization ID
* Virtual data center name
* Number of additional IPs required

For more information about opening a support ticket, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).

To view virtual data center resource reservation details:

Under **Resource Reservation**, view the total reserved virtual CPU (vCPU) and RAM for the virtual data center.

| Resource        | Description       |
|:------------- |:------------- |
| vCPU limit | The limit or reserved amount of vCPU that can be used at any time by the virtual data center.  |
| RAM limit | The limit or reserved amount of memory that can be used at any time by the virtual data center.  |
{: caption="Table 4. Virtual data center resource reservation details" caption-side="top"}

To view virtual data center private network endpoint details:

For information about private network endpoint details, see [Procedure to view a private network endpoint for virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_creatingendpoints#shared_creatingendpoints-view-procedure).

To view virtual data center recommended services details:

For more information about recommended services details, see [Managing Veeam for VMware Solutions Shared virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_veeam) and [Managing Zerto for VMware Solutions Shared virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto).

## Procedure to access the vCloud Director Management console
{: #shared_managing-accessing}

Use the vCloud Director Management console to manage the virtual data center. You can access the vCloud Director console from the virtual data center details page.

The first time that you access the vCloud Director console for the virtual data center region, you must set the **admin** credentials to generate an initial, complex, and random password. After the first **admin** password is generated, the **vCloud Director console** option is enabled on the virtual data center details page.

You do not need to generate an **admin** password for each virtual data center. Reuse the same password for all virtual data centers in the same region.

{{site.data.keyword.vmwaresolutions_short}} does not store the **admin** password. After a password is generated, you must capture it. If the password is lost or you get locked out of your account, you can generate a new password at any time.
{:note}

1. From the **Properties** pane on the virtual data center details page, click **Set Organization Admin Password** to generate a random password.
2. On the upper right of the virtual data center details page, click **vCloud Director console** to access the console.
3. Use the ** admin** username and password to log in to the vCloud Director console.

After the **admin** is logged in to the vCloud Director console, you can create additional users who have roles that allow them to access the vCloud Director console.

All virtual data centers in the same region have the same **admin** password. Resetting the password on a virtual data center resets the **admin** password for accessing the vCloud Director Management console for all virtual data centers in the same region.
{:important}

## Related links
{: #shared_managing-related}

* [Resizing virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_resize)
* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [Deleting VMware Solutions Shared virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_deletinginstance)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
