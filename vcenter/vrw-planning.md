---

copyright:

  years:  2021

lastupdated: "2021-02-01"

keywords: planning regulated workloads, data center for workloads, vmware workloads data centers

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}

# Requirements and planning for regulated workloads
{: #vrw-planning}

Review the following requirements before you order your regulated workloads instance. Plan your instance based on the {{site.data.keyword.cloud}} data center location, your workload capacity requirements, and add-on service requirements.

## IBM Cloud account requirements
{: #vrw-planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## IBM Cloud data center availability
{: #vrw-planning-dc-availability}

The regulated workloads deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements. The following {{site.data.keyword.cloud_notm}} data centers are available for regulated workloads deployment.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:----------------------|:-------|
| Amsterdam 03 | Europe |
| Chennai 01 | Asia-Pacific |
| Dallas 09 | NA South |
| Dallas 10 | NA South |
| Dallas 12 | NA South |
| Dallas 13 | NA South |
| Frankfurt 02 | Europe |
| Frankfurt 04 | Europe |
| Frankfurt 05 | Europe |
| Hong Kong 02 | Asia-Pacific |
| London 02 | Europe |
| London 04 | Europe |
| London 05 | Europe |
| London 06 | Europe |
| Mexico 01 | NA South |
| Milan 01 | Europe |
| Montreal 01 | NA East |
| Osaka 21 | Asia-Pacific |
| Osaka 22 | Asia-Pacific |
| Osaka 23 | Asia-Pacific |
| Paris 01 | Europe |
| Sao Paulo 01 | South America |
| Seoul 01 | Asia-Pacific |
| San Jose 03 | NA West |
| San Jose 04 | NA West |
| Singapore 01| Asia-Pacific |
| Sydney 01 | Asia-Pacific |
| Sydney 04 | Asia-Pacific |
| Sydney 05 | Asia-Pacific |
| Tokyo 02 | Asia-Pacific |
| Tokyo 04 | Asia-Pacific |
| Tokyo 05 | Asia-Pacific |
| Toronto 01 | NA East |
| Toronto 04 | NA East |
| Toronto 05 | NA East |
| Washington DC 04 | NA East |
| Washington DC 06 | NA East |
| Washington DC 07 | NA East |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for regulated workloads" caption-side="top"}

Depending on availability and inventory supply, {{site.data.keyword.cloud_notm}} data centers might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.cloud_notm}} data center is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.cloud_notm}} data center has no availability currently. |
| Limited Inventory             | The {{site.data.keyword.cloud_notm}} data center has limited availability and the order might not be completed. |
{: caption="Table 2. Status indicators for {{site.data.keyword.cloud_notm}} data centers when you order vCenter Server instances" caption-side="top"}

## Services for regulated workloads
{: #vrw-planning-addon-services}

The following services are required for the regulated workloads:
* [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* [Direct Link Dedicated](https://cloud.ibm.com/interconnectivity/direct-link)
* [KMIP™ for VMware®](https://cloud.ibm.com/infrastructure/vmware-solutions/console/servicestandalonenew/KMIPAdapter)

The following services are included with regulated workloads:
* [Veeam® 10](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Caveonix RiskForesight™](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations)
* [HyTrust® CloudControl™](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [Juniper® vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview) (for **Edge services cluster with Juniper vSRX**)
* [vRealize Operations™ and Log Insight™](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview)

VMware HCX™ is an optional service for regulated workloads. For more information, see [Planning for VMware HCX](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning#vc_planning-addon-services-hcx).

## Related links
{: #vrw-planning-related}

* [Regulated workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-overview)
* [Ordering regulated workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-orderinginstance)
* [Viewing and deleting regulated workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-view-delete-instance)
* [VMware regulated workloads reference architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-archi-overview)
