---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-07"

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

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions?topic=vmware-solutions-cloud-infra-acct-req).

## IBM Cloud Data Center availability
{: #vs_planning-dc-availability}

The vSphere deployment has strict requirements on the physical infrastructure. Therefore, you can deploy clusters only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCent_notm}} are available for vSphere deployment.

Cascade Lake {{site.data.keyword.baremetal_short}} are available on Multi-Zone Region
{{site.data.keyword.CloudDataCents_notm}}. For more information, see [Multi-Zone Region (MZR) Overview](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

If you select a vSAN component, the location list is filtered by SSD (Solid-State Disk) availability.
{:note}

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region | Server options |
|:----------------------|:---------|:---------------|:--------------|
| AMS03 | Amsterdam | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| CHE01 | Chennai | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| DAL09 | Dallas | NA South | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| DAL10 | Dallas | NA South | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| DAL12 | Dallas | NA South | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| DAL13 | Dallas | NA South | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| FRA02 | Frankfurt | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| FRA04 | Frankfurt | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| FRA05 | Frankfurt | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| HKG02 | Hong Kong | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| LON02 | London | Europe | For vSphere 6.5u3: Skylake, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| LON04 | London | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| LON05 | London | Europe | For vSphere 6.5u3: Skylake, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| LON06 | London | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| MEL01 | Melbourne | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| MEX01 | Queretaro | NA South | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| MIL01 | Milan | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| MON01 | Montreal | NA East | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| OSL01 | Oslo | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| PAR01 | Paris | Europe | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| SAO01 | Sao Paulo | South America | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| SEO01 | Seoul | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| SJC03 | San Jose | NA West | For vSphere 6.5u3: Skylake, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| SJC04 | San Jose | NA West | For vSphere 6.5u3: Skylake, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| SNG01 | Singapore | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| SYD01 | Sydney | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| SYD04 | Sydney | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| SYD05 | Sydney | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified<br><br>For vSphere 6.7u2: Skylake, Cascade Lake |
| TOK02 | Tokyo | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| TOK04 | Tokyo | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| TOK05 | Tokyo | Asia-Pacific | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| TOR01 | Toronto | NA East | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Broadwell |
| WDC04 | Washington, DC | NA East | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| WDC06 | Washington, DC | NA East | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
| WDC07 | Washington, DC | NA East | For vSphere 6.5u3: Skylake, SAP-certified, Broadwell<br><br>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell |
{: caption="Table 1. Available {{site.data.keyword.CloudDataCents_notm}} for vSphere clusters" caption-side="top"}

## Related links
{: #vs_planning-related}

* [Ordering new vSphere clusters](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances)
* [Scaling existing clusters](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_scalingexistingclusters)
* [Scaling existing clusters created outside of the console](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderingforclustersoutside)
