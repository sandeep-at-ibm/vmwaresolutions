---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購及刪除單一節點試用版 VMware vCenter Server on IBM Cloud 實例

「單一節點試用版 VMware vCenter Server on {{site.data.keyword.cloud}}」是單一承租戶代管專用雲端，提供 VMware vSphere 堆疊作為服務。雖然用戶端管理的環境通常會部署最少三個節點，但這個單一節點試用版可讓您以低廉的價格，體驗混合式雲端實作的好處。

此試用版是下列概念的最好證明：展現 IBM 在起始部署方面的進階自動化速度，以及將簡單的非正式作業工作負載移至雲端的簡易性。使用 VMware Hybrid Cloud Extension (HCX) 可讓您將內部部署資料中心網路安全地延伸至 {{site.data.keyword.CloudDataCent_notm}}，同時降低配置交互連接的網路複雜性。HCX 會將基礎網路資源擷取至公用網際網路上的通道，讓您無需重新設定虛擬機器 (VM) 的 IP，就可以順暢地雙向移動工作負載。有了 HCX，就不需要在內部部署安裝 VMware NSX，而且可與舊版 vSphere 相容。  

單一節點試用版僅用來證明概念。不要在此環境中執行正式作業工作負載。新增及移除主機和叢集、訂購其他附加程式服務，以及套用更新項目等管理功能皆不受支援。{:important}

此試用版最多可使用 90 天。完成試用後，您可以刪除此環境，然後再佈建符合您容量需求的高可用性環境。如需相關資訊，請參閱[訂購 vCenter Server with Hybridity Bundle 實例](vc_hybrid_orderinginstance.html)。

## 單一節點試用版 vCenter Server 實例的技術規格

下列元件內含在「單一節點試用版 vCenter Server」實例中：

標準化硬體配置的可用性及定價可能會根據選取以用於部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。{:note}

### Bare Metal Server

雙重 Intel Xeon Gold 5120（28 核心，2.20 GHz）處理器，含 384 GB RAM。

### 網路

訂購了下列網路元件：
*  10 Gbps 雙重公用及專用網路上行鏈路
*  三個 VLAN（虛擬 LAN）：一個公用 VLAN 和兩個專用 VLAN
*  一個具有 DLR（分散式邏輯路由器）的 VXLAN (Virtual eXtensible LAN)，以便在連接至第 2 層 (L2) 網路的本端工作負載之間，進行潛在的東西向通訊。VXLAN 是部署成一個遞送拓蹼範例，您可以加以修改、在其上進行建置，或是移除它。您也可以將其他 VXLAN 連接到 DLR 上的新邏輯介面，來新增安全區域。
*  兩個 VMware NSX Edge Services Gateway：
  * 用於出埠 HTTPS 管理資料流量的安全管理服務 VMware NSX Edge Services Gateway (ESG)，IBM 將它部署為管理網路拓蹼的一部分。IBM 管理 VM 使用此 ESG，以與跟自動化相關的特定外部 IBM 管理元件進行通訊。如需相關資訊，請參閱[將您的網路配置成使用客戶管理的 ESG](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)。

