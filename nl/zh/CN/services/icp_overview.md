---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-29"

keywords: IBM Cloud Private, ICP, tech specs ICP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Private Hosted 概述
{: #icp_overview}

{{site.data.keyword.cloud}} Private Hosted 服务会自动在 VMware vCenter Server 实例上部署 {{site.data.keyword.cloud_notm}} Private Hosted 和 {{site.data.keyword.cloud_notm}} Automation Manager。此服务会将微服务和容器的强大功能引入到 {{site.data.keyword.cloud_notm}} 上的 VMware 环境中。使用此服务，可以将内部部署中您熟悉的 VMware 和 {{site.data.keyword.cloud_notm}} Private 操作模型和工具扩展到 {{site.data.keyword.cloud_notm}} 中。

此服务可供以下实例使用：
* 部署在（或已升级到）V2.7 和更高版本的 vCenter Server with Hybridity Bundle 实例
* 部署在（或已升级到）V2.5 和更高版本的 vCenter Server 实例

当前安装的 IBM Cloud Private 版本为 3.1.2。{{site.data.keyword.cloud_notm}} Automation Manager 还会作为 {{site.data.keyword.cloud}} Private Hosted 服务订单的一部分进行部署。
{:note}

## IBM Cloud Private Hosted 的技术规范
{: #icp_overview-specs}

下表列出了为**生产就绪**环境和**开发/测试**环境订购 IBM Cloud Private Hosted 服务的最低需求。

|环境|核心数|内存 (GB)|主机数|存储器 (GB) |
|:---------- |:---- |:------ |:---- |:------- |
|生产就绪|52|640|3|8,000|
|开发/测试|30|200|3|4,000|
{: caption="表 1. 生产就绪环境和开发/测试环境的最低需求" caption-side="top"}

### IBM Cloud Private Hosted 的资源需求
{: #icp_overview-resource-req}

下表列出了 {{site.data.keyword.cloud_notm}} Private Hosted 服务在生产就绪环境中的资源需求。

|节点类型|CPU 核心数|内存 (GB)|磁盘 1 (GB)|磁盘 2 (GB)|VM 数|
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
|引导| 12 |24|100|1|1|   
|管理|8| 64 |500|3|3|
|主节点|8| 64 |200|3|3|  
|代理|2|4|150|3|3|
|工作程序|4|16|200|300|6|
|漏洞顾问程序|8|16|500|1|1|
|GlusterFS|8|16|150|50|3|
|NFS 服务器|8|4|350|1|1|
|NSX Edge 服务网关|2|1|0.5|0.5|2|
|记录的约束|52|640|  |8,000|   |
{: caption="表 2. 生产就绪环境" caption-side="top"}

下表列出了 {{site.data.keyword.cloud_notm}} Private Hosted 服务在开发和测试环境中的资源需求。

|节点类型|CPU 核心数|内存 (GB)|磁盘 1 (GB)|磁盘 2 (GB)|VM 数|
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
|引导| 12 |24|100|1|1|   
|管理|8|16|150|1|1|
|主节点|8|16|200|1|1|  
|代理|2|4|150|1|1|
|工作程序|4|16|200|300|3|
|漏洞顾问程序|8|16|150|1|1|
|GlusterFS|8|16|150|50|3|
|NFS 服务器|8|4|350|1|1|
|NSX Edge 服务网关|2|1|0.5|0.5|2|
|记录的约束|30|200|  |4,000|  |
{: caption="表 3. {{site.data.keyword.cloud_notm}} 开发和测试环境" caption-side="top"}

### 用于计算 IBM Cloud Private Hosted 空间需求的公式
{: #icp_overview-formulas}

以下公式用于计算 IBM Cloud Private 的空间需求和管理开销。

#### 计算可用核心数的公式
{: #icp_overview-formulas-1}

下表列出了公式 1 中的变量：

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

|变量|描述|单位|vSAN 示例|NFS 示例|
|:--------- |:----------- |:---- |:------------- |:----------- |
|AvailableCores|可用于环境中的工作负载和服务的实际核心数|核心数|38|43|
|HostCount|缺省集群中的主机数|主机数|4|4|
|HostCoreCount|缺省集群内每个主机中的可用原始核心数|核心数|16|16|
|HostOverheadCores|ESXi 服务器保留为开销的核心数，值为 0.1 个核心|核心数|0.1|0.1|
|MgmtOverheadCores|vCenter Server 管理组件（vCenter Server、PSC、AD/DNS 和 Edge）保留的核心数，值为 5 个核心|核心数| 5 | 5 |
|vSphereHAHostTolerance|vSphere HA 配置中容许的主机数，值为 1 个主机|	主机数|1|1|
|HostVsanOverheadCorePercentage|vSAN 使用的主机核心的百分比，值为 10%，如果是非 vSAN 主机，值为 0%| % |10%|0%|
{: caption="表 4. 公式 1 中变量的描述" caption-side="top"}

#### 计算可用内存的公式
{: #icp_overview-formulas-2}

下表列出了公式 2 中的变量：

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

|变量|描述|单位|vSAN 示例|NFS 示例|
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory |可用于环境中的工作负载和服务的内存 GB 数|GB| 693 |860|
|HostCount|缺省集群中的主机数|主机数|6|6|
|HostMemory|缺省集群内每个主机中的可用内存原始 GB 数|GB|192|192|
|HostVsanCapacityDiskSize|此主机上每个 vSAN 容量 SSD 磁盘容量的 GB 数，值为 960、1,946 或 3,891；如果是非 vSAN 主机，值为 0 GB|GB|960|0|
|HostOverheadMemory|ESXi 服务器保留为开销的内存 GB 数，值为 4.6 GB|GB|4.6|4.6|
|MgmtOverheadMemory|vCenter Server 管理组件（vCenter Server、PSC、AD/DNS 和 Edge）保留的内存 GB 数，值为 77 GB|GB|77|77|
|vSphereHAHostTolerance|vSphere HA 配置中容许的主机数，值为 1 个主机|主机数|1|1|
|HostVsanOverheadMemoryDiskPercentage|vSAN 管理保留的内存 GB 数（以其中一个容量 vSAN 磁盘的百分比表示）, 值为 2.75%| % |2.75%|2.75%|
|HostVsanOverheadMemory|vSAN 管理保留的内存 GB 数（不考虑磁盘大小），值为 7 GB，如果是非 vSAN 主机，值为 0 GB|GB|7|0|
{: caption="表 5. 公式 2 中变量的描述" caption-side="top"}

## 安装 IBM Cloud Private Hosted 时的注意事项
{: #icp_overview-install}

* 安装 {{site.data.keyword.cloud_notm}} Private Hosted 服务之前，请收集必需的许可证。这包括 {{site.data.keyword.cloud_notm}} Private 和 {{site.data.keyword.cloud_notm}} Automation Manager 许可证。确保许可证不仅支持初始服务部署，还支持未来在基础架构中扩展大小。
* 对于生产就绪型环境中的 {{site.data.keyword.cloud_notm}} Private Hosted 部署，不支持每个主机 64 GB RAM。因此，必须为 **RAM** 选择高于 64 GB 的选项。
* 在环境中安装 {{site.data.keyword.cloud_notm}} Private Hosted 服务之前，会针对环境中缺省集群的可用容量执行检查，以确保服务组件能够适合在此环境中运行。如果容量检查失败，那么不会安装该服务，并且会在控制台上将该服务的状态设置为**容量验证失败**。此外，还会显示一条包含更多详细信息的控制台消息，并且会通过电子邮件通知您。要安装该服务，必须通过添加更多主机或者释放 RAM、CPU 或磁盘空间来增加缺省集群中的容量，然后在控制台中再次添加该服务。添加后，可以通过单击处于**容量验证失败**状态的现有服务旁边的**删除**图标来除去该服务。
* 如果要部署更多节点，请参阅[部署更多节点](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering-deploy-nodes#icp_ordering-deploy-nodes)。

## 除去 IBM Cloud Private Hosted 时的注意事项
{: #icp_overview-remove}

* 仅删除初始安装 {{site.data.keyword.cloud_notm}} Private Hosted 服务期间部署的虚拟机 (VM)。不会清除安装后部署的任何节点。
* {{site.data.keyword.cloud_notm}} 将删除在初始部署 {{site.data.keyword.cloud_notm}} Private Hosted 期间创建的 VXLAN、DLR 和 Edge 网关。启动除去 {{site.data.keyword.cloud_notm}} Private Hosted 服务的操作后，在 VXLAN 上部署的 VM 将断开连接。

## 相关链接
{: #icp_overview-related}

* [订购 {{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)
* [vCenter Server 和 {{site.data.keyword.cloud_notm}} Private 指南](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [开具有关 {{site.data.keyword.cloud_notm}} Private 的凭单](https://www.ibm.com/mysupport/s/?language=en_US){:external}
* [{{site.data.keyword.cloud_notm}} Automation Manager 许可](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/licensing.html){:external}
* [{{site.data.keyword.cloud_notm}} Automation Manager 组件](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_managed_components.html){:external}
