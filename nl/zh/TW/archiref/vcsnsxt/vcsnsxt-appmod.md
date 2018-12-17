---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# 應用程式現代化概觀

下圖顯示 Acme Skateboards 所部署的應用程式現代化參照架構，在此系列文件中會有深入說明。

圖 1. 架構概觀
![架構概觀圖](vcsnsxt-aod.svg)

此混合式架構可讓 Acme Skateboards 執行下列作業：
- 以極少的關閉時間或不需要關閉時間，即可將 VMware 虛擬機器 (VM) 從內部部署移轉到 {{site.data.keyword.cloud}}，且不需要重新配置應用程式。
-	可讓 Acme Skateboards 專注在將較簡單的 Web 介面和中介軟體容器化，同時允許較複雜的資料庫保持作為 VM，而開始應用程式現代化旅程。
-	運用 Cloud Automation Manager (CAM) 來編寫「基礎架構即程式碼 (IaC)」，以組合並編排從 VM 和容器建立的服務，使其與 DevOps 工具鏈和 ITSM 解決方案整合。

聚焦於網路架構，此參照架構具有下列主要元件：
- **內部部署虛擬化** - 這是目前管理 Acme Skateboards VM 的 VMware 叢集。目前就是由這些 VM 來管理將要現代化的應用程式。此叢集必須符合 [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)文件中所記錄的必要條件，才能執行 HCX。HCX 會將內部部署網路延伸至 {{site.data.keyword.cloud_notm}}，讓客戶可以將 VM 移轉至正在 {{site.data.keyword.cloud_notm}} 上執行的 VCS 實例，並視需要移轉回來。
- **VMware vCenter Server on IBM Cloud** - VCS 提供必要的基礎 VMware 構成要素：vSphere、vCenter Server、NSX-V 及儲存空間選項（包括 vSAN 或「{{site.data.keyword.cloud_notm}} 耐久性」儲存空間），以自動部署「VMware 軟體定義資料中心 (SDDC)」解決方案。此 VMware 叢集是移轉 VM 的目標，也是 ICP 所管理容器中部分現代化應用程式的目標。

  架構的主要元件如下：
 - **NSX-V** - NSX-V 提供 VCS 中的網路虛擬化層級，可為 Acme Skateboards VM 提供網路層疊。NSX-V 會啟用 BYOIP，並將工作負載網路與 {{site.data.keyword.cloud_notm}} 網路隔離開來。NSX-V 是由 HCX 進行程式設計，以建立 Acme Skateboards 要從內部部署延伸的網路。
 - **IBM Cloud Private** - ICP 是用來開發及管理容器化應用程式的應用程式平台。這是整合環境，其中包括容器編排程式 Kubernetes、專用映像檔儲存庫、管理主控台、監視架構，以及圖形使用者介面，Acme Skateboards 可以集中在此介面中部署、管理、監視及調整其應用程式。VCS 實例會管理 ICP 元件、主節點、工作者節點等等，並且以 VM 的形式執行它們。
  -	**IBM Cloud Automation Manager** - CAM 是準備供企業使用的現成「基礎架構即程式碼 (IaC)」平台，其提供單一窗格，可以直接使用範本同時佈建虛擬機器型工作負載與 Kubernetes 型工作負載。CAM 是在 ICP 之上執行的 Docker 化應用程式，針對授權、RBAC 和其他功能緊密整合。
  - **IBM Kubernetes Service** - IKS 可讓 Acme Skateboards 將其現代化的應用程式部署在執行於 Kubernetes 叢集的 Docker 容器中。主節點完全由 IBM 管理，而工作者節點儲存區中的工作者節點會部署至與其 VCS 實例相同的 {{site.data.keyword.cloud_notm}} 帳戶。工作者節點是裸機、公用或專用虛擬伺服器實例。Calico 會自動安裝並配置在 IKS 中。Calico 為容器提供安全的網路連線功能，而且配置在 IKS 中，可將 IP-in-IP 封裝用於封裝在子網路之間傳輸的封包，並針對從容器送出的連線使用 NAT。
  - **Direct Link** - {{site.data.keyword.cloud_notm}} Direct Link 使用 Acme Skateboards 的 WAN 提供者將其資料中心連接至 {{site.data.keyword.cloud_notm}}，以提供可靠、低延遲、安全的網路連線。此連線提供：
      - 從企業使用者存取雲端管理的應用程式。
      - 內部部署 VM 與雲端 VM 之間的 VM 間資料流量。
      - 內部部署資料中心與雲端 VM 中，舊式系統之間的資料流量。

## Acme Skateboards 的主要優點

-	已將採購、架構、實作及部署資源所需的時間從數週甚至數個月縮減為數小時，以加速將 IT 專案交付給開發人員和事業單位。等待網路或安全團隊佈建負載平衡器、防火牆、交換器和路由器這類服務，可縮短其創造價值的時間。
-	已利用受管理專用雲端中的專用 Bare Metal Server 來加強安全，包括將專用端點部署至 {{site.data.keyword.cloud_notm}} 服務（例如 IKS 和 KMIP）。
-	提供虛擬化管理的完整管理存取權，而能夠對所部署的混合式雲端進行一致的管理與控制，進而保留您現有的 VMware 工具、Script 和訓練投資。
-	透過遍佈全球 30 個以上 {{site.data.keyword.CloudDataCents_notm}} 的 IBM Professional and Managed Services 的全球規模 VMware 專門知識。

朝向雲端原生應用程式平台（例如 ICP 和 IKS）移動的客戶著重於速度與創新，而不必隨時心中掛記著安全與網路。此參照架構顯示 VCS、ICP 和 IKS 如何安全地推動 Acme Skateboards 的應用程式現代化旅程。

## 相關鏈結

* [VCS Hybridity Bundle 概觀](../vcs/vcs-hybridity-intro.html)
