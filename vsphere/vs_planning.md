---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-14"

keywords: planning vSphere, data center, vSphere data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requirements and planning for VMware vSphere
{: #vs_planning}

Review the following requirements before you order a VMware vSphere cluster. Plan your VMware vSphere clusters based on the {{site.data.keyword.CloudDataCent_notm}} location and your workload capacity requirements.

You are responsible for setting up the environment, installing, and configuring various VMware components after the ESXi servers are deployed. The following examples are VMware components: VMware vCenter Server, VMware NSX, and VMware vSAN.
{:note}

## IBM Cloud account requirements
{: #vs_planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).

## IBM Cloud Data Center availability
{: #vs_planning-dc-availability}

The vSphere deployment has strict requirements on the physical infrastructure. Therefore, you can deploy clusters only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCent_notm}} are available for vSphere deployment.

Cascade Lake {{site.data.keyword.baremetal_short}} are available on Multi-Zone Region
{{site.data.keyword.CloudDataCents_notm}}. For more information, see [Multi-Zone Region (MZR) Overview
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

If you select a vSAN component, the location list is filtered by SSD (Solid-State Disk) availability.
{:note}

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region | Server options |
|:----------------------|:---------|:---------------|:--------------|
| AMS03 | Amsterdam | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| CHE01 | Chennai | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| DAL09 | Dallas | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| DAL10 | Dallas | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| DAL12 | Dallas | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| DAL13 | Dallas | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| FRA02 | Frankfurt | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| FRA04 | Frankfurt | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| FRA05 | Frankfurt | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| HKG02 | Hong Kong | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> 
| LON02 | London | Europe | <ul><li>For vSphere 6.5u2: Skylake, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> 
| LON04 | London | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| LON05 | London | Europe | <ul><li>For vSphere 6.5u2: Skylake, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> 
| LON06 | London | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| MEL01 | Melbourne | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> 
| MEX01 | Queretaro | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> 
| MIL01 | Milan | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| MON01 | Montreal | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| OSL01 | Oslo | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> 
| PAR01 | Paris | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> 
| SAO01 | Sao Paulo | South America | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SEO01 | Seoul | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SJC03 | San Jose | NA West | <ul><li>For vSphere 6.5u2: Skylake, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SJC04 | San Jose | NA West | <ul><li>For vSphere 6.5u2: Skylake, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SNG01 | Singapore | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> 
| SYD01 | Sydney | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> 
| SYD04 | Sydney | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| SYD05 | Sydney | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified</li><li>For vSphere 6.7u2: Skylake, Cascade Lake</li></ul> |
| TOK02 | Tokyo | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| TOK04 | Tokyo | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| TOK05 | Tokyo | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| TOR01 | Toronto | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> 
| WDC04 | Washington, DC | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| WDC06 | Washington, DC | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| WDC07 | Washington, DC | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
{: caption="Table 1. Available {{site.data.keyword.CloudDataCents_notm}} for vSphere clusters" caption-side="top"}

## Related links
{: #vs_planning-related}

* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Scaling existing clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Scaling existing clusters created outside of the console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
