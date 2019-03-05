---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-27"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 單一節點試用版 vCenter Server on IBM Cloud 的 HCX on IBM Cloud 架構設計

具有單一節點試用版 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的 VMware HCX on {{site.data.keyword.cloud}} 是新的供應項目，可啟用 {{site.data.keyword.vmwaresolutions_short}} 實例與內部部署 VMware 虛擬化資料中心之間的無縫連線。雖然建議 vCenter Server 最少具有三個節點，但是單一節點試用版可讓您以低廉的價格來測試並體驗混合式雲端實作的好處。

{{site.data.keyword.vmwaresolutions_short}} 包括 {{site.data.keyword.cloud_notm}} 中 vCenter Server 配置的完整自動化快速部署。單一節點試用版 vCenter Server 供應項目補足內部部署基礎架構，並容許在 {{site.data.keyword.cloud_notm}} 中執行現有及未來工作負載，而不需要進行轉換。此供應項目使用內部部署所使用的相同工具、技能及處理程序。如需 {{site.data.keyword.vmwaresolutions_short}} 供應項目的相關資訊，請參閱 [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture)。

HCX on {{site.data.keyword.cloud_notm}} 服務會混合 vCenter Server 實例與現有內部部署虛擬化資料中心，方法是啟用建立無縫網路延伸及雙向移轉工作負載。HCX on IBM Cloud 元件（其部署為 {{site.data.keyword.cloud_notm}} VMware 目標站台中的虛擬機器 (VM)）能夠建立與安裝至對等節點內部部署來源站台之 HCX on {{site.data.keyword.cloud_notm}} 元件的連線。

圖 1. HCX 架構

![HCX 架構](hcx-architecture.svg "HCX 架構")

下列資訊提供 HCX on {{site.data.keyword.cloud_notm}} 服務實作的設計。它包括目標端 {{site.data.keyword.vmwaresolutions_short}} 實例上的元件以及來源內部部署上所部署的元件。

## HCX on IBM Cloud 概觀

{{site.data.keyword.cloud_notm}} 將內部部署 vSphere vCenter 網路無縫整合至 {{site.data.keyword.vmwaresolutions_short}} 部署。混合式網路將內部部署 vSphere vCenter 網路擴充至 {{site.data.keyword.cloud_notm}}，並支援雙向 VM 行動性。

HCX 擁有來源及目的地加密和解密處理程序，以確定一致安全並提供 VM 移轉及網路延伸這類混合式工作流程的許可。此供應項目建立最佳化的軟體定義廣域網路 (WAN) 來增加延伸網路效能，以使效能達到區域網路 (LAN) 速度。HCX 支援雙向工作負載和 VMware NSX 安全原則移轉至 {{site.data.keyword.cloud_notm}}、與 vSphere vCenter 整合，並從 vSphere Web Client 進行管理。

### 第 2 層網路延伸

HCX 容許現有內部部署 vSphere 財產將網路從其內部部署 vCenter 安全地延伸至執行 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 或 vCenter Server 的 {{site.data.keyword.CloudDataCent_notm}}。下列項目會啟用此特性：

* HCX 提供稱為「第 2 層集中器 (L2C)」的應用裝置。
* 延伸網路鏈結至 vCenter Server 上所部署的 {{site.data.keyword.cloud_notm}} NSX Edge 應用裝置。
* 可以部署多個標準第 2 層集中器，以達到可調整性並增加內部部署 vCenter 的傳輸量。
* 透過「雲端閘道」及透過延伸第 2 層移轉的 VM 可以保留其 IP 及 MAC 位址。

### 虛擬機器移轉

HCX 提供下列三種 VM 移動方法：

* 低關閉時間移轉
* vSphere vMotion 移轉
* 冷移轉

#### 低關閉時間移轉

低關閉時間移轉根據「vSphere 抄寫」，這是 VMware ESX 或 VMware ESXi Hypervisor 中所實作的分散式技術。內部部署 HCX 部署會在 {{site.data.keyword.cloud_notm}} 中建立即時 VM 的抄本、執行切換以關閉來源 VM 的電源，以及開啟所移轉 VM 的電源。移轉路徑一律是透過「雲端閘道」。傳輸可以是網際網路、第 2 層延伸網路或 Direct Connect 線路。您可以在任一方向多次移轉 VM。

#### vSphere vMotion 移轉

透過延伸至 {{site.data.keyword.cloud_notm}} 的網路使用 vSphere vMotion 移轉，即可傳送即時 VM。vMotion 移轉也稱為零關閉時間移轉或跨雲端 vMotion。

#### 冷移轉

冷移轉可以透過「第 2 層集中器」所建立的延伸網路，將關閉電源的 VM 傳送至 {{site.data.keyword.cloud_notm}}。

#### 一般移轉特性

下列是這三種移轉類型可用的特性：

* 可增加移轉傳輸量及速度的軟體定義 WAN 最佳化。
* 排定指定時間的移轉。
* 保留主機名稱、VM 名稱或兩者。

### 網路

下列網路特性會建置到「雲端閘道」及「第 2 層集中器」。

#### 智慧型流程遞送

智慧型流程遞送根據網際網路路徑自動選取最佳連線，有效率地溢出整個連線，以盡快移動工作負載。備份或抄寫這類較大的流程導致 CPU 競用時，會將較小的流程遞送至較不忙碌的 CPU，以改善互動式傳輸的效能。

