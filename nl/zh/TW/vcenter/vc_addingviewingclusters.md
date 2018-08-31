---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-02"

---

# 新增、檢視及刪除 vCenter Server 實例的叢集

依預設，您訂購實例時所配置的 ESXi 伺服器會分組為 **cluster1**。

您可以將自己的叢集新增至 VMware vCenter Server 實例，以擴充運算及儲存空間容量。在叢集內，您可以管理 ESXi 伺服器，以進行更適當的資源配置及高可用性。不再需要時，您可以從實例中刪除新增的叢集。

**可用性**：只有部署在（或升級至）2.3 版及更新版本的實例，才能使用刪除叢集特性。

## 將叢集新增至 vCenter Server 實例

可新增至實例的叢集數目視實例版本而定：
* 對於已部署在（或升級至）2.2 版及更新版本的實例，您最多可以新增 10 個叢集。
* 對於已部署在 2.2 版或更早版本的實例，您最多可以新增 5 個叢集。

### 系統設定

新增 vCenter Server 實例的叢集時，您必須指定下列設定。

#### 叢集名稱

叢集名稱必須符合下列需求：
* 只容許英數及橫線 (-) 字元。
* 叢集名稱的開頭及結尾必須是英數字元。
* 叢集名稱的長度上限為 30 個字元。
* 叢集名稱在 vCenter Server 實例中必須是唯一的。

#### 資料中心位置

依預設，叢集的 {{site.data.keyword.CloudDataCent}} 位置是設為 vCenter Server 實例的 {{site.data.keyword.CloudDataCent_notm}}。您可以將叢集部署至不同於已部署實例的 {{site.data.keyword.CloudDataCent_notm}}，但您必須確定兩個 {{site.data.keyword.CloudDataCents_notm}} 之間的網路延遲少於 150 毫秒。若要檢查網路延遲，您可以使用 [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} 之類的工具。

如果您將叢集部署至不同的 {{site.data.keyword.CloudDataCent_notm}} 或 {{site.data.keyword.cloud_notm}} 基礎架構 pod，則會訂購另外三個 VLAN，以便與已訂購的 {{site.data.keyword.baremetal_short}} 搭配使用。

### Bare Metal Server 設定

您可以選擇**預先配置**或**自訂**。

#### 預先配置

對於**預先配置**設定，您可以根據需求選擇 **Bare Metal Server 配置**：
* 小型（雙重 Intel Xeon E5-2620 v4 /總計 16 核心，2.1 GHz / 128 GB RAM / 2 個磁碟）
* 中型（雙重 Intel Xeon E5-2650 v4 /總計 24 核心，2.2 GHz / 256 GB RAM / 2 個磁碟）
* 大型（雙重 Intel Xeon E5-2690 v4 /總計 28 核心，2.6 GHz / 512 GB RAM  /2 個磁碟）

#### 自訂

對於**自訂**設定，您有數個 **CPU 型號**及 **RAM** 選項。根據一開始部署您實例的版本，可用的選項可能會不同。

表 1. 自訂 {{site.data.keyword.baremetal_short}} 的選項

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon E5-2620 v4 /總計 16 核心，2.1 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2650 v4 /總計 24 核心，2.2 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2690 v4 /總計 28 核心，2.6 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Silver 4110 處理器/總計 16 核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器/總計 28 核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 Processor / 總計 36 核心，2.3 GHz |64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

#### Bare Metal Server 數目

一個叢集至少需要兩部 {{site.data.keyword.baremetal_short}}。

對於在 2.1 版或更新版本中部署的 vCenter Server 實例，您可以針對叢集新增最多 59 部 {{site.data.keyword.baremetal_short}}，並且一次可以新增 1 到 59 部 ESXi 伺服器。

對於已部署在 2.0 版或更早版本的 vCenter Server 實例，您最多可以為叢集新增 32 部 {{site.data.keyword.baremetal_short}}。您一次可以新增的 {{site.data.keyword.baremetal_short}} 數目如下所示：
* 如果是**小型**、**中型**、**大型** Bare Metal Server 配置，您一次可以新增 1 - 10 部 ESXi 伺服器。
* 如果是**自訂** Bare Metal Server 配置，您一次可以新增 1 - 20 部 ESXi 伺服器。

部署之後，您最多可以建立另外四個叢集。如果您選取**自訂** Bare Metal Server 配置搭配 VMware vSAN 儲存空間，則起始叢集和後置部署叢集都需要 4 部伺服器。

### 儲存空間設定

儲存空間設定是根據您選取的 Bare Metal Server 配置及儲存空間類型而定。

#### vSAN 儲存空間

vSAN 僅適用於自訂 Bare Metal Server 配置。您可以指定符合您儲存空間需求的 vSAN 容量磁碟數目（2、4、6 或 8）、磁碟類型和大小以及 vSAN 授權選項，來自訂 VMware vSAN 儲存空間。

