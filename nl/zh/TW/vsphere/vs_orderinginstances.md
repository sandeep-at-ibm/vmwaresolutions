---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

{:tip: .tip}

# 訂購新的 vSphere 叢集

若要部署可高度自訂的 VMware 虛擬化平台，請訂購 {{site.data.keyword.cloud}} 上的 VMware vSphere 叢集。使用此程序來定義新的 VMware vSphere 叢集。

此程序引導您完成 VMware 元件選取、{{site.data.keyword.cloud_notm}} Bare Metal Server 設定、儲存空間設定及網路選項，以建立新叢集。在下單之後，會擷取叢集配置，以便您可以返回並視需要繼續擴充叢集。完成訂單之後，您可以根據需求，手動配置 VMware 叢集。

## 需求

請確定您已完成下列作業：
*  您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[使用者帳戶及設定](../vmonic/useraccount.html)。
*  您已檢閱 [vSphere 叢集的需求及規劃](vs_planning.html)中的需求及考量。

## 系統設定

<!--**Important: Do not modify any values that are set during ordering and cluster deployment. Doing so can result in your cluster becoming unusable.**-->
訂購新的 vSphere 叢集時，您必須指定下列系統設定。

### 叢集名稱

叢集名稱在您的帳戶中必須是唯一的。

## 授權設定

選取要隨叢集訂購的 VMware 元件，並指定元件的授權選項。

### （僅限事業夥伴使用者）元件組合

如果您是事業夥伴使用者，則可以在訂購新的 vSphere 叢集時選取元件授權組合。可用的組合如下：

表 1. vSphere 叢集的事業夥伴元件組合

|組合|元件|
|:-------------------------|:-----------------------|
|Standard with Management      |vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vRealize Operations Enterprise                 |
|Advanced                 |vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vCloud Director、NSX Base |
|Advanced with Networking      |vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、NSX Advanced |
|Advanced with Networking and Management |vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vRealize Operations Enterprise、vCloud Director、NSX Enterprise |

您也可以在訂單中包括下列其他 VMware 元件：
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

**附註：**事業夥伴使用者沒有「自帶授權 (BYOL)」選項。完成您的訂單時，無法使用**我會提供授權**選項。

### （僅限非事業夥伴使用者）個別元件

如果您是非事業夥伴使用者，則可以針對 vSphere 叢集彈性地選取下列 VMware 元件：
* VMware vSphere Enterprise Plus
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

**附註：**當您訂購 VMware vSphere Enterprise Plus 6.0 時，VMware vSAN 元件無法使用。如果您打算使用自己的 VMware vSphere Enterprise Plus 6.0 授權，則會代表您開立 {{site.data.keyword.cloud_notm}} 基礎架構問題單，要求將已訂購的 {{site.data.keyword.baremetal_short}} 的 vSphere 授權取代為您提供的授權。

### 授權選項

您在授權已選取的 VMWare 元件時有下列選項：
* **購買隨附授權**：在此情況下，會代表您購買 VMware 元件的新授權。會產生結合的 VMware 授權，以符合訂單的叢集大小。
* **我將提供授權**：在此情況下，您將使用您自己的 VMware 元件授權。

如果您選擇購買任何授權（除了 vSphere Enterprise Plus 及 vCenter Server 以外），且您訂購多部 ESXi 伺服器，則會代表您自動開立 {{site.data.keyword.cloud_notm}} 問題單，以結合授權碼。您負責追蹤問題單，以確保您只使用 DevOps 團隊所產生的授權碼。

**重要事項**：將個別授權碼與結合的授權碼一起使用，不符合您所需授權的付款需求。

## Bare Metal Server 設定

### 資料中心位置

選取要在其中管理叢集的 {{site.data.keyword.CloudDataCent_notm}}。

**附註：**如果您選取一個 vSAN 元件，則會依 SSD 可用性來過濾位置清單。

### CPU 型號及 RAM

指定 Bare Metal Server 的 CPU 型號及 RAM。

表 2. 自訂 {{site.data.keyword.baremetal_short}} 的選項

