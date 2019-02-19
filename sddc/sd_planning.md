---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Requirements and planning for Cloud Foundation instances
{: #sd_planning}

Review the following requirements before you order your VMware Cloud Foundation instances. Plan your instance based on the {{site.data.keyword.CloudDataCent}} location, your workload capacity requirements, and service requirements.

## IBM Cloud account requirements
{: #sd_planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## IBM Cloud Data Center availability
{: #sd_planning-dc-availability}

The Cloud Foundation deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCents_notm}} are available for Cloud Foundation deployment:

Table 1. Available {{site.data.keyword.CloudDataCents_notm}} and {{site.data.keyword.cloud_notm}} Bare Metal Server configurations for Cloud Foundation instances

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region | Server configurations |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europe | Skylake, Broadwell |
| CHE01 | Chennai | Asia-Pacific | Skylake, Broadwell |
| DAL09 | Dallas | NA South | Skylake, Broadwell |
| DAL10 | Dallas | NA South | Skylake, Broadwell |
| DAL12 | Dallas | NA South | Skylake, Broadwell |
| DAL13 | Dallas | NA South | Skylake, Broadwell |
| FRA02 | Frankfurt | Europe | Skylake, Broadwell |
| FRA04 | Frankfurt | Europe | Skylake, Broadwell |
| HKG02 | Hong Kong | Asia-Pacific | Skylake, Broadwell |
| LON02 | London | Europe | Skylake, Broadwell |
| LON04 | London | Europe | Skylake, Broadwell |
| LON06 | London | Europe | Skylake, Broadwell |
| MEL01 | Melbourne | Asia-Pacific | Skylake, Broadwell |
| MEX01 | Queretaro | NA South | Skylake, Broadwell |
| MIL01 | Milan | Europe | Skylake, Broadwell |
| MON01 | Montreal | NA East | Skylake, Broadwell |
| OSL01 | Oslo | Europe | Skylake, Broadwell |
| PAR01 | Paris | Europe | Skylake, Broadwell |
| SAO01 | Sao Paulo | South America | Skylake, Broadwell |
| SEO01 | Seoul | Asia-Pacific | Skylake, Broadwell |
| SJC03 | San Jose | NA West | Skylake, Broadwell |
| SJC04 | San Jose | NA West | Skylake, Broadwell |
| SNG01 | Singapore | Asia-Pacific | Skylake, Broadwell |
| SYD01 | Sydney | Asia-Pacific | Skylake, Broadwell |
| SYD04 | Sydney | Asia-Pacific | Skylake, Broadwell |
| TOK02 | Tokyo | Asia-Pacific | Skylake, Broadwell |
| TOR01 | Toronto | NA East | Skylake, Broadwell |
| WDC04 | Washington, DC | NA East | Skylake, Broadwell |
| WDC06 | Washington, DC | NA East | Skylake, Broadwell |
| WDC07 | Washington, DC | NA East | Skylake, Broadwell |

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

Table 2. Status indicators for {{site.data.keyword.CloudDataCents_notm}} when you order Cloud Foundation instances

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.CloudDataCent_notm}} is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.CloudDataCent_notm}} has no availability currently. |
| Limited Inventory             | The {{site.data.keyword.CloudDataCent_notm}} has limited availability and the order might not be completed. |

## Backup of management components
{: #sd_planning-backup-mgmt-components}

You are responsible for maintaining and ensuring the availability of all instance components. It is recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services for Cloud Foundation instances
{: #sd_planning-addon-services}

You can order add-on services for your instance base on your needs, for example, disaster recovery. For more information, see [Ordering, viewing, and removing services for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices).

## Capacity considerations
{: #sd_planning-capacity-considerations}

For more information about capacity, see [Scaling capacity](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Related links
{: #sd_planning-related}

* [Cloud Foundation overview](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
* [Ordering Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Expanding and contracting capacity for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Ordering, viewing, and removing services for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)
