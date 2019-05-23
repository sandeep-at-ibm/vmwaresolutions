---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-08"

subcollection: vmware-solutions


---

# 订购 KMIP for VMware on IBM Cloud 实例
{: #kmip_standalone_ordering}

您可以订购 KMIP for VMware on {{site.data.keyword.cloud}} 实例，并且无需将其与任何 VMware 实例相关联，就可灵活管理服务和实例。

## 开始之前
{: #kmip_standalone_ordering-req}

确保已完成以下任务：
* 已在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。有关更多信息，请参阅[用户帐户和设置](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。
* 已查看[安装 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例时的注意事项](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations-install)中的所有注意事项。

## 订购 KMIP for VMware on IBM Cloud 实例的过程
{: #kmip_standalone_ordering-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**开始**。
2. 在**订购其他服务**区域中，单击 **KMIP for VMware on IBM Cloud**。
3. 在 **KMIP for VMware on IBM Cloud** 页面上，根据需要配置服务设置。
4. 单击**供应**。

## KMIP for VMware on IBM Cloud 服务配置
{: #kmip_standalone_ordering-config}

订购此服务时，请提供以下设置：

### 实例名称
{: #kmip_standalone_ordering-config-instance-name}

指定 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例的名称。

### 服务位置
{: #kmip_standalone_ordering-config-service-region}

选择要托管 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例的 {{site.data.keyword.cloud_notm}} 位置。

{{site.data.keyword.cloud_notm}} 在提供了 KMIP for VMware on {{site.data.keyword.cloud_notm}} 网络服务的每个位置中维护该服务的高可用性端点。

表 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} 网络服务端点位置

|位置|端点|
|:---------------|:-----------------------|
|达拉斯| <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
|法兰克福|  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
|伦敦| <ul><li><code>kmip-1.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
|悉尼|  <ul><li><code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
|东京| <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| 华盛顿| <ul><li><code>kmip-1.private.us-east.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-east.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### 服务标识的 API 密钥
{: #kmip_standalone_ordering-config-api-key}

输入用于访问 Key Protect 或 Hyper Protect Crypto Services 服务实例的 {{site.data.keyword.cloud_notm}} 服务标识的 API 密钥。

### 密钥管理器实例
{: #kmip_standalone_ordering-config-key-protect}

单击**检索**以获取可用密钥管理器实例的列表，然后选择用于密钥管理的实例。

### 客户根密钥
{: #kmip_standalone_ordering-config-root-key}

单击**检索**以获取在所选密钥管理器实例中存储的客户根密钥。

## 结果
{: #kmip_standalone_ordering-results}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例的订购会自动启动。您将收到说明订单正在处理的确认，并且您可以通过查看实例详细信息来检查订单的状态。

实例准备就绪可供使用后，该实例的状态会更改为**已安装**，并且您将收到通过电子邮件发送的通知。

## 后续步骤
{: #kmip_standalone_ordering-next}

添加所订购 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例的客户机证书。有关更多信息，请参阅[添加、查看和删除 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例的证书](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)。

## 相关链接
{: #kmip_standalone_ordering-related}

* [查看 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [删除 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker 事件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