如果起始叢集是 vSAN 叢集，則任何其他 vSAN 叢集都使用相同的 vSAN 授權，且與起始 vSAN 叢集具有相同的配置。如果實例中的任何叢集都選擇部署 vSAN（起始或其他），則也是這種情況。第一次會提示您提供 vSAN 授權（BYOL 或購買）和版本。下次選取 vSAN 作為其他叢集時，就會重複使用最初選擇的授權。

#### NFS 儲存空間

當您選取 **NFS 儲存空間**時，可以為實例新增所有共用相同設定的檔案層次共用儲存空間，也可以為每一個檔案共用指定不同的配置設定。請指定下列 NFS 選項：

**附註：**檔案共用數目必須在 1 到 32 的範圍內。

* **個別配置共用**：選取以指定每一個檔案共用的不同配置設定。
* **共用數目**：使用每一個檔案共用的相同配置設定時，請指定您要新增之 NFS 共用儲存空間的檔案共用數目。
* **大小**：選取符合共用儲存空間需求的容量。
* **效能**：根據您的工作負載需求，選取每 GB IOPS（每秒輸入/輸出作業數）。
* **新增 NFS**：選取以新增將使用不同配置設定的個別檔案共用。

表 2. NFS 效能層次選項

|選項          |詳細資料      |
  |:------------- |:------------- |
  |2 IOPS/GB |這個選項是為大部分通用工作負載而設計。應用的範例包括：管理小型資料庫、備份 Web 應用程式，或是 Hypervisor 用的虛擬機器磁碟映像檔。|
  |4 IOPS/GB |這個選項是為一次擁有高百分比作用中資料的高密度工作負載而設計。應用的範例包括：交易式資料庫。|
  |10 IOPS/GB |這個選項是為需求最大的工作負載類型而設計，例如分析。應用的範例包括：高交易量資料庫，以及其他對效能敏感的資料庫。此效能層次限制為每個檔案共用的容量上限為 4 TB。|

### 授權設定

指定叢集中 VMware vSphere 元件的授權選項：
* 對於「事業夥伴」使用者，包括 vSphere 授權（Enterprise Plus 版本），並可代表您購買。
* 對於非「事業夥伴」使用者，您可以選取**購買隨附**以將 IBM 提供的 VMware 授權用於此元件，也可以選取**我將提供**並輸入自己的授權碼以「自帶授權 (BYOL)」。

### 訂單摘要

根據您選取的叢集配置，預估成本會立即產生並顯示在**訂單摘要**右窗格中。

## 將叢集新增至 vCenter Server 實例的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要新增叢集的實例。

   **附註**：請確定實例處於**備妥使用**狀態。否則，您無法將叢集新增至實例。

3. 按一下左導覽窗格上的**基礎架構**，然後按一下 **CLUSTERS** 表格右上角的**新增**。
4. 在**新增叢集**頁面上，輸入叢集名稱。
5. 如果您要在與實例管理所在不同的 {{site.data.keyword.CloudDataCent_notm}} 中管理叢集，請勾選 **Bare Metal Server** 下的**選取不同的位置**勾選框，然後選擇 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。
6. 完成 Bare Metal Server 配置。
   * 如果您選取**預先配置**，請指定 **Bare Metal Server 配置**，以及 **{{site.data.keyword.baremetal_short}} 數目**。如果您打算使用 vSAN 作為儲存空間解決方案，請注意，至少需要 4 部 {{site.data.keyword.baremetal_short}}。
   * 如果您選取**自訂**，請指定 **CPU 型號**、**RAM** 數量，以及**{{site.data.keyword.baremetal_short}}數目**。
7. 完成儲存空間配置。
  * 當您選取 **vSAN 儲存空間**時，請指定 **vSAN 容量磁碟的磁碟類型及大小**、**vSAN 容量磁碟數目**，以及如何提供 **vSAN 授權**。
  * 當您選取 **NFS 儲存空間**且想要對所有檔案共用新增及配置相同的設定時，請指定**共用數目**、**大小**及**效能**。
  * 當您選取 **NFS 儲存空間**且想要個別新增及配置檔案共用時，請選取**個別配置共用**，然後按一下**新增 NFS** 標籤旁的 **+** 圖示，並針對每一個個別檔案共用選取**大小**及**效能**。您必須至少選取一個檔案共用。
8. 指定如何提供 vSphere 授權碼：
  * 對於「事業夥伴」使用者，包括 vSphere 授權（Enterprise Plus 版本），並可代表您購買。
  * 對於非「事業夥伴」使用者，您可以選取下列其中一個選項：
      * 如果您想要我們代表您購買新授權，請針對元件選取**購買隨附**。
      * 如果您要針對元件使用自己的 VMware 授權，則請選取**我將提供**，並輸入其授權碼。
9. 在**訂單摘要**窗格上，先驗證叢集配置，再新增叢集。
   1. 檢閱叢集的設定。
   2. 檢閱預估的叢集成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
   3. 按一下適用於您訂單的條款鏈結，並先確定您同意這些條款，再新增叢集。
   4. 按一下**佈建**。

### 將叢集新增至 vCenter Server 實例之後的結果

