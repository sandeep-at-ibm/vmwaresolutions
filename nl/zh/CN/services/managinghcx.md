---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HCX updates, HCX management console, login HCX console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}


# 管理 VMware HCX on IBM Cloud
{: #managinghcx}

## 访问 HCX on IBM Cloud 管理控制台
{: #managinghcx-accessing-consoles}

要管理 HCX on {{site.data.keyword.cloud}} 服务，必须访问 HCX 云控制台或 HCX Manager 管理控制台：
1. 使用 {{site.data.keyword.cloud_notm}} 基础架构 VPN 或跳板机来允许访问 HCX Manager 虚拟设备 (HCX Manager) 的 IP 地址。可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台上 HCX on {{site.data.keyword.cloud_notm}} 服务详细信息页面中找到该 IP 地址。
2. 要访问 HCX 云控制台，请单击 HCX on {{site.data.keyword.cloud_notm}} 服务详细信息页面上的**查看 HCX 云控制台**，然后使用 vCenter Server 凭证登录。
3. 要访问 HCX Manager 管理控制台，请单击 HCX on {{site.data.keyword.cloud_notm}} 服务详细信息页面上的**查看 HCX Manager 管理控制台**，然后使用此服务详细信息页面上列出的 HCX Manager 凭证进行登录。

有关更多信息，请参阅[订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)。

## 对 HCX on IBM Cloud 应用更新
{: #managinghcx-updates}

HCX on {{site.data.keyword.cloud_notm}} 通过 VMware Hybrid Cloud Extension 技术的最新测试构建进行部署。VMware 将定期提供这些构建的更新，包括重要修订和新功能。这些构建会自动推送到 HCX on {{site.data.keyword.cloud}} 安装，包括内部部署 HCX 安装。

要应用已推送到环境的任何维护修订，您必须使用内部部署数据中心内的 HCX Manager 管理控制台以及 vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 实例。

如果看不到所需的构建更新、使用 HCX 时遇到问题，或者希望立即将最新的 HCX 构建推送到系统，请按照[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)中的步骤来开具支持凭单。

## 相关链接
{: #managinghcx-related}

* [HCX on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [HCX 术语的词汇表](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [VMware Hybrid Cloud Extension 概述](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension 文档](https://cloud.vmware.com/vmware-hcx/resources){:external}
