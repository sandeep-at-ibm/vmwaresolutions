---

copyright:

  years:  2016, 2020

lastupdated: "2020-09-30"

subcollection: vmwaresolutions


---

# All-in-one deployment
{: #caveonix-allinone}

An automated deployment and configuration of a single virtual machine (VM) that hosts all the RiskForesight application components. This deployment model is suitable for small deployments, up to 100 assets with 7 - 30 days of indexing. The details of the “all-in-one” VM and the additional Remote Collector VM are shown in the following tables.

| Parameter | Value |
|---|---|
| Type | Base |
| VM qty | 1 |
| vCPU | 16 |
| RAM | 32 GB |
| Disk | 80 GB |
| OS | CentOS 7 |
| Installed application components | UI, App, Plug-ins, Central collector, Index datastore, Messaging datastore, Relational datastore, Index datastore, Remote collector |
{: class="simple-tab-table"}
{: caption="Table 1. All-in-one VM parameters" caption-side="top"}
{: #table1}
{: tab-title="All-in-one VM"}
{: tab-group="all-in-one-vm"}

|Parameter | Value |
|---|---|
| VM qty | As required |
| vCPU | 8 |
| RAM | 8 GB |
| Disk | 1 TB |
| OS | CentOS 7 |
| Installed application components | Remote collector |
{: caption="Table 1. Remote collector VM parameters" caption-side="top"}
{: #table2}
{: tab-title="Remote collector VM"}
{: tab-group="all-in-one-vm"}
{: class="simple-tab-table"}

**Next topic:** [Partially distributed](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix-partially)
