---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-07"

keywords: user account, user permissions, VRF account

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Requirements for the IBM Cloud infrastructure account
{: #cloud-infra-acct-req}

To use {{site.data.keyword.vmwaresolutions_full}} to order instances, you must have an {{site.data.keyword.cloud_notm}} infrastructure account. The cost of the components that are ordered in your instances is billed to that {{site.data.keyword.cloud_notm}} account.

## Permissions for the IBM Cloud infrastructure account
{: #cloud-infra-acct-req-permissions}

The {{site.data.keyword.cloud_notm}} infrastructure account that you are using must have certain permissions to be able to order the components in your instances and perform operations on your behalf. The permission requirements are applicable to all types of instances and services you are ordering from the {{site.data.keyword.vmwaresolutions_short}} console.

Authorized users can verify and update the permissions for an {{site.data.keyword.cloud_notm}} infrastructure account in the {{site.data.keyword.slportal}}. For more information, see [Editing a user's customer portal permissions](/docs/customer-portal?topic=customer-portal-customerportal_accuserprof#cp_editusercpperm){:external}.

| Permission         | Details                                 |
|:------------------ |:--------------------------------------- |
| Add Server | This permission is required for the following operations: to order {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} on which VMware ESXi runs and to provision hourly virtual servers that are used for instance configuration, maintenance, and support operations. |
| Cancel Server | This permission is required to release and reclaim {{site.data.keyword.baremetal_short}} on which VMware ESXi runs. If you delete your instance, the ordered components are automatically released in the correct dependency sequence. |
| View Virtual Server Details | This permission is required to retrieve the server provisioning details, which are required for order validation and automated configuration. |
| Add Storage | This permission is required to order backup storage and shared storage for the instance. |
| Manage Storage | This permission is required to manage backup storage and shared storage for the instance. |
| Hardware Firewall | This permission is required to edit or view firewall log files and settings for the Fortinet service, if it is installed on your instance. |
| Add Compute with Public Network Port | This permission is required to order hardware and VSIs (Virtual Server Instances) with public network ports. |
| Add IP Addresses | This permission is required to order portable private subnet ranges on your behalf, which is needed to manage the virtual machines that run in a vSphere cluster. When more services are added to your instance, the portable private IP addresses are assigned to VMware ESXi servers to isolate and allocate bandwidth. |
| Add Tickets | This permission is required to open service tickets on your behalf. Tickets might be created for the following operations: to initiate restore operations and to initiate problem resolution processes automatically when issues are found. |
| Edit Tickets | This permission is required to edit the service tickets that are created on your behalf. |
| View Tickets | This permission is required to monitor the service tickets that are related to the components in your instance for {{site.data.keyword.cloud_notm}} infrastructure provisioning delays and problems. |
| View Hardware Details | This permission is required to retrieve the hardware details, which are needed for order validation and automated configuration. |
| Reboot/Control | This permission is required to power off the hardware during the hardware cancellation process when you delete an instance. |
| View Licenses | This permission is required to retrieve and validate the licenses that are used by your instance. |
| View Passwords | This permission is required to be able to administer the ordered VSIs. |
| Manage Server Monitoring | This permission is not required to place an order but it is required to retrieve and validate the monitoring status of the {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} on which the VMware ESXi servers are running in your instance. |
{: caption="Table 1. Required permissions for the {{site.data.keyword.cloud_notm}} infrastructure account" caption-side="top"}

## VRF with Service Endpoints enabled
{: #cloud-infra-acct-req-vrf-se}

Your {{site.data.keyword.cloud_notm}} infrastructure account must be a Virtual Routing and Forwarding (VRF) account. If your account is non-VRF, you must convert to a VRF account. It's also recommended to enable your VRF account for using Service Endpoints.

For more information, see:
* [Virtual routing and forwarding on {{site.data.keyword.cloud_notm}}](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Converting to VRF](/docs/infrastructure/direct-link?topic=direct-link-what-happens-during-the-account-conversion-process)
* [Enabling service endpoints](/docs/account?topic=account-vrf-service-endpoint#service-endpoint)

## Related links
{: #cloud-infra-acct-req-related}

* [Requirements for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_planning)
* [User account and settings](/docs/services/vmwaresolutions?topic=vmware-solutions-useraccount)
