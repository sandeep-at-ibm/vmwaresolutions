---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware 实现和管理

**注**：在此发行版中，KMIP for VMware on {{site.data.keyword.cloud_notm}} 限制为仅使用 vSphere 加密。

## 连接密钥管理服务器

要使用 KMIP for VMware on {{site.data.keyword.cloud_notm}} 来启用 vSphere 加密或 vSAN 加密，需要完成以下任务：

1. [支持帐户使用服务端点](/docs/services/service-endpoint/enable-servicepoint.html#getting-started)。
2. 创建 [IBM Key Protect](/docs/services/key-protect/index.html) 实例。
3. 在 IBM Key Protect 中创建客户根密钥 (CRK)。
4. 创建 Identity and Access Management (IAM) [服务标识和 API 密钥](/docs/iam/serviceid_keys.html)，以用于 KMIP for VMware。授予此服务标识对 Key Protect 实例的平台“查看者”访问权和服务“写入者”访问权。
5. 通过“{{site.data.keyword.cloud_notm}}”目录创建 [KMIP for VMware](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html) 实例。
6. 在 VMware vCenter 中，创建一个密钥管理服务器 (KMS) 集群，该集群包含两个服务器，每个服务器对应于您所选区域中的每个 KMIP for VMware 端点。
7. 选择其中一种 VMware 方法在 vCenter 中生成或安装 KMS 客户机证书。
8. 导出证书的公共版本，并在 KMIP for VMware 实例中将其配置为允许的客户机证书。

## 启用加密

要使用 vSAN 加密，请编辑 vCenter 集群中的 vSAN 常规设置，并选中加密复选框。

要使用 vSphere 加密，请编辑虚拟机存储策略以要求磁盘加密。

## 密钥轮换

使用 {{site.data.keyword.cloud_notm}} 控制台或 API 来[轮换 Key Protect 客户根密钥 (CRK)](/docs/services/key-protect/rotate-keys.html)。

对于 VMware vSAN 加密，请轮换 VMware 密钥的加密密钥 (KEK)，并可选择通过 vCenter 集群中的 vSAN 常规设置来轮换数据加密密钥 (DEK)。

对于 VMware vSphere 加密，请使用 **Set-VMEncryptionKey** PowerShell 命令来轮换 VMware KEK 和 DEK（可选）。

## 密钥撤销

您可以通过从 Key Protect 中删除所选 CRK 来撤销 KMIP for VMware 使用的所有密钥。

撤销密钥后，受这些密钥和 KMIP for VMware 实例保护的所有数据都会通过此方法以加密方式粉碎。ESXi 主机处于电源打开状态时，VMware 会保留一些密钥，因此您需要重新启动 vSphere 集群，以确保不再使用所有加密数据。
{:important}

KMIP for VMware 使用与 VMware 已知的密钥标识关联的名称，将各个包装的 KEK 存储在 Key Protect 实例中。您可以删除单个密钥，以撤销单个磁盘或驱动器的加密。

从清单中除去具有加密磁盘的 VM 时，VMware 不会从 KMS 中删除密钥。这是为了允许从备份恢复该 VM，或者在将其还原到清单的情况下这样做。如果您希望回收这些密钥并以加密方式使所有备份失效，您需要在删除 VM 后，从 Key Protect 中删除密钥。
{:note}

### 相关链接

* [解决方案概述](/docs/services/vmwaresolutions/archiref/kmip/overview.html)
* [解决方案设计](/docs/services/vmwaresolutions/archiref/kmip/design.html)
* [IBM Key Protect](/docs/services/key-protect/index.html)
