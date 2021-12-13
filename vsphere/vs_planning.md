---

copyright:

  years:  2016, 2021

lastupdated: "2021-11-22"

keywords: planning vSphere, data center, vSphere data centers

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Requirements and planning for VMware vSphere
{: #vs_planning}

Review the following requirements before you order a VMware vSphere® cluster. Plan your VMware vSphere clusters based on the {{site.data.keyword.cloud}} data center location and your workload capacity requirements.

You are responsible for setting up the environment, installing, and configuring various VMware components after the VMware ESXi™ servers are deployed. The following examples are VMware components: VMware vCenter Server®, VMware NSX®, and VMware vSAN™.
{: note}

## IBM Cloud account requirements
{: #vs_planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## IBM Cloud data center availability
{: #vs_planning-dc-availability}

The vSphere deployment has strict requirements on the physical infrastructure. Therefore, you can deploy clusters only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements. The following {{site.data.keyword.cloud_notm}} data centers are available for vSphere deployment.

Cascade Lake bare metal servers are available in [multizone region](#x9774820){: term}
{{site.data.keyword.cloud_notm}} data centers. For more information, see [Multizone region (MZR) overview](/docs/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

If you select a vSAN component, the location list is filtered by SSD (Solid-State Disk) availability.
{: note}

| Region | {{site.data.keyword.cloud_notm}} data center | Pod | Server options[^vsphere-7] |
|:-----------|:----------|:---------------|:--------------|
| South America | Sao Paulo 01 | 01 | Skylake, Cascade Lake, SAP-certified |
| South America | Sao Paulo 04 | 01 | Cascade Lake, SAP-certified |
| South America | Sao Paulo 05 | 01 | Cascade Lake, SAP-certified |
| NA South | Dallas 09 | 01-06 | Skylake, Cascade Lake, SAP-certified |
| NA South | Dallas 10 | 01-04 | Skylake, Cascade Lake, SAP-certified |
| NA South | Dallas 12 | 01-02 | Skylake, Cascade Lake, SAP-certified |
| NA South | Dallas 13 | 01-03 | Skylake, Cascade Lake, SAP-certified |
| NA South | Mexico 01 | 01 | Skylake, Cascade Lake, SAP-certified[^sap-mex01] |
| Asia-Pacific | Chennai 01 | 01 | Skylake, Cascade Lake, SAP-certified[^sap-che01] |
| Asia-Pacific | Hong Kong 02 | 02 | Skylake, Cascade Lake, SAP-certified |
| Asia-Pacific | Osaka 21 | 01 | Cascade Lake, SAP-certified |
| Asia-Pacific | Osaka 22 | 01 | Cascade Lake, SAP-certified |
| Asia-Pacific | Osaka 23 | 01 | Cascade Lake, SAP-certified |
| Asia-Pacific | Seoul 01 | 01 | Skylake, Cascade Lake, SAP-certified |
| Asia-Pacific | Singapore 01 | 02 | Skylake, Cascade Lake, SAP-certified |
| Asia-Pacific | Sydney 01 | 01-02 | Skylake, Cascade Lake, SAP-certified |
| Asia-Pacific | Sydney 04 | 01 | Skylake, Cascade Lake, SAP-certified |
| Asia-Pacific | Sydney 05 | 01 | Skylake, Cascade Lake, SAP-certified |
| Asia-Pacific | Tokyo 02 | 01-02 | Skylake, Cascade Lake, SAP-certified |
| Asia-Pacific | Tokyo 04 | 01 | Skylake, Cascade Lake, SAP-certified |
| Asia-Pacific | Tokyo 05 | 01 | Skylake, Cascade Lake, SAP-certified |
| Europe | Amsterdam 03 | 01-02 | Skylake, Cascade Lake, SAP-certified |
| Europe | Frankfurt 02 | 01-03 | Skylake, Cascade Lake, SAP-certified |
| Europe | Frankfurt 04 | 01 | Skylake, Cascade Lake, SAP-certified|
| Europe | Frankfurt 05 | 01 | Skylake, Cascade Lake, SAP-certified |
| Europe | London 02 | 01-02 | Skylake, Cascade Lake, SAP-certified |
| Europe | London 04 | 01 | Skylake, Cascade Lake, SAP-certified |
| Europe | London 05 | 01 | Skylake, Cascade Lake, SAP-certified |
| Europe | London 06 | 01 | Skylake, Cascade Lake, SAP-certified |
| Europe | Milan 01  | 01 | Skylake, Cascade Lake, SAP-certified[^sap-mil01] |
| Europe | Paris 01 | 01 | Skylake, Cascade Lake, SAP-certified[^sap-par01] |
| NA East | Montreal 01 | 01-02 | Skylake, Cascade Lake, SAP-certified[^sap-mon01] |
| NA East | Toronto 01 | 01-02 | Skylake, Cascade Lake, SAP-certified |
| NA East | Toronto 04 | 01 | Cascade Lake |
| NA East | Toronto 05 | 01 | Cascade Lake |
| NA East | Washington DC 04 | 01-05 | Skylake, Cascade Lake, SAP-certified |
| NA East | Washington DC 06 | 01 | Skylake, Cascade Lake, SAP-certified |
| NA East | Washington DC 07 | 01 | Skylake, Cascade Lake, SAP-certified |
| NA West | San Jose 03 |  | Skylake, Cascade Lake, SAP-certified |
| NA West | San Jose 04 |  | Skylake, Cascade Lake, SAP-certified |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for vSphere clusters" caption-side="top"}

[^vsphere-7]: Skylake is not supported for vSphere 7 instances

[^sap-che01]: Existing vSphere 6.5 clusters only

[^sap-mex01]: Existing vSphere 6.5 clusters only

[^sap-mil01]: Existing vSphere 6.5 clusters only

[^sap-mon01]: Existing vSphere 6.5 clusters only

[^sap-par01]: Existing vSphere 6.5 clusters only

## Related links
{: #vs_planning-related}

* [Ordering new vSphere clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderinginstances)
* [Scaling existing clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_scalingexistingclusters)
* [Scaling existing clusters created outside of the console](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderingforclustersoutside)
