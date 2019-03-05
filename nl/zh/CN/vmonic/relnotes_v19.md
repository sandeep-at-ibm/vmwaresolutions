---

copyright:

  years:  2016, 2019

lastupdated: "2017-10-13"

---

# V1.9 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VMware vSphere on IBM Cloud

本发行版引入了 VMware vSphere on {{site.data.keyword.cloud_notm}} 产品。此产品支持根据所选 VMware 组件定制和订购与 VMware 兼容的计算、存储和网络资源，以构建您自己的 IBM 托管的 VMware 虚拟环境。虽然 vSphere on {{site.data.keyword.cloud_notm}} 不会自动安装、配置和打开可选的 VMware 组件，但您在设计和构造最适合您业务需求的环境方面将拥有最大的灵活性。首先创建 ESXi 服务器的新 vSphere 集群，或者首先对 {{site.data.keyword.CloudDataCent_notm}} 中的现有 vSphere 集群进行向外扩展。

有关更多信息，请参阅以下主题：
* [订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)
* [缩放现有 vSphere 集群](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)

## NetApp ONTAP Select on IBM Cloud

此发行版引入了 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} 产品，这是一种面向软件定义的存储器的虚拟设备，可将 NetApp ONTAP Select 实现为 IBM Cloud 的专用 {{site.data.keyword.baremetal_short}} 上的服务。NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} 同时在高性能（所有 SSD）和高容量（所有 SATA）配置中提供。
此产品可在专用基础架构上托管存储器，并提供多种 NetApp 功能，例如静态数据的去重、压缩和加密。使用高级数据管理功能，您可以在保护数据的同时，为存储资源供应敏捷性和灵活性。例如，使用快速高效的 NetApp Snapshot® 副本、FlexClone® 副本和 SnapMirror® 复制。

有关更多信息，请参阅以下主题：
* [NetApp ONTAP Select 概述](/docs/services/vmwaresolutions/netapp/np_netappoverview.html)
* [订购 NetApp ONTAP Select 实例](/docs/services/vmwaresolutions/netapp/np_orderinginstances.html)

## F5 on IBM Cloud 服务

F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} 服务现在可用于 VMware Cloud Foundation 和 VMware vCenter Server 实例。此服务提供本地和全球规模的智能 L4-L7 负载均衡和流量管理服务、稳健的网络和 Web 应用程序防火墙保护，以及安全和联合的应用程序访问。您可以在订购实例时就订购包含 F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} 服务的实例，也可以日后在 {{site.data.keyword.vmwaresolutions_short}} 控制台的实例属性详细信息页面上的**服务**选项卡中向现有实例添加此服务。根据您的需求，可为 BIG-IP VE 选择三个许可选项中的一个选项。

有关更多信息，请参阅以下主题：
* [F5 on {{site.data.keyword.cloud_notm}} 的注意事项](/docs/services/vmwaresolutions/services/f5_considerations.html)
* [管理 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managing_f5.html)

## IBM-Integrated Managed Infrastructure 中的受管服务

IBM-Integrated Managed Infrastructure (IMI) 中的受管服务现在可用于 VMware Cloud Foundation 实例。IMI 可以通过模块化服务简化 VMware 虚拟基础架构管理，并可以充当可信的单个提供者，以降低监视和管理虚拟 IT 基础架构的复杂性。将某些日常操作卸载到 IMI（例如，监视），以便您可以将精力集中在更高价值的计划上。

