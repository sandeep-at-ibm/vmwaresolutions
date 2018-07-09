---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# V2.4 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的更多提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 和 Meltdown 修复

{{site.data.keyword.vmwaresolutions_short}} 发布了来自 VMware 的补丁，以响应称为 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 和 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

有关更多信息，请参阅[解决 Spectre 和 Meltdown 漏洞](../vmonic/trbl_fix_spectre.html)。

## 本地语言支持

从 V2.4 发行版开始，本地语言支持 (NLS) 可用于 IBM Cloud for VMware Solutions。控制台上的所有功能（包括用户文档）都提供多语言版本。

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

**注**：参考体系结构文档仅提供英语版本。

## Skylake Xeon CPU 支持

从 V2.4 发行版开始，以下新的裸机服务器 CPU 型号可用于部署 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}、VMware vSphere on {{site.data.keyword.cloud_notm}} 和 VMware Federal on {{site.data.keyword.cloud_notm}} 实例与集群：

* 双 Intel Skylake Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz
* 双 Intel Skylake Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz
* 双 Intel Skylake Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz

有关更多信息，请参阅以下内容中的*裸机服务器设置*部分：

* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [订购新的 vSphere 集群](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)
* [订购 VMware Federal 实例](../vcenter/vc_fed_orderinginstance.html#bare-metal-server-settings)

## 对 VMware vCenter Server 实例的更新

### 网络文件系统性能增强

设计用于要求最苛刻的工作负载类型的性能级别 10 IOPS/GB 不再仅限于特定 {{site.data.keyword.CloudDataCent_notm}}，现在可用于所有数据中心。有关更多信息，请参阅 [vCenter Server 概述](../vcenter/vc_vcenterserveroverview.html#vcenter-server-technical-specifications)中的*存储*部分。

## 对 VMware Federal 实例的更新

### 新增 IBM Cloud Data Center 选项

现在，您可以将 VMware Federal 实例部署到 DAL08 - 达拉斯（德克萨斯州）{{site.data.keyword.CloudDataCent_notm}}。有关更多信息，请参阅 [VMware Federal 实例的需求和规划](../vcenter/vc_fed_planning.html#ibm-cloud-data-center-availability)中的 *IBM Cloud Data Center 可用性*部分。

## 对附加组件服务的更新

### IBM Spectrum Protect Plus on IBM Cloud

当前发行版在所有新部署的实例上安装 IBM Spectrum Protect&trade; Plus V10.1.1 补丁 1。有关 IBM Spectrum Protect Plus IBM Cloud V10.1.1 补丁 1 中新增功能的信息，请参阅 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}。

### VMware HCX on IBM Cloud

现在，订购此服务时，有一个新选项可供您为 HCX 互连选择公用网络或专用网络。有关更多信息，请参阅[订购 VMware HCX on IBM Cloud](../services/hcx_ordering.html)。

## 新增和更新的文档

### 参考体系结构文档

现在，用户文档的*参考*部分中提供了 {{site.data.keyword.vmwaresolutions_short}} 体系结构文档。参考体系结构文档仅提供英语版本。有关更多信息，请参阅[解决方案概述](../archiref/solution/solution_overview.html)。

### 服务文档

服务信息已重构，并且导航也已改进，以便在订购服务时可轻松找到相关信息。

有关更多信息，请参阅：

* [订购 F5 on IBM Cloud](../services/f5_ordering.html)
* [订购 FortiGate Security Appliance on IBM Cloud](../services/fsa_ordering.html)
* [订购 FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_ordering.html)
* [订购 Hytrust CloudControl on IBM Cloud](../services/htcc_ordering.html)
* [订购 Hytrust DataControl on IBM Cloud](../services/htdc_ordering.html)
* [订购 IBM Spectrum Protect Plus on IBM Cloud](../services/spp_ordering.html)
* [订购 KMIP for VMware on IBM Cloud](../services/kmip_ordering.html)
* [订购 Veeam on IBM Cloud](../services/veeam_ordering.html)
* [订购 Zerto on IBM Cloud](../services/zerto_ordering.html)

## 用户界面更新和增强功能

用户界面已更新，并提供了以下增强功能：

* 现在，“添加集群”和“添加服务”窗格使用的页面格式具有更好的组织布局，支持您更高效地完成任务。
* **部署的实例**页面的功能通过搜索、分页和排序功能得到了增强。通过这些改进，您可以极快找到实例。
* 现在，实例详细信息页面使用左侧导航菜单，通过该菜单，可以轻松、快速地访问实例信息。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择适当的设置。
