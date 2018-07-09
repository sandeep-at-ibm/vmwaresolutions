---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# KMIP for VMware on IBM Cloud 概述

KMIP for VMware on {{site.data.keyword.cloud}} 服务用于提供全天候高可用性服务，以管理 {{site.data.keyword.cloud_notm}} 中 VMware 使用的加密密钥。此服务提供了运行时功能，以支持客户创建、检索、激活、撤销和销毁加密密钥。还提供了管理功能，以维护客户机凭证与加密密钥之间的关联。

**可用性**：此服务仅可用于在 V2.2 或更高发行版中部署的实例。

## 安装 KMIP for VMware on IBM Cloud 时的注意事项

KMIP for VMware on {{site.data.keyword.cloud_notm}} 使用 IBM Key Protect for {{site.data.keyword.cloud_notm}} 服务来创建、加密和解密加密密钥。因此，安装 KMIP for VMware on {{site.data.keyword.cloud_notm}} 之前，确保：
* 订购了可使用的 Key Protect 服务。
* 已通过执行[创建服务标识](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id)中的步骤来创建 {{site.data.keyword.cloud_notm}} 服务标识。此服务标识用于访问创建的 Key Protect 服务实例。
* 为服务标识授予了以下访问级别：
   * 在平台访问级别：对 IBM Key Protect 实例的“查看者”权限。
   * 在服务访问级别：对 IBM Key Protect 实例的“作者”权限
* 您具有所创建的服务标识的 API 密钥。在订购服务时，需要密钥。
* 您已通过执行[创建根密钥](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys)中的步骤或通过使用 [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect) 中的 REST API，在 Key Protect 用户界面中至少创建了一个客户根密钥 (CRK)。

   **重要信息**：没有 CRK，无法订购此服务。强烈建议您通过该方法来使用现有密钥资料创建 CRK，并备份创建的密钥资料。通过执行此操作，可确保在其中应用 IBM Key Protect 来存储 CRK 的数据中心发生故障的情况下，您也可以恢复密钥。

## 使用 KMIP for VMware on IBM Cloud 时的注意事项

* 要将订购的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务用作向 VMware vCenter Server 注册的密钥管理服务器 (KMS)，请确保 vCenter Server 与已订购 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的端点之间的网络连接正常运行。
* 要将该服务用于 VMware vSAN 加密，请确保目标 vSAN 上的主机与已订购 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的端点之间的网络连接正常运行。

## 除去 KMIP for VMware on IBM Cloud 时的注意事项

订购或使用此服务时提供的 VMware 公用证书用作客户机证书来与此服务实例进行通信。除去服务时，此服务实例为关联的 VMware 公用证书创建的所有加密密钥也将除去。

因此，在除去服务之前，确保没有虚拟机或 vSAN 是使用 KMIP 服务创建的密钥进行加密的。

## 相关链接

* [订购 KMIP for VMware on IBM Cloud](kmip_ordering.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere 安全性](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [常见问题](../vmonic/faq.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
