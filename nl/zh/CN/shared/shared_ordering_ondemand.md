---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购 Shared - 随需应变
{: #shared_ordering_ondemand}

{{site.data.keyword.vmwaresolutions_full}} Shared 作为试验性产品提供。
{:note}

为了实现随需应变，虚拟数据中心的 vCPU 和 RAM 根据需要进行分配，并且执行分配所需时间可能有所不同，具体取决于虚拟数据中心 vCPU 和 RAM 使用量的全局使用情况。
* 为 vCPU 和 RAM 量确定的限制是可随时使用的最大值。
* vCPU 和 RAM 资源可在以后根据需要增加和减少。
* 成本按小时计算，并基于虚拟数据中心内的资源使用情况。
* 可以在虚拟数据中心内分配和使用的存储量没有限制。费用将根据分配的存储量 (GB) 按小时收取。
* 入站和出站公用联网量没有限制。公共带宽按 GB 收费。

## IBM Cloud for VMware Solutions Shared 的需求
{: #shared_ordering_ondemand-req}

### IBM Cloud 基础架构帐户
{: #shared_ordering_ondemand-account-req}

要使用 {{site.data.keyword.vmwaresolutions_short}} 订购 IBM Cloud for VMware Solutions Shared，您必须具有**现收现付**或**预订** {{site.data.keyword.cloud_notm}} 帐户。订购的资源的成本将计入到该 {{site.data.keyword.cloud_notm}} 帐户。

### 虚拟数据中心名称需求
{: #shared_ordering_ondemand-vdc-name-req}

虚拟数据中心名称*应该*满足以下需求。命名需求在未来将强制实施。
* 只允许使用小写字母、数字和短划线 (-) 字符。
* 名称必须以小写字母字符开头。
* 名称必须以小写字母或数字字符结尾。
* 虚拟数据中心名称的最大长度为 10 个字符。
* 虚拟数据中心名称在您的帐户中必须唯一。

## 订购“Shared - 随需应变”的过程
{: #shared_ordering_ondemand-procedure}

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格中的 **VMware** 图标，然后单击 **VMware 虚拟数据中心**部分中的 **IBM Cloud for VMware Solutions Shared** 卡。
2. 在 **IBM Cloud for VMware Solutions Shared** 页面上，单击**随需应变**卡，然后单击**创建**。
3. 在 **IBM Cloud for VMware Solutions Shared - 随需应变**页面上，输入虚拟数据中心名称。已预先选择提供该产品的 {{site.data.keyword.CloudDataCent_notm}}。
4. 根据需求选择 vCPU 和 RAM 限制。
5. 在**订单摘要**窗格上，验证配置和估算成本，然后再下订单。
6. 单击**供应**。

## 订购“Shared - 随需应变”后的结果
{: #shared_ordering_ondemand-results}

* 资源部署会自动启动，并且您将收到确认，指示正在处理订单。通过查看**虚拟数据中心状态**部分，可以检查部署状态，包括可能需要注意的任何问题。
* 成功部署资源后，[{{site.data.keyword.cloud_notm}} for VMware Solutions Shared 的技术规范](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs)中描述的组件已安装在 VMware 虚拟平台上。
* 资源准备就绪可供使用后，其状态会更改为**可供使用**。

## 相关链接
{: #shared_ordering_ondemand-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [订购 Shared - 保留](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [管理 {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
