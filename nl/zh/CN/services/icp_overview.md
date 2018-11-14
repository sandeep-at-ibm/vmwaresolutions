---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Private Hosted 概述

{{site.data.keyword.cloud}} Private Hosted 服务会自动在 VMware vCenter Server 实例上部署 {{site.data.keyword.cloud_notm}} Private Hosted。此服务会将微服务和容器的强大功能引入到 {{site.data.keyword.cloud_notm}} 上的 VMware 环境中。使用此服务，可以将内部部署中您熟悉的 VMware 和 {{site.data.keyword.cloud_notm}} Private 操作模型和工具扩展到 {{site.data.keyword.cloud_notm}} 中。

此服务可用于：
* 部署在或已升级到 V2.5 和更高版本的 vCenter Server 实例
* 部署在或已升级到 V2.7 和更高版本的 vCenter Server with Hybridity Bundle 实例
{:note}

## IBM Cloud Private Hosted 的技术规范

下表列出了为**生产就绪**环境和**开发/测试**环境订购 IBM Cloud Private Hosted 服务的最低需求。

表 1. 生产就绪环境和开发/测试环境的最低需求

|环境|核心数|内存|主机|存储|
|:---------- |:---- |:------ |:---- |:------- |
|生产就绪|52|640|3|8000|
|开发/测试|30|200|3|4000|

### IBM Cloud Private Hosted 的资源需求

以下各表列出了 {{site.data.keyword.cloud_notm}} Private Hosted 服务在生产就绪环境和开发/测试环境中的资源需求。

表 2. {{site.data.keyword.cloud_notm}} Private Hosted 在生产就绪环境中的资源需求

|节点类型|CPU 核心数|内存 (GB)|磁盘 1 (GB)|磁盘 2 (GB)|VM 数|
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
|引导|8|16|100|1|1|   
|管理|8| 64 |500|3|3|
|主节点|8| 64 |200|3|3|  
|代理|2|4|150|3|3|
|工作程序|4|16|200|300|6|
|漏洞顾问程序|8|16|500|3|3|
|GlusterFS|8|16|150|50|3|
|引导程序 ICP/CAM |16| 32 |250|1|1|
|NFS 服务器|8|4|350|1|1|
|Edge|2|1|0.5|0.5|2|
|总计|162|642|6401|1951|26|
|记录的约束|52|640|  |8000|   |
|   |比率 1:3|比率 1:1|  |比率 1:1|  |

表 3. {{site.data.keyword.cloud_notm}} Private Hosted 在开发/测试环境中的资源需求

|节点类型|CPU 核心数|内存 (GB)|磁盘 1 (GB)|磁盘 2 (GB)|VM 数|
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
|引导|8|16|100|1|1|   
|管理|8|16|150|1|1|
|主节点|8|16|200|1|1|  
|代理|2|4|150|1|1|
|工作程序|4|16|200|300|3|
|漏洞顾问程序|8|16|150|1|1|
|GlusterFS|8|16|150|50|3|
|引导程序 ICP/CAM |16| 32 |250|1|1|
|NFS 服务器|8|4|350|1|1|
|Edge|1|0.5|0.5|2|2|
|总计|96|201|2401|1050|15|
|记录的约束|30|200|  |4000|  |
|  |比率 1:3|比率 1:1|  |比率 1:1|  |

### 用于计算 IBM Cloud Private Hosted 空间需求的公式

以下公式用于计算 IBM Cloud Private 的空间需求和管理开销。

公式 1：`AvailableCores = [ HostCoreCount - HostOverheadCores - ( HostVSanOverheadCorePercentage * HostCoreCount) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadCores`

表 4. 公式 1 中变量的描述

|变量|描述|	单位|	vSAN 示例|NFS 示例|
|:--------- |:----------- |:---- |:------------- |:----------- |
|AvailableCores|	可用于环境中的工作负载和服务的实际核心数|	核心|	38|43|
|HostCount|缺省集群中的主机数|主机|4|4|
|HostCoreCount|缺省集群内每个主机中的可用原始核心数|	核心|	16|16|
|HostOverheadCores|ESXi 服务器保留为开销的核心数，值为 0.1 个核心|核心|0.1|	0.1|
|MgmtOverheadCores|vCenter Server 管理组件（vCenter Server、PSC、AD/DNS 和 Edge）保留的核心数，值为 5 个核心|核心|5| 5 |
|vSphereHAHostTolerance|	vSphere HA 配置中容许的主机数，值为 1 个主机|	主机|1|1|
|HostVsanOverheadCorePercentage|vSAN 利用的主机核心的百分比，值为 10% 或 0%（如果是非 vSAN 主机）| % |10%|	0%|

公式 2：`AvailableMemory = [ HostMemory - HostOverheadMemory - HostVsanOverheadMemory - ( HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadMemory`

表 5. 公式 2 中变量的描述

|变量|描述|	单位|	vSAN 示例|NFS 示例|
|:--------- |:----------- |:---- |:------------- |:----------- |
|AvailableMemory|可用于环境中的工作负载和服务的内存 GB 数|GB| 	693|860|
|HostCount|缺省集群中的主机数|主机数|6|6|
|HostMemory|	缺省集群内每个主机中的可用内存原始 GB 数|	GB|192|	192|
|HostVsanCapacityDiskSize|此主机上每个 vSAN 容量 SSD 磁盘容量的 GB 数，值为 960、1946 或 3891；如果是非 vSAN，值为 0 GB|GB|	960|0|
|HostOverheadMemory|	ESXi 服务器保留为开销的内存 GB 数，值为 4.6 GB|	GB|4.6|	4.6|
|MgmtOverheadMemory|	vCenter Server 管理组件（vCenter Server、PSC、AD/DNS 和 Edge）保留的内存 GB 数，值为 77 GB|GB|77|77|
|vSphereHAHostTolerance|vSphere HA 配置中容许的主机数，值为 1 个主机|主机|1|1|
|HostVsanOverheadMemoryDiskPercentage|vSAN 管理保留的内存 GB 数（以其中一个容量 vSAN 磁盘的百分比表示）, 值为 2.75%|	% |2.75%|2.75%|
|HostVsanOverheadMemory|vSAN 管理保留的内存 GB 数（不考虑磁盘大小），值为 7 GB 或 0 GB（如果是非 vSAN）|GB|7|0|

## 安装 IBM Cloud Private Hosted 时的注意事项

安装 {{site.data.keyword.cloud_notm}} Private Hosted 服务之前，请收集必需的许可证。建议您确保许可证不仅可以支持初始 {{site.data.keyword.cloud_notm}} Private Hosted 部署，还支持未来在基础架构中扩展 {{site.data.keyword.cloud_notm}} Private Hosted 的大小。

## 除去 IBM Cloud Private Hosted 时的注意事项

* {{site.data.keyword.cloud_notm}} 仅删除初始安装 {{site.data.keyword.cloud_notm}} Private Hosted 服务期间部署的虚拟机 (VM)。不会清除任何安装后部署的节点。
* {{site.data.keyword.cloud_notm}} 将删除在初始部署 {{site.data.keyword.cloud_notm}} Private Hosted 服务期间创建的 VXLAN、DLR 和 Edge 网关。启动除去 {{site.data.keyword.cloud_notm}} Private Hosted 服务的操作后，在 VXLAN 上部署的 VM 将断开连接。

### 相关链接

* [订购 IBM Cloud Private Hosted](../services/icp_ordering.html)
* [IBM Cloud Private Hosted](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf)（PDF 下载）
* [开具有关 IBM Cloud Private 的凭单](https://www.ibm.com/mysupport/s/?language=en_US)
