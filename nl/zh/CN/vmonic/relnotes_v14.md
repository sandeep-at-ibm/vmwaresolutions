---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-08"

---

# V1.4 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Cloud Foundation 实例的组件更新

新增或更新了以下组件：

* VC 和 PSC（vCenter 和 Platform Services Controller）6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* 为 Microsoft Active Directory (AD) 和 DNS（域名系统）服务订购了新的 Windows VSI（虚拟服务器实例），在此发行版中，多站点配置支持需要此 VSI。此 VSI 具有以下规范：Windows 2012 R2（8 GB RAM / 2 个 CPU 核心 / 100 GB 磁盘 / 双 1 Gbps 专用上行链路）。

有关更多信息，请参阅 [Cloud Foundation 概述](../sddc/sd_cloudfoundationoverview.html)。

## vCenter Server 实例的组件更新

新增或更新了以下组件：

### VMware NSX for vSphere 6.2.4

缺省情况下，会在所有 vCenter Server 实例上安装 VMware NSX for vSphere 6.2.4（先前仅在 Cloud Foundation 实例上安装）。

在 NSX 安装过程中，NSX Manager 将在所有部署的新实例上安装并获得许可。此外，还会创建 NSX Edge 用于实例管理，但您也可以根据需要创建自己的 NSX Edge 组件。有关 NSX Edge 的更多信息，请参阅此页面上的 _VMware NSX Edge_ 部分。

**注**：不会在 vCenter Server 实例上安装 NSX Controller（像安装在 Cloud Foundation 实例上那样）。如果要对 vCenter Server 实例使用 VXLAN 或分布式逻辑路由器，那么您必须自行安装 NSX Controller。

有关 VMware NSX for vSphere 6.2.4 中引入的增强功能、其需求和已知问题的更多信息，请参阅 [NSX for vSphere 6.2.4 发行说明](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}。

### VMware NSX Edge

NSX Edge 现在包含在要订购的新 vCenter Server 实例中。NSX Edge 提供网络边缘安全性和网关服务，以隔离虚拟化网络。

在实例部署期间，IBM 会部署“管理 VMware NSX Edge 服务网关 (ESG)”。IBM 管理虚拟机使用此 ESG 与自动化相关的特定外部 IBM 管理组件进行通信。此 ESG 部署为包含两个接口：一个接口连接到 {{site.data.keyword.cloud_notm}} 专用 VLAN，另一个接口连接到 {{site.data.keyword.cloud_notm}} 公用 VLAN。

为了确保安全性，采用了防火墙规则，以仅允许由管理虚拟机发起的出站 HTTPS 通信。此 ESG 部署在大型配置中，只有 IBM 支持人员才能修改该配置。有关更多信息，请参阅以下主题：

* [vCenter Server 技术规范](../vcenter/vc_vcenterserveroverview.html)
* [管理服务 NSX Edge 会构成安全风险吗？](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX 文档](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### NSX 许可证

为每个节点订购了一个 VMware NSX Base for Service Providers 版本的许可证。

### 新增子网地址块

为每个节点订购了包含 16 个公共可移植地址的子网块。

## 服务收费模型更新

简化了服务收费模型：

* 对于 Cloud Foundation 实例，停止收取 _VMware Cloud Foundation 实例服务_、_VMware Cloud Foundation 存储服务_和 _VMware 解决方案系统管理程序_费用。
* 对于 vCenter Server 实例，停止收取 _VMware vCenter Server 实例_和 _VMware Solutions 系统管理程序_费用。
* 对于这两种实例类型，引入了新的_支持和服务_费用，将按每个节点每月收取费用。

## 对实例联网拓扑的更新

此发行版包含针对实例的以下拓扑增强功能：

* 对于 Cloud Foundation 实例和 vCenter Server 实例：优化了联网配置，即，仅 SoftLayer® 分配的主公共 IP 地址和专用 IP 地址会连接到 ESXi 服务器。不再为管理流量部署可移植专用地址。
* 仅限 Cloud Foundation 实例：Windows AD SSO (Active Directory Single Sign-On) 和域名系统 (DNS) 服务器

**注**：由于这些更改，您无法在当前发行版中使用 V1.4 之前的现有实例。要复用现有实例的配置，必须将其升级到当前版本。有关更多信息，请参阅[从 V1.4 之前的发行版升级实例](movinginstances.html)。

## Cloud Foundation 实例的多站点配置支持

现在，您可以部署单个 Cloud Foundation 实例，就像在前发行版中那样，或者额外部署连接到主实例的辅助实例。多站点配置模型使用轴辐式拓扑，其中包含一个主站点和最多七个辅助站点。

有关更多信息，请参阅 [Cloud Foundation 实例的多站点配置](../sddc/sd_multisite.html)。

## Zerto 灾难恢复部署的增强功能

* 对于 Cloud Foundation 实例，Zerto 灾难恢复部署会自动执行，而不是通过支持凭单来处理。所有 Zerto 组件（例如，专用可移植子网、Windows VSI（虚拟服务实例）和 Zerto 许可证）的费用都会列在估算成本上，这样您可以在下订单之前进行复查。
* 对于 vCenter Server 实例，Zerto 灾难恢复部署是通过支持凭单完成的（与前发行版一样）。但是，不再需要 NSX Edge 和公用可移植子网，因为这两项现在包含在基本部署中。专用可移植子网、Windows VSI（虚拟服务实例）和 Zerto 许可证的费用仍然适用。

有关更多信息，请参阅 [Zerto 灾难恢复](../services/addingzertodr.html)。

## 实例订购过程

极大地简化了实例订购过程：

* 对于 Cloud Foundation 实例和 vCenter Server 实例，在订购过程中不再显示“SoftLayer 凭证”页面。缺省情况下，将使用在“设置”页面上定义的 SoftLayer 凭证，并且仅当不满足需求时，系统才会提示您更新这些凭证。
* 此外，对于 vCenter Server 实例，现在对于**硬件**类型仅提供**大型**选项，对于**上行链路端口速度**仅提供 **10 Gbps 双**设置，这可减少订购时要指定的设置数量。

有关更多信息，请参阅以下主题：

* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)
* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)

## 实例管理

为实例管理过程提供了以下新功能和改进：

* 对于 Cloud Foundation 实例，可以在实例详细信息页面上查看各种实例组件的用户名和密码。有关更多信息，请参阅[查看 Cloud Foundation 实例](../sddc/sd_viewinginstances.html)。
* 对于 vCenter Server 实例，可以直接在控制台中安装 IBM 组件的软件更新和补丁。有关更多信息，请参阅[对 vCenter Server 实例应用更新和补丁](../vcenter/vc_applyingupdates.html)。

## 控制台通知

现在，可以在**设置**页面上配置控制台通知。缺省情况下，此设置已启用，这意味着您将在控制台中收到所有事件的通知。还可以在**设置**页面上禁用控制台的通知。

有关更多信息，请参阅以下主题：

* [用户帐户和设置](useraccount.html)
* [通知](notifications.html)
