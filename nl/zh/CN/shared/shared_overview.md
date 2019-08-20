---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: vmware solutions shared, get started shared, tech specs shared

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud for VMware Solutions Shared 概述
{: #shared_overview}

{{site.data.keyword.vmwaresolutions_full}} Shared 作为试验性产品提供。
{:note}

通过 VMware 虚拟数据中心，您可以快速、无缝地将 VMware 工作负载迁移或部署到基于专业管理的 VMware 基础架构的云。IBM 提供了一个自助服务的随需应变 VMware 云计算平台，其中 vCloud Director 在 {{site.data.keyword.cloud_notm}} 上运行。此基础架构即服务 (IaaS) 现收现付产品支持用户根据需要使用特定 vCPU、存储器、vRAM、网络和 IP。

{{site.data.keyword.vmwaresolutions_short}} 有三种“基础架构即服务”(IaaS) 预订服务类型：
- 多租户保留虚拟数据中心
- 多租户现收现付虚拟数据中心
- 单租户专用虚拟数据中心

客户可使用 {{site.data.keyword.vmwaresolutions_short}} 产品来管理虚拟数据中心的生命周期。无论使用 Web UI 还是公共 API，都支持以下功能：
- 创建虚拟数据中心
- 虚拟数据中心弹性
- 删除虚拟数据中心
- 添加和除去 VMware 服务
- 随需应变 Windows 许可
- 随需应变 Red Hat 许可

所有这三种 {{site.data.keyword.cloud_notm}} 虚拟数据中心产品都标配 NSX Edge 服务网关上的五个公共 IP 地址，支持通过公用网络进行无限制流入。

虚拟数据中心针对以下组件收取费用：
- 基于存储性能的分层定价的存储器分配
- 虚拟 CPU 使用量
- 虚拟内存使用量
- 公用联网上的流出量
- 使用的商用操作系统许可证
- 可选 VMware 服务

## IBM Cloud for VMware Solutions Shared 体系结构
{: #shared_overview-archi}

下图描绘了 {{site.data.keyword.vmwaresolutions_short}} Shared 部署的高级别体系结构和组件。

![{{site.data.keyword.vmwaresolutions_short}} Shared 体系结构](../images/vclouddirector-architecture-public.svg "{{site.data.keyword.vmwaresolutions_short}} Shared 体系结构")

### VMware vCloud Director
{: #shared_overview-vcloud-dir}

此层表示管理接口。VMware® vCloud Director 支持对基于 Web 的租户门户网站进行基于角色的访问，允许组织成员与组织的资源交互，以创建和使用 vApp 和虚拟机 (VM)。

### 组织
{: #shared_overview-org}

组织是用户、组和计算资源集合的管理单元。用户在组织级别进行认证，提供的是创建或导入用户时由组织管理员建立的凭证。组织管理员负责管理组织用户、组和目录。

### 用户和策略
{: #shared_overview-users-policies}

组织可以包含任意数量的用户和组。用户可以由组织管理员在本地创建，也可以通过目录服务（如 LDAP）导入。组织中的许可权通过向用户和组分配权限和角色进行控制。

### 目录
{: #shared_overview-cat}

组织使用目录来存储 vApp 模板和媒体文件。有权访问目录的组织成员可以使用目录的 vApp 模板和媒体文件来创建自己的 vApp。组织管理员可以将公共目录中的项复制到自己的组织目录。

### 虚拟数据中心
{: #shared_overview-vc}

组织虚拟数据中心为组织提供资源。虚拟数据中心提供了可以存储、部署和操作虚拟系统的环境。虚拟数据中心还可为虚拟 CD 和 DVD 介质提供存储。一个组织可以有多个虚拟数据中心。

![{{site.data.keyword.cloud_notm}} 的虚拟数据中心体系结构](../images/virtual-datacenter-architecture-public.svg "{{site.data.keyword.cloud_notm}} 的虚拟数据中心体系结构")

## IBM Cloud for VMware Solutions Shared 的技术规范
{: #shared_overview-specs}

{{site.data.keyword.cloud_notm}} 中包含以下组件：

### 计算
{: #shared_overview-specs-comp}

计算处理以虚拟 CPU (vCPU) 为增量分配给虚拟数据中心。每个 vCPU 增量表示一个 2.0 GHz 核心。计算内存以 GB 为增量进行分配。

### 联网
{: #shared_overview-specs-net}

缺省情况下，每个虚拟数据中心都配置有一个边缘网关，该网关具有五个公共 IP 地址和一个专用服务 IP 地址。边缘网关可供客户配置，因此可以进行定制。

公共地址可用于面向公众的 vApp，以处理入站或出站公用因特网流量。

服务地址可用于访问 IBM Cloud 内部专用网络上的 IBM Cloud 基础架构服务，包括以下服务：
- NTP
- Windows 操作系统许可和更新
- Red Hat 操作系统许可和更新
- Cloud Object Storage

### 存储
{: #shared_overview-specs-storage}

创建或部署 vApp 或 VM 时，将选择存储策略。有 4 个不同的存储层可用，具体取决于所需的存储性能：

- NFS（白金级）：此存储层的最大吞吐量为 10 IOPS/GB，性能最高
- NFS（黄金级）：此存储层的最大吞吐量为 4 IOPS/GB
- NFS（白银级）：此存储层的最大吞吐量为 2 IOPS/GB
- NFS（青铜级）：此存储层的最大吞吐量为 0.25 IOPS/GB

## 相关链接
{: #shared_overview-related}

* [订购 Shared - 随需应变](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [订购 Shared - 保留](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [管理 {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-74C9E10D-9197-43B0-B469-126FFBCB5121.html){:external}
