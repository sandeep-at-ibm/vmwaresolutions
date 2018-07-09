---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# 管理 IBM Spectrum Protect Plus on IBM Cloud

## 访问 IBM Spectrum Protect Plus 管理控制台

要管理 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} 服务，必须通过完成以下步骤来访问 IBM Spectrum Protect Plus 管理控制台：
1. 使用 {{site.data.keyword.cloud_notm}} 基础架构 VPN 或跳跃服务器来允许访问 IBM Spectrum Protect Plus 虚拟机 (VM) 的 IP 地址。可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台的 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的服务详细信息页面上找到该 IP 地址。
2. 要访问 IBM Spectrum Protect Plus 管理控制台，请单击 IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} 的服务详细信息页面上的**查看 IBM Spectrum Protect Plus 控制台**，然后使用相同的服务详细信息页面上列出的凭证进行登录。

## 对 IBM Spectrum Protect Plus on IBM Cloud 应用更新

您负责维护 IBM Spectrum Protect Plus，以使其保持更新为最新版本。可以从 [IBM Spectrum Protect Plus 支持](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus)页面中下载必需的更新。

有关更多信息，请参阅以下主题：
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)

## 更新 IBM Spectrum Protect Plus VM 的操作系统

要更新 IBM Spectrum Protect Plus VM 的操作系统，您必须以 **root** 用户身份登录。**root** 用户密码与 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的服务详细信息页面中的密码相同。

## 备份和复原安装了 IBM Spectrum Protect Plus on IBM Cloud 的实例的管理组件

**注**：以下信息适用于部署在（或已升级到）V2.3 或更高版本中的实例上的 IBM Spectrum Protect Plus 安装。对于 V2.2 实例，此服务仅为工作负载 VM 提供数据保护。

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务已预配置一个自动运行的管理备份作业。此作业每天运行，备份以下管理组件，最多可有 7 个复原点：
* VMware vCenter Server
* Platform Services Controller (PSC)
* IBM CloudDriver
* **仅限 Cloud Foundation 实例**：VMware SDDC Manager
* **仅限具有 HA AD/DNS 的 vCenter Server 实例**：AD/DNS 的高可用性对

如果管理组件发生故障，可以通过[联系 IBM 支持](../vmonic/trbl_support.html)来开具凭单，以请求将管理组件复原到先前的备份。

## 相关链接

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 概述](spp_considerations.html)
* [部署后如何增大 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的 VSNAP 存储](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [IBM Spectrum Protect Plus 文档](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
