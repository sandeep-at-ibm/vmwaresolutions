---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# IBM Cloud for VMware Solutions 的一般常見問題

尋找 {{site.data.keyword.vmwaresolutions_full}} 相關常見問題的回答。

## IBM Cloud for VMware Solutions 需要何種使用者帳戶？

* **IBM ID 帳戶**。需要此帳戶才能存取 {{site.data.keyword.vmwaresolutions_short}} 主控台。主控台是與 {{site.data.keyword.slportal}} 分開的獨立式使用者介面。如需相關資訊，請參閱[開始使用](../index.html)。
* **{{site.data.keyword.cloud_notm}} 帳戶**。需要此帳戶才能進行佈建。您可以使用現有 **IBM ID** 或建立新的 **IBM ID**，來註冊 {{site.data.keyword.cloud_notm}} 帳戶。
* **{{site.data.keyword.cloud_notm}} 基礎架構帳戶**。此帳戶（先前稱為 **IBM SoftLayer** 帳戶）用來登入 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站，以提供一些額外功能來管理基礎架構產品及服務。您可以取得 {{site.data.keyword.cloud_notm}} 基礎架構帳戶，方法是將 **{{site.data.keyword.cloud_notm}} 帳戶**升級至「隨收隨付制」類型的帳戶，或將現有 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶鏈結至 {{site.data.keyword.cloud_notm}} 帳戶。您使用的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶必須符合特定需求。如需相關資訊，請參閱[註冊必要帳戶](signing_softlayer_account.html)及 [{{site.data.keyword.cloud_notm}} 基礎架構帳戶需求](slaccountrequirement.html)。

## 如何使 IBM Cloud 基礎架構認證與 IBM Cloud for VMware Solutions 主控台產生關聯？

第一次訂購實例時，請遵循主控台之**設定**頁面上的指示，從 {{site.data.keyword.slportal}} 中尋找並複製 {{site.data.keyword.cloud_notm}} 基礎架構使用者名稱及 API 金鑰。第一次訂購之後，{{site.data.keyword.cloud_notm}} 基礎架構認證會儲存在 {{site.data.keyword.vmwaresolutions_short}} 主控台中。未來訂單會自動使用已儲存的認證。

## 我的 VMware 虛擬平台耗用如何計費？

實體和虛擬基礎架構的所有成本以及從實例中產生的授權會向您的 {{site.data.keyword.cloud_notm}} 帳戶收費。訂購實例時，您必須具有 {{site.data.keyword.cloud_notm}} 帳戶，並提供與該帳戶相關聯的 {{site.data.keyword.slapi_short}} 金鑰。

## vCenter Server 實例、Cloud Foundation 實例與 VMware vSphere 叢集之間有何差異？

所有實例類型都提供 VMware 虛擬環境的部署選項。不過，差異在於自訂功能及自動化的範圍。

* 當您訂購 VMware vCenter Server 實例時，您會部署具有自訂運算、儲存空間及網路資源的 VMware 虛擬環境。如需已部署元件的相關資訊，請參閱 [vCenter Server 實例的技術規格](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)。
* 當您訂購 VMware Cloud Foundation 實例時，您將部署統一的軟體定義資料中心 (SDDC) 平台。如需已部署元件的相關資訊，請參閱 [Cloud Foundation 實例的技術規格](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)。
* 當您訂購 VMware vSphere 叢集時，您會有最大的彈性來設計及建置受管理的 VMware 環境，同時納入 VMware 相容的硬體。不過，{{site.data.keyword.cloud_notm}} 不會使 VMware vSphere 叢集之選用 VMware 元件的安裝、配置及啟動自動化。
* 對 vCenter Server 實例、Cloud Foundation 實例及 vSphere 叢集所支援的功能不同。如需相關資訊，請參閱[提供比較圖表](inst_comp_chart.html)。

## vCenter Server 實例包含了什麼？

如需相關資訊，請參閱 [vCenter Server 實例的技術規格](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)。

## Cloud Foundation 實例包含了什麼？

如需相關資訊，請參閱 [Cloud Foundation 實例的技術規格](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)。

## vSphere 叢集包括哪些內容？
如需相關資訊，請參閱 [VMware vSphere on {{site.data.keyword.cloud_notm}} 的元件](../vsphere/vs_vsphereclusteroverview.html)。

## 雙節點 vCenter Server 實例是否為高可用性？

建議將正式作業工作負載部署到至少有三個節點的環境。

依預設，會啟用 VMware vSphere DRS（分散式資源排程器）及 VMware HA（高可用性）。不過，來自 VMware 的最佳作法建議您將三個 NSX Controller 的每個都放置在個別節點上。

在雙節點的最小部署中，一個節點具有一個 NSX Controller，另一個節點具有兩個 NSX Controller。如果具有兩個 NSX Controller 的節點關閉，則 NSX Controller 作業會處於唯讀模式，而新的 VM（虛擬機器）或 vMotion VM 可能會遇到網路問題。

當第三個節點新增至雙節點叢集時，vCenter Server 會自動在三個節點之間重新平衡三個 NSX Controller，並建立高可用性環境。

## 我可以設定 VMware vCenter 6.5 HA 配置嗎？

不，不建議這麼做。可能會發生 {{site.data.keyword.vmwaresolutions_short}} 功能失敗。

## 叢集可以重新命名嗎？

對於 vCenter Server 實例，在部署期間建立的第一個叢集，其預設名稱為 **cluster1**。您可以在 VMware vSphere Client 中將預設叢集重新命名。當您將叢集新增至 vCenter Server 實例時，可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台上指定您想要的名稱。

**附註：**對於 Cloud Foundation 實例，無法變更預設叢集名稱。