您無法存取此 ESG，因此無法使用它。如果您修改它，則可能無法從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 vCenter Server 實例的「單一節點試用版」。此外，請注意，使用防火牆或停用與外部 IBM 管理元件的 ESG 通訊，將導致 {{site.data.keyword.vmwaresolutions_short}} 變成無法使用。
{:important}
  * 用於出埠和入埠 HTTPS 工作負載資料流量的安全客戶管理 VMware NSX Edge Services Gateway，IBM 將它部署為範本，您可以修改它來提供 VPN 存取或公用存取。如需相關資訊，請參閱[客戶管理的 NSX Edge 是否造成安全風險？](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

如需在 {{site.data.keyword.cloud_notm}} 服務上部署 HCX 時所訂購之網路元件的相關資訊，請參閱 [HCX on {{site.data.keyword.cloud_notm}} 概觀](../services/hcx_considerations.html)。

### 虛擬伺服器實例

已訂購下列虛擬伺服器實例 (VSI)：

* IBM CloudBuilder 的 VSI，在完成實例部署之後會關閉它。
* 已部署並可查閱 Microsoft Windows Server VSI for Microsoft Active Directory (AD)。VSI 是作為登錄主機及 VM 之實例的 DNS。

### IBM 提供的授權及費用

「單一節點試用版 vCenter Server」實例訂單隨附下列授權。

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

「單一節點試用版 vCenter Server」實例不支援「自帶授權」。
{:note}

可以提供其他支援及服務費用。

## VMware HCX on IBM Cloud 的技術規格

vCenter Server 的「單一節點試用版」包括 HCX on {{site.data.keyword.cloud_notm}}。如需 HCX on {{site.data.keyword.cloud_notm}} 技術規格和注意事項的相關資訊，請參閱 [VMware HCX on IBM Cloud 概觀](../services/hcx_considerations.html)。

## 訂購單一節點試用版 vCenter Server 實例的需求及規劃

您務必確認下列需求並完成下列作業：
* 內部部署 HCX 實例的必要條件：
 * 需要 VMware vSphere 及 vCenter 5.5 或更新版本。
 * vSphere 環境必須具有將移轉至 {{site.data.keyword.cloud_notm}} 的 VMx 的分散式交換器。
 * 「HCX Manager 虛擬應用裝置」必須能夠部署在內部部署環境的專用網路上，且必須能夠存取公用網際網路。
* 您使用的 {{site.data.keyword.cloud_notm}} 帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 帳戶的需求](../vmonic/slaccountrequirement.html)。
*  在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[管理使用者帳戶及設定](../vmonic/useraccount.html)。
* 檢閱實例名稱需求：  
 * 只容許英數及橫線 (-) 字元。
 * 實例名稱的開頭及結尾必須是英數字元。
 * 實例名稱的長度上限為 10 個字元。
 * 實例名稱在您的帳戶中必須是唯一的。
