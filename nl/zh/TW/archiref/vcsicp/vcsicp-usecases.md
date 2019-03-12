---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-18"

---

# 使用案例
{: #vcsicp-usecases}

## 工作負載移轉至 IBM Cloud
{: #vcsicp-usecases-wkld-mig}

Acme Skateboards 想要將其內部部署 VMware SDDC 無縫延伸到 VMware vCenter Server on {{site.data.keyword.cloud}} 實例。他們需要讓業務持續運作，並使關閉時間降到最低。重新配置其應用程式以便在雲端執行並不是最佳解決方案。

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 能夠在 {{site.data.keyword.cloud_notm}} 與內部部署 VMware 虛擬化資料中心之間建立無縫連線。

{{site.data.keyword.cloud_notm}} 的 vCenter Server with Hybridity Bundle 供應項目能夠促成對等內部部署來源站台與 {{site.data.keyword.cloud_notm}} 目標站台之間的安全連線。

圖 1. VMware Hybridity 服務

![VMware Hybrid Cloud Extension Services](vcsicp-hcx.svg)

VMware Hybrid Cloud Extension Services 會在內部部署與 {{site.data.keyword.cloud_notm}} 之間建立鬆散耦合的交互連線，並且啟用下列這類功能：
- **簡單交互連線** - 可透過任何實體連線（包括公用網際網路、專用 VPN 或 {{site.data.keyword.cloud_notm}} Direct Link），輕鬆建立邏輯網路連線。
- **第 2 層延伸** - 內部部署網路延伸至雲端，包括內部部署子網路和 IP 位址。
- **加密** - 在對等節點站台之間安全地加密網路資料流量。
- **網路最佳化** - 選取最佳連線，並有效率地溢滿連線，讓網路資料流量儘可能地快速移動。
- **刪除重複資料** - 可讓網路資料流量減少達 50%。
- **智慧型遞送** - 當工作負載移動時，鄰近遞送可以變更網路路徑（即閘道），讓網路資料流量使用目標站台閘道，而不會「回流」到起始站台。
- **零關閉時間移轉** - 使用 vMotion 將執行中的虛擬機器 (VM) 移至雲端，或從雲端移回。
- **排定的移轉** - 您可以將任意數目的 VM 抄寫至目的地站台，然後在該站台上依指定時間啟動，以取代在起始站台上執行的系統。
- **安全原則的移轉** - 如果在內部部署使用 NSX，則任何安全原則、防火牆等等，都會隨著工作負載一起移動。

使用這個解決方案，Acme Skateboards 已順利將其內部部署 VMware 工作負載移轉至 {{site.data.keyword.cloud_notm}}，以滿足極短或沒有任何關閉時間且不需重新配置應用程式的需求。

## 混合式架構部署
{: #vcsicp-usecases-hybrid-archi-deployment}

Acme Skateboards 想要在由 vCenter Server 和 {{site.data.keyword.icpfull_notm}} 組成的 {{site.data.keyword.cloud_notm}} 上部署混合式架構，以進行應用程式現代化。他們的需求是在虛擬機器上執行其資料庫、在容器中執行應用程式和 Web 服務，並使用一組共用的工具來進行網路和安全管理。

圖 2. Acme Skateboards 混合式應用程式

![Acme Skateboards 混合式應用程式](vcsicp-acme-skateboards-app.svg)

{{site.data.keyword.vmwaresolutions_short}} 提供自動化，以在全球的 {{site.data.keyword.CloudDataCents_notm}} 中部署 VMware 技術元件。架構由單一雲端地區組成，可支援延伸至位於另一個地理位置的其他雲端地區，或延伸至相同資料中心內的另一個 {{site.data.keyword.cloud_notm}} Pod。

{{site.data.keyword.icpfull_notm}} 及 Cloud Automation Manager (CAM) 產品會手動部署至內部部署的虛擬化平台，因而能夠從內部部署位置進行雲端管理。或者，{{site.data.keyword.icpfull_notm}} 和 CAM 也可以透過自動化功能當作服務延伸提供給現有或新的 vCenter Server 部署，因而能夠從 {{site.data.keyword.cloud_notm}} 進行雲端管理。

下圖代表 vCenter Server 實例上執行的 {{site.data.keyword.icpfull_notm}}。NSX-V 已配置專用交換器/VXLAN、DLR，以及專門用於 {{site.data.keyword.icpfull_notm}} 層疊網路的 ESG，而且透過 ESG 設定遞送來存取基礎網路。

使用 {{site.data.keyword.cloud_notm}} 自動化，Acme Skateboards 可以佈建封裝 VMware on {{site.data.keyword.cloud_notm}} 的混合式解決方案，以在 VMware on {{site.data.keyword.cloud_notm}} 上執行其資料庫 VM 和 {{site.data.keyword.icpfull_notm}}，並在容器中執行其應用程式和前端系統 Web 服務。NSX 為其提供一組共用的管理工具，用來管理層疊網路中的網路和安全。

圖 3. 具有 {{site.data.keyword.icpfull_notm}} 的 vCenter Server

![具有 {{site.data.keyword.icpfull_notm}} 的 vCenter Server](vcsicp-virtual-icp-deployment-vcs.svg)

## 相關鏈結
{: #vcsicp-usecases-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
