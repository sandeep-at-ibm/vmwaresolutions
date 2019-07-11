---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Caveonix console, Caveonix RiskForesight license, login Caveonix console

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix}

## 访问 Caveonix RiskForesight 控制台
{: #managingcaveonix-access-console}

要管理 Caveonix RiskForesight on {{site.data.keyword.cloud}} 服务，您必须通过完成以下步骤来访问 Caveonix RiskForesight 控制台：

1. 使用 IBM Cloud 基础架构 VPN 或跳板机来允许访问 Caveonix RiskForesight 虚拟机 (VM) 的 IP 地址。可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台上 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 的服务详细信息页面中找到该 IP 地址。具体步骤如下：
   1. 在 {{site.data.keyword.cloud_notm}} 基础架构客户门户网站中创建 VPN 密码。
   2. 使用 {{site.data.keyword.cloud_notm}} 基础架构 VPN 凭证，登录到数据中心 VPN 门户网站。
   3. 从本地计算机将 IP 地址和主机名映射添加到 `hosts` 文件中。使用以下格式：

      ```javascript
      RiskForesight_VM_IP_Address      RiskForesight_FQDN
      ```
2. 要访问 Caveonix RiskForesight 控制台，请单击 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 的服务详细信息页面上的**查看 RiskForesight 控制台**，然后使用此服务详细信息页面上列出的凭证进行登录。

## 对 Caveonix RiskForesight on IBM Cloud 应用更新 
{: #managingcaveonix-update}

您应负责维护 Caveonix RiskForesight，以使其保持更新为最新版本。您可以从 [Caveonix Service Provider Portal](https://support.caveonix.com) 下载所需的更新。

## 更新 Caveonix RiskForesight 许可证

Caveonix RiskForesight 许可证有效期为 1 年。Caveonix RiskForesight 许可证到期时，您可以使用以下过程来进行更新：
1. 订购新的 Caveonix RiskForesight 许可证并将其复制到 Caveonix RiskForesight 控制台。有关更多信息，请参阅[订购 Caveonix RiskForesight 许可证的过程](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure)。
2. 从 {{site.data.keyword.vmwaresolutions_short}} 控制台的 **Caveonix RiskForesight Licenses** 表中删除到期的许可证。有关更多信息，请参阅[删除 Caveonix RiskForesight 许可证的过程](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete)。

## 相关链接
{: #managingcaveonix-related}

* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [订购 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
