---

copyright:

  years:  2020

lastupdated: "2020-02-20"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Viewing and managing Virtual Data Center instances
{: #shared_managing}

View the summary and detailed information of the {{site.data.keyword.vmwaresolutions_full}} Shared Virtual Data Center instance and reset the **admin** password to access the vCloud Director Management console.

## Procedure to view Virtual Data Center instances
{: #shared_managing-viewing}

To view a summary of all the VMware Solutions Shared Virtual Data Center instances that are provisioned for a user account, complete the following steps:

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. From the console banner, click your user account icon, and then click the **Account** field to select the user account that you want to check instances for.  
3. In the **VMware Solutions Shared** table, view the list of instances that are provisioned in the selected user account.

| Item        | Description       |  
|:------------- |:------------- |
| Name | The name of the instance. |
| Type | The type of the Virtual Data Center. |
| Version | The release version that the instance was deployed in, or upgraded to. |
| Location | The {{site.data.keyword.CloudDataCent_notm}} where the instance is hosted. |  
| Creation time | The date and time when the instance was created. |
| Status | The status of the instance. |
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

## Procedure to view Virtual Data Center instance details
{: #shared_managing-procedure-view-vdc-details}

The instance details include property details, recommended services that are enabled or available for the instance, operating system details, and the total reserved vCPU and RAM.

To view the details of an instance:

1. In the **VMware Solutions Shared** table, click an instance name.
2. View the instance property, service, operating system, and resource details.

| Property        | Description       |
|:------------- |:------------- |
| Name | The name of the instance. |
| Organization name | The name of the organization. |
| Type | The Virtual Data Center type. |
| Location | The {{site.data.keyword.CloudDataCent_notm}} where the instance is hosted. |
| ID | The ID of the instance. |
| Creation time | The date and time when the instance was created, which is also when billing starts. |
| Red Hat activation key | The activation key that you use to register the Red Hat virtual machine (VM). |
| Public IP | Every Virtual Data Center comes with five public IP addresses that can be used to connect virtual applications (vApps) and VMs to the internet. |
{: caption="Table 3. Virtual Data Center instance properties" caption-side="top"}

| Resource        | Description       |
|:------------- |:------------- |
| vCPU reserved | The limit or reserved amount of CPU that can be used at any time by the Virtual Data Center.  |
| RAM | The limit or reserved amount of memory that can be used at any time by the Virtual Data Center.  |
{: caption="Table 4. Virtual Data Center instance resource reservations" caption-side="top"}

## Procedure to launch the vCloud Director Management console
{: #shared_managing-accessing}

Use the vCloud Director Management console to manage the Virtual Data Center. You can access the vCloud Director console from the Virtual Data Center details page.

The first time that you access the vCloud Director console, you must use the **admin** credentials to generate an initial, complex, and random password. After the first **admin** password is generated, the **vCloud Director console** option is enabled on the Virtual Data Center instance details page.

{{site.data.keyword.vmwaresolutions_short}} does not store the **admin** password. After a password is generated, you must capture it. If the password is lost or you get locked out of your account, you can generate a new password at any time.
{:note}

1. From the **Properties** pane on the Virtual Data Center instance details page, click **Reset location password** to generate a random password.
2. From the upper right corner of the Virtual Data Center instance details page, click **Launch vCloud Director** to access the console.
3. Use the ** admin** username and password to log in to the vCloud Director console.

All Virtual Data Centers in the same location have the same **admin** password. Resetting the password on a Virtual Data Center instance resets the **admin** password for accessing the vCloud Director Management console for all Virtual Data Center instances in the same location.
{:important}

## Related links
{: #shared_managing-related}

* [VMware Solutions Shared overview](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview)
* [Requirements and planning for VMware Solutions Shared instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_planning)
* [Ordering VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_ordering)
* [Resizing Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_resizeinstance)
* [Operating VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_vcd-ops-guide)
* [Managing Veeam for VMware Solutions Shared instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_veeam)
* [Deleting VMware Solutions Shared instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_deletinginstance)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
