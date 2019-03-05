---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-28"

---

# V2.8 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Migration and App Modernization 单节点试用版实例

通过 Migration and App Modernization 单节点试用版，可以快速试用 {{site.data.keyword.cloud_notm}}，以将 VMware 工作负载迁移到 {{site.data.keyword.cloud_notm}}，然后使用容器对工作负载进行现代化。此试用版是 {{site.data.keyword.icpfull_notm}} Hosted on VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的一个版本，提供了针对容器的 Kubernetes 管理平台，同时提供了可以使用与内部部署环境相同的熟悉工具进行管理的单租户 VMware 平台。

有关更多信息，请参阅 [Migration and App Modernization 单节点试用版概述](/docs/services/vmwaresolutions/vcenter/cloud_modern_bundle_overview.html)。

## 添加和除去网络文件系统存储器

从 V2.8 发行版开始，现在可以向现有 NFS 或 vSAN vCenter Server 集群添加网络文件系统 (NFS) 存储共享，也可以从现有 vCenter Server 集群中除去 NFS 文件共享。


对于定制共享文件级别的存储器，现在提供了以下选项：

* NFS 共享大小，最低 20 GB，最高 12 TB，以单个 GB 为单位递增
* 0.25 IOPS/GB 

有关更多信息，请参阅[扩展和收缩 vCenter Server 实例的容量](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservers.html#adding-nfs-storage-to-vcenter-server-instances)中的*向 vCenter Server 实例添加 NFS 存储器*和*从 vCenter Server 实例中除去 NFS 存储器*部分。

## SAP 认证的 Broadwell E5-2690 和 E7-8890 服务器支持

从 V2.8 发行版开始，以下新的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 型号可用于部署 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 和 VMware vSphere on {{site.data.keyword.cloud_notm}} 实例与集群：

* 双 Intel Xeon E5-2690 V4 处理器 / 共 28 个核心，2.60 GHz / 512 GB RAM
* 四核 Intel Xeon E7-8890 V4 处理器 / 共 96 个核心，2.20 GHz / 1024 GB RAM
* 四核 Intel Xeon E7-8890 V4 处理器 / 共 96 个核心，2.20 GHz / 2048 GB RAM
* 四核 Intel Xeon E7-8890 V4 处理器 / 共 96 个核心，2.20 GHz / 4096 GB RAM

有关更多信息，请参阅以下内容中的 *{{site.data.keyword.baremetal_short_sing}} 设置*部分：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## Broadwell E7-4820 和 E7-4850 服务器支持

从 V2.8 发行版开始，以下新的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 型号可用于部署 vCenter Server、vCenter Server with Hybridity Bundle、vCloud Foundation 和 vSphere on {{site.data.keyword.cloud_notm}} 实例与集群：

* 四核 Intel Xeon E7-4820 V4 / 共 40 个核心，2.0 GHz
* 四核 Intel Xeon E7-4850 V4 / 共 64 个核心，2.1 GHz

有关更多信息，请参阅以下内容中的 *{{site.data.keyword.baremetal_short_sing}} 设置*部分：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [订购 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/vcenter/vc_hybrid_orderinginstance.html#bare-metal-server-settings)
* [订购 Cloud Foundation 实例](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## 嵌入式 Platform Services Controller

从 V2.8 发行版开始，vCenter Server 部署有嵌入式 PSC (Platform Services Controller)，即 vCenter Server、vCenter Server 组件和 PSC 都部署在单个虚拟机上。此更改会应用于所有新部署的 vCenter Server、vCenter Server with Hybridity 和 NetApp 实例。

对于从更低发行版升级到 V2.8 的实例，PSC 未嵌入在 vCenter Server 中。如果要使用嵌入式 PSC，您必须自行从外部 PSC 转换为嵌入式 PSC。

在多站点配置中，主实例是手动将外部 PSC 转换为嵌入式 PSC 的已升级实例，任何新部署的 V2.8 辅助实例都具有嵌入式 PSC。

有关更多信息，请参阅 [vCenter Server 概述](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html#vcenter-server-architecture)中的 *vCenter Server 体系结构*部分。

## 对 VMware vCenter Server 实例的更新

本发行版应用了以下升级和改进：

* vSphere ESXi 6.5 Update P3（构建 6.5.0-10884925）
* vCenter Server 6.5 U2d（构建 6.5.0-10964411）
* Platform Services Controller 6.5 U2d（构建 6.5.0-10964411）

## 对 VMware Cloud Foundation 实例的更新

本发行版应用了以下升级和改进：

* vSphere ESXi 6.5 Update EP11（构建 6.5.0-10719125）
* vCenter Server 6.5 U2c（构建 6.5.0-9451637）
* Platform Services Controller 6.5 U2c（构建 6.5.0-9451637）

## 对附加组件服务的更新

### IBM Spectrum Protect Plus on IBM Cloud

当前发行版在所有新部署的实例上安装 IBM Spectrum Protect™ Plus V10.1.2。有关 IBM Spectrum Protect Plus V10.1.2 中新增功能的更多信息，请参阅 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}。

### KMIP for VMware on IBM Cloud

先前，可以订购包含 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的 Cloud Foundation 或 vCenter Server 实例，也可以在初始部署后向现有 Cloud Foundation 或 vCenter Server 实例添加此服务。

从 V2.8 发行版开始，该服务作为独立服务提供，无需与 VMware 实例相关联。每个服务实例都可以为一个或多个 Cloud Foundation 实例、vCenter Server 实例或 vSphere 集群提供服务。

**注**：在此发行版中，KMIP for VMware on {{site.data.keyword.cloud_notm}} 限制为仅使用 vSphere 加密。

有关更多信息，请参阅 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html)。

## 参考体系结构文档

用户文档的*参考*部分中提供了新的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 解决方案体系结构技术文档。有关更多信息，请参阅 [KMIP for VMware 概述](/docs/services/vmwaresolutions/archiref/kmip/overview.html)。

## 用户界面更新和增强功能

用户界面已更新，并提供了以下增强功能：

* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
