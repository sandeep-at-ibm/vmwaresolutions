---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: planning vSphere, data center, vSphere data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requirements and planning for VMware vSphere on IBM Cloud
{: #vs_planning}

Review the following requirements before you order VMware vSphere on {{site.data.keyword.cloud}}. Plan your VMware vSphere clusters based on the {{site.data.keyword.CloudDataCent_notm}} location and your workload capacity requirements.

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

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region |
|:----------------------|:---------|:---------------|
| AMS03 | Amsterdam | Europe |
| CHE01 | Chennai | Asia-Pacific |
| DAL09 | Dallas | NA South |
| DAL10 | Dallas | NA South |
| DAL12 | Dallas | NA South |
| DAL13 | Dallas | NA South |
| FRA02 | Frankfurt | Europe |
| FRA04 | Frankfurt | Europe |
| FRA05 | Frankfurt | Europe |
| HKG02 | Hong Kong | Asia-Pacific |
| LON02 | London | Europe |
| LON04 | London | Europe |
| LON05 | London | Europe |
| LON06 | London | Europe |
| MEL01 | Melbourne | Asia-Pacific |
| MEX01 | Queretaro | NA South |
| MIL01 | Milan | Europe |
| MON01 | Montreal | NA East |
| OSL01 | Oslo | Europe |
| PAR01 | Paris | Europe |
| SAO01 | Sao Paulo | South America |
| SEO01 | Seoul | Asia-Pacific |
| SJC03 | San Jose | NA West |
| SJC04 | San Jose | NA West |
| SNG01 | Singapore | Asia-Pacific |
| SYD01 | Sydney | Asia-Pacific |
| SYD04 | Sydney | Asia-Pacific |
| TOK02 | Tokyo | Asia-Pacific |
| TOK04 | Tokyo | Asia-Pacific |
| TOR01 | Toronto | NA East |
| WDC04 | Washington, DC | NA East |
| WDC06 | Washington, DC | NA East |
| WDC07 | Washington, DC | NA East |
{: caption="Table 1. Available {{site.data.keyword.CloudDataCents_notm}} for vSphere clusters" caption-side="top"}

## Related links
{: #vs_planning-related}

* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Scaling existing clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Scaling existing clusters created outside of the console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
