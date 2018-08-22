---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

---

# V2.1 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的更多提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 和 Meltdown 修复

{{site.data.keyword.vmwaresolutions_short}} 发布了来自 VMware 的补丁，以响应称为 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 和 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

有关更多信息，请参阅[解决 Spectre 和 Meltdown 漏洞](../vmonic/trbl_fix_spectre.html)。

## VMware HCX on IBM Cloud

HCX on {{site.data.keyword.cloud_notm}} 服务现在可用于运行 vSphere 6.5 以及部署在或已升级到 V2.1 或更高发行版中的 VMware Cloud Foundation 实例和 VMware vCenter Server 实例。此服务可以将内部部署数据中心的网络无缝扩展到 {{site.data.keyword.cloud_notm}}，这允许虚拟机 (VM) 在不进行任何更改的情况下，在内部部署数据中心与 {{site.data.keyword.cloud_notm}} 之间进行双向迁移。通过建立第 2 层网桥，HCX 可利用 WAN 优化、去重、压缩和加密功能，更快、更安全地通过直接链路或 VPN 隧道迁移数据。批量迁移 VM 向后兼容 VMware vSphere 5.1 或更高版本。如果使用的是 vSphere 6.0 或更高版本的内部部署，那么可以通过 vMotion 将活动（已打开电源）的 VM 从内部部署迁移到 {{site.data.keyword.CloudDataCent_notm}}。使用 HCX 时，您无需将 VMware NSX 安装到数据中心。

您可以在订购实例时订购包含 HCX on {{site.data.keyword.cloud_notm}} 服务的 Cloud Foundation 或 vCenter Server 实例，也可以日后在实例详细信息页面上的**服务**选项卡中向现有实例添加此服务。

还可以订购内部部署 HCX 实例，以对内部部署 HCX 安装进行许可和激活。

有关更多信息，请参阅：
* [HCX on {{site.data.keyword.cloud_notm}} 的注意事项](../services/hcx_considerations.html)
* [管理 HCX on {{site.data.keyword.cloud_notm}}](../services/managinghcx.html)
* [内部部署 HCX 实例的注意事项](../services/standalone_considerations.html)
* [订购内部部署 HCX 实例](../services/standalone_orderingserviceinstances.html)

## 更灵活的自带许可证模型用于 VMware Cloud Foundation 和 vCenter Server

创建新集群时自带许可证 (BYOL) 或购买 IBM 提供的预订许可现在可用于 V2.1 和更高版本的 VMware Cloud Foundation 实例和 VMware vCenter Server 实例，支持您利用现有组件密钥或向 IBM 租用许可证。在 V2.1 之前，如果使用 BYOL，将无法购买针对特定 VMware 组件的 IBM 提供的许可。目前，仅 VMware vSphere 和 VMware vSAN 可用于针对每个集群进行许可。

此外，将节点添加到使用密钥许可的集群时，如果节点数超过密钥容量，控制台会提示您提供新的许可证密钥。

有关更多信息，请参阅：

* [添加和查看 Cloud Foundation 实例的集群](../sddc/sd_addingviewingclusters.html)
* [添加和查看 vCenter Server 实例的集群](../vcenter/vc_addingviewingclusters.html)
* [关于 BYOL 的常见问题](../vmonic/faq_byol.html)

## Zerto on IBM Cloud 服务组件更新

对于部署在 V2.1 和更高版本 Cloud Foundation 实例和 vCenter Server 实例中的 Zerto on {{site.data.keyword.cloud_notm}} 服务，将供应 Zerto Virtual Replication 5.5u2。出于性能原因，Zerto Virtual Replication 设备 (VRA) 现在会部署到管理数据存储（VSAN 或耐久性），而不是部署到本地数据存储。如果您有现有的 VRA，那么应考虑将其存储器迁移到管理数据存储，以提高性能。

有关更多信息，请参阅 [Zerto on {{site.data.keyword.cloud_notm}} 概述](../services/addingzertodr.html)。