#### 鄰近遞送

鄰近遞送確定在內部部署及雲端連接至延伸和遞送網路之 VM 間的轉遞是對稱的。此特性需要在客戶內部部署與雲端之間配置具有「動態遞送」的「進階網路服務」。

使用者將其網路擴充至雲端時，會將第 2 層連線功能延伸至 {{site.data.keyword.cloud_notm}} 網路。不過，如果沒有路徑最佳化，則第 3 層通訊要求必須回到要遞送的內部部署網路原點。此回程稱為「轉接」或「回流」。轉接並不足夠，因為封包必須在網路原點與雲端之間來回流動，即使來源及目的地 VM 位於雲端時也是一樣。

如果轉遞路徑包括有狀態防火牆，或必須看到連線兩端的其他行內設備，則通訊可能會失敗。結束雲端的輸出路徑可以是延伸第 2 層網路或「組織遞送網路」時，會發生沒有路徑最佳化的 VM 通訊失敗。內部部署網路不知道延伸網路「捷徑」。此問題稱為非對稱遞送。此解決方案是啟用鄰近遞送，讓內部部署網路可以瞭解從 {{site.data.keyword.cloud_notm}} 開始的路徑。

「雲端閘道」會維護雲端中的 VM 庫存。它也瞭解下列 VM 狀態：

* 使用 vMotion 傳送至 {{site.data.keyword.cloud_notm}}（零關閉時間移轉）
* 使用主機型抄寫移轉至雲端（低關閉時間移轉）
* 建立於雲端中（在延伸網路上）

#### 安全

「雲端閘道」提供符合「套組 B」標準的 AES-GCM，其具有 IKEv2、AES-NI 卸載及流程型許可控制。HCX 也擁有來源及目的地加密和解密處理程序，以確定 VM 移轉及網路延伸這類混合式工作流程的一致安全及管理。您可以移轉安全原則，這些安全原則會定義並指派給具有 {{site.data.keyword.cloud_notm}} 之 VM 的 VM 內部部署。

下列是原則移轉所需的條件：

* 內部部署資料中心執行 NSX 6.2.2 版或更新版本。
* 在 vSphere 中，安全原則是可具有許多規則的單一「NSX 區段」。
* 您可以命名 IP 位址組或 MAC 位址組來參與該原則。
* 「MAC 組」或「IP 組」的名稱不能超過 218 個字元。
* 支援的規則將第 3 層 IP 位址或「IP 組」或是第 2 層 MAC 位址或「MAC 組」指定為來源或目的地。

### HCX 的元件

HCX on {{site.data.keyword.cloud_notm}} 服務會部署在內部部署資料中心和 IBM Cloud 目標上安裝及配置的四個虛擬應用裝置。下列資訊說明這四個必要虛擬應用裝置。或者，根據實作設計，可能需要邊緣裝置。

#### HCX Manager

HCX Manager 虛擬應用裝置是內部部署 vCenter 的延伸。該應用裝置會部署為 VM，而其檔案結構包含其他混合式服務虛擬應用裝置。HCX Manager 會監督內部部署及 {{site.data.keyword.cloud_notm}} 內的「雲端閘道」、「第 2 層集中器」及「WAN 最佳化」虛擬應用裝置的部署和配置。

#### 混合式雲端閘道

「混合式雲端閘道 (CGW)」會維護內部部署 vSphere 財產與 {{site.data.keyword.cloud_notm}} 之間的安全頻道。HCX 使用高度加密來引導與 {{site.data.keyword.cloud_notm}} 的站台對站台連線。vSphere 與 {{site.data.keyword.cloud_notm}} 之間的安全頻道防止網路「中程傳輸」安全問題。「雲端閘道」也會納入 vSphere 抄寫技術，以執行雙向移轉。

#### WAN 最佳化

「WAN 最佳化」應用裝置是執行 WAN 調節來減少延遲效果的元件。它也納入「轉遞錯誤更正」以使封包流失情境無效，以及刪除重複的備用資料流量型樣。總而言之，這些會減少頻寬使用，並確定最佳使用可用的網路容量來加速與 {{site.data.keyword.cloud_notm}} 之間的資料傳送。

VM 移轉根據「雲端閘道」與「WAN 最佳化」應用裝置的組合，以達到 vSphere 內部部署與 {{site.data.keyword.cloud_notm}} 之間的不平行行動性。此外，透過「雲端閘道」遞送資料路徑時，第 2 層延伸會獲益於 WAN 最佳化。{:important}

#### 第 2 層集中器

「第 2 層集中器 (L2C)」應用裝置容許將第 2 層網路從內部部署 vSphere 資料中心擴充至 {{site.data.keyword.cloud_notm}}。

「第 2 層集中器」有下列介面：

* **內部幹線介面**：此介面使用翻譯橋接器與 {{site.data.keyword.cloud_notm}} 中對應延伸網路的對映，處理延伸網路的 VM 資料流量內部部署。
* **上行鏈路介面**：HCX 使用此介面來傳送與 {{site.data.keyword.cloud_notm}} 之間的封裝套版資料流量。應用程式資料會流過「上行鏈路」介面。

### 部署架構

如需 HCX on {{site.data.keyword.cloud_notm}} 部署的相關資訊，請參閱 [VMware HCX on {{site.data.keyword.cloud_notm}} 部署及作業](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf)。
