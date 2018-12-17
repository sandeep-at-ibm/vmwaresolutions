---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---

# 架構概觀

{{site.data.keyword.vmwaresolutions_full}} 供應項目提供自動化，以在全球的 {{site.data.keyword.CloudDataCents_notm}} 中部署 VMware 技術元件。架構由單一雲端地區組成，可支援延伸至位於另一個地理位置的其他雲端地區，及/或延伸至相同資料中心內的另一個  {{site.data.keyword.cloud_notm}} Pod。

您可以將 {{site.data.keyword.cloud_notm}} Private (ICP) 及 Cloud Automation Manager (CAM) 產品手動部署至內部部署的虛擬化平台，因而能夠從內部部署位置進行雲端管理。或者，ICP 及 CAM 也可以當作服務延伸提供給現有或新的 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 部署，透過自動化功能，從 {{site.data.keyword.cloud_notm}} 進行雲端管理。

ICP 是用來開發及管理內部部署容器化應用程式的應用程式平台。ICP 是用來管理容器的整合環境，其中包括容器編排程式 Kubernetes、專用映像檔儲存庫、管理主控台和監視架構。

IBM Multi-Cluster Manager (MCM) 提供使用者可見性、以應用程式為中心的管理（原則、部署、性能、作業），以及雲端與叢集之間的原則型規範。透過 MCM，您可以控制 Kubernetes 叢集。您可以確保叢集安全、有效率地運作，並且提供在 ICP 上執行的服務管理平台，讓開發人員和管理者能夠符合商業需求。使用 Cloud Automation Manager 服務編製器來顯示 ICP 型錄中的混合式雲端服務。

## IBM Cloud 端的雲端管理平台

下列是具有 {{site.data.keyword.cloud_notm}} 基礎架構的 ICP 及 CAM 部署範例，以及部署在 {{site.data.keyword.cloud_notm}} 之內部部署 vCenter 及 IBM Kubernetes Service (IKS) 服務的連線。使用者可以在內部部署虛擬機器 (VM)、將 VM 部署至 vCenter Server 實例，以及將容器部署至 ICP 及 IKS 叢集。

圖 1. 從雲端進行雲端管理

![在雲端上 - 雲端管理](vcsicp-oncloud-cloudmgt.svg)

在圖表中，CAM 邏輯地建立與 vCenter、雲端提供者、ICP 和 IKS 環境的雲端連線。「ICP 叢集」必須部署至每個資料中心雲端環境，並由 MCM 提供將 ICP 叢集連接至單一管理視圖的機制。

您可以部署具有 NSX-V 或 NSX-T 元件的 ICP。ICP 搭配 NSX-V 可讓 ICP VM 在 VXLAN 網路上執行，並使用 Kubernetes Calico 內部網路。

ICP 搭配 NSX-T 可讓使用者從中央使用者介面 (NSX-T Manager) 控制及配置網路、子網路、原則。若要瞭解 NSX-V 與 NSX-T 之間的差異，請參閱 [vCenter Server 網路手冊](../vcsnsxt/vcsnsxt-intro.html)。

## 內部部署雲端管理平台

下圖是內部部署基礎架構中的 ICP 及 CAM 部署範例，以及部署在 {{site.data.keyword.cloud_notm} 之 vCenter 及 IKS 的連線。使用者可以在內部部署 VM、將 VM 部署至 vCenter Server 實例，以及將容器部署至 IKS 叢集。

圖 2. 從內部部署端進行雲端管理
![內部部署雲端管理](vcsicp-onprem-cloudmgt.svg)

strongSwan VPN 可用來與已部署的 IKS 容器建立連線。strongSwan VPM 可能會取代為 Direct Link 連線。

在圖表中，CAM 邏輯地建立與 vCenter、雲端提供者、ICP 和 IKS 環境的雲端連線。ICP 叢集必須部署至每個資料中心雲端環境，並由 MCM 提供將 ICP 叢集連接至單一管理視圖的機制。

### 相關鏈結

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](../vcs/vcs-hybridity-intro.html)
