---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# 擴充及縮減 vCenter Server with Hybridity Bundle 實例的容量

您可以根據商業需要，透過新增或移除 ESXi 伺服器來擴充或縮減 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 實例的容量。

因為您的起始叢集以 vSAN 作為其儲存空間，所以在部署之後新增一部以上的 ESXi 伺服器可以增加叢集儲存空間容量。

## 開始之前

* 不要從 VMware vSphere Web Client 新增或移除 ESXi 伺服器。您對 vSphere Web Client 所做的變更與 {{site.data.keyword.vmwaresolutions_short}} 主控台未同步。
* vSAN 儲存空間需要至少 4 部 ESXi 伺服器。
* 開始移除已安裝 F5 on {{site.data.keyword.cloud_notm}} 或 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務的 ESXi 伺服器之前，您必須將 F5 BIG-IP 及 FortiGate VM 移轉至與目前管理 VM 不同的 ESXi 伺服器。
* 如果已安裝 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務，在您移除 ESCi 伺服器之前，請確定沒有作用中（失敗或進行中）的備份或還原作業，因為這些作用中作業可能導致無法移除 ESXi 伺服器。
* 當您移除 ESXi 伺服器時，伺服器會進入維護模式，之後，就會先移轉伺服器上執行的所有虛擬機器 (VM)，再從 vCenter Server 中移除它們。如果要對 VM 重新定位擁有最大控制權，建議您讓要移除的 ESXi 伺服器進入維護模式，並使用 VMware vSphere Web Client 手動移轉在它們上面執行的 VM。之後，請使用 {{site.data.keyword.vmwaresolutions_full}} 主控台來移除 ESXi 伺服器。

## 程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要擴充或縮減容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在 **CLUSTERS** 表格中，按一下您要在其中新增或移除 ESXi 伺服器的叢集。
5. 若要新增 ESXi 伺服器，請完成下列步驟：
   1. 在 **ESXi 伺服器**表格中，按一下**新增**。
   2. 在**新增伺服器**視窗中，選取您要新增的伺服器數目，並按一下價格鏈結來檢閱預估成本，然後按一下**新增**。
6. 若要移除 ESXi 伺服器，請在 **ESXi 伺服器**表格中選取您要移除的伺服器，然後按一下**移除**。

## 結果

啟動新增或移除作業之後，當實例狀態從**備妥使用**變成**正在修改**的時候，您可能會感覺稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。

您將會收到電子郵件，通知您正在處理您要新增或移除 ESXi 伺服器的要求。與 ESXi 伺服器相關聯的叢集狀態會變更為**正在修改**。移除伺服器時，請注意，在 {{site.data.keyword.cloud_notm}} 基礎架構計費週期（通常是 30 天）結束時，{{site.data.keyword.cloud_notm}} 基礎架構會完全收回 ESXi 伺服器。

**注意：**將向您收取已移除的 ESXi 伺服器到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。

如果您未看到新 ESXi 伺服器新增至叢集中的清單，請檢查電子郵件或主控台通知，以尋找關於失敗的其他詳細資料。

## 相關鏈結

* [vCenter Server 資料清單](vc_bom.html)
* [vCenter Server with Hybridity Bundle 實例的需求及規劃](vc_hybrid_planning.html)
* [新增、檢視及刪除 vCenter Server with Hybridity Bundle 實例的叢集](vc_hybrid_addingviewingclusters.html)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
