---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.4 发行说明
{: #relnotes_v24}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 和 Meltdown 修复
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} 发布了来自 VMware 的补丁，以响应称为 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 和 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## 本地语言支持
{: #relnotes_v24-nls}

从 V2.4 发行版开始，本地语言支持 (NLS) 可用于 {{site.data.keyword.vmwaresolutions_short}}。控制台上的所有功能（包括用户文档）都提供多语言版本。

除了英语之外，还支持以下语言：
* 德语
* 西班牙语
* 法语
* 意大利语
* 日语
* 韩国语
* 巴西葡萄牙语
* 简体中文
* 繁体中文

## Skylake Xeon CPU 支持
{: #relnotes_v24-skylake}

从 V2.4 发行版开始，以下新的裸机服务器 CPU 型号可用于部署 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 和 VMware vSphere on {{site.data.keyword.cloud_notm}} 实例与集群：

* 双 Intel Skylake Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz
* 双 Intel Skylake Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz
* 双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz

有关更多信息，请参阅[订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)中的*裸机服务器设置*部分。

## 对 VMware vCenter Server 实例的更新
{: #relnotes_v24-vcs}

### 网络文件系统性能增强
{: #relnotes_v24-nfs}

设计用于要求最苛刻的工作负载类型的性能级别 10 IOPS/GB 不再仅限于特定 {{site.data.keyword.CloudDataCent_notm}}，现在可用于所有数据中心。有关更多信息，请参阅 [vCenter Server 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#technical-specifications-for-vcenter-server-instances)中的*存储*部分。

## 对附加组件服务的更新
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

当前发行版在所有新部署的实例上安装 IBM Spectrum Protect&trade; Plus V10.1.1 补丁 1。有关 IBM Spectrum Protect Plus V10.1.1 P1 中新增功能的更多信息，请参阅 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}。

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

现在，订购此服务时，有一个新选项可供您为 HCX 互连选择公用网络或专用网络。有关更多信息，请参阅[订购 VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)。

## 新增和更新的文档
{: #relnotes_v24-new-docs}

### 参考体系结构文档
{: #relnotes_v24-ref-archi}

现在，用户文档的*参考*部分中提供了 {{site.data.keyword.vmwaresolutions_short}} 体系结构文档。有关更多信息，请参阅[解决方案概述](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)。

### 服务文档
{: #relnotes_v24-docs-services}

服务信息已重构，并且导航也已改进，以便在订购服务时可轻松找到相关信息。

有关更多信息，请参阅以下主题：

* [订购 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [订购 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [订购 Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [订购 Hytrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [订购 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [订购 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [订购 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## 用户界面更新和增强功能
{: #relnotes_v24-ui}

用户界面已更新，并提供了以下增强功能：

* 现在，“添加集群”和“添加服务”窗格使用的页面格式具有更好的组织布局，支持您更高效地完成任务。
* **资源**页面的功能通过搜索、分页和排序功能得到了增强。通过这些改进，您可以极快找到实例。
* 现在，实例详细信息页面使用左侧导航菜单，通过该菜单，可以轻松、快速地访问实例信息。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
