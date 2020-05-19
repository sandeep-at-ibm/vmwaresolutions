---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-30"

subcollection: vmwaresolutions


---

# All-in-one deployment
{: #caveonix-allinone}

An automated deployment and configuration of a single virtual machine (VM) that hosts all the RiskForesight application components. This deployment model is suitable for small deployments, up to 100 assets with 7 - 30 days of indexing. The details of the “all-in-one” VM and the additional Remote Collector VM are shown in the following tables.

|Parameter	|Value|
|---|---|
|Type	|Base|
|VM qty	|1|
|vCPU	|16|
|RAM	|32 GB|
|Disk	|80 GB|
|OS	|CentOS 7|
|Installed Application Components|	UI, App, Plug-ins, Central Collector, Index Datastore, Messaging Datastore, Relational Datastore, Index Datastore, Remote Collector|
{: caption="Table 1. All-in-one VM parameters" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the parameter of the all-in-one VM. The column headers indentify the value of the parameter. To find the value of a parameter, navigate to the row, and then find the value in the parameter column."}
{: #table1}
{: tab-title="All-in-one VM"}
{: tab-group="All-in-one deployment VM details"}
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
{: caption="Table 2. Remote collector VM parameters" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the parameter of the Remote Collector VM. The column headers indentify the value of the parameter. To find the value of a parameter, navigate to the row, and then find the value in the parameter column."}
{: #table2}
{: tab-title="Remote Collector VM"}
{: tab-group="All-in-one deployment VM details"}
{: class="comparison-tab-table"}
{: row-headers}

**Next topic:** [Partially distributed](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix-partially)
