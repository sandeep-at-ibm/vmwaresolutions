---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# 体系结构概述

此部分提供了有关此参考体系结构中使用的网络体系结构的更多详细信息，其中包含以下各部分：
* **VCS 概述** - 此部分描述 VCS 平台的亮点。
* **网络概述** - 以下各部分提供有关此参考体系结构中使用的网络组件的信息：
  - **IBM Cloud 联网** - {{site.data.keyword.cloud}} 提供物理网络，并且由 {{site.data.keyword.cloud_notm}} 完全管理。此网络具有一些关键特征，需要了解这些特征才能理解内部部署与外部部署之间的网络流以及在不同服务中托管的工作负载之间的网络流。
  - **NSX-V** - VCS 联网基于 {{site.data.keyword.cloud_notm}} 网络构建，该网络具有由 VMware NSX-V 提供的覆盖。此覆盖对来自 {{site.data.keyword.cloud_notm}} 底层网络的流量分段，支持拥有更大的控制力和可配置能力（包括 BYOIP）。
  - **IBM Kubernetes Service** - IKS 将 Calico 用作其容器网络接口插件。
  - **IBM Cloud Private** - ICP 将 Calico 用作其容器网络接口插件。

* **集成** - 此部分描述允许所需网络流量流和寻址的联网组件的体系结构：
  - IP 地址分配
  - 网络流量流

## VCS 概述

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle (VCS) 是一种托管的专用云，可帮助您快速、轻松地将内部部署基础架构扩展到云中，从而实现安全、无缝的基础架构混合和真正的应用程序移动性。

VCS Hybridity Bundle 至少部署在 4 台 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 上，通过虚拟存储区域网络 (VSAN) 提供专用存储器，并包含自动部署和配置易于管理的软件定义联网基础架构 (NSX-V)。VCS Hybridity Bundle 是一种通过自动化部署的参考体系结构，能确保一致性、性能和合规性。在许多情况下，整个环境可以在一天内供应完，而裸机基础架构可根据需要，快速、弹性地向上和向下扩展计算和存储容量。

有许多选项可用于增强和扩展 VCS Hybridity Bundle。{{site.data.keyword.cloud_notm}} 服务产品不仅包含附加组件存储选项以及各种公用和专用 WAN 连接选项，还涵盖了从平台安全性、网络安全性、流量负载均衡一直到备份和灾难恢复等多个领域。

平台安全服务包括 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}、HyTrust DataControl on IBM Cloud、IBM Cloud Secure Virtualization 和 KMIP for VMware on IBM Cloud。HyTrust CloudControl on IBM Cloud 用于提供自动安全和合规性支持，让您能够更好地了解和控制云环境和管理员。HyTrust DataControl on {{site.data.keyword.cloud_notm}} 通过强大的加密和可扩展密钥管理来提供数据保护，以确保工作负载整个生命周期的安全。{{site.data.keyword.cloud_notm}} Secure Virtualization 简化了合规性，并通过加密、地理围栏策略和基于角色的访问控制来保护数据。KMIP for VMware on {{site.data.keyword.cloud_notm}} 是一款加密密钥生命周期管理产品，用于管理 {{site.data.keyword.cloud_notm}} 服务或客户内置应用程序使用的加密密钥。

网络安全选项是 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 和 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}；前者可供应 FortiGate Security Appliance 设备的高可用性对来分析网络流量并保护虚拟基础架构，后者则通过实施虚拟基础架构内的关键安全性控制，在 {{site.data.keyword.cloud_notm}} 上部署 FortiGate VM 的高可用性对，从而降低风险。更多网络安全产品正在开发中。

F5 on {{site.data.keyword.cloud_notm}} 网络负载均衡器服务产品通过 F5 BIG-IP 套件，优化最关键应用程序的性能，并确保其可用性和安全性。

IBM、Veeam 和 Zerto 提供的备份和灾难恢复产品让您安心无忧，在发生灾难时可实现持续运营。IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 是一种用于虚拟环境的数据保护和可用性解决方案。Veeam on {{site.data.keyword.cloud_notm}} 通过 {{site.data.keyword.cloud_notm}} 上的集成备份、恢复和复制功能，支持 Always-On Enterprise™ 的可用性。Zerto on {{site.data.keyword.cloud_notm}} 为内部部署和 {{site.data.keyword.cloud_notm}} 客户提供安全、灵活且可扩展的灾难恢复解决方案。

{{site.data.keyword.cloud_notm}} VCS Hybridity Bundle 不是受管服务，但您可以添加 IBM 管理的服务，以分担对虚拟化、访客操作系统或应用程序层的日常操作和维护。另外还有 {{site.data.keyword.cloud_notm}} 专业服务团队可通过迁移、实施、规划和上线服务，帮助您加速迁移到云。

VCS Hybridity Bundle 的平台集成选项不仅包含 VMware 提供的选项（例如，vRealize Suite 或 vSphere with Operations Management），还涵盖多种 {{site.data.keyword.cloud_notm}} 服务产品（例如，[vCenter Server 和 IBM Kubernetes](../vcsiks/vcsiks-intro.html) 以及 [vCenter Server 和 {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html)），这些产品使用开放式源代码 Terraform 将基础架构作为代码进行管理和交付。

可用于 VCS Hybridity Bundle 的广泛服务产品组合与多产品集成选项提供了一个真正的混合平台，使混合即服务成为可能。

### 相关链接

* [VCS Hybridity Bundle 概述](../vcs/vcs-hybridity-intro.html)
