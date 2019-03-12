---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 针对 vCenter Server on IBM Cloud 单节点试用版的 HCX on IBM Cloud 体系结构设计
{: #vc_trial_hcx_arch}

使用 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 单节点试用版的 VMware HCX on {{site.data.keyword.cloud}} 是一个新产品，支持在 {{site.data.keyword.vmwaresolutions_short}} 实例与内部部署 VMware 虚拟化数据中心之间进行无缝连接。虽然建议 vCenter Server 至少有三个节点，但通过此单节点试用版，能以低成本来测试并体验混合云实施的优点。

{{site.data.keyword.vmwaresolutions_short}} 包含在 {{site.data.keyword.cloud_notm}} 中全自动快速部署 vCenter Server 配置。vCenter Server 单节点试用版产品是对内部部署基础架构的补充，允许现有和未来的工作负载无需转换就能在 {{site.data.keyword.cloud_notm}} 中运行。该产品使用的工具、技能和流程与内部部署所用的相同。有关 {{site.data.keyword.vmwaresolutions_short}} 产品的更多信息，请参阅 [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture)。

HCX on {{site.data.keyword.cloud_notm}} 服务通过支持创建无缝网络扩展和工作负载双向迁移，将 vCenter Server 实例与现有的内部部署虚拟化数据中心混合在一起。HCX on IBM Cloud 组件（在 {{site.data.keyword.cloud_notm}} VMware 目标站点中部署为虚拟机 (VM)）支持建立与安装在对等内部部署源站点中的 HCX on {{site.data.keyword.cloud_notm}} 组件的连接。

图 1. HCX 体系结构

![HCX 体系结构](hcx-architecture.svg "HCX 体系结构")

下面提供了 HCX on {{site.data.keyword.cloud_notm}} 服务实现的设计信息。该实现包括目标端 {{site.data.keyword.vmwaresolutions_short}} 实例上的组件以及内部部署在源上的组件。

## HCX on IBM Cloud 概述
{: #vc_trial_hcx_arch-ovw}

{{site.data.keyword.cloud_notm}} 将内部部署 vSphere vCenter 网络无缝集成到 {{site.data.keyword.vmwaresolutions_short}} 部署中。通过混合联网，将内部部署 vSphere vCenter 网络扩展到 {{site.data.keyword.cloud_notm}}，以支持双向 VM 移动性。

HCX 拥有源和目标加密与解密过程，这可确保一致的安全性，并为混合工作流程（例如，VM 迁移和网络扩展）提供许可。此产品可创建经过优化的软件定义的广域网 (WAN)，以提高延伸网络性能，使性能接近局域网 (LAN) 速度。HCX 支持双向工作负载以及将 VMware NSX 安全策略迁移到 {{site.data.keyword.cloud_notm}}，并且 HCX 与 vSphere vCenter 集成，并通过 vSphere Web Client 进行管理。

### 第 2 层网络扩展
{: #vc_trial_hcx_arch-layer-2-extension}

HCX 允许现有的内部部署 vSphere 资产安全地将网络从其内部部署 vCenter 延伸到在 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 或 vCenter Server 上运行的 {{site.data.keyword.CloudDataCent_notm}}。以下各项支持此功能：

* HCX 提供称为第 2 层集中器 (L2C) 的设备。
* 通过扩展网络链接到部署在 vCenter Server 上的 {{site.data.keyword.cloud_notm}} NSX Edge 设备。
* 能够部署多个标准第 2 层集中器，以实现可扩展性并提高内部部署 vCenter 的吞吐量。
* 通过云网关和延伸的第 2 层迁移的 VM 可以保留其 IP 和 MAC 地址。

### 虚拟机迁移
{: #vc_trial_hcx_arch-vm-mig}

HCX 提供了以下三种 VM 迁移方法：

* 短停机时间迁移
* vSphere vMotion 迁移
* 冷迁移

#### 短停机时间迁移
{: #vc_trial_hcx_arch-low-downtime-mig}

短停机时间迁移依赖于 vSphere 复制；vSphere 复制是 VMware ESX 或 VMware ESXi 系统管理程序中实施的一种分布式技术。内部部署 HCX 部署创建 {{site.data.keyword.cloud_notm}} 中活动 VM 的副本，然后执行转换以关闭源 VM 的电源，并打开所迁移 VM 的电源。迁移路径始终通过云网关执行。传输可以通过因特网、第 2 层延伸网络或 Direct Connect 线路执行。可以在任一方向多次迁移一个 VM。

#### vSphere vMotion 迁移
{: #vc_trial_hcx_arch-vmotion-mig}

可以在延伸到 {{site.data.keyword.cloud_notm}} 的网络上使用 vSphere vMotion 迁移来传输活动 VM。vMotion 迁移也称为零停机时间迁移或跨云 vMotion。

#### 冷迁移
{: #vc_trial_hcx_arch-cold-mig}

冷迁移能够通过利用第 2 层集中器创建的延伸网络，将已关闭电源的 VM 传输到 {{site.data.keyword.cloud_notm}}。

#### 共同迁移功能
{: #vc_trial_hcx_arch-common-feat}

所有三种类型的迁移都具有以下功能：

* 软件定义的 WAN 优化，可提高迁移吞吐量和速度。
* 将迁移安排在指定时间执行。
* 保留主机名和/或 VM 名称。

### 联网
{: #vc_trial_hcx_arch-network}

以下联网功能内置于云网关和第 2 层集中器中。

#### 智能流量路由
{: #vc_trial_hcx_arch-intel-flow}

智能流量路由根据因特网路径自动选择最佳连接，对整个连接高效地处理洪流，以便尽快迁移工作负载。较大的流量（例如，备份或复制）会导致 CPU 争用，而较小的流量则路由到繁忙程度较低的 CPU，从而提高交互式流量的性能。

#### 邻近路由
{: #vc_trial_hcx_arch-prox-routing}

邻近路由确保连接到内部部署和云中延伸网络和路由网络的 VM 之间的转发是对称的。此功能需要在客户内部部署和云之间配置具有动态路由的高级网络服务。

用户将其网络扩展到云时，第 2 层连接会延伸到 {{site.data.keyword.cloud_notm}} 网络。但是，在不优化路径的情况下，第 3 层通信请求必须返回到内部部署网络源进行路由。这种往返行为称为“长号传输”或“发夹传输”。“长号传输”效率低下，因为包必须在网络源和云之间来回传输，即使源和目标 VM 都位于云中也是如此。

如果转发路径包含有状态防火墙或必须看到连接两端的其他内联设备，那么通信可能会失败。云的流出路径为延伸的第 2 层网络或组织路由网络时，会发生 VM 通信（如果未优化路径）失败。内部部署网络并不知道关于延伸网络“快捷方式”的信息。此问题称为非对称路由。解决方案是启用邻近路由，使内部部署网络可以了解来自 {{site.data.keyword.cloud_notm}} 的路径。

云网关会维护云中 VM 的清单。此外，云网关还将了解以下 VM 状态：

* 已使用 vMotion 传输到 {{site.data.keyword.cloud_notm}}（零停机时间迁移）
* 已使用基于主机的复制迁移到云（短停机时间迁移）
* 已在云中创建（在延伸网络上）

#### 安全性
{: #vc_trial_hcx_arch-sec}

云网关提供符合 Suite B 标准的带有 IKEv2 的 AES-GCM、AES-NI 卸载和基于流量的许可控制。此外，HCX 还拥有源和目标加密与解密过程，从而确保对混合工作流程（例如，VM 迁移和网络扩展）提供一致的安全性和管理。您可以将已定义且分配给内部部署 VM 的安全策略随 VM 一起迁移到 {{site.data.keyword.cloud_notm}}。

下面是策略迁移需要的条件：

* 内部部署数据中心运行的是 NSX V6.2.2 或更高版本。
* 在 vSphere 中，安全策略是单个“NSX 部分”，可以具有许多规则。
* 可以指定一组 IP 地址或 MAC 地址来参与策略。
* “MAC 集”或“IP 集”的名称不能超过 218 个字符。
* 支持的规则将第 3 层 IP 地址或 IP 集，或将第 2 层 MAC 地址或 MAC 集指定为源或目标。

### HCX 组件
{: #vc_trial_hcx_arch-hcx-comp}

HCX on {{site.data.keyword.cloud_notm}} 服务会部署 4 个虚拟设备，内部部署数据中心和 IBM Cloud 目标上都会安装并配置这些设备。以下信息分别描述了所需的 4 个虚拟设备。（可选）有可能会需要 Edge 设备，具体取决于实现设计。

#### HCX Manager
{: #vc_trial_hcx_arch-hcx-manager}

HCX Manager 虚拟设备是内部部署 vCenter 的扩展。此设备会部署为 VM，其文件结构包含其他混合服务虚拟设备。HCX Manager 监管内部部署和 {{site.data.keyword.cloud_notm}} 中的云网关、第 2 层集中器和 WAN 优化虚拟设备的部署与配置。

#### Hybrid Cloud Gateway
{: #vc_trial_hcx_arch-hcg}

Hybrid Cloud Gateway (CGW) 在内部部署 vSphere 资产和 {{site.data.keyword.cloud_notm}} 之间维护一个安全通道。HCX 使用高强度加密来引导与 {{site.data.keyword.cloud_notm}} 的站点到站点连接。通过 vSphere 和 {{site.data.keyword.cloud_notm}} 之间的安全通道，可防止联网“中途”安全问题。云网关还采用了 vSphere 复制技术，用于执行双向迁移。

#### WAN 优化
{: #vc_trial_hcx_arch-wan-opt}

WAN 优化设备是用于执行 WAN 调节以减少等待时间所产生影响的组件。它还包含前向纠错功能，可解决丢包问题，并可执行冗余流量模式去重。总而言之，这些设备可以减少带宽使用量，并确保最充分地利用可用网络容量来加速与 {{site.data.keyword.cloud_notm}} 之间的数据传输。

VM 迁移依赖于云网关和 WAN 优化设备的组合，以实现 vSphere 内部部署和 {{site.data.keyword.cloud_notm}} 之间无与伦比的移动性。此外，当数据路径通过云网关路由时，第 2 层扩展可受益于 WAN 优化。
{:important}

#### 第 2 层集中器
{: #vc_trial_hcx_arch-layer-2-conc}

通过第 2 层集中器 (L2C) 设备，能够将第 2 层网络从内部部署 vSphere 数据中心扩展到 {{site.data.keyword.cloud_notm}}。

第 2 层集中器具有以下接口：

* **内部中继接口**：使用映射到 {{site.data.keyword.cloud_notm}} 中对应延伸网络的转换网桥，处理扩展网络的内部部署 VM 流量。
* **上行链路接口**：HCX 使用此接口发送封装的 {{site.data.keyword.cloud_notm}} 进出覆盖流量。应用程序数据通过上行链路接口进行传输。

### 部署体系结构
{: #vc_trial_hcx_arch-deployment}

有关 HCX on {{site.data.keyword.cloud_notm}} 部署的信息，请参阅 [VMware HCX on {{site.data.keyword.cloud_notm}} Deployment and Operations](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf)。
