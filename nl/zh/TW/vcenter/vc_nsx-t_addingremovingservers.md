---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 擴充及縮減 vCenter Server with NSX-T 實例的容量
{: #vc_nsx-t_addingremovingservers}

您可以根據商業需要，透過新增或移除 ESXi 伺服器或網路檔案系統 (NFS) 儲存空間，來擴充或縮減 VMware vCenter Server with NSX-T 實例的容量。

您可以在叢集處於維護模式時將新的 ESXi 伺服器新增至叢集。此外，您還可以跨越多個叢集同時新增或移除 ESXi 伺服器。以下是可同時進行的作業：

* 將主機新增至 **cluster1** 以及將主機新增至其他叢集。
* 從 **cluster1** 移除主機以及從其他叢集移除主機。
* 將主機新增至 **cluster1** 以及從其他叢集移除主機。
*  從 **cluster1** 移除主機以及將主機新增至其他叢集。

您可以對具有 NSX-T 叢集的現有 NFS 或 vSAN vCenter Server 進行新增或移除 NFS 儲存空間共用。{:note}

如果您的起始叢集以 vSAN 作為其儲存空間，則在部署之後新增一部以上的 ESXi 伺服器，可增加叢集儲存空間容量。

## 將 ESXi 伺服器新增至 vCenter Server with NSX-T 實例
{: #vc_nsx-t_addingremovingservers-adding}

### 新增 ESXi 伺服器之前
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* 不要從 VMware vSphere Web Client 新增 ESXi 伺服器。您在 vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_full}} 主控台同步。
* 具有 NFS 儲存空間的 vCenter Server with NSX-T 實例必須至少具有 3 部 ESXi 伺服器。您可以將預設叢集擴充為具有多達 51 部 ESXi 伺服器。每一個非預設叢集可以擴充為具有多達 59 部 ESXi 伺服器。
* 具有 vSAN 儲存空間的 vCenter Server with NSX-T 實例必須至少具有 4 部 ESXi 伺服器。

### 新增 ESXi 伺服器的程序
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要擴充容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在**叢集**表格中，按一下您要在其中新增 ESXi 伺服器的叢集。
5. 在 **ESXi 伺服器**區段中，按一下**新增**。
6. 在**新增伺服器**視窗中，輸入您要新增的伺服器數目。
7. 選擇性地選取勾選框，以便在維護模式期間新增伺服器。
8. 檢閱預估成本，然後按一下**新增**。

### 新增 ESXi 伺服器之後的結果
{: #vc_nsx-t_addingremovingservers-adding-results}

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 您將會收到電子郵件，通知正在處理您的新增 ESXi 伺服器要求。在主控台上，與 ESXi 伺服器相關聯的叢集狀態會變更為**正在修改**。
3. 如果您未看到新的 ESXi 伺服器新增至叢集裡的清單，請檢查電子郵件或主控台通知，以尋找關於失敗的其他詳細資料。

如果您要在維護模式期間新增 ESXi 伺服器，在從維護模式移除叢集之前，虛擬機器不會移轉至新的伺服器。   
{:important}

## 從 vCenter Server with NSX-T 實例移除 ESXi 伺服器
{: #vc_nsx-t_addingremovingservers-removing}

### 移除 ESXi 伺服器之前
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* 不要從 VMware vSphere Web Client 移除 ESXi 伺服器。您在 vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_short}} 主控台同步。
* 具有 NFS 儲存空間的 vCenter Server with NSX-T 實例必須至少具有 3 部 ESXi 伺服器，具有 vSAN 儲存空間的 vCenter Server with NSX-T 實例必須至少具有 4 部 ESXi 伺服器。
* 當您移除 ESXi 伺服器時，伺服器會進入維護模式，之後，會移轉伺服器上執行的所有 VM，然後再從 vCenter Server 將它們移除。如果要對 VM 重新定位擁有最大控制權，建議您讓要移除的 ESXi 伺服器進入維護模式，並使用 VMware vSphere Web Client 手動移轉在它們上面執行的 VM。之後，請使用 {{site.data.keyword.vmwaresolutions_short}} 主控台來移除 ESXi 伺服器。

