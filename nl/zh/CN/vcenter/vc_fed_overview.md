---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# VMware Federal on IBM Cloud 概述

VMware Federal on {{site.data.keyword.cloud}} 除了向美国联邦政府机构提供用于确保已部署 vCenter Server 实例安全的选项外，还支持订购基本 vCenter Server 实例。选择用于确保已部署实例安全的选项会除去存储的有关实例的敏感信息，并除去打开用于持续访问实例以实现管理功能（例如，添加和除去主机与集群）的管理连接。选择安全选项后，将禁用所有管理功能，但完全实例删除操作除外。

有关 vCenter Server on {{site.data.keyword.cloud_notm}} 和 vCenter Server 体系结构的更多信息，请参阅 [vCenter Server 概述](vc_vcenterserveroverview.html)。

**注意**：VMware Federal on {{site.data.keyword.cloud_notm}} 只是 vCenter Server 产品的一部分。不支持多站点配置、预配置的 {{site.data.keyword.cloud_notm}} 裸机服务器、自带许可证以及用于订购更多服务的选项。

## VMware Federal on IBM Cloud 的 vCenter Server 实例组件

包括以下组件：

### 裸机服务器

可以使用下列其中一个配置来订购两个或更多定制 {{site.data.keyword.baremetal_short}}：

* 2 个 Intel Broadwell 代 CPU（Intel Xeon E5-2600 V4 系列）
* 2 个 Intel Skylake 代 CPU（Intel Xeon 4100/5100/6100 系列）

对于 NFS 存储配置，建议的 {{site.data.keyword.baremetal_short}} 数设置为缺省值 3。

**注**：如果选择 vSAN 存储器，那么配置需要 4 个 {{site.data.keyword.baremetal_short}}。

### 联网

订购了以下联网组件：
*  三个 VLAN（虚拟 LAN）：一个公用 VLAN 和两个专用 VLAN
*  一个 VXLAN（虚拟可扩展 LAN），带 DLR（分布式逻辑路由器），用于处理连接到第 2 层 (L2) 网络的本地工作负载之间的潜在东-西通信。VXLAN 部署为样本路由拓扑，可以基于该拓扑进行构建，或者进行修改或将其除去。还可以通过将其他 VXLAN 连接到 DLR 上的新逻辑接口来添加安全区域。
*  两个 VMware NSX Edge 服务网关：
  * 用于出站 HTTPS 管理流量的安全管理服务 VMware NSX Edge 服务网关 (ESG)，由 IBM 部署为管理联网拓扑的一部分。IBM 管理虚拟机使用此 ESG 与自动化相关的特定外部 IBM 管理组件进行通信。有关更多信息，请参阅[配置网络以使用客户管理的 ESG](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)。

    **重要信息**：此 ESG 对您不可访问，因此您无法使用此 ESG。如果对其进行修改，那么可能无法在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理 vCenter Server 实例。此外，请注意，使用防火墙或禁用与外部 IBM 管理组件的 ESG 通信将导致 {{site.data.keyword.vmwaresolutions_short}} 无法使用。
  * 用于出站和入站 HTTPS 工作负载流量的客户管理的安全 VMware NSX Edge 服务网关，由 IBM 部署为模板，您可修改此模板来提供 VPN 访问或公共访问。有关更多信息，请参阅[客户管理的 NSX Edge 会构成安全风险吗](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)。

  **注**：在确保已部署 VMware 实例安全的操作过程中，会除去用于出站 HTTPS 管理流量的 VMware NSX Edge 服务网关 (ESG)。有关更多信息，请参阅[确保 VMware Federal 实例安全](vc_fed_securinginstance.html)。

### 虚拟服务器实例

订购了以下 VSI（虚拟服务器实例）：
* 用于 IBM CloudBuilder 的 VSI，在完成实例部署后关闭。
* （对于实例 V2.3 和更高版本）可以选择在管理集群中部署单个 Microsoft Windows Server VSI for Microsoft Active Directory (AD) 或两个高可用性 Microsoft Windows VM，以帮助增强安全性和稳健性。
* （对于 V2.2 实例）用于 Microsoft Active Directory (AD) 的 Microsoft Windows Server VSI，充当在其中注册主机和虚拟机的实例的 DNS，已部署并且可进行查找。

### 存储

在初始部署期间，可以选择 vSAN 或 NFS 存储器选项。

vSAN 选项提供定制配置，具有各种磁盘类型和数量的选项：
* 磁盘数量：2、4、6 或 8 个。
* 存储磁盘：960 GB SSD SED、1.9 TB SSD SED 或 3.8 TB SSD SED。

  此外，每个主机还会订购 2 个 960 GB 高速缓存磁盘。

NFS 选项为工作负载提供定制的共享文件级别存储器，具有各种大小和性能的选项：
* 大小：1、2、4、8 或 12 TB。
* 性能：2、4 或 10 IOPS/GB。
* 单独配置文件共享。

如果选择 NFS 选项，那么会为管理组件订购一个 2 TB、4 IOPS/GB 文件共享。

### IBM 提供的许可证和费用

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.3
* （对于 vSAN 集群）VMware vSAN Advanced 或 Enterprise 6.6

## vCenter Server 扩展节点组件

每个 vCenter Server 扩展节点将在您的 {{site.data.keyword.cloud_notm}} 帐户中部署以下组件并收取相应费用。

### 扩展节点的硬件

一个裸机服务器，其配置在 [VMware Federal on IBM Cloud 的 vCenter Server 实例组件](../vcenter/vc_fed_overview.html#vcenter-server-instance-components-for-vmware-federal-on-ibm-cloud)中提供。

### 扩展节点的许可证和费用

* 一个 VMware vSphere Enterprise Plus 6.5u1
* 一个 VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.3
* （对于 vSAN 集群）VMware vSAN Advanced 或 Enterprise 6.6

**重要信息**：您只能在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 组件，而不能在 {{site.data.keyword.slportal_full}} 中或在控制台外部通过其他任何方法来进行管理。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步。

**注意**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部管理任何 {{site.data.keyword.vmwaresolutions_short}} 组件（在订购实例时已安装到 {{site.data.keyword.cloud_notm}} 帐户中）可能会使环境变得不稳定。这些管理活动包括：
*  添加、修改、返回或除去组件
*  通过添加或除去 ESXi 服务器来扩展或收缩实例容量
*  关闭组件电源
<!--*  Restarting services-->

   这些活动的例外情况包括在 {{site.data.keyword.slportal}} 中管理共享存储器文件共享。此类活动包括：订购、删除（如果已安装，可能会影响数据存储）、授权和安装共享存储器文件共享。

## 相关链接

* [vCenter Server 软件材料清单](vc_bom.html)
* [针对 VMware Federal 实例的需求和规划](vc_fed_planning.html)
* [订购 VMware Federal 实例](vc_fed_orderinginstance.html)
* [确保 VMware Federal 实例安全](vc_fed_securinginstance.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [{{site.data.keyword.cloud_notm}} 文件和块存储器](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
