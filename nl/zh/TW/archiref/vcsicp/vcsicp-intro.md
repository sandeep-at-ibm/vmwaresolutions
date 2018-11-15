---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

# vCenter Server 和 IBM Cloud Private 簡介

本文件提供朝向 IBM Cloud 發展的應用程式現代化旅程觀點，著重在雲端管理元件，讓整合式多重雲端能夠運用於應用程式現代化：

- **VMware vCenter Server on IBM Cloud** - VCS 是來自 IBM Cloud for VMware Solutions 的供應項目，其為自動佈建在 IBM Cloud 上的 VMware 型平台。

- **IBM Cloud Private** - ICP 是用來開發及管理容器化應用程式的應用程式平台，這些應用程式的設計是要部署至虛擬化基礎架構平台，例如 VMware。

- **IBM Kubernetes Services** - IKS 是 IBM Cloud 上的受管理服務，其運用 Kubernetes 作為編排引擎，可在整個單一承租戶叢集中自動部署、調整及運作應用程式容器。

- **IBM Multi-Cluster Manager** – MCM 提供使用者可見性、以應用程式為中心的管理（原則、部署、性能、作業），以及雲端與叢集之間的原則型相符性。透過 MCM，您可以控制 Kubernetes 叢集。

- **IBM Cloud Automation Manager** – CAM 是在 ICP 上執行的多雲端自助式管理平台，讓開發人員與管理者能夠符合商業需求。

## IBM Cloud 上的應用程式現代化
應用程式現代化一詞說明轉移現有應用程式以在雲端上運用新方法的程序。當今的客戶不斷追求創新、有效率的方式，協助他們根據企業和應用程式複雜性來進行這項移轉。

商業壓力要求更快的上市時間。您現有的產品不僅包括應用程式，還包括資料、處理程序、商業邏輯和使用者介面，這些全都需要適應新的商業需求。

應用程式現代化的好處如下：
- 增進開發人員生產力。
- 提升作業效率。
- 減少建置新功能的成本。
- 在短時間內遞送擴充的容量。

IBM 瞭解 70% 專用雲端的採用，是受到應用程式環境現代化的需求所驅使，不過，大部分的組織都是以編譯打包的方式在進行應用程式現代化，而這需要混合式的多重雲端環境，其中：
- 通常在大型主機或 UNIX 系統上執行的複雜和整合型舊式應用程式，仍保留在內部部署。
- 用於記錄系統 (SoR) 的 x86 環境，或是具有安全敏感性或規則性工作負載的應用程式，會放在虛擬化基礎架構或專用雲端上。
- 諸如 SAP 或高效能運算等應用程式會耗用裸機資源。
- 具有安全敏感性和某些規則性的工作負載（可以移至公用雲端）會移至專用環境。
- 參與系統 (SoE)（例如 web、行動、IoT、AI 或視訊）會移至公用雲端。

例如，常見的型樣是將前端 SOE 應用程式部署為具有資料庫的容器，並將舊式中介軟體部署在專用雲端的 VM 上。

因為您的 IT 基礎架構與商業需求都是獨一無二的，所以您需要有現代化的方法，以協助加速商業價值交付、降低風險，並保留現有的投資。IBM 正是提供這樣的方法，您可以自訂此方法來因應與應用程式現代化相關的特殊商業和技術需求。

此文件是以下五份文件之一，這些文件對於朝向 IBM Cloud 發展的應用程式現代化旅程中所使用的技術，提供不同的觀點：

參照架構手冊，VCS – ICP 和 CAM - 即為本節。

用來部署下列平台的參照架構：
  - **VMware vCenter Server on IBM Cloud** - 來自 IBM Cloud for VMware Solutions 的供應項目，其為自動佈建在 IBM Cloud 上的 VMware 型平台。
  - **IBM Cloud Private** – 用來開發及管理容器化應用程式的應用程式平台。這是整合的環境，其中包括容器編排程式 Kubernetes，以及專用映像檔儲存庫、管理主控台、監視架構和圖形使用者介面，您可以集中在此介面中部署、管理、監視及調整您的應用程式。
  - **IBM Cloud Automation Manager** – 這是準備供企業使用的現成 Infrastructure as Code (IaC) 平台，其提供單一窗格，可以直接使用儲存庫中所儲存及版本化的範本，同時佈建 VM 型工作負載與 Kubernetes 型工作負載。

[參照架構手冊，VCS - IKS](../vcsiks/vcsiks-intro.html)

  用來部署下列平台的參照架構：
  - **VMware vCenter Server on IBM Cloud** - 來自 IBM Cloud for VMware Solutions 的供應項目，其為自動佈建在 IBM Cloud 上的 VMware 型平台。
  - **IBM Cloud Kubernetes Service** – IBM Cloud 上的受管理服務，其運用 Kubernetes 作為編排引擎，可在整個單一承租戶叢集中自動部署、調整及運作應用程式容器。

[參照架構手冊，VCS – 網路](../vcsnsxt/vcsnsxt-intro.html)

此文件著重在 VCS、ICP 和 IKS 中所使用的網路技術，例如 NSX-V、NSX-T 和 Calico。

[參照架構手冊，Watson 和 Sk8boarding 概念汽車](../vcscar/vcscar-intro.html)

此文件使用「概念汽車」方法來示範 Watson AI 與機器學習之間的互動。

此文件特別強調下列技術：
  - **Pepper** - 該介面能夠整合雲端環境，以執行應用程式和搜尋作業。 
  - **VMware vCenter Server on IBM Cloud** - 用來管理應用程式的元素，例如資料庫工作負載。
  - **IBM Cloud Kubernetes Service** - 用來管理應用程式的容器化元素。
  - **IBM Cloud Private** - 用來提供平台和服務層級的編排，能夠跨 VM 與容器平台來管理及擴充應用程式。此元件也容許對平台啟用 Watson 開發人員服務，以容許存取 AI 功能。

[參照架構手冊，VCS – 內容](../vcscontent/vcscontent-intro.html)

此文件著重在 IBM Cloud Automation Manager 中提供的下列內容類型：
- 內部型錄內容，例如「預先定義」的 Helm 圖表、Terraform 範本和 Chef 秘訣。
- 服務內容，例如 Blockchain 和 Watson 服務。

### 相關鏈結

  * [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