|CPU 選項           |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon E5-2620 v4 /總計 16 核心，2.1 GHz |64 GB、128 GB、256 GB、384 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2650 v4 /總計 24 核心，2.2 GHz |64 GB、128 GB、256 GB、384 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2690 v4 /總計 28 核心，2.6 GHz |64 GB、128 GB、256 GB、384 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Silver 4110 處理器/總計 16 核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器/總計 28 核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 Processor / 總計 36 核心，2.3 GHz |64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

可用的選項取決於您是否已選取 VMware vSAN 元件。

### Bare Metal Server 數目

您要新增至 vSphere 叢集的 ESXi 伺服器數目。所有 ESXi 伺服器都會共用相同的配置。
* 如果您選取 VMware NSX 元件，則至少需要 3 部伺服器。
* 如果您選取 VMware vSAN 元件，則至少需要 4 部伺服器。

## 儲存空間設定

對於不包含 vSAN 的訂單，會訂購具有 12 磁碟機箱的 ESXi 伺服器，以及用於 ESXi 作業系統 (OS) 的兩個磁碟。

對於含有 vSAN 的訂單，會訂購具有 12 磁碟機箱的 ESXi 伺服器，並訂購四個磁碟：兩個用於 ESXi OS，兩個保留供快取使用。依預設會配置這些設定，且無法變更。您可以選取 **vSAN 容量磁碟的磁碟類型及大小**及 **vSAN 容量磁碟數目**，來訂購更多容量磁碟。

當您已選取叢集的 VMware vSAN 元件時，請指定下列設定。

### vSAN 容量磁碟的磁碟類型及大小

只有在您選取 VMware vSAN 元件時，才能使用此選項。

可用的磁碟類型如下：
* 960 GB SSD SED
* 1.9 TB SSD SED
* 3.8 TB SSD SED（當 3.8 TB SSD SED 磁碟機在正式發行至資料中心時就會予以支援）

### vSAN 容量磁碟數目

只有在您選取 VMware vSAN 元件時，才能使用此選項。磁碟數量選項包括 2、4、6 和 8。

## 網路介面設定

訂購新的 vSphere 叢集時，您必須指定下列網路介面設定。

### 主機名稱字首

主機名稱使用於所有 Bare Metal Server 訂單。建議您對所有管理虛擬機器使用主機名稱，例如 vCenter Server、NSX 等等。

主機名稱字首必須符合下列需求：
* 名稱的開頭及結尾必須是英數字元。
* 只容許英數及橫線 (-) 字元。
* 最大長度是 10 個字元。

### 子網域標籤

子網域標籤必須符合下列需求：
*  只容許英數及橫線 (-) 字元。
*  子網域標籤的開頭及結尾必須是英數字元。
*  子網域標籤的長度上限為 10 個字元。
*  子網域標籤在您的帳戶內必須是唯一的。

### 網域名稱

網域名稱使用於所有 {{site.data.keyword.baremetal_short}}，且必須符合下列需求：
* 名稱必須包含兩個以上以句點 (.) 區隔的字串
* 只容許英數及橫線 (-) 字元。
* 每一個字串的開頭都必須是英文字母、結尾必須是英數字元，而最後一個字串只能包含英文字母。
* 最後一個字串的長度範圍必須在 2 到 24 個字元之間。
* 其他字串的長度必須在 1 - 63 個字元的範圍內。
* 網域名稱的長度上限為 189 個字元。

### VLAN

網路設定是根據您選取**訂購新的 VLAN** 或**選取現有的 VLAN** 而定。

您的叢集訂單需要一個公用 VLAN 及兩個專用 VLAN。兩個專用 VLAN 成為每部 Bare Metal Server 的主幹。

#### 訂購新的 VLAN
選取訂購一個新的公用 VLAN 和兩個新的專用 VLAN。

#### 選取現有的 VLAN  
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

#### FortiGate Physical Appliance 300 系列 HA 配對

您也可以選取是否包括「FortiGate Physical Appliance 300 系列 HA 配對」來保護雲端環境安全。如需相關資訊，請參閱 [FortiGate Security Appliance on IBM Cloud 概觀](../services/fsa_considerations.html)。