可以在**入门**页面中随时请求咨询和估算。
有关更多信息，请参阅[向 IMI 请求受管服务](/docs/services/vmwaresolutions/services/managing_imi.html#requesting-managed-services-from-imi)。

## vCenter Server 和 NetApp ONTAP Select 实例的实例名称限制

订购实例时，在 {{site.data.keyword.vmwaresolutions_short}} 上输入的实例名称不能包含特殊字符（例如，短划线字符）。只允许使用字母数字字符。此限制不适用于 Cloud Foundation 实例。

有关更多信息，请参阅以下主题：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [订购 NetApp ONTAP Select 实例](/docs/services/vmwaresolutions/netapp/np_orderinginstances.html)

## 对 VMware Cloud Foundation 实例的更新

### 定制实例的 CPU 和内存

在预构建并经过测试的“小型”和“标准”选项旁边，提供了用户定制的服务器选项。为了更好地将工作负载的 CPU/RAM 比率与 VMware 兼容硬件相匹配，现在可以独立选择双 CPU 服务器上的总核心数以及 RAM 量。本地存储器不可定制。

有关更多信息，请参阅[订购 Cloud Foundation 实例](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)。

## 对 VMware vCenter Server 实例的更新

### 跨数据中心集群支持

为了增强托管 VMware 环境的向外扩展，现在可在其他 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) pod 中创建新集群，或在与实例中部署的初始集群不同的 {{site.data.keyword.CloudDataCent_notm}} 中创建新集群。

有关更多信息，请参阅[添加和查看 vCenter Server 实例的集群](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)。

### 更改组件

此发行版消除了当 Single Sign-On 管理员从本机 VMware 工具更改某些 vCenter Server 资源时，对 {{site.data.keyword.vmwaresolutions_short}} 控制台中操作的影响。例如，现在可以在 VMware vSphere Web Client 中修改 VMware 虚拟数据中心、集群、交换机、端口组和数据存储名称，以根据公司或个人命名约定来定制部署，而不会对 {{site.data.keyword.vmwaresolutions_short}} 控制台中的操作造成任何下游影响。

有关更多信息，请参阅[更改 vCenter Server 实例组件产生的影响](/docs/services/vmwaresolutions/vcenter/vcenter_chg_impact.html)。

### 更多 RAM 大小

订购 vCenter Server 实例或为 vCenter Server 实例添加集群时，现在有更多 RAM 大小可供选择，以帮助将工作负载的 CPU/RAM 比率与硬件相匹配。在 {{site.data.keyword.vmwaresolutions_short}} 控制台中订购服务器时，**用户定制**配置选项中提供了以下选项：64 GB、128 GB、256 GB、384 GB、512 GB、768 GB、1.5 TB。

有关更多信息，请参阅[订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)。

### 网络文件系统版本更新

网络文件系统 (NFS) V4.1 不再作为用户界面中的存储设置提供。所有 vCenter Server 实例都通过 NFS V3 进行部署。虽然 NFS V3 是较旧的协议版本，但它在支持 VMware 存储分布式资源调度程序 (SDRS) 和 Storage I/O Control (SIOC) 的 VMware 环境中启用了增强的功能。

有关更多信息，请参阅[订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)。

### 单站点域名服务器域名

现在，可以在订购期间为 vCenter Server 实例提供域名服务器 (DNS) 域名。Microsoft Windows Server 虚拟服务器实例 (VSI) 已部署并可进行查找，它充当在其中注册主机和虚拟机的实例的 DNS。此外，还在 Microsoft Windows VSI 上设置了 Microsoft Active Directory (AD)，并且 DNS 域名是 AD 域林根。此 Microsoft Windows VSI 仅在 V1.9 及更高版本中可用。

有关更多信息，请参阅以下主题：
* [vCenter Server 概述](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html)
* [查看 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_viewinginstances.html)

## Windows Server 自动安装更新的需求

Microsoft Active Directory (AD) / 域名服务器 (DNS) 自动设置为仅下载更新。不会自动安装和重新启动这些更新。您必须以手动方式安装更新并在安排的时间重新启动，以避免对正在进行的 Active Directory 服务器配置和其他备份作业造成任何中断。要应用 Windows 更新，请手动安装更新。

## 新增和更新的文档

* 了解如何保护专用多站点 Cloud Foundation 实例，同时将 VMware 应用程序扩展为使用公共 {{site.data.keyword.cloud_notm}} 服务。有关更多信息，请参阅[安全连接 {{site.data.keyword.cloud_notm}} 中的专用 VMware 工作负载](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}。
* 提供了更多文档，描述如何配置防火墙以允许来自 IBM CloudDriver 和 SDDC Manager 虚拟机的所有协议通信。有关更多信息，请参阅 [Fortinet on {{site.data.keyword.cloud_notm}} 的组件和注意事项](/docs/services/vmwaresolutions/services/fsa_considerations.html)。
