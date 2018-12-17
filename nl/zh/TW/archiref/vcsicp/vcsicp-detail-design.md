---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---

# 詳細的設計

## 共用服務元件
共用服務提供雲端管理平台中其他服務所使用的服務。共用服務包括身分及存取服務、網域名稱服務及 NTP 服務。

圖 1. {{site.data.keyword.cloud_notm}} Private (ICP) 共用服務

![ICP 共用服務](vcsicp-icp-commonservices.svg)

### 身分及存取服務
在 VMware vCenter Server on {{site.data.keyword.cloud}} 自動化過程中，採用 Microsoft Active Directory (AD) 來進行身分管理。已部署單一 AD 虛擬伺服器實例 (VSI)。vCenter 配置為使用 AD 鑑別，而且您可以配置 ICP 進行「LDAP 鑑別」。

###	網域名稱服務
vCenter Server 部署會將已部署的 AD VSI 用作實例的 DNS 伺服器。所有已部署的元件（例如，vCenter、PSC、NSX 及 ESXi 主機）都會配置成指向 AD，以作為其預設 DNS。

###	NTP 服務
vCenter Server 部署使用 {{site.data.keyword.cloud_notm}} 基礎架構 NTP 伺服器。所有已部署的元件都已配置成使用這些 NTP 伺服器。為了讓憑證和 AD 鑑別正常運作，使設計內的所有元件都使用相同的 NTP 伺服器十分重要。

## 網路

### NSX-V 網路

NSX-V 的設計讓單一 NSX-V Manager 平台與單一 vCenter Server 實例相關聯。它將網路服務提供給在 vSphere 環境內執行的應用程式。

使用 VCS 部署中所含的 NSX-V 網路，我們可以將 ICP 部署到 VXLAN 層疊網路。

ICP 是使用 Kubneges 的預設 Calico 網路堆疊進行部署，可在您的叢集內提供網路隔離。

圖 2. 具有 NSX-V 網路功能的 ICP

![具有 NSX-V 網路功能的 ICP](vcsicp-nsxv-networking.svg)

如需相關資訊，請參閱 [vCenter Server 網路手冊](../vcsnsxt/vcsnsxt-intro.html)。

### NSX-T 網路

NSX-T 的設計讓單一網路平台可以連接到任何類型的應用程式，不論是虛擬機器型還是容器型、在 vSphere 環境內部或外部執行。

ICP 提供將 Calico 網路取代為 NSX-T 實例的選項，並提供單一位置以便管理網路和安全。

圖 3. 具有 NSX-T 網路的 ICP

![具有 NSX-T 網路的 ICP](vcsicp-icp-nsxt-networking.svg)

### 相關鏈結

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](../vcs/vcs-hybridity-intro.html)