## 对 VMware vCenter Server 实例的更新

### 网络 MTU 配置设置

对于 V2.1 或更高发行版，订购新的 vCenter Server 实例时，公用分布式虚拟交换机 (DVS) 设置为 MTU 1500（缺省值）。
有关更多信息，请参阅 [vCenter Server 材料清单](../vcenter/vc_bom.html)中的_网络 MTU 配置设置_。

### 自动对主机应用 VMware ESXi 补丁和更新

在 V2.0 和更低版本的 VMware vCenter Server 实例中，补丁不会自动应用于添加到集群的 ESXi 主机。

在 V2.1 和更高版本的实例中，自动化会将补丁应用于新的 ESXi 主机，这可使补丁级别与供应初始实例时的补丁级别相匹配。您负责手动应用任何未来的补丁和更新。
VMware 补丁和更新在未来发行版中可用时，自动化将扫描现有实例的 ESXi 主机，并通过电子邮件向您发送手动应用最新补丁和更新的提示。

有关更多信息，请参阅[对 vCenter Server 实例应用更新](../vcenter/vc_applyingupdates.html)。

### 对 VMware NSX 许可证升级的价格估算

现在，可以在提交订单以升级到 VMware NSX Advanced 或 Enterprise Edition 之前查看价格估算。定价基于 vCenter Server 实例中的 ESXi 主机数。此购买仅更改 NSX 许可证密钥，并将 VMware NSX Base Edition 升级到 Advanced 或 Enterprise Edition。此购买不会升级 NSX 软件版本。

有关更多信息，请参阅 [vCenter Server 概述](../vcenter/vc_vcenterserveroverview.html)。

### 每个集群的最大服务器数从 32 增加

对于实例中的缺省集群，最多可以部署或扩展至 51 个服务器。对于实例中的所有后续集群，最多可以部署或扩展至 59 个服务器。有关更多信息，请参阅[添加和查看 vCenter Server 实例的集群](../vcenter/vc_addingviewingclusters.html)。

**注**：此功能仅可用于在 V2.1 和更高版本中部署的实例。从 V2.1 之前的发行版升级到 V2.1 的实例没有此功能。

### 用户定制的 IBM Cloud 裸机服务器配置选项

现在，用户定制的裸机服务器配置提供双 Intel Xeon Gold 6140（共 36 个核心，2.3 GHz）。

有关更多信息，请参阅：
* [vCenter Server 概述](../vcenter/vc_vcenterserveroverview.html)
* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)

### 单个 NFS 文件共享配置

现在，可以选择逐个配置 NFS 文件共享。为每个文件共享分别选择文件大小和性能级别，或者为订购的所有文件共享选择相同的文件大小和性能级别。

有关更多信息，请参阅：
* [vCenter Server 概述](../vcenter/vc_vcenterserveroverview.html)
* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)
* [添加和查看 vCenter Server 实例的集群](../vcenter/vc_addingviewingclusters.html)

## 用户界面更新和增强功能

对整个用户界面进行了改进：

* 从左侧导航窗格中，除去了**订购实例**选项。单击**入门**可完成实例订购步骤。
* 订购实例时的**基本**页面中的**子域前缀**字段已重命名为**子域标签**。
* 现在，订购主或辅助 vCenter Server 或 Cloud Foundation 实例时，除了可以在**摘要**页面上查看成本估算外，还可以在为实例订单提供详细信息时，在任何面板上计算成本估算。
* 面包屑导航已作为导航备用方法添加到**部署的实例**页面中，从而减少了在这些页面上访问父页面所需的步骤数。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择适当的设置。

## 新增和更新的文档

新的 developerWorks 诀窍提供了有关如何使用 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} 将专用存储器连接到现有 {{site.data.keyword.vmwaresolutions_full}} 部署的逐步指示信息。有关更多信息，请参阅[将专用存储器连接到 VMware Solutions on IBM Cloud 的步骤](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)。
