---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vCenter Server Hybridity add host, add server vCenter Server Hybridity, remove host vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 擴充及縮減 vCenter Server with Hybridity Bundle 實例的容量
{: #vc_hybrid_addingremovingservers}

您可以根據商業需要，透過新增或移除 ESXi 伺服器來擴充或縮減 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 實例的容量。

從 3.1 版開始，您可以藉由選取現有的配置，或叢集裡現有主機以外的替代配置，來新增 ESXi 伺服器至現有的叢集。當您訂購新的伺服器時，現有配置可用於即時選取。為了避免效能或穩定性問題，建議叢集在 CPU、RAM 及儲存空間等方面使用相同或類似的配置。這個功能適用於相同叢集內的硬體更新。叢集只能有一種類型的儲存空間。

從 2.9 版開始，您可以在叢集處於維護模式時，將新的 ESXi 伺服器新增至叢集。此外，您還可以跨越多個叢集同時新增或移除 ESXi 伺服器。以下是可同時進行的作業：

* 將主機新增至叢集以及將主機新增至其他叢集。
* 從叢集中移除主機以及從其他叢集移除主機。
* 將主機新增至叢集以及從其他叢集移除主機。
* 從叢集移除主機以及將主機新增至其他叢集。

因為您的起始叢集以 vSAN 作為其儲存空間，所以在部署之後新增一部以上的 ESXi 伺服器可以增加叢集儲存空間容量。

## 將 ESXi 伺服器新增至 vCenter Server with Hybridity Bundle 實例
{: #vc_hybrid_addingremovingservers-adding}

### 新增 ESXi 伺服器之前
{: #vc_hybrid_addingremovingservers-adding-prereq}

* 盡可能使用 {{site.data.keyword.vmwaresolutions_full}} 主控台新增 ESXi 伺服器，因為您在 VMware vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_short}} 主控台同步。因此，請只針對內部部署 ESXi 伺服器或您在 {{site.data.keyword.vmwaresolutions_short}} 主控台中無法或不會管理的 ESXi 伺服器，將 ESXi 伺服器新增至 vCenter Server。
* vSAN 儲存空間需要至少 4 部 ESXi 伺服器。

## 新增 ESXi 伺服器的程序
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要擴充容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在**叢集**表格中，按一下您要在其中新增 ESXi 伺服器的叢集。
5. 在 **ESXi 伺服器**表格中，按一下**新增**。
6. 在**新增伺服器**視窗中，輸入您要新增的伺服器數目。
7. 選擇性地選取勾選框，以便在維護模式期間新增伺服器。依預設會選取勾選框。

   佈建新的 ESXi 伺服器時，如果您未選取**維護模式**勾選框，虛擬機器 (VM) 會立即移轉到新伺服器。移轉開始之前，您不會收到確認訊息。
   {:important}

8. 完成 Bare Metal Server 配置。
   * 從叢集裡的現有主機選取配置。
   * 選取新的 {{site.data.keyword.baremetal_short_sing}} 配置，然後指定 CPU 型號及 RAM 大小。
9. 完成儲存空間配置。請指定容量及快取磁碟的磁碟類型、磁碟數目以及「vSAN 授權」版本。如果您要更多儲存空間，請勾選**高效能 Intel Optane** 方框。
10. 檢閱預估成本，然後按一下**新增**。

  您也可以按一下**新增至預估**，將佈建的資源新增至 {{site.data.keyword.cloud_notm}} 預估工具。這適用於您想要預估所選取 {{site.data.keyword.vmwaresolutions_short}} 資源與可能考慮購買之其他 {{site.data.keyword.cloud_notm}} 資源的成本時。

### 新增 ESXi 伺服器之後的結果
{: #vc_hybrid_addingremovingservers-adding-results}

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 您將會收到電子郵件，通知正在處理您的新增 ESXi 伺服器要求。在主控台上，與 ESXi 伺服器相關聯的叢集狀態會變更為**正在修改**。
3. 如果您未看到新的 ESXi 伺服器新增至叢集裡的清單，請檢查電子郵件或主控台通知，以尋找關於失敗的其他詳細資料。

如果您要在維護模式期間新增 ESXi 伺服器，在從維護模式移除叢集之前，虛擬機器不會移轉至新的伺服器。   
{:important}

## 從 vCenter Server with Hybridity Bundle 實例移除 ESXi 伺服器
{: #vc_hybrid_addingremovingservers-removing}

### 移除 ESXi 伺服器之前
{: #vc_hybrid_addingremovingservers-removing-prereq}

* 盡可能使用 {{site.data.keyword.vmwaresolutions_full}} 主控台移除 ESXi 伺服器，因為您在 vSphere Web Client 上所做的變更不會與 {{site.data.keyword.vmwaresolutions_short}} 主控台同步。因此，請只針對內部部署 ESXi 伺服器或您在 {{site.data.keyword.vmwaresolutions_short}} 主控台中無法或不會管理的 ESXi 伺服器，移除 vCenter Server 中的 ESXi 伺服器。
* vSAN 儲存空間需要至少 4 部 ESXi 伺服器。
* 移除已安裝 F5 on {{site.data.keyword.cloud_notm}} 或 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務的 ESXi 伺服器之前，您必須將 F5 BIG-IP 及 FortiGate VM 移轉至與管理 VM 不同的 ESXi 伺服器。
* 移除已安裝 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務的 ESXi 伺服器之前，請確定沒有作用中（失敗或進行中）的備份或還原作業，因為這些作用中作業可能會導致無法移除 ESXi 伺服器。
* 當您移除 ESXi 伺服器時，伺服器會進入維護模式，之後，就會先移轉伺服器上執行的所有虛擬機器 (VM)，再從 vCenter Server 移除它們。如果要對 VM 重新定位擁有最大控制權，建議您讓要移除的 ESXi 伺服器進入維護模式，並使用 VMware vSphere Web Client 手動移轉在它們上面執行的 VM。之後，請使用 {{site.data.keyword.vmwaresolutions_short}} 主控台來移除 ESXi 伺服器。

## 移除 ESXi 伺服器的程序
{: #vc_hybrid_addingremovingservers-removing-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要縮減容量的實例。
3. 在左導覽窗格上，按一下**基礎架構**。
4. 在**叢集**表格中，按一下您要從中移除 ESXi 伺服器的叢集。
5. 在 **ESXi 伺服器**表格中，選取您要移除的伺服器，然後按一下**移除**。

### 移除 ESXi 伺服器後的結果
{: #vc_hybrid_addingremovingservers-removing-results}

1. 實例狀態從**備妥使用**變更為**正在修改**時，您可能會在主控台上感覺到稍微延遲。在對實例進行其他變更之前，請讓作業全部完成。
2. 您將會收到電子郵件，通知正在處理您的移除 ESXi 伺服器要求。在主控台上，與 ESXi 伺服器相關聯的叢集狀態會變更為**正在修改**。
3. 在 {{site.data.keyword.cloud_notm}} 基礎架構計費週期（通常是 30 天）結束時，{{site.data.keyword.cloud_notm}} 基礎架構會完全收回 ESXi 伺服器。

   將針對已移除的 ESXi 伺服器，向您收取到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。
   {:note}

## 相關鏈結
{: #vc_hybrid_addingremovingservers-related}

* [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server with Hybridity Bundle 實例的需求及規劃](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [新增、檢視及刪除 vCenter Server with Hybridity Bundle 實例的叢集](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Place a host in maintenance mode](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:new_window}
