---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-28"

subcollection: vmwaresolutions


---

# 叢集設定
{: #cluster-settings}

在新增連接儲存空間之前，vCenter Server 解決方案並未啟用進階特性，例如「vSphere 分散式資源排程器 (DRS)」和「vSphere 高可用性 (HA)」。新增 NFS 連接儲存空間裝置之後，這些特性會在叢集上啟用，並使用下列幾節所列出的設定。

## vSphere 分散式資源排程器
{: #cluster-settings-vsphere-drs}

在叢集上開啟 vSphere DRS 之後，會啟用兩個主要特性：「負載平衡」及「電源管理」。

###  負載平衡           
{: #cluster-settings-load-balance}

透過負載平衡，叢集裡所有主機和虛擬機器 (VM) 的 CPU 和記憶體資源的分配與使用，會持續受到監視。DRS 將這些度量值與理想資源使用進行比較，並且會考量叢集資源儲存區和 VM，以及現行需求。然後它會視需要完成或建議 VM 移轉。

當 VM 第一次在叢集中開啟電源時，DRS 會將 VM 放置在適當的主機上或提出建議，嘗試維護適當的負載平衡。放置或建議的設定，是設定在叢集設定的「DRS 自動化」區段中。

在本設計中，「DRS 自動化」層次會設定為全自動，因此當 VM 開啟電源時，它們會自動放置於具有足夠容量的主機上。VM 也會從一部主機自動移轉至另一部主機，使叢集負載平衡。此外，DRS 叢集的移轉臨界值是設定在保守與激進兩者的中間點，例如，會套用優先順序 1、優先順序 2 和優先順序 3 的建議。vCenter Server 對叢集的負載平衡至少提供不錯的改善。

下表顯示在 VMware vSphere Web Client 中的 vSphere DRS 叢集設定。

表 1. vSphere DRS 叢集的 DRS 自動化設定

| 設定          | 值  |
|:------------------- |:------ |
| 開啟 vSphere DRS | 已選取|
| 自動化層次 | 全自動|
| 移轉臨界值 | 套用優先順序 1、優先順序 2 及優先順序 3 的建議 |
| 啟用個別機器自動化層次 | 已選取，設為 15 毫秒 |

如需在 vSphere Web Client 中配置這些設定的相關資訊，請參閱 [Set a Custom Automation Level for a Virtual Machine in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-C21C0609-923B-46FB-920C-887F00DBCAB9.html)。

除了叢集的自動化層次和移轉臨界值之外，本設計也會啟用 VM 自動化，讓您可以置換每部個別 VM 的值。更精細地控制 VM 可以進一步設定 VM 負載平衡的優先順序。

### 電源管理
{: #cluster-settings-power-mgmt}

啟用「VMware 分散式電源管理」特性之後，DRS 會將叢集層次與主機層次容量與叢集 VM 的需求進行比較，包括最近的歷程需求。如果發現有足夠的過剩容量，電源管理特性會讓主機處於（或建議處於）待命電源模式，如果需要容量，則開啟主機電源。視結果的主機電源狀態建議而定，VM 可能也需要與主機之間進行雙向移轉。在本設計中，電源管理是停用的，因為在叢集中開啟和關閉主機電源並沒有作業上或財務上的好處。

## vSphere 高可用性
{: #cluster-settings-vsphere-ha}

vSphere 藉由將 VM 及其所在的主機，集合成為一個叢集，以提供高可用性。叢集中的主機會受到監視，而且如果發生失敗，失敗主機上的 VM 會在替代主機上重新啟動。在本設計中，會透過叢集上的主機監視和 VM 監視而啟用 vSphere 高可用性。

### 主機監視
{: #cluster-settings-host-monitor}

主機監視可容許叢集中的主機交換網路活動訊號，並在偵測到失敗時啟用 vSphere HA。本設計已啟用此特性。

### 虛擬機器監視
{: #cluster-settings-machine-monitor}

VM 監視特性使用 VMware 工具擷取的活動訊號資訊作為 Proxy，以提供來賓作業系統可用性。VM 監視可讓 vSphere HA 自動重設或重新啟動不再有傳送活動訊號能力的個別 VM。本設計同時啟用 VM 監視和應用程式監視。

#### 失敗狀況和 VM 回應
{: #cluster-settings-failure-conditions}

失敗狀況定義 VM 失敗的方式，以及對於每一種失敗情況的回應。在本設計中，VM 重新啟動優先順序設為「中」。請檢閱此值，並調整設定，使重新啟動優先順序符合工作負載的重要性。此外，主機隔離的回應設為「關閉電源並重新啟動 VM」，使 VM 不受叢集中的隔離主機影響。此設定的其餘值是設為預設值。

下表顯示在 VMware vSphere Web Client 中的 vSphere HA 叢集設定。

表 2. vSphere HA 叢集的失敗狀況和 VM 回應設定

| 設定          | 值  |
|:------------------- |:------ |
| VM 重新啟動優先順序 |中|
| 對主機隔離的回應 |關閉電源並重新啟動 VM|
|對於發生永久裝置流失 (PDL) 的資料儲存庫的回應| 已停用 |
|對於發生所有路徑關閉 (APD) 的資料儲存庫的回應| 已停用 |
| 對於 APD 逾時之後的 APD 回復的回應 | 已停用 |
| VM 監視靈敏度 | 自訂 |
| 失敗間隔 | 50 秒 |
| 執行時間下限 | 90 秒 |
| 每部 VM 重設上限 | 10 |
| 重設時間範圍上限 | 1 小時內 |

如需在 vSphere Web Client 中配置這些設定的相關資訊，請參閱 [Configure Virtual Machine Responses](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.avail.doc/GUID-3DAED2B1-55B8-4877-BD0F-BC57C10A516C.html)。

#### 許可控制
{: #cluster-settings-admin-control}

vCenter Server 使用許可控制來確保叢集裡有足夠的資源可用來提供失效接手保護，以及確保有遵循 VM 資源保留。在本設計中，會透過指定叢集資源百分比來保留失效接手容量。定義的失效接手容量是設為 25% CPU 和 25% 記憶體。

#### 資料儲存庫活動訊號
{: #cluster-settings-datastore}

vSphere HA 使用資料儲存庫活動訊號來識別失敗的主機與位於網路分割區上的主機。資料儲存庫活動訊號可在發生管理網路分割時由 vSphere HA 監視主機，並繼續回應發生的失敗。在本設計中，活動訊號資料儲存庫選取原則是設為「自動選取可從主機存取的資料儲存庫」。

## 相關鏈結
{: #cluster-settings-related}

* [解決方案概觀](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
