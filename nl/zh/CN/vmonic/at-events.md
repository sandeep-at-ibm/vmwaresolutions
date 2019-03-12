---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-14"

---

# Activity Tracker 事件
{: #at-events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务可跟踪用户和应用程序如何与 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.vmwaresolutions_short}} 进行交互。

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务将记录用户启动的会更改 {{site.data.keyword.Bluemix_notm}} 中服务状态的活动。有关更多信息，请参阅 [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla)。

## Activity Tracker 事件表
{: #at-events-table}

查看下表以了解 Activity Tracker 事件表中各列的描述。

表 1. Activity Tracker 事件表的描述

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

有关更多信息，请参阅 [Activity Tracker 事件字段](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event)。

## 跟踪实例管理事件
{: #at-events-instance-mgmt}

在 {{site.data.keyword.vmwaresolutions_short}} 中管理用户帐户、实例、集群和服务时，会生成事件并将其发送到 Activity Tracker 中的**帐户域**。

查看下表以了解生成管理事件并将其发送到 Activity Tracker 的操作。

表 2. 生成管理事件的操作的描述

|操作|描述|结果|
|:-----------------------------------------|:------------|:-------|
|`vmware-solutions.user_account.update`| <ul><li>收到更新用户帐户的请求。</li><li>响应了更新用户帐户的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.notification.update`| <ul><li>收到更新通知的请求。</li><li>应答了更新通知的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.secure_data.wipe`| <ul><li>收到擦除安全数据的请求。</li><li>应答了擦除安全数据的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.bss_account.migrate`| <ul><li>收到迁移到 BSS 帐户的请求。</li><li>应答了迁移到 BSS 帐户的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcf.order`| <ul><li>收到订购 Cloud Foundation 实例的请求。</li><li>应答了订购 Cloud Foundation 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcf.delete`| <ul><li>收到删除 Cloud Foundation 实例的请求。</li><li>应答了删除 Cloud Foundation 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcf.add_hosts`| <ul><li>收到将 ESXi 服务器添加到 Cloud Foundation 实例的请求。</li><li>应答了将 ESXi 服务器添加到 Cloud Foundation 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcf.remove_hosts`| <ul><li>收到从 Cloud Foundation 实例中删除 ESXi 服务器的请求。</li><li>应答了从 Cloud Foundation 实例中删除 ESXi 服务器的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcf.create_cluster`| <ul><li>收到为 Cloud Foundation 实例创建集群的请求。</li> <li>应答了为 Cloud Foundation 实例创建集群的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcf.delete_cluster`| <ul><li>收到从 Cloud Foundation 实例中删除集群的请求。</li><li>应答了从 Cloud Foundation 实例中删除集群的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcf.schedule_update`| <ul><li>收到安排 Cloud Foundation 实例更新的请求。</li><li>应答了安排 Cloud Foundation 实例更新的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.order`| <ul><li>收到订购 vCenter Server 实例的请求。</li><li>应答了订购 vCenter Server 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.delete`| <ul><li>收到删除 vCenter Server 实例的请求。</li><li>应答了删除 vCenter Server 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.add_host`| <ul><li>收到将 ESXi 服务器添加到 vCenter Server 实例的请求。</li><li>应答了将 ESXi 服务器添加到 vCenter Server 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.remove_hosts`| <ul><li>收到从 vCenter Server 实例中删除 ESXi 服务器的请求。</li><li>应答了从 vCenter Server 实例中删除 ESXi 服务器的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.schedule_update`| <ul><li>收到安排 vCenter Server 实例更新的请求。</li><li>应答了安排 vCenter Server 实例更新的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.create_cluster`| <ul><li>收到为 vCenter Server 实例创建集群的请求。</li><li>应答了为 vCenter Server 实例创建集群的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.delete_cluster`| <ul><li>收到从 vCenter Server 实例中删除集群的请求。</li> <li>应答了从 vCenter Server 实例中删除集群的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.update_nsx_license`| <ul><li>收到更新 VMware NSX 许可证的请求。</li><li>应答了更新 VMware NSX 许可证的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vcs.upgrade_to_hybridity`| <ul><li>收到将 vCenter Server 实例升级到 vCenter Server with Hybridity Bundle 实例的请求。</li><li>应答了将 vCenter Server 实例升级到 vCenter Server with Hybridity Bundle 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vsphere.order`| <ul><li>收到订购 vSphere 集群的请求。</li><li>应答了订购 vSphere 集群的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vsphere.update`| <ul><li>收到更新 vSphere 集群的请求。</li><li>应答了更新 vSphere 集群的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.vsphere.save_template`| <ul><li>收到保存 vSphere 集群配置的请求。</li><li>应答了保存 vSphere 集群配置的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.netapp.order`| <ul><li>收到订购 NetApp ONTAP Select 实例的请求。</li><li>应答了订购 NetApp ONTAP Select 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.netapp.delete`| <ul><li>收到删除 NetApp ONTAP Select 实例的请求。</li><li>应答了删除 NetApp ONTAP Select 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.service_variable.update`| <ul><li>收到更新服务配置的请求。</li><li>应答了更新服务配置的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.service.order`| <ul><li>收到为实例订购服务的请求。</li><li>应答了为实例订购服务的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.service.delete_by_id`| <ul><li>收到从实例中删除服务的请求。</li><li>应答了从实例中删除服务的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.service.upgrade_to_hybridity`| <ul><li>收到将现有 vCenter Server 实例升级到 vCenter Server with Hybridity Bundle 实例的请求。</li><li>应答了将现有 vCenter Server 实例升级到 vCenter Server with Hybridity Bundle 实例的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.service.deploy`|运行了在实例上部署服务的操作。|`success`|
|`vmware-solutions.service.undeploy`|运行了从实例中除去服务的操作。|`success`|

## 跟踪 KMIP for VMware on IBM Cloud 服务的事件
{: #at-events-kmip}

管理 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的密钥时，会生成事件并将其发送到 Activity Tracker 中的**帐户域**。

查看下表以了解生成并发送 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的事件的操作。

表 3. 生成 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的事件的操作描述

|操作|描述|结果|
|:--------------------------------------------|:------------------------------------------|:-------|
|`vmware-solutions.key.create`| <ul><li>收到创建密钥的请求。</li><li>应答了创建密钥的请求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.key.get`| <ul><li>收到获取密钥内容的请求。</li><li>应答了获取密钥内容的请求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.key.get_attributes`| <ul><li>收到获取密钥属性的请求。</li><li>应答了获取密钥属性的请求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.key.activate`| <ul><li>收到激活密钥的请求。</li><li>应答了激活密钥的请求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.key.revoke`| <ul><li>收到撤销密钥的请求。</li><li>应答了撤销密钥的请求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.key.destroy`| <ul><li>收到销毁密钥的请求。</li><li>应答了销毁密钥的请求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
|`vmware-solutions.key.discover_versions`| <ul><li>收到查找 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务版本的请求。</li><li>应答了查找 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务版本的请求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |

## 查看事件的位置
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} 事件在生成事件的 {{site.data.keyword.Bluemix_notm}} 区域中可用的 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**中提供。

## 相关链接
{: #at-events-related}

* [供应 Activity Tracker](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [在 {{site.data.keyword.cloud_notm}} 控制台中浏览至 Activity Tracker 仪表板](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
