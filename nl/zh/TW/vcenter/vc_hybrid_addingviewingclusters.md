---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# 新增、檢視及刪除 vCenter Server with Hybridity Bundle 實例的叢集

依預設，您訂購實例時所配置的 ESXi 伺服器會分組為 **cluster1**。

您可以將叢集新增至 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 實例，以擴充運算及儲存空間容量。在叢集內，管理 ESXi 伺服器，以進行更適當的資源配置及高可用性。不再需要時，請從實例刪除新增的叢集。

## 將叢集新增至 vCenter Server with Hybridity Bundle 實例

您最多可以將 10 個叢集新增至 vCenter Server with Hybridity Bundle 實例。

### 系統設定

新增 vCenter Server with Hybridity Bundle 實例的叢集時，您必須指定下列設定。

#### 叢集名稱

叢集名稱必須符合下列需求：
* 只容許英數及橫線 (-) 字元。
* 叢集名稱的開頭及結尾必須是英數字元。
* 叢集名稱的長度上限為 30 個字元。
* 叢集名稱在 vCenter Server with Hybridity Bundle 實例內必須是唯一的。

#### 資料中心位置

依預設，叢集的 {{site.data.keyword.CloudDataCent_notm}} 位置是設為 vCenter Server 實例的 {{site.data.keyword.CloudDataCent_notm}}。您可以將叢集部署至不同於已部署實例的 {{site.data.keyword.CloudDataCent_notm}}，但您必須確定兩個 {{site.data.keyword.CloudDataCents_notm}} 之間的網路延遲少於 150 毫秒。若要檢查網路延遲，請使用 [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} 這類工具。

如果您將叢集部署至不同的 {{site.data.keyword.CloudDataCent_notm}} 或 {{site.data.keyword.cloud_notm}} 基礎架構 Pod，則會訂購其他三個 VLAN，以與已訂購的 {{site.data.keyword.baremetal_short}} 搭配使用。

### Bare Metal Server 設定

#### 自訂

指定 Bare Metal Server 的 CPU 型號及 RAM。可用的選項可能會根據一開始部署您實例所用的版本而不同。

表 2. 自訂的 Bare Metal Server 選項

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon E5-2620 v4 / 總計 16 核心，2.1 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2650 v4 / 總計 24 核心，2.2 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2690 v4 / 總計 28 核心，2.6 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz |96 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Silver 4110 處理器 / 總計 16 核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz |64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

#### Bare Metal Server 數目

一個叢集至少需要兩部 {{site.data.keyword.baremetal_short}}。

您可以針對叢集新增最多 59 部 {{site.data.keyword.baremetal_short}}，並且一次可以新增 1 到 59 部 ESXi 伺服器。

部署之後，您最多可以建立另外四個叢集。對於 VMware vSAN 儲存空間，起始叢集及部署後的叢集都需要四部伺服器。

### vSAN 儲存空間設定

vCenter Server with Hybridity Bundle 實例訂單隨附 VMware vSAN 6.6。請指定下列 vSAN 選項：
* **vSAN 容量磁碟的磁碟類型及大小**：選取所需容量磁碟的選項。
* **vSAN 容量磁碟數目**：指定您要新增的容量磁碟數目。
* 如果您要新增超過限制 8 個的容量磁碟，請勾選**高效能 Intel Optane** 方框。這個選項提供 2 個額外容量磁碟機槽來放置共 10 個容量磁碟，並且適用於需要較少延遲且較高 IOPS 傳輸量的工作負載。**高效能 Intel Optane** 選項僅適用於雙重 Intel Xeon Gold 5120 及 6140 處理器。

* 檢閱 **vSAN 快取磁碟的磁碟類型**及 **vSAN 快取磁碟數目**值。這些值取決於您是否已勾選**高效能 Intel Optane** 方框。
* **vSAN 授權**：選取 VMware vSAN 6.6 授權版本（Advanced 或 Enterprise）。

### 授權設定

由 IBM 提供的下列 VMware 元件授權：
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4（Advanced 或 Enterprise 版本）

### 網路介面設定

網路介面卡 (NIC) 設定是根據您選取**公用及專用網路**或**僅限專用網路**而定。下列附加程式服務需要公用 NIC，而且在使用專用選項時無法使用：

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### 訂單摘要

根據您選取的叢集配置，預估成本會立即產生並顯示在**訂單摘要**右窗格中。

## 將叢集新增至 vCenter Server with Hybridity Bundle 實例的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下實例來檢視其中的叢集。

   **附註：**請確定實例狀態處於**備妥使用**。否則，您無法將叢集新增至實例。

