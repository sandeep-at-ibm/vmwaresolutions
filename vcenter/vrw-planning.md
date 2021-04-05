---

copyright:

  years:  2021

lastupdated: "2021-03-21"

keywords: planning regulated workloads, data center for workloads, vmware workloads data centers

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}

# Requirements and planning for VMware Regulated Workloads
{: #vrw-planning}

Review the following requirements before you order your VMware Regulated Workloads instance. Plan your instance based on the {{site.data.keyword.cloud}} data center location, your workload capacity requirements, and services requirements.

## IBM Cloud account requirements
{: #vrw-planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## IBM Cloud data center availability
{: #vrw-planning-dc-availability}

The VMware Regulated Workloads deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements. The following {{site.data.keyword.cloud_notm}} data centers are available for VMware Regulated Workloads deployment.

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
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for VMware Regulated Workloads" caption-side="top"}

## Services for VMware Regulated Workloads
{: #vrw-planning-addon-services}

The following services are required for the VMware Regulated Workloads:
* [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* [Direct Link Dedicated](https://cloud.ibm.com/interconnectivity/direct-link)
* [KMIP™ for VMware®](https://cloud.ibm.com/infrastructure/vmware-solutions/console/servicestandalonenew/KMIPAdapter)

The following services are included with VMware Regulated Workloads:
* [Veeam® 11](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Caveonix RiskForesight™](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations)
* [HyTrust® CloudControl™](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [Juniper® vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview) (for **Edge services cluster with Juniper vSRX**)
* [vRealize Operations™ and Log Insight™](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview)

VMware HCX™ is an optional service for VMware Regulated Workloads. For more information, see [Planning for VMware HCX](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning#vc_planning-addon-services-hcx).

## Related links
{: #vrw-planning-related}

* [VMware Regulated Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-overview)
* [Ordering VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-orderinginstance)
* [Viewing and deleting VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-view-delete-instance)
* [VMware Regulated Workloads reference architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-archi-overview)
