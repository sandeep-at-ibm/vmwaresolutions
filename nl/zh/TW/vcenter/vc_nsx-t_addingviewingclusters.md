---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: vCenter Server NSX-T add cluster, view cluster vCenter Server NSX-T, delete cluster vCenter Server NSX-T

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 新增、檢視及刪除 vCenter Server with NSX-T 實例的叢集
{: #vc_nsx-t_addingviewingcluster}

您可以將您自己的叢集新增至 VMware vCenter Server with NSX-T 實例，以擴充運算和儲存空間容量。在叢集內，您可以管理 ESXi 伺服器，以進行更適當的資源配置及高可用性。不再需要時，請從實例刪除新增的叢集。

## 將叢集新增至 vCenter Server 實例
{: #vc_nsx-t_addingviewingclusters-adding}

### 新增叢集之前
{: #vc_nsx-t_addingviewingclusters-before-add}

* 盡可能使用 {{site.data.keyword.vmwaresolutions_full}} 主控台新增叢集，因為您在 VMware vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_short}} 主控台同步。因此，請只針對內部部署叢集或您在 {{site.data.keyword.vmwaresolutions_short}} 主控台中無法或不會管理的叢集，將叢集新增至 vCenter Server。
* 叢集、主機及虛擬機器 (VM) 的數目決定您可以新增的叢集數目上限。您必須遵守 VMware 大小準則及部署限制。如需上限的相關資訊，請參閱 [VMware 配置上限](https://configmax.vmware.com/home){:external}。

### 系統設定
{: #vc_nsx-t_addingviewingclusters-adding-sys-settings}

當您新增 vCenter Server with NSX-T 實例的叢集時，您必須指定下列設定。

#### 叢集名稱
{: #vc_nsx-t_addingviewingclusters-adding-cluster-name}

叢集名稱必須滿足下列需求：
* 只容許小寫英文字母、數字及橫線 (-) 字元。
* 叢集名稱的開頭必須是小寫英文字母。
* 叢集名稱的結尾必須是小寫英文字母或數值字元。
* 叢集名稱的長度上限為 30 個字元。
* 叢集名稱在 vCenter Server with NSX-T 實例內必須是唯一的。

#### 資料中心位置
{: #vc_nsx-t_addingviewingclusters-adding-dc-location}

依預設，叢集的 {{site.data.keyword.CloudDataCent}} 位置是設為 vCenter Server 實例的 {{site.data.keyword.CloudDataCent_notm}}。您可以將叢集部署至不同於已部署實例的 {{site.data.keyword.CloudDataCent_notm}}，但您必須確定兩個 {{site.data.keyword.CloudDataCents_notm}} 之間的網路延遲少於 150 毫秒。若要檢查網路延遲，您可以使用 [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass) 這類工具。

如果您將叢集部署至不同的 {{site.data.keyword.CloudDataCent_notm}} 或 {{site.data.keyword.cloud_notm}} 基礎架構 Pod，則會額外訂購三個 VLAN，以便與已訂購的 {{site.data.keyword.baremetal_short}} 搭配使用。

### Bare Metal Server 設定
{: #vc_nsx-t_addingviewingclusters-bare-metal-settings}

您可以選擇 **Skylake**、**Cascade** 或 **Broadwell**。

#### Skylake
{: #vc_nsx-t_addingviewingclusters-adding-skylake}

若為 **Skylake** 設定，您有數個選項可用於 **CPU 型號**及 **RAM**。可用的選項可能會根據一開始部署您實例所用的版本而不同。

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon Silver 4110 處理器 / 總計 16 核心，2.1 GHz| 128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，2.2 GHz| 128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz| 128 GB、192 GB、384 GB、768 GB、1.5 TB |
{: caption="表 1. Skylake {{site.data.keyword.baremetal_short}} 的選項" caption-side="top"}

#### Cascade
{: #vc_nsx-t_addingviewingclusters-adding-cascade}

若為 **Cascade** 設定，您有數個選項可用於 **CPU 型號**及 **RAM**。

Cascade {{site.data.keyword.baremetal_short}} 僅適用於 VMware vSphere Enterprise Plus 6.7 U2 實例。
{:note}

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon Gold 4210 處理器 / 總計 20 核心，2.3 GHz| 64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5218 處理器 / 總計 32 核心，2.3 GHz| 64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6248 處理器 / 總計 40 核心，2.5 GHz| 64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB |
{: caption="表 2. Cascade {{site.data.keyword.baremetal_short}} 的選項" caption-side="top"}

#### Broadwell
{: #vc_nsx-t_addingviewingclusters-adding-broadwell}

若為 **Broadwell** 設定，您有數個選項可用於 **CPU 型號**和 **RAM**。可用的選項可能會根據一開始部署您實例所用的版本而不同。

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|四重 Intel Xeon E7-4820 v4 / 總計 40 核心，1.9 GHz |128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
|四重 Intel Xeon E7-4850 v4 / 總計 64 核心，2.2 GHz |128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
{: caption="表 3. Broadwell {{site.data.keyword.baremetal_short}} 的選項" caption-side="top"}

#### Bare Metal Server 數目
{: #vc_nsx-t_addingviewingclusters-adding-bare-metal-number}

* 您訂購的所有伺服器都有相同的配置。
* 若為 vSAN 儲存空間，您可以訂購 4 到 59 部伺服器。
* 若為 NFS 儲存空間，您可以訂購 2 到 59 部伺服器。不過，對於正式作業工作負載，建議至少 3 部伺服器。如需相關資訊，請參閱[雙節點 vCenter Server 實例是否為高可用性？](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)。

### 儲存空間設定
{: #vc_nsx-t_addingviewingclusters-adding-storage-settings}

儲存空間設定是根據您選取的 Bare Metal Server 配置及儲存空間類型而定。

#### vSAN 儲存空間
{: #vc_nsx-t_addingviewingclusters-adding-vsan-storage}

請指定下列 vSAN 選項：
* **vSAN 容量磁碟的磁碟類型及大小**：選取所需容量磁碟的選項。
* **vSAN 容量磁碟數目**：指定您要新增的容量磁碟數目。
* 如果您要新增超過所限制的 10 個容量磁碟，請勾選**高效能 Intel Optane** 方框。這個選項提供 2 個額外容量磁碟機槽來放置共 12 個容量磁碟，並且適用於需要較少延遲且較高 IOPS 傳輸量的工作負載。

  **高效能 Intel Optane** 選項僅適用於 Skylake 及 Cascade CPU 型號。
  {:note}

* 檢閱 **vSAN 快取磁碟的磁碟類型**及 **vSAN 快取磁碟數目**值。這些值取決於您是否已勾選**高效能 Intel Optane** 方框。
* **vSAN 授權**：選取**購買隨附**以將 IBM 提供的 VMware 授權用於 vSAN 元件，也可以選取**我將提供**並輸入自己的授權碼以「自帶授權 (BYOL)」。

如果起始叢集是 vSAN 叢集，則任何額外的 vSAN 叢集都會使用相同的 vSAN 授權，且與起始 vSAN 叢集具有相同的配置。如果實例中的任何叢集都選擇在其上（起始或額外叢集）部署 vSAN，則也是這種情況。第一次系統會提示您提供 vSAN 授權（BYOL 或購買）及版本。下次為新叢集選取 vSAN 時，就會重複使用最初選擇的授權。

#### NFS 儲存空間
{: #vc_nsx-t_addingviewingclusters-adding-nfs-storage}

當您選取 **NFS 儲存空間**時，可以為所有共用使用相同設定的實例新增檔案層次共用儲存空間，也可以為每一個檔案共用指定不同的配置設定。請指定下列 NFS 選項：

檔案共用數目必須在 1 到 32 的範圍內。
{:note}

* **個別配置共用**：選取以為每一個檔案共用指定不同的配置設定。
* **共用數目**：要為每個檔案共用使用相同的配置設定時，請指定您要新增之 NFS 共用儲存空間的檔案共用數目。
* **大小**：選取符合共用儲存空間需求的容量。
* **效能**：根據您的工作負載需求，選取每 GB 的 IOPS（每秒輸入/輸出作業數）。
* **新增 NFS**：選取以新增要使用不同配置設定的個別檔案共用。

效能層次詳細資料：

|選項          |詳細資料     |
|:------------- |:------------- |
|0.25 IOPS/GB |這個選項是為未經常使用的工作負載而設計。應用的範例包括：加密配置檔資料、管理具有舊版資料的大型資料庫，或是作為備份之虛擬記憶體系統的虛擬磁碟映像檔。|
|2 IOPS/GB |這個選項是為大部分通用工作負載而設計。應用的範例包括：管理小型資料庫、備份 Web 應用程式，或是 Hypervisor 用的虛擬機器 (VM) 磁碟映像檔。|
|4 IOPS/GB |這個選項是為一次擁有高百分比作用中資料的高密度工作負載而設計。應用的範例包括：交易式資料庫。|
|10 IOPS/GB |這個選項是為要求最嚴苛的工作負載類型而設計，例如分析。應用的範例包括：高交易量資料庫，以及其他對效能敏感的資料庫。此效能層次限制為每個檔案共用的容量上限為 4 TB。|
{: caption="表 4. NFS 效能層次選項" caption-side="top"}

### 授權設定
{: #vc_nsx-t_addingviewingclusters-adding-licensing-settings}

指定叢集裡 VMware vSphere 元件的授權選項：
* 對於「事業夥伴」使用者，已包含 vSphere 授權（Enterprise Plus 版本），並代表您購買。
* 對於非「事業夥伴」使用者，您可以選取**購買隨附**以將 IBM 提供的 VMware 授權用於此元件，也可以選取**我將提供**並輸入自己的授權碼以「自帶授權 (BYOL)」。

### 網路介面設定
{: #vc_nsx-t_addingviewingclusters-adding-network-interface-settings}

網路介面卡 (NIC) 啟用設定是根據您選取**公用及專用網路**或**僅限專用網路**而定。

### 訂單摘要
{: #vc_nsx-t_addingviewingclusters-adding-order-summary}

根據您選取的叢集配置，預估成本會立即產生並顯示在**訂單摘要**右窗格中。按一下**定價詳細資料**，以產生具有 {{site.data.keyword.vmwaresolutions_short}} 資源文件摘要的 PDF 文件。

您也可以按一下**新增至預估**，將佈建的資源新增至 {{site.data.keyword.cloud_notm}} 預估工具。這適用於您想要預估所選取 {{site.data.keyword.vmwaresolutions_short}} 資源與可能考慮購買之其他 {{site.data.keyword.cloud_notm}} 資源的成本時。

## 將叢集新增至 vCenter Server with NSX-T 實例的程序
{: #vc_nsx-t_addingviewingclusters-adding-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要新增叢集的實例。

   請確定實例處於**備妥使用**狀態。否則，您無法將叢集新增至實例。
   {:note}
3. 按一下左導覽窗格上的**基礎架構**，然後按一下**叢集**表格右上角的**新增**。
4. 在**新增叢集**頁面上，輸入叢集名稱。
5. 如果您要在與實例管理所在不同的 {{site.data.keyword.CloudDataCent_notm}} 中管理叢集，請勾選 **Bare Metal Server** 下的**選取不同的位置**勾選框，然後選擇 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。
6. 完成 Bare Metal Server 配置。指定 **CPU 模型**、**RAM** 數量，以及 **{{site.data.keyword.baremetal_short}} 數目**。
7. 完成儲存空間配置。
  * 如果您選取 **vSAN 儲存空間**，請指定容量及快取磁碟的磁碟類型、磁碟數目以及「vSAN 授權」版本。如果您要更多儲存空間，請勾選**高效能 Intel Optane** 方框。
  * 如果您選取 **NFS 儲存空間**，而且要對所有檔案共用新增及配置相同的設定，請指定**共用數目**、**效能**及**大小 (GB)**。
  * 如果您選取 **NFS 儲存空間**，而且要個別新增及配置檔案共用，請選取**個別配置共用**。然後，按一下**新增共用儲存空間**標籤旁的 **+** 圖示，並針對每個檔案共用選取**效能**及**大小 (GB)**。您必須至少選取一個檔案共用。
8. 完成網路介面設定。
8. 指定如何提供 vSphere 授權碼：
  * 對於「事業夥伴」使用者，已包含 vSphere 授權（Enterprise Plus 版本），並代表您購買。
  * 對於非「事業夥伴」的使用者，您可以選取下列其中一個選項：
      * 如果您想要我們代表您購買新授權，請針對元件選取**購買隨附**。
      * 如果您要針對元件使用自己的 VMware 授權，請選取**我將提供**，並輸入授權碼。
9. 選取**公用及專用網路**或**僅限專用網路**的網路設定。
10. 在**訂單摘要**窗格上，先驗證叢集配置，再新增叢集。
   1. 檢閱叢集的設定。
   2. 檢閱預估的叢集成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
   3. 按一下適用於您訂單的條款鏈結，並先確認您同意這些條款，再新增叢集。
   4. 按一下**佈建**。

### 將叢集新增至 vCenter Server with NSX-T 實例之後的結果
{: #vc_nsx-t_addingviewingclusters-adding-results}

1. 會自動啟動叢集的部署，而且叢集的狀態變更為**正在起始設定**。您可以從實例的**摘要**頁面檢視部署歷程，以檢查部署的狀態。
2. 叢集備妥可用時，其狀態會變更為**備妥使用**。新增的叢集已啟用「vSphere 高可用性 (HA)」及「vSphere 分散式資源排程器 (DRS)」。

您不能變更叢集名稱。變更叢集名稱可能會導致在叢集裡新增或移除 ESXi 伺服器的作業失敗。
{:important}

## 檢視 vCenter Server with NSX-T 實例中的叢集的程序
{: #vc_nsx-t_addingviewingclusters-viewing-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
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
  * **動作**：按一下**刪除**圖示，以刪除叢集。
4. 按一下叢集名稱來檢視 ESXi 伺服器、儲存空間和網路介面詳細資料：

|項目        |說明       |  
|:------------- |:------------- |
|名稱 |ESXi 伺服器的名稱格式如下：`<data_center>-<host_prefix><n>.<subdomain_label>.<root_domain>`，其中 `n` 是 ESXi 伺服器序列。|
|版本|ESXi 伺服器的版本。|
|認證|用來存取 ESXi 伺服器的使用者名稱和密碼。|
|專用 IP |ESXi 伺服器的專用 IP 位址。|
|狀態|ESXi 伺服器的狀態，可以是下列其中一個值：<br> **已新增** ESXi 伺服器已完成新增並已備妥可供使用。<br> **正在新增** 正在新增 ESXi 伺服器。<br> **正在刪除** 正在刪除 ESXi 伺服器。|
{: caption="表 5. ESXi 伺服器詳細資料" caption-side="top"}

檢視儲存空間詳細資料：

|項目        |說明              |  
|:------------- |:------------- |
|名稱 |資料儲存庫名稱。|
|大小|儲存空間的容量。|
| IOPS/GB |儲存空間的效能層次。|
| NFS 通訊協定| 儲存空間的 NFS 版本。|
{: caption="表 6. 儲存空間詳細資料" caption-side="top"}

檢視網路介面詳細資料：

|項目        |說明       |  
|:------------- |:------------- |
| VLAN 號碼 | 唯一的 VLAN 號碼。 |
|說明              | VLAN 的說明。|
|位置| 資料中心位置。 |
| 主要路徑 | VLAN 的主要路徑。 |
{: caption="表 7. 網路介面 - VLAN 詳細資料" caption-side="top"}

按一下**檢視資源**來存取 VLAN 詳細資料。

檢視子網路詳細資料：

|項目        |說明              |  
|:------------- |:------------- |
|名稱 | 子網路名稱。按一下名稱來存取子網路詳細資料。|
|類型      | 子網路的類型：主要或可攜式。 |
|說明              | 子網路的說明。|
{: caption="表 8. 網路介面 - 子網路詳細資料" caption-side="top"}

檢視 IP 詳細資料：

|項目        |說明              |  
|:------------- |:------------- |
| IP    | IP 位址。 |
|狀態| IP 位址的狀態。 |
|說明              |IP 位址的說明。|
{: caption="表 9. 網路介面 - IP 詳細資料" caption-side="top"}

## 從 vCenter Server with NSX-T 實例刪除叢集
{: #vc_nsx-t_addingviewingclusters-deleting}

不再需要叢集時，即可從實例刪除叢集。

### 刪除之前
{: #vc_nsx-t_addingviewingclusters-deleting-prereq}

* 盡可能使用 {{site.data.keyword.vmwaresolutions_full}} 主控台刪除叢集，因為您在 VMware vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_short}} 主控台同步。因此，請只針對內部部署叢集或您在 {{site.data.keyword.vmwaresolutions_short}} 主控台中無法或不會管理的叢集，刪除 vCenter Server 中的叢集。
* 您一次可以刪除單一叢集。若要刪除多個叢集，您必須依序進行。請等待前一個叢集刪除後，再刪除下一個叢集。
* 在您刪除叢集之前，請確定叢集裡的所有節點都已開啟電源且正常運作。
* 當您刪除叢集時，也會一併刪除叢集中的所有 VM，且無法回復。如果您要保留 VM，請將它們移轉至其他叢集。
* 無法刪除預設叢集。

### 從 vCenter Server with NSX-T 實例刪除叢集的程序
{: #vc_nsx-t_addingviewingclusters-deleting-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要從中刪除叢集的實例。

   請確定實例處於**備妥使用**狀態。否則，您無法從實例刪除叢集。
   {:note}

3. 在左導覽窗格上，按一下**基礎架構**。在**叢集**表格中，找出您要刪除的叢集，然後按一下**動作**直欄中的**刪除**圖示。
4. 確認您已完成將 VM 移轉至其他叢集（必要的話），以及您要刪除叢集。

## 相關鏈結
{: #vc_nsx-t_addingviewingclusters-related}

* [檢視 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [擴充及縮減 vCenter Server with NSX-T 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
