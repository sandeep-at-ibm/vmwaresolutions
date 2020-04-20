---

copyright:

  years:  2020

lastupdated: "2020-04-13"

keywords: planning VMware Solutions Shared, data center, VMware Solutions Shared data centers

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Requirements and planning for VMware Solutions Shared
{: #shared_planning}

Review the following requirements before you order your {{site.data.keyword.vmwaresolutions_full}} Shared virtual data center instances. Plan your instance based on the {{site.data.keyword.cloud_notm}} data center location, your workload capacity requirements, and add-on service requirements.

## IBM Cloud account requirements
{: #shared_ordering-account-req}

To order VMware Solutions Shared, you must have a **Pay As You Go** or **Subscription** {{site.data.keyword.cloud_notm}} account. The cost of the resources that are ordered is billed to that {{site.data.keyword.cloud_notm}} account.

## Virtual data center name requirements
{: #shared_ordering-vdc-name-req}

The virtual data center name must meet the following requirements:

* Maximum length is 128 characters
* Only alphanumeric, dash (-), and underscore (_) characters are allowed

## IBM Cloud data center availability
{: #shared_planning-dc-availability}

The VMware Solutions Shared deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements.

The following {{site.data.keyword.cloud_notm}} data center is available for VMware Solutions Shared deployment.

| {{site.data.keyword.cloud_notm}} data center | Location | Region |
|:----------------------|:---------|:-------|:---------------|
| DAL10 | Dallas | NA South |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data center for VMware Solutions Shared instances" caption-side="top"}

The following {{site.data.keyword.cloud_notm}} data center is offered as a Limited Availability data center for VMware Solutions Shared deployment.

| Limited Availability {{site.data.keyword.cloud_notm}} data center | Location | Region |
|:----------------------|:---------|:-------|:---------------|
| FRA04 | Frankfurt | Europe |
{: caption="Table 2.  Limited Availability {{site.data.keyword.cloud_notm}} data center for VMware Solutions Shared instances" caption-side="top"}

## Services for VMware Solutions Shared
{: #shared_planning-addon-services}

Preinstalled add-on services are available for your instance based on your needs. For more information, see [Managing Veeam for VMware Solutions Shared](/docs/vmwaresolutions?topic=vmware-solutions-shared_veeam).

Service charges are incurred only if you choose to use the service.
{:note}

## Related links
{: #shared_planning-related}

* [Ordering virtual data center instances](/docs/vmwaresolutions?topic=vmware-solutions-shared_ordering)
* [Viewing and managing virtual data center instances](/docs/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmware-solutions-shared_vcd-ops-guide)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
