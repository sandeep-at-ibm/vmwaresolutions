---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購及刪除單一節點試用版 VMware vCenter Server on IBM Cloud 實例

「單一節點試用版 VMware vCenter Server on {{site.data.keyword.cloud}}」是單一承租戶代管專用雲端，提供 VMware vSphere 堆疊作為服務。雖然用戶端管理的環境通常會部署最少三個節點，但這個單一節點試用版可讓您以低廉的價格，體驗混合式雲端實作的好處。

此試用版是下列概念的最好證明：展現 IBM 在起始部署方面的進階自動化速度，以及將簡單的非正式作業工作負載移至雲端的簡易性。使用 VMware Hybrid Cloud Extension (HCX) 可讓您將內部部署資料中心網路安全地延伸至 {{site.data.keyword.CloudDataCent_notm}}，同時降低配置交互連接的網路複雜性。HCX 會將基礎網路資源擷取至公用網際網路上的通道，讓您無需重新設定虛擬機器 (VM) 的 IP，就可以順暢地雙向移動工作負載。有了 HCX，就不需要在內部部署安裝 VMware NSX，而且可與舊版 vSphere 相容。  

單一節點試用版僅用來證明概念。不要在此環境中執行正式作業工作負載。新增及移除主機和叢集、訂購其他附加程式服務，以及套用更新項目等管理功能皆不受支援。{:important}

此試用版最多可使用 90 天。完成試用後，您可以刪除此環境，然後再佈建符合您容量需求的高可用性環境。

如需架構設計的相關資訊，請參閱[單一節點試用版 vCenter Server on IBM Cloud 的 HCX on IBM Cloud 架構設計](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)。

## 單一節點試用版 vCenter Server 實例的技術規格

下列元件內含在「單一節點試用版 vCenter Server」實例中：

標準化硬體配置的可用性及定價可能會根據選取以用於部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。{:note}

### Bare Metal Server

雙重 Intel Xeon Gold 5120（28 核心，2.20 GHz）處理器，含 384 GB RAM。

### 單一節點試用版 vCenter Server 實例的網路規格

訂購了下列網路元件：
*  10 Gbps 雙重公用及專用網路上行鏈路
*  三個 VLAN（虛擬 LAN）：一個公用 VLAN 和兩個專用 VLAN
*  一個具有 DLR（分散式邏輯路由器）的 VXLAN (Virtual eXtensible LAN)，以便在連接至第 2 層 (L2) 網路的本端工作負載之間，進行潛在的東西向通訊。VXLAN 是部署成一個遞送拓蹼範例，您可以加以修改、在其上進行建置，或是移除它。您也可以將其他 VXLAN 連接到 DLR 上的新邏輯介面，來新增安全區域。
*  兩個 VMware NSX Edge Services Gateway：
  * 用於出埠 HTTPS 管理資料流量的安全管理服務 VMware NSX Edge Services Gateway (ESG)，IBM 將它部署為管理網路拓蹼的一部分。IBM 管理 VM 使用此 ESG，以與跟自動化相關的特定外部 IBM 管理元件進行通訊。

您無法存取此 ESG，因此無法使用它。如果您修改它，則可能無法從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 vCenter Server 實例的「單一節點試用版」。此外，請注意，使用防火牆或停用與外部 IBM 管理元件的 ESG 通訊，將導致 {{site.data.keyword.vmwaresolutions_short}} 變成無法使用。
{:important}
  * 用於出埠和入埠 HTTPS 工作負載資料流量的安全客戶管理 VMware NSX Edge Services Gateway，IBM 將它部署為範本，您可以修改它來提供 VPN 存取或公用存取。

### 虛擬伺服器實例

已訂購下列虛擬伺服器實例 (VSI)：

* IBM CloudBuilder 的 VSI，在完成實例部署之後會取消它。
* 已部署並可查閱 Microsoft Windows Server VSI for Microsoft Active Directory (AD)。VSI 是作為登錄主機及 VM 之實例的 DNS。

### IBM 提供的授權及費用

「單一節點試用版 vCenter Server」實例訂單隨附下列授權。

* VMware vSphere Enterprise Plus 6.5
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

「單一節點試用版 vCenter Server」實例不支援「自帶授權」。
{:note}

## VMware HCX on IBM Cloud 的技術規格

vCenter Server 的「單一節點試用版」包括 HCX on {{site.data.keyword.cloud_notm}}。下列元件已訂購並包括在 HCX on {{site.data.keyword.cloud_notm}} 服務中。

內部部署 HCX 實例只包括授權及啟動。
{:note}

### 用於 HCX 管理的 VMware NSX Edge Services Gateway 主動/被動配對

* CPU：6 個 vCPU
* RAM：8 GB
* 磁碟：3 GB VMDK

### HCX 管理應用裝置 - 虛擬機器

* CPU：4 個 vCPU
* RAM：12 GB
* 磁碟：60 GB VMDK

視需要，在配置進行 L2 連線功能、WAN 最佳化及閘道連線期間，會部署其他的 HCX 應用裝置。

### HCX on IBM Cloud 服務的網路規格

* 一個具有 16 個 IP 位址的公用可攜式子網路
* 兩個具有 64 個 IP 位址的專用可攜式子網路
* 來自專用可攜式 vMotion 子網路的八個 IP 位址

## 訂購單一節點試用版 vCenter Server 實例的需求及規劃

