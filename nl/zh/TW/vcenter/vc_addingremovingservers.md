---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-07"

---

# 擴充及縮減 vCenter Server 實例的容量

您可以根據商業需要，透過新增或移除 ESXi 伺服器來擴充或縮減 VMware vCenter Server 實例的容量。

如果您的起始叢集以 vSAN 作為其儲存空間，則在部署之後新增一部以上的 ESXi 伺服器，可增加叢集儲存空間容量。

## 將 ESXi 伺服器新增至 vCenter Server 實例

### 新增 ESXi 伺服器之前

* 不要從 VMware vSphere Web Client 新增 ESXi 伺服器。您對 vSphere Web Client 所做的變更與 {{site.data.keyword.vmwaresolutions_full}} 主控台未同步。
* 具有 NFS 儲存空間的 vCenter Server 實例至少必須有 2 部 ESXi 伺服器。對於在 2.1 版或更新版本中部署的實例，您可以將預設叢集擴充為具有多達 51 部 ESXi 伺服器。每個非預設叢集可以擴充為具有多達 59 部 ESXi 伺服器。
* 具有 vSAN 儲存空間的 vCenter Server 實例至少必須有 4 部 ESXi 伺服器。
* 對於 2.0 版或更舊版本中部署的 vCenter Server 實例，您可以將每一個叢集擴充為具有多達 32 部 ESXi 伺服器。您可以一次新增的 {{site.data.keyword.baremetal_short}} 數目如下所示：
   * 如果是**小型**、**中型**、**大型**配置，您一次可以新增 1 - 10 部 ESXi 伺服器。
   * 如果是**自訂**配置，您一次可以新增 1 - 20 部 ESXi 伺服器。如需最少 ESXi 伺服器的相關資訊，請參閱[雙節點 vCenter Server 實例是否為高可用性？](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## 新增 ESXi 伺服器的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要擴充容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在 **CLUSTERS** 表格中，按一下您要在其中新增 ESXi 伺服器的叢集。
5. 在 **ESXi 伺服器**區段中，按一下**新增**。
6. 在**新增伺服器**視窗中，輸入您要新增的伺服器數目、檢閱預估成本，然後按一下**新增**。

### 新增 ESXi 伺服器後的結果

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 您將會收到電子郵件，通知您正在處理新增 ESXi 伺服器的要求。在主控台上，與 ESXi 伺服器相關聯的叢集狀態會變更為**正在修改**。
3. 如果您未看到新 ESXi 伺服器新增至叢集中的清單，請檢查電子郵件或主控台通知，以尋找關於失敗的其他詳細資料。

## 從 vCenter Server 實例移除 ESXi 伺服器

### 移除 ESXi 伺服器之前

* 不要從 VMware vSphere Web Client 移除 ESXi 伺服器。您對 vSphere Web Client 所做的變更與 {{site.data.keyword.vmwaresolutions_full}} 主控台未同步。
* 具有 NFS 儲存空間的 vCenter Server 實例至少必須有 2 部 ESXi 伺服器，而具有 vSAN 儲存空間的 vCenter Server 實例至少必須有 4 部 ESXi 伺服器。
* 開始移除已安裝 F5 on {{site.data.keyword.cloud_notm}} 或 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務的 ESXi 伺服器之前，您必須將 F5 BIG-IP 及 FortiGate VM 移轉至與目前管理 VM 不同的 ESXi 伺服器。
* 如果已安裝 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務，在您移除 ESCi 伺服器之前，請確定沒有作用中（失敗或進行中）的備份或還原作業，因為這些作用中作業可能導致無法移除 ESXi 伺服器。
* 當您移除 ESXi 伺服器時，伺服器會進入維護模式，之後，就會先移轉伺服器上執行的所有虛擬機器 (VM)，再從 vCenter Server 中移除它們。如果要對 VM 重新定位擁有最大控制權，建議您讓要移除的 ESXi 伺服器進入維護模式，並使用 VMware vSphere Web Client 手動移轉在它們上面執行的 VM。之後，請使用 {{site.data.keyword.vmwaresolutions_short}} 主控台來移除 ESXi 伺服器。

## 移除 ESXi 伺服器的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要縮減容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在 **CLUSTERS** 表格中，按一下您要從中移除 ESXi 伺服器的叢集。
5. 在 **ESXi 伺服器**區段中，選取您要移除的伺服器，然後按一下**移除**。

### 移除 ESXi 伺服器後的結果

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 您將會收到電子郵件，通知您正在處理移除 ESXi 伺服器的要求。在主控台上，與 ESXi 伺服器相關聯的叢集狀態會變更為**正在修改**。
3. 在 {{site.data.keyword.cloud_notm}} 基礎架構計費週期（通常是 30 天）結束時，{{site.data.keyword.cloud_notm}} 基礎架構會完全收回 ESXi 伺服器。

   **注意**：將向您收取已移除的 ESXi 伺服器到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。

### 相關鏈結

* [vCenter Server 資料清單](vc_bom.html)
* [vCenter Server 實例的需求與規劃](vc_planning.html)
* [新增、檢視及刪除 vCenter Server 實例的叢集](vc_addingviewingclusters.html)
* [讓主機進入維護模式](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [加強型 vMotion 相容性 (EVC) 處理器支援](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
