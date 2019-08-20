---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# vCenter Server 及 IBM Cloud Kubernetes Service 簡介
{: #vcsiks-intro}

本文件提供 {{site.data.keyword.cloud}} 的應用程式現代化旅程觀點，聚焦在下列平台的網路層面，讓整合式多重雲端能夠用於應用程式現代化：

本文件提供 {{site.data.keyword.cloud_notm}} 的應用程式現代化旅程觀點，聚焦在雲端管理元件，讓整合式多重雲端能夠用於應用程式現代化：

- **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - vCenter Server 是來自 {{site.data.keyword.vmwaresolutions_full}} 的供應項目，而且是自動佈建在 {{site.data.keyword.cloud_notm}} 上的 VMware 型平台。
- **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} 是用來開發及管理容器化應用程式的應用程式平台，而這些應用程式部署至虛擬化基礎架構平台，例如 VMware。
- **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} 是 {{site.data.keyword.cloud_notm}} 上的受管理服務，其使用 Kubernetes 作為編排引擎，可在整個單一承租戶叢集中自動部署、調整及運作應用程式容器。
- **IBM Multi-Cluster Manager** - MCM 提供使用者可見性、以應用程式為中心的管理（原則、部署、性能、作業），以及雲端與叢集之間的原則型規範。透過 MCM，您可以控制 Kubernetes 叢集。
- **{{site.data.keyword.cloud_notm}} Automation Manager** - CAM 是在 {{site.data.keyword.icpfull_notm}} 上執行的多重雲端自助式管理平台，讓開發人員與管理者能夠滿足商業需求。

## IBM Cloud 上的應用程式現代化
{: #vcsiks-intro-app-mod}

應用程式現代化一詞說明轉移現有應用程式以在雲端上使用新方法的處理程序。當今的客戶不斷追求創新、有效率的方式，協助他們根據企業和應用程式複雜性來進行這項轉移。

商業壓力要求更快的上市時間。您現有的財產不僅包括應用程式，還包括資料、處理程序、商業邏輯和使用者介面，這些全都需要適應以跟上新的商業需求。

應用程式現代化的好處如下：
- 增進開發人員生產力。
- 提升作業效率。
- 減少建置新功能的成本。
- 在短時間內提供擴充的容量。

IBM 瞭解，有 70% 專用雲端的採用是受到應用程式環境現代化的需求所驅使，不過，大部分的組織都是以階段性的方式在進行應用程式現代化，而這需要混合式的多重雲端環境，其中：
- 通常在大型主機或 UNIX 系統上執行的複雜和整合型舊式應用程式，仍保留在內部部署。
- 用於「記錄系統 (SoR)」的 x86 環境、具有安全敏感性的應用程式以及受到規範的工作負載，都會放在虛擬化基礎架構或專用雲端上。
- 諸如 SAP 或高效能運算的應用程式會使用裸機資源。
- 具有安全敏感性和某些受到規範的工作負載，它們可以移至公用雲端，現在則正在移至專用環境。
- 參與系統 (SoE)（例如 Web、行動、IoT、AI 或視訊）正在移至公用雲端。

例如，常見的模式是將前端 SoE 應用程式部署為具有資料庫的容器，並將舊式中介軟體部署在專用雲端的 VM 上。

因為您的 IT 基礎架構與商業需求都是獨一無二的，所以您需要有現代化的方法，以協助加速商業價值交付、降低風險，並保全現有的投資。IBM 您可以自訂的方法，以便您可以因應與應用程式現代化相關的獨特商業和技術需求。

此文件是五份文件之一，這些文件對於朝向 {{site.data.keyword.cloud_notm}} 發展的應用程式現代化旅程中所使用的技術，提供不同的觀點：

* [vCenter Server 及 {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro) - 用來部署下列平台的參照架構：
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - 來自 {{site.data.keyword.vmwaresolutions_full}} 的供應項目，而且是自動佈建在 {{site.data.keyword.cloud_notm}} 上的 VMware 型平台。
  - **{{site.data.keyword.cloud_notm}} Private** - 用來開發及管理容器化應用程式的應用程式平台。{{site.data.keyword.icpfull_notm}} 是整合環境，其中包括容器編排程式 Kubernetes 以及專用映像檔儲存庫、管理主控台、監視架構和圖形使用者介面，您可以集中在此介面中部署、管理、監視及調整應用程式。
  - **{{site.data.keyword.cloud_notm}} Automation Manager** - 準備供企業使用的現成「基礎架構即程式碼 (IaC)」平台，其提供單一窗格，可以使用儲存庫中所儲存及版本化的範本，同時佈建 VM 型工作負載與 Kubernetes 型工作負載。
* [vCenter Server 及 {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - 用來部署下列平台的參照架構：
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - 來自 {{site.data.keyword.vmwaresolutions_full}} 的供應項目，而且是自動佈建在 {{site.data.keyword.cloud_notm}} 上的 VMware 型平台。
  - **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.cloud_notm}} 上的受管理服務，其使用 Kubernetes 作為編排引擎，可在整個單一承租戶叢集中自動部署、調整及運作應用程式容器。
* [vCenter Server 網路](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) - 聚焦在 vCenter Server、{{site.data.keyword.icpfull_notm}} 及 {{site.data.keyword.containerlong_notm}} 內使用的網路技術，例如 NSX-V、NSX-T 和 Calico。
* [VMware 及 Skate Advisor 概念車](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro) - 此參照架構是一種「概念車」，亦即，用來強調及顯示解決真實世界問題之技術的機制。我們想要以真實方式示範 Watson AI 與機器學習之間的互動。我們透過滑板運動的文化，以獨特方式來示範雲端服務。「概念車」的實作是一個稱為 Skate Advisor 的 Acme Skateboard 應用程式的延伸。Skate Advisor 是一個工具，它容許使用者與 Watson 驅動引擎進行滑板技巧對話。
* [VMware：Stock Trader 的現代化旅程](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - 我們的參照使用案例說明典型 WebSphere Application Server 應用程式使用 {{site.data.keyword.cloud_notm}} Private、IBM Middleware 內容、{{site.data.keyword.containerlong_notm}} 及 vCenter Server on {{site.data.keyword.cloud_notm}} 進行現代化。我們全都在雲端旅程中，而且各自在該旅程的不同定點上。透過應用程式架構設計師 Jane 與雲端基礎架構設計師 Todd 的漸進式步驟，我們將一個稱為 Stock Trader 的現有應用程式進行現代化。它顯示的範例可協助您在旅程中採取每一個步驟，並實現您的企業價值（不論每一個步驟是大是小）。我們聚焦在以下四個主題：應用程式、DevOps、整合和管理。所有佈景主題都會共同運作，協助您達到目標。現代化一個佈景主題，而未現代化其他佈景主題，可能會導致問題。
