---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Requirements and planning for Cloud Foundation instances

Review the following requirements before you order your VMware Cloud Foundation instances. Plan your instance based on the {{site.data.keyword.CloudDataCent}} location, your workload capacity requirements, and additional service requirements.

## IBM Cloud account requirements

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](../vmonic/slaccountrequirement.html).

## IBM Cloud Data Center availability

The Cloud Foundation deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCents_notm}} are available for Cloud Foundation deployment:

Table 1. Available {{site.data.keyword.CloudDataCents_notm}} and {{site.data.keyword.cloud_notm}} Bare Metal Server configurations for Cloud Foundation instances

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region | Server configurations |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europe | Customized |
| CHE01 | Chennai | Asia Pacific | Customized |
| DAL09 | Dallas | NA South | Customized |
| DAL10 | Dallas | NA South | Customized, Small, Large |
| DAL12 | Dallas | NA South | Customized |
| DAL13 | Dallas | NA South | Customized |
| FRA02 | Frankfurt | Europe | Customized, Large |
| FRA04 | Frankfurt | Europe | Customized |
| HKG02 | Hong Kong | Asia Pacific | Customized |
| LON02 | London | Europe | Customized |
| LON04 | London | Europe | Customized |
| LON06 | London | Europe | Customized, Small, Large |
| MEL01 | Melbourne | Asia Pacific | Customized |
| MEX01 | Queretaro | NA South | Customized |
| MIL01 | Milan | Europe | Customized |
| MON01 | Montreal | NA East | Customized |
| OSL01 | Oslo | Europe | Customized |
| PAR01 | Paris | Europe | Customized |
| SAO01 | Sao Paulo | South America | Customized |
| SEO01 | Seoul | Asia Pacific | Customized |
| SJC03 | San Jose | NA West | Customized |
| SJC04 | San Jose | NA West | Customized |
| SNG01 | Singapore | Asia Pacific | Customized |
| SYD01 | Sydney | Asia Pacific | Customized |
| SYD04 | Sydney | Asia Pacific | Customized |
| TOK02 | Tokyo | Asia Pacific | Customized |
| TOR01 | Toronto | NA East | Customized, Small, Large |
| WDC04 | Washington, DC | NA East | Customized, Small, Large |
| WDC06 | Washington, DC | NA East | Customized |
| WDC07 | Washington, DC | NA East | Customized |

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

Table 2. Status indicators for {{site.data.keyword.CloudDataCents_notm}} when ordering Cloud Foundation instances

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.CloudDataCent_notm}} is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.CloudDataCent_notm}} has no availability at this time. |
| Limited Inventory             | The {{site.data.keyword.CloudDataCent_notm}} has limited availability and the order might not be completed. |

## Backup of management components

You are responsible for maintaining and ensuring the availability of all instance components. It is strongly recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](../archiref/solution/solution_backingup.html).

## Services for Cloud Foundation instances

You can order add-on services for your instance base on your needs, for example, disaster recovery. For more information, see [Ordering, viewing, and removing services for Cloud Foundation instances](sd_addingremovingservices.html).

## Capacity considerations

For capacity information and considerations, see [Scaling capacity](../archiref/solution/solution_scaling.html).

### Related links

* [Cloud Foundation overview](sd_cloudfoundationoverview.html)
* [Ordering Cloud Foundation instances](sd_orderinginstance.html)
* [Expanding and contracting capacity for Cloud Foundation instances](sd_addingremovingservers.html)
* [Ordering, viewing, and removing services for Cloud Foundation instances](sd_addingremovingservices.html)
