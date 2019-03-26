---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud 概述
{: #kmip_standalone_considerations}

KMIP for VMware on {{site.data.keyword.cloud}} 服务用于提供全天候高可用性服务，以管理 {{site.data.keyword.cloud_notm}} 中 VMware 使用的加密密钥。此服务提供了运行时功能，以支持客户创建、检索、激活、撤销和销毁加密密钥。还提供了管理功能，以维护客户机凭证与加密密钥之间的关联。

KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务作为独立服务提供，无需与 VMware 实例相关联。每个服务实例都可以为一个或多个 Cloud Foundation 实例、vCenter Server 实例或 vSphere 集群提供服务。

## KMIP for VMware on IBM Cloud 的技术规范
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务随附以下规范：

* 与 VMware 兼容的密钥管理互操作性协议 (KMIP)
* 受管服务
* 在全球多个地理区域中可用
* 每个区域中提供两个 KMIP 网络服务端点，以实现高可用性

## 安装 KMIP for VMware on IBM Cloud 实例时的注意事项
{: #kmip_standalone_considerations-install}

安装 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例之前，请查看以下注意事项：

* KMIP for VMware on {{site.data.keyword.cloud_notm}} 使用 IBM Key Protect for {{site.data.keyword.cloud_notm}} 服务来创建、加密和解密加密密钥。因此，安装 KMIP for VMware on {{site.data.keyword.cloud_notm}} 之前，确保：
   * 已在要托管 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例的 {{site.data.keyword.cloud_notm}} 区域中订购了可用的 Key Protect 服务。有关更多信息，请参阅[供应服务](/docs/services/key-protect?topic=key-protect-provision)。
   * 已通过执行[创建服务标识](/docs/iam?topic=iam-serviceids)中的步骤来创建 {{site.data.keyword.cloud_notm}} 服务标识。此服务标识用于访问创建的 Key Protect 服务实例。
   * 为服务标识授予了以下访问级别：
      * 在平台访问级别：对 IBM Key Protect 实例的“查看者”权限
      * 在服务访问级别：对 IBM Key Protect 实例的“管理者”权限
   * 您具有所创建的服务标识的 API 密钥。在订购服务时，需要密钥。
   * 您已通过执行[创建根密钥](/docs/services/keymgmt/keyprotect_create_root.html)中的步骤或通过使用 [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect) 中的 REST API，在 Key Protect 用户界面中至少创建了一个客户根密钥 (CRK)。

     **重要信息**：没有 CRK，无法订购此服务。强烈建议您通过该方法来使用现有密钥资料创建 CRK，并备份创建的密钥资料。通过执行此操作，可确保如果在其中应用 IBM Key Protect 来存储 CRK 的数据中心发生故障，您也可以恢复密钥。
* 确保 {{site.data.keyword.cloud_notm}} 基础架构帐户已启用支持虚拟路由和转发 (VRF) 以及与服务端点的连接。有关更多信息，请参阅：
   * [IBM Cloud 上的虚拟路由和转发 (VRF) 概述](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [使用 IBM Cloud CLI 支持帐户使用服务端点](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started)
* 由于仅支持专用连接，因此无需在 vCenter Server 中配置任何防火墙或 SNAT 规则，以用于从 vCenter Server 到 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例的端点的网络连接。

有关更多信息，请参阅 [KMIP for VMware on IBM Cloud 解决方案体系结构](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)。

## 删除 KMIP for VMware on IBM Cloud 实例时的注意事项
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

除去 KMIP for VMware on IBM Cloud 服务后，受该服务保护的所有数据（包括加密的备份）都无法解密。

## 相关链接
{: #kmip_standalone_considerations-related}

* [订购 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [添加、查看和删除 KMIP for VMware on IBM Cloud 实例的证书](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [查看 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [删除 KMIP for VMware on {{site.data.keyword.cloud_notm}} 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker 事件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
