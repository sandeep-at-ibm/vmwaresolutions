---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-21"

---

# Viewing VMware Federal instances

Use this procedure to view the VMware Federal instances that you ordered and detailed information about them.

## Procedure

### Viewing the VMware Federal instance summary

To view the VMware Federal instance summary, click **Deployed Instances** from the left navigation pane. In the **vCenter Server Instances** table, view the summary about the ordered instances:

Table 1. VMware Federal instance items

| Item        | Description       |  
|:------------- |:------------- |
| Name | The name of the instance. |
| Version | The release version the instance was deployed in, or upgraded to. |  
| Location | The {{site.data.keyword.CloudDataCent}} where the instance is hosted. |  
| Creation time | The date and time that the instance was created. |  
| Status | The status of the instance. |  
| Actions | The option to delete an instance. |

The instance **Status** can have a range of options. Review the following table for each status description:

Table 2. VMware Federal data center instance status descriptions

| Status        | Description       |
|:------------- |:------------- |
| Creating | The instance is being created. |
| Building | The instance is being configured. |
| Ready to Use | The instance is ready to use. |
| Modifying | The instance is being modified. |
| Secured | The deployed instance is disconnected from an open management connection and automation.
| Failed | The creation, configuration, or modification process failed. |
| Deleting | The instance is being deleted. |
| Deletion Error | An error occurred when the instance was being deleted. |
| Deleted | The instance is deleted. |


### Viewing VMware Federal instance property details

To view the property details of an instance, click the instance on the **vCenter Server Instances** table. On the instance details page, ensure that you are on the **Summary** tab.

You can view the instance **Properties** and **Deployment History** from the summary page.

Table 3. VMware Federal instance property details

| Property        | Description       |
|:------------- |:------------- |
| ID | The ID of the instance. |
| Name | The name of the instance. |
| Location | The {{site.data.keyword.CloudDataCent_notm}} where the instance is hosted. |
| Current version |  The current version of {{site.data.keyword.vmwaresolutions_short}}. |
| vCenter version | The version of VMware vCenter Server.<br><br>**Note:** There is a slight variation between the vCenter Server version displayed on the {{site.data.keyword.vmwaresolutions_short}} console and the VMware vSphere Web Client. Both are correct. |
| NSX for vSphere | The VMware NSX for vSphere product version. |
| NSX license edition | The version and edition of the VMware NSX license. |
| DNS Root Domain | The root domain name is the DNS (Domain Name System) domain name and the Microsoft Active Directory (AD) forest root name. |
| DNC SSO Domain | The SSO domain is the vSphere Single Sign-On domain. The SSO domain name is fixed for all deployed vCenter Server instances with a value of <samp class="ph codeph">vsphere.local</samp>. |
| DNS Subdomain | The subdomain is the DNS subdomain name of the root domain name where the local vCenter Server instance host names reside. The subdomain name is in the format <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Status | The status of the instance. |

Table 4. VMware Federal instance deployment history

| Item        | Description       |  
|:------------- |:------------- |
| Date | The date and time when the instance status is changed. |
| Summary | The details of the change. |


### What to do if errors occurs

If errors occur during instance deployment or instance deletion, an {{site.data.keyword.cloud_notm}} Support ticket is created automatically on your behalf. You can click the ticket link to check its status and progress.

## What to do next

Secure the VMware Federal instance that you ordered. For more information, see [Securing VMware Federal instances](vc_fed_securinginstance.html).

<!--Manage your instances from the {{site.data.keyword.vmwaresolutions_short}} console or the VMware vSphere Web Client.

**Important**: Before you click **vCenter console** on the instance details page to go to the vSphere Web Client and start managing
your ESXi servers, you must log in to the VPN portal of the IBM Cloud data center. Hover over the **vCenter console** button and
follow the instructions to ensure that you meet all requirements and you completed the necessary steps before you access the vSphere
Web Client.

Review the following topics for information to help you complete the login instructions:

*  For the requirements and necessary steps before you access the vSphere Web Client, see [Timeout reached while connecting to
   the vSphere Web Client](../vmonic/trbl_timeout_vc_console.html).
*  For a list of access points to log in to the {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) Private Network using VPN, see [VPN Access](http://www.softlayer.com/vpn-access){:new_window}.
*  If you have problems when you deploy an OVF (Open Virtualization Format) file using the vSphere Web Client, see [Deploying an OVF file using the vSphere Web Client](../vmonic/trbl_deploy_ovf.html).-->

## Related links

* [VMware Federal on IBM Cloud overview](vc_fed_overview.html)
* [Ordering VMware Federal instances](vc_fed_orderinginstance.html)
* [Deleting VMware Federal instances](vc_fed_deletinginstance.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
