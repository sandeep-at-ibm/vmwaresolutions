---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# 訂購 VMware Federal 實例

若要部署彈性且可自訂的 VMware 虛擬化平台，以符合您的工作負載需求，請訂購 VMware Federal 實例，讓您能夠中斷已開啟的管理連線及維護已部署實例的安全。

**附註：**目前只有 vCenter Server 實例支援 VMware Federal on {{site.data.keyword.cloud}}。

## 需求

請確定您已完成下列作業：
* 您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[管理使用者帳戶及設定](../vmonic/useraccount.html)。
* 您已檢閱 [VMware Federal 實例的需求及規劃](vc_fed_planning.html)中的資訊。
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

**重要事項**：請不要修改在訂購及實例部署期間設定的任何值。這樣做會導致您的實例變成無法使用。例如，公用網路可能會關閉、伺服器和「虛擬伺服器實例 (VSI)」在進行佈建時可能會移到 Vyatta 後方，或 IBM CloudBuilder VSI 可能會停止或遭到刪除。

## 系統設定

訂購 VMware Federal 實例時，您必須指定下列系統設定。

### 實例名稱

實例名稱必須符合下列需求：
* 只容許英數及橫線 (-) 字元。
* 實例名稱的開頭及結尾必須是英數字元。
* 實例名稱的長度上限為 10 個字元。
* 實例名稱在您的帳戶中必須是唯一的。

### 主要或次要

訂購新的主要實例。目前不支援部署次要實例來獲得高可用性。

## 授權設定

下列項目的 IBM 提供的 VMware 授權：

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.4
* （針對 vSAN 叢集）VMware vSAN Advanced 或 Enterprise 6.6

**注意：**

* 使用者介面上會指出最低授權版本。如果支援不同的元件版本，您可以選取您想要的版本。您必須負責確保所提供的授權碼對於每一個選取的 VMware 元件都是正確的。
* 對於 vSphere，會在訂購時產生授權費用，但授權費用將在後來記入您的帳戶中。

## Bare Metal Server 設定

Bare Metal Server 設定是根據您的自訂配置。目前不支援選取預先配置的選項。

### 資料中心位置

選取要在其中管理實例的 {{site.data.keyword.CloudDataCent_notm}}。

### 自訂

指定 Bare Metal Server 的 CPU 型號及 RAM。

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

您可以配置在 2 - 20 範圍內的 ESXi 伺服器數目。