##如何管理修補程式？

IBM 提供 IBM 程式碼的持續更新，方法是隨需應變部署 IBM CloudDriver 虛擬伺服器實例 (VSI)。IBM 不對 Zerto on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}} 等附加服務提供持續更新。您必須負責取得並安裝這些更新。

根據您已部署的 VMware 實例類型，會以不同的方式套用 VMware 更新：

* 對於 VMware Cloud Foundation 實例，透過 {{site.data.keyword.vmwaresolutions_short}} 主控台提供 vSphere ESXi、NSX、vCenter、Platform Services Controller 及 SDDC Manager 元件的更新。
* 對於 VMware vCenter Server 實例：
  * 對於已部署至或升級至 2.1 版或更新版本的實例，新部署的 ESXi 伺服器和叢集將以 VMware 所提供最近但未必最新的 ESXi 更新進行修補。
  * 您必須負責處理 VMware 元件的所有其他更新，包括確保新部署的 ESXi 伺服器和叢集具有您需要的所有最近更新。
  * 對於在 2.0 版或更新版本上部署的實例，VMware Update Manager (VUM) 已整合至 vCenter Server。您可以配置 VUM 來下載 VMware 的 ESXi 更新。

如需相關資訊，請參閱下列資源：
* [VMware 支援](https://www.vmware.com/support.html)
* [將更新套用至 vCenter Server 實例](../vcenter/vc_applyingupdates.html)
* [將更新套用至 Cloud Foundation 實例](../sddc/sd_applyingupdates.html)

## 管理服務 NSX Edge 是否造成安全風險？

雖然管理服務的 VMware NSX Edge 位於公用子網路上，但仍提供安全措施，以確保不會造成安全風險。這些措施如下：
*  已配置 NSX Edge 防火牆，只容許管理虛擬機器所起始的送出 HTTPS（TCP 埠 443）資料流量。
*  使用 SNAT（來源網址轉換），使專用 IP 位址不顯示於專用網路以外。
*  已停用對管理服務 NSX Edge 應用裝置的遠端存取。
*  從專用網路存取管理服務 NSX Edge 的密碼已隨機化且已加密。

## 客戶管理的 NSX Edge 是否造成安全風險？

雖然客戶管理的 NSX Edge 已連接至公用 VLAN，但仍提供安全措施，以確保不會造成安全風險。以下是可用的安全測量：
*  已設置防火牆規則，只容許來自專用子網路 IP 位址範圍的送出資料流量。
*  已設置 SNAT（來源網址轉換）規則（依預設會停用），將專用子網路中的所有 IP 位址轉換為公用子網路上的單一 IP 位址。
*  已停用對客戶管理的 NSX Edge 應用裝置的遠端存取。
*  從專用網路存取客戶管理的 NSX Edge 的密碼已隨機化且已加密。

## 如何為我的實例選擇資料中心？

實例部署具有嚴格的實體基礎架構需求，這在 {{site.data.keyword.CloudDataCents_notm}} 之間會不同。當您訂購實例時，會列出地區內的可用資料中心，而且您可以從此清單中選取您要的資料中心。

如需相關資訊，請參閱以下的 _IBM Cloud Data Center 可用性_ 小節：
* [vCenter Server 實例的需求及規劃](../vcenter/vc_planning.html)
* [vCenter Server with Hybridity Bundle 實例的需求及規劃](../vcenter/vc_hybrid_planning.html)
* [Cloud Foundation 實例的需求及規劃](../sddc/sd_planning.html)
* [VMware vSphere on {{site.data.keyword.cloud_notm}} 的需求及規劃](../vsphere/vs_planning.html)
* [NetApp ONTAP Select 實例的需求及規劃](../netapp/np_planning.html)
* [VMware Federal 實例的需求與規劃](../vcenter/vc_fed_planning.html)

## 部署實例需要花費多久的時間？

您可以從 {{site.data.keyword.vmwaresolutions_short}} 主控台檢視實例詳細資料頁面上的部署歷程，以檢查實例部署的狀態。

##  VMware vSphere on IBM Cloud 是否使用自動化來安裝、配置及啟動 VMware 堆疊？

否。VMware vSphere on {{site.data.keyword.cloud_notm}} 並未使用在 Cloud Foundation 及 vCenter Server 平台上找到的進階自動化。根據您訂購的內容，平台會提供選用的 VMware 授權、ESXi 伺服器，以及選擇性地提供 FortiGate 實體防火牆的 HA 配對。如果建立新的叢集，則也會佈建三個新的 VLAN：一個公用 VLAN，兩個專用 VLAN。

VMware ESXi 會自動安裝在每一部 Bare Metal Server 上，但您必須負責安裝其他任何 VMware 元件，諸如 vCenter Server 或 NSX。雖然 vSphere on {{site.data.keyword.cloud_notm}} 可確保根據所選取的 VMware 元件來訂購 VMware 相容硬體，但沒有自動化可配置及啟動 VMware 環境。您必須負責設計及架構 IBM 管理的環境。

## 如何檢視所有通知的清單？

如果要檢視完整的通知歷程，請從左導覽窗格中按一下**通知**。

## 如果我有 IBM Cloud for VMware Solutions 方面的問題該怎麼辦？

如果您需要 {{site.data.keyword.vmwaresolutions_short}} 方面的協助，請透過其中一個支援管道與 IBM 支援中心聯絡。如需相關資訊，請參閱[與 IBM 支援中心聯絡](trbl_support.html)。

### 相關鏈結

* [通知](notifications.html)
* [Cloud Foundation 實例](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 實例](../vcenter/vc_vcenterserveroverview.html)
* [存取主控台](loginmethod.html)
* [使用者帳戶及設定](useraccount.html)
