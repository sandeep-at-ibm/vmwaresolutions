---

copyright:

  years:  2021

lastupdated: "2021-03-29"

keywords: planning vcs Security and Compliance Readiness Bundle, data centers for Security and Compliance Readiness Bundle, services for security and compliance bundle, vcs scb

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}

# Requirements and planning for Security and Compliance Readiness Bundle
{: #scb-planning}

Review the following requirements before you order your Security and Compliance Readiness Bundle instance. Plan your instance based on the {{site.data.keyword.cloud}} data center location, your workload capacity requirements, and services requirements.

## IBM Cloud account requirements
{: #scb-planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## IBM Cloud data center availability
{: #scb-planning-dc-availability}

The Security and Compliance Readiness Bundle deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements. The following {{site.data.keyword.cloud_notm}} data centers are available for Security and Compliance Readiness Bundle deployment.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:----------------------|:-------|
| Amsterdam 03 | Europe |
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
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for Security and Compliance Readiness Bundle" caption-side="top"}

## Services for Security and Compliance Readiness Bundle
{: #scb-planning-addon-services}

The following services are required for Security and Compliance Readiness Bundle instances.
* [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* [KMIP™ for VMware®](https://cloud.ibm.com/infrastructure/vmware-solutions/console/servicestandalonenew/KMIPAdapter)

The following services are included with Security and Compliance Readiness Bundle instances.
* [Caveonix RiskForesight™](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations)
* [HyTrust® CloudControl™](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [vRealize Operations™ and Log Insight™](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview)

The following services are recommended for Security and Compliance Readiness Bundle instances.
* [Veeam® 11](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Juniper® vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview)

The following services are optional for Security and Compliance Readiness Bundle instances.
* [VMware HCX™](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)
* [Red Hat® OpenShift® for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_ordering)

## Related links
{: #scb-planning-related}

* [Security and Compliance Readiness Bundle overview](/docs/vmwaresolutions?topic=vmwaresolutions-scb-overview)
* [Ordering Security and Compliance Readiness Bundle instances](/docs/vmwaresolutions?topic=vmwaresolutions-scb-orderinginstance)
* [Viewing and deleting Security and Compliance Readiness Bundle instances](/docs/vmwaresolutions?topic=vmwaresolutions-scb-view-delete-instance)
