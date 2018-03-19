---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

# Requirements and planning for VMware vSphere on IBM Cloud

Review the following requirements before you order VMware vSphere on {{site.data.keyword.cloud}}. Plan your VMware vSphere clusters based on the {{site.data.keyword.CloudDataCent_notm}} location and your workload capacity requirements.

**Note**: You are responsible for setting up the environment, installing, and configuring various VMware components after the ESXi servers are deployed. Such components are: VMware vCenter Server, VMware NSX, and VMware vSAN.

## IBM Cloud account requirements

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} account requirements](../vmonic/slaccountrequirement.html).

## IBM Cloud Data Center availability

The vSphere deployment has strict requirements on the physical infrastructure. Therefore, you can deploy clusters only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCent_notm}} are available for vSphere deployment.

**Note:** If you select a vSAN component, the location list is filtered by SSD availablity.

Table 1. Available {{site.data.keyword.CloudDataCent_notm}} for vSphere clusters

| IBM Cloud Data Center | Location |
|:-----|:----------------|
| AMS03 | Amsterdam |
| CHE01 | Chennai |
| DAL09 | Dallas |
| DAL10 | Dallas |
| DAL12 | Dallas |
| DAL13 | Dallas |
| FRA02 | Frankfurt |
| HKG02 | Hong Kong |
| LON02 | London |
| LON04 | London |
| LON06 | London |
| MEL01 | Melbourne |
| MEX01 | Queretaro |
| MIL01 | Milan |
| MON01 | Montreal |
| OSL01 | Oslo |
| PAR01 | Paris |
| SAO01 | Sao Paulo |
| SEO01 | Seoul |
| SJC03 | San Jose |
| SJC04 | San Jose |
| SNG01 | Singapore |
| SYD01 | Sydney |
| SYD04 | Sydney |
| TOK02 | Tokyo |
| TOR01 | Toronto |
| WDC03 | Washington, DC |
| WDC04 | Washington, DC |
| WDC06 | Washington, DC |
| WDC07 | Washington, DC |

<!--## Capacity considerations-->

<!--For capacity information and considerations, see the _Bill of
Materials_ document on the [Reference Architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page.-->

## Related links

* [Ordering new vSphere clusters](vs_orderinginstances.html)
* [Scaling existing clusters](vs_scalingexistingclusters.html)
* [Scaling existing clusters created outside of the console](vs_orderingforclustersoutside.html)
