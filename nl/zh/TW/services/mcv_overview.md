---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

# Mission Critical VMware on IBM Cloud 概觀
{: #mcv_overview}

Mission Critical VMware on {{site.data.keyword.cloud}} 提供多區域雲端架構，可協助企業避免雲端應用程式的關閉，以及在雲端地區內自動失效接手。

與使用內部部署環境或競爭雲端平台的大部分 VMWare 用戶端相較，此雲端架構可讓客戶達到更高的可用性和失效接手成功率。

此架構支援現有的關鍵任務舊式工作負載，包括非雲端原生應用程式，目標聚集可用性為 99.99%。IBM Cloud 多區域地區的設計目的，是要在發生站台運行中斷時，讓關鍵任務工作負載保持在線上。故障站台中的工作負載會在近乎即時的情況下自動重新啟動，而鄰接站台中的工作負載則保持在線上且可供使用。

此架構涵蓋各種企業服務，包括網路、儲存空間、備援，以及為了監視和疑難排解雲端型應用程式而建置的其他工具。此外，此架構可以與 IBM Services Platform with Watson（以 {{site.data.keyword.cloud_notm}} 為建置基礎）整合，以容許更廣泛地使用服務。藉由使用平台的認知功能，用戶端可以對新的商業洞察進行更有效的資料採礦，以協助維護持續運作。

## Mission Critical VMware on IBM Cloud 的技術規格
{: #mcv_overview-specs}

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 架構是端對端參照架構，可為客戶的工作負載提供自動化失效接手。它會使用 {{site.data.keyword.cloud_notm}} 多區域地區來搭配 IBM 管理的服務，其中涵蓋下列元件：

* 運算架構 (VMware vSphere)
* 網路架構（目前是 NSX-V）
* 儲存空間架構 (VMware vSAN)
* 與 IBM Services Platform with Watson 整合，以供使用服務
* 用於監視、疑難排解、效能和容量管理的工具：
  * vRealize Suite 型樣（Operations、Log Insight 和 Network Insight）
  * Active Directory 型樣
  * 與 Netcool/Bluecare 整合，可用於自動開票、警示和事件強化
  * 備援型樣（備份及回復）

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 適用於下列地區：
* 美洲：NA 南部 - 達拉斯的所有 IBM Cloud Data Center，以及 NA 東部 - 華盛頓特區的所有 IBM Cloud Data Center
* 歐洲：法蘭克福和倫敦的所有 IBM Cloud Data Center
* 亞太地區：雪梨和東京的所有 IBM Cloud Data Center

### 基礎架構的架構規格
{: #mcv_overview-base-specs}

基礎架構具有下列規格：
* 每個站台都有自己的專用邊緣和管理叢集
* 資源叢集是 vSphere + vSAN 延伸叢集
* 見證站台包含見證 ESXi 主機
* 單一 vCenter 和 NSX Manager 架構
* vCenter Server Appliance 內嵌 Platform Services Controller (PSC)，可透過 L3 網路架構使用「vCenter 高可用性 (HA)」
* NSX Manager 回復是使用向上同步備份檔的「快速待命」方法

### 工具與技術架構規格
{: #mcv_overview-tooling-specs}

工具與技術架構具有下列規格：
* vRealize Operations、vRealize Log Insight 和 vRealize Network Insight，可提供所使用之 VMware 產品的特定作業和管理功能，例如 NSX、vSAN 和 vSphere
* IBM Software Defined Environment Automation Tool Health Check (SAT HC)，可依據最佳作法和安全原則來驗證部署
* 選用性災難回復 (DR) 至 {{site.data.keyword.cloud_notm}} 地區外部的站台
* Fortigate Security Appliance 或類似的安全應用裝置，以保護任何網際網路存取，並促進「主動-主動」網路與內部部署網路的整合

### vSphere + vSAN 延伸叢集架構規格
{: #mcv_overview-stretched-cluster-specs}

vSphere + vSAN 延伸叢集架構具有下列規格：
* 此叢集提供跨越兩個站台的儲存和運算功能，以加強可用性。
* 從虛擬機器 (VM) 發出的寫入要求會同步寫入至兩個站台，而導致站台對站台的網路延遲。
* 從 VM 發出的讀取要求會在 VM 所在的實體位置本端完成，因此避免了額外的延遲。
* 見證站台和見證主機用來作為分割的 Brain/Quorum。
* 「vSAN 原生加密」（用於靜態加密）可與此架構組合使用。

### 網路架構規格
{: #mcv_overview-network-specs}

網路架構具有下列規格：
* Edge/DLR/VXLAN 與 BGP 度量型遞送組合，有助於採用自動化失效接手的「主動-主動」站台設計。
* 每個站台都有自己的一組 Edge/DLR 和 VXLAN 概念。
* 在正常情況下，所有 VM 都會連接至 DLR-A，例如 VM-A 會在 {{site.data.keyword.cloud_notm}} 可用性區域 #1 中，而資料流量會在本端進出。
* 在 VM-A 的 vMotion 活動期間，資料傳輸仍會透過 {{site.data.keyword.cloud_notm}} 可用性區域 #1 進出。
* 在站台或邊緣故障期間，資料流量會遞送至剩下可用的站台之外。

## 相關鏈結
{: #mcv_overview-related}

* [要求 Mission Critical VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_mcv)
