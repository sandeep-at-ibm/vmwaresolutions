---

copyright:

  years:  2016, 2018

lastupdated: "2017-05-22"

---

# V1.6 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## 对 VMware Cloud Foundation 实例的更新

新增或更新了以下组件：

*  SDDC Manager 2.2.1
*  IBM 管理组件 V1.6
*  新的硬件规范：**小型**或**标准**，具体取决于您的需求。
*  可用于部署的新数据中心：**HKG02 - 中国香港特别行政区**、**OSL01 - 奥斯陆**、**SEO01 - 首尔**、**SNG01 - 新加坡**和 **SYD04 - 悉尼**。

有关组件的完整列表，请参阅 [VMware Cloud Foundation 概述](../sddc/sd_cloudfoundationoverview.html)。

## 对 VMware vCenter Server 实例的更新

### vCenter Server 实例的硬件增强功能

从 V1.6 发行版开始，有多项增强功能可用于 vCenter Server 实例。

*  完整实现了针对 vCenter Server 产品的 V2.0 规范。有关更多信息，请参阅 [VMware vCenter Server on {{site.data.keyword.cloud_notm}} 解决方案体系结构](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture#2_0)。
*  新的硬件规范：**小型**、**中型**或**大型**，具体取决于您的需求。
*  可用于部署的新数据中心：**HKG02 - 中国香港特别行政区**、**OSL01 - 奥斯陆**、**SEO01 - 首尔**、**SNG01 - 新加坡**和 **SYD04 - 悉尼**。
*  实例订单中至少两个 ESXi 服务器，并且缺省情况下已启用 VMware vSphere DRS（分布式资源调度程序）和 VMware HA（高可用性）。
*  订购实例时，最多可以添加七个 NFS 文件共享。现在，管理组件（vCenter、PSC、NSX Manager 和 NSX Controller、CloudDriver）在 NFS 文件共享上运行以实现高可用性。
*  自动部署和配置客户管理的 VMware NSX Edge 服务网关。

由于这些更改，您无法在当前发行版中按原样使用（或升级）现有 vCenter Server 实例。V1.6 之前的发行版中的 vCenter Server 实例仍然会以“仅查看”方式在 {{site.data.keyword.vmwaresolutions_short}} 控制台上显示。这些实例在用户界面上标记为**不推荐**，并带有警告符号图标。

在 V1.6 之前的 vCenter Server 实例上，以下操作可用：

*  在实例详细信息页面上查看信息。实例属性中显示的信息反映的是截至 V1.6 发行日期的数据，这些数据不会再刷新。
*  打开 VMware vSphere Web Client 并使用 vCenter 中的实例。
*  删除实例。

对于 V1.6 之前的实例，其他所有操作都不再可用。

### vCenter Server 实例的联网增强功能

*  将以您的名义订购公用 VLAN 上包含 16 个 IP 地址的公用子网，用于允许 VM（虚拟机）访问因特网。
*  将以您的名义订购专用 VLAN 上包含 64 个 IP 地址的专用子网，用于允许 VM 访问 SoftLayer® 内部网络。
*  NSX Controller 通过反关联性规则进行部署，并分别在 3 节点部署配置中的单独 ESXi 服务器上运行。
*  新的 VMware NSX Edge 服务网关可供客户使用。

   现在，有一个额外的 NSX Edge 服务网关 (ESG) 作为订购的新 vCenter Server 实例的一部分进行部署。

   提供此 ESG 是为了与您自己的 VM 一起使用，以便在以您的名义订购的专用和公用子网之间进行通信；此 ESG 包含两个接口：一个接口连接到与 VM 关联的虚拟化 VXLAN，另一个接口连接到公用 VLAN。此外，还会配置以下设置：
   *  防火墙规则，用于允许来自 IP 地址的专用子网范围的所有传出流量。
   *  SNAT（源网络地址转换）规则（缺省情况下禁用），用于将专用子网中的所有 IP 地址转换为公用子网上的单个 IP 地址。
   * VMware HA（高可用性）配置为使用在管理 ESG 与客户管理的 ESG 之间共享的新端口组。

   此 ESG 针对所有实例硬件类型进行部署，客户可以修改相应配置。有关更多信息，请参阅以下主题：
   *  [配置网络以将客户管理的 NSX Edge 服务网关用于 VM](../vcenter/vc_esg_config.html)
   *  [VMware NSX 文档](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## 易用性增强功能

对整个用户界面进行了改进：

*  通过引入可访问用户界面所有区域的左侧导航窗格，极大地改进了控制台上的主导航。您可以快速订购新实例，查看已部署的实例，复查系统通知，更改设置以及访问联机文档。
*  可从左侧导航窗格访问的新**开始**页面，直接在控制台上提供了足够的详细信息，以帮助您就要订购的实例组件做出知情决策。在**开始**页面上，还将逐步引导您完成实例订购过程，从满足订购实例的所有先决条件（例如，必需的用户帐户）开始，一直到下订单结束。
*  Cloud Foundation 实例和 vCenter Server 实例的摘要详细信息已合并到单个页面上，可通过左侧导航窗格上**已部署的实例**菜单来访问该页面。在该页面中，可以选择相应的选项卡来过滤 Cloud Foundation 实例或 vCenter Server 实例。
* 如果实例上安装了 Zerto 灾难恢复，那么可通过一次单击直接从服务详细信息页面访问 Zerto 控制台。有关更多信息，请参阅[订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)和[订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)。
