---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 基础架构管理设计

基础架构管理是指用于管理 VMware 基础架构的组件。此设计使用一个外部 Platform Services Controller (PSC) 实例和一个 vCenter Server 实例：
* vCenter Server 是用于管理 vSphere 环境的集中式平台，也是此解决方案中的其中一个基本组件。
* 在此解决方案中将使用 PSC 来提供一组基础架构服务，包括 VMware vCenter Single Sign On、许可服务、查找服务和 VMware Certificate Authority。

PSC 实例和 vCenter Server 实例是不同的虚拟机 (VM)。

## PSC 设计

此设计将一个外部 PSC 部署为与管理 VM 关联的专用 VLAN 上可移植子网中的虚拟设备。其缺省网关设置为后端客户路由器 (BCR)。虚拟设备使用下表中的规范进行配置。

这些值是在部署时设置的，无法更改。
{:note}

表 1. Platform Services Controller 规范

|属性|规范|
|------------------------------|--------------------------------|
|Platform Services Controller|虚拟设备|
|vCPU 数量|2|
|内存|4 GB |
|磁盘|本地 VMFS 数据存储上 114 GB|
|磁盘类型|自动精简配置|

位于主实例中的 PSC 分配有缺省 SSO 域 `vsphere.local`。

## vCenter Server 设计

vCenter Server 也部署为虚拟设备。此外，vCenter Server 将安装在与管理 VM 关联的专用 VLAN 上的可移植子网中。其缺省网关设置为该特定子网的 BCR 上分配的 IP 地址。虚拟设备使用下表中的规范进行配置。

表 2. vCenter Server Appliance 规范

|属性|规范|
|------------------------------|-------------------------------------|
|vCenter Server|虚拟设备|
|设备安装大小|中（最多 400 个主机，4000 个 VM）|
|Platform Services Controller|外部|
|vCPU 数量|8|
|内存|24 GB |
|磁盘|本地数据存储上 400 GB|
|磁盘类型|自动精简配置|

### vCenter Server 数据库

vCenter Server 配置使用设备随附的本地嵌入式 PostgreSQL 数据库。嵌入式数据库用于除去对外部数据库和许可的所有依赖关系。

### vCenter Server 集群规范

通过此设计，您可以对通过解决方案供应的 vSphere ESXi 主机建立集群。但是，会先创建一个数据中心对象（以表示 vSphere ESXi 主机的位置）以及该数据中心内的 pod，然后才能创建集群。创建数据中心对象后，会创建集群。集群部署时会启用 VMware vSphere 高可用性 (HA) 和 VMware vSphere 分布式资源调度程序 (DRS)。

### vSphere 分布式资源调度程序

此设计在初始集群中使用 vSphere 分布式资源安排 (DRS) 来对 VM 定位，并在其他集群中使用 DRS 来动态迁移 VM，以实现集群均衡。自动化级别设置为完全自动化，以便 vSphere 可自动运行初始定位和迁移建议。此外，迁移阈值设置为“中”，以便 vCenter 应用优先级为 1、2 和 3 的建议，从而在集群负载均衡方面至少实现适当改进。

此设计中未使用通过**分布式电源管理**功能进行的电源管理。
{:note}

### vSphere 高可用性

此设计在初始集群和额外集群中使用 vSphere 高可用性 (HA) 来检测计算故障，并恢复在集群内运行的 VM。此设计中的 vSphere HA 功能配置为在集群中同时启用**主机监视**和**许可控制**选项。此外，初始集群会将一个节点的资源保留为用于许可控制策略的备用容量。

日后扩展或收缩集群时，您应负责相应地调整许可控制策略。
{:note}

缺省情况下，**VM 重新启动优先级**选项设置为“中”，**主机隔离响应**选项处于禁用状态。此外，**VM 监视**处于禁用状态，并且**数据存储脉动信号传递**功能已配置为包含任何集群数据存储。此方法使用 NAS 数据存储（如果存在）。

## 自动化

