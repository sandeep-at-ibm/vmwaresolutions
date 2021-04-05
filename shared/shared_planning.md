---

copyright:

  years:  2020, 2021

lastupdated: "2021-03-21"

keywords: planning VMware Solutions Shared, data center, VMware Solutions Shared data centers

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Requirements and planning for VMware Solutions Shared
{: #shared_planning}

Review the following requirements before you order your {{site.data.keyword.vmwaresolutions_full}} Shared virtual data center instances. Plan your instance based on the {{site.data.keyword.cloud_notm}} data center location, your workload capacity requirements, and services requirements.

## IBM Cloud account requirements
{: #shared_ordering-account-req}

To order VMware® Solutions Shared, you must have a **Pay As You Go** or **Subscription** {{site.data.keyword.cloud_notm}} account. The cost of the resources that are ordered is billed to that {{site.data.keyword.cloud_notm}} account.

## Virtual data center name requirements
{: #shared_ordering-vdc-name-req}

The virtual data center name must meet the following requirements:

* Maximum length is 128 characters.
* Only alphanumeric, dash (-), and underscore (_) characters are allowed.
* The name must be unique from active virtual data centers within your account. You can create a virtual data center that has the same name as a previously deleted virtual data center.

## IBM Cloud data center availability
{: #shared_planning-dc-availability}

The VMware Solutions Shared deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements.

The following {{site.data.keyword.cloud_notm}} data centers are available for VMware Solutions Shared deployment.

| {{site.data.keyword.cloud_notm}} data centers | Region |
|:----------------------|:-------|
| Dallas 10 | NA South |
| Dallas 12 | NA South |
| Dallas 13 | NA South |
| Frankfurt 04 | Europe |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for VMware Solutions Shared instances" caption-side="top"}

## Services for VMware Solutions Shared
{: #shared_planning-addon-services}

The following preinstalled services are available for your instance based on your needs.
* [Managing Veeam for VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_veeam)
* [Managing Zerto for VMware Solutions Shared instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto)

Service charges are incurred only if you choose to use the service.
{:note}

## Related links
{: #shared_planning-related}

* [Ordering virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [Viewing and managing virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_managing)
* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
