---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-30"

subcollection: vmwaresolutions


---

# Fully distributed
{: #caveonix-fully}

Additional base virtual machines (VMs) and scale-out VMs are added according to the number of assets and data retention requirements.

|Parameter	|Value|
|---|---|
|Type	|Base|
|VM qty	|2|
|vCPU	|2|
|RAM	|6 GB|
|Disk	|60 GB|
|OS	|CentOS 7|
|Installed Application Components	|UI|
{: caption="Table 1. Base - user interface" caption-side="bottom"}

|Parameter	|Value|
|---|---|
|Type	|Base|
|VM qty	|2|
|vCPU	|8|
|RAM	|16 GB|
|Disk	|500 GB|
|OS	|CentOS 7|
|Installed Application Components	|App, Plugins|
{: caption="Table 2. Base - applications and plug-ins" caption-side="bottom"}

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|500 GB |
|OS	|CentOS 7 |
|Installed Application Components	|Central Collector (Cluster) |
{: caption="Table 3. Base - central collector" caption-side="bottom"}

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|2 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	C|entOS 7 |
|Installed Application Components	|Relational Datastore (Primary / Secondary) |
{: caption="Table 4. Base - relational database" caption-side="bottom"}

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Messaging Datastore (Cluster) |
{: caption="Table 5. Base - messaging datastore" caption-side="bottom"}

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Index Datastore (Master Nodes) |
{: caption="Table 6. Base - index datastore (master nodes)" caption-side="bottom"}

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|5 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|4 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Index Datastore (Data Nodes) |
{: caption="Table 7. Database - index datastore (data nodes)" caption-side="bottom"}

The scale-out VM details are described in the following table.

|Parameter	|Value |
|---|---|
|Type	|Scale-out |
|VM qty	28 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|4 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Data Nodes (scale-out) |
{: caption="Table 8. Scale-out - data nodes" caption-side="bottom"}

The Remote Collector VM details are shown in the following table.

|Parameter	|Value |
|---|---|
|VM qty	|As required |
|vCPU	|8 |
|RAM	|8 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Remote Collector |
{: caption="Table 9. Remote collector" caption-side="bottom"}

**Next topic:** [Step 1 - Initial planning and prerequisites](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix-step1)
