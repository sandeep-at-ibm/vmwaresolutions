---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-08"

keywords: planning vSphere, data center, vSphere data centers

subcollection: vmwaresolutions

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requirements and planning for VMware vSphere
{: #vs_planning}

Review the following requirements before you order a VMware vSphere cluster. Plan your VMware vSphere clusters based on the {{site.data.keyword.cloud}} data center location and your workload capacity requirements.

You are responsible for setting up the environment, installing, and configuring various VMware components after the ESXi servers are deployed. The following examples are VMware components: VMware vCenter Server, VMware NSX, and VMware vSAN.
{:note}

## IBM Cloud account requirements
{: #vs_planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## IBM Cloud data center availability
{: #vs_planning-dc-availability}

The vSphere deployment has strict requirements on the physical infrastructure. Therefore, you can deploy clusters only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements. The following {{site.data.keyword.cloud_notm}} data centers are available for vSphere deployment.

Cascade Lake bare metal servers are available on Multi-Zone Region
{{site.data.keyword.cloud_notm}} data centers. For more information, see [Multi-Zone Region (MZR) Overview](/docs/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

If you select a vSAN component, the location list is filtered by SSD (Solid-State Disk) availability.
{:note}

| {{site.data.keyword.cloud_notm}} data center | Region | Server options |
|:---------------------|:---------------|:--------------|
| Amsterdam 03 | Europe | Skylake, Cascade Lake, SAP-certified |
| Chennai 01 | Asia-Pacific | Skylake, SAP-certified[^sap-che01] |
| Dallas 09 | NA South | Skylake, SAP-certified |
| Dallas 10 | NA South | Skylake, Cascade Lake, SAP-certified |
| Dallas 12 | NA South | Skylake, Cascade Lake, SAP-certified |
| Dallas 13 | NA South | Skylake, Cascade Lake, SAP-certified |
| Frankfurt 02 | Europe | Skylake, Cascade Lake, SAP-certified |
| Frankfurt 04 | Europe | Skylake, Cascade Lake, SAP-certified|
| Frankfurt 05 | Europe | Skylake, Cascade Lake, SAP-certified |
| Hong Kong 02 | Asia-Pacific | Skylake, SAP-certified |
| London 02 | Europe | Skylake, Cascade Lake |
| London 04 | Europe | Skylake, Cascade Lake, SAP-certified |
| London 05 | Europe | Skylake, Cascade Lake, SAP-certified |
| London 06 | Europe | Skylake, Cascade Lake, SAP-certified |
| Mexico 01 | NA South | Skylake, SAP-certified[^sap-mex01] |
| Milan 01  | Europe | Skylake, SAP-certified[^sap-mil01] |
| Montreal 01 | NA East | Skylake, Cascade Lake, SAP-certified[^sap-mon01] |
| Oslo 01 | Europe | Skylake, SAP-certified[^sap-osl01] |
| Paris 01| Europe | Skylake, Cascade Lake, SAP-certified[^sap-par01] |
| Sao Paulo 01 | South America | Skylake, SAP-certified |
| Seoul 01 | Asia-Pacific | Skylake, SAP-certified |
| San Jose 03 | NA West | Skylake |
| San Jose 04 | NA West | Skylake |
| Singapore 01 | Asia-Pacific | Skylake, SAP-certified |
| Sydney 01 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified |
| Sydney 04 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified |
| Sydney 05 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified |
| Tokyo 02 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified |
| Tokyo 04 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified |
| Tokyo 05 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified |
| Toronto 01 | NA East | Skylake, SAP-certified |
| Washington DC 04 | NA East | Skylake, Cascade Lake, SAP-certified |
| Washington DC 06 | NA East | Skylake, Cascade Lake, SAP-certified |
| Washington DC 07 | NA East | Skylake, Cascade Lake, SAP-certified |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for vSphere clusters" caption-side="top"}

[^sap-che01]: vSphere 6.5 only

[^sap-mex01]: vSphere 6.5 only

[^sap-mil01]: vSphere 6.5 only

[^sap-mon01]: vSphere 6.5 only

[^sap-osl01]: vSphere 6.5 only

[^sap-par01]: vSphere 6.5 only

## Related links
{: #vs_planning-related}

* [Ordering new vSphere clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderinginstances)
* [Scaling existing clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_scalingexistingclusters)
* [Scaling existing clusters created outside of the console](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderingforclustersoutside)