所有 ESXi 伺服器都共用相同的配置。在後置部署中，您可以再新增四個叢集。對於 vSAN 儲存空間設定，起始及後置部署叢集都需要 4 部 ESXi 伺服器。如需最少 ESXi 伺服器的相關資訊，請參閱[雙節點 vCenter Server 實例是否為高可用性？](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## 儲存空間設定

儲存空間設定是根據您選取的 Bare Metal Server 配置及儲存空間類型而定。

### vSAN 儲存空間

對於 vSAN，請指定下列儲存空間選項：

* **vSAN 容量磁碟的磁碟類型及大小**：選取符合共用儲存空間需求的容量。
* **vSAN 容量磁碟數目**：選取您要新增的 vSAN 共用儲存空間的磁碟數目。磁碟數量必須是 2、4、6 或 8。
* 選取 VMware vSAN 6.6 授權版本（Advanced 或 Enterprise）。

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

### DNS 配置

選取實例的「網域名稱系統 (DNS)」配置：

* **適用於 Active Directory/DNS 的單一公用 Windows VSI**：用於 Microsoft Active Directory (AD)（其充當已登錄主機及虛擬機器之實例的 DNS）的 Microsoft Windows Server VSI，已部署並可查閱。
* **管理叢集上有兩部高可用性的專用 Windows Server VM**：對於 2.3 版及未來版本，會部署兩部 Microsoft Windows 虛擬機器，協助加強安全及穩健性。

**重要事項：**如果您將實例配置為使用兩部 Microsoft Windows 虛擬機器，則必須提供兩個 Microsoft Windows Server 2012 R2 授權。請使用 Microsoft Windows Server 2012 R2 Standard 版本授權及/或 Microsoft Windows Server 2012 R2 Datacenter 版本授權。

目前，每一個授權只能指派給一部單一實體伺服器，且最多涵蓋兩個實體處理器。以一個 Standard 版本授權而言，每一部雙處理器伺服器可執行兩部虛擬化的 Microsoft Windows 虛擬機器。因此，必須有兩個授權，因為兩部 Microsoft Windows 虛擬機器是部署在兩部不同的主機中。

您有 30 天的時間可啟動虛擬機器。

如需訂購 Windows 授權的相關資訊，請參閱 [Windows Server 2012 R2 文件](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2)。

## 訂單摘要

根據您選取的實例配置，預估成本會立即產生並顯示在右窗格的**訂單摘要**區段中。按一下右窗格底端的**定價詳細資料**，以產生提供預估值詳細資料的 PDF 文件。

## 程序

1. 在「{{site.data.keyword.cloud_notm}} 型錄」中，從左導覽窗格中按一下 **VMware**，然後按一下**虛擬資料中心**區段中的 **vCenter Server**。
2. 在 **VMware vCenter Server on IBM Cloud** 頁面上，按一下 **vCenter Server** 卡片，然後按一下**建立**。
3. 在 **vCenter Server** 頁面上，輸入實例名稱。
4. 按一下**主要實例**，以在環境中部署單一實例。
5. 指定 VMware NSX 授權版本。
6. 完成 Bare Metal Server 配置：
  1. 選取 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。
  2. 選取**自訂** CPU 型號及 **RAM** 數量。
7. 完成儲存空間配置。
  * 當您選取 **vSAN 儲存空間**時，請指定 **vSAN 容量磁碟的磁碟類型及大小**、**vSAN 容量磁碟數目**，以及如何提供 **vSAN 授權**。
  * 當您選取 **NFS 儲存空間**且想要對所有檔案共用新增及配置相同的設定時，請指定**共用數目**、**大小**及**效能**。
  * 當您選取 **NFS 儲存空間**且想要個別新增及配置檔案共用時，請選取**個別配置共用**，然後按一下**新增 NFS** 標籤旁的 **+** 圖示，並針對每一個個別檔案共用選取**大小**及**效能**。您必須至少選取一個檔案共用。
8. 完成網路介面配置。
   1. 輸入主機名稱字首、子網域標籤及根網域名稱。
   2. 選取 DNS 配置。
9. 在**訂單摘要**窗格上，先驗證實例配置，再下訂單。
   1. 檢閱實例的設定。
   2. 按一下適用於您的訂單的條款鏈結，並先確認您同意這些條款，再訂購實例。
   3. 按一下**計算成本**下的成本鏈結，以檢閱實例的預估成本。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
   4. 按一下**佈建**。

## 結果

實例的部署會自動啟動。您會收到正在處理訂單的確認，您可以檢視實例詳細資料來檢查部署的狀態。

順利部署實例之後，會在 VMware 虛擬平台上安裝 [VMware Federal on {{site.data.keyword.cloud_notm}} 實例的技術規格](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances)中所說明的元件。依預設，您所訂購的 ESXi 伺服器會分組為 **cluster1**。

實例已備妥可供使用時，實例的狀態會變更為**備妥使用**，而且您會透過電子郵件收到通知。

## 下一步

檢視、管理或保護您所訂購的 VMware Federal 實例。

**重要事項：**您必須從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 {{site.data.keyword.cloud_notm}} 帳戶中所建立的 {{site.data.keyword.vmwaresolutions_short}} 元件，而不是在主控台以外的 {{site.data.keyword.slportal}} 或透過任何其他方法進行管理。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更這些元件，則變更不會與主控台同步。

**警告：**從 {{site.data.keyword.vmwaresolutions_short}} 主控台以外來管理您在訂購實例時安裝至 {{site.data.keyword.cloud_notm}} 帳戶的任何 {{site.data.keyword.vmwaresolutions_short}} 元件，會使您的環境變得不穩定。這些管理活動包括：
*  新增、修改、退回或移除元件
*  透過移除 ESXi 伺服器來擴充或縮減實例容量
*  關閉元件電源

   這些活動的例外包括從 {{site.data.keyword.slportal}} 管理共用儲存空間檔案共用。這類活動包括：訂購、刪除（這可能會影響已裝載的資料儲存庫）、授權及裝載共用儲存空間檔案共用。

### 相關鏈結

* [註冊 {{site.data.keyword.cloud_notm}} 帳戶](../vmonic/signing_softlayer_account.html)
* [檢視 VMware Federal 實例](vc_fed_viewinginstance.html)
* [擴充及縮減 VMware Federal 實例的容量](vc_fed_addingremovingservers.html)
* [新增、檢視及刪除 VMware Federal 實例的叢集](fed_addviewdeleteclusters.html)
* [維護 VMware Federal 實例的安全](vc_fed_securinginstance.html)
* [刪除 VMware Federal 實例](vc_fed_deletinginstance.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