## 訂單摘要

根據您的配置，預估成本會立即產生並顯示在右側的**訂單摘要**窗格中。按一下窗格底端的**定價詳細資料**，以產生提供預估值詳細資料的 PDF 文件。

## 程序

1. 在「{{site.data.keyword.cloud_notm}} 型錄」中，按一下左導覽窗格上的 **VMware**，然後按一下**虛擬資料中心**區段中的 **VMware vSphere**。
2. 在 **VMware vSphere on IBM Cloud** 頁面上，按一下**建立**。  
   請確定您位於**建立新項目**標籤，並在**叢集配置**清單中顯示**新叢集**。
3. 輸入叢集名稱。
4. 選取 VMware 元件：
  * 如果您是事業夥伴使用者，則請選取一個授權組合及任何其他可用的 VMware 元件。
  * 如果您是非事業夥伴使用者，則請選取元件（如果有的話，則請選取版本），並指定授權選項。
  當您選擇針對 VMware vSphere Enterprise Plus「自帶授權 (BYOL)」時，會代表您自動開立 {{site.data.keyword.cloud_notm}} 問題單，要求將您訂購的 {{site.data.keyword.baremetal_short}} 上的預設 vSphere 授權取代為您提供的授權。   

    **重要事項：**您負責追蹤問題單，以確保在新訂購的 ESXi 伺服器上取代 vSphere 授權，以便 {{site.data.keyword.cloud_notm}} 基礎架構授權取消初始提供的 {{site.data.keyword.cloud_notm}} 基礎架構 vSphere 授權費。如果要取代您的 ESXi vSphere 授權，請參閱[配置 ESXi 主機的授權設定](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}。

5. 完成 Bare Metal Server 設定：
   1. 選取 {{site.data.keyword.CloudDataCent_notm}} 來管理叢集。
   2. 選取 CPU 型號及 RAM 大小。
   3. 指定 Bare Metal Server 數目。
6. 如果您已選取 **VMware vSAN** 元件，請選取 **vSAN 容量磁碟的磁碟類型及大小**及 **vSAN 容量磁碟數目**，來完成 vSAN 儲存空間設定。
7. 完成網路介面設定：
   1. 輸入主機名稱字首、子網域標籤及網域名稱。
   2. 選取要使用的網路介面：
    * 如果您要訂購新的公用及專用 VLAN，則請按一下**訂購新的 VLAN**。
    * 如果您要重複使用可用的現有公用及專用 VLAN，則請按一下**選取現有的 VLAN**，然後指定 VLAN 及選用子網路。
    3. 指定是否套用「FortiGate Physical Appliance 300 系列 HA 配對」來保護雲端環境安全。  
8. 在**訂單摘要**窗格中，驗證叢集配置及預估成本。
   * 若要將配置儲存為範本而不下訂單，請按一下**儲存配置**。
   * 若要下訂單，請確定要收費的帳戶正確，請檢閱並接受條款，然後按一下**佈建**。

   **附註**：僅安裝 {{site.data.keyword.baremetal_short}}。您負責在叢集部署之後安裝及配置各種元件，例如 VMware vCenter、VMware NSX、VMware vSAN。

## 結果

如果您將叢集配置儲存為範本，則會收到主控台通知，指出已順利儲存配置，然後您可以在**叢集配置**清單中找到該範本。

如果您已下訂單，則會自動啟動叢集的部署，且您會收到電子郵件確認，指出正在處理該訂單。當叢集已備妥可供使用時，會透過電子郵件通知您。

**附註：**vSphere 叢集與 vCenter Server 及 Cloud Foundation 實例不同，並不會顯示在**已部署的實例**頁面上。

## 相關鏈結

* [根據現有配置來訂購 vSphere 叢集](vs_orderingbasedonexistingconfig.html)
* [擴充現有的叢集](vs_scalingexistingclusters.html)
* [擴充在主控台以外建立的叢集](vs_orderingforclustersoutside.html)
