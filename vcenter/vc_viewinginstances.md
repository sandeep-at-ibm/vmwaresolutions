---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-07"

keywords: view vCenter Server, view instance, view instance details

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Viewing vCenter Server instances
{: #vc_viewinginstances}

View the summary and detailed information of the VMware vCenter Server instances that are provisioned for different user accounts.

## Procedure to view the vCenter Server instances summary
{: #vc_viewinginstances-procedure-view-inst-summary}

To view a summary of all the vCenter Server instances that are provisioned for a user account, complete the following steps:

1. In the {{site.data.keyword.vmwaresolutions_full}} console, click **Resources** from the left navigation pane.
2. From the console banner, click your user account icon, and then click the **Account** field to select the user account that you want to check instances for.  
3. In the **vCenter Server Instances** table, view the list of instances that are provisioned in the selected user account.

| Item        | Description       |  
|:------------- |:------------- |
| Name | The name of the instance. |
| Type | The type of vCenter Server instance. |
| Version | The release version that the instance was deployed in, or upgraded to. |  
| Location | The {{site.data.keyword.cloud_notm}} data center where the instance is hosted. |  
| Creation time | The date and time when the instance was created. |
| Status | The status of the instance. |   
{: caption="Table 1. vCenter Server instance items" caption-side="top"}

The instance can have a range of statuses.

| Status        | Description       |
|:------------- |:------------- |
| Creating | The instance is being created. |
| Building | The instance is being configured. |
| Ready to Use | The instance is ready to use. |
| Modifying | The instance is being modified. |
| Failed | The creation, configuration, or modification process failed. |
| Deleting | The instance is being deleted. |
| Deletion Error | An error occurred when the instance was being deleted. |
| Deleted | The instance is deleted. |
{: caption="Table 2. vCenter Server instances status descriptions" caption-side="top"}

## Procedure to view the vCenter Server instance property details
{: #vc_viewinginstances-procedure-view-inst-property}

To view the property details of an instance:

1. In the **vCenter Server Instances** table, click an instance name.
2. Under **Properties**, view the details for the instance.

| Property        | Description       |
|:------------- |:------------- |
| Name | The name of the instance. |
| ID | The ID of the instance. |
| Location | The {{site.data.keyword.cloud_notm}} data center where the instance is hosted.<br><br>**Note:** IBM Cloud for VMware Mission Critical Workloads list locations for each cluster type. |
| Current version | The current version of {{site.data.keyword.vmwaresolutions_short}}. |
| vCenter version | The VMware vCenter Server version.<br><br>**Note:** There is a slight variation between the vCenter Server version that is displayed on the {{site.data.keyword.vmwaresolutions_short}} console and the VMware vSphere Web Client. Both are correct. |
| NSX for vSphere | The VMware NSX for vSphere product version. |
| _VMware component_ license | If you selected to use your own VMware license for any of the VMware components on the **Licensing** page when you ordered the instance, the VMware component name and the license key that you entered for the component are displayed.<br><br>Examples of VMware component licenses can include: **NSX License**, **vCenter Server License**, and **vSAN License**. |
| NSX license edition | The version and edition of the VMware NSX license. |
| DNS (Domain Name System), Root Domain | The root domain name is the DNS domain name and the Microsoft Active Directory (AD) forest root name. |
| DNS, SSO Domain | The SSO domain is the vSphere Single Sign-On domain. The SSO domain name is fixed for all deployed vCenter Server instances with a value of <samp class="ph codeph">vsphere.local</samp>. |
| DNS, Subdomain | The subdomain is the DNS subdomain name of the root domain name where the local vCenter Server instance hostnames reside. The subdomain name is in the format <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Status  | The status of the instance.<br><br>The information that is displayed provides an update on the progress of the deployment or the action that is taken on the instance. If there are issues, a message might be displayed to help you investigate and resolve the problem. |
{: caption="Table 3. vCenter Server instance properties" caption-side="top"}

## Procedure to view the access information for vCenter Server instances
{: #vc_viewinginstances-procedure-view-access-info}

Under **Access Information**, view the access information for the instance-related components. The passwords that are displayed are initial passwords that are generated by the system. If you change them outside of the {{site.data.keyword.vmwaresolutions_short}} console, they are not updated on the instance summary page.

| Component        | Description       |
|:------------- |:------------- |
| AD/DNS IPs | The IP addresses of the two AD servers. |
| AD/DNS FQDNs | The AD/DNS server fully qualified domain names.<br><br>**Note:** The same administrator password can be used to connect to all the AD/DNS servers by using a remote desktop connection. |
| AD/DNS ADMIN (Remote Desktop)  | For primary instances, it displays the username and password to access the AD server through a remote desktop connection.<br><br>For secondary instances, click the **View on primary instance** link to be directed to the username and password information on the primary instance.<br><br>**Note:** After the secondary instance is added to the primary DNS domain and replication occurs, the local administrator password on the primary instance might overwrite the local administrator password on the secondary instance. By clicking the **View on primary instance** link, you receive access to the correct administrator password.  
| NSX Manager IP  | The IP address of the NSX Manager.  |
| NSX Manager FQDN  | The NSX Manager fully qualified domain name (FQDN).  |
| NSX Manager HTTP  | The username and password that is used to access the NSX Manager web console. |
| vCenter IP  | The IP address of the vCenter Server.  |
| vCenter FQDN  | The vCenter Server fully qualified domain name (FQDN).  |
| vCenter ADMIN  | The VMware vCenter Single Sign-On username and password that you can use to log in to the vCenter Server by using the vSphere Web Client.  |
| vCenter SSH  | The username and password that you can use to access the vCenter Server VM through SSH connection.  |
{: caption="Table 4. vCenter Server access information for instance-related components" caption-side="top"}

## Procedure to view the deployment history for vCenter Server instances
{: #vc_viewinginstances-procedure-view-deploy-history}

Click **Deployment History** from the left navigation pane to view the deployment history for the instance.

| Item        | Description       |  
|:------------- |:------------- |
| Date | The date and time when the instance status is changed. |
| Summary | The details of the change. |
{: caption="Table 5. vCenter Server instance deployment history" caption-side="top"}

## What to do if errors occur
{: #vc_viewinginstances-if-errors-occur}

If errors occur during instance deployment or instance deletion, the {{site.data.keyword.cloud_notm}} Support team is automatically notified. To inquire about the status of your ticket, you can [contact IBM Support](/docs/vmwaresolutions?topic=vmware-solutions-trbl_support).

## What to do next
{: #vc_viewinginstances-next}

Manage your instances from the {{site.data.keyword.vmwaresolutions_short}} console or the VMware vSphere Web Client.

Before you click **vCenter console** on the instance summary page to go to the vSphere Web Client and start managing your ESXi servers, you must log in to the VPN portal of the {{site.data.keyword.cloud_notm}} data center. Hover over **vCenter console** and follow the instructions to ensure that you meet all requirements and you completed the necessary steps before you access the vSphere Web Client.
{:important}

Review the following topics for information to help you complete the login instructions:
*  For the requirements and necessary steps before you access the vSphere Web Client, see [Timeout reached while connecting to the vSphere Web Client](/docs/vmwaresolutions?topic=vmware-solutions-trbl_timeout_vc_console).
*  For a list of access points to log in to the {{site.data.keyword.cloud_notm}} infrastructure Private Network by using VPN, see [VPN Access](https://www.ibm.com/cloud/vpn-access){:external}.
*  If you have problems when you deploy an OVF (Open Virtualization Format) file by using the vSphere Web Client, see [Deploying an OVF file using the vSphere Web Client](/docs/vmwaresolutions?topic=vmware-solutions-trbl_deploy_ovf).

## Related links
{: #vc_viewinginstances-related}

* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Adding, viewing, and deleting clusters for vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers)
* [Deleting vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_deletinginstance)