您務必確認下列需求並完成下列作業：
* 內部部署 HCX 實例的必要條件：
 * 需要 VMware vSphere 及 vCenter 5.5 或更新版本。
 * vSphere 環境必須具有將移轉至 {{site.data.keyword.cloud_notm}} 的 VMx 的分散式交換器。
 * 「HCX Manager 虛擬應用裝置」必須能夠部署在內部部署環境的專用網路上，且必須能夠存取公用網際網路。
 * 若要使用 {{site.data.keyword.vmwaresolutions_short}} 來訂購實例，您必須具有 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶。實例中訂購的元件費用會向該 {{site.data.keyword.cloud_notm}}帳戶收費。
 *  在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**設定**。
 * 檢閱實例名稱需求：
    * 只容許英數及橫線 (-) 字元。
    * 實例名稱的開頭及結尾必須是英數字元。
    * 實例名稱的長度上限為 10 個字元。
    * 實例名稱在您的帳戶中必須是唯一的。

## 單一節點試用版 vCenter Server 實例的訂購程序

1. 在**單一節點試用版 VMware vCenter Server on {{site.data.keyword.cloud_notm}}** 頁面上，按一下**繼續**。
2. 在**單一節點試用版 VMware vCenter Server** 頁面上，完成要求 {{site.data.keyword.cloud_notm}} 基礎架構帳戶的步驟，或提供您現有的**使用者名稱**和 **API 金鑰**，然後按一下**擷取**。

 如果 API 金鑰已存在，則會隱藏本節。
 {:note}
3. 輸入實例名稱。
4. 選取 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。  

 依預設，會預先選取 DAL09 {{site.data.keyword.CloudDataCent_notm}}。必要的話，可選取不同的 {{site.data.keyword.CloudDataCent_notm}} 位置。{:note}
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
   * 配置負載平衡器規則及資源儲存區。這些規則及資源儲存區用來將 HCX 相關入埠資料流量轉遞至 HCX Manager 及 vCenter Server（具有內嵌的 Platform Services Controller）的適當虛擬應用裝置。
   * 套用 SSL 憑證，以加密來自 ESG 的 HCX 相關入埠 HTTPS 資料流量。

   HCX 管理邊緣專用於內部部署 HCX 元件與雲端 HCX 元件之間的 HCX 管理資料流量。請不要修改 HCX 管理邊緣，或對 HCX 網路延伸使用它。請改為建立網路延伸的個別邊緣。此外，使用防火牆或停用與專用 IBM 管理元件或公用網際網路的 HCX 管理邊緣通訊，可能會對 HCX 功能造成負面影響。{:important}

5. 部署、啟動及配置 HCX Manager on {{site.data.keyword.cloud_notm}}：
   * 向 vCenter Server 登錄 HCX Manager。
   * 配置 HCX Manager、vCenter Server（具有內嵌的 Platform Services Controller）及 NSX Manager。
   * 配置 HCX 機群。
   * 配置本端及遠端 HCX 部署容器。
6. 向 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的 DNS 伺服器登錄 HCX Manager 的主機名稱及 IP 位址。

#### 檢視實例詳細資料

您可以檢視實例詳細資料，以查看部署的狀態。從左導覽窗格中，按一下**已部署的實例**，然後找出 **vCenter Server 實例**或**內部部署 HCX 實例**表格，以檢視您所訂購實例的相關資訊。

順利部署實例之後，此主題的*技術規格* 小節中所說明的元件即會安裝在 VMware 虛擬平台上，而內部部署 HCX on {{site.data.keyword.cloud_notm}} 服務啟動金鑰會列在**內部部署 HCX 實例**表格中。

實例的狀態會變更為**備妥使用**，且您會收到電子郵件通知。

### 下一步

安裝內部部署 HCX Enterprise Manager，並配置與 HCX on {{site.data.keyword.cloud_notm}} 實例的連線。

1. 在**部署的實例**頁面中，找出內部部署啟動金鑰。
  1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
  2. 在 **vCenter Server 實例**表格中，檢閱**類型**直欄，以找出 vCenter Server 單一節點試用版實例，並記下實例名稱。
  3. 捲動至**內部部署 HCX 實例**表格，檢閱**名稱**直欄，以找出與使用 *-OnPrem* 字尾所訂購之單一節點實例同名的實例。
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

當您刪除「單一節點試用版 vCenter Server」實例時，會循序釋出下列元件：

1. 所有已部署的服務
3. VMware 產品授權
4. ESXi 伺服器
5. 子網路
6. VLAN

由於資源相依關係，當您刪除實例時，不會立即釋放實例中的元件。例如，在 {{site.data.keyword.cloud_notm}} 基礎架構完整收回 ESXi 伺服器（發生於 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束時）之前，無法刪除子網路及 VLAN。當 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束（通常是 30 天），就會刪除子網路和 VLAN，並且完成實例刪除。

將針對已刪除的實例，向您收取到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。
{:note}

請完成下列步驟，以刪除「單一節點試用版 vCenter Server」實例：

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，尋找要刪除的實例。
3. 在**動作**直欄中，按一下「刪除」圖示。
   實例的狀態會變更為**刪除中**。順利刪除實例後，會釋出該實例的元件，且該實例的狀態會變更為**已刪除**。
4. 如果您要從 {{site.data.keyword.vmwaresolutions_short}} 主控台移除實例記錄，請完成下列步驟：
   1. 在**動作**直欄中，再按一次「刪除」圖示。
   2. 在**刪除實例**視窗中，按一下**確定**。

### 相關鏈結

* [單一節點試用版 vCenter Server on IBM Cloud 的 HCX on IBM Cloud 架構設計](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)
* [VMware Hybrid Cloud Extension 文件](https://hcx.vmware.com/#/vm-documentation)
* [取得 HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