1. 會自動啟動叢集的部署，而且叢集的狀態變更為**正在起始設定**。您可以從實例的**摘要**頁面檢視部署歷程，以檢查部署的狀態。
2. 叢集備妥可用時，其狀態會變更為**備妥使用**。新增的叢集已具有「vSphere 高可用性 (HA)」及「vSphere 分散式資源排程器 (DRS)」。

**重要事項**：您不能變更叢集名稱。變更叢集名稱可能會導致在叢集中新增或移除 ESXi 伺服器的作業失敗。

## 檢視 vCenter Server 實例中的叢集

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下實例來檢視其中的叢集。
3. 在左導覽窗格上，按一下**基礎架構**。在 **CLUSTERS** 表格中，檢視叢集的摘要：
  * **名稱**：叢集的名稱。
  * **ESXi 伺服器**：叢集中的 ESXi 伺服器數目。
  * **CPU**：叢集中 ESXi 伺服器的 CPU 規格。
  * **自訂 vSAN 磁碟**：叢集中的 vSAN 磁碟數目（包括磁碟類型及容量）。
  * **記憶體**：叢集中 ESXi 伺服器的總記憶體大小。
  * **資料中心位置**：管理叢集的 {{site.data.keyword.CloudDataCent_notm}}。
  * **Pod**：部署叢集的 Pod。
  * **狀態**：叢集的狀態。狀態可以具有下列其中一個值：
    <dl class="dl">
        <dt class="dt dlterm">正在起始設定</dt>
        <dd class="dd">正在建立及配置叢集。</dd>
        <dt class="dt dlterm">正在修改</dt>
        <dd class="dd">正在修改叢集。</dd>
        <dt class="dt dlterm">備妥使用</dt>
        <dd class="dd">叢集已備妥可供使用。</dd>
        <dt class="dt dlterm">正在刪除</dt>
        <dd class="dd">正在刪除叢集。</dd>
        <dt class="dt dlterm">已刪除</dt>
        <dd class="dd">已刪除叢集。</dd>
    </dl>
  * **動作**：按一下**刪除**圖示，以刪除叢集。
4. 按一下叢集名稱，以檢視 ESXi 伺服器及儲存空間的詳細資料：

  * ESXi 伺服器詳細資料：
     * **名稱**：ESXi 伺服器的名稱格式為 `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中：

       `host_prefix` 是主機名稱字首、

       `n` 是伺服器序列、

       `subdomain_label` 是子網域標籤，而

       `root_domain` 是根網域名稱。

     * **版本**：ESXi 伺服器的版本。
     * **認證**：存取 ESXi 伺服器的使用者名稱及密碼。
     * **專用 IP**：ESXi 伺服器的專用 IP 位址。
     * **狀態**：ESXi 伺服器的狀態，可以是下列其中一個值：
        <dl class="dl">
        <dt class="dt dlterm">已新增</dt>
        <dd class="dd">已新增 ESXi 伺服器，且隨時可用。</dd>
        <dt class="dt dlterm">正在新增</dt>
        <dd class="dd">正在新增 ESXi 伺服器。</dd>
        <dt class="dt dlterm">正在刪除</dt>
        <dd class="dd">正在刪除 ESXi 伺服器。</dd>
        </dl>
  * 儲存空間詳細資料：
    * **名稱**：資料儲存庫名稱。
    * **大小**：儲存空間的容量。
    * **IOPS/GB**：儲存空間的效能層次。
    * **NFS 通訊協定**：儲存空間的 NFS 版本。

## 從 vCenter Server 實例中刪除叢集

不再需要叢集時，即可從實例中刪除叢集。

### 刪除之前

* 使用此程序，從部署在 2.3 版或更新版本的實例中刪除叢集。
* 對於部署在 2.2 版或更早版本實例的叢集，您必須將實例升級至 2.3 版，才能刪除您新增至實例的叢集。
* 您一次可以刪除單一叢集。若要刪除多個叢集，您必須依序執行它；請先等待刪除前一個叢集，再嘗試刪除下一個叢集。
* 刪除叢集之前，請確定叢集中的所有節點都已開啟電源且正常運作。
* 當您刪除叢集時，也會一併刪除叢集中的所有 VM（虛擬機器），且無法回復。如果您要保留 VM，請將它們移轉至其他叢集。
* 無法刪除預設叢集。

## 從 vCenter Server 實例中刪除叢集的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要從中刪除叢集的實例。

   **附註**：請確定實例處於**備妥使用**狀態。否則，您無法從實例中刪除叢集。

3. 在左導覽窗格上，按一下**基礎架構**。在 **CLUSTERS** 表格中，找出您要刪除的叢集，然後按一下**動作**直欄中的**刪除**圖示。
4. 確認您已完成將虛擬機器移轉至其他叢集（必要的話），以及您要刪除叢集。

### 相關鏈結

* [檢視 vCenter Server 實例](vc_viewinginstances.html)
* [擴充及縮減 vCenter Server 實例的容量](vc_addingremovingservers.html)
