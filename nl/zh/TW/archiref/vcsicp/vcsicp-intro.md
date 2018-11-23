---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# vCenter Server 和 IBM Cloud Private 簡介

本文件提供朝向 IBM Cloud 發展的應用程式現代化旅程觀點，著重在雲端管理元件，讓整合式多重雲端能夠運用於應用程式現代化：

- **VMware vCenter Server on IBM Cloud** - VCS 是來自 IBM Cloud for VMware Solutions 的供應項目，也是自動佈建在 IBM Cloud 上的 VMware 型平台。
- **IBM Cloud Private** - ICP 是用來開發及管理容器化應用程式的應用程式平台，這些應用程式的設計是要部署至虛擬化基礎架構平台，例如 VMware。
- **IBM Kubernetes Services** - IKS 是 IBM Cloud 上的受管理服務，其運用 Kubernetes 作為編排引擎，可在整個單一承租戶叢集中自動部署、調整及運作應用程式容器。
- **IBM Multi-Cluster Manager** – MCM 提供使用者可見性、以應用程式為中心的管理（原則、部署、性能、作業），以及雲端與叢集之間的原則型規範。透過 MCM，您可以控制 Kubernetes 叢集。
- **IBM Cloud Automation Manager** – CAM 是在 ICP 上執行的多雲端自助式管理平台，它讓開發人員與管理者能夠滿足商業需求。

## IBM Cloud 上的應用程式現代化

應用程式現代化一詞說明轉移現有應用程式以在雲端上運用新方法的程序。當今的客戶不斷追求創新、有效率的方式，協助他們根據企業和應用程式複雜性來進行這項轉移。

商業壓力要求更快的上市時間。您現有的財產不僅包括應用程式，還包括資料、處理程序、商業邏輯和使用者介面，這些全都需要適應以跟上新的商業需求。

應用程式現代化的好處如下：
- 增進開發人員生產力。
- 提升作業效率。
- 減少建置新功能的成本。
- 在短時間內提供擴充的容量。

IBM 瞭解，有 70% 專用雲端的採用，是受到應用程式環境現代化的需求所驅使，不過，大部分的組織都是以階段性的方式在進行應用程式現代化，而這需要混合式的多重雲端環境，其中：
- 通常在大型主機或 UNIX 系統上執行的複雜和整合型舊式應用程式，仍保留在內部部署。
- 用於記錄系統 (SoR) 的 x86 環境，或是具有安全敏感性的應用程式或受到規範的工作負載，會放在虛擬化基礎架構或專用雲端上。
- 諸如 SAP 或高效能運算的應用程式會使用裸機資源。
- 具有安全敏感性和某些受到規範的工作負載，它們可以移至公用雲端，現在則正在移至專用環境。
- 參與系統 (SoE)（例如 Web、行動、IoT、AI 或視訊）正在移至公用雲端。

例如，常見的模式是將前端 SOE 應用程式部署為具有資料庫的容器，並將舊式中介軟體部署在專用雲端的 VM 上。

因為您的 IT 基礎架構與商業需求都是獨一無二的，所以您需要有現代化的方法，以協助加速商業價值交付、降低風險，並保留現有的投資。IBM 您可以自訂的方法，以便您可以因應與應用程式現代化相關的獨特商業和技術需求。

此文件是五份文件之一，這些文件對於朝向 IBM Cloud 發展的應用程式現代化旅程中所使用的技術，提供不同的觀點：

* _vCenter Server 及 IBM Cloud Private_ - 現行手冊，此為部署下列平台的參照架構：
  - **VMware vCenter Server on IBM Cloud** - 來自 IBM Cloud for VMware Solutions 的供應項目，它是自動佈建在 IBM Cloud 上的 VMware 型平台。
  - **IBM Cloud Private** – 用來開發及管理容器化應用程式的應用程式平台。這是整合的環境，其中包括容器編排程式 Kubernetes，以及專用映像檔儲存庫、管理主控台、監視架構和圖形使用者介面，您可以集中在此介面中部署、管理、監視及調整您的應用程式。
  - **IBM Cloud Automation Manager** – 這是準備供企業使用的現成 Infrastructure as Code (IaC) 平台，其提供單一窗格，可以直接使用儲存庫中所儲存及版本化的範本，同時佈建以 VM 為基礎的工作負載與以 Kubernetes 為基礎的工作負載。
* [vCenter Server 及 IBM Kubernetes Service](../vcsiks/vcsiks-intro.html) - 本手冊是部署下列平台的參照架構：
  - **VMware vCenter Server on IBM Cloud** - 來自 IBM Cloud for VMware Solutions 的供應項目，它是自動佈建在 IBM Cloud 上的 VMware 型平台。
  - **IBM Cloud Kubernetes Service** – IBM Cloud 上的受管理服務，其運用 Kubernetes 作為編排引擎，可在整個單一承租戶叢集中自動部署、調整及運作應用程式容器。
* [vCenter Server 網路](../vcsnsxt/vcsnsxt-intro.html) - 本手冊專注在 VCS、ICP 及 IKS 內使用的網路技術，例如 NSX-V、NSX-T 和 Calico。
* [VMware 和 Skate Advisor 概念車](../vcscar/vcscar-intro.html) - 此參考架構是一種「概念車」，亦即，用來強調及顯示解決真實世界問題之技術的機制。我們想要以真實方式示範 Watson AI 與機器學習之間的互動。首先，我們透過滑板運動的文化，以獨特方式來示範雲端服務。「概念車」的實作是一個稱為 Skate Advisor 的 Acme Skateboard 應用程式的延伸。Skate Advisor 是一個工具，它容許使用者與 Watson 驅動引擎進行滑板技巧對話。
* [VMware：Stock Trader 的現代化旅程](../vcscontent/vcscontent-modjourney.html) - 我們的參照使用案例說明典型 WebSphere Application Server 應用程式使用 IBM Cloud Private、IBM Middleware 內容、IBM Cloud Kubernetes Service 及 vCenter Server on IBM Cloud 進行現代化。我們全都在雲端旅程中，而且各自在該旅程的不同定點上。透過應用程式架構設計師 Jane 與雲端基礎架構設計師 Todd 的漸進式步驟，我們將一個稱為 Stock Trader 的現有應用程式進行現代化。它顯示的範例可協助您在旅程中採取每一個步驟，並實現您的企業價值（不論每一個步驟是大是小）。我們聚焦在以下四個主題：應用程式、DevOps、整合和管理。每一個工作共同協助您達到目標，事實上，只有一項進行現代化，其他項目未現代化，將會造成全面性問題。

### 相關鏈結

* [VCS Hybridity Bundle 概觀](../vcs/vcs-hybridity-intro.html)
