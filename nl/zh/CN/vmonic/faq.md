---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# 关于 IBM Cloud for VMware Solutions 的一般常见问题

查找有关 {{site.data.keyword.vmwaresolutions_full}} 的常见问题的答案。

## 我需要将哪些用户帐户用于 IBM Cloud for VMware Solutions？
{: faq}

* **IBM 标识帐户**。需要此帐户才能访问 {{site.data.keyword.vmwaresolutions_short}} 控制台。控制台是与 {{site.data.keyword.slportal}} 分开的独立用户界面。有关更多信息，请参阅[入门](/docs/services/vmwaresolutions/index.html)。
* **{{site.data.keyword.cloud_notm}} 帐户**。需要此帐户才能进行供应。您可以使用现有 **IBM 标识**或创建新的 **IBM 标识**来注册 {{site.data.keyword.cloud_notm}} 帐户。
* **{{site.data.keyword.cloud_notm}} 基础架构帐户**。此帐户先前称为 **IBM SoftLayer** 帐户，用于登录到 {{site.data.keyword.cloud_notm}} 基础架构客户门户网站，该门户网站提供了某种额外的功能来管理基础架构产品和服务。您可以通过将 **{{site.data.keyword.cloud_notm}} 帐户**升级到现收现付类型的帐户，或通过将现有 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) 帐户与 {{site.data.keyword.cloud_notm}} 帐户链接，获取 {{site.data.keyword.cloud_notm}} 基础架构帐户。要使用的 {{site.data.keyword.cloud_notm}} 基础架构帐户必须满足特定需求。有关更多信息，请参阅[注册必需的帐户](/docs/services/vmwaresolutions/vmonic/signing_softlayer_account.html)和 [{{site.data.keyword.cloud_notm}} 基础架构帐户需求](/docs/services/vmwaresolutions/vmonic/slaccountrequirement.html)。

## 如何将我的 IBM Cloud Infrastructure 凭证与 IBM Cloud for VMware Solutions 控制台相关联？

首次订购实例时，请遵循控制台中**设置**页面上的指示信息，在 {{site.data.keyword.slportal}} 中查找并复制 {{site.data.keyword.cloud_notm}} 基础架构用户名和 API 密钥。首次订购后，{{site.data.keyword.cloud_notm}} 基础架构凭证会存储在 {{site.data.keyword.vmwaresolutions_short}} 控制台中。未来订购时会自动使用存储的凭证。

## 如何对我的 VMware 虚拟平台使用量计费？

物理和虚拟基础架构以及该实例所导致的许可证的所有成本都将向您的 {{site.data.keyword.cloud_notm}} 帐户收费。订购实例时，您必须具有 {{site.data.keyword.cloud_notm}} 帐户，并提供与该帐户关联的 {{site.data.keyword.slapi_short}} 密钥。

## vCenter Server 实例、Cloud Foundation 实例和 VMware vSphere 集群有什么区别？

所有实例类型都会为 VMware 虚拟环境提供部署选项。但是，差别在于可定制和自动化程度。

* 订购 VMware vCenter Server 实例时，部署的是具有定制计算、存储和网络资源的 VMware 虚拟环境。有关部署的组件的更多信息，请参阅 [vCenter Server 实例的技术规范](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)。
* 订购 VMware Cloud Foundation 实例时，部署的是统一软件定义数据中心 (SDDC) 平台。有关部署的组件的更多信息，请参阅 [Cloud Foundation 实例的技术规范](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)。
* 订购 VMware vSphere 集群时，您在合并与 VMware 兼容的硬件时，将有最大的灵活性来设计和构建托管的 VMware 环境。但是，{{site.data.keyword.cloud_notm}} 不会自动为 VMware vSphere 集群安装、配置和启动可选 VMware 组件。
* vCenter Server 实例、Cloud Foundation 实例和 vSphere 集群支持的功能不同。有关更多信息，请参阅[产品比较图表](/docs/services/vmwaresolutions/vmonic/inst_comp_chart.html)。

