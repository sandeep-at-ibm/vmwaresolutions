---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-13"

subcollection: vmwaresolutions

---

# Partially distributed
{: #caveonix-partially}

After the automated deployment is completed, you can manually scale out by increasing RAM and disk in the initial virtual machine (VM) and add three scale-out VMs. The Riskforesight configuration script can be run to enable and configure the application components on all four VMs.

This deployment model is expected to service up to 500 Assets with up to 30 days of data indexing.

Select the next available IP addresses from the {{site.data.keyword.cloud}} private portable subnet. Configure FQDN names in ADDNS.

Find the details of the base VM, scale-out VM, and Remote Collector VM in the following tables.

|Parameter	|Value|
|---|---|
|Type	|Base|
|VM qty	|1|
|vCPU	|16|
|RAM	|64 GB|
|Disk	|1000 GB|
|OS	|CentOS 7|
|Installed Application Components	|UI, App, Plugins, Central Collector, Index Datastore, Messaging Datastore, Relational Datastore, Remote Collector|
{: caption="Table 1. Base VM parameters" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the parameter of the initial VM. The column headers indentify the value of the parameter. To find the value of a parameter, navigate to the row, and then find the value in the parameter column."}
{: #table1}
{: tab-title="Base VM"}
{: tab-group="Partially distributed - VM details"}
{: class="comparison-tab-table"}
{: row-headers}

| Parameter	| Value |
|---|---|
| Type	| Scale-out |
| VM qty	| 3 |
| vCPU	| 8 |
| RAM	| 16 GB |
| Disk	| 4 TB |
| OS	| CentOS 7 |
| Installed Application Components	| Data Nodes (scale-out) |
{: caption="Table 2. Scale-out VM parameters" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the parameter of the scale-out VM. The column headers indentify the value of the parameter. To find the value of a parameter, navigate to the row, and then find the value in the parameter column."}
{: #table2}
{: tab-title="Scale-out VM"}
{: tab-group="Partially distributed - VM details"}
{: class="comparison-tab-table"}
{: row-headers}

|Parameter	|Value|
|---|---|
|VM qty	|As required|
|vCPU	|8|
|RAM	|8 GB|
|Disk	|1 TB|
|OS	|CentOS 7|
|Installed Application Components	|Remote Collector|
{: caption="Table 3. Remote Collector VM parameters" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the parameter of the Remote Collector VM. The column headers indentify the value of the parameter. To find the value of a parameter, navigate to the row, and then find the value in the parameter column."}
{: #table3}
{: tab-title="Remote Collector VM"}
{: tab-group="Partially distributed - VM details"}
{: class="comparison-tab-table"}
{: row-headers}

**Next topic:** [Fully distributed](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix-fully)
