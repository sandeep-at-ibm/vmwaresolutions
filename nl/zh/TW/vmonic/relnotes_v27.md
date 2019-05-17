---

copyright:

  years:  2016, 2018

lastupdated: "2018-12-14"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# 2.7 版的版本注意事項
{: #relnotes_v27}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## SAP 認證的 6140 伺服器支援
{: #relnotes_v27-sap}

從 2.7 版開始，下列新的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 型號可用於部署 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 及 VMware vSphere on {{site.data.keyword.cloud_notm}} 實例和叢集：
* 雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz / 192 GB RAM
* 雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.2 GHz / 384 GB RAM
* 雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz / 768 GB RAM

如需相關資訊，請參閱下列主題中的 *{{site.data.keyword.baremetal_short_sing}} 設定* 小節：
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-bare-metal-settings)
* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-bare-metal-settings)

## 附加服務的更新
{: #relnotes_v27-services}

### IBM Cloud Private Hosted
{: #relnotes_v27-icp}

{{site.data.keyword.cloud_notm}} Private Hosted 服務不僅可用於部署在（或升級至）2.5 版或更新版本的 VMware vCenter Server 實例，現在還可用於 VMware vCenter Server with Hybridity Bundle 實例。您現在可以在訂購 vCenter Server 實例或 vCenter Server with Hybridity Bundle 實例時包括該服務。您也可以在起始部署之後，將該服務新增至現有 vCenter Server 實例或 vCenter Server with Hybridity Bundle 實例。

如需相關資訊，請參閱下列主題：
* [{{site.data.keyword.cloud_notm}} Private Hosted 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [訂購 {{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)

### Mission Critical VMware on IBM Cloud
{: #relnotes_v27-mcv}

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 服務現在可用於部署在（或升級至）2.7 版或更新版本的實例。

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 提供多區域雲端架構，可協助企業避免雲端應用程式的關閉，以及在雲端地區內自動失效接手。與使用內部部署環境或競爭雲端平台的大部分 VMWare 用戶端相較，此雲端架構可讓您達到更高的可用性和失效接手成功率。

如需相關資訊，請參閱 [Mission Critical VMware on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-mcv_overview)。

### F5 on IBM Cloud
{: #relnotes_v27-f5}

現在當您訂購 F5 on {{site.data.keyword.cloud_notm}} 服務時，可以選擇要讓 F5 透過公用網路還是透過具有 Proxy 伺服器的專用網路來套用授權。如需相關資訊，請參閱[訂購 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)。

### FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v27-fva}

Fortinet 已於 2018 年第 3 季變更其訂閱組合。如需相關資訊，請參閱[訂購 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)。

對於部署在 2.7 版及更新版本 Cloud Foundation 實例和 vCenter Server 實例中的 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務，會佈建 FortiOS 6.0.3。

當您訂購 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 時，可以選擇要 FortiGuard 透過公用網路還是透過具有 Proxy 伺服器的專用網路，來套用授權和安全更新項目。如需相關資訊，請參閱[訂購 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)。

### Zerto on IBM Cloud 服務元件更新
{: #relnotes_v27-zerto}

對於部署在 2.7 版及更新版本 Cloud Foundation 實例和 vCenter Server 實例中的 Zerto on {{site.data.keyword.cloud_notm}} 服務，會佈建 Zerto Virtual Replication 6.0 Update 3。如需相關資訊，請參閱 [Zerto on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)。

### KMIP for VMware on IBM Cloud 與 IBM Cloud Activity Tracker 的整合
{: #relnotes_v27-kmip-icat}

除了 VMware 實例事件之外，KMIP for VMware on {{site.data.keyword.cloud_notm}} 的事件（例如金鑰建立、金鑰刪除及金鑰存取）現在已與 {{site.data.keyword.cloud_notm}} Activity Tracker 實例整合。

### KMIP for VMware on IBM Cloud - 已淘汰
{: #relnotes_v27-kmip-deprecated}

（已於 2018 年 12 月 14 日更新）現行 KMIP for VMware on {{site.data.keyword.cloud_notm}} 版本即將淘汰。如需相關資訊，請參閱[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。
{:deprecated}

## 新文件與更新的文件
{: #relnotes_v27-new-docs}

### 參照架構文件
{: #relnotes_v27-ref-archi}

現在可於使用者說明文件的*參照* 小節中取得下列技術文件：

* [NSX Edge Services Gateway 解決方案架構](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx_overview)
* [VMware Update Manager 手冊](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro)
* [vCenter Server 網路手冊](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro)
* [vCenter Server 和 {{site.data.keyword.cloud_notm}} Private 手冊](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [vCenter Server 和 IBM Kubernetes 服務手冊](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro)
* [VMware 和 Skate Advisor 概念車手冊](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro)
* [VMware - Stock Trader 的現代化旅程](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney)

## 使用者介面更新和加強功能
{: #relnotes_v27-ui}

使用者介面已更新，並提供下列加強功能：

* 當您訂購實例時，供您指定 {{site.data.keyword.baremetal_short_sing}} 設定的 CPU 型號和 RAM 的**自訂**標籤，現在會根據伺服器類型而分成 **Skylake** 標籤和 **Broadwell** 標籤，以協助您進行伺服器選取。
* Bare Metal Server 配置的**預先配置**選項已無法再使用。
* **類型**直欄現在包含在**資源**頁面上的 **vCenter Server 實例**表格中，用來識別 vCenter Server、vCenter Server with Hybridity Bundle，以及 vCenter Limited Test Drive 實例。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
