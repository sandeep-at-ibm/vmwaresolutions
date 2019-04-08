---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# VMware 和 Skate Advisor 概念車手冊
{: #vcscar-intro}

下列參照架構是一種「概念車」，亦即，用來強調及顯示解決真實世界問題之技術的機制。「概念車」現在根本不代表立即可用的服務。

本參照架構也提供下列資訊：

-   為各種利害關係人提供一般語言。
-   提供技術實作的一致性，以解決問題。
-   支援針對經證明的參照架構來驗證解決方案。
-   鼓勵遵守一般標準、規格和型樣。

## 關於 ACME Skate Advisor
{: #vcscar-intro-about}

我們想要以真實方式示範 Watson 人工智慧與機器學習之間的互動，並透過它更深入地探索滑板運動文化。我們以獨特的方式示範可用的服務及雲端基礎架構，並示範此領域中的技術功能及進展。「概念車」的實作是稱為 Skate Advisor 之示範性 Acme Skateboard 應用程式的延伸。Skate Advisor 是一個工具，它容許使用者與 Watson 驅動引擎進行滑板技巧對話。下列報價是交談範例：

-   「Watson，顯示 Casper 技巧的組合」
-   「Watson，顯示可執行技巧的一般位置」
-   「Watson，顯示 Casper 技巧的視訊」

Acme Skate Advisor 利用 Watson Discovery Service 來汲取文章、視訊、部落格及其他網際網路型內容，以建立學習到且可由應用程式查詢的技巧資料庫。

Skate Advisor 應用程式也會實作於應用程式現代化平台，以透過 {{site.data.keyword.cloud_notm}} for VMware Services 平台上所管理的 {{site.data.keyword.icpfull_notm}} 來提供容器型服務。

ACME Skate Advisor 應用程式利用 Watson 平台及應用程式現代化平台。

## 使用案例
{: #vcscar-intro-use-cases}

### 應用程式現代化示範
{: #vcscar-intro-app-mod-demo}

示範已部署至應用程式現代化平台的應用程式。此平台包括在針對 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 供應項目之 {{site.data.keyword.cloud_notm}} 上部署的 {{site.data.keyword.icpfull_notm}}、CAM 及 NSX 元件。

### 使用 Watson Assistant 的 Watson 語音辨識
{: #vcscar-intro-speech}

Acme Skate Advisor 透過 Watson 平台所提供的語音轉文字及文字轉語音服務以與使用者進行通訊。

### Watson Discovery Service 用法及訓練
{: #vcscar-intro-watson-disc}

Acme Skate Advisor 使用 Watson Discovery Service 來追蹤已套用分類語言的「技巧」資料庫，以及從線上服務探索到的技巧。

### Watson 服務用法
{: #vcscar-intro-watson-services}

下列「Watson 服務」用來建立 Acme Skate Advisor：
-   Watson Text to Speech。
-   Watson Speech to Text。
-   Watson Advisor。
-   Watson Discovery Service。
-   Watson Knowledge Studio。

## IBM Cloud 上的應用程式現代化
{: #vcscar-intro-app-mod}

應用程式現代化一詞說明轉移現有應用程式以在雲端上使用新開發及交付方法的處理程序。當今的客戶不斷追求創新、有效率的方式，協助他們根據企業和應用程式複雜性來進行這項轉移。

商業壓力要求更快的上市時間。您現有的財產不僅包括應用程式，還包括資料、處理程序、商業邏輯和使用者介面，這些全都需要適應以跟上新的商業需求。

下列清單說明應用程式現代化的好處：
- 改善開發人員生產力
- 增加作業效率
- 減少建置新特性的成本
- 擴充在短時間內交付的容量

IBM 瞭解，有 70% 專用雲端的採用是受到應用程式環境現代化的需求所驅使。不過，大部分的組織都是以階段性的方式在進行應用程式現代化，而這需要混合式的多重雲端環境，其中：

- 通常在大型主機或 UNIX 系統上執行的複雜和整合型繼承應用程式仍然保留在內部部署。
- 用於「記錄系統 (SoR)」的 x86 環境、具有安全敏感性的應用程式以及受到規範的工作負載，都會放在虛擬化基礎架構或專用雲端上。
- SAP 或高效能運算這類應用程式會使用裸機資源。
- 具有安全敏感性和某些受到規範的工作負載，它們可以移至公用雲端，現在則正在移至專用環境。
- 「參與系統 (SoE)」（例如 Web、行動、IoT、AI 或視訊）正在移至公用雲端。

例如，常見的模式是將前端 SoE 應用程式部署為具有資料庫的容器，並將繼承中介軟體部署在專用雲端的 VM 上。

因為 IT 基礎架構和商業需求是獨一無二的，所以現代化的方法必須提供下列優先順序：

* 加速企業價值
* 將交付時間減到最小
* 減少風險
* 保留現有投資。

IBM 提供您可以自訂的應用程式現代化方法，以因應獨特商業及技術需求。

下列文件對於朝向 {{site.data.keyword.cloud_notm}} 發展的應用程式現代化旅程中所使用的技術，提供不同的觀點：

* [vCenter Server 及 {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro) - 用來部署下列平台的參照架構。
   - **VMware vCenter Server on IBM Cloud** - vCenter Server 是來自 {{site.data.keyword.vmwaresolutions_short}} 的供應項目，其為自動佈建在 {{site.data.keyword.cloud_notm}} 上的 VMware 型平台。
   - **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} 是一個應用程式平台，用於開發及管理容器化應用程式。{{site.data.keyword.icpfull_notm}} 是整合環境，其中包括容器編排程式 Kubernetes、專用映像檔儲存庫、管理主控台、監視架構，以及圖形使用者介面。此使用者介面提供一個集中位置，而您可以從中部署、管理、監視及調整您的應用程式。
   - **IBM Cloud Automation Manager** - CAM 是準備供企業使用的現成「基礎架構即程式碼」平台，其提供單一窗格，可以使用儲存庫中所儲存及版本化的範本，同時佈建 VM 型工作負載與 Kubernetes 型工作負載。
* [vCenter Server 及 {{site.data.keyword.containerlong_notm}} 服務](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - 用來部署下列平台的參照架構。
   - **VMware vCenter Server on IBM Cloud** - vCenter Server 是來自 {{site.data.keyword.vmwaresolutions_short}} 的供應項目，其為自動佈建在 {{site.data.keyword.cloud_notm}} 上的 VMware 型平台。
   - **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} 是 {{site.data.keyword.cloud_notm}} 上的受管理服務，其使用 Kubernetes 作為編排引擎，可在整個單一承租戶叢集中自動部署、調整及運作應用程式容器。
* [vCenter Server 網路](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) - 聚焦在用於 vCenter Server、{{site.data.keyword.icpfull_notm}} 與 {{site.data.keyword.containerlong_notm}} 之間整合的網路技術（例如 NSX-V 及 Calico），以及使用 NSX-T 的技術預覽。
* _VMware 及 Skate Advisor 概念車手冊_ - 為「概念車」的參照架構，亦即，用來強調及顯示解決真實世界問題之技術的機制。我們想要以真實方式示範 Watson AI 與機器學習之間的互動。我們透過滑板運動的文化，以獨特方式來示範雲端服務。「概念車」的實作是一個稱為 Skate Advisor 的 Acme Skateboard 應用程式的延伸。Skate Advisor 是一個工具，它容許使用者與 Watson 驅動引擎進行滑板技巧對話。
* [VMware：Stock Trader 的現代化旅程](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - 此參照使用案例說明如何使用 {{site.data.keyword.cloud_notm}} Private、IBM Middleware 內容、{{site.data.keyword.containerlong_notm}} 及 vCenter Server on {{site.data.keyword.cloud_notm}}，將典型 WebSphere Application Server 應用程式現代化。我們全都在雲端旅程中，而且各自在該旅程的不同定點上。透過應用程式架構設計師 Jane 與雲端基礎架構設計師 Todd 的漸進式步驟，我們將一個稱為 Stock Trader 的現有應用程式進行現代化。請檢閱範例，以協助您在旅程中採取每個步驟，並實現您的企業價值，不論每個步驟是大還是小。我們聚焦在以下四個主題：應用程式、DevOps、整合和管理。所有佈景主題都會共同運作，協助您達到目標。現代化一個佈景主題，而未現代化其他佈景主題，可能會導致問題。

## 相關鏈結
{: #vcscar-intro-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
