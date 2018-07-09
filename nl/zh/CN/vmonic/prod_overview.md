---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# 关于 IBM Cloud for VMware Solutions

通过 {{site.data.keyword.vmwaresolutions_full}}，可以使用可扩展、安全和高性能的 {{site.data.keyword.cloud_notm}} 基础架构及行业领先的 VMware 混合虚拟化技术，快速、无缝地集成内部部署 VMware 工作负载或将其迁移到 {{site.data.keyword.cloud_notm}}。

{{site.data.keyword.vmwaresolutions_short}} 支持轻松部署 VMware 虚拟环境，并在 {{site.data.keyword.cloud_notm}} 上管理基础架构资源。同时，您仍可以使用熟悉的本机 VMware 产品控制台来管理 VMware 工作负载。

## IBM Cloud for VMware Solutions 优点

{{site.data.keyword.vmwaresolutions_short}} 提供了以下主要优点：
* **全球覆盖**：支持将混合云覆盖范围扩展到全球各地多达 30 个企业级 {{site.data.keyword.CloudDataCents_notm}}。
* **无缝集成**：支持通过 {{site.data.keyword.cloud_notm}} 基础架构实现整个混合云中的无缝集成。
* **快速供应**：自动执行 VMware 环境的部署和配置，这将支持通过随需应变的 {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}} 和虚拟服务器，快速部署企业级 VMware 环境。
* **简化**：支持您使用 VMware 云平台，而无需确定、购买、部署和管理底层物理基础架构（计算、存储和网络）以及软件许可证。
* **扩展和收缩灵活性**：支持根据业务需求，轻松扩展和收缩 VMware 工作负载。
* **单个管理控制台**：提供单个控制台，可部署、访问和管理 {{site.data.keyword.cloud_notm}} 上的 VMware 环境。

## 部署产品

{{site.data.keyword.vmwaresolutions_short}} 提供了 VMware 虚拟环境的标准化和可定制部署选项。提供了以下部署类型：
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**：vCenter Server 产品支持使用定制计算、存储和网络资源来部署 VMware 虚拟环境，从而最好地适应您的业务需求。
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle**：vCenter Server with Hybridity 产品是一种托管的专用云，可帮助您快速、轻松地将内部部署基础架构扩展到云中。VMware 环境基于 IBM 提供的 VMware 软件定义的数据中心许可证，并包含 VMware Hybrid Cloud Extension (HCX)。通过使用 HCX，可以安全地将内部部署 vSphere 5.0+ 环境与 IBM Cloud 站点相连接，以实现无缝的基础架构混合和真正的应用程序移动性。
* **VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}**：Cloud Foundation 产品使用专用于每个用户部署的标准 {{site.data.keyword.cloud_notm}} 计算、存储和网络资源，提供统一的 VMware 虚拟环境。
* **VMware vSphere on {{site.data.keyword.cloud_notm}}**：vSphere on {{site.data.keyword.cloud_notm}} 产品提供可定制的虚拟化服务，用于组合使用与 VMware 兼容的 {{site.data.keyword.baremetal_short}}、硬件组件和许可证，以构建您自己的 IBM 托管的 VMware 环境。
* **NetApp ONTAP Select**：NetApp ONTAP Select 产品支持部署软件定义的存储器集群，以满足基于 NetApp ONTAP Select 的专用和高可用性存储设备的需求。
* **VMware Federal on {{site.data.keyword.cloud_notm}}**：VMware Federal on {{site.data.keyword.cloud_notm}} 产品除了提供用于确保已部署实例安全的选项、除去敏感信息以及打开用于持续访问实例以获取管理功能的管理连接外，还支持订购基本 vCenter Server 实例。

## 其他服务

{{site.data.keyword.vmwaresolutions_short}} 支持在订购实例时或在部署实例后添加各种服务。提供了以下服务：

### FortiGate Security Appliance on IBM Cloud

此服务用于部署 FortiGate Security Appliance (FSA) 300 系列设备的 HA 对，这些设备可以提供防火墙、路由、NAT 和 VPN 服务来保护环境的公用网络连接。

此服务仅可用于在 V1.8 或更高发行版中部署的实例。

有关更多信息，请参阅[管理 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html)。

### FortiGate Virtual Appliance on IBM Cloud

此服务用于部署 FortiGate Virtual Appliance 的 HA 对，这些设备支持通过在虚拟基础架构中实施关键安全控制来降低风险。

此服务仅可用于在 V2.0 或更高发行版中部署的实例。

有关更多信息，请参阅[管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html)。

### F5 on IBM Cloud

此服务用于优化性能，并通过 F5 BIG-IP Virtual Edition (VE) 确保应用程序的可用性和安全性。

此服务仅可用于在 V1.9 或更高发行版中部署的实例。

有关更多信息，请参阅[管理 F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html)。

### IBM Spectrum Protect Plus on IBM Cloud

此服务用于在虚拟环境下为数据保护、数据复用和数据恢复提供高效的可扩展解决方案。可以将此服务作为独立解决方案实施，也可以与 IBM Spectrum Protect&trade; Plus 环境集成，以便卸载用于长期存储和数据监管的副本。

**注**：
* 此服务仅可用于部署在（或已升级到）V2.2 或更高发行版中的实例。
* 对于在 V2.3 或更高发行版中部署的实例，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 自动提供管理 VM 的备份。
* 对于在 V2.2 中部署的实例，此服务仅为工作负载 VM 提供数据保护。

有关更多信息，请参阅[管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html)。

### Veeam on IBM Cloud

此服务与 VMware 环境无缝集成，以帮助管理环境中所有虚拟机 (VM) 的备份和复原，包括备份和复原管理组件。它可以在数据配置完成后的 15 分钟之内提供恢复点目标 (RPO)。

此服务配置为在部署实例后立即备份管理 VM。

此服务仅可用于在 V1.8 或更高发行版中部署的实例。

有关更多信息，请参阅[管理 Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html)。

### Zerto on IBM Cloud

此服务用于提供复制和灾难恢复功能，以帮助保护工作负载。有关更多信息，请参阅[管理 Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html)。

### IMI 中的受管服务

通过这些服务，IBM Integrated Managed Infrastructure (IMI) 可以针对广泛的各种云基础架构提供动态远程管理服务。

这些服务仅可用于 Cloud Foundation 实例。

有关更多信息，请参阅[向 IMI 请求受管服务](../services/managing_imi.html)。

## 相关链接

* [入门](../index.html)
* [Cloud Foundation 概述](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 概述](../vcenter/vc_vcenterserveroverview.html)
* [vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [NetApp ONTAP Select](../netapp/np_netappoverview.html)