3. 按一下左導覽窗格上的**基礎架構**，然後按一下**叢集**表格右上角的**新增**。
4. 在**新增叢集**頁面上，輸入叢集名稱。
5. 您可以在與實例管理所在不同的 {{site.data.keyword.CloudDataCent_notm}} 中管理叢集。若要這樣做，請勾選 **Bare Metal Server** 下的**選取不同的位置**勾選框，然後選擇 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。
6. 針對 Bare Metal Server 配置，選取 **CPU 型號**、**RAM** 數量及 **Bare Metal Server 數目**。
7.  選取 **vSAN 儲存空間**，然後指定容量及快取磁碟的磁碟類型以及磁碟數目。如果您要更多儲存空間，請勾選**高效能 Intel Optane** 方框。
8. 選取授權配置的 VMware vSAN 授權版本。
9. 選取**公用及專用網路**或**僅限專用網路**的網路設定。
10. 在**訂單摘要**窗格上，先驗證叢集配置，再新增叢集。
   1. 檢閱叢集的設定。
   2. 檢閱預估的叢集成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
   3. 按一下適用於您訂單的條款鏈結，並先確定您同意這些條款，再新增叢集。
   4. 按一下**佈建**。

### 將叢集新增至 vCenter Server with Hybridity Bundle 實例之後的結果

1. 會自動啟動叢集的部署，而且叢集的狀態變更為**正在起始設定**。您可以在實例的**摘要**頁面上檢視部署歷程，以檢查部署的狀態。
2. 叢集備妥可用時，其狀態會變更為**備妥使用**。新增的叢集已啟用「vSphere 高可用性 (HA)」及「vSphere 分散式資源排程器 (DRS)」。

**重要事項：**您不能變更叢集名稱。變更叢集名稱可能會導致在叢集裡新增或移除 ESXi 伺服器的作業失敗。

## 檢視 vCenter Server with Hybridity Bundle 實例中叢集的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下實例來檢視其中的叢集。
3. 在左導覽窗格上，按一下**基礎架構**。在**叢集**表格中，檢視叢集的摘要：
  * **名稱**：叢集的名稱。
  * **ESXi 伺服器**：叢集裡的 ESXi 伺服器數目。
  * **CPU**：叢集裡 ESXi 伺服器的 CPU 規格。
  * **自訂 vSAN 磁碟**：叢集裡的 vSAN 磁碟數目（包括磁碟類型及容量）。
  * **記憶體**：叢集裡 ESXi 伺服器的記憶體大小總計。
  * **資料中心位置**：管理叢集所在的 {{site.data.keyword.CloudDataCent_notm}}。
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
4. 按一下叢集名稱，以檢視 ESXi 伺服器及儲存空間的詳細資料：

  * ESXi 伺服器詳細資料：
     * **名稱**：ESXi 伺服器的名稱格式為 `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中：

       `host_prefix` 是主機名稱字首、

       `n` 是伺服器序列、

       `subdomain_label` 是子網域標籤，而

       `root_domain` 是根網域名稱。

     * **版本**：ESXi 伺服器的版本。
     * **認證**：用來存取 ESXi 伺服器的使用者名稱及密碼。
     * **專用 IP**：ESXi 伺服器的專用 IP 位址。
     * **狀態**：ESXi 伺服器的狀態，可以是下列其中一個值：
        <dl class="dl">
        <dt class="dt dlterm">已新增</dt>
        <dd class="dd">已新增 ESXi 伺服器，且已備妥可供使用。</dd>
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

## 從 vCenter Server with Hybridity Bundle 實例刪除叢集

不再需要叢集時，即可從實例刪除叢集。

### 刪除之前

* 您一次可以刪除單一叢集。若要刪除多個叢集，您必須依序執行它；請等待前一個叢集刪除後，再刪除下一個叢集。
* 在您刪除叢集之前，請確定叢集裡的所有節點都已開啟電源且正常運作。
* 當您刪除叢集時，也會一併刪除叢集裡的所有 VM（虛擬機器），且無法回復。如果您要保留 VM，請將它們移轉至其他叢集。
* 無法刪除預設叢集。

## 從 vCenter Server with Hybridity Bundle 實例刪除叢集的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要從中刪除叢集的實例。

   **附註：**請確定實例處於**備妥使用**狀態。否則，您無法從實例移除叢集。

3. 在左導覽窗格上，按一下**基礎架構**。在**叢集**表格中，找出您要刪除的叢集，然後按一下**動作**直欄中的**刪除**圖示。

### 相關鏈結

* [檢視 vCenter Server with Hybridity Bundle 實例](vc_hybrid_viewinginstances.html)
* [擴充及縮減 vCenter Server with Hybridity Bundle 實例的容量](vc_hybrid_addingremovingservers.html)
