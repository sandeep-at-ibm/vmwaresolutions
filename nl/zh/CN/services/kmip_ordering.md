---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# 订购 KMIP for VMware on IBM Cloud

订购 KMIP for VMware on {{site.data.keyword.cloud}} 服务时，可订购包含此服务的新实例，也可通过向现有实例添加此服务来进行订购。

## 为新实例订购 KMIP for VMware on IBM Cloud

可以使用下列其中一种方法订购包含 KMIP for VMware on {{site.data.keyword.cloud_notm}} 的新实例：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，订购新实例时，请在**服务**部分中选择 **KMIP for VMware on IBM Cloud**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **KMIP for VMware on IBM Cloud**，指定服务设置，然后选择**添加到新实例**。

## 为现有实例订购 KMIP for VMware on IBM Cloud

可以使用下列其中一种方法将 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务添加到现有实例中：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **KMIP for VMware on IBM Cloud**，指定服务设置，然后选择**添加到现有实例**。

## KMIP for VMware on IBM Cloud 服务配置

订购此服务时，请提供以下设置：

### 服务区域

选择要在其中托管 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务实例的 {{site.data.keyword.cloud_notm}} 区域。

{{site.data.keyword.cloud_notm}} 在提供了 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的每个区域中维护该服务的高可用性端点。

### 客户机 SSL 证书

对于 vCenter Server，必须配置密钥管理服务器 (KMS) 集群。所选区域中的端点通过客户机 SSL 证书安全地连接到 KMS。有关每个区域中的端点，请参阅下表。这些端点使用由 {{site.data.keyword.vmwaresolutions_short}} 团队维护的自签名证书。证书的指纹为 `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`。

表 1：KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务端点区域

|区域|端点|
|:---------------|:-----------------------|
|德国|`161.156.68.107:5696`|
|悉尼|`130.198.73.134:5696`|
|英国|`158.175.93.122:5696`|
|美国南部|`169.60.185.42:5696`|

此设置在初始配置时是可选的。此时可以将此字段保留为空，因为部署实例之后，vCenter Server 中的 KMS 的客户机证书是已知的。但是，必须在部署实例之后输入证书，才能成功完成 vCenter Server 与 KMS 的连接。

### 服务标识的 API 密钥

输入用于访问 IBM Key Protect 服务实例的 {{site.data.keyword.cloud_notm}} 服务标识的 API 密钥。

### Key Protect 实例

单击**检索**以获取可用 IBM Key Protect 服务实例的列表，然后选择用于密钥管理的实例。

### 客户根密钥

单击**检索**以获取在所选 IBM Key Protect 实例中存储的客户根密钥。



### 相关链接

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概述](kmip_considerations.html)
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere 安全性](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [常见问题](../vmonic/faq.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
