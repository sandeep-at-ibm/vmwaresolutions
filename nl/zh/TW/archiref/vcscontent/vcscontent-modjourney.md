---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# 現代化旅程
{: #vcscontent-modjourney}

此參照使用案例說明如何使用 {{site.data.keyword.cloud}} Private、IBM Middleware 內容、{{site.data.keyword.containerlong_notm}} 及 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 將典型 WebSphere Application Server 應用程式現代化。

## 現代化不只是應用程式
{: #vcscontent-modjourney-modernization}

我們全都在雲端旅程中，而且各自在該旅程的不同定點上。此使用案例聚焦在如何透過應用程式架構設計師 Jane 及雲端基礎架構設計師 Todd 所規劃的漸進式步驟，將現有應用程式 Stock Trader 現代化。此使用案例顯示的範例可協助您在旅程中採取每個步驟，並實現您的企業價值，不論每個步驟是大還是小。

此旅程的大部分焦點都在於將 Stock Trader 應用程式現代化。若要將您的業務完全現代化為雲端原生業務，必須討論應用程式、DevOps、整合及管理佈景主題。所有佈景主題都會共同運作，協助您達到目標。現代化一個佈景主題，而未現代化其他佈景主題，可能會導致問題。

## 現代化的原因
{: #vcscontent-modjourney-reasons}

### 應用程式現代化
{: #vcscontent-modjourney-app-mod}

目標是可調整及回應快速變化需求的雲端原生應用程式。

* 您需要將現有應用程式現代化，並建立新的雲端原生應用程式來擷取客戶的想像。
* 您需要應用程式可以調整規模、全球連結、依需求調整、改變、加強且可快速調整樞軸轉向。

### DevOps 現代化
{: #vcscontent-modjourney-devops-mod}

當您將應用程式現代化時，會將您交付該應用程式的方式（即整個交付管道）現代化，因此，您開發人員所建立的新雲端原生文化可以調整為如何交付該應用程式。

* 當您將應用程式現代化時，需要將「開發及作業（和安全）」文化現代化。
* 您需要 DevOps 團隊可以調整規模、全球連結、依需求調整、改變、加強且可快速調整樞軸轉向。

###  整合現代化
{: #vcscontent-modjourney-integration-mod}

在整個現代化旅程，您的團隊需要與現有資產、新雲端服務、您的資料以及從對該資料執行之分析所取得的新見解整合。

* 您需要透過可以調整規模、全球連結、依需求調整、改變、加強且可快速調整樞軸轉向的方法，在此旅程使用現有資產。
* 您需要在此旅程的每個步驟，使用新的雲端服務進行強化。
* 您需要整合資料與從將分析套用至資料所取得的見解。

### 管理
{: #vcscontent-modjourney-mgmt}

將管理實務現代化是在將應用程式現代化時所採取的另一個平行旅程。如何管理及維護現代化應用程式的工具、文化及核心行為與之前極為不同。

* 您需要使用內建的編排、記載及監視來管理微服務及容器化中介軟體。
* 您需要透過可以調整規模、全球連結、依需求調整、改變、加強且可快速調整樞軸轉向的方法，管理全球各地的多重雲端混合式平台。
* 您需要以自動化方式來管理多個雲端，以及其上執行的應用程式及中介軟體。

## 滿足 Todd 及 Jane
{: #vcscontent-modjourney-todd-jane}

對於我們的 Stock Trader 旅程，我們聚焦於兩個人：Todd 及 Jane。Todd 是 ACME 公司的作業負責人，負責基礎架構、安全、雲端環境，以及確保其中執行的工作負載符合各種法規的原則。

Jane 是 Stock Trader 解決方案的發展領導人，現在必須負責將 Stock Trader 現代化，這表示與其開發團隊合作來變更開發工具、文化及平台，以將現有的整合型 Stock Trader 解決方案現代化為可運作良好的雲端原生解決方案。

## 滿足 Stock Trader
{: #vcscontent-modjourney-meet-stock-trader}

Todd 及 Jane 已建置在 WebSphere 中執行的應用程式，稱為 Stock Trader。雖然它具有基本使用者介面，但本身為組合管理員可在其中管理組合（包括購買及銷售股票，以及檢視內部忠誠度層次）的可靠應用程式。

Stock Trader 可在 WebSphere 中執行、使用幾個 .war 檔建置，並使用在其信賴多年之資料中心內執行的傳統 Db2 資料庫。基於基礎架構團隊、開發團隊與資料團隊之間的相依關係，需要花很長的時間來加強此應用程式。

不過，雖然 Stock Trader 不錯，但公司中的每個人還是會覺得不足。產品經理想要在其忠誠度計畫中新增社交媒體。Jane 很高興，因為她可以將應用程式重構為微服務，讓它們持續交付具有較少相依關係的加強功能。Todd 愛雲端效率的構想，但仍需要控管以維護與公司原則的法規遵循。

## 旅程的步驟
{: #vcscontent-modjourney-steps}

Todd 及 Jane 透過經驗得知將解決方案現代化的不錯旅程是從導覽圖開始。雖然計劃可能會變更，但從這個願景來思考一向是不錯選擇，並定義一個實際的路徑來達成。每個步驟都必須對公司有其價值，而且這些步驟不致於重要到對客戶造成代價慘重的岔斷。

對於 Todd 和 Jane，他們在 Stock Trader 旅程中的步驟如下：
1. 將 Stock Trader VM 放入 {{site.data.keyword.cloud_notm}}。此步驟可讓 Todd 不需要在本端資料中心內管理自己的硬體及 VMware 內容。

2. 將 WebSphere Application Server 中的 Stock Trader 轉變成容器中的 Stock Trader。此步驟可增加備援，因為在 Kubernetes 中執行容器會產生編排及其他雲端行為。這需要 Todd 在其 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 環境中準備 {{site.data.keyword.cloud_notm}} Private 實例，然後讓 Jane 與 Transformation Advisor 合作以將 Stock Trader 容器化。

3. 將中介軟體重構及新增至 {{site.data.keyword.cloud_notm}} Private。此步驟會將其現有中介軟體帶入雲端環境，並最佳化雲端行為。這也會簡化授權，並準備完全可攜以用於其他 Kubernetes 環境的解決方案。

4. 使用 Watson 及其他公用雲端服務強化。此步驟可以透過在 AI 服務取回，以及與全球雲端資料中心進行通訊的能力，以指數方式新增 Stock Trader 體驗的價值。

5. {{site.data.keyword.cloud_notm}} Kubernetes Service 的真正混合。此步驟可讓 Todd 具有受管理 Kubernetes 服務，而此服務仍然連接至與其 {{site.data.keyword.cloud_notm}} Private 實例相同的雲端地區。它也可讓 Jane 的開發團隊擁有他們可實驗的開發及測試叢集，同時仍然存取與其核心 {{site.data.keyword.cloud_notm}} Private 叢集相同的資料來源。

6. 將 DevOps 現代化。在此旅程中，Jane 改善 Stock Trader 交付方式。

7. 將管理現代化。Todd 及 Jane 合作以改善 Stock Trader 管理方式，以及其執行所在的平台，甚至跨多個叢集及雲端環境。

## 相關鏈結
{: #vcscontent-modjourney-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
