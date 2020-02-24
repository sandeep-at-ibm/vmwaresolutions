---

copyright:

  years: 2020

lastupdated: "2020-02-21"

keywords: vmware solutions shared, price for shared, pricing plan

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware Solutions Shared pricing
{: #shared_pricing}

{{site.data.keyword.vmwaresolutions_full}} Shared offers two pricing plans for creating VMware Virtual Data Centers. Virtual Data Centers incur charges for the following Virtual Data Center resource usages:

* Storage allocations with tiered pricing based on storage performance
* Virtual CPU usage
* Virtual memory usage
* Egress on public networking
* Commercial operating system licenses used
* Third-party VMware services

| Plans | Description |
|:----- |:----------- |
| VMware Solutions Shared On-demand | - The vCPU and RAM Virtual Data Center are allocated based on the demand. Resources are not preallocated and in cases of large regional demand there can be delays in availability. <br/> - The limits that are established for the amount of vCPU and RAM are maximums. <br/> - vCPU and RAM resource limits can be increased and decreased later as required. <br/> - The cost is calculated hourly and it is based on the resource usage in the Virtual Data Center. <br/> - There are no limits on the amount of storage that can be allocated and used in the Virtual Data Center. Charges are hourly based on GB of allocated storage. <br/> - There are no limits on the amount of inbound and outbound public networking. Public outbound bandwidth is charged per GB. |
| VMware Solutions Shared Reserved | - The vCPU and RAM Virtual Data Center reservations are pre-allocated and their availability is guaranteed. <br/> - vCPU and RAM resources can be increased and decreased later as required. <br/> - There are no limits on the amount of storage that can be allocated and used in the Virtual Data Center. Charges are hourly based on GB of allocated storage. <br/> - There are no limits on the amount of inbound and outbound public networking. Public outbound bandwidth is charged per GB. |
{: caption="Table 1. Pricing plans" caption-side="top"}

## Cost Breakdown
{: #shared_pricing-cost}

### Usage
{: #shared_pricing-term-usage}

Metering is for the full potential size of the resource for the time period the resource is used.

For example, an On-demand Virtual Data Center is created with a resource limit of 100 vCPU and 800 GB RAM. The data center has no VMs running on it, so there is no charge for the vCPU and RAM. If an 8 vCPU with 8 GB virtual machine (VM) is started, metering is calculated for the size of that VM. If the VM uses fewer than all the resources assigned to it, metering is applicable to the full size of the VM.

### Allocation
{: #shared_pricing-term-alloc}

Metering is applicable to the full potential size of the resource for the life of the resource.

For example, a reserved Virtual Data Center is created with a resource allocation of 100 vCPU and 800 GB RAM. There are no VMs running or created on it. Metering is applicable to 100 vCPU and 800 GB RAM.

### Monthly peak metric usage
{: #shared_pricing-term-mon-peak}

The maximum value of the metric used over a full month.

For example, a reserved Virtual Data Center is created with 100 vCPU and 800 GB RAM. Later in the month, the data center is reduced to 50 vCPU and 400 GB RAM. The monthly peak usage is 100 vCPU and 800 GB RAM.

### Hourly peak metric usage
{: #shared_pricing-term-hour-peak}

The maximum value of the metric used over an hour. For example, if 100 vCPU is used for a minute of the hour with 0 vCPU used for the other 59 mins, the hourly peak metric usage is 100 vCPU.


## VMware Shared Solutions On-Demand billing plan
{: #shared_pricing-cost-ondemand}

VMware Solutions Shared On-Demand Virtual Data Center resources are allocated as needed. Pricing is hourly based on the resource usage in the Virtual Data Center. The following metrics are part of this plan.

| Metric                                   | Frequency | Description |
|:-----------------------------------------|:------------|:------------|
| MAX_BASE_COST | Monthly | Instance cost, which includes the edge gateway with five IP addresses. |
| TOTAL_VCPU_HOURS | Hourly | The peak vCPU **usage** over the period of an hour. |
| TOTAL_RAM_GB_HOURS | Hourly | The peak memory **usage** over the period of an hour. |
| TOTAL_EGRESS_GB | Usage | The **total** outbound public traffic is charged per GB transferred over the period of an hour. This value includes public outbound traffic. |
{: caption="Table 2. VMware Shared Solutions On-Demand billing plan - General metrics" caption-side="top"}
{: summary="This table has row and column headers. The row headers identify the metric. The column headers identify the frequency and description of the metric. To find the frequency and description of a metric, locate the row, and then find the information in the corresponding column."}
{: #table1}
{: tab-title="General metrics"}
{: tab-group="VMware Shared Solutions On-Demand billing plan metrics"}
{: class="comparison-tab-table"}
{: row-headers}

| Metric                                   | Frequency | Description |
|:-----------------------------------------|:------------|:------------|
| TOTAL_STORAGE_POINT_TWO_FIVE_IOPS_GB_HOUR | Hourly | The peak storage **allocation** at the 0.25 IOPS/GB tier over the period of an hour. |
| TOTAL_STORAGE_TWO_IOPS_GB_HOURS | Hourly | The peak storage **allocation** at the two IOPS/GB tier over the period of an hour. |
| TOTAL_STORAGE_FOUR_IOPS_GB_HOURS | Hourly | The peak storage **allocation** at the four IOPS/GB tier over the period of an hour. |
| TOTAL_STORAGE_TEN_IOPS_GB_HOURS | Hourly | The peak storage **allocation** at the 10 IOPS/GB tier over the period of an hour. |
{: caption="Table 3. VMware Shared Solutions On-Demand billing plan - Storage metrics" caption-side="top"}
{: summary="This table has row and column headers. The row headers identify the metric. The column headers identify the frequency and description of the metric. To find the frequency and description of a metric, locate the row, and then find the information in the corresponding column."}
{: #table2}
{: tab-title="Storage metrics"}
{: tab-group="VMware Shared Solutions On-Demand billing plan metrics"}
{: class="comparison-tab-table"}
{: row-headers}

| Metric                                   | Frequency | Description |
|:-----------------------------------------|:------------|:------------|
| MAX_WINDOWS_LICENSES | Monthly | The peak number of Windows license **usage** based on Windows VM vCPU size. For example, if you have two Windows VMs, one VM with 16 vCPU and one VM with 8vCPU, the usage is 24 vCPU of Windows license usage. |
| TOTAL_RHEL_SMALL_LICENSES | Hourly | The peak (High Watermark) number of small RHEL licenses usage in one hour intervals. Small RHEL VMs are four cores or smaller.	|
| TOTAL_RHEL_LARGE_LICENSES | Hourly | The peak (High Watermark) number of large RHEL licenses usage in one hour intervals. Large RHEL VMs are larger than four cores. |
{: caption="Table 4. VMware Shared Solutions On-Demand billing plan - Operating system metrics" caption-side="top"}
{: summary="This table has row and column headers. The row headers identify the metric. The column headers identify the frequency and description of the metric. To find the frequency and description of a metric, locate the row, and then find the information in the corresponding column."}
{: #table3}
{: tab-title="Operating system metrics"}
{: tab-group="VMware Shared Solutions On-Demand billing plan metrics"}
{: class="comparison-tab-table"}
{: row-headers}

## VMware Shared Solutions Reserved billing plan
{: #shared_pricing-cost-reserved}

VMware Shared Solutions Reserved Virtual Data Center resources are preallocated and guaranteed. Pricing is monthly based on the allocation size of the Virtual Data Center.

| Metric                                   | Frequency | Description |
|:-----------------------------------------|:------------|:------------|
| MAX_VCPU | Monthly | The peak vCPU **allocation** for the Virtual Data Center over the period of one month. The peak vCPU metric is determined by the largest vCPU reservation value that is selected by the customer over a one month period. |
| MAX_RAM_GB | Monthly | The peak memory **allocation** for the Virtual Data Center over the period of one month. The peak vCPU metric is determined by the largest memory reservation value that is selected by the customer over a one month period. |
| TOTAL_EGRESS_GB  | Usage | The **total** outbound public traffic is charged per GB transferred over the period of one month. This value includes public outbound traffic through the Virtual Data Center ESG and public outbound hybridity traffic. |
{: caption="Table 5. VMware Shared Solutions Reserved billing plan - General metrics" caption-side="top"}
{: summary="This table has row and column headers. The row headers identify the metric. The column headers identify the frequency and description of the metric. To find the frequency and description of a metric, locate the row, and then find the information in the corresponding column."}
{: #reservedbilling-table1}
{: tab-title="General metrics"}
{: tab-group="VMware Shared Solutions Reserved billing plan metrics"}
{: class="comparison-tab-table"}
{: row-headers}

| Metric                                   | Frequency | Description |
|:-----------------------------------------|:------------|:------------|
| TOTAL_STORAGE_POINT_TWO_FIVE_IOPS_GB_HOUR | Hourly | The peak storage **allocation** at the 0.25 IOPS/GB tier over the period of an hour. |
| TOTAL_STORAGE_TWO_IOPS_GB_HOURS | Hourly | The peak storage **allocation** at the two IOPS/GB tier over the period of an hour. |
| TOTAL_STORAGE_FOUR_IOPS_GB_HOURS | Hourly | The peak storage **allocation** at the four IOPS/GB tier over the period of an hour. |
| TOTAL_STORAGE_TEN_IOPS_GB_HOURS | Hourly | The peak storage **allocation** at the 10 IOPS/GB tier over the period of an hour. |
{: caption="Table 6. VMware Shared Solutions Reserved billing plan - Storage metrics" caption-side="top"}
{: summary="This table has row and column headers. The row headers identify the metric. The column headers identify the frequency and description of the metric. To find the frequency and description of a metric, locate the row, and then find the information in the corresponding column."}
{: #reservedbilling-table2}
{: tab-title="Storage metrics"}
{: tab-group="VMware Shared Solutions Reserved billing plan metrics"}
{: class="comparison-tab-table"}
{: row-headers}

| Metric                                   | Frequency | Description |
|:-----------------------------------------|:------------|:------------|
| MAX_WINDOWS_LICENSES | Monthly | The peak number of Windows license **usage** based on Windows VM vCPU size. For example, if you have two Windows VMs, one VM with 16 vCPU and one VM with 8vCPU, the usage is 24 vCPU of Windows license usage. |
| TOTAL_RHEL_SMALL_LICENSES | Hourly | The peak (High Watermark) number of small RHEL licenses usage in one hour intervals. Small RHEL VMs are four cores or smaller.	|
| TOTAL_RHEL_LARGE_LICENSES | Hourly | The peak (High Watermark) number of large RHEL licenses usage in one hour intervals. Large RHEL VMs are larger than four cores. |
{: caption="Table 7. VMware Shared Solutions Reserved billing plan - Operating system metrics" caption-side="top"}
{: summary="This table has row and column headers. The row headers identify the metric. The column headers identify the frequency and description of the metric. To find the frequency and description of a metric, locate the row, and then find the information in the corresponding column."}
{: #reservedbilling-table3}
{: tab-title="Operating system metrics"}
{: tab-group="VMware Shared Solutions Reserved billing plan metrics"}
{: class="comparison-tab-table"}
{: row-headers}

## Licenses and fees for Veeam Availability Suite
{: #shared_pricing-veeam}

Veeam usage incurs the following On-Demand charges. You can view the charges on the **{{site.data.keyword.cloud_notm}} billing and usage** view along with the usage and charges from all other {{site.data.keyword.cloud_notm}} services.

In the **{{site.data.keyword.cloud_notm}} Usage** view, locate the **VMware Solutions** service type. Locate the **Organization** plan to find the Veeam usage across all Virtual Data Centers in that organization. The Virtual Data Center usage is located in a separate plan for either VMware Solutions Shared On-Demand or VMware Solutions Shared Reserved.

| Metric                                   | Frequency   | Description |
|:-----------------------------------------|:------------|:------------|
| Veeam_Instances_License | Monthly | Veeam license charge for every VM under backup. The monthly charge is for the highest number of VMs under backup at any time period in the month. |
| Veeam_Backup_Block_Storage_GB_Hour | Hourly | Charge per GB of block storage used for all backups. |
| Veeam_Backup_Object_Storage_GB_Hour | Hourly | Charge per GB of object storage used for all backups. |
{: caption="Table 8. Licenses and fees" caption-side="top"}

There are no additional Veeam usage charges for VMware Solutions Shared.
{:note}

Initially, all backups go to the block storage that is closest to their VM workloads. Backups that are a part of an inactive backup chain are immediately moved to Cloud Object Storage. The restore speed for these inactive backups might be impacted.

You can change how fast inactive backup chains are moved to Cloud Object Storage by opening a {{site.data.keyword.vmwaresolutions_short}} service ticket.

## Related links
{: #shared_pricing-related}

* [VMware Solutions Shared overview](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview)
* [Requirements and planning for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_planning)
* [Ordering Data Center Virtual instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_ordering)
* [Managing VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [Resizing Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_resizeinstance)
* [Operating VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_vcd-ops-guide)
* [Managing Veeam for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_veeam)
* [VMware vCloud Director](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-74C9E10D-9197-43B0-B469-126FFBCB5121.html){:external}
* [Troubleshooting NSX Edge](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.troubleshooting.doc/GUID-E6CD6FAA-3DA7-4AD7-9577-EE121AA7E1E6.html){:external}
