---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-02"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Activity Tracker 事件
{: #at-events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务可跟踪用户和应用程序如何与 {{site.data.keyword.cloud_notm}} 中的 {{site.data.keyword.vmwaresolutions_short}} 进行交互。

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务将记录用户启动的会更改 {{site.data.keyword.cloud_notm}} 中服务状态的活动。有关更多信息，请参阅[关于 IBM® Cloud Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#gs_ov)。

## Activity Tracker 事件表
{: #at-events-table}

查看下表以了解 Activity Tracker 事件表中各列的描述。

|列|值类型|描述|
|:----------------------|:-----------|:------------|
| Time                  |不适用|事件的创建日期和时间。|
| initiator.name        |字符串|启动操作的用户的 IBM 标识。|
| target_name           |字符串|对其运行操作的资源。|
| target.typeURI        |字符串|对其运行操作的目标的通用唯一标识 (UUID)。|
| action                |字符串|触发事件的操作。有效值为 `create`、`update` 和 `delete`。|
| outcome               |字符串|操作的结果。值为 `success`、`failure` 或 `pending`。|
| reason_reasonCode     |整数|结果的原因码。|
| initiator_host_address|字符串|发出请求的 IP 地址。|
{: caption="表 1. Activity Tracker 事件表的描述" caption-side="top"}

有关更多信息，请参阅[事件字段](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-event)。

## 跟踪实例管理事件
{: #at-events-instance-mgmt}

在 {{site.data.keyword.vmwaresolutions_short}} 中管理用户帐户、实例、集群和服务时，会生成事件并将其发送到 Activity Tracker 中的**帐户域**。

查看下表以了解生成管理事件并将其发送到 Activity Tracker 的操作。

|操作|描述|结果|
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` |将更新帐户的基础架构 API 密钥。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.account-notification.update` | 将更新帐户的通知设置。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | 将擦除实例安全数据。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	实例会迁移到 BSS 帐户。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.create` |将创建 vCenter Server 实例。|`pending`<br>`success`<br>`failure` |
|`vmware-solutions.vcs.delete`|将删除 vCenter Server 实例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.add` |主机将添加到 vCenter Server 实例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.remove` |主机将从 vCenter Server 实例中除去。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.update`	| 将更新 vCenter Server 实例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.create`	| 将为 vCenter Server 实例创建集群。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete`	| 将为 vCenter Server 实例删除集群。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update`	| 将为 vCenter Server 实例更新 NSX 许可证。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add`	| 将为 vCenter Server 实例更新 Hybridity Bundle。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove`	| 将为 vCenter Server 实例除去 Hybridity Bundle。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add`	| NFS 存储器将添加到 vCenter Server 实例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove`	| NFS 存储器将从 vCenter Server 实例中除去。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-plan.update`	| 将更新 vCenter Server 实例的套餐。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.create`	|将创建 vSphere 实例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.update`	| 将更新 vSphere 实例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss-template.remove` |将除去 vSphere 模板。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.create`	|将创建服务。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.delete`	|将删除服务。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` |Hybridity Bundle 将升级到 `version`。|`pending`<br>`success`<br>`failure` |
{: caption="表 2. 生成管理事件的操作的描述" caption-side="top"}

## 跟踪 KMIP for VMware on IBM Cloud 服务的事件
{: #at-events-kmip}

管理 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的密钥时，会生成事件并将其发送到 Activity Tracker 中的**帐户域**。

查看下表以了解生成并发送 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的事件的操作。

|操作|描述|结果|
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` |将创建 KMIP 密钥。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` |将检索 KMIP 密钥。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` |将检索 KMIP 密钥的属性。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.activate` |将激活 KMIP 密钥。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` |将撤销 KMIP 密钥。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` |将销毁 KMIP 密钥。|`pending`<br>`success`<br>`failure` |
{: caption="表 3. 生成 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的事件的操作描述" caption-side="top"}

## 在何处查看事件
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} 事件在生成这些事件的 {{site.data.keyword.cloud_notm}} 区域中可用的 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**中提供。

使用 {{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA 来查看实例。有关更多信息，请参阅[查看事件](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events)。

## 相关链接
{: #at-events-related}

* [供应实例](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [导航至 Web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
