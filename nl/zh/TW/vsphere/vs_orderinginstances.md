---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vSphere order cluster, order vSphere, order vSphere cluster

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購新的 vSphere 叢集
{: #vs_orderinginstances}

若要部署可高度自訂的 VMware 虛擬化平台，請訂購 {{site.data.keyword.cloud}} 上的 VMware vSphere 叢集。使用此程序來定義新的 vSphere 叢集。

此程序引導您完成選取 VMware 元件、{{site.data.keyword.cloud_notm}} Bare Metal Server 設定、儲存空間設定及網路選項，以建立新叢集。在下訂單之後，會擷取叢集配置，以便您可以回來視需要繼續橫向擴充叢集。完成訂單之後，您可以根據需求，手動配置 VMware 叢集。

## 需求
{: #vs_orderinginstances-req}

請確定您已完成下列作業：
*  您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[管理使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。
*  您已檢閱 [vSphere 叢集的需求及規劃](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)中的需求及考量。

## 系統設定
{: #vs_orderinginstances-sys-settings}

當您訂購新的 vSphere 叢集時，必須指定下列系統設定。

### 叢集名稱
{: #vs_orderinginstances-cluster-name}

叢集名稱在您的帳戶中必須是唯一的。

## 授權設定
{: #vs_orderinginstances-licensing-settings}

選取要隨叢集訂購的 VMware 元件，並指定元件的授權選項。

### IBM 事業夥伴使用者的元件組合
{: #vs_orderinginstances-component-bundles-for-bp-users}

如果您是「IBM 事業夥伴」使用者，則可以在訂購新的 vSphere 叢集時選取元件授權組合。可用的組合如下：

|組合|元件|
|:------------------------- |:----------------------- |
|Standard with Management      |vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vRealize Operations Enterprise                 |
|Advanced                 |vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vCloud Director、NSX Base |
|Advanced with Networking      |vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、NSX Advanced |
|Advanced with Networking and Management |vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vRealize Operations Enterprise、vCloud Director、NSX Enterprise |
{: caption="表 1. vSphere 叢集的「IBM 事業夥伴」元件組合" caption-side="top"}

您也可以在訂單中包括下列 VMware 元件：
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

對於「IBM 事業夥伴」使用者，無法使用「自帶授權 (BYOL)」選項。
{:note}

### 非事業夥伴使用者的個別元件
{: #vs_orderinginstances-individual-components-for-non-bp-users}

如果您是非「事業夥伴」，則可以針對 vSphere 叢集選取下列元件：
* VMware vSphere Enterprise Plus 6.7 U1 或 6.5 U2
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

當您訂購 VMware vSphere Enterprise Plus 6.0 時，VMware vSAN 元件無法使用。如果您打算使用自己的 VMware vSphere Enterprise Plus 6.0 授權，則會代表您開立 {{site.data.keyword.cloud_notm}} 基礎架構問題單。此問題單要求將已訂購的 {{site.data.keyword.baremetal_short}} 的 vSphere 授權取代為您提供的授權。
{:note}

### 授權選項
{: #vs_orderinginstances-licensing-options}

您在授權已選取的 VMWare 元件時有下列選項：
* **購買隨附授權**：在此情況下，會代表您購買 VMware 元件的新授權。會產生結合的 VMware 授權，以符合訂單的叢集大小。
* **我將提供授權**：在此情況下，您會使用自己的 VMware 元件授權。

如果您選擇購買任何授權（除了 vSphere Enterprise Plus 及 vCenter Server 以外），且您訂購多部 ESXi 伺服器，則會代表您自動開立 {{site.data.keyword.cloud_notm}} 問題單，以結合授權碼。您負責追蹤問題單，以確保您只使用 DevOps 團隊所產生的授權碼。

將個別授權碼與結合的授權碼一起使用，不符合您所需授權的付款需求。
{:important}

## Bare Metal Server 設定
{: #vs_orderinginstances-bare-metal-settings}

### 資料中心位置
{: #vs_orderinginstances-dc-location}

選取要在其中管理叢集的 {{site.data.keyword.CloudDataCent_notm}}。

####  附註 
{: #vs_orderinginstances-notes}

* 如果您選取 vSAN 元件，則會依 SSD 可用性來過濾位置清單。
* Broadwell Bare Metal Server 不適用於 **FRA05 - 法蘭克福**資料中心位置。
* SAP 認證及 Broadwell Bare Metal Server 不適用於 **LON05 - 倫敦**資料中心位置。

### Skylake
{: #vs_orderinginstances-skylake}

當您選取 **Skylake** 時，可以根據需求來為 Bare Metal Server 選擇 CPU 與 RAM 組合。可用的選項取決於您是否已選取 VMware vSAN 元件。

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon Silver 4110 處理器 / 總計 16 核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
{: caption="表 2. Skylake {{site.data.keyword.baremetal_short}} 的選項" caption-side="top"}

### SAP 認證
{: #vs_orderinginstances-sap}

如果您先前已選取 VMware vSAN，則無法使用 **SAP 認證**標籤。當您選取 **SAP 認證**時，無法變更 CPU 或 RAM 設定。

根據您的需求，選取 Bare Metal Server 配置：
  * 雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz / 192 GB RAM
  * 雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz / 384 GB RAM
  * 雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz / 768 GB RAM
  * 雙重 Intel Xeon E5-2690 v4 處理器 / 總計 28 核心，2.6 GHz / 512 GB RAM
  * 四重 Intel Xeon E7-8890 v4 處理器 / 總計 96 核心，2.2 GHz / 1024 GB RAM
  * 四重 Intel Xeon E7-8890 v4 處理器 / 總計 96 核心，2.2 GHz / 2048 GB RAM
  * 四重 Intel Xeon E7-8890 v4 處理器 / 總計 96 核心，2.2 GHz / 4096 GB RAM

### Broadwell
{: #vs_orderinginstances-broadwell}

當您選取 **Broadwell** 時，可以根據需求來為 Bare Metal Server 選擇 CPU 與 RAM 組合。可用的選項取決於您是否已選取 VMware vSAN 元件。

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|四重 Intel Xeon E7-4820 v4 / 總計 40 核心，2.0 GHz |128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
|四重 Intel Xeon E7-4850 v4 / 總計 64 核心，2.1 GHz |128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
{: caption="表 3. Broadwell {{site.data.keyword.baremetal_short}} 的選項" caption-side="top"}

### Bare Metal Server 數目
{: #vs_orderinginstances-bare-metal-number}

您要新增至 vSphere 叢集的 ESXi 伺服器數目。所有 ESXi 伺服器都有相同的配置。
* 如果您選取 VMware NSX 元件，則至少需要三部伺服器。
* 如果您選取 VMware vSAN 元件，則至少需要四部伺服器。

## 儲存空間設定
{: #vs_orderinginstances-storage-settings}

對於不包含 vSAN 的訂單，會訂購具有 12 磁碟機箱的 ESXi 伺服器，以及用於 ESXi 作業系統 (OS) 的兩個磁碟。

對於含有 vSAN 的訂單，會訂購具有 12 磁碟機箱的 ESXi 伺服器，並訂購四個磁碟：兩個用於 ESXi OS，兩個保留供快取使用。依預設會配置這些設定，且無法變更。您可以選取 **vSAN 容量磁碟的磁碟類型及大小**及 **vSAN 容量磁碟數目**，來訂購更多容量磁碟。

如果您選取叢集的 VMware vSAN 元件，請指定下列設定。
* **vSAN 容量磁碟的磁碟類型及大小**：選取所需容量磁碟的選項。
* **vSAN 容量磁碟數目**：指定您要新增的容量磁碟數目。
* 如果您要新增超過所限制的 8 個容量磁碟，請勾選**高效能 Intel Optane** 方框。這個選項提供 2 個額外容量磁碟機槽來放置共 10 個容量磁碟，並且適用於需要較少延遲且較高 IOPS 傳輸量的工作負載。

  **高效能 Intel Optane** 選項僅適用於 Skylake CPU 型號。
  {:note}

* 檢閱 **vSAN 快取磁碟的磁碟類型**及 **vSAN 快取磁碟數目**值。這些值取決於您是否已勾選**高效能 Intel Optane** 方框。

## 網路介面設定
{: #vs_orderinginstances-network-interface-settings}

當您訂購新的 vSphere 叢集時，必須指定下列網路介面設定。

### 主機名稱字首
{: #vs_orderinginstances-host-name-prefix}

主機名稱使用於所有裸機伺服器訂單。建議您對所有管理虛擬機器使用主機名稱（例如 vCenter Server 及 NSX）。

主機名稱字首必須滿足下列需求：
* 名稱的開頭及結尾必須是英數字元。
* 只容許英數及橫線 (-) 字元。
* 最大長度是 10 個字元。

### 子網域標籤
{: #vs_orderinginstances-subdomain-label}

子網域標籤必須滿足下列需求：
*  只容許英數及橫線 (-) 字元。
*  子網域標籤的開頭及結尾必須是英數字元。
*  子網域標籤的長度上限為 10 個字元。

### 網域名稱
{: #vs_orderinginstances-domain-name}

網域名稱使用於所有 {{site.data.keyword.baremetal_short}}，且必須滿足下列需求：
* 名稱必須包含兩個以上以句點 (.) 區隔的字串
* 只容許英數及橫線 (-) 字元。
* 每一個字串的開頭都必須是英文字母、結尾必須是英數字元，而最後一個字串只能包含英文字母。
* 最後一個字串的長度範圍必須在 2 到 24 個字元之間。
* 其他字串的長度必須在 1 - 63 個字元的範圍內。
* 網域名稱的長度上限為 189 個字元。

### 公用或專用網路
{: #vs_orderinginstances-public-private-network}

網路介面卡 (NIC) 啟用設定是根據您選取**公用及專用網路**或**僅限專用網路**而定。

### VLAN
{: #vs_orderinginstances-vlans}

網路設定是根據您選取**訂購新的 VLAN** 或**選取現有的 VLAN** 而定。

您的叢集訂單需要一個公用 VLAN 及兩個專用 VLAN。兩個專用 VLAN 成為每部 Bare Metal Server 的主幹。

#### 訂購新的 VLAN
{: #vs_orderinginstances-new-vlans}

選取訂購一個新的公用 VLAN 和兩個新的專用 VLAN。

#### 選取現有的 VLAN
{: #vs_orderinginstances-existing-vlans}

視您選取的 {{site.data.keyword.CloudDataCent_notm}} 而定，可能會提供現有的公用和專用 VLAN。

  當您選擇重複使用現有的公用及專用 VLAN 時，請指定 VLAN 及子網路：
  * **公用 VLAN** 適用於公用網路存取。
  * **專用 VLAN** 適用於 {{site.data.keyword.cloud_notm}} 內資料中心與服務之間的連線功能。
  * **次要專用 VLAN** 適用於 VMware 特性（例如 vSAN）。
  * **主要子網路**已指派給實體主機，以進行公用網路存取。
  * **主要專用子網路**已指派給實體主機，以處理管理資料流量。

##### 重要
{: #vs_orderinginstances-important}

* 確保所選取 VLAN 上的防火牆配置未封鎖管理資料流量。
* 確保您選取的所有 VLAN 都在相同的 Pod 中。無法在混合 Pod VLAN 上佈建 ESXi 伺服器。

#### FortiGate Physical Appliance 300 系列 HA 配對
{: #vs_orderinginstances-fortigate-physical-appliance}

您也可以選取是否包括「FortiGate Physical Appliance 300 系列 HA 配對」來保護雲端環境安全。如需相關資訊，請參閱 [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)。

## 訂單摘要
{: #vs_orderinginstances-order-summary}

根據您選取的配置，預估成本會立即產生並顯示在**訂單摘要**右窗格中。按一下**定價詳細資料**，以產生具有 {{site.data.keyword.vmwaresolutions_short}} 資源文件摘要的 PDF 文件。

您也可以按一下**新增至預估**，將佈建的資源新增至 {{site.data.keyword.cloud_notm}} 預估工具。這適用於您想要預估所選取 {{site.data.keyword.vmwaresolutions_short}} 資源與可能考慮購買之其他 {{site.data.keyword.cloud_notm}} 資源的成本時。

## 訂購 vSphere 叢集的程序
{: #vs_orderinginstances-procedure}

1. 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格上的 **VMware** 圖示，然後按一下 **VMware Services** 區段中的 **VMware vSphere on IBM Cloud** 卡。
2. 在 **VMware vSphere on IBM Cloud** 頁面上，按一下**建立**。  
   請確定您位於**建立新項目**標籤，並在**叢集配置**清單中顯示**新叢集**。
3. 輸入叢集名稱。
4. 選取 VMware 元件：
  * 如果您是「IBM 事業夥伴」，則請選取一個授權組合及任何其他可用的 VMware 元件。
  * 如果您是非「事業夥伴」，則請選取元件（如果有的話，則請選取版本），並指定授權選項。當您選擇針對 VMware vSphere Enterprise Plus「自帶授權 (BYOL)」時，會代表您自動開立 {{site.data.keyword.cloud_notm}} 問題單，要求將您訂購的 {{site.data.keyword.baremetal_short}} 上的預設 vSphere 授權取代為您提供的授權。   

    **重要事項：**您負責追蹤問題單，以在新訂購的 ESXi 伺服器上取代 vSphere 授權。因此 {{site.data.keyword.cloud_notm}} 基礎架構授權取消初始提供的 {{site.data.keyword.cloud_notm}} 基礎架構 vSphere 授權費。若要取代您的 ESXi vSphere 授權，請參閱[配置 ESXi 主機的授權設定](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:external}。
5. 完成 Bare Metal Server 設定：
   1. 選取 {{site.data.keyword.CloudDataCent_notm}} 來管理叢集。
   2. 選取 Bare Metal Server 配置。
      * 當您選取 **Skylake** 或 **Broadwell** 時，請指定 CPU 型號及 RAM 大小。
      * 當您選取 **SAP 認證**時，請選取其中一個預設配置。
   3. 指定 Bare Metal Server 數目。
6. 如果您選取 **VMware vSAN** 元件，請完成 vSAN 儲存空間配置。指定容量及快取磁碟的磁碟類型以及磁碟數目。如果您要更多儲存空間，請勾選**高效能 Intel Optane** 方框。
7. 完成網路介面設定：
   1. 輸入主機名稱字首、子網域標籤及網域名稱。
   2. 選取**公用及專用網路**或**僅限專用網路**的網路設定。
   3. 選取要使用的網路介面。
    * 如果您要訂購新的公用及專用 VLAN，則請按一下**訂購新的 VLAN**。
    * 如果您要重複使用可用的現有公用及專用 VLAN，則請按一下**選取現有的 VLAN**，然後指定 VLAN 及選用子網路。
    4. 指定是否套用「FortiGate Physical Appliance 300 系列 HA 配對」來保護雲端環境安全。  
8. 在**訂單摘要**窗格中，驗證叢集配置及預估成本。
   * 若要將配置儲存為範本而不下訂單，請按一下**儲存配置**。
   * 若要下訂單，請確定要收費的帳戶正確，請檢閱並接受條款，然後按一下**佈建**。

   僅安裝 {{site.data.keyword.baremetal_short}}。您負責在叢集部署之後安裝及配置各種元件，例如 VMware vCenter、VMware NSX、VMware vSAN。
   {:note}

### 訂購 vSphere 叢集後的結果
{: #vs_orderinginstances-results}

如果您將叢集配置儲存為範本，則會收到主控台通知，指出已順利儲存配置，然後您可以在**叢集配置**清單中找到該範本。

如果您已下訂單，則會自動啟動叢集的部署，且您會收到電子郵件確認，指出正在處理該訂單。當叢集已備妥可供使用時，會透過電子郵件通知您。

不同於 vCenter Server 實例，vSphere 叢集並不會顯示在**資源**頁面上。
{:note}

## 相關鏈結
{: #vs_orderinginstances-related}

* [根據現有配置來訂購 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [擴充現有的叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [擴充在主控台之外建立的叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
