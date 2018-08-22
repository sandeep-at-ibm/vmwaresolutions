---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# 訂購 vCenter Server 實例

若要部署彈性且可自訂的 VMware 虛擬化平台，以符合您的工作負載需求，請訂購 VMware vCenter Server 實例。在起始訂購期間，您也可以新增服務，例如 [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html)，來進行災難回復。

## 需求

請確定您已完成下列作業：
* 您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[管理使用者帳戶及設定](../vmonic/useraccount.html)。
* 您已檢閱 [vCenter Server 實例的需求及規劃](vc_planning.html)中的資訊。
* 您已檢閱實例及網域名稱格式。網域名稱及子網域標籤已用來產生實例的使用者名稱及伺服器名稱。

表 1. 實例及網域名稱的值格式

|名稱 |值格式            |
  |:------------- |:------------- |
  |網域名稱    | `<root_domain>` |  
  |vCenter Server 登入使用者名稱  | `<user_id>@<root_domain>`（Microsoft Active Directory 使用者）或 `administrator@vsphere.local` |
  |vCenter Server FQDN |`vcenter.<subdomain_label>.<root_domain>`. 長度上限為 50 個字元。|
  |單一登入 (SSO) 站台名稱| `<subdomain_label>` |
  |完整的 ESXi 伺服器名稱| `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中 `<n>` 是 ESXi 伺服器的序號。長度上限為 50 個字元。|  
  |PSC FQDN |`psc-<subdomain_label>.<subdomain_label>.<root_domain>`. 長度上限為 50 個字元。|

**重要事項**：請不要修改在訂購及實例部署期間設定的任何值。這樣做會導致您的實例變成無法使用。例如，公用網路可能會關閉、伺服器和虛擬伺服器實例 (VSI) 可能在 Vyatta 佈建進行中落後，或者 IBM CloudBuilder VSI 可能會停止或遭到刪除。

## 系統設定

訂購 vCenter Server 實例時，您必須指定下列系統設定。

### 實例名稱

實例名稱必須符合下列需求：
* 只容許英數及橫線 (-) 字元。
* 實例名稱的開頭及結尾必須是英數字元。
* 實例名稱的長度上限為 10 個字元。
* 實例名稱在您的帳戶中必須是唯一的。

### 主要或次要

選取要訂購新的主要實例，還是要為現有的主要實例訂購次要實例。

## 授權設定

在實例中，指定下列 VMware 元件的授權選項：
* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.4

對於「事業夥伴」使用者，包括 vCenter Server 授權（Standard 版本）、vSphere 授權（Enterprise Plus 版本）及 NSX 授權，並可代表您購買。不過，您必須指定 NSX 授權的版本。

對於非「事業夥伴」使用者，您可以選取**購買隨附**以將 IBM 提供的 VMware 授權用於這些元件，也可以選取**我將提供**並輸入自己的授權碼以「自帶授權 (BYOL)」。

**注意**：
* 需要最少有 8 個 CPU 的授權，這是針對 4 部伺服器，而每部伺服器都有 2 個 CPU。每個 VMware 元件的授權選項適用於基本實例，以及之後新增至該實例的任何 ESXi 伺服器。因此，您必須確保您的授權支援基礎架構中的未來容量擴充。
* 使用者介面上會指出最低授權版本。如果支援不同的元件版本，您可以選取您想要的版本。您必須負責確保所提供的授權碼對於每一個選取的 VMware 元件都是正確的。
* 對於 vSphere，會在訂購時產生授權費用，但授權費用將在後來記入您的帳戶中。
* 實例部署完成之後，您可以使用 VMware vSphere Web Client 來變更所提供的任何授權。
* 針對您提供授權的 VMware 元件，其支援將直接由 VMware 提供，而不是由 IBM 支援中心提供。

## Bare Metal Server 設定

Bare Metal Server 設定是根據您選取的資料中心，以及選擇預先配置還是自訂配置。

### 資料中心位置

選取要在其中管理實例的 {{site.data.keyword.CloudDataCent_notm}}。

### 預先配置

當您選取**預先配置**時，無法變更 CPU 或 RAM 設定。

根據您的需求，選取 Bare Metal Server 配置：
  * 小型（雙重 Intel Xeon E5-2620 v4 /總計 16 核心，2.1 GHz / 128 GB RAM / 2 個磁碟機）
  * 中型（雙重 Intel Xeon E5-2650 v4 /總計 24 核心，2.2 GHz / 256 GB RAM / 2 個磁碟機）
  * 大型（雙重 Intel Xeon E5-2690 v4 /總計 28 核心，2.6 GHz / 512 GB RAM / 2 個磁碟機）

### 自訂

當您選取**自訂**時，可以根據需求來選擇 CPU 與 RAM 組合。

選取 Bare Metal Server 的 CPU 型號及 RAM。

表 2. 自訂 {{site.data.keyword.baremetal_short}} 的選項

|CPU 選項           |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon E5-2620 v4 /總計 16 核心，2.1 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2650 v4 /總計 24 核心，2.2 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2690 v4 /總計 28 核心，2.6 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Silver 4110 處理器/總計 16 核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器/總計 28 核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 Processor / 總計 36 核心，2.3 GHz |64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

### Bare Metal Server 數目

對於實例中的起始叢集，您可以如下所示配置 ESXi 伺服器數目：
* 如果您選取**預先配置**，您可以配置在 2 - 10 範圍內的 ESXi 伺服器數目。
* 如果您選取**自訂**，您可以配置在 2 - 20 範圍內的 ESXi 伺服器數目。

所有 ESXi 伺服器都共用相同的配置。起始部署之後，您可以再新增四個叢集。如果您對 vSAN 選取了**自訂**配置，則起始叢集和後置部署叢集都需要 4 部 ESXi 伺服器。如需最少 ESXi 伺服器數目的相關資訊，請參閱[雙節點 vCenter Server 實例是否為高可用性](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)。

## 儲存空間設定

儲存空間設定是根據您選取的 Bare Metal Server 配置及儲存空間類型而定。

### vSAN 儲存空間

只有選取**自訂** Bare Metal Server 配置時，才能使用 vSAN。請指定下列 vSAN 選項：

* **vSAN 容量磁碟數目**：指定您要新增的 vSAN 共用儲存空間的磁碟數目。磁碟數量必須是 2、4、6 或 8。
* **vSAN 容量磁碟的磁碟類型及大小**：選取符合共用儲存空間需求的容量。
* **vSAN 授權**：選取**購買隨附**以將 IBM 提供的 VMware 授權用於 vSAN 元件，也可以選取**我將提供**並輸入自己的授權碼以「自帶授權 (BYOL)」。

### NFS 儲存空間

當您選取 **NFS 儲存空間**時，可以為實例新增所有共用相同設定的檔案層次共用儲存空間，也可以為每一個檔案共用指定不同的配置設定。請指定下列 NFS 選項：

**附註：**檔案共用數目必須在 1 到 32 的範圍內。

* **個別配置共用**：選取以指定每一個檔案共用的不同配置設定。
* **共用數目**：使用每一個檔案共用的相同配置設定時，請指定您要新增之 NFS 共用儲存空間的檔案共用數目。
* **大小**：選取符合共用儲存空間需求的容量。
* **效能**：根據您的工作負載需求，選取每 GB IOPS（每秒輸入/輸出作業數）。
* **新增 NFS**：選取以新增要使用不同配置設定的個別檔案共用。

表 3. NFS 效能層次選項

|選項          |詳細資料      |
  |:------------- |:------------- |
  |2 IOPS/GB |這個選項是為大部分通用工作負載而設計。應用的範例包括：管理小型資料庫、備份 Web 應用程式，或是 Hypervisor 用的虛擬機器磁碟映像檔。|
  |4 IOPS/GB |這個選項是為一次擁有高百分比作用中資料的高密度工作負載而設計。應用的範例包括：交易式資料庫。|
  |10 IOPS/GB |這個選項是為需求最大的工作負載類型而設計，例如分析。應用的範例包括：高交易量資料庫，以及其他對效能敏感的資料庫。此效能層次限制為每個檔案共用的容量上限為 4 TB。|

## 網路介面設定

訂購 vCenter Server 實例時，您必須指定下列網路介面設定。

### 主機名稱字首

主機名稱字首必須符合下列需求：
*  只容許英數及橫線 (-) 字元。
*  主機名稱字首的開頭及結尾必須是英數字元。
*  主機名稱字首的長度上限為 10 個字元。

### 子網域標籤

子網域標籤必須符合下列需求：
*  只容許英數及橫線 (-) 字元。
*  子網域標籤的開頭及結尾必須是英數字元。
*  子網域標籤的長度上限為 10 個字元。
*  子網域標籤在您的帳戶內必須是唯一的。

### 網域名稱

根網域名稱必須符合下列需求：
* 網域名稱必須包含兩個以上以句點 (.) 區隔的字串
* 第一個字串的開頭必須是英文字母，而且結尾必須是英數字元。
* 除了最後一個字串以外，所有字串都只能包含英數字元和橫線 (-) 字元。
* 最後一個字串只能包含英文字母。
* 最後一個字串的長度範圍必須在 2 到 24 個字元之間。

**附註：**主機和 VM 的「完整網域名稱 (FQDN)」長度上限為 50 個字元。網域名稱必須在這個長度上限以內。

### VLAN

網路設定是根據您選取**訂購新的 VLAN** 或**選取現有的 VLAN** 而定。

您的實例訂單需要一個公用 VLAN 及兩個專用 VLAN。兩個專用 VLAN 成為每部 Bare Metal Server 的主幹。

**訂購新的 VLAN**  
選取訂購一個新的公用 VLAN 和兩個新的專用 VLAN。

**選取現有的 VLAN**  
視您選取的 {{site.data.keyword.CloudDataCent_notm}} 而定，可能會提供現有的公用和專用 VLAN。

當您選擇重複使用現有的公用及專用 VLAN 時，請指定 VLAN 及子網路：
* **公用 VLAN** 適用於公用網路存取。
* **專用 VLAN** 適用於 {{site.data.keyword.cloud_notm}} 內資料中心與服務之間的連線功能。
* **次要專用 VLAN** 適用於 VMware 特性（例如 vSAN）。
* **主要子網路**已指派給實體主機，以進行公用網路存取。
* **主要專用子網路**已指派給實體主機，以處理管理資料流量。

**重要事項：**
* 確保所選取 VLAN 上的防火牆配置未封鎖管理資料流量。
* 確保您選取的所有 VLAN 都在相同的 Pod 中，因為無法在混合 Pod VLAN 上佈建 ESXi 伺服器。

### DNS 配置

選取實例的「網域名稱系統 (DNS)」配置：

* **單一公用 Windows VSI for Active Directory/DNS**：已部署並可查閱單一 Microsoft Windows Server VSI for Microsoft Active Directory (AD)（其充當已登錄主機及 VM 之實例的 DNS）。依預設，已對 1.9 版以及更新版本的實例部署此選項。
* **管理叢集上有兩部高可用性的專用 Windows Server VM**：部署兩部 Microsoft Windows VM，協助加強安全及穩健性。

**重要事項：**如果您將實例配置為使用兩部 Microsoft Windows VM，則必須提供兩個 Microsoft Windows Server 2012 R2 授權。請使用 Microsoft Windows Server 2012 R2 Standard 版本授權及（或）Microsoft Windows Server 2012 R2 Datacenter 版本授權。

每一個授權都只能指派給一部單一實體伺服器，且最多涵蓋兩個實體處理器。以一個 Standard 版本授權而言，每一部雙處理器伺服器都可以執行兩部虛擬化 Microsoft Windows VM。因此，必須有兩個授權，因為兩部 Microsoft Windows VM 部署在兩部不同的主機中。

您有 30 天的時間可啟動 VM。

如需 Windows 授權的相關資訊，請參閱 [Windows Server 2012 R2 文件](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2)。

## 服務設定

當您訂購 vCenter Server 實例時，也可以訂購其他服務。如需服務的相關資訊，請參閱 [vCenter Server 實例的可用服務](vc_addingremovingservices.html#available-services-for-vcenter-server-instances)。

## 訂單摘要

根據您選取的實例及附加程式服務配置，預估成本會立即產生並顯示在右窗格的**訂單摘要**區段中。按一下右窗格底端的**定價詳細資料**，以產生提供預估值詳細資料的 PDF 文件。

## 程序

1. 在「{{site.data.keyword.cloud_notm}} 型錄」中，從左導覽窗格中按一下 **VMware**，然後按一下**虛擬資料中心**區段中的 **vCenter Server**。
2. 在 **VMware vCenter Server on IBM Cloud** 頁面上，按一下 **vCenter Server** 卡片，然後按一下**建立**。
3. 在 **vCenter Server** 頁面上，輸入實例名稱。
4. 選取實例類型：
   * 按一下**主要實例**，以在環境中部署單一實例，或是部署多站台拓蹼中的第一個實例。
   * 按一下**次要實例**，以連接該實例與環境中的現有（主要）實例以獲得高可用性，然後完成下列步驟：
     1. 選取您要與次要實例連接的主要實例。
     2. 輸入主要實例的 PSC 管理者密碼。
5. 完成實例元件的授權設定。  
   *  若要使用 IBM 提供的授權，請選取**購買隨附**，然後選取授權版本（必要的話）。
   *  若要使用您自己的授權，請選取**我將提供**，然後輸入授權碼。
6. 完成 Bare Metal Server 設定。
    1. 選取 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。
    2. 選取 Bare Metal Server 配置。
       * 當您選取**預先配置**時，請針對配置選擇**小型**、**中型**或**大型**。
       * 當您選取**自訂**時，請指定 CPU 型號及 RAM 大小。
    3. 指定 {{site.data.keyword.baremetal_short}} 數目。如果您打算使用 vSAN 作為儲存空間解決方案，請注意，至少需要 4 部 {{site.data.keyword.baremetal_short}}。  

7. 完成儲存空間設定：
  * 當您選取 **vSAN 儲存空間**時，請指定 **vSAN 容量磁碟的磁碟類型及大小**、**vSAN 容量磁碟數目**，以及如何提供 **vSAN 授權**。
  * 當您選取 **NFS 儲存空間**且想要對所有檔案共用新增及配置相同的設定時，請指定**共用數目**、**大小**及**效能**。
  * 當您選取 **NFS 儲存空間**且想要個別新增及配置檔案共用時，請選取**個別配置共用**，然後按一下**新增 NFS** 標籤旁的 **+** 圖示，並針對每一個個別檔案共用選取**大小**及**效能**。您必須至少選取一個檔案共用。

8. 完成網路介面設定。
   1. 輸入主機名稱字首、子網域標籤及根網域名稱。對於次要實例，會自動填寫網域名稱。
   2. 選取 VLAN 設定：
      * 如果您要訂購新的公用及專用 VLAN，則請按一下**訂購新的 VLAN**。
      * 如果您要重複使用可用的現有公用及專用 VLAN，則請按一下**選取現有的 VLAN**，然後指定 VLAN 及子網路。
   3. 指定 DNS 配置。

9. 按一下對應的服務卡，以選取要部署到實例中的附加程式服務。如果需要配置服務，則請完成服務特定設定，然後按一下卡片上的**新增服務**。如需如何提供服務設定的相關資訊，請參閱對應的服務訂購主題。

10. 在**訂單摘要**窗格上，先驗證實例配置，再下訂單。
   1. 檢閱實例的設定。
   2. 檢閱預估實例成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
   3. 按一下適用於您的訂單的條款鏈結，並先確認您同意這些條款，再訂購實例。
   4. 按一下**佈建**。

## 結果

實例的部署會自動啟動。您會收到正在處理訂單的確認，您可以檢視實例詳細資料來檢查部署的狀態。

順利部署實例之後，會在 VMware 虛擬平台上安裝 [vCenter Server 實例的技術規格](vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)中所說明的元件。依預設，您所訂購的 ESXi 伺服器會分組為 **cluster1**。如果您已訂購其他服務，則會在完成訂單之後開始部署服務。

實例已備妥可供使用時，實例的狀態會變更為**備妥使用**，而且您會透過電子郵件收到通知。

當您訂購次要實例時，可能會在您完成次要實例訂單之後重新啟動主要實例（鏈結至次要實例）的 VMware vSphere Web Client。

## 下一步

檢視及管理您訂購的 vCenter Server 實例。

**重要事項**：您只能從 {{site.data.keyword.vmwaresolutions_short}} 主控台而不是 {{site.data.keyword.slportal}} 或透過主控台以外的任何其他方法，來管理在 {{site.data.keyword.cloud_notm}} 帳戶中建立的 {{site.data.keyword.vmwaresolutions_short}} 元件。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更這些元件，則變更不會與主控台同步。

**警告**：從 {{site.data.keyword.vmwaresolutions_short}} 主控台以外來管理您在訂購實例時所安裝至 {{site.data.keyword.cloud_notm}} 帳戶的任何 {{site.data.keyword.vmwaresolutions_short}} 元件，會使您的環境變得不穩定。這些管理活動包括：
*  新增、修改、退回或移除元件
*  透過新增或移除 ESXi 伺服器來擴充或縮減實例容量
*  關閉元件電源
*  重新啟動服務

   這些活動的例外包括從 {{site.data.keyword.slportal}} 管理共用儲存空間檔案共用。這類活動包括：訂購、刪除（這可能會影響已裝載的資料儲存庫）、授權及裝載共用儲存空間檔案共用。

### 相關鏈結

* [註冊 {{site.data.keyword.cloud_notm}} 帳戶](../vmonic/signing_softlayer_account.html)
* [檢視 vCenter Server 實例](vc_viewinginstances.html)
* [vCenter Server 實例的多站台配置](vc_multisite.html)
* [新增、檢視及刪除 vCenter Server 實例的叢集](vc_addingviewingclusters.html)
* [擴充及縮減 vCenter Server 實例的容量](vc_addingremovingservers.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](vc_addingremovingservices.html)
* [刪除 vCenter Server 實例](vc_deletinginstance.html)
