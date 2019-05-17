---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 2.4 版的版本注意事項
{: #relnotes_v24}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 及 Meltdown 補救
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} 發行來自 VMware 的修補程式，以回應已知的 Spectre 及 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 及 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## 國家語言支援
{: #relnotes_v24-nls}

從 2.4 版開始，「國家語言支援 (NLS)」適用於 {{site.data.keyword.vmwaresolutions_short}}。
主控台上的所有特性（包括使用者文件）都提供數種語言版本。

除了英文之外，還支援下列語言：
* 德文
* 西班牙文
* 法文
* 義大利文
* 日文
* 韓文
* 巴西葡萄牙文
* 簡體中文
* 繁體中文

## Skylake Xeon CPU 支援
{: #relnotes_v24-skylake}

從 2.4 版開始，下列新的 Bare Metal Server CPU 型號可用於部署 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 及 VMware vSphere on {{site.data.keyword.cloud_notm}} 實例和叢集：

* 雙重 Intel Skylake Xeon Silver 4110 處理器 / 總計 16 核心，2.1 GHz
* 雙重 Intel Skylake Xeon Gold 5120 處理器 / 總計 28 核心，2.2 GHz
* 雙重 Intel Skylake Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz

如需相關資訊，請參閱 [Bare Metal Server 設定](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-bare-metal-settings)。

## VMware vCenter Server 實例的更新
{: #relnotes_v24-vcs}

### 網路檔案系統效能加強功能
{: #relnotes_v24-nfs}

效能層次 10 IOPS/GB 是針對要求最嚴苛的工作負載類型所設計，並且不再限制為特定 {{site.data.keyword.CloudDataCent_notm}}，現在可用於所有項目。如需相關資訊，請參閱[儲存空間](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vc_vcenterserveroverview-storage)。

## 附加服務的更新
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

現行版本會將 IBM Spectrum Protect&trade; Plus 10.1.1 版 Patch 1 安裝至所有新部署的實例。如需 IBM Spectrum Protect Plus 10.1.1 版 Patch 1 中新增特性的相關資訊，請參閱 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}。

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

在您訂購此服務時，現在可以使用新的選項來選擇公用網路與專用網路以進行 HCX 交互連接。如需相關資訊，請參閱[訂購 VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)。

## 新文件與更新的文件
{: #relnotes_v24-new-docs}

### 參照架構文件
{: #relnotes_v24-ref-archi}

{{site.data.keyword.vmwaresolutions_short}} 架構文件現在位於使用者文件的*參照* 小節中。如需相關資訊，請參閱[解決方案概觀](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)。

### 服務文件
{: #relnotes_v24-docs-services}

已重組服務資訊，並且已改良導覽，在您訂購服務時可輕鬆地找到相關資訊。

如需相關資訊，請參閱下列主題：

* [訂購 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [訂購 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [訂購 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [訂購 Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [訂購 Hytrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [訂購 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [訂購 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [訂購 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## 使用者介面更新和加強功能
{: #relnotes_v24-ui}

使用者介面已更新，並提供下列加強功能：

* 新增叢集及新增服務窗格現在會使用具有更有系統佈置的頁面格式，讓您更有效率地完成作業。
* 已使用搜尋、分頁和排序特性來加強**資源**頁面。這些改善可讓您快速地找到實例。
* 實例詳細資料頁面現在使用左導覽功能表，可讓您輕鬆且快速地存取實例資訊。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