* 檢閱符合實體基礎架構需求的 {{site.data.keyword.CloudDataCents_notm}}。如需相關資訊，請參閱 [vCenter Server with Hybridity Bundle 實例的需求及規劃](../vcenter/vc_hybrid_planning.html#ibm-cloud-data-center-availability)中的 *{{site.data.keyword.CloudDataCent_notm}} 可用性* 小節。

## 單一節點試用版 vCenter Server 實例的訂購程序

1. 在**單一節點試用版 VMware vCenter Server on {{site.data.keyword.cloud_notm}}** 頁面上，按一下 **vCenter Server** 卡片，然後按一下**繼續**。
2. 在**單一節點試用版 VMware vCenter Server** 頁面上，完成要求 {{site.data.keyword.cloud_notm}} 基礎架構帳戶的步驟，或提供您現有的**使用者名稱**和 **API 金鑰**，然後按一下**擷取**。

 如果 API 金鑰已存在，則會隱藏本節。
 {:note}
3. 輸入實例名稱。
4. 選取 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。  

 已預先選取 {{site.data.keyword.CloudDataCent_notm}}。必要的話，可選取不同的 {{site.data.keyword.CloudDataCent_notm}} 位置。{:note}
5. 在**訂單摘要**窗格上，先驗證實例配置，再下訂單。
   1. 檢閱實例的設定。
   2. 檢閱預估實例成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
   3. 按一下適用於您的訂單的條款鏈結，並先確認您同意這些條款，再訂購實例。
   4. 按一下**佈建**。

### 結果

自動啟動實例的部署作業，並且會訂購內部部署 HCX on {{site.data.keyword.cloud_notm}} 服務啟動金鑰。

#### HCX on IBM Cloud 的部署處理程序

自動部署 HCX on {{site.data.keyword.cloud_notm}}。下列步驟是由 {{site.data.keyword.vmwaresolutions_short}} 自動化處理程序完成：
1. 從 {{site.data.keyword.cloud_notm}} 基礎架構訂購三個 HCX 的子網路：
   * 兩個專用可攜式子網路，以進行 HCX 管理。
   * 一個公用可攜式子網路，以使用 VMware 啟動及維護。這個子網路也用於 HCX 交互連接。

   為 HCX 訂購的子網路中的 IP 位址，是要由 VMware on {{site.data.keyword.cloud_notm}} 自動化進行管理。這些 IP 位址無法指派給您建立的 VMware 資源（例如 VM 及 NSX Edge）。如果您需要 VMware 構件的其他 IP 位址，則必須從 {{site.data.keyword.cloud_notm}} 訂購自己的子網路。{:important}
3. 為 HCX 建立三個資源儲存區及 VM 資料夾，而 HCX 交互連接、本端 HCX 元件及遠端 HCX 元件需要這些資源儲存區及 VM 資料夾。
4. 針對 HCX 管理資料流量，部署及配置一組 VMware NSX Edge Services Gateway (ESG)：
   * 使用訂購的子網路來配置公用及專用上行鏈路介面。
   * 將 ESG 配置為一組啟用「高可用性 (HA)」的額外大型邊緣應用裝置。
   * 配置防火牆規則及網址轉換 (NAT) 規則，以容許與 HCX Manager 之間往返的入埠及出埠 HTTPS 資料流量。
   * 配置負載平衡器規則及資源儲存區。這些規則是資源儲存區，用來將 HCX 相關入埠資料流量轉遞至 HCX Manager、vCenter Server 及 Platform Services Controller (PSC) 的適當虛擬應用裝置。
   * 套用 SSL 憑證，以加密來自 ESG 的 HCX 相關入埠 HTTPS 資料流量。

   HCX 管理邊緣專用於內部部署 HCX 元件與雲端 HCX 元件之間的 HCX 管理資料流量。請不要修改 HCX 管理邊緣，或對 HCX 網路延伸使用它。請改為建立網路延伸的個別邊緣。此外，使用防火牆或停用與專用 IBM 管理元件或公用網際網路的 HCX 管理邊緣通訊，可能會對 HCX 功能造成負面影響。{:important}

5. 部署、啟動及配置 HCX Manager on {{site.data.keyword.cloud_notm}}：
   * 向 vCenter Server 登錄 HCX Manager。
   * 配置 HCX Manager、vCenter Server、PSC 及 NSX Manager。
   * 配置 HCX 機群。
   * 配置本端及遠端 HCX 部署容器。
6. 向 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的 DNS 伺服器登錄 HCX Manager 的主機名稱及 IP 位址。

#### 檢視實例詳細資料

您可以檢視實例詳細資料，以查看部署的狀態。如需檢視實例詳細資料的相關資訊，請參閱：

* [檢視 vCenter Server 實例](vc_viewinginstances.html)
* [檢視內部部署 VMware HCX on IBM Cloud 實例](../services/standalone_viewingserviceinstances.html)

順利部署實例之後，此主題的*技術規格* 區段中所說明的元件即會安裝在 VMware 虛擬平台上，而內部部署 HCX on {{site.data.keyword.cloud_notm}} 服務啟動金鑰會出現在內部部署 HCX on {{site.data.keyword.cloud_notm}} 詳細資料頁面上。

實例的狀態會變更為**備妥使用**，且您會收到電子郵件通知。

### 下一步

安裝內部部署 HCX Enterprise Manager，並配置與 HCX on {{site.data.keyword.cloud_notm}} 實例的連線。

1. 在**部署的實例**頁面中，找出內部部署啟動金鑰。
  1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
  2. 在 **vCenter Server 實例**表格中，檢閱**類型**直欄，以找出單一節點試用版實例，並記下實例名稱。
  3. 捲動至**內部部署 HCX 實例**表格，檢閱**名稱**直欄，以找出與單一節點實例同名的實例。實例名稱後面會附加 *-OnPrem*。
  4. 記下**啟動金鑰**欄位中的金鑰。
2. 從 HCX on {{site.data.keyword.cloud_notm}} HCX Manager 主控台取得內部部署 HCA Enterprise Manager Open Virtual Appliance (OVA)。
  1. 連接至「HCX Cloud 主控台」。
    1. 在 **vCenter Server 實例**表格中，按一下單一節點試用版實例，以檢視實例詳細資料。
    2. 在**存取資訊**之下，尋找並記下 vCenter 認證。
    3. 從左導覽窗格中，按一下**服務**。
    4. 在**服務**頁面上，按一下 **HCX on IBM Cloud**。
    5. 在 **HCX on IBM Cloud** 詳細資料頁面中，尋找並記下 **HCX Cloud IP**。
    6. 請確定您已連接至 VPN，以存取 {{site.data.keyword.cloud_notm}} 專用網路。
    7. 按一下**檢視 HCX Cloud 主控台**。
  2. 在 **HCX Cloud 主控台**中，完成下列步驟：
      1. 按一下**管理**標籤。
      2. 在**系統更新**標籤上，按一下**要求下載鏈結**。
      3. 按一下**複製鏈結**，然後使用此鏈結將 HCX Enterprise Client 下載至內部部署環境，而且可以存取您的內部部署 vSphere 環境。
3. 在 VMware vSphere Web Client 中，將 HCX Enterprise Client 當成 HCX Manager 虛擬應用裝置 (HCX Manager) 部署至內部部署環境。如需相關資訊，請參閱[安裝 HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html)。

    您必須在專用網路上部署內部部署 HCX Manager，並容許它存取公用網路。您可以使用 NSX Edge、Vyatta 或類似閘道，容許透過網際網路存取內部部署 HCX Manager。如果用於專用網路存取及公用網路存取的閘道不同，則建議您使用預設閘道來容許公用網路存取及內部部署 **HCX Manager 管理主控台**，以建立進行專用網路存取的靜態路徑。  
    {:note}
4. 使用在步驟 1 所記下的內部部署啟動鍵，來啟動內部部署 HCX Enterprise Manager VM。
  1. 使用部署 OVA 時指定的認證，登入您的內部部署 HCX Enterprise Manager VM。
  2. 系統提示時，輸入啟動鍵。

  如需相關資訊，請參閱 [HCX 啟動及起始配置](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html)。
  {:note}
5. 自簽 SSL 憑證由 HCX on {{site.data.keyword.cloud_notm}} 服務產生。您必須完成下列步驟，將憑證匯入至內部部署 HCX Manager：
    1. 在內部部署 **HCX Manager 管理主控台**中，按一下**管理**標籤。
    2. 從左導覽窗格中，按一下**授信 CA 憑證**，然後按一下右側的**匯入**。
    3. 按一下 **URL**，然後輸入您要套用之憑證的 URL（即 **HCX Cloud IP** (``https://<cloud-side public IP>``)），而您可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台的 HCX on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到它。
    4. 按一下**套用**。
6. 繼續起始配置並建置交互連接。如需相關資訊，請參閱[安裝及配置 VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html)。
7. 將 VMware HCX 中的網路從內部部署延伸到 {{site.data.keyword.cloud_notm}}。如需相關資訊，請參閱[透過 VMware HCX 延伸網路](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g)。
8. 在內部部署與 {{site.data.keyword.cloud_notm}} 之間移轉 VM。如需相關資訊，請參閱[透過 VMware HCX 移轉虛擬機器](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA)。

您只能從 {{site.data.keyword.vmwaresolutions_short}} 主控台，而不能從 {{site.data.keyword.slportal}} 或透過主控台以外的任何其他方法，來管理在 {{site.data.keyword.cloud_notm}} 帳戶中建立的 {{site.data.keyword.vmwaresolutions_short}} 基礎架構元件。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台之外變更這些元件，這些變更不會與主控台同步化，而且會使您的環境不穩定。{:important}

## 單一節點試用版 vCenter Server 實例的刪除程序

若要釋出您在「單一節點試用版 vCenter Server」實例中訂購的元件，請刪除該實例。

如需相關資訊，請參閱[刪除 vCenter Server 實例](vc_deletinginstance.html)。

### 相關鏈結

* [註冊 {{site.data.keyword.cloud_notm}} 帳戶](../vmonic/signing_softlayer_account.html)
* [HCX 術語名詞解釋](../services/hcx_glossary.html)
* [VMware Hybrid Cloud Extension 文件](https://hcx.vmware.com/#/vm-documentation)
* [取得 HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
* [訂購 vCenter Server with Hybridity Bundle 實例](vc_hybrid_orderinginstance.html)
