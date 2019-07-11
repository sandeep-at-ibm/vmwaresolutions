---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购 Zerto on IBM Cloud
{: #zerto_ordering}

订购 Zerto on {{site.data.keyword.cloud}} 服务时，可订购包含此服务的新实例，也可通过向现有实例添加此服务来进行订购。

## 针对 Zerto 复制的计费
{: #zerto_ordering-billing}

使用 Zerto 复制的 VM 按 Zerto 和 {{site.data.keyword.cloud_notm}} 计量。此使用量的帐单将通过 {{site.data.keyword.cloud_notm}} 计费帐户（而不是 {{site.data.keyword.cloud_notm}} 基础架构帐户）收费。

在订购 Zerto on {{site.data.keyword.cloud_notm}} 之前，请确保您的 {{site.data.keyword.cloud_notm}} 帐户是计费帐户，并且该帐户已链接到部署实例的 {{site.data.keyword.cloud_notm}} 基础架构帐户。 

如果您有来自 V3.0 或更低版本的 Zerto on {{site.data.keyword.cloud_notm}} 安装，那么您的 VM 复制成本仍将使用 {{site.data.keyword.cloud_notm}} 基础架构计费来进行计算。如果您的帐户和计费设置满足先前列出的需求，那么可以将 Zerto 计费方法转换为可计费。

在 {{site.data.keyword.vmwaresolutions_short}} 控制台上，系统会提示您将 {{site.data.keyword.cloud_notm}} 基础架构套餐转换为计费套餐，并根据需要将 {{site.data.keyword.cloud_notm}} 帐户升级到计费帐户。

* 有关免费和计费帐户的信息，请参阅[帐户类型](/docs/account?topic=account-accounts)。
* 有关升级到计费帐户的信息，请参阅[升级帐户](/docs/account?topic=account-upgrading-account)。
* 有关链接 {{site.data.keyword.cloud_notm}} 和 {{site.data.keyword.cloud_notm}} 基础架构帐户的信息，请参阅[切换到 IBM 标识和链接帐户](/docs/account?topic=account-unifyingaccounts)。

## 为新实例订购 Zerto on IBM Cloud
{: #zerto_ordering-new}

可以使用下列其中一种方法订购包含 Zerto on {{site.data.keyword.cloud_notm}} 的新实例：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，订购新实例时，请在**服务**部分中选择 **Zerto on IBM Cloud**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **Zerto on IBM Cloud**，指定服务设置，然后选择**添加到新实例**。

## 为现有实例订购 Zerto on IBM Cloud
{: #zerto_ordering-existing}

可以使用下列其中一种方法将 Zerto on {{site.data.keyword.cloud_notm}} 服务添加到现有实例中：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **Zerto on IBM Cloud**，指定服务设置，然后选择**添加到现有实例**。

如果将 Zerto on {{site.data.keyword.cloud_notm}} 添加到具有处于维护模式的 ESXi 服务器的 vCenter Server 实例中，那么您必须使用 Zerto Virtual Manager (ZVM) 控制台和预填充的 Zerto Virtual Replication Appliance (VRA) IP 地址来手动部署 VRA 虚拟机 (VM)。
{:note}

## 为仅专用实例订购 Zerto on IBM Cloud
{: #zerto_ordering-private-only}

如果要将 Zerto on {{site.data.keyword.cloud_notm}} 添加到仅专用实例，请确保满足以下需求：
* 您负责设置自己的代理服务器以连接到因特网。有关更多信息，请参阅[公用网络连接](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity)。
* 您还必须为 Zerto 配置“回拨”功能。有关 Zerto“回拨”的更多信息，请参阅 [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window}。

## 相关链接
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [管理 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [请求 Zerto on {{site.data.keyword.cloud_notm}} 的受管服务](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com Web 站点](https://www.zerto.com){:new_window}
* [Zerto 技术文档](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
