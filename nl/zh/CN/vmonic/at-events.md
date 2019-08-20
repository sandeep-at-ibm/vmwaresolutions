---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Activity Tracker 事件
{: #at-events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务可跟踪用户和应用程序如何与 {{site.data.keyword.cloud_notm}} 中的 {{site.data.keyword.vmwaresolutions_short}} 进行交互。

{{site.data.keyword.at_full_notm}} 将记录用户启动的会更改 {{site.data.keyword.cloud_notm}} 中服务状态的活动。您可以使用此服务来调查异常活动和关键操作，并符合监管审计需求。此外，您可以在操作发生时收到警报。收集的事件符合 Cloud Auditing Data Federation (CADF) 标准。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)。

## 跟踪实例管理事件
{: #at-events-instance-mgmt}

在 {{site.data.keyword.vmwaresolutions_short}} 中管理用户帐户、实例、集群和服务时，会生成事件并将其发送到全局域，或者发送到供应服务的位置中的服务实例。有关更多信息，请参阅[监视全局事件和基于位置的事件](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type)。

下表提供了生成管理事件并将其发送到 Activity Tracker 的操作。

|操作|描述|
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` |将更新帐户的基础架构 API 密钥。|
| `vmware-solutions.account-notification.update` | 将更新帐户的通知设置。|
| `vmware-solutions.instance-secure-data.wipe` | 将擦除实例安全数据。|
| `vmware-solutions.instance-bss-account.migrate` |	实例会迁移到 BSS 帐户。|
| `vmware-solutions.vcs.create` |将创建 vCenter Server 实例。|
|`vmware-solutions.vcs.delete`|将删除 vCenter Server 实例。|
| `vmware-solutions.vcs-host.add` |主机将添加到 vCenter Server 实例。|
| `vmware-solutions.vcs-host.remove` |主机将从 vCenter Server 实例中除去。|
| `vmware-solutions.vcs.update`	| 将更新 vCenter Server 实例。|
| `vmware-solutions.vcs-cluster.create`	| 将为 vCenter Server 实例创建集群。|
| `vmware-solutions.vcs-cluster.delete`	| 将为 vCenter Server 实例删除集群。|
| `vmware-solutions.vcs-nsx-license.update`	| 将为 vCenter Server 实例更新 NSX 许可证。|
| `vmware-solutions.vcs-nfs-storage.add`	| NFS 存储器将添加到 vCenter Server 实例。|
| `vmware-solutions.vcs-nfs-storage.remove`	| NFS 存储器将从 vCenter Server 实例中除去。|
| `vmware-solutions.vcs-plan.update`	| 将更新 vCenter Server 实例的套餐。|
| `vmware-solutions.vss.create`	|将创建 vSphere 实例。|
| `vmware-solutions.vss.update`	| 将更新 vSphere 实例。|
| `vmware-solutions.vss-template.remove` |将除去 vSphere 模板。|
| `vmware-solutions.service.create`	|将创建服务。|
| `vmware-solutions.service.delete`	|将删除服务。|
{: caption="表 1. 生成管理事件的操作的描述" caption-side="top"}

## 跟踪 KMIP for VMware on IBM Cloud 服务的事件
{: #at-events-kmip}

管理 KMIP for VMware on {{site.data.keyword.cloud_notm}} 的密钥时，会生成事件并将其发送到全局域，或者发送到供应服务的位置中的服务实例。有关更多信息，请参阅[监视全局事件和基于位置的事件](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type)。

下表提供了生成并发送 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的事件的操作。

|操作|描述|
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` |将创建 KMIP 密钥。|
| `vmware-solutions.kmip-key.retrieve` |将检索 KMIP 密钥。|
| `vmware-solutions.kmip-key-attributes.retrieve` |将检索 KMIP 密钥的属性。|
| `vmware-solutions.kmip-key.activate` |将激活 KMIP 密钥。|
| `vmware-solutions.kmip-key.revoke` |将撤销 KMIP 密钥。|
| `vmware-solutions.kmip-key.destroy` |将销毁 KMIP 密钥。|
{: caption="表 2. 生成 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的事件的操作描述" caption-side="top"}

## 在何处查看事件
{: #at-events-viewing}

事件在**法兰克福**位置可用。

每个位置只有 1 个 {{site.data.keyword.at_full_notm}} 实例。要查看事件，必须访问 **EU-DE** 位置的 {{site.data.keyword.at_full_notm}} 服务的 Web UI。有关更多信息，请参阅[通过 IBM Cloud UI 启动 Web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2)。

## 相关链接
{: #at-events-related}

* [供应实例](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [导航至 Web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
