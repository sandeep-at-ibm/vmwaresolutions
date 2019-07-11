---

copyright:

  years:  2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# VMware 混合式雲端移轉
{: #hcxclient-migrations}

佈建並延伸 HCX 服務網和網路延伸後，下一步是移轉 VM。

有三種移轉類型：
  -  vMotion 
  - 大量移轉
  - 冷移轉

## 作業
{: #hcxclient-migrations-operation}

使用 HCX Web 使用者介面嵌入式管理入口網站或 vSphere Web 用戶端環境定義延伸功能表，來起始跨雲端 vMotion。在任一情況下，都會啟動相同的移轉精靈。對於環境定義功能表，只會選取單一 VM 進行移轉作業。對於入口網站，可以選取多部 VM。

反轉移轉 VM 只能從 Web 使用者介面入口網站進行，即使用「HCX 移轉」精靈中的**反轉移轉**勾選框。

##  vMotion 
{: #hcxclient-migrations-vmotion}

HCX 內的 vMotion 功能可延伸 vSphere vMotion 功能，能在不同版本的 vSphere、個別的 SSO 網域以及網際網路上不同類型的網路連線之間運作。HCX 假設用來連接的網路並不安全，而且無論連線類型為何，一律都會透過加密通道來移動資料流量。

### vMotion 的概念和最佳作法
{: #hcxclient-migrations-best-practices-vmotion}

HCX 實際上就是 vMotion 雙向 Proxy。每一個 HCX 實例模擬 vSphere 資料中心內的單一 ESXi 主機，在任何叢集之外，它本身就是雲端閘道機群元件 (CGW) 的「前端」。對於每一個連結至目前所檢視網站的 HCX 網站，都會出現一部 Proxy 主機。當 vMotion 起始至遠端主機時，本端 ESXi 主機會以 vMotion 讓 VM 連接至本端 Proxy ESXi 主機，其成為 CGW 的前端，同時使用遠端系統上的 CGW 來維護加密通道。

同時，會從遠端 ESXi Proxy 主機起始 vMotion 移轉至目的地 vSphere 實體 ESXi 主機，同時它會從通道接收來源 CGW 的資料。應用 vMotion 時，一次只能執行一個 VM 移轉作業，這與大量移轉選項不同。因此，對於要移轉大量 VM 的情況，建議僅在不允許停機時或在將 VM 重新開機有風險時，才使用 vMotion。不過，就像標準 vMotion 一樣，VM 在此處理程序期間內可以是即時狀態。

我們觀察到，單一 vMotion 在 LAN 上大約 1.7 Gbps，以及在 WAN 上 300 到 400 Mbps 將達到最高點（透過 WAN 最佳化工具）。這不表示 LAN 上的 1.7 Gbps 等於 WAN 上的 400 Mbps（透過 WAN 最佳化工具），而是在特定環境上觀察到這些最大值。此類環境由 10 GB LAN vMotion 網路和 1 GB 網際網路上行鏈路（與正式作業 Web 資料流量共用）組成。

請在下列情況下使用 vMotion：
- VM 很難關閉、啟動，或執行時間較長，關閉它會帶來風險。
- 需要磁碟 UUID 的任何叢集類型的應用程式，例如 Oracle RAC 叢集。請注意，vMotion 不會變更目的地上的磁碟 UUID。
- 您想要儘快移動單一 VM。
- 不需要排定的移轉。

## 大量移轉
{: #hcxclient-migrations-bulk-mig}

### 大量移轉的概念和最佳作法
{: #hcxclient-migrations-best-practices-bulk-mig}

HCX 的大量移轉功能會使用 vSphere 抄寫來移轉磁碟資料，同時在目的地 vSphere HCX 實例上重建 VM。移轉 VM 需要下列工作流程：
- 在目的地端及其對應的虛擬磁碟上建立新的 VM。
- 將 VM 資料抄寫至新的 VM。無論是否切換排程，只要完成精靈，抄寫就會立即開始。
- 關閉原始 VM 的電源。
- 在關閉電源期間，會進行任何資料變更的最終抄寫。
- 在目的地端開啟新 VM 的電源。
- 重新命名原始 VM 並將它移至移動目的地雲端資料夾中。

以下是大量移轉優於 vMotion 的優點：
- 同時移轉多部 VM。
- 頻寬使用更一致。vMotion 可以產生頻寬使用的變動，這些變動在網路監視工具內或 WAN 最佳化工具使用者介面中會顯示為尖峰及低谷。
- 使用大量移轉，比單一 vMotion 能夠達到網路頻寬功能更高的整體使用率。
- 排定大量移轉，在排定的中斷期間切換至新移轉的 VM。
- 容許移轉目前使用虛擬 CPU 特性（和雲端不同）的 VM。在這些情況下，vMotion 移轉可能失敗。

以下是大量移轉劣於 vMotion 的缺點：
- 個別 VM 移轉的速度比 vMotion 慢很多。
- 在目的地端啟動新的複製 VM 時，VM 需要暫時關閉。
- 取決於磁碟排序及磁碟 UUID (Oracle RAC) 的 VM 可能會發生問題，其磁碟顯示會因為 UUID 變更而不同，這可能會將 OS 路徑變更至虛擬磁碟裝置。

## 移轉類型最佳作法
{: #hcxclient-migrations-mig-type-best-practices}

### 共用磁碟叢集
{: #hcxclient-migrations-shared-disk-clusters}

Oracle RAC、MS Exchange 和 MS-SQL 叢集是應用程式範例，其中兩部以上的 VM 參與叢集，且需要在所有 VM 或叢集節點上共用磁碟。在屬於應用程式叢集的磁碟（非 OS 虛擬磁碟）的所有 VM 節點上，需要啟用 VMware 多寫入器旗標。不支援對任何虛擬磁碟啟用多寫入器旗標的 VM。

移轉已啟用多寫入器虛擬磁碟的叢集：
- 會使用 vMotion 作為原始 VM 磁碟，並維護 UUID 對映。
- 在移轉期間，叢集在欠佳狀態下維持啟動（單一節點）。
- 叢集在移轉開始之前及移轉完成之後會出現關閉時間，以便在叢集 VM 之間重新組合多寫入器配置。

完成下列步驟，以移轉啟用多寫入器磁碟的叢集：
1. 根據應用程式最佳作法，關閉叢集和所有節點的電源。
2. 如果應用程式有需要，請記下每個節點 VM 中針對多寫入器配置的虛擬磁碟的磁碟順序。
3. 若為 Oracle 和使用虛擬磁碟 UUID 特性的其他任何應用程式，請登入特定 ESXi 主機，並執行 `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` 指令，以取得需要為該叢集設定多寫入器旗標的每個虛擬磁碟檔的 UUID。如果最佳作法是使磁碟順序與路徑在作業系統中的顯示方式一致，則這是必要的。vMotion 可以將磁碟重新排序（disk1、disk2、disk3），但 UUID 維持相同。當移轉完成時，請使用所指明的 UUID 來對映磁碟資訊，必要的話，請重建磁碟命名順序及 SCSI ID。不論哪一種方式，應用程式應該都能運作。當 Oracle 實例具有許多虛擬磁碟是為了應用程式疑難排解而對映時，會使用此選項。
4. 從主要叢集以外的所有叢集 VM 移除虛擬磁碟。
5. 從主要叢集 VM 移除多寫入器旗標，該節點應該是目前唯一擁有叢集磁碟的節點。
6. 視需要開啟主要叢集的電源，使關閉時間縮至最少。
7. 使用 vMotion 移轉所有叢集節點。先移轉主要叢集。在關閉電源之後移轉所有其他節點。
8. 當擁有節點的主要磁碟完成移轉時，關閉電源。
9. 必要的話，以適當的磁碟 UUID 和 Scsi ID 重新對映磁碟順序。應用程式要能運作，並不需要重新對映。
10. 在主要節點上重新啟用多寫入器旗標。
11. 啟動主要節點並驗證作業。
12. 在所有其他叢集 VM 上對映磁碟 / 啟用多寫入器旗標，然後開啟電源。
13. 驗證其他叢集作業。

### 一般 VM
{: #hcxclient-migrations-general-vms}

對 HCX 的功能建立信賴度之後，必須採用大量移轉。對於備援應用程式，有必要執行大量移轉。例如，Web 伺服器以及要將幾百個或幾千個的 VM 移轉到的位置。

### 使用直接連接 NAS 的 VM
{: #hcxclient-migrations-vms-direct-nas}

NFS 通常用來共用許多伺服器之間的資料，例如 Web 伺服器內容。在包含應用程式叢集（例如電子郵件或 RDBMS）的 VM 節點之間可以採用 iSCSI，它通常比 NFS 更加有延遲敏感性。

在任何一種情況下，如果延遲能夠低到 {{site.data.keyword.CloudDataCent_notm}}（對於 iSCSI 為 < ~7 毫秒，以及應用程式對 NFS 能夠容忍的數字），並容許應用程式以 ~1 Gbps 或更小的頻寬操作，則 NAS 網路能以 HCX 延伸到 {{site.data.keyword.cloud_notm}} 位置。完成此操作後，可以使用 HCX 對 VM 執行移轉/vMotion 操作。

在移轉後，iSCSI 磁區可與 OS 鏡映到另一個本端雲端儲存空間解決方案，而且 NFS 資料可以抄寫至任何雲端解決方案。考量如下：
- 延遲（iSCSI 或對 NFS 的應用程式容錯）
- 頻寬（每個延伸網路為 ~1 Gbps）
- 基礎鏈結頻寬

在移轉生命週期之後，請先測試開發或暫置應用程式，然後再嘗試正式作業。您可以在支援延遲敏感延伸 L2 網路的 L2C HCX 應用裝置之間，對基礎通道資料流量 (udp 500 / 4500) 採用 QoS（服務品質）。

## 網路擺盪 (Network Swing)
{: #hcxclient-migrations-network-swing}

如果目標是資料中心撤離至 {{site.data.keyword.cloud_notm}}，則在 HCX 移除之前的倒數第二個步驟是網路擺盪 (network swing)。網路擺盪可達到網路子網路移轉的目的，這些存放著所移轉 VM 的子網路從來源資料中心擺盪到 {{site.data.keyword.cloud_notm}} 內的 NSX 層疊網路。

擺盪網路涉及下列步驟：
- 驗證網路的所有工作負載已全部撤除，且任何非 VM 網路裝置已移至另一網路，或者功能性地移轉至雲端，或者已淘汰。
- 驗證已完成任何 NSX 拓蹼或 {{site.data.keyword.cloud_notm}} 支援的網路拓蹼，以支援網路擺盪。例如，動態遞送通訊協定和防火牆。
- 在使用者介面中執行 HCX 取消延伸網路工作流程，並選取適當的遞送 NSX 裝置來接管未延伸網路的預設閘道。
- 執行任何外部遞送變更，包括：插入已移轉的網路的已變更遞送、從已移轉的網路移除至來源網站的遞送，以及確保未移轉的應用程式透過 WAN 遞送至已移轉的子網路仍然可以運作。
- 應用程式擁有者從所有可能的存取點測試已移轉的應用程式：網際網路、企業內部網路和 VPN。

假設您要對所有 VM 移轉至雲端的特定應用程式執行網路擺盪。例如：
- 您在專用網路端使 vyatta 將遞送插入至 MPLS 雲端，並透過通道到達 MPLS 上的邊緣遞送裝置，以避免 {{site.data.keyword.cloud_notm}} IP 空間。
- 您已使用 {{site.data.keyword.cloud_notm}} VRF 設定您的帳戶。
- 部分應用程式位於網路負載平衡虛擬 IP (vIP) 背後。那些 vIP 位於您自己的子網路上，而這個子網路位於 vyatta 背後的虛擬 F5 上。

對透過 HCX 向擺盪到 {{site.data.keyword.cloud_notm}} 的網路新增更具體的遞送至 MPLS 對其他網路很有用，但對個別 vIP 卻非如此，這是因為新增 /32 遞送。

解決方案：WAN 提供者經常會過濾掉新增的 /32 路徑。請與 WAN 供應商合作以便容許。

以下是注意事項及含意：
- 共用子網路、vLAN 及 VXLAN 的應用程式必須一起移動。
- 使用內部可遞送 IP 的負載平衡器背後的應用程式可以要求遞送變更（如果它們無法一起移動或不想要這樣做的話）。例如，因為一次擺盪涉及太多應用程式而發現風險太高。
- 需要涉及 VMware 管理者、網路管理者（包括客戶和 WAN 供應商），以及應用程式擁有者，即使對特定系統或網路設備沒有預定的影響。

## 相關鏈結
{: #hcxclient-migrations-related}

* [HCX 元件和術語的名詞解釋](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [準備安裝環境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 用戶端部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 內部部署服務網](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [監視參數及元件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
