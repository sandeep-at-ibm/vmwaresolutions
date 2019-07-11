---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: Hytrust KeyControl, Hytrust configuration, order Hytrust

subcollection: vmware-solutions


---

# 订购 HyTrust KeyControl on IBM Cloud
{: #htkc_ordering}

订购 HyTrust KeyControl on {{site.data.keyword.cloud}} 服务时，可订购包含 HyTrust KeyControl 设备 HA 对的新实例，也可通过向现有实例添加 HyTrust KeyControl 设备来进行订购。

## 为新实例订购 HyTrust KeyControl on IBM Cloud
{: #htkc_ordering-new}

可以使用下列其中一种方法订购包含 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 的新实例：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，订购新实例时，请在**服务**部分中选择 **HyTrust KeyControl on IBM Cloud**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **HyTrust KeyControl on IBM Cloud**，指定服务设置，然后选择**添加到新实例**。

## 为现有实例订购 HyTrust KeyControl on IBM Cloud
{: #htkc_ordering-existing}

可以使用下列其中一种方法将 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服务添加到现有实例中：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **HyTrust KeyControl on IBM Cloud**，指定服务设置，然后选择**添加到现有实例**。

## HyTrust KeyControl on IBM Cloud 服务配置
{: #htkc_ordering-config}

订购此服务时，请提供以下设置。

指定是否要创建双节点高可用性 KeyControl 集群：
* 如果选择此选项，将部署两个 KeyControl 节点，并创建新的主动/主动高可用性集群。这是缺省选项。
* 如果未选择此选项，将部署两个独立的 KeyControl 节点，而不创建集群。部署后，可以对独立节点手动建立集群，或将其添加到现有 KeyControl 集群。

## 相关链接
{: #htkc_ordering-related}

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [管理 HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Web 站点](https://www.hytrust.com/)
