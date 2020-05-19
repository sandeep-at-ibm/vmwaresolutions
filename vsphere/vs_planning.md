---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-17"

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

| {{site.data.keyword.cloud_notm}} data center | Location | Region | Server options |
|:----------------------|:---------|:---------------|:--------------|
| AMS03 | Amsterdam | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell |
| CHE01 | Chennai | Asia-Pacific | Skylake, SAP-certified[^sap-che01], Broadwell |
| DAL09 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| DAL10 | Dallas | NA South | Skylake, Cascade Lake, SAP-certified, Broadwell |
| DAL12 | Dallas | NA South | Skylake, Cascade Lake, SAP-certified, Broadwell |
| DAL13 | Dallas | NA South | Skylake, Cascade Lake, SAP-certified, Broadwell |
| FRA02 | Frankfurt | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell |
| FRA04 | Frankfurt | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell|
| FRA05 | Frankfurt | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell |
| HKG02 | Hong Kong | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| LON02 | London | Europe | Skylake, Cascade Lake, Broadwell |
| LON04 | London | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell |
| LON05 | London | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell |
| LON06 | London | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell |
| MEX01 | Queretaro | NA South | Skylake, SAP-certified[^sap-mex01], Broadwell |
| MIL01 | Milan | Europe | Skylake, SAP-certified[^sap-mil01], Broadwell |
| MON01 | Montreal | NA East | Skylake, Cascade Lake, SAP-certified[^sap-mon01], Broadwell |
| OSL01 | Oslo | Europe | Skylake, SAP-certified[^sap-osl01], Broadwell |
| PAR01 | Paris | Europe | Skylake, Cascade Lake, SAP-certified[^sap-par01], Broadwell |
| SAO01 | Sao Paulo | South America | Skylake, SAP-certified, Broadwell |
| SEO01 | Seoul | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| SJC03 | San Jose | NA West | Skylake, Broadwell |
| SJC04 | San Jose | NA West | Skylake, Broadwell |
| SNG01 | Singapore | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| SYD01 | Sydney | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell |
| SYD04 | Sydney | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell |
| SYD05 | Sydney | Asia-Pacific | Skylake, Cascade Lake, SAP-certified |
| TOK02 | Tokyo | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell |
| TOK04 | Tokyo | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell |
| TOK05 | Tokyo | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell |
| TOR01 | Toronto | NA East | Skylake, SAP-certified, Broadwell |
| WDC04 | Washington, DC | NA East | Skylake, Cascade Lake, SAP-certified, Broadwell |
| WDC06 | Washington, DC | NA East | Skylake, Cascade Lake, SAP-certified, Broadwell |
| WDC07 | Washington, DC | NA East | Skylake, Cascade Lake, SAP-certified, Broadwell |
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
