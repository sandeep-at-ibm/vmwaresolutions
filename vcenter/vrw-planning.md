---

copyright:

  years:  2021

lastupdated: "2021-11-16"

keywords: planning vmware regulated workloads, data center vmware regulated workloads, vmware regulated workloads data centers

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Requirements and planning for VMware Regulated Workloads
{: #vrw-planning}

Review the following requirements before you order your VMware® Regulated Workloads instance. Plan your instance based on the {{site.data.keyword.cloud}} data center location, your capacity requirements, and services requirements.

## IBM Cloud account requirements
{: #vrw-planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## IBM Cloud data center availability
{: #vrw-planning-dc-availability}

The VMware Regulated Workloads deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements.

### Data centers available for single-zone deployment
{: #vrw-planning-dc-single-zone}

The following {{site.data.keyword.cloud_notm}} data centers are available for VMware Regulated Workloads single-zone deployment.

| Region | {{site.data.keyword.cloud_notm}} data center | Pod |
|:----------|:------------|:-------|
| South America | Sao Paulo 01 | 01 |
| South America | Sao Paulo 04 | 01 |
| South America | Sao Paulo 05 | 01 |
| NA South | Dallas 09 | 01-06 |
| NA South | Dallas 10 | 01-04 |
| NA South | Dallas 12 | 01-02 |
| NA South | Dallas 13 | 01-03 |
| NA South | Mexico 01 | 01 |
| Asia-Pacific |Chennai 01 | 01 |
| Asia-Pacific | Hong Kong 02 | 02 |
| Asia-Pacific | Osaka 21 | 01 |
| Asia-Pacific | Osaka 22 | 01 |
| Asia-Pacific | Osaka 23 | 01 |
| Asia-Pacific | Seoul 01 | 01 |
| Asia-Pacific | Singapore 01| 02 |
| Asia-Pacific | Sydney 01 | 01-02 |
| Asia-Pacific | Sydney 04 | 01 |
| Asia-Pacific | Sydney 05 | 01 |
| Asia-Pacific | Tokyo 02 | 01-02 |
| Asia-Pacific | Tokyo 04 | 01 |
| Asia-Pacific | Tokyo 05 | 01 |
| Europe | Amsterdam 03 | 01-02 |
| Europe | Frankfurt 02 | 01-03 |
| Europe | Frankfurt 04 | 01 |
| Europe | Frankfurt 05 | 01 |
| Europe | London 02 | 01-02 |
| Europe | London 04 | 01 |
| Europe | London 05 | 01 |
| Europe | London 06 | 01 |
| Europe | Milan 01 | 01 |
| Europe | Paris 01 | 01 |
| NA East | Montreal 01 | 01-02 |
| NA East | Toronto 01 | 01-02 |
| NA East | Toronto 04 | 01 |
| NA East | Toronto 05 | 01 |
| NA East | Washington DC 04 | 01-05 |
| NA East | Washington DC 06 | 01 |
| NA East | Washington DC 07 | 01 |
| NA West | San Jose 03 | 01-02 |
| NA West | San Jose 04 | 01 |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for VMware Regulated Workloads single-zone deployment" caption-side="top"}

### Regions available for multizone deployment
{: #vrw-planning-reg-multizone}

The following regions are available for VMware Regulated Workloads multizone deployment.

| {{site.data.keyword.cloud_notm}} data centers | Mutizone region |
|:----------------------|:-------|
| Dallas, Sao Paulo, Toronto, and Washington DC | Americas |
| Frankfurt and London | Europe |
| Sydney, Tokyo, and Osaka | Asia Pacific |
{: caption="Table 2. Available regions for VMware Regulated Workloads multizone deployment" caption-side="top"}

## Services for VMware Regulated Workloads
{: #vrw-planning-addon-services}

The following services are required for the VMware Regulated Workloads:
* [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* [KMIP for VMware](https://cloud.ibm.com/infrastructure/vmware-solutions/console/servicestandalonenew/KMIPAdapter)
* [Direct Link Dedicated](https://cloud.ibm.com/interconnectivity/direct-link)

The following services are included with VMware Regulated Workloads:
* [Veeam 11](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview). This service is included when you choose **Edge services cluster with Juniper vSRX**. It is available for single-zone and multizone instances.
* [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview)

The following services are optional for VMware Regulated Workloads and are available to single-zone VMware instances only:
* [VMware HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)
* [F5 BIG-IP](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations)

## Related links
{: #vrw-planning-related}

* [VMware Regulated Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-overview)
* [Ordering VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-orderinginstance)
* [Viewing and deleting VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-view-delete-instance)
* [VMware Regulated Workloads reference architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-archi-overview)
