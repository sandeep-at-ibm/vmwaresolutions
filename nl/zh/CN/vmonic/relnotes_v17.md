---

copyright:

  years:  2016, 2017

lastupdated: "2017-07-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V1.7 发行说明
{: #relnotes_v17}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## 对 VMware Cloud Foundation 实例的更新

此更新将应用下列升级和改进：
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware 安全补丁 6.0 EP7c
* 对 IBM CloudDriver 组件的稳定性改进
* 升级时，会在 V3 服务器上预先存在的 VMware 部署上启用 EVC 方式（基于 Intel“Haswell”2690-V3 处理器）。

  不会对 V4 服务器上的任何现有部署或新部署启用 EVC 方式。
  {:note}

* 现在，向实例添加新节点时，在 5 月 22 日前部署并因此使用 V3 服务器的 VMware Cloud Foundation 部署将订购 V4 服务器。这些服务器的内存为 256 GB；如果需要 512 GB 内存，请在添加服务器后，开具支持凭单以请求将服务器升级到 512 GB 内存。有关联系 IBM 支持人员的更多信息，请参阅[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。

有关组件的更多信息，请参阅 [Cloud Foundation 实例的技术规范](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview#technical-specifications-for-cloud-foundation-instances)。

### 更新过程需求

根据 Cloud Foundation 实例部署的复杂性以及您是否具有多站点配置，更新过程可能需要您必须完成控制台上的**更新和补丁**选项卡中所显示的一系列步骤。有关更多信息，请参阅[对 Cloud Foundation 实例应用更新](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_applyingupdates#applying-updates-to-cloud-foundation-instances)。

## 对 VMware vCenter Server 实例的更新

### 集群支持

从 V1.7 发行版开始，可以使用集群来管理 vCenter Server 实例中的 ESXi 服务器，以更好地管理资源，并实现高可用性。缺省情况下，订购实例时配置的 ESXi 服务器会分组为 **cluster1**。可以在实例详细信息页面上新引入的**基础架构**选项卡中，查看集群详细信息或向实例最多添加共五个集群。展开或收缩实例的容量时，可以选择要向其添加 ESXi 服务器或要从中除去 ESXi 服务器的集群。有关更多信息，请参阅[添加和查看 vCenter Server 实例的集群](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)。

### Zerto 灾难恢复部署的增强功能

现在，Zerto 灾难恢复部署会自动执行，而不是通过支持凭单来处理。所有 Zerto 组件（例如，专用可移植子网、Windows VSI（虚拟服务实例）和 Zerto 许可证）的费用都会列在估算成本上，这样您可以在下订单之前进行复查。有关更多信息，请参阅 [Zerto 灾难恢复部署过程](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)。

### NSX 许可证升级功能

可以在 vCenter Server 实例的**摘要**选项卡中升级 NSX 许可证版本。许可证升级会将帐户中的所有现有 NSX SoftLayer 许可证替换为新许可证。有关更多信息，请参阅[查看 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)。

## 易用性增强功能

对整个用户界面进行了改进：
* Cloud Foundation 实例详细信息页面上的**属性**选项卡已重命名为**摘要**。现在，可以在此选项卡上查看实例的详细信息、与实例相关的组件的访问信息以及实例部署历史记录。
* Cloud Foundation 实例详细信息页面上引入了新的**基础架构**选项卡。可以在此选项卡上查看、添加或除去 ESXi 服务器。
* {{site.data.keyword.vmwaresolutions_short}} 的文档采用新格式，现在与 Bluemix 文档集一起完全集成到 Bluemix“目录”中。可以通过下列其中一种方式访问该文档：
  * 在 {{site.data.keyword.vmwaresolutions_short}} 中，单击条幅左侧的**文档**。
  * 在 Bluemix 文档目录中，向下滚动到**计算和服务**部分，然后单击 **{{site.data.keyword.vmwaresolutions_short}}**。
