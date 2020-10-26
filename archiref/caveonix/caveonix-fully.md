---

copyright:

  years:  2016, 2020

lastupdated: "2020-09-21"

subcollection: vmwaresolutions


---

# Fully distributed
{: #caveonix-fully}

Additional base virtual machines (VMs) and scale-out VMs are added according to the number of assets and data retention requirements.

| Parameter | Value |
|---|---|
| Type | Base |
| VM qty | 2 |
| vCPU | 2 |
| RAM | 6 GB |
| Disk | 60 GB |
| OS |CentOS 7|
|  Installed application components | UI |
{: caption="Table 1. Base - user interface" caption-side="top"}

|Parameter | Value |
|---|---|
| Type | Base |
| VM qty | 2 |
| vCPU | 8 |
| RAM | 16 GB |
| Disk | 500 GB |
| OS | CentOS 7 |
| Installed application components | App, Plugins|
{: caption="Table 2. Base - applications and plug-ins" caption-side="top"}

| Parameter | Value |
|---|---|
| Type | Base |
| VM qty | 3 |
| vCPU | 8 |
| RAM | 16 GB |
| Disk | 500 GB |
| OS | CentOS 7 |
| Installed application components | Central collector (cluster) |
{: caption="Table 3. Base - Central collector" caption-side="top"}

|Parameter | Value |
|---|---|
| Type | Base |
| VM qty | 2 |
| vCPU | 8 |
| RAM | 16 GB |
| Disk | 1 TB |
| OS | CentOS 7 |
|Installed application components | Relational datastore (Primary / secondary) |
{: caption="Table 4. Base - relational database" caption-side="top"}

|Parameter | Value |
|---|---|
| Type | Base |
| VM qty | 3 |
| vCPU | 8 |
| RAM | 16 GB |
| Disk |1 TB |
| OS | CentOS 7 |
| Installed application components | Messaging datastore (cluster) |
{: caption="Table 5. Base - messaging datastore" caption-side="top"}

|Parameter | Value |
|---|---|
| Type | Base |
| VM qty |3 |
| vCPU | 8 |
| RAM | 16 GB |
| Disk | 1 TB |
| OS | CentOS 7 |
| Installed application components	|Index Datastore (Primary Nodes) |
{: caption="Table 6. Base - index datastore (primary nodes)" caption-side="top"}

|Parameter | Value |
|---|---|
| Type | Base |
| VM qty | 5 |
| vCPU | 8 |
| RAM | 16 GB |
| Disk | 4 TB |
| OS | CentOS 7 |
| Installed application components | Index datastore (data nodes) |
{: caption="Table 7. Database - index datastore (data nodes)" caption-side="top"}

The scale-out VM details are described in the following table.

|Parameter | Value |
|---|---|
| Type | Scale-out |
| VM qty | 28 |
| vCPU | 8 |
| RAM | 16 GB |
| Disk | 4 TB |
| OS | CentOS 7 |
| Installed application components | Data nodes (scale-out) |
{: caption="Table 8. Scale-out - data nodes" caption-side="top"}

The Remote Collector VM details are shown in the following table.

|Parameter | Value |
|---|---|
| VM qty | As required |
| vCPU | 8 |
| RAM | 8 GB |
| Disk | 1 TB |
| OS | CentOS 7 |
| Installed application components | Remote collector |
{: caption="Table 9. Remote collector" caption-side="top"}

**Next topic:** [Step 1 - Initial planning and prerequisites](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix-step1)
