---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server NSX-T order instance, order vCenter Server NSX-T, order NSX-T

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購 vCenter Server with NSX-T 實例
{: #vc_nsx-t_orderinginstance}

若要部署具有彈性且可自訂的 VMWare 虛擬化平台以符合您的工作負載需求，請訂購 VMware vCenter Server with NSX-T 實例。

## vCenter Server with NSX-T 的需求
{: #vc_nsx-t_orderinginstance-req}

請確定您已完成下列作業：
* 您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[管理使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。
* 您已檢閱 [vCenter Server 實例的需求及規劃](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)中的資訊。
* 您已檢閱實例及網域名稱格式。網域名稱及子網域標籤已用來產生實例的使用者名稱及伺服器名稱。

|名稱 |值格式            |
|:------------|:------------ |
|網域名稱    | `<root_domain>` |  
|vCenter Server 登入使用者名稱  | `<user_id>@<root_domain>`（Microsoft Active Directory 使用者）或 `administrator@vsphere.local` |
|vCenter Server（具有內嵌的 PSC）FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`。長度上限為 50 個字元。|
|單一登入 (SSO) 站台名稱| `<subdomain_label>` |
|完整的 ESXi 伺服器名稱| `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中 `<n>` 是 ESXi 伺服器序列。長度上限為 50 個字元。|
{: caption="表 1. 實例及網域名稱的值格式" caption-side="top"}

請不要修改在訂購或部署實例期間設定的任何值。這樣做會讓您的實例無法使用。例如，如果公用網路關閉、伺服器和虛擬伺服器實例 (VSI) 在佈建進行中移到 Vyatta 之後，或者 IBM CloudBuilder VSI 停止或遭到刪除。
{:important}

## 系統設定
{: #vc_nsx-t_orderinginstance-sys-settings}

訂購 vCenter Server 實例時，您必須指定下列系統設定。

### 實例名稱
{: #vc_nsx-t_orderinginstance-inst-name}

實例名稱必須滿足下列需求：
* 只容許英數及橫線 (-) 字元。
* 實例名稱的開頭必須是英文字母，而且結尾必須是英數字元。
* 實例名稱的長度上限為 10 個字元。
* 實例名稱在您的帳戶中必須是唯一的。

### VMware vSphere 授權
{: ##vc_nsx-t_orderinginstance-vsphere-license}

依預設，已選取 vSphere Enterprise Plus 6.7u1 授權。

### 主要或次要
{: #vc_nsx-t_orderinginstance-primary-secondary}

選取要訂購新的主要實例，還是要為現有的主要實例訂購次要實例。

## 授權設定
{: #vc_nsx-t_orderinginstance-licensing-settings}

在實例中，指定下列 VMware 元件的授權選項：
* vCenter Server 6.5
* vSphere Enterprise Plus 6.7
* NSX-T 2.4（Base、Advanced 或 Enterprise 版本）

對於「事業夥伴」使用者，包括 vCenter Server 授權（Standard 版本）、vSphere 授權（Enterprise Plus 版本）及 NSX 授權，並可代表您購買。不過，您必須指定 NSX 授權的版本。

對於非「事業夥伴」使用者，您可以選取**購買隨附**以將 IBM 提供的 VMware 授權用於這些元件，也可以選取**我將提供**並輸入自己的授權碼以「自帶授權 (BYOL)」。

### 授權注意事項
{: #vc_nsx-t_orderinginstance-licensing-notes}

* 需要最少有 8 個 CPU 的授權，這是針對 4 部伺服器，而每部伺服器都有 2 個 CPU。每個 VMware 元件的授權選項適用於基礎實例，以及之後新增至該實例的任何 ESXi 伺服器。請確保您的授權支援基礎架構中的未來容量擴充。
* 使用者介面上會指出最低授權版本。如果支援不同的元件版本，您可以選取您想要的版本。您必須負責確保所提供的授權碼對於每一個選取的 VMware 元件都是正確的。
* 對於 vSphere，會在訂購時產生授權費用，但授權費用接著會記入您的帳戶中。
* 實例部署完成之後，您可以使用 VMware vSphere Web Client 來變更所提供的任何授權。
* 您為其提供授權之 VMware 元件的支援是由 VMware 所提供，而不是由「IBM 支援中心」所提供。

## Bare Metal Server 設定
{: #vc_nsx-t_orderinginstance-bare-metal-settings}

「裸機」設定是根據您選取的資料中心，以及「裸機伺服器」配置。

### 資料中心位置
{: #vc_nsx-t_orderinginstance-dc-location}

選取要在其中管理實例的 {{site.data.keyword.CloudDataCent_notm}}。

### Skylake
{: #vc_nsx-t_orderinginstance-skylake}

當您選取 **Skylake** 時，可以根據需求來為 Bare Metal Server 選擇 CPU 與 RAM 組合。

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon Silver 4110 處理器 / 總計 16 核心，2.1 GHz| 128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，2.2 GHz| 128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz| 128 GB、192 GB、384 GB、768 GB、1.5 TB |
{: caption="表 2. Skylake {{site.data.keyword.baremetal_short}} 的選項" caption-side="top"}

### Broadwell
{: #vc_nsx-t_orderinginstance-broadwell}

當您選取 **Broadwell** 時，可以根據需求來為 Bare Metal Server 選擇 CPU 與 RAM 組合。

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|四重 Intel Xeon E7-4820 v4 / 總計 40 核心，2.0 GHz |128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
|四重 Intel Xeon E7-4850 v4 / 總計 64 核心，2.1 GHz |128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
{: caption="表 3. Broadwell {{site.data.keyword.baremetal_short}} 的選項" caption-side="top"}

### Bare Metal Server 數目
{: #vc_nsx-t_orderinginstance-bare-metal-number}

* 您訂購的所有伺服器都有相同的配置。
* 如果規劃使用 vSAN 儲存空間，您可以訂購 4 到 20 部伺服器。
* 如果規劃使用 NFS 儲存空間，您可以訂購 2 到 20 部伺服器。不過，對於正式作業工作負載，建議至少 3 部伺服器。如需相關資訊，請參閱[雙節點 vCenter Server 實例是否為高可用性？](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)。

## 儲存空間設定
{: #vc_nsx-t_orderinginstance-storage-settings}

儲存空間設定是根據您選取的 Bare Metal Server 配置及儲存空間類型而定。

對於已部署的實例，您可以將 NFS 儲存空間共用新增至現有 NFS 或 vSAN 叢集。如需相關資訊，請參閱[擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances)中的*將 NFS 儲存空間新增至 vCenter Server 實例* 小節。
{:note}

### vSAN 儲存空間
{: #vc_nsx-t_orderinginstance-vsan-storage}

vSAN 僅適用於 **Skylake** 或 **Broadwell** Bare Metal 配置。請指定下列 vSAN 選項：
* **vSAN 容量磁碟的磁碟類型及大小**：選取所需容量磁碟的選項。
* **vSAN 容量磁碟數目**：指定您要新增的容量磁碟數目。
* 如果您要新增超過所限制的 10 個容量磁碟，請勾選**高效能 Intel Optane** 方框。這個選項提供 2 個額外容量磁碟機槽來放置共 12 個容量磁碟，並且適用於需要較少延遲且較高 IOPS 傳輸量的工作負載。

  **高效能 Intel Optane** 選項僅適用於 Skylake CPU 型號。
  {:note}

* 檢閱 **vSAN 快取磁碟的磁碟類型**及 **vSAN 快取磁碟數目**值。這些值取決於您是否已勾選**高效能 Intel Optane** 方框。
* **vSAN 授權**：選取**購買隨附**以將 IBM 提供的 VMware 授權用於 vSAN 元件，也可以選取**我將提供**並輸入自己的授權碼以「自帶授權 (BYOL)」。

### NFS 儲存空間
{: #vc_nsx-t_orderinginstance-nfs-storage}

當您選取 **NFS 儲存空間**時，可以為所有共用使用相同設定的實例新增檔案層次共用儲存空間，也可以為每一個檔案共用指定不同的配置設定。請指定下列 NFS 選項：

檔案共用數目必須在 1 到 32 的範圍內。
{:note}

* **個別配置共用**：選取以為每一個檔案共用指定不同的配置設定。
* **共用數目**：當您使用每個檔案共用的相同配置設定時，請指定您要新增之 NFS 共用儲存空間的檔案共用數目。
* **效能**：根據您的工作負載需求，選取每 GB 的 IOPS（每秒輸入/輸出作業數）。
* **大小 (GB)**：選取符合共用儲存空間需求的容量。
* **新增共用儲存空間**：選取以新增要使用不同配置設定的個別檔案共用。

效能層次詳細資料：

|選項          |詳細資料     |
|:------------- |:------------- |
|0.25 IOPS/GB |這個選項是為未經常使用的工作負載而設計。應用的範例包括：加密配置檔資料、管理具有舊版資料的大型資料庫，或是作為備份之虛擬記憶體系統的虛擬磁碟映像檔。|
|2 IOPS/GB |這個選項是為大部分一般工作負載而設計。應用的範例包括：管理小型資料庫、備份 Web 應用程式，或是 Hypervisor 用的虛擬機器磁碟映像檔。|
|4 IOPS/GB |這個選項是為一次擁有高百分比作用中資料的高密度工作負載而設計。應用的範例包括：交易式資料庫。|
|10 IOPS/GB |這個選項是為要求最嚴苛的工作負載類型而設計，例如分析。應用的範例包括：高交易量資料庫，以及其他對效能敏感的資料庫。此效能層次限制為每個檔案共用的容量上限為 4 TB。|
{: caption="表 4. NFS 效能層次選項" caption-side="top"}

## 網路介面設定
{: #vc_nsx-t_orderinginstance-network-interface-settings}

訂購 vCenter Server 實例時，您必須指定下列網路介面設定。

### 主機名稱字首
{: #vc_nsx-t_orderinginstance-host-name-prefix}

主機名稱字首必須滿足下列需求：
*  只容許英數及橫線 (-) 字元。
*  主機名稱字首的開頭及結尾必須是英數字元。
*  主機名稱字首的長度上限為 10 個字元。

### 子網域標籤
{: #vc_nsx-t_orderinginstance-subdomain-label}

子網域標籤必須滿足下列需求：
*  只容許英數及橫線 (-) 字元。
*  子網域標籤的開頭必須是英文字母，而且結尾必須是英數字元。
*  子網域標籤的長度上限為 10 個字元。

### 網域名稱
{: #vc_nsx-t_orderinginstance-domain-name}

根網域名稱必須滿足下列需求：
* 網域名稱必須包含兩個以上以句點 (.) 區隔的字串
* 第一個字串的開頭必須是英文字母，而且結尾必須是英數字元。
* 除了最後一個字串以外，所有字串都只能包含英數字元和橫線 (-) 字元。
* 最後一個字串只能包含英文字母。
* 最後一個字串的長度範圍必須在 2 到 24 個字元之間。

主機和 VM 的「完整網域名稱 (FQDN)」長度上限為 50 個字元。網域名稱必須在這個長度上限以內。
{:note}

### 公用或專用網路
{: #vc_nsx-t_orderinginstance-public-private-network}

網路介面卡 (NIC) 啟用設定是根據您選取**公用及專用網路**或**僅限專用網路**而定。

### VLAN
{: #vc_nsx-t_orderinginstance-vlans}

網路設定是根據您選取**訂購新的 VLAN** 或**選取現有的 VLAN** 而定。

您的實例訂單需要一個公用 VLAN 及兩個專用 VLAN。兩個專用 VLAN 成為每部 Bare Metal Server 的主幹。

#### 訂購新的 VLAN
{: #vc_nsx-t_orderinginstance-new-vlans}

選取訂購一個新的公用 VLAN 和兩個新的專用 VLAN。

#### 選取現有的 VLAN
{: #vc_nsx-t_orderinginstance-existing-vlans}

視您選取的 {{site.data.keyword.CloudDataCent_notm}} 而定，可能會提供現有的公用和專用 VLAN。

當您選擇重複使用現有的公用及專用 VLAN 時，請指定 VLAN 及子網路：
* **公用 VLAN** 適用於公用網路存取。
* **專用 VLAN** 適用於 {{site.data.keyword.cloud_notm}} 內資料中心與服務之間的連線功能。
* **次要專用 VLAN** 適用於 VMware 特性（例如 vSAN）。
* **主要子網路**已指派給實體主機，以進行公用網路存取。
* **主要專用子網路**已指派給實體主機，以處理管理資料流量。

確保所選取 VLAN 上的防火牆配置未封鎖管理資料流量。也請確保您選取的所有 VLAN 都在相同的 Pod 中。無法在混合 Pod VLAN 上佈建 ESXi 伺服器。
{:important}

### DNS 配置
{: #vc_nsx-t_orderinginstance-dns-config}

選取實例的「網域名稱系統 (DNS)」配置：

* **適用於 Active Directory/DNS 的單一公用 Windows VSI**：適用於 Microsoft Active Directory (AD) 的單一 Microsoft Windows Server VSI 充當登錄主機及 VM 之實例的 DNS，已部署並可查閱。依預設，已對 1.9 版以及更新版本的實例部署這個選項。
* **管理叢集上有兩部高可用性的專用 Windows Server VM**：部署兩部 Microsoft Windows VM，協助加強安全及穩健性。

如果您將實例配置為使用兩部 Microsoft Windows VM，則必須提供兩份 Microsoft Windows Server 2016 標準版授權。
{:important}

每一份授權都只能指派給一部單一實體伺服器，且最多涵蓋兩個實體處理器。以一份 Standard 版本授權而言，每部雙處理器伺服器都可以執行兩部虛擬化 Microsoft Windows VM。因此，必須有兩份授權，因為兩部 Microsoft Windows VM 部署在兩部不同的主機中。

您有 30 天的時間可啟動 VM。

如需訂購 Windows Server 2016 授權的相關資訊，請參閱[開始使用 Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:external}。

## 訂單摘要
{: #vc_nsx-t_orderinginstance-order-summary}

根據您選取的配置，預估成本會立即產生並顯示在**訂單摘要**右窗格中。按一下**定價詳細資料**，以產生具有 {{site.data.keyword.vmwaresolutions_short}} 資源文件摘要的 PDF 文件。

您也可以按一下**新增至預估**，將佈建的資源新增至 {{site.data.keyword.cloud_notm}} 預估工具。這適用於您想要預估所選取 {{site.data.keyword.vmwaresolutions_short}} 資源與可能考慮購買之其他 {{site.data.keyword.cloud_notm}} 資源的成本時。

## 訂購 vCenter Server with NSX-T 實例的程序
{: #vc_nsx-t_orderinginstance-procedure}

1. 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格中的 **VMware** 圖示，然後按一下 **VMware Services** 區段中的 **VMware vCenter Server on IBM Cloud** 卡。
2. 在 **VMware vCenter Server on IBM Cloud** 頁面上，按一下 **vCenter Server** 卡片，然後按一下**建立**。
3. 在 **vCenter Server** 頁面上，輸入實例名稱。
4. 選取實例類型：
   * 按一下**主要實例**，以在環境中部署單一實例，或是部署多站台拓蹼中的第一個實例。
   * 按一下**次要實例**，以連接該實例與環境中的現有（主要）實例以獲得高可用性，然後完成下列步驟：
     1. 選取您要與次要實例連接的主要實例。
     2. 對於主要實例 2.8 版或更新版本，輸入主要實例的 vCenter Server 管理者密碼。
     3. 對於主要實例 2.5、2.6 或 2.7 版，輸入主要實例的 PSC 管理者密碼。
     4. 對於主要實例 2.4 版或更早版本，驗證主要實例 PSC 管理者密碼的預先填入值正確無誤。
6. 完成實例元件的授權設定。
   *  若要使用 IBM 提供的授權，請選取**購買隨附**，然後選取授權版本（必要的話）。
   *  若要使用您自己的授權，請選取**我將提供**，然後輸入授權碼。
7. 完成 Bare Metal Server 設定。
    1. 選取 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。
    2. 選取 Bare Metal Server 配置，然後指定 CPU 型號及 RAM 大小。
    3. 指定 {{site.data.keyword.baremetal_short}} 數目。如果您打算使用 vSAN 作為儲存空間解決方案，則至少需要 4 部 {{site.data.keyword.baremetal_short}}。  
8. 完成儲存空間配置。
  * 如果您選取 **vSAN 儲存空間**，請指定容量及快取磁碟的磁碟類型、磁碟數目以及「vSAN 授權」版本。如果您要更多儲存空間，請勾選**高效能 Intel Optane** 方框。
  * 如果您選取 **NFS 儲存空間**，而且要對所有檔案共用新增及配置相同的設定，請指定**共用數目**、**效能**及**大小 (GB)**。
  * 如果您選取 **NFS 儲存空間**，而且要個別新增及配置檔案共用，請選取**個別配置共用**。然後，按一下**新增共用儲存空間**標籤旁的 **+** 圖示，並針對每個檔案共用選取**效能**及**大小 (GB)**。您必須至少選取一個檔案共用。
9. 完成網路介面設定。
   1. 輸入要佈建之實例的主機名稱字首、子網域標籤，以及根網域名稱。對於次要實例，會自動完成網域名稱。
   2. 選取**公用及專用網路**或**僅限專用網路**的網路設定。
   3. 選取 VLAN 設定：
      * 如果您要訂購新的公用及專用 VLAN，則請按一下**訂購新的 VLAN**。
      * 如果您要重複使用可用的現有公用及專用 VLAN，則請按一下**選取現有的 VLAN**，然後指定 VLAN 及子網路。
   4. 指定 DNS 配置。

11. 在**訂單摘要**窗格上，先驗證實例配置，再下訂單。
   1. 檢閱實例的設定。
   2. 檢閱預估實例成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
   3. 按一下適用於您的訂單的條款鏈結，並先確認您同意這些條款，再訂購實例。
   4. 按一下**佈建**。

## 訂購 vCenter Server with NSX-T 實例之後的結果
{: #vc_nsx-t_orderinginstance-results}

* 實例的部署會自動啟動，且您會收到確認，指出正在處理該訂單。您可以檢查部署狀態，包括可能需要注意的任何問題，方法是檢視實例詳細資料的**部署歷程**區段。
* 順利部署實例之後，會在您的 VMware 虛擬平台上安裝 [vCenter Server with NSX-T 實例的技術規格](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_overview#vc_nsx-t_overview-specs)中所說明的元件。依預設，您所訂購的 ESXi 伺服器會分組為 **cluster1**。
* 實例已備妥可供使用時，實例的狀態會變更為**備妥使用**，而且您會透過電子郵件收到通知。
* 當您訂購次要實例時，可能會在您完成次要實例訂單之後重新啟動主要實例（鏈結至次要實例）的 VMware vSphere Web Client。

## 下一步
{: #vc_nsx-t_orderinginstance-next}

檢視及管理您訂購的 vCenter Server with NSX-T 實例。如需檢視實例的相關資訊，請參閱[檢視 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)。

您只能從 {{site.data.keyword.vmwaresolutions_short}} 主控台，而不能從 {{site.data.keyword.slportal}} 或透過主控台以外的任何其他方法，來管理在 {{site.data.keyword.cloud_notm}} 帳戶中建立的 {{site.data.keyword.vmwaresolutions_short}} 元件。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更這些元件，則變更不會與主控台同步。
{:important}

**警告：**從 {{site.data.keyword.vmwaresolutions_short}} 主控台以外來管理您在訂購實例時安裝至 {{site.data.keyword.cloud_notm}} 帳戶的任何 {{site.data.keyword.vmwaresolutions_short}} 元件，會使您的環境變得不穩定。這些管理活動包括：
*  新增、修改、退回或移除元件
*  透過新增或移除 ESXi 伺服器來擴充或縮減實例容量
*  關閉元件電源
*  重新啟動服務

   這些活動的例外包括從 {{site.data.keyword.slportal}} 管理共用儲存空間檔案共用。這類活動包括：訂購、刪除（這可能會影響已裝載的資料儲存庫）、授權及裝載共用儲存空間檔案共用。

## 相關鏈結
{: #vc_nsx-t_orderinginstance-related}

* [註冊 {{site.data.keyword.cloud_notm}} 帳戶](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts)
* [檢視 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server 實例的多站台配置](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)
* [新增、檢視及刪除 vCenter Server with NSX-T 實例的叢集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [擴充及縮減 vCenter Server with NSX-T 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
* [刪除 vCenter Server with NSX-T 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
