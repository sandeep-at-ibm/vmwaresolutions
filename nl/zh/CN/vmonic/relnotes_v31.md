---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: release notes, what's new, version 3.1

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.1 发行说明
{: #relnotes_v31}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Data Protection and Disaster Recovery 单节点试用版实例
{: #relnotes_v31-dr-bundle}

利用 Data Protection and Disaster Recovery 单节点试用版，可以快速试用 {{site.data.keyword.cloud_notm}} 以将 VMware 工作负载迁移和恢复到 {{site.data.keyword.cloud_notm}}。此试用版是 VMware vCenter Server on IBM Cloud 的一个版本，这是一个单租户 VMware 平台，可以使用与内部部署环境相同的熟悉工具进行管理。此试用版包含 Veeam on {{site.data.keyword.cloud_notm}}、VMware HCX on {{site.data.keyword.cloud_notm}} 和 Zerto on {{site.data.keyword.cloud_notm}} 服务。

有关更多信息，请参阅 [Disaster Recovery 单节点试用版概述](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview)。

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

现在，您可以让 IBM Expert Services 与您的内部团队协作，以部署、迁移和维护自己的 {{site.data.keyword.cloud_notm}} 解决方案，可以是从规划到现代化的所有阶段，或中间的任何一个阶段。

您可以通过在**入门**页面中请求咨询，随时将 {{site.data.keyword.cloud_notm}} Expert Services 添加到实例订单。有关更多信息，请参阅[请求 {{site.data.keyword.cloud_notm}} Expert Services](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices)。

## 与 IBM Cloud Cost Estimator 集成

现在，您可以在 {{site.data.keyword.cloud_notm}} 框架提供的统一估算工具中估算 {{site.data.keyword.vmwaresolutions_short}} 资源的成本。通过此功能，您可以保存整个 {{site.data.keyword.cloud_notm}}“目录”中的资源的快照，并将其存储在单个 PDF 文件下，您可以下载该文件以供将来参考。成本估算工具不是合同或公司报价，而仅是估算总成本。

有关成本估算工具的更多信息，请参阅[估算成本](/docs/billing-usage?topic=billing-usage-cost)。

## 对 VMware vCenter Server 实例的更新
{: #relnotes_v31-vcs}

本发行版对新部署的实例、集群和主机应用了以下升级和改进：

* vSphere ESXi 6.5 Update 2（构建 6.5.0-13635690）
* vCenter Server Appliance 6.5 Update 2g（构建 6.5.0-13638625）

有关更多信息，请参阅 [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

### 集群的备用 ESXi 服务器配置
{: #relnotes_v31-esxi-config}

现在您可以通过选择现有配置或不同于集群中现有主机的替代配置，将新的 ESXi 服务器添加到现有集群。从**添加服务器**窗口订购新服务器时，可以立即选择集群中的现有配置或选择新的	{{site.data.keyword.baremetal_short_sing}} 配置。这适用于所有 vCenter Server、vCenter Server with Hybridity 和 vCenter Server with NSX-T 实例。

为了避免性能或稳定性问题，建议集群使用相同或类似的 CPU、RAM 和存储器配置。此功能对于同一集群中的硬件更新非常有用。

有关更多信息，请参阅[扩展和收缩 vCenter Server 实例的容量](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers)。

### 策略配置更新
{: #relnotes_v31-policy-config}

为 vCenter Server 主实例生成的 vCenter 密码现在长度为 15 个字符，并且具有以下密码和锁定策略配置：

* vCenter 密码策略的最短长度现在为 15 个字符。
* 现在，vCenter 锁定策略允许最多 3 次失败的登录尝试。
* 现在，vCenter 锁定策略允许在相邻失败之间有 900 秒的时间间隔。

为 vCenter Server 主实例生成的 NSX Manager 密码现在长度是 15 个字符。先前，生成的密码长度为 8 个字符。

 有关更多信息，请参阅 [vCenter Server 实例的合规性信息](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config)。

## 对附加组件服务的更新
{: #relnotes_v31-services}

### HyTrust 许可证的自动更新
{: #relnotes_v31-services-ht}

现在，{{site.data.keyword.vmwaresolutions_short}} 为已启用“回拨”功能的 HyTrust 许可证提供自动更新支持。从以下版本开始提供此支持：

* HyTrust CloudControl 5.5.1 和更高版本
* HyTrust DataControl 4.3.2 和更高版本
* HyTrust KeyControl 4.3.2 和更高版本

您必须完成对 HyTrust 虚拟机 (VM) 启用因特网访问的过程，以确保自动更新许可证。如果未完成此过程，许可证将继续每年到期。
{:important}

有关更多信息，请参阅：

* [启用对 HyTrust CloudControl VM 的因特网访问](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [启用对 HyTrust DataControl VM 的因特网访问](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [启用对 HyTrust KeyControl VM 的因特网访问](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### Veeam on IBM Cloud
{: #relnotes_v31-services-veeam}

在当前发行版中，Veeam Availability Suite 9.5 安装在所有新部署的实例上。此外，还对 Veeam VSI 和 Veeam 配置存储库进行了若干更新。有关更多信息，请参阅 [Veeam on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)。

### Zerto on IBM Cloud
{: #relnotes_v31-services-zerto}

对于在 V3.1 和更高版本中部署的新实例，Zerto on {{site.data.keyword.cloud_notm}} 安装需要一个计费 {{site.data.keyword.cloud_notm}} 帐户。现在，VM 复制的成本使用 {{site.data.keyword.cloud_notm}} 计费套餐而不是 {{site.data.keyword.cloud_notm}} 基础架构计费。

要订购 Zerto on {{site.data.keyword.cloud_notm}}，{{site.data.keyword.cloud_notm}} 帐户必须满足特定需求。如果有现有的 Zerto on {{site.data.keyword.cloud_notm}} 安装，那么可以将 Zerto VM 计费类型转换为可计费。有关更多信息，请参阅 [Zerto 复制计费](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing)。

## 新增和更新的文档
{: #relnotes_v31-updated-doc}

* 更新了 Activity Tracker 实例管理事件和 KMIP for VMware on IBM Cloud 服务的事件。有关更多信息，请参阅 [Activity Tracker 事件](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events)。
* 用户标识参考文档通过 {{site.data.keyword.cloud_notm}} 服务自动化使用用于安装和配置服务的用户标识进行了更新。有关更多信息，请参阅 [IBM 用户标识](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids)中的*服务用户标识*部分。
* 为新的 API ``检索集群的详细网络接口``提供了参考文档。有关更多信息，请参阅 [API 参考](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}。
* 以下技术文档是用户文档的*参考*部分中的新增内容：
  * [操作管理](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [第 2 天操作过程](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## 用户界面更新和增强功能
{: #relnotes_v31-ui}

用户界面已更新，并提供了以下增强功能：
* 现在，**集群**详细信息页面会显示集群使用的存储器的类型。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
