---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

---

# 操作程序簡介
{: #opsprocs-intro}

許多 IT 組織會在 Runbook 中記錄他們的作業程序。Runbook 是一組標準化文件、參考資料及程序，可說明重複進行的一般 IT 作業。IT 人員會參閱 Runbook，以取得完成工作的最佳方式。Runbook 透過標準化來提升組織效率，並更有效地協助加入的員工。Runbook 通常有兩種類型：

1. 一般文件，用於擷取程序、手冊和作業。它們通常會是一般的性質，並參照供應商提供的現有文件。
2. 為企業撰寫的專門文件。此文件是特別針對系統、應用程式或應用程式套組，且供應商文件未涵蓋。在記錄專用文件時，建議採用下列結構：

 * 概觀 - 服務的概觀，具有小節來說明下列各項：
    * 何謂服務，以及企業為何需要服務？
    * 誰是服務的主要聯絡人？
    * 如何報告服務的問題。
 * 建置 - 本節著重於開發團隊、服務的主要軟體元件，以及如何建構服務。軟體產品的相關資訊、OVA 的位置、配送媒體或原始碼的位置。包裝或配送版本的必要步驟。它包含開發人員如何開始使用的任何必要指示。
 * 部署 - 本節著重於作業團隊，以及如何部署軟體。它包含硬體及虛擬化基礎架構的詳細資料，以及如何建置虛擬機器 (VM)，包括：vCPU、RAM 及磁碟需求、OS 版本及配置、要安裝的中介軟體或套件。
 * 程序 - 一般作業的逐步指示，一般作業例如：新增、變更與刪除、常見問題及其解決方案、疑難排解建議。
 * 疑難排解 - 來自監視系統的一般警示清單，其中包括這些警示的逐步作業，以及服務疑難排解的一般指引。
 * 災難回復計劃及程序 - 關於因為主要位置發生災難，如何在另一個位置回復服務的詳細資料。
 * 服務水準合約 - 同意的服務參數，例如作業水準合約、關鍵點指標、可用性目標、回復點目標、回復時間目標。

大部分的 IT 組織都有多個 Runbook，可充當其參考手冊。這一系列的文件設計是要用來作為一般的 Runbook，以便您的組織使用 vCenter Server 實例。雖然每個 Runbook 的內容專門針對組織的需要，但 Runbook 的建立方法相當標準，會使用兩個階段：

1. 第一個階段是決定需要記錄哪些程序，並且在列出時，記錄每個程序的足夠詳細資料。
2. 第二個階段是持續性的，包含了維護、更新及更正這些程序、新增程序以及淘汰不再需要的程序。

{{site.data.keyword.vmwaresolutions_full}} 可讓您善用團隊內部部署的現有技能、工具集及 Runbook，以在 {{site.data.keyword.cloud_notm}} 中管理實例。

下列清單包含常用程序、手冊和作業：
* 配置作業 - 這些作業是系統管理者需要執行的常見活動，用於對環境進行自訂，以滿足企業需求和回應服務要求，例如新增新 VM 和增加容量。這些作業會分組成下列結構：
 * 一般指引
 * VM 程序
 * vCenter 程序
 * vSphere ESXi 主機程序
 * 儲存空間程序
 * 網路程序
* 警示 - vSphere 包含事件及警示子系統，它會追蹤 vSphere 環境中發生的事件，並使此資訊可用於 vCenter 中。本節說明這個子系統，以及如何啟用及使用企業中的警示。
* 主動每日檢查 - 這些檢查可讓系統管理者保持環境性能良好。每天執行檢查時，應該可以防止與容量和效能相關的許多常見問題影響工作負載。
* 疑難排解 - 即使執行主動每日檢查，也會發生影響工作負載的問題。因此，您需要盡快解決基礎問題。這些疑難排解手冊和一些常見的疑難排解情境，能協助系統管理者快速識別並修正這些問題。
* 法規遵循 - 法規遵循手冊提供關於針對法規遵循體制或產業最佳作法來維護環境法規遵循的一些見解。本手冊的重點在於 VMware 強化手冊，這是 VMware 環境最佳作法的一些記錄清單。

上述許多作業是在 Operations Management on {{site.data.keyword.cloud_notm}} 中自動化的，而對於未自動化的作業，這些工具會使系統管理者在進行手動程序時輕鬆許多。您務必要在受監視 VMware 環境具有核心元件，在 Operations Management on {{site.data.keyword.cloud_notm}} 中，達成這點的方法如下所示：

## Operations Management on IBM Cloud
{: #opsprocs-intro-ops-mgmt}

您可能已實施了企業工具，可利用這些工具來監視和管理 vCenter Server 實例。表 1 說明了 vCenter Server 環境的核心元件，為什麼需要監視這些元件，以及如何使用 Operations Management on {{site.data.keyword.cloud_notm}} 來監視這些元件。如需相關資訊，請參閱參考架構文件。

表 1. vCenter Server 環境核心元件

|元件|原因|監視者|
|---|---|---|
|vCenter|vCenter 是用來管理 vSphere 主機及管理虛擬化建構（例如叢集）的基礎架構管理元件。vSAN 是透過 vCenter 進行監視。vSphere 網路（例如分散式交換器及埠群組）是透過 vCenter 進行監視。| vRealize Operations Manager (vROps) 及 VMware SDDC Health Management Pack。vRealize Log Insights (vRLI) 會從 vCenter 收集日誌資料，而 Content Pack for vSphere 會在日誌中新增特定的瞭解，然後將警示傳送至 vROps。|
|vSphere 主機| vSphere 主機可為運算 VM 提供虛擬化的 CPU、RAM 及網路。| vROps，透過 vCenter。vRLI 會收集日誌資料|
|vSAN                |vSAN 透過合併主機中的儲存空間來提供資料儲存庫，以供 VM 使用。影響容量及效能的問題會對這些 VM 上執行的應用程式有影響。|vROps 及 vROps Management Pack for vSAN 能提供額外的儀表板，以輔助監視 vSAN。vCenter vSAN 性能檢查是透過 vROps 收集。vRLI 會從 vCenter 收集日誌資料。|
|NSX            | NSX 提供了運算 VM 使用的虛擬化網路元件，網路的任何故障都可能會影響在這些 VM 上執行的應用程式。|vROps 及 vROps Management Pack for VMware NSX 提供網路拓蹼的可見性。vRLI 從 NSX 元件（例如，控制器、ESG 和邏輯交換器）中收集日誌資料。vRealize Network Insight (vRNI) 提供網路問題的深度疑難排解。|

除了監視之外，Operations Management on {{site.data.keyword.cloud_notm}} 還提供配置、法規遵循及許多主動式作業的協助，如本文件中所詳述。


## 相關鏈結
{: #opsprocs-intro-links}

* [vSphere Monitoring](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [VMware Security Hardening Guide](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [變更 vCenter Server 構件的考量](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