## vCenter Server 实例中包含哪些内容？

有关更多信息，请参阅 [vCenter Server 实例的技术规范](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)。

## Cloud Foundation 实例中包含哪些内容？

有关更多信息，请参阅 [Cloud Foundation 实例的技术规范](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)。

## vSphere 集群中包含哪些内容？
有关更多信息，请参阅 [VMware vSphere on {{site.data.keyword.cloud_notm}} 的组件](/docs/services/vmwaresolutions/vsphere/vs_vsphereclusteroverview.html)。

## 双节点 vCenter Server 实例具有高可用性吗？

建议将生产工作负载部署到至少有三个节点的环境中。

缺省情况下，VMware vSphere DRS（分布式资源调度程序）和 VMware HA（高可用性）已启用。但 VMware 的最佳实践建议您将三个 NSX Controller 分别放在单独的节点上。

在双节点最低部署中，一个节点有一个 NSX Controller，另一个节点有两个 NSX Controller。如果带有两个 NSX Controller 的节点关闭，那么 NSX Controller 操作将置于只读模式，并且新的 VM（虚拟机）或 vMotion VM 可能会遇到联网问题。

将第三个节点添加到双节点集群后，vCenter Server 会自动在这三个节点之间重新均衡三个 NSX Controller，并创建高可用性环境。

## 可以设置 VMware vCenter 6.5 HA 配置吗？

不，建议不要这样做。否则，{{site.data.keyword.vmwaresolutions_short}} 功能中可能会出现故障。

## 可以重命名集群吗？

对于 vCenter Server 实例，在部署期间创建的第一个集群具有缺省名称 **cluster1**。可以在 VMware vSphere Client 中重命名缺省集群。在您将集群添加到 a vCenter Server 实例时，可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台上指定所需名称。

**注**：对于 Cloud Foundation 实例，无法更改缺省集群名称。

## 如何管理补丁？

IBM 通过按需部署 IBM CloudDriver 虚拟服务器实例 (VSI)，提供 IBM 代码的持续更新。IBM 不会提供附加组件服务（例如，Zerto on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}}）的持续更新。获取并安装这些更新是您的责任。

根据实例类型，VMware 更新会以不同方式应用。

### VMware Cloud Foundation 实例

对 vSphere ESXi、NSX、vCenter、Platform Services Controller 和 SDDC Manager 组件的更新将通过 {{site.data.keyword.vmwaresolutions_short}} 控制台提供。

### VMware vCenter Server 实例

对于部署或升级到 V2.1 或更高版本的实例，将使用 VMware 中最近（但不一定是最新）的 ESXi 更新，对新部署的 ESXi 服务器和集群进行修补。

您负责对 VMware 组件执行其他所有更新，包括确保新部署的 ESXi 服务器和集群都具有全部所需的最新更新。
{:important}

对于部署到 V2.0 或更高版本的实例，VMware Update Manager (VUM) 将集成到 vCenter Server 中。可以将 VUM 配置为从 VMware 下载 ESXi 更新。

