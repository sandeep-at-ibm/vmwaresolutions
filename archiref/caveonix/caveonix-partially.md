---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-29"

subcollection: vmware-solutions


---

# Partially distributed
{: #caveonix-partially}

After the automated deployment is completed, you can manually scale out by increasing RAM and disk in the initial virtual machine (VM) and add three scale-out VMs. The Riskforesight configuration script can be run to enable and configure the application components on all four VMs.

This deployment model is expected to service up to 500 Assets with up to 30 days of data indexing.

Select the next available IP addresses from the {{site.data.keyword.cloud}} private portable subnet. Configure FQDN names in ADDNS.

The sizing of the VMs are as follows:

|Parameter	|Value|
|---|---|
|Type	|Base|
|VM qty	|1|
|vCPU	|16|
|RAM	|64 GB|
|Disk	|1000 GB|
|OS	|CentOS 7|
|Installed Application Components	|UI, App, Plugins, Central Collector, Index Datastore, Messaging Datastore, Relational Datastore, Remote Collector|
{: caption="Table 1. Base parameters" caption-side="bottom"}

The scale-out VM details are as follows:

| Parameter	| Value |
|---|---|
| Type	| Scale-out |
| VM qty	| 3 |
| vCPU	| 8 |
| RAM	| 16 GB |
| Disk	| 4 TB |
| OS	| CentOS 7 |
| Installed Application Components	| Data Nodes (scale-out) |
{: caption="Table 2. Scale-out parameters" caption-side="bottom"}

The Remote Collector VM details are shown in the following table.

|Parameter	|Value|
|---|---|
|VM qty	|As required|
|vCPU	|8|
|RAM	|8 GB|
|Disk	|1 TB|
|OS	|CentOS 7|
|Installed Application Components	|Remote Collector|
{: caption="Table 3. Remote collector parameters" caption-side="bottom"}

**Next topic:** [Fully distributed](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix-fully)