这些解决方案的基石是自动化。自动化提供了以下优点：
* 降低部署的复杂性。
* 大幅缩短部署时间。
* 确保以一致的方式部署 VMware 实例。

{{site.data.keyword.IBM}} CloudBuilder、IBM CloudDriver 和 SDDC Manager VM 协同工作，以启动新的 VMware 实例并执行生命周期管理功能。

### IBM CloudBuilder 和 IBM CloudDriver

IBM CloudBuilder 和 IBM CloudDriver 虚拟服务器实例 (VSI) 是 IBM 开发的组件，您无法对其进行访问。
* IBM CloudBuilder 是临时的 {{site.data.keyword.cloud_notm}} 虚拟服务器实例 (VSI)，用于引导在供应的裸机 ESXi 主机中对解决方案组件的部署、配置和验证。
* 将部署 IBM CloudDriver VSI 以创建实例，然后根据需要定期部署操作（例如，部署更多节点、集群或服务）的最新 {{site.data.keyword.cloud_notm}} for VMware 代码。IBM CloudDriver 通过专用于管理实例而部署的 VMware NSX Edge 服务网关与 {{site.data.keyword.vmwaresolutions_short}} 控制台进行通信，并充当维护实例的代理程序。IBM CloudDriver 负责执行持续操作，例如将新的裸机主机添加到集群以及将附加组件服务部署到实例中。对于 Cloud Foundation 实例，IBM CloudDriver 会与 VMware SDDC Manager VM 进行通信，以执行添加主机和补丁安装等功能。

用户有可能删除或损坏 VM，如以下部分中所述。除去 VM、关闭 VM 或使其变为不可操作时，会中断 {{site.data.keyword.vmwaresolutions_short}} 控制台上的以下 Cloud Foundation 或 vCenter Server 操作：
* 查看实例或主机状态
* 添加或除去集群
* 添加或除去 ESXi 主机
* 添加或除去服务
* 补丁安装

### SDDC Manager

对于 Cloud Foundation 实例，SDDC Manager VM 是由 VMware 开发并维护的组件。在整个生命周期内，它始终作为实例的一部分。它负责实例的以下生命周期功能：
* 管理 VMware 组件：vCenter Server、Platform Services Controller (PSC)、vSAN 和 NSX，包括 IP 地址分配和主机名解析。
* 扩展和收缩集群中的 ESXi 主机，包括任何受影响的服务，例如 NSX VTEP、vSAN 和资源池。

对于 vCenter Server 实例，这些活动由 IBM CloudDriver 执行，因为没有 SDDC Manager。

### 自动化流程

以下过程描述了通过 {{site.data.keyword.vmwaresolutions_short}} 控制台订购 VMware 实例时的事件顺序：
1.  订购 VLAN 和子网以通过 {{site.data.keyword.cloud_notm}} 联网。
2.  订购安装了 vSphere Hypervisor 的 {{site.data.keyword.baremetal_short}}。
3.  （如果适用）订购 Microsoft Windows 虚拟服务器实例 (VSI)，以充当 Active Directory 域控制器。
4.  验证联网情况和部署的硬件。
5.  （如果适用）初始配置单节点 vSAN。
6.  （如果适用）部署并配置两个 Microsoft Windows 虚拟机，以充当 Active Directory 域控制器。
7.  部署并配置 vCenter、PSC 和 NSX。
8.  对剩余 ESXi 节点建立集群，扩展 vSAN（如果适用）以及配置 NSX 组件 (VTEP)。
9.  部署 VMware Cloud Foundation SDDC Manager VM（如果适用）和 IBM CloudDriver VSI。
10.  验证环境的安装和配置。
11. 除去 CloudBuilder VSI。
12. 部署可选服务，例如备份服务器和存储器。

### 相关链接

* [物理基础架构设计](/docs/services/vmwaresolutions/archiref/solution/design_physicalinfrastructure.html)
* [虚拟基础架构设计](/docs/services/vmwaresolutions/archiref/solution/design_virtualinfrastructure.html)
* [公共服务设计](/docs/services/vmwaresolutions/archiref/solution/design_commonservice.html)
