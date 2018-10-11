---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-28"

---

# 擴充及縮減 Cloud Foundation 實例的容量

您可以根據商業需求來擴充或縮減 VMware Cloud Foundation 實例的容量，方法是新增或移除 ESXi 伺服器。

Cloud Foundation 實例最多可以有五個叢集，而其中一個是預設值。每個起始叢集最多都可以有 51 部 ESXi 伺服器，而其他叢集最多可以有 59 部。

## 將 ESXi 伺服器新增至 Cloud Foundation 實例

### 新增 ESXi 伺服器之前

* 不要從 VMware vSphere Web Client 新增 ESXi 伺服器。您在 VMware vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_full}} 主控台同步。
* 依預設，您訂購的基本平台會有 4 部 ESXi 伺服器。您可以將平台擴充至最多 32 部 ESXi 伺服器。不過，您可以同時新增的 {{site.data.keyword.baremetal_short}} 數目如下所示：
   * 如果是**小型**及**大型**配置，您一次可以新增 1 - 10 部 ESXi 伺服器。
   * 如果是**自訂**配置，您一次可以新增 1 - 20 部 ESXi 伺服器。

## 新增 ESXi 伺服器的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格上的**已部署的實例**。
2. 在 **Cloud Foundation 實例**表格中，按一下您要擴充容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在 **CLUSTERS** 表格中，按一下您要在其中新增 ESXi 伺服器的叢集。
5. 在 **ESXi 伺服器**區段中，按一下**新增**。
6. 在**新增伺服器**視窗中，輸入您要新增的伺服器數目、檢閱預估成本，然後按一下**新增**。

### 新增 ESXi 伺服器之後的結果

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 新增 ESXi 伺服器時，會透過電子郵件通知您。
3. 如果您未看到新 ESXi 伺服器新增至叢集裡的清單，請檢查電子郵件或主控台通知，以尋找關於失敗的其他詳細資料。

## 從 Cloud Foundation 實例移除 ESXi 伺服器

### 移除 ESXi 伺服器之前

* 不要從 VMware vSphere Web Client 移除 ESXi 伺服器。您在 VMware vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_short}} 主控台同步。
* 依預設，您訂購的基本平台會有 4 部 ESXi 伺服器。您可以移除所新增的 ESXi 伺服器。您無法移除預設 ESXi 伺服器。
* 移除已安裝 F5 on {{site.data.keyword.cloud_notm}} 或 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務的 ESXi 伺服器之前，您必須將 F5 BIG-IP 及 FortiGate VM 移轉至與管理 VM 不同的 ESXi 伺服器。
* 移除已安裝 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務的 ESXi 伺服器之前，請確定沒有作用中備份或還原作業。作用中作業（失敗或進行中）可能會防止移除 ESXi 伺服器。

## 移除 ESXi 伺服器的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格上的**已部署的實例**。
2. 在 **Cloud Foundation 實例**表格中，按一下您要縮減容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在 **CLUSTERS** 表格中，按一下您要從中移除 ESXi 伺服器的叢集。
6. 在 **ESXi 伺服器**區段中，選取您要移除的伺服器，然後按一下**移除**。

### 移除 ESXi 伺服器之後的結果

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 移除 ESXi 伺服器時，會透過電子郵件通知您。
3. 在 {{site.data.keyword.cloud_notm}} 計費週期（通常是 30 天）結束時，{{site.data.keyword.cloud_notm}} 基礎架構會完全收回 ESXi 伺服器。

   **注意**：將向您收取已移除的 ESXi 伺服器到 {{site.data.keyword.cloud_notm}} 計費週期結束為止的費用。

### 相關鏈結

* [Cloud Foundation 資料清單](sd_bom.html)
* [Cloud Foundation 實例的需求及規劃](sd_planning.html)
* [新增、檢視及刪除 Cloud Foundation 實例的叢集](sd_addingviewingclusters.html)
* [讓主機進入維護模式](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [加強型 vMotion 相容性 (EVC) 處理器支援](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
