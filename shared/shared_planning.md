---

copyright:

  years:  2020, 2021

lastupdated: "2021-12-02"

keywords: planning VMware Solutions Shared, data center, VMware Solutions Shared data centers

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Requirements and planning for VMware Solutions Shared
{: #shared_planning}

Review the following requirements before you order your {{site.data.keyword.cloud}} for VMware® Solutions Shared virtual data centers. Plan for your order by considering the {{site.data.keyword.cloud_notm}} data center location, your workload capacity requirements, and services requirements.

## IBM Cloud account requirements
{: #shared_ordering-account-req}

To order VMware Solutions Shared, you must have a **Pay As You Go** or **Subscription** {{site.data.keyword.cloud_notm}} account. The cost of the resources that are ordered is billed to that {{site.data.keyword.cloud_notm}} account.

## Virtual data center name requirements
{: #shared_ordering-vdc-name-req}

The virtual data center name must meet the following requirements:

* Maximum length is 128 characters.
* Only alphanumeric, dash (-), and underscore (_) characters are allowed.
* The name must be unique from active virtual data centers within your account. You can create a virtual data center that has the same name as a previously deleted virtual data center.

## IBM Cloud data center availability
{: #shared_planning-dc-availability}

The VMware Solutions Shared deployment has strict requirements on the physical infrastructure. Therefore, you can deploy your virtual data centers only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements.

### Regions available for deployment
{: #shared-planning-dc-singlezone}

The following {{site.data.keyword.cloud_notm}} data centers are available for VMware Solutions Shared deployment.

| {{site.data.keyword.cloud_notm}} data centers | Region | vSAN support | Multizone support |
|:----------|----------|:-------|:-------|
| Dallas 10 | NA South | None | Yes |
| Dallas 12 | NA South | None | Yes |
| Dallas 13 | NA South | vSAN | No |
| Frankfurt 02 | Europe | None | No |
| Frankfurt 04 | Europe | None | No |
| Frankfurt 05 | Europe | None | No |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for deployment" caption-side="top"}

## Services for VMware Solutions Shared
{: #shared_planning-addon-services}

The following preinstalled services are available for your virtual data center based on your needs.
* [Managing Veeam for VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_veeam)
* [Managing Zerto for VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-portal)

Service charges are incurred only if you choose to use the service.
{: note}

## Related links
{: #shared_planning-related}

* [Ordering virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [Viewing and managing virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-summary)
* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){: external}
