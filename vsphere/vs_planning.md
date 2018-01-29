---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# Requirements and planning for VMware vSphere on IBM Cloud

Review the following requirements before you order VMware vSphere on IBM Cloud. Plan your VMware vSphere clusters based on the IBM Cloud data center location and your workload capacity requirements.

**Note**: You are responsible for setting up the environment, installing, and configuring various VMware components after the ESXi servers are deployed. Such components are: VMware vCenter Server, VMware NSX, and VMware vSAN.

## IBM Cloud account requirements

The {{site.data.keyword.cloud}} account that you are using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} account requirements](../vmonic/slaccountrequirement.html).

## Data centers availability

The vSphere deployment has strict requirements on the physical infrastructure. Therefore, you can deploy clusters only in IBM® Cloud data centers that meet the requirements. The following data centers are available for vSphere deployment.

**Note:** If you select a vSAN component, the location list is filtered by SSD availablity.

Table 1. Available data centers for vSphere clusters

| Data center | Location |
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
| WDC04 | Washington, DC |
| WDC06 | Washington, DC |
| WDC07 | Washington, DC |

<!--## Capacity considerations-->

<!--For capacity information and considerations, see the _Bill of
Materials_ document in the [Architecture Center](https://www.ibm.com/devops/method/content/architecture/virtVCenterServerPlatform){:new_window}.-->

## Related links

* [Ordering new vSphere clusters](vs_orderinginstances.html)
* [Scaling existing clusters](vs_scalingexistingclusters.html)
* [Scaling existing clusters created outside of the console](vs_orderingforclustersoutside.html)
