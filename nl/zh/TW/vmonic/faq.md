---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-01"

keywords: FAQ, user account, patch management

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# IBM Cloud for VMware Solutions 的一般常見問題
{: #faq}

尋找 {{site.data.keyword.vmwaresolutions_full}} 相關常見問題的回答。

## IBM Cloud for VMware Solutions 需要何種使用者帳戶？
{: #faq-user-accts}
{: faq}

* **IBM ID 帳戶**。需要此帳戶才能存取 {{site.data.keyword.vmwaresolutions_short}} 主控台。主控台是與 {{site.data.keyword.slportal}} 分開的獨立式使用者介面。如需相關資訊，請參閱[開始使用](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)。
* **{{site.data.keyword.cloud_notm}} 帳戶**。需要此帳戶才能進行佈建。您可以使用現有 **IBM ID** 或建立新的 **IBM ID**，來註冊 {{site.data.keyword.cloud_notm}} 帳戶。
* **{{site.data.keyword.cloud_notm}} 基礎架構帳戶**。此帳戶用來登入 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站，以提供一些額外功能來管理基礎架構產品及服務。您可以取得 {{site.data.keyword.cloud_notm}} 基礎架構帳戶，方法是將 **{{site.data.keyword.cloud_notm}} 帳戶**升級至計費帳戶，或將現有 {{site.data.keyword.cloud_notm}} 基礎架構帳戶鏈結至 {{site.data.keyword.cloud_notm}} 帳戶。您使用的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶必須符合特定需求。如需相關資訊，請參閱[註冊必要帳戶](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts)及 [{{site.data.keyword.cloud_notm}} 基礎架構帳戶需求](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)。

## 如何使 IBM Cloud 基礎架構認證與 IBM Cloud for VMware Solutions 主控台相關聯？
{: #faq-associate-credentials}
{: faq}

第一次訂購實例時，請遵循主控台之**設定**頁面上的指示，從 {{site.data.keyword.slportal}} 中尋找並複製 {{site.data.keyword.cloud_notm}} 基礎架構使用者名稱及 API 金鑰。第一次訂購之後，{{site.data.keyword.cloud_notm}} 基礎架構認證會儲存在 {{site.data.keyword.vmwaresolutions_short}} 主控台中。未來訂單會自動使用已儲存的認證。

## 我的 VMware 虛擬平台耗用如何計費？
{: #faq-billing}
{: faq}

實體和虛擬基礎架構的所有成本以及從實例中產生的授權會向您的 {{site.data.keyword.cloud_notm}} 帳戶收費。訂購實例時，您必須具有 {{site.data.keyword.cloud_notm}} 帳戶，並提供與該帳戶相關聯的 {{site.data.keyword.slapi_short}} 金鑰。

## vCenter Server 實例和 VMware vSphere 叢集之間有何差異？
{: #faq-vcs-cf-vss}
{: faq}

所有實例類型都提供 VMware 虛擬環境的部署選項。不過，差異在於自訂功能及自動化的範圍。

* 當您訂購 VMware vCenter Server 實例時，您會部署具有自訂運算、儲存空間及網路資源的 VMware 虛擬環境。如需已部署元件的相關資訊，請參閱 [vCenter Server 實例的技術規格](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs)。
* 當您訂購 VMware vSphere 叢集時，您會有最大的彈性來設計及建置受管理的 VMware 環境，同時納入 VMware 相容的硬體。不過，{{site.data.keyword.cloud_notm}} 不會使 VMware vSphere 叢集之選用 VMware 元件的安裝、配置及啟動自動化。
* vCenter Server 實例和 vSphere 叢集所支援的功能並不相同。如需相關資訊，請參閱[提供比較圖表](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart)。

## vCenter Server 實例包含了什麼？
{: #faq-vcs}
{: faq}

如需相關資訊，請參閱 [vCenter Server 實例的技術規格](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs)。

## vSphere 叢集包括哪些內容？
{: #faq-vss}
{: faq}

如需相關資訊，請參閱 [VMware vSphere on {{site.data.keyword.cloud_notm}} 的元件](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)。

## 雙節點 vCenter Server 實例是否為高可用性？
{: #is-a-two-node-vcenter-server-instance-highly-available}
{: faq}

建議將正式作業工作負載部署到至少有三個節點的環境。

依預設，會啟用 VMware vSphere DRS（分散式資源排程器）及 VMware HA（高可用性）。不過，來自 VMware 的最佳作法建議您將三個 NSX Controller 的每個都放置在個別節點上。

在雙節點的最小部署中，一個節點具有一個 NSX Controller，另一個節點具有兩個 NSX Controller。如果具有兩個 NSX Controller 的節點關閉，則 NSX Controller 作業會處於唯讀模式，而新的 VM（虛擬機器）或 vMotion VM 可能會遇到網路問題。

當第三個節點新增至雙節點叢集時，vCenter Server 會自動在三個節點之間重新平衡三個 NSX Controller，並建立高可用性環境。

## 我可以設定 VMware vCenter HA 配置嗎？
{: #faq-ha}
{: faq}

您可以配置 vCenter HA，但 {{site.data.keyword.vmwaresolutions_short}} 未提供配置支援。

## 叢集可以重新命名嗎？
{: #faq-rename-cluster}
{: faq}

對於新的 vCenter Server 實例，您可以設定在部署期間建立的初始叢集的名稱。當您將叢集新增至 vCenter Server 實例時，可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台上指定您想要的名稱。

## 如何管理修補程式？
{: #faq-patches}
{: faq}

IBM 提供 IBM 程式碼的持續更新，方法是隨需應變部署 IBM CloudDriver 虛擬伺服器實例 (VSI)。IBM 不對 Zerto on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}} 等附加服務提供持續更新。您必須負責取得並安裝這些更新。

對於已部署在或升級至 2.1 版或更新版本的 VMware vCenter Server 實例，新部署的 ESXi 伺服器和叢集會以 VMware 最近但未必最新的 ESXi 更新進行修補。

您必須負責處理 VMware 元件的所有其他更新，包括確保新部署的 ESXi 伺服器和叢集具有您需要的所有最近更新。
{:important}

對於在 2.0 版或更新版本上部署的實例，VMware Update Manager (VUM) 已整合至 vCenter Server。您可以配置 VUM 來下載 VMware 的 ESXi 更新。

如需相關資訊，請參閱下列資源：
* [VMware 支援](https://www.vmware.com/support.html){:external}
* [將更新套用至 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)

## 管理服務 NSX Edge 是否造成安全風險？
{: #faq-mgmt-nsx}
{: faq}

雖然管理服務的 VMware NSX Edge 位於公用子網路上，但仍提供下列安全措施，以確保不會造成安全風險：
*  已配置 NSX Edge 防火牆，只容許管理虛擬機器所起始的送出 HTTPS（TCP 埠 443）資料流量。
*  使用 SNAT（來源網址轉換），讓專用 IP 位址不顯示於專用網路以外。
*  已停用對管理服務 NSX Edge 應用裝置的遠端存取。
*  從專用網路存取管理服務 NSX Edge 的密碼已隨機化且已加密。

## 客戶管理的 NSX Edge 是否造成安全風險？
{: #faq-customer-nsx}
{: faq}

雖然客戶管理的 NSX Edge 已連接至公用 VLAN，但仍提供安全措施，以確保不會造成安全風險。以下是可用的安全測量：
*  已設定防火牆規則，只容許來自專用子網路 IP 位址範圍的送出資料流量。
*  已設定 SNAT 規則（依預設會停用），將專用子網路中的所有 IP 位址轉換為公用子網路上的單一 IP 位址。
*  已停用對客戶管理的 NSX Edge 應用裝置的遠端存取。
*  從專用網路存取客戶管理的 NSX Edge 的密碼已隨機化且已加密。

## 如何為我的實例選擇資料中心？
{: #faq-data-center}
{: faq}

實例部署具有嚴格的實體基礎架構需求，這在 {{site.data.keyword.CloudDataCents_notm}} 之間會不同。當您訂購實例時，會列出地區內的可用資料中心，而且您可以從此清單中選取您要的資料中心。

如需相關資訊，請參閱以下的 _IBM Cloud Data Center 可用性_ 小節：
* [vCenter Server 實例的需求及規劃](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [VMware vSphere on {{site.data.keyword.cloud_notm}} 的需求及規劃](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [NetApp ONTAP Select 實例的需求及規劃](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning)

## 部署實例需要花費多久的時間？
{: #faq-deploy}
{: faq}

您可以從 {{site.data.keyword.vmwaresolutions_short}} 主控台檢視實例詳細資料頁面上的部署歷程，以檢查實例部署的狀態。

##  VMware vSphere on IBM Cloud 是否使用自動化來安裝、配置及啟動 VMware 堆疊？
{: #faq-vss-automation}
{: faq}

不是，VMware vSphere on {{site.data.keyword.cloud_notm}} 未使用 vCenter Server 平台中的進階自動化。根據您訂購的內容，平台會提供選用的 VMware 授權、ESXi 伺服器，以及選擇性地提供 FortiGate 實體防火牆的 HA 配對。如果建立新的叢集，則也會佈建三個新的 VLAN：一個公用 VLAN，兩個專用 VLAN。

VMware ESXi 會自動安裝在每一部裸機伺服器上，但您必須負責安裝其他任何 VMware 元件，諸如 vCenter Server 或 NSX。雖然 vSphere on {{site.data.keyword.cloud_notm}} 可確保根據所選取的 VMware 元件來訂購 VMware 相容硬體，但沒有自動化可配置及啟動 VMware 環境。您必須負責設計及架構 IBM 管理的環境。

## 如何檢視所有通知的清單？
{: #faq-notification}
{: faq}

若要檢視完整的通知歷程，請從左導覽窗格中按一下**通知**。

## 如果我有 IBM Cloud for VMware Solutions 方面的問題該怎麼辦？
{: #faq-support}
{: faq}

如果您需要 {{site.data.keyword.vmwaresolutions_short}} 方面的協助，請透過其中一個支援管道與 IBM 支援中心聯絡。如需相關資訊，請參閱[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。


## 相關鏈結
{: #faq-related}

* [通知](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [存取主控台](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
