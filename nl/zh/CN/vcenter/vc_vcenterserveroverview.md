---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# vCenter Server 概述

VMware vCenter Server on {{site.data.keyword.cloud}} 是一种托管的专用云，可将 VMware vSphere 堆栈作为服务交付。VMware 环境至少基于两个（建议三个）{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 而构建，提供共享的网络连接存储器和专用的软件定义存储器选项，包括自动部署和配置基于 VMware NSX 技术的易于管理的逻辑边缘防火墙。

在许多情况下，整个环境可以在一天内供应完，而裸机基础架构可根据需要，快速、弹性地向上和向下扩展计算容量。

部署后，可以通过在 {{site.data.keyword.slportal}} 中订购更多 NFS（网络文件系统）文件共享来增加共享存储器，并可以手动连接集群中所有 ESXi 服务器上的共享存储器。如果需要专用存储器，可使用同时在高性能（所有 SSD）和高容量（所有 SATA）配置中提供的 [NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}](../netapp/np_netappoverview.html)。

VMware vSAN 还可作为专用存储器选项提供。要增大 vSAN 集群的基于 vSAN 的存储容量，可以在部署后添加更多 ESXi 服务器。

如果购买了 IBM 提供的 VMware 许可，那么可以将 VMware NSX Base Edition 升级到 Advanced 或 Enterprise Edition，并且可以购买更多 VMware 组件，例如 VMware vRealize Operations。

如果要卸载虚拟化、访客操作系统或应用程序层的日常操作和维护，可以添加 IBM 受管服务。另外还有 {{site.data.keyword.cloud_notm}} 专业服务团队可通过迁移、实施、规划和上线服务，帮助您加速迁移到云。

## vCenter Server 体系结构

下图描绘了三节点 vCenter Server 部署的高级别体系结构和组件。

图 1. 三节点集群的 vCenter Server 高级别体系结构

![vCenter Server 体系结构](vc_architecture.svg "针对三节点集群的 vCenter Server 高级别体系结构")

### 物理基础架构

此层提供要由虚拟基础架构使用的物理基础架构（计算、存储和网络资源）。

### 虚拟化基础架构（计算和网络）

此层通过不同 VMware 产品对物理基础架构进行虚拟化：
* VMware vSphere 对物理计算资源进行虚拟化。
* VMware NSX 是网络虚拟化平台，用于提供逻辑联网组件和虚拟网络。

### 虚拟化管理

此层由 vCenter Server Appliance (vCSA)、NSX Manager、两个 NSX ESG、三个 NSX Controller、Platform Services Controller (PSC) 虚拟设备和 IBM CloudDriver 虚拟服务器实例 (VSI) 组成。对于某些操作（例如，向环境添加主机），将根据需要部署 CloudDriver VSI。

基本产品随 vCenter Server Appliance 一起部署，后者的大小设置为支持具有最多 400 个主机和最多 4000 个 VM 的环境。可以使用与 vSphere API 兼容的相同工具和脚本来管理 IBM 托管的 VMware 环境。

基本产品总计需要 38 个 vCPU 和 67 GB vRAM，这些均保留用于虚拟化管理层。VM 的其余主机容量取决于若干因素，例如超额预订比率、VM 大小设置和工作负载性能需求。

有关体系结构的详细信息，请参阅 [{{site.data.keyword.vmwaresolutions_short}} 体系结构参考](../archiref/solution/solution_overview.html)。

## vCenter Server 实例的技术规范

vCenter Server 实例中包含以下组件。

**注**：标准化硬件配置的可用性和定价可能会因选择用于部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。

### 裸机服务器

可以使用下列其中一个配置来订购三个或更多 {{site.data.keyword.baremetal_short}}：
*  **定制**：具有所选 CPU 型号和 RAM 大小的 {{site.data.keyword.baremetal_short}}。   
   * 2 个 Intel Broadwell 代 CPU（Intel Xeon E5-2600 V4 系列）
   * 2 个 Intel Skylake 代 CPU（Intel Xeon 4100/5100/6100 系列）

     **注**：如果计划使用 vSAN 存储器，那么配置需要 4 个 {{site.data.keyword.baremetal_short}}。
*  **预配置**：2 个 Intel Broadwell 代 CPU（Intel Xeon E5-2600 V4 系列）
   * **小型**（双 Intel Xeon E5-2620 V4 / 共 16 个核心，2.1 GHz / 128 GB RAM / 2 个磁盘）
   * **中型**（双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz / 256 GB RAM / 2 个磁盘）
   * **大型**（双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz / 512 GB RAM / 2 个磁盘）

### 联网