### 移除 ESXi 伺服器的程序
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要縮減容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在**叢集**表格中，按一下您要從中移除 ESXi 伺服器的叢集。
5. 在 **ESXi 伺服器**區段中，選取您要移除的伺服器，然後按一下**移除**。

### 移除 ESXi 伺服器之後的結果
{: #vc_nsx-t_addingremovingservers-removing-results}

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 您將會收到電子郵件，通知正在處理您的移除 ESXi 伺服器要求。在主控台上，與 ESXi 伺服器相關聯的叢集狀態會變更為**正在修改**。
3. 在 {{site.data.keyword.cloud_notm}} 基礎架構計費週期（通常是 30 天）結束時，{{site.data.keyword.cloud_notm}} 基礎架構會完全收回 ESXi 伺服器。

   將針對已移除的 ESXi 伺服器，向您收取到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。{:note}

## 將 NFS 儲存空間新增至 vCenter Server with NSX-T 實例
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### 新增 NFS 儲存空間之前
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

不要從 VMware vSphere Web Client 新增 NFS 儲存空間。您在 vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_short}} 主控台同步。IBM 將不會管理您手動新增至實例的 NFS 檔案共用。

### 新增 NFS 儲存空間的程序
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1.  從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要擴充容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在**叢集**表格中，按一下您要在其中新增 NFS 儲存空間的叢集。
5. 在**儲存空間**區段中，按一下**新增**。
6. 在**儲存空間**視窗中，完成儲存空間配置。
   * 如果您要對所有檔案共用新增及配置相同的設定，請指定**共用數目**、**效能**及**大小 (GB)**。
   * 如果您要個別新增及配置檔案共用，請選取**個別配置共用**，然後按一下**新增共用儲存空間**標籤旁的 **+** 圖示，並針對每個個別檔案共用選取**效能**及**大小 (GB)**。您必須至少選取一個檔案共用。
7. 按一下**新增 NFS 儲存空間**。

### 新增 NFS 儲存空間之後的結果
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 您將會收到電子郵件，通知正在處理您的新增 NFS 儲存空間要求。在主控台上，與 NFS 儲存空間相關聯的叢集狀態會變更為**正在修改**。
3. 如果您未看到新的 NFS 儲存空間新增至叢集中的清單，請檢查電子郵件或主控台通知，以尋找關於失敗的其他詳細資料。

## 從 vCenter Server with NSX-T 實例移除 NFS 儲存空間
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### 移除 NFS 儲存空間之前
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* 不要從 VMware vSphere Web Client 移除 NFS 儲存空間。您在 vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_short}} 主控台同步。
* 在您移除 NFS 儲存空間之前，請確定已移除所有位於儲存空間上的 VM。
* 確定您要移除的共用與正確的 vCenter Server 實例相關聯。
* 叢集必須處於**備妥使用**狀態。

### 移除 NFS 儲存空間的程序
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要縮減容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在**叢集**表格中，按一下您要從中移除 NFS 儲存空間的叢集。
5. 在**儲存空間**區段中，選取您要移除的儲存空間共用，然後按一下**刪除**。
6. 按一下**移除儲存空間**視窗中的**移除**。

### 移除 NFS 儲存空間之後的結果
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 您將會收到電子郵件，通知正在處理您的移除 NFS 儲存空間要求。在主控台上，與 NFS 儲存空間相關聯的叢集狀態會變更為**正在修改**。
3. 在 {{site.data.keyword.cloud_notm}} 基礎架構計費週期（通常是 30 天）結束時，{{site.data.keyword.cloud_notm}} 基礎架構會完全收回 NFS 儲存空間。

   將針對已移除的 NFS 儲存空間，向您收取到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。
   {:note}

## 相關鏈結
{: #vc_nsx-t_addingremovingservers-related}

* [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server 實例的需求及規劃](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [訂購 vCenter Server with NSX-T 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [新增、檢視及刪除 vCenter Server with NSX-T 實例的叢集](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
