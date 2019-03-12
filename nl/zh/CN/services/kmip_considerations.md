---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# KMIP for VMware on IBM Cloud 概述 - 不推荐
{: #kmip_considerations}

不推荐使用当前版本的 KMIP for VMware on IBM Cloud。有关更多信息，请[联系 IBM 支持人员](../vmonic/trbl_support.html)。
{:deprecated}

KMIP for VMware on {{site.data.keyword.cloud}} 服务用于提供全天候高可用性服务，以管理 {{site.data.keyword.cloud_notm}} 中 VMware 使用的加密密钥。此服务提供了运行时功能，以支持客户创建、检索、激活、撤销和销毁加密密钥。还提供了管理功能，以维护客户机凭证与加密密钥之间的关联。

## KMIP for VMware on IBM Cloud 的技术规范
{: #kmip_considerations-specs}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务随附以下规范：

* 与 VMware 兼容的密钥管理互操作性协议 (KMIP)
* 受管服务
* 在全球多个地理区域中可用
* 每个区域中一个高可用性 KMIP 服务端点

## 安装 KMIP for VMware on IBM Cloud 时的注意事项
{: #kmip_considerations-install}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 使用 IBM Key Protect for {{site.data.keyword.cloud_notm}} 服务来创建、加密和解密加密密钥。因此，安装 KMIP for VMware on {{site.data.keyword.cloud_notm}} 之前，确保：
* 订购了可使用的 Key Protect 服务。
* 已通过执行[创建服务标识](../../../iam/serviceid.html)中的步骤来创建 {{site.data.keyword.cloud_notm}} 服务标识。此服务标识用于访问创建的 Key Protect 服务实例。
* 为服务标识授予了以下访问级别：
   * 在平台访问级别：对 IBM Key Protect 实例的“查看者”权限。
   * 在服务访问级别：对 IBM Key Protect 实例的“写入者”权限
* 您具有所创建的服务标识的 API 密钥。在订购服务时，需要密钥。
* 您已通过执行[创建根密钥](../../keymgmt/keyprotect_create_root.html)中的步骤或通过使用 [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect) 中的 REST API，在 Key Protect 用户界面中至少创建了一个客户根密钥 (CRK)。

   **重要信息**：没有 CRK，无法订购此服务。强烈建议您通过该方法来使用现有密钥资料创建 CRK，并备份创建的密钥资料。通过执行此操作，可确保如果在其中应用 IBM Key Protect 来存储 CRK 的数据中心发生故障，您也可以恢复密钥。

## 使用 KMIP for VMware on IBM Cloud 时的注意事项
{: #kmip_considerations-use}

* 要将订购的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务用作向 VMware vCenter Server 注册的密钥管理服务器 (KMS)，请确保 vCenter Server 与已订购 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的端点之间的网络连接正常运行。
* 要将该服务用于 VMware vSAN 加密，请确保目标 vSAN 上的主机与已订购 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的端点之间的网络连接正常运行。
* 将 KMIP for VMware 用于 vSAN 加密时，vSAN 运行状况检查可能会定期发出警告，指示无法从一个或多个 vSphere 主机连接到 KMS 集群。出现这些警告是因为 vSAN 运行状况检查连接超时过快。您可以忽略这些警告。

## 除去 KMIP for VMware on IBM Cloud 时的注意事项
{: #kmip_considerations-remove}

订购或使用此服务时提供的 VMware 公用证书用作客户机证书来与此服务实例进行通信。除去服务时，此服务实例为关联的 VMware 公用证书创建的所有加密密钥也将除去。

因此，在除去服务之前，请确保没有虚拟机或 vSAN 是使用 KMIP 服务创建的密钥进行加密的。

## 相关链接
{: #kmip_considerations-related}

* [订购 KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_ordering.html)
* [{{site.data.keyword.cloudaccesstrailshort}} 事件](../vmonic/at-events.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](../../keymgmt/index.html)
* [vSphere 安全性](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [常见问题](../vmonic/faq.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
