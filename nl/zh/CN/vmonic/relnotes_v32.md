---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.2 发行说明
{: #relnotes_v32}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}。

## VMware HCX for IBM Cloud 可用性
{: #relnotes_v32-HCX}

从 3.2 发行版开始，您现在可以选择随 VMware vCenter Server 实例一起订购 VMware HCX on {{site.data.keyword.cloud_notm}} 服务。先前，HCX on {{site.data.keyword.cloud_notm}} 服务只能通过 VMware vCenter Server with Hybridity Bundle 实例进行订购。vCenter Server with Hybridity Bundle 实例不再可用。

订购 HCX on {{site.data.keyword.cloud_notm}} 服务时，需要承诺使用 12 个月。在 12 个月承诺期到期后，您可以在 {{site.data.keyword.cloud_notm}} 服务上安装和卸载 HCX，并且可以添加和除去主机和集群，没有任何限制。随后会按月向您的帐户收费，您可以随时取消。

有关更多信息，请参阅 [VMware HCX on IBM Cloud 概述](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations)。

## VMware vSphere 6.7 Update 2 支持
{: #relnotes_v32-vsphere-v67}

您现在可以选择随 VMware vCenter Server、VMware vCenter Server with NSX-T 和 VMware vSphere on IBM Cloud 实例一起订购 VMware vSphere V6.7 Update 2。vSphere Enterprise Plus 6.7u2 替代了随新实例一起订购 vSphere Enterprise Plus 6.7u1 的选项。此外，Single-node Trial for Migration and App Modernization 实例和 Single-node Trial for Data Protection and Disaster Recovery 实例现在随 vSphere Enterprise Plus 6.7u2 一起订购。

vSphere Enterprise Plus 6.7u2 仅可用于 Skylake、Cascade 和 Broadwell {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}。


如果您有使用 vSphere Enterprise Plus 6.7u1 的现有实例，那么可以选择添加使用 vSphere Enterprise Plus 6.7u1 或 vSphere Enterprise Plus 6.7u2 的新主机。但是，添加新的 6.7u1 主机并不安全。建议您尽快将主机更新为最新的 ESXi 服务器版本。
{:note}

## Cascade Lake 支持
{: #relnotes_v32-cascade}

从 V3.2 发行版开始，以下新的 {{site.data.keyword.baremetal_short_sing}} CPU 型号可用于部署使用 VMware vSphere 6.7 Update 2 的实例和集群。这适用于 vCenter Server、vCenter Server with NSX-T 和 VMware vSphere。

* 双 Intel Xeon Gold 4210 处理器 / 共 20 个核心，2.3 GHz
* 双 Intel Xeon Gold 5218 处理器 / 共 32 个核心，2.3 GHz
* 双 Intel Xeon Gold 6248 处理器 / 共 40 个核心，2.5 GHz

Cascade Lake {{site.data.keyword.baremetal_short}} 在多专区区域 {{site.data.keyword.CloudDataCents_notm}} 上可用。有关更多信息，请参阅[多专区区域 (MZR) 概述](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview)。

有关 {{site.data.keyword.baremetal_short_sing}} 设置的更多信息，请参阅：

* [订购 vCenter Server 实例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [订购 vCenter Server with NSX-T 实例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [订购新的 vSphere 集群](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## 对 VMware vCenter Server 实例的更新
{: #relnotes_v32-vcs}

本发行版对新部署的实例、集群和主机应用了以下升级和改进：

* VMware NSX for vSphere 6.4.5（构建 13282012）
* vSphere ESXi 6.7 EP 10（构建 6.7.0-13981272）
* vCenter Server Appliance 6.7 Update 2b (6.7.0.-13843469)
* Platform Services Controller 6.7 Update 2b (6.7.0.-13843469)

有关更多信息，请参阅 [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

### 初始集群命名
{: #relnotes_v32-vcs-initial-cluster}

现在，在下实例订单的同时，可以指定要创建的初始集群的名称。有关更多信息，请参阅：

* [订购 vCenter Server 实例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [订购 vCenter Server with NSX-T 实例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## 对 VMware vSphere 实例的更新
{: #relnotes_v32-vss}

订购仅使用专用网络的新 vSphere 集群时，不再需要公用 VLAN。

有关更多信息，请参阅[订购新的 vSphere 集群](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings)中的*网络接口设置*部分。

## 对附加组件服务的更新
{: #relnotes_v32-services}

此发行版在新部署的实例上安装以下服务版本：

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Update 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Update 4

### VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} 服务现在可用于部署或升级到 V3.2 或更高发行版的 VMware vCenter Server 实例。

此服务提供与 vRealize Operations Manager (vROps) 集成的 VMware vRealize Log Insight (vRLI)，以帮助您监视和主动管理虚拟化环境的运行状况和性能，以及通过过滤和搜索日志来对问题的根本原因进行分析。

您可以订购包含 vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} 服务的 vCenter Server 实例，或者以后在实例详细信息页面上的“服务”选项卡上将此服务添加到现有实例。

您还可以将自己的企业 vRealize Operations 和 vRealize Log Insight 许可证用于云（按 CPU 或 OSI），也可以向 IBM Cloud 租用许可证。

有关更多信息，请参阅 [VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview)。

## 新增和更新的文档
{: #relnotes_v32-updated-doc}

* Activity Tracker 文档已更新。有关更多信息，请参阅 [Activity Tracker 事件](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events)。

## 用户界面更新和增强功能
{: #relnotes_v32-ui}

用户界面已更新，并提供了以下增强功能：

* 更改了实例名称需求。有关更多信息，请参阅要订购的实例类型的相应主题。
* 更改了标准 ESXi 服务器的格式。有关更多信息，请参阅要订购的实例类型的相应主题。
* 在主机和集群名称中添加了前导零，以支持正确排序。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
