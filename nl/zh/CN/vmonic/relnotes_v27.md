---

copyright:

  years:  2016, 2018

lastupdated: "2018-12-14"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V2.7 发行说明
{: #relnotes_v27}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## SAP 认证的 6140 服务器支持
{: #relnotes_v27-sap}

从 V2.7 发行版开始，以下新的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 型号可用于部署 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 和 VMware vSphere on {{site.data.keyword.cloud_notm}} 实例与集群：
* 双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz / 192 GB RAM
* 双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.2 GHz / 384 GB RAM
* 双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz / 768 GB RAM

有关更多信息，请参阅以下内容中的 *{{site.data.keyword.baremetal_short_sing}} 设置*部分：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## 对附加组件服务的更新
{: #relnotes_v27-services}

### IBM Cloud Private Hosted
{: #relnotes_v27-icp}

现在，{{site.data.keyword.cloud_notm}} Private Hosted 服务除了可用于部署在（或已升级到）V2.5 和更高发行版中的 VMware vCenter Server 实例外，还可用于 VMware vCenter Server with Hybridity Bundle 实例。现在，可以订购包含该服务的 vCenter Server 实例或 vCenter Server with Hybridity Bundle 实例。您还可以在初始部署后将该服务添加到现有 vCenter Server 实例或 vCenter Server with Hybridity Bundle 实例。

有关更多信息，请参阅以下主题：
* [{{site.data.keyword.cloud_notm}} Private Hosted 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [订购 {{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)

### Mission Critical VMware on IBM Cloud
{: #relnotes_v27-mcv}

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 服务现在可用于部署在（或已升级到）V2.7 或更高发行版中的实例。

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 交付多专区云体系结构，可帮助企业防止云应用程序发生停机时间，并可自动在云区域内执行故障转移。利用这种云体系结构实现的可用性和故障转移成功率，要高于大多数 VMware 客户机在内部部署环境或竞争对手的云平台中实现的可用性和故障转移成功率。

有关更多信息，请参阅 [Mission Critical VMware on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-mcv_overview)。

### F5 on IBM Cloud
{: #relnotes_v27-f5}

现在，订购 F5 on {{site.data.keyword.cloud_notm}} 服务时，可以选择是希望 F5 通过公用网络应用许可证，还是使用代理服务器通过专用网络应用许可证。有关更多信息，请参阅[订购 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)。

### FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v27-fva}

在 2018 年第 3 季度，Fortinet 更改了其预订捆绑软件。有关更多信息，请参阅[订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)。

对于部署在 V2.7 和更高版本 Cloud Foundation 实例和 vCenter Server 实例中的 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务，将供应 FortiOS 6.0.3。

订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 时，可以选择是希望 FortiGuard 通过公用网络应用许可证和安全更新，还是使用代理服务器通过专用网络应用许可证和安全更新。有关更多信息，请参阅[订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)。

### Zerto on IBM Cloud 服务组件更新
{: #relnotes_v27-zerto}

对于部署在 V2.7 和更高版本 Cloud Foundation 实例和 vCenter Server 实例中的 Zerto on {{site.data.keyword.cloud_notm}} 服务，将供应 Zerto Virtual Replication 6.0 Update 3。有关更多信息，请参阅 [Zerto on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)。

### 集成有 IBM Cloud Activity Tracker 的 KMIP for VMware on IBM Cloud
{: #relnotes_v27-kmip-icat}

现在，除了 VMware 实例事件之外，KMIP for VMware on {{site.data.keyword.cloud_notm}} 的事件（例如，密钥创建、密钥删除和密钥访问）也与 {{site.data.keyword.cloud_notm}} Activity Tracker 实例相集成。

### KMIP for VMware on IBM Cloud - 不推荐
{: #relnotes_v27-kmip-deprecated}

（更新时间：2018 年 12 月 14 日）不推荐使用当前版本的 KMIP for VMware on {{site.data.keyword.cloud_notm}}。有关更多信息，请[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。
{:deprecated}

## 新增和更新的文档
{: #relnotes_v27-new-docs}

### 参考体系结构文档
{: #relnotes_v27-ref-archi}

现在，用户文档的*参考*部分中提供了以下技术文档：

* [NSX Edge 服务网关解决方案体系结构](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx_overview)
* [VMware Update Manager 指南](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro)
* [vCenter Server 联网指南](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro)
* [vCenter Server 和 {{site.data.keyword.cloud_notm}} Private 指南](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [vCenter Server 和 IBM Kubernetes 服务指南](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro)
* [VMware 和 Skate Advisor 概念车指南](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro)
* [VMware - Stock Trader 现代化之旅](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney)

## 用户界面更新和增强功能
{: #relnotes_v27-ui}

用户界面已更新，并提供了以下增强功能：

* 原先订购实例时，可在其中指定 {{site.data.keyword.baremetal_short_sing}} 的 CPU 型号和 RAM 设置的**定制**选项卡，现已根据服务器类型拆分为 **Skylake** 和 **Broadwell** 选项卡，以帮助您选择服务器。
* 裸机服务器配置的**预配置**选项不再可用。
* 现在，**类型**列包含在**资源**页面上的 **vCenter Server 实例**表中，可用于识别 vCenter Server、vCenter Server with Hybridity Bundle 和 vCenter Limited Test Drive 实例。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
