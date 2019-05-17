---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购 Zerto on IBM Cloud
{: #zerto_ordering}

订购 Zerto on {{site.data.keyword.cloud}} 服务时，可订购包含此服务的新实例，也可通过向现有实例添加此服务来进行订购。

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

如果将 Zerto for {{site.data.keyword.cloud_notm}} 添加到具有处于维护模式的 ESXi 服务器的 vCenter Server 实例中，那么您必须使用 Zerto Virtual Manager (ZVM) 控制台和预填充的 Zerto Virtual Replication Appliance (VRA) IP 地址来手动部署 VRA 虚拟机 (VM)。
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
