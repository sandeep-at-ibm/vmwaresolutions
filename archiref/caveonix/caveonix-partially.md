---

copyright:

  years:  2016, 2020

lastupdated: "2020-09-30"

subcollection: vmwaresolutions

---

# Partially distributed
{: #caveonix-partially}

After the automated deployment is completed, you can manually scale out by increasing RAM and disk in the initial virtual machine (VM) and add three scale-out VMs. The Riskforesight configuration script can be run to enable and configure the application components on all four VMs.

This deployment model is expected to service up to 500 Assets with up to 30 days of data indexing.

Select the next available IP addresses from the {{site.data.keyword.cloud}} private portable subnet. Configure FQDN names in ADDNS.

Find the details of the base VM, scale-out VM, and Remote collector VM in the following tables.

|Parameter | Value |
|----------|-------|
| Type | Base |
| VM qty | 1 |
| vCPU | 16 |
| RAM | 64 GB |
| Disk | 1,000 GB |
| OS | CentOS 7 |
| Installed application components | UI, App, Plugins, Central collector, Index datastore, Messaging datastore, Relational datastore, Remote collector |
{: class="simple-tab-table"}
{: caption="Table 1. Base VM parameters" caption-side="top"}
{: #table1}
{: tab-title="Base VM"}
{: tab-group="partially-caveonix"}

| Parameter | Value |
|---|---|
| Type | Scale-out |
| VM qty | 3 |
| vCPU | 8 |
| RAM | 16 GB |
| Disk | 4 TB |
| OS | CentOS 7 |
| Installed application components | Data nodes (scale-out) |
{: caption="Table 1. Scale-out VM parameters" caption-side="top"}
{: #table2}
{: tab-title="Scale-out VM"}
{: tab-group="partially-caveonix"}
{: class="simple-tab-table"}

| Parameter | Value |
|-----------|-------|
| VM qty | As required |
| vCPU | 8 |
| RAM | 8 GB |
| Disk | 1 TB |
| OS | CentOS 7 |
| Installed application components | Remote collector |
{: caption="Table 1. Remote collector VM parameters" caption-side="top"}
{: #table3}
{: tab-title="Remote collector VM"}
{: tab-group="partially-caveonix"}
{: class="simple-tab-table"}

**Next topic:** [Fully distributed](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix-fully)