有关更多信息，请参阅以下资源：
* [VMware 支持](https://www.vmware.com/support.html)
* [对 vCenter Server 实例应用更新](/docs/services/vmwaresolutions/vcenter/vc_applyingupdates.html)
* [对 Cloud Foundation 实例应用更新](/docs/services/vmwaresolutions/sddc/sd_applyingupdates.html)
* [对 vCenter Server with Hybridity Bundle 实例应用更新](/docs/services/vmwaresolutions/vcenter/vc_hybrid_applyingupdates.html)

## 管理服务 NSX Edge 会构成安全风险吗？

虽然用于管理服务的 VMware NSX Edge 位于公用子网上，但已采用以下安全措施来确保它不会构成安全风险：
*  NSX Edge 防火墙已配置为仅允许管理虚拟机发起的传出 HTTPS（TCP 端口 443）流量。
*  使用了 SNAT（源网络地址转换），用于使专用 IP 地址在专用网络外部不可见。
*  禁用了管理服务 NSX Edge 设备的远程访问。
*  用于访问专用网络中管理服务 NSX Edge 的密码是随机的，并已加密。

## 客户管理的 NSX Edge 会构成安全风险吗？

虽然客户管理的 NSX Edge 位于公用 VLAN 上，但已采用安全措施来确保它不会构成安全风险。现有的安全措施如下：
*  采用了防火墙规则，仅允许来自 IP 地址的专用子网范围的传出流量。
*  采用了 SNAT（源网络地址转换）规则（缺省情况下禁用），用于将专用子网中的所有 IP 地址转换为公用子网上的单个 IP 地址。
*  禁用了客户管理的 NSX Edge 设备的远程访问。
*  用于访问专用网络中客户管理的 NSX Edge 的密码是随机的，并已加密。

## 如何为实例选择数据中心？

实例部署具有严格的物理基础架构需求，这些需求在各个 {{site.data.keyword.CloudDataCents_notm}} 中有所不同。订购实例时，会列出区域内的可用数据中心，您可以从列表中选择数据中心。

有关更多信息，请参阅以下内容中的 _IBM Cloud Data Center 可用性_部分：
* [针对 vCenter Server 实例的需求和规划](/docs/services/vmwaresolutions/vcenter/vc_planning.html)
* [针对 vCenter Server with Hybridity Bundle 实例的需求和规划](/docs/services/vmwaresolutions/vcenter/vc_hybrid_planning.html)
* [针对 Cloud Foundation 实例的需求和规划](/docs/services/vmwaresolutions/sddc/sd_planning.html)
* [针对 VMware vSphere on {{site.data.keyword.cloud_notm}} 的需求和规划](/docs/services/vmwaresolutions/vsphere/vs_planning.html)
* [针对 NetApp ONTAP Select 实例的需求和规划](/docs/services/vmwaresolutions/netapp/np_planning.html)
* [针对 VMware Federal 实例的需求和规划](/docs/services/vmwaresolutions/vcenter/vc_fed_planning.html)

## 实例部署需要多长时间？

可以通过在 {{site.data.keyword.vmwaresolutions_short}} 控制台中查看实例详细信息页面上的部署历史记录，以检查实例部署的状态。

## VMware vSphere on IBM Cloud 是使用自动化来安装、配置和启动 VMware 堆栈的吗？

不是，VMware vSphere on {{site.data.keyword.cloud_notm}} 未使用 Cloud Foundation 和 vCenter Server 平台中的高级自动化。根据您订购的内容，该平台会交付可选的 VMware 许可证以及 ESXi 服务器，还可以选择交付 FortiGate 物理防火墙的 HA 对。如果创建了一个新集群，那么还会供应三个新的 VLAN：一个公用 VLAN，两个专用 VLAN。

VMware ESXi 会自动安装在每个裸机服务器上，但您负责安装 vCenter Server 或 NSX 等其他任何 VMware 组件。虽然 vSphere on {{site.data.keyword.cloud_notm}} 会确保根据所选的 VMware 组件订购与 VMware 兼容的硬件，但不存在任何自动化来配置和启动 VMware 环境。您负责设计和构造 IBM 托管的环境。

## 如何查看所有通知的列表？

要查看完整的通知历史记录，请单击左侧导航窗格中的**通知**。

## 如果使用 IBM Cloud for VMware Solutions 时发生问题怎么办？

如果您需要有关 {{site.data.keyword.vmwaresolutions_short}} 的帮助，请通过下列其中一种支持渠道联系 IBM 支持人员。有关更多信息，请参阅[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic/trbl_support.html)。

### 相关链接

* [通知](/docs/services/vmwaresolutions/vmonic/notifications.html)
* [Cloud Foundation 实例](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html)
* [访问控制台](/docs/services/vmwaresolutions/vmonic/loginmethod.html)
* [用户帐户和设置](/docs/services/vmwaresolutions/vmonic/useraccount.html)
