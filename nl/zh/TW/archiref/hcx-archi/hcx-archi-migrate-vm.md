---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 移轉虛擬機器
{: #hcx-archi-migrate-vm}

HCX 啟用雙向移轉：從內部部署至雲端，或從雲端至內部部署資料中心。HCX 會在移轉處理程序期間使用抄寫技術。抄寫技術已整合至「混合式雲端閘道」虛擬應用裝置。不需要額外安裝抄寫軟體。

## 低關閉時間移轉

低關閉時間移轉使用主機型抄寫，將即時虛擬機器從 vCenter 移至虛擬資料中心或相反方向。為了減少關閉時間，來源 VM 會在抄寫期間保持連線，並在抄寫完成之後於目的地 ESX 主機上予以引導。

1. 移轉要求會觸發下列動作：
  * 抄寫開始完整同步傳送至 VCS HCX 虛擬資料中心。抄寫所需的時間取決於 VM 的大小及可用頻寬。
  * 根據工作負載如何變更磁碟上的區塊，抄寫頻寬的耗用量會不同。
2. 完整同步化完成時，會發生差異同步化。
3. 差異同步化完成時，HCX 會觸發切換。切換可以立即啟動或排定到特定的時間啟動。
4. 在切換之後，會關閉來源 VM 的電源，並開啟所移轉抄本的電源。如果因故無法開啟 VM 的電源，則會關閉新 VM 的電源（或保持關閉電源），並開啟原始 VM 的電源。
5. HCX 會重新命名已關閉電源的原始 VM，以避免與移轉 VM 產生命名衝突，並將二進位時間戳記附加至原始 VM 名稱。
6. 如果未指定啟用**保留 MAC**，則移轉 VM 會取得新的 MAC 位址。
7. 移轉完成。在「vSphere 範本」視圖中，Hybrid Cloud Services 會將原始 VM 複製到**移轉 VM** 資料夾。

## 無關閉時間 vMotion
{: #hcx-archi-migrate-vm-no-downtime-vm}

vMotion 會將即時虛擬機器從 vSphere vCenter 傳送至 VCS Cloud。此 vMotion 需要延伸網路。vMotion 傳送會擷取虛擬機器的作用中記憶體、其執行狀態、其 IP 位址及其 MAC 位址。

虛擬機器硬體版本必須至少為第 9 版，否則跨雲端 vMotion 可能會失敗。
{:note}

## 冷移轉
{: #hcx-archi-migrate-vm-cold-mig}

冷移轉使用與跨雲端 vMotion 相同的資料平面，透過延伸網路來傳送已關閉電源的虛擬機器。會保留其 IP 位址及 MAC 位址。vMotion 的虛擬機器需求及限制相同。

### 使用雙向精靈移轉 VM
{: #hcx-archi-migrate-vm-mig-bidir-wiz}

使用 vSphere Web Client，可以從 Hybrid Cloud Services「開始使用」標籤存取雙向移轉精靈。此精靈會處理所有移轉詳細資料，包括多個虛擬機器。

從 vSphere Web Client 中，可以從 Hybrid Cloud Services「開始使用」標籤存取雙向移轉精靈。此精靈會處理所有移轉詳細資料，包括多個虛擬機器。
* 從 vSphere 至 VCS Hybrid Cloud Services
* 從 VCS HCX Cloud 至 vSphere

### 先檢查 VM 再移轉
{: #hcx-archi-migrate-vm-check-vms}

若要移轉虛擬機器，需要「混合式雲端閘道」所維護的安全連線，而且 VM 必須符合下列需求：
* 必須開啟虛擬機器的電源。
* 不論作業系統為何，基礎架構都必須是 x86。
* 若要使用 vMotion 移轉，硬體版本必須大於 9。
* 硬體版本必須小於 10。
* 可以移轉具有「原始磁碟對映」並處於相容模式的 VM。

不支援移轉具有下列屬性的 VM：
* 超過 2 TB。
* 共用 VMDK 檔案。
* 已連接虛擬媒體或 ISO。
* 硬體版本小於 9。

### 監視移轉
{: #hcx-archi-migrate-vm-monitor-mig}

您可以從使用者介面或指令行，監視抄寫型移轉的進度。檢視「作業」主控台（如「監視服務應用裝置部署」所述），並尋找**移轉 VM** 作業。狀態為**已完成**時，會移轉 VM，並開啟它的電源。

此程序使用相同 vCenter 中的不相關 VM，來追蹤移轉 VM 的進度。

1. 識別要移轉的 VM，並選擇可連線測試移轉中 VM 的觀察程式 VM。
2. 從使用者介面中，開始移轉 VM，並從「作業」主控台進行監視。
3. 使用 SSH，登入用於執行觀察程式 VM 的 ESXi 主機。
4. 執行下列指令以取得 VM ID（即 vmid）：

  ```
  # vim-cmd vmsvc/getallvms | grep -i vmname 5
  ```

5. 執行下列指令以監視抄寫狀態，其中，vmid 是前一個步驟中所取得的值：

  ```
  # vim-cmd hbrsvc/vmreplica.getState vmid
  # vim-cmd hbrsvc/vmreplica.queryReplicationState vmid 6
  ```

6. ICMP 連線測試 - 監視稍早啟動的連續連線測試。

在切換期間，連續連線測試中可能會發生岔斷。不過，測試連線測試會在**移轉 VM** 作業完成之後快速繼續，如「作業」主控台中所反映。

### 檢視移轉 VM
{: #hcx-archi-migrate-vm-view-vms}

Hybrid Cloud Services 在順利移轉的虛擬機器上開啟電源時，會關閉原始 VM 的電源，並將它儲存在 vCenter 的資料夾中。持續保留儲存的虛擬機器，直到它被手動刪除。

移轉之後，請檢視 vCenter，並記下標示為**從雲端移轉的 VM** 及**移轉至雲端的 VM** 的資料夾。
* 當已關閉電源的 VM 作為抄本時，它具有附加二進位時間戳記的原始名稱。
* 移轉 VM 的處理方式與任何其他 VM 相似。例如，它們可以移至不同的位置，並開啟電源。
* 可以刪除這些資料夾內不想要的 VM。
* 除非具有備份解決方案，否則刪除就是最終結果。

## 相關鏈結
{: #hcx-archi-migrate-vm-related}

* [修改或解除安裝 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
