---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

---

# 部署前的規劃
{: #vcshcx-planning}

部署 HCX 所花費的時間大部分是在部署前階段。
一般而言，資訊系統移轉專案通常需要數個月或是數年來完成，但 HCX 可在極短時間內完成移轉，而且在部署之後網路連線至雲端即可立即啟動。

因為企業層級客戶的 HCX 部署通常需要安全、網路、儲存空間及 vSphere 基礎架構團隊，所以在 POC 中需要這些團隊是合理的。有效的專案管理及利害關係人提早加入，對於確保實現 HCX 的部署和作業速度非常重要。

## 避免分析癱瘓
{: #vcshcx-planning-avoiding}

移轉虛擬機器 (VM) 或 VM 群組有許多障礙且很花時間，這是因為需要修改應用程式環境的組件、要設計那些變更以及為了進行那些變更所需的關閉時間排程。完成這些變更之後，移轉很難回復，進而使分析癱瘓。嘗試掌控移轉的所有層面、進行跨團隊協調，以及變更主要利害關係人都會導致專案進度落後。

HCX 容許跨 vSphere 實例移轉 VM 或 VM 群組（其代表一個局部或完整複合應用程式），而不需進行任何應用程式修改。因此，從移轉中取消表示將 VM 移回或重新延伸網路。這樣就不需要大型移轉規劃，並容許在規劃程序中有一些平行化。在選取要移動的應用程式以及建立高階網路設計之後，可以開始在雲端實例上以最小配置移轉應用程式，同時解決最終網路連線和設計。

## 延伸網路
{: #vcshcx-planning-stretched-net}

HCX 機群的網路延伸元件非常穩定。一位特定客戶有超過 20 個 VLAN，且透過 1 Gbps WAN 延伸到 {{site.data.keyword.cloud}} 與其他資料流量及 HCX 移轉通道共用，並沒有產生任何歸因於網路的應用程式問題。此方式的網路鏈結可運作 6 個月以上。


新增及移除更多延伸網路也沒有問題。在鄰近之處挑選 {{site.data.keyword.CloudDataCent_notm}}（此特定客戶 < 6ms 的延遲）也對延伸網路的網路穩定起了作用。假設您有足夠的頻寬，對應用程式的延遲夠低，那麼，讓延伸網路保持長時間運作，不應該成為您設計中的不利因素。

## 移轉生命週期
{: #vcshcx-planning-mig-lifecycle}

下列各節說明一般 HCX 移轉生命週期內的階段，其表示工作串流可以平行執行之處。

## vSphere 庫存
{: #vcshcx-planning-vsphere-planning}

- 在要移轉的應用程式內，進行粗略的 VM 評量。
粗略意味僅瞭解參與應用程式的 VM，而不深入探索詳細資料。
- 如果您計劃移轉許多 VM，但來源和雲端網站之間的網路頻寬有限，則當來源採用 NSX 時，可依 VLAN 或 VXLAN 將 VM 進一步分組。這樣可以進行階式 HCX 移轉計劃，進行依 VLAN 分組的 VM 群組的移轉，而且所在的 L2 個網路只會延伸到 VLAN 釋放為止。

這表示唯有當雲端網路設計定案及部署後，才能將相關 L2 延伸網路的起始群組取消延伸。取消延伸意味擺盪的特定 VXLAN 資料流量現在是透過雲端實例 NSX 基礎架構遞送。

## 基準線網路配置
{: #vcshcx-planning-baseline-net-config}

在雲端 vSphere 實例內建立安全的周邊網路。這通常是由 NSX DLR 或 Edge 應用裝置所組成。如果您使用「HCX 近似性遞送」，則不需要建立任何防火牆規則或上行鏈路拓蹼，因為可在之後或同時完成它，而不會影響延伸的 L2 資料流量。

## 	網路延伸
{: #vcshcx-planning-net-extension}

延伸網路僅意味著從虛擬分散式交換器埠群組 (vDS) 代表的來源 vSphere 環境中使用現有的 VLAN 或 VXLAN，然後將它延伸至 HCX 雲端上的 NSX VXLAN。

## 啟航前測試
{: #vcshcx-planning-preflight-tests}

啟航前測試包含以 vMotion 及大量移轉功能執行 HCX 移轉，以建立基準線傳送速率。

## 非正式作業應用程式的移轉
{: #vcshcx-planning-mig-non-prod-apps}

此時，VM 的移轉會從較不重要 VM 的計劃階段開始。開發、測試等階段則使用網際網路連線功能來進行移轉和延伸的 L2 資料流量。

## 雲端網路設計及實作開始
{: #vcshcx-planning-cloud-net-begins}

移轉作業繼續時，雲端網路設計會終結並在雲端 vSphere 實例內實作。

## 更多網路連線功能考量
{: #vcshcx-planning-connect-considerations}

移轉作業繼續進行時，會訂購專用的 WAN 網路連線，因為雲端提供者通常需要幾週到幾個月的時間才能建立。完成專用網路連線之後，HCX 可以配置成同時使用專用網路鏈結和網際網路，來進行移轉和延伸的 L2 資料流量。

## 實體伺服器
{: #vcshcx-planning-physical-servers}

當目標是要將資料中心移轉至雲端時，可評量與移轉中 VM 互動的任何實體伺服器是要以 VM (P2V)、裸機移轉至 {{site.data.keyword.cloud_notm}}，或保留在來源處。如果實體伺服器要保留在來源處，而且在建立專用網路之前的移轉期間內僅使用 HCX，則務必瞭解它是否位於以 HCX 延伸至雲端的任何網路上。在此情境中，HCX 不僅容許 VM，還容許整個子網路移轉至雲端。如果要在移轉結束時移除 HCX，而且如果要維持實體裝置與已移轉的 VM 之間的連線，則該子網路不能存在於來源與目的地。這意味著位於延伸 L2 網路的來源網站上所留下的任何實體裝置，都必須移轉至能夠遞送至雲端的另一個網路子網路。但如運用了其他延伸 L2 技術（例如 NSX L2 VPN）來取代 HCX 延伸 L2 端點，則為例外狀況。

## 移轉正式作業和複式應用程式
{: #vcshcx-planning-mig-prod-complex-app}

具有共用多寫入器 VMDK 的 VM，例如 Oracle RAC 或 MS Exchange / SQL 叢集或具有原始裝置對映的 VM，都是移轉前需要額外考量的 VM 範例。

## 網路擺盪 (Network Swing)
{: #vcshcx-planning-net-swing}

當來源端網路上的 VM 撤除完成，且雲端上的網路設計 / 實作完成之後，即會發生網路擺盪 (Network Swing)。配置 HCX 在移轉浪潮中把所完成之 VM 的相關網路取消延伸，可讓移轉的 VM 能夠使用雲端 NSX 基礎架構遞送網路資料流量。

## 支援的用戶端平台
{: #vcshcx-planning-client-platforms}

對於網路延伸，只支援具有 vSphere 虛擬分散式交換器 (vDS) 的埠群組。這也意味著不支援獨立式 ESXi 主機，因為當 vCenter 管理 ESXi 主機時，您只能有一個 vDS。
- vSphere 5.1（指令行僅透過 API 使用於 vCenter 5.1）
- vSphere 5.5（在 vCenter 5.5u3 及更新版本上支援 Web 用戶端使用者介面）
- vSphere 6.0
- vSphere 6.5（vDS 必須是 6.0 層次）

## 支援的雲端平台
{: #vcshcx-planning-cloud-platforms}

HCX 雲端是由 {{site.data.keyword.cloud_notm}} 自動化佈建。

## 連線功能選項
{: #vcshcx-planning-connect-options}

### 標準 HCX 連線功能
{: #vcshcx-planning-standard-connect}

由於是透過 {{site.data.keyword.vmwaresolutions_short}} 自動化所部署，依預設，HCX 雲端安裝會配置為透過公用網際網路連接。

### 選用的連線功能
{: #vcshcx-planning-optional-connect}

在訂購時，可以選取透過 {{site.data.keyword.cloud_notm}} 專用網路的連線。

## 相關鏈結
{: #vcshcx-planning-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
