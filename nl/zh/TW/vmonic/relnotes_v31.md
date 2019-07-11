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

# 3.1 版的版本注意事項
{: #relnotes_v31}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Data Protection and Disaster Recovery 單一節點試用版實例
{: #relnotes_v31-dr-bundle}

利用 Data Protection and Disaster Recovery 單一節點試用版，可以快速測試 {{site.data.keyword.cloud_notm}} 以將 VMware 工作負載移轉和回復到 {{site.data.keyword.cloud_notm}}。此試用版是 VMware vCenter Server on IBM Cloud 的一個版本，這是一個單一承租戶 VMware 平台，可以使用與內部部署環境相同的熟悉工具進行管理。此試用版包含 Veeam on {{site.data.keyword.cloud_notm}}、VMware HCX on {{site.data.keyword.cloud_notm}} 和 Zerto on {{site.data.keyword.cloud_notm}} 服務。

如需相關資訊，請參閱 [Disaster Recovery 單一節點試用版概觀](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview)。

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

現在，您可以讓 IBM Expert Services 與您的內部團隊協作，以部署、移轉和維護自己的 {{site.data.keyword.cloud_notm}} 解決方案，可以是從規劃到現代化的所有階段，或中間的任何一個階段。

您可以藉由從**開始使用**頁面要求商議，隨時將 {{site.data.keyword.cloud_notm}} Expert Services 新增到實例訂單。如需相關資訊，請參閱[要求 {{site.data.keyword.cloud_notm}} Expert Services](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices)。

## 與 IBM Cloud Cost Estimator 整合

現在，您可以在 {{site.data.keyword.cloud_notm}} 架構提供的統一預估工具中預估 {{site.data.keyword.vmwaresolutions_short}} 資源的成本。使用此功能，您可以儲存整個 {{site.data.keyword.cloud_notm}} 型錄中資源的 Snapshot，並將其儲存在單一 PDF 檔案下，您可以下載該檔案以供將來參考。成本預估器不是合約或確定報價，而僅是預估總成本。

如需成本預估器的相關資訊，請參閱[預估成本](/docs/billing-usage?topic=billing-usage-cost)。

## VMware vCenter Server 實例的更新
{: #relnotes_v31-vcs}

本版本對新部署的實例、叢集和主機套用了下列升級和改進：

* vSphere ESXi 6.5 Update 2（建置 6.5.0-13635690）
* vCenter Server Appliance 6.5 Update 2g（建置 6.5.0-13638625）

如需相關資訊，請參閱 [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

### 叢集的替代 ESXi 伺服器配置
{: #relnotes_v31-esxi-config}

現在您可以藉由選取現有的配置或不同於叢集內現有主機的替代配置，而將新的 ESXi 伺服器新增到現有叢集。從**新增伺服器**視窗訂購新伺服器時，可以立即選取叢集中的現有配置或選取新的	{{site.data.keyword.baremetal_short_sing}} 配置。這適用於所有 vCenter Server、vCenter Server with Hybridity，以及 vCenter Server with NSX-T 實例。

為了避免效能或穩定性問題，建議叢集在 CPU、RAM 及儲存空間等方面使用相同或類似的配置。這個功能適用於相同叢集內的硬體更新。

如需相關資訊，請參閱[擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers)。

### 原則配置更新
{: #relnotes_v31-policy-config}

為 vCenter Server 主要實例產生的 vCenter 密碼現在長度為 15 個字元，並且具有下列密碼和鎖定原則配置：

* vCenter 密碼原則的最短長度現在為 15 個字元。
* 現在，vCenter 鎖定原則容許最多 3 次失敗的登入嘗試。
* 現在，vCenter 鎖定原則容許在相鄰失敗之間有 900 秒的時間間隔。

針對 vCenter Server 主要實例產生的 NSX Manager 密碼現在長度為 15 個字元。先前，所產生的密碼長度為 8 個字元。

 如需相關資訊，請參閱 [vCenter Server 實例的合規性資訊](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config)。

## 附加服務的更新
{: #relnotes_v31-services}

### HyTrust 授權的自動更新
{: #relnotes_v31-services-ht}

現在，{{site.data.keyword.vmwaresolutions_short}} 為已啟用「回撥」特性的 HyTrust 授權提供自動更新支援。從以下版本開始提供此支援：

* HyTrust CloudControl 5.5.1 和更高版本
* HyTrust DataControl 4.3.2 和更高版本
* HyTrust KeyControl 4.3.2 和更高版本

您必須完成對 HyTrust 虛擬機器 (VM) 啟用網際網路存取的程序，以確保自動更新授權。如果未完成此程序，授權將繼續以每年到期的方式進行。
{:important}

如需相關資訊，請參閱：

* [啟用對 HyTrust CloudControl VM 的網際網路存取](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [啟用對 HyTrust DataControl VM 的網際網路存取](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [啟用對 HyTrust KeyControl VM 的網際網路存取](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### Veeam on IBM Cloud
{: #relnotes_v31-services-veeam}

在現行版本中，Veeam Availability Suite 9.5 安裝在所有新部署的實例上。此外，還對 Veeam VSI 和 Veeam 配置儲存庫進行多個更新。如需相關資訊，請參閱 [Veeam on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)。

### Zerto on IBM Cloud
{: #relnotes_v31-services-zerto}

對於在 3.1 版和更高版本中部署的新實例，Zerto on {{site.data.keyword.cloud_notm}} 安裝需要一個計費 {{site.data.keyword.cloud_notm}} 帳戶。現在，VM 抄寫的成本使用 {{site.data.keyword.cloud_notm}} 計費方案而不是 {{site.data.keyword.cloud_notm}} 基礎架構計費。

若要訂購 Zerto on {{site.data.keyword.cloud_notm}}，{{site.data.keyword.cloud_notm}} 帳戶必須符合特定需求。如果有現有的 Zerto on {{site.data.keyword.cloud_notm}} 安裝，則可以將 Zerto VM 計費類型轉換為可計費。如需相關資訊，請參閱 [Zerto 抄寫計費](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing)。

## 新文件與更新的文件
{: #relnotes_v31-updated-doc}

* 已更新 Activity Tracker 實例管理事件和 KMIP for VMware on IBM Cloud 服務的事件。如需相關資訊，請參閱 [Activity Tracker 事件](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events)。
* 使用者 ID 參考文件藉由 {{site.data.keyword.cloud_notm}} 服務自動化，以用於安裝和配置服務的使用者 ID 進行更新。如需相關資訊，請參閱 [IBM 使用者 ID](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) 中的*服務使用者 ID* 區段。
* 為新的 API ``擷取叢集的詳細網路介面``提供了參考文件。如需相關資訊，請參閱 [API 參考資料](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}。
* 下列技術文件是使用者說明文件的*參照*小節中的新增內容：
  * [作業管理](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [第 2 天操作程序](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## 使用者介面更新和加強功能
{: #relnotes_v31-ui}

使用者介面已更新，並提供下列加強功能：
* 現在，**叢集**詳細資料頁面會顯示叢集使用的儲存空間的類型。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
