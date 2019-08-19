---

copyright:

  years:  2019

lastupdated: "2019-08-08"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing Shared resources
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} Shared is provided as an experimental offering and is intended for IBM users only.
{:note}

You can manage the lifecycle of virtual data centers by using the {{site.data.keyword.vmwaresolutions_short}} Shared offering.

By using the {{site.data.keyword.vmwaresolutions_short}} Shared offering, you acknowledge that you have read and agreed to the following conditions:
* Only IBM users will have access to the ordered instances.
* No licenses will be used with Windows Catalog images.
* No Red Hat Enterprise Linux virtual machines will be added to the environment.

The following functions are supported, either by using the web UI or the public API:
- View Virtual Data Center instances
- Access the vCloud Management Console
- Resize Virtual Data Center instances
- Delete Virtual Data Center instances
- Adding and removing VMware Services to and from Virtual Data Center instances (**Future**)

## Viewing Virtual Data Center instances
{: #shared_managing-viewing}

To view a summary of all the Virtual Data Center instances that are provisioned for a user account, complete the following steps:

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. From the console banner, click your user account icon, and then click the **Account** field to select the user account that you want to check instances for.  
3. In the **IBM Cloud VMware Solutions Shared** table, view the list of instances that are provisioned in the selected user account.

| Item        | Description       |  
|:------------- |:------------- |
| Name | The name of the instance |
| Allocation Model | The type of the virtual data center |
| Location | The {{site.data.keyword.CloudDataCent_notm}} where the instance is hosted |  
| Creation time | The date and time when the instance was created |
| Status | The status of the instance |
{: caption="Table 1. Virtual Data Center instance items" caption-side="top"}

The instance can have a range of statuses.

| Status        | Description       |
|:------------- |:------------- |
| Creating | The instance is being created. |
| Ready to Use | The instance is ready to use. |
| Modifying | The instance is being modified. |
| Deleting | The instance is being deleted. |
| Deleted | The instance is deleted. |
{: caption="Table 2. Status descriptions for Virtual Data Center instances" caption-side="top"}

## Procedure to view the Virtual Data Center details
{: #vc_viewinginstances-procedure-view-vdc-details}

To view the property details of an instance:

1. In the **IBM Cloud VMware Solutions Shared** table, click an instance name.
2. Under **Properties**, view the details for the instance.

| Property        | Description       |
|:------------- |:------------- |
| Name | The name of the instance. |
| Allocation Model | The virtual data center type. |
| Location | The {{site.data.keyword.CloudDataCent_notm}} where the instance is hosted. |
| ID | The ID of the instance. |
| Creation Time | The date and time when the instance was created, which is also when billing starts. |
| vCPU Limit | The limit or reserved amount of CPU that can be used at any time by the virtual data center.  |
| RAM Limit | The limit or reserved amount of memory that can be used at any time by the virtual data center.  |
| Public IP | Every virtual data center comes with five public IP addresses that can be used to connect virtual applications (vApps) and virtual machines (VMs) to the internet. |
{: caption="Table 3. Virtual Data Center properties" caption-side="top"}

## Accessing the vCloud Director Management Console
{: #shared_managing-accessing}

Manage the virtual data center through the vCloud Director Management Console.

The first access to the vCloud Director Management Console is done by using the **admin** credential. Generate a password in the Virtual Data Center details page with the **Get Location Password** link. This action generates an initial complex random password, which can be reset at any time.

The {{site.data.keyword.vmwaresolutions_short}} offering does not store the **admin** password. After a password is generated, you must capture it. If the password is lost, a new password should be generated.

All virtual data centers in the same location have the same **admin** password. Resetting the password on a Virtual Data Center instance resets the **admin** password for accessing the vCloud Director Management Console for all Virtual Data Center instances in the same location.

After the first **admin** password is generated, the **Management Portal** button becomes available in the upper right corner of the details page. Click **Management Portal** to access the vCloud Director Management Console. To log in, use the user name **admin** and the password that is obtained with the **Get Location Password** link.

## Resizing Virtual Data Center instances
{: #shared_managing-resizing}

At any time when a Virtual Data Center instance is in the **Ready To Use** state, you can change the amount of resources that are assigned to a virtual data center.

Resize the vCPU or RAM resources for a Virtual Data Center instance in the Virtual Data Center details page. Click the pencil icon next to **Resources** on the details page and change the values of the vCPU or RAM properties.

Lastly, verify the configuration and estimated cost before you place the order.

  The configuration change fails if the vCPU and RAM resources are in use while being lowered, because the Virtual Data Center resources cannot be lowered to a level less than the currently active resource usage.
  {:note}

The Virtual Data Center instance enters in the **Modifying** state while the change is being made. When the resources are ready to use, the status is changed to **Ready to Use**.

## Deleting Virtual Data Center instances
{: #shared_managing-deleting}

### Before you delete Virtual Data Center instances
{: #shared_managing-delete-before}

A Virtual Data Center instance can be deleted when it's in the **Ready To Use** state.

Before you delete your Virtual Data Center instance, ensure that any items that you created within the instance are removed. Such items might include the following artifacts:
* vApps, vApp templates, and VMs (even if they are stopped)
* Organization networks removed or unshared from the instance
* Organization catalogs
* DHCP pools created within the Organization Virtual Data Center edge gateway

### Procedure to delete Virtual Data Center instances
{: #shared_managing-delete-proc}

Perform the delete operation from the Virtual Data Center details page or from the {{site.data.keyword.vmwaresolutions_short}} Shared Resource table:
* From the details page, click the **Delete** icon in the overflow menu option on the far upper right of the details page. Then, confirm that you want to delete the instance.
* From the {{site.data.keyword.vmwaresolutions_short}} Shared Resource table, locate the instance that you want to delete and click the **Delete** icon in the **Actions** column. Then, confirm that you want to delete the instance.

## Related links
{: #shared_managing-related}

* [Overview of {{site.data.keyword.vmwaresolutions_short}} Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Ordering Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Ordering Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