订购了以下联网组件：
*  10 Gbps 双公用和专用网络上行链路
*  三个 VLAN（虚拟 LAN）：一个公用 VLAN 和两个专用 VLAN
*  一个 VXLAN（虚拟可扩展 LAN），带 DLR（分布式逻辑路由器），用于处理连接到第 2 层 (L2) 网络的本地工作负载之间的潜在东-西通信。VXLAN 部署为样本路由拓扑，可以基于该拓扑进行构建，或者进行修改或将其除去。还可以通过将其他 VXLAN 连接到 DLR 上的新逻辑接口来添加安全区域。
*  两个 VMware NSX Edge 服务网关：
  * 用于出站 HTTPS 管理流量的安全管理服务 VMware NSX Edge 服务网关 (ESG)，由 IBM 部署为管理联网拓扑的一部分。IBM 管理虚拟机使用此 ESG 与自动化相关的特定外部 IBM 管理组件进行通信。有关更多信息，请参阅[配置网络以使用客户管理的 ESG](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)。

    **重要信息**：此 ESG 对您不可访问，因此您无法使用此 ESG。如果对其进行修改，那么可能无法在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理 vCenter Server 实例。此外，请注意，使用防火墙或禁用与外部 IBM 管理组件的 ESG 通信将导致 {{site.data.keyword.vmwaresolutions_short}} 无法使用。
  * 用于出站和入站 HTTPS 工作负载流量的客户管理的安全 VMware NSX Edge 服务网关，由 IBM 部署为模板，您可修改此模板来提供 VPN 访问或公共访问。有关更多信息，请参阅[客户管理的 NSX Edge 会构成安全风险吗？](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

### 虚拟服务器实例

订购了以下虚拟服务器实例 (VSI)：
* 用于 IBM CloudBuilder 的 VSI，在完成实例部署后关闭。
* （对于实例 V2.2 和更高版本）可以选择在管理集群中部署单个 Microsoft Windows Server VSI for Microsoft Active Directory (AD) 或两个高可用性 Microsoft Windows VM，以帮助增强安全性和稳健性。
* （对于实例 V1.9 到 V2.1）用于 Microsoft Active Directory (AD) 的 Microsoft Windows Server VSI，充当在其中注册主机和虚拟机的实例的 DNS，已部署并且可进行查找。
* （对于实例 V1.8 和更低版本）用于基于快照备份管理组件的 VSI，在完成实例部署后会保持运行。

### 存储

在初始部署期间，可以选择 vSAN 或 NFS 存储器选项。

vSAN 选项提供定制配置，具有各种磁盘类型和数量的选项：
* 磁盘数量：2、4、6 或 8 个
* 存储磁盘：960 GB SSD SED、1.9 TB SSD SED 或 3.8 TB SSD SED。

  此外，每个主机还会订购 2 个 960 GB 高速缓存磁盘。

  **注**：3.8 TB SSD（固态磁盘）驱动器在数据中心内基本可用后就会受到支持。

NFS 选项为工作负载提供定制的共享文件级别存储器，具有各种大小和性能的选项：
* 大小：1、2、4、8 或 12 TB
* 性能：2、4 或 10 IOPS/GB。
* 单独配置文件共享。

如果选择 NFS 选项，那么会为管理组件订购一个 2 TB、4 IOPS/GB 文件共享。

### 许可证（IBM 提供或 BYOL）和费用

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.4
* （对于 vSAN 集群）VMware vSAN Advanced 或 Enterprise 6.6
* 支持和服务费用（每个节点一个许可证）

## vCenter Server 扩展节点的技术规范

每个 vCenter Server 扩展节点将在您的 {{site.data.keyword.cloud_notm}} 帐户中部署以下组件并收取相应费用。

### 扩展节点的硬件

一个裸机服务器，其配置在 [vCenter Server 实例的技术规范](vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)中提供。

### 扩展节点的许可证和费用

* 一个 VMware vSphere Enterprise Plus 6.5u1
* 一个 VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.4
* 一个支持和服务费用
* （对于 vSAN 集群）VMware vSAN Advanced 或 Enterprise 6.6

**重要信息**：您只能在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 组件，而不能在 {{site.data.keyword.slportal}} 中或在控制台外部通过其他任何方法来进行管理。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步。

**注意**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部管理任何 {{site.data.keyword.vmwaresolutions_short}} 组件（在订购实例时已安装到 {{site.data.keyword.cloud_notm}} 帐户中）可能会使环境变得不稳定。这些管理活动包括：
*  添加、修改、返回或除去组件
*  通过添加或除去 ESXi 服务器来扩展或收缩实例容量
*  关闭组件电源
*  重新启动服务

   这些活动的例外情况包括在 {{site.data.keyword.slportal}} 中管理共享存储器文件共享。此类活动包括：订购、删除（如果已安装，可能会影响数据存储）、授权和安装共享存储器文件共享。

### 相关链接

* [vCenter Server 软件材料清单](vc_bom.html)
* [规划 vCenter Server 实例](vc_planning.html)
* [订购 vCenter Server 实例](vc_orderinginstance.html)
* [{{site.data.keyword.cloud_notm}} 文件和块存储器](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
