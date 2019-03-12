---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.3 发行说明
{: #relnotes_v23}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 和 Meltdown 修复

{{site.data.keyword.vmwaresolutions_short}} 发布了来自 VMware 的补丁，以响应称为 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 和 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

有关更多信息，请参阅[解决 Spectre 和 Meltdown 漏洞](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_fix_spectre)。

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

本发行版引入了 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 产品。vCenter Server with Hybridity Bundle 是一种托管的专用云，可帮助您快速、轻松地将内部部署基础架构扩展到云中。VMware 环境基于 IBM 提供的 VMware 软件定义的数据中心许可证，并包含 VMware HCX on {{site.data.keyword.cloud_notm}} 服务，该服务可以轻松、安全地将内部部署 vSphere 5.0+ 环境与 {{site.data.keyword.cloud_notm}} 站点相连接，以实现无缝的基础架构混合性和真正的应用程序移动性。

HCX on {{site.data.keyword.cloud_notm}} 服务仅通过 vCenter Server with Hybridity Bundle 实例提供。在第一次应用基本 vCenter Server V2.3 软件更新之后，可以将现有 vCenter Server 实例升级到 vCenter Server with Hybridity Bundle 实例。有关更多信息，请参阅[对 vCenter Server 实例应用更新](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)。

有关 vCenter Server with Hybridity Bundle 的更多信息，请参阅以下主题：

* [vCenter Server with Hybridity Bundle 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [针对 vCenter Server with Hybridity Bundle 实例的需求和规划](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [订购 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## 删除对 vCenter Server 和 Cloud Foundation 实例的集群支持

现在，可以从实例中删除集群，而不必删除整个实例。对于在 V2.2 或更低版本实例中部署的集群，必须将实例升级到 V2.3，才能删除已添加到实例的集群。

有关更多信息，请参阅以下主题：

* [添加、查看和删除 vCenter Server 实例的集群](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances#deleting-clusters-from-vcenter-server-instances)
* [添加、查看和删除 Cloud Foundation 实例的集群](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-adding-and-viewing-clusters-for-cloud-foundation-instances#deleting-clusters-from-cloud-foundation-instances)

## 对 VMware vCenter Server 实例的更新

本发行版应用了以下升级和改进：
*	VMware vSphere ESXi 6.5 U1g（应用了补丁级别 ESXi650-201803001 的 ESXi 6.5u1）
*	VMware vCenter Server 6.5 Update 1g

### vCenter Server 实例和集群的增强功能

从 V2.3 发行版开始，选择**定制**裸机设置时，以下新的 CPU 型号可供部署：
* 双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz
* 双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz

有关更多信息，请参阅以下主题：

* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [添加、查看和删除 vCenter Server 实例的集群](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

## 对 VMware Cloud Foundation 实例的更新

本发行版应用了以下升级和改进：
*	VMware vSphere ESXi 6.5 U1g（应用了补丁级别 ESXi650-201803001 的 ESXi 6.5u1）
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## 对附加组件服务的更新

### HyTrust CloudControl on IBM Cloud

现在，HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服务可用于运行 vSphere 6.5 以及部署在或已升级到 V2.3 或更高发行版中的 VMware Cloud Foundation 实例和 VMware vCenter Server 实例。该服务根据安全标准强制实施和控制合规性，并提供基于角色的访问控制 (RBAC)。与 HyTrust DataControl 组合使用时，该服务可确保虚拟机和工作负载数据不会离开 {{site.data.keyword.cloud_notm}} 数据中心内的特定区域、集群或 ESXi 服务器。

您可以在订购实例时订购包含此服务的实例，也可以日后向现有实例添加此服务。

有关更多信息，请参阅以下主题：
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 的组件和注意事项](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [管理 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)

### HyTrust DataControl on IBM Cloud

现在，HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服务可用于运行 vSphere 6.5 以及部署在或已升级到 V2.3 或更高发行版中的 VMware Cloud Foundation 实例和 VMware vCenter Server 实例。该服务通过集成密钥管理提供高强度加密功能，以确保工作负载在整个生命周期中的安全。此服务可以提供操作系统级别和数据级别的加密，这意味着可以对工作负载中的任何目录、文件夹或文件进行加密和解密。

您可以在订购实例时订购包含此服务的实例，也可以日后向现有实例添加此服务。

有关更多信息，请参阅以下主题：
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} 的组件和注意事项](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [管理 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)

### IBM Spectrum Protect Plus on IBM Cloud

当前发行版在所有新部署的实例上将 IBM Spectrum Protect&trade; Plus V10.1.1 安装为缺省备份服务。有关 IBM Spectrum Protect Plus V10.1.1 中新增功能的更多信息，请参阅 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}。

## 新增和更新的文档

新的 developerWorks 诀窍提供了有关如何向部署后的 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 添加存储器的逐步指示信息。有关更多信息，请参阅[向部署后的 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 添加存储器](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)。

## 用户界面更新和增强功能

用户界面已更新，并提供了以下增强功能：
* **一致性**：现在，用户界面的外观与 {{site.data.keyword.cloud_notm}} 上的其他服务一致。
* **轻松访问**：现在，可以直接在 {{site.data.keyword.cloud_notm}} **目录**中访问 VMware 产品。
* **精简优化的订购体验**：现在，只要在一个界面中就能完成订购 VMware 实例和部署其附加组件服务。此外，计算了估算成本后，该成本会立即在同一界面中显示，以便您可以根据成本计划来调整配置。
* 订购实例或添加集群时，自带许可证 (BYOL) 选项对于业务合作伙伴用户不可用。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
