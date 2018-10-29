---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# 常見服務設計

常見服務提供雲端管理平台中其他服務所使用的服務。解決方案的常見服務包括身分及存取服務、網域名稱服務、NTP 服務、SMTP 服務及憑證管理中心服務。

## 身分及存取服務

在此設計中，Microsoft Active Directory (AD) 用於身分管理。此設計會部署一或兩部 Windows Active Directory 虛擬機器，作為 Cloud Foundation 及 vCenter Server 部署自動化的一部分。vCenter 將配置成使用 AD 鑑別。

### Microsoft Active Directory

依預設，單一 Active Directory VSI 會部署至 {{site.data.keyword.cloud}} 基礎架構。此設計還提供選項，可將兩部高可用性 Microsoft Active Directory 伺服器部署為管理叢集裡的專用 Windows Server VM。

**附註**：如果您選擇這個選項，則負責提供 Microsoft 授權及啟動。

Active Directory 僅用來鑑別管理 VMware 實例的存取權，並不會將工作負載的一般使用者存放至已部署的實例。Active Directory 伺服器的樹系根網域名稱等於您指定的 DNS 網域名稱。只有在鏈結多個實例時，才會針對主要 Cloud Foundation 及 vCenter Server 實例指定此網域名稱。如果是已鏈結的實例，則每個實例都會包含位於樹系根抄本環中的 Active Directory 伺服器。DNS 區域檔案也會在 Active Directory 伺服器上進行抄寫。

### vSphere SSO 網域

vSphere Single Sign On (SSO) 網域用來作為單一實例或多個已鏈結實例的起始鑑別機制。SSO 網域也可用來將某個 VMware 實例或多個已鏈結實例連接至 Microsoft Active Directory 伺服器。會套用下列 SSO 配置：  
* 一律使用 SSO 網域 `vsphere.local`
* 對於與現有實例相關聯的 VMware 實例，PSC 會加入至現有實例的 SSO 網域
* SSO 站台名稱等於實例名稱

## 網域名稱服務 (DNS)

此設計中的 DNS 僅適用於雲端管理及基礎架構元件。

### VMware vCenter Server

vCenter Server 部署會將已部署的 Active Directory 伺服器用作實例的 DNS 伺服器。所有已部署的元件（vCenter、PSC、NSX 及 ESXi 主機）都會配置成指向 Active Directory 伺服器，以作為其預設 DNS 伺服器。如果您的配置不會干擾已部署元件的配置，則您可以自訂 DNS 區域配置。

此設計會透過下列配置來整合 Active Directory 伺服器上的 DNS 服務：
* 您可以指定網域結構。網域名稱可以是任意數目的層次（最多為 vCenter Server 元件將處理的上限）。最低層次是實例的子網域。
   * 您指定的 DNS 網域名稱將會用來作為 Active Directory 根樹系網域名稱。例如，如果 DNS 網域名稱為 `cloud.ibm.com`，則 Active Directory 樹系根網域名稱為 `cloud.ibm.com`。在所有已鏈結的 vCenter Server 實例中，此 DNS 與 Active Directory 網域名稱會相同。
   * 您可以額外指定實例的子網域名稱。在所有已鏈結的 vCenter Server 實例中，子網域名稱必須是唯一的。
* 將 Active Directory DNS 伺服器配置成具有 DNS 網域及子網域空間的授權性。
* 將 Active Directory DNS 伺服器配置成指向所有其他區域的 {{site.data.keyword.cloud_notm}} DNS 伺服器。
* 任何要整合至現有目標實例的實例都必須使用與主要實例相同的網域名稱。

### VMware Cloud Foundation

Cloud Foundation 部署使用 VMware Cloud Foundation 自動化，以使用它自己在 SDDC Manager VM 元件內的 DNS 伺服器。SDDC Manager 所管理的 Cloud Foundation 元件（包括 vCenter、PSC、NSX 及 ESXi 主機）依設計會配置成使用 SDDC Manager VM IP 位址作為其預設 DNS。

因為 SDDC Manager 會為其管理的元件產生及維護主機名稱，所以不建議透過新增及移除主機來直接竄改其 DNS 區域檔案。

此設計會使用下列配置來整合 Active Directory 伺服器上的 DNS 服務與 SDDC Manager VM：
* 您可以指定網域結構。網域名稱可以是任意數目的層次（最多為 Cloud Foundation 元件將處理的上限）。
* 最低層次是 SDDC Manager 具有授權性的子網域。
* 您指定的 DNS 網域名稱將會用來作為 Active Directory 根樹系網域名稱。例如，如果 DNS 網域名稱為 `cloud.ibm.com`，則 Active Directory 網域樹系根為 `cloud.ibm.com`。在所有已鏈結的 Cloud Foundation 實例中，此 DNS 網域與 Active Directory 網域會相同。
* 您可以額外指定實例的子網域名稱。在所有已鏈結的 Cloud Foundation 實例中，子網域名稱必須是唯一的。  
* SDDC Manager DNS 配置會變更為指向所有區域的 Active Directory 伺服器，但它負責的區域除外。
* 將 Active Directory DNS 伺服器配置成具有 SDDC Manager 上方之 DNS 網域空間與 Cloud Foundation 實例子網域的授權性。
* 將 Active Directory DNS 伺服器配置成指向 SDDC Manager 具有授權性之區域子網域委派的 SDDC Manager IP 位址。
* 將 Active Directory DNS 伺服器配置成指向所有其他區域的 {{site.data.keyword.cloud_notm}} DNS 伺服器。
* 任何要整合至第一個或目標實例的次要實例都必須利用 SDDC Manager 子網域上方的相同 DNS 名稱結構。

## NTP 服務

此設計利用 {{site.data.keyword.cloud_notm}} 基礎架構 NTP 伺服器。所有已部署的元件都已配置成利用這些 NTP 伺服器。為了讓憑證及 Active Directory 鑑別正常運作，使此設計內的所有元件都使用相同的 NTP 伺服器十分重要。

圖 1. NTP 服務

![NTP 服務](commonservice_ntp.svg "在此設計中，實例的所有元件都會透過 NTP 服務使用相同的 {{site.data.keyword.cloud_notm}} 基礎架構 NTP 伺服器。")

## 憑證管理中心服務

依預設，VMware vSphere 會使用位於 VMware Platform Services Controller 應用裝置之「VMware 憑證管理中心 (VMCA)」所簽署的 TLS 憑證。一般使用者裝置或瀏覽器不會信任這些憑證。將面對使用者的憑證取代為協力廠商或企業憑證管理中心 (CA) 所簽署的憑證，是一種安全最佳作法。機器對機器通訊的憑證可以保留作為 VMCA 所簽署的憑證，不過，建議您遵循組織的最佳作法，這通常涉及使用已識別的企業 CA。

您可以使用此設計內的 Windows AD 伺服器來建立本端實例所簽署的憑證。不過，必要的話，您也可以選擇配置 CA 服務。

### 相關鏈結

* [實體基礎架構設計](design_physicalinfrastructure.html)
* [虛擬基礎架構設計](design_virtualinfrastructure.html)
* [基礎架構管理設計](design_infrastructuremgmt.html)
