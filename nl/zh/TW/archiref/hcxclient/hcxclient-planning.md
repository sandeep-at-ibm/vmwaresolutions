---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# 準備安裝環境
{: #hcxclient-planning-prep-install}

VMware HCX on IBM Cloud 安裝具有下列軟體需求：
* vSphere 5.5 U3，或是 vSphere 6.0u2 或更新版本。
* 如果使用 NSX，則為 6.2.2 版或更新版本。原則移轉需要 NSX。
* 若要使用跨雲端 vMotion，則相同親緣性限制會套用至雲端，就像在內部部署上一樣。如需相關資訊，請參閱 [VMware EVC 及 CPU 相容性常見問題](https://kb.vmware.com/s/article/1005764)。

## 配置網路連線功能
{: #hcxclient-planning-config-net}

HCX 必須遍訪公用網際網路及專用線路，並連接至資料中心元件（例如網路、交換器及埠群組）。
* 如需必須開啟才能順利安裝 HCX 虛擬應用裝置的埠的相關資訊，請參閱[埠存取需求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)。
* 內部部署 vSphere 環境和 VCS HCX 雲端環境都必須容許 vSphere 內部部署裝置與 VCS HCX 裝置之間進行網路時間通訊協定 (NTP) 時鐘同步化。HCX 虛擬應用裝置及網路必須可存取 UDP 埠 123。

## 內部部署環境
{: #hcxclient-planning-on-prem-env}

在您安裝 HCX 之前，請驗證環境可以支援您要完成的作業。內部部署環境必須先支援下列作業，才能安裝 HCX。
* 具有 vSphere 5.5 Update 3 或 6.0 Update 2 的「虛擬中心」。
* vMotion 及原則移轉特性需要 NSX 6.2.2 版或更新版本。
* 獲指派「管理者 vCenter Server」系統角色的 vSphere 服務帳戶。
* 在 vCenter 中，要安裝的 HCX 應用裝置要有足夠的磁碟空間。
* 足夠用於安裝期間所佈建之內部部署 VM 的 IP 位址。
* 如「埠存取需求」所記載，視需要開啟埠及防火牆。
* 如果單一登入 (SSO) 伺服器在遠端，則必須識別 vCenter、「外部 SSO 伺服器」或執行外部查閱服務之 Platform Services Controller (PSC) 的 URL。向 vCenter 登錄 HCX Manager 時，必須提供此 URL。
* 如果 vCenter 沒有自己的內部查閱服務實例，則可能是因為下列其中一個原因：
  * vCenter 6.0u2 正在執行外部 Platform Services Controller。
  * vCenter 處於鏈結模式（其中，次要 vCenter 使用主要 vCenter 或外部 SSO 服務中的 SSO 服務）。

## 驗證第 2 層安裝環境
{: #hcxclient-planning-verify-layer-2-inst}

第 2 層網路延伸具有下列需求：
* vSphere Enterprise Plus 版本。
* vSphere vCenter 必須滿足下列需求，才能支援第 2 層延伸：
  * vSphere Enterprise Plus 授權
  * 必須有 vSphere Distributed Switch (vDS)。vSphere Enterprise Plus Edition 提供分散式交換器。
  * 安裝時，內部部署第 2 層集中器服務應用裝置必須可以存取 vNIC 埠以及任何要延伸的 VLAN。
  * 如果要透過公用網際網路或 VPN（在替代路徑上）來延伸網路，則 VCS 中的 L2C 虛擬機器需要 IP 位址。需要有遠端 IP 位址，才能配置第 2 層集中器。
  * 如果想要多個第 2 層集中器，則各在內部部署及雲端中都必須有 IP 位址。

## 部署前的規劃
{: #hcxclient-planning-predepl}

部署 HCX 所花費的時間大部分是在部署前階段。
一般而言，資訊系統移轉專案通常需要數個月或是數年來完成，但 HCX 可在短時間內完成移轉，而且在部署之後網路連線至雲端即可立即啟動。

因為企業層級客戶的 HCX 部署通常需要安全、網路、儲存空間及 vSphere 基礎架構團隊，所以在 POC 中需要這些團隊是合理的。有效的專案管理及利害關係人提早加入，對於確保實現 HCX 的部署和作業速度非常重要。

## 避免分析癱瘓
{: #hcxclient-planning-avoiding}

移轉虛擬機器 (VM) 或 VM 群組有許多障礙且很花時間，這是因為需要修改應用程式環境的組件、要設計那些變更以及為了進行那些變更所需的關閉時間排程。完成這些變更之後，移轉很難回復，進而使分析癱瘓。嘗試掌控移轉的所有層面、進行跨團隊協調，以及變更主要利害關係人都會導致專案進度落後。

HCX 容許跨 vSphere 實例移轉 VM 或 VM 群組（其代表一個局部或完整複合應用程式），而不需進行任何應用程式修改。因此，從移轉中取消表示將 VM 移回或重新延伸網路。這樣就不需要大型移轉規劃，並容許在規劃程序中有一些平行化。在選取要移動的應用程式以及建立高階網路設計之後，可以開始在雲端實例上以最小配置移轉應用程式，同時解決最終網路連線和設計。

## 延伸網路
{: #hcxclient-planning-stretched-net}

HCX 機群的網路延伸元件非常穩定。一位特定客戶有超過 20 個 VLAN，且透過 1 Gbps WAN 延伸到 {{site.data.keyword.cloud}} 與其他資料流量及 HCX 移轉通道共用，並沒有產生任何歸因於網路的應用程式問題。此方式的網路鏈結可運作 6 個月以上。


新增及移除更多延伸網路也沒有問題。選取離得很近的 {{site.data.keyword.CloudDataCent_notm}}（對於此特定客戶，等待時間小於 6 毫秒）也會提高延伸網路連線功能的網路穩定性。假設您有足夠的頻寬，對應用程式的延遲夠低，則，讓延伸網路保持長時間運作，不應該成為您設計中的不利因素。

## 移轉生命週期
{: #hcxclient-planning-mig-lifecycle}

下列各節說明一般 HCX 移轉生命週期內的階段，其表示工作串流可以平行執行之處。

## vSphere 庫存
{: #hcxclient-planning-vsphere-planning}

- 在要移轉的應用程式內，進行粗略的 VM 評量。
粗略意味僅瞭解參與應用程式的 VM，而不深入探索詳細資料。
- 如果您計劃移轉許多 VM，但來源和雲端網站之間的網路頻寬有限，則當來源採用 NSX 時，可依 VLAN 或 VXLAN 將 VM 進一步分組。這樣可以進行階式 HCX 移轉計劃，進行依 VLAN 分組的 VM 群組的移轉，而且所在的 L2 個網路只會延伸到 VLAN 釋出為止。

這表示唯有當雲端網路設計定案及部署後，才能將相關 L2 延伸網路的起始群組取消延伸。取消延伸意味擺盪的特定 VXLAN 資料流量現在是透過雲端實例 NSX 基礎架構遞送。

## 基準線網路配置
{: #hcxclient-planning-baseline-net-config}

在雲端 vSphere 實例內建立安全的周邊網路。這通常是由 NSX DLR 或 Edge 應用裝置所組成。如果您使用「HCX 近似性遞送」，則不需要建立任何防火牆規則或上行鏈路拓蹼，因為可在之後或同時完成它，而不會影響延伸的 L2 資料流量。

## 網路延伸
{: #hcxclient-planning-net-extension}

延伸網路僅意味著從虛擬分散式交換器埠群組 (vDS) 代表的來源 vSphere 環境中使用現有的 VLAN 或 VXLAN，然後將它延伸至 HCX 雲端上的 NSX VXLAN。

## 預先測試
{: #hcxclient-planning-preflight-tests}

預先測試包含以 vMotion 及大量移轉功能執行 HCX 移轉，來建立基準線傳送速率。

## 非正式作業應用程式的移轉
{: #hcxclient-planning-mig-non-prod-apps}

VM 的移轉會從不太重要的 VM 的計劃階段開始。開發和測試團隊會使用網際網路連線功能來進行移轉和延伸的 L2 資料流量。

## 雲端網路設計及實作開始
{: #hcxclient-planning-cloud-net-begins}

移轉作業繼續時，雲端網路設計會終結並在雲端 vSphere 實例內實作。

## 更多網路連線功能考量
{: #hcxclient-planning-connect-considerations}

移轉作業繼續進行時，會訂購專用的 WAN 網路連線，因為雲端提供者通常需要幾週到幾個月的時間才能建立。完成專用網路連線之後，HCX 可以配置成同時使用專用網路鏈結和網際網路，來進行移轉和延伸的 L2 資料流量。

## 實體伺服器
{: #hcxclient-planning-physical-servers}

當目標是要將資料中心移轉至雲端時，可評量與移轉中 VM 互動的任何實體伺服器是要以 VM (P2V)、裸機移轉至 {{site.data.keyword.cloud_notm}}，或保留在來源處。如果實體伺服器要保留在來源中，並且 HCX 在移轉期間僅會使用到建立專用網路時，則務必瞭解該實體伺服器是否位於已使用 HCX 延伸到雲端中的任何網路上。在此情境中，HCX 不僅容許 VM 移轉到雲端中，還容許整個子網路移轉到雲端中。

若要在移轉結束時移除 HCX，而且如果要維持實體裝置與已移轉的 VM 之間的連線，則該子網路不能存在於來源與目的地。這意味著位於延伸 L2 網路的來源網站上所留下的任何實體裝置，都必須移轉至可以遞送至雲端的另一個網路子網路。但如運用了其他延伸 L2 技術（例如 NSX L2 VPN）來取代 HCX 延伸 L2 端點，則為例外狀況。

## 移轉正式作業和複合應用程式
{: #hcxclient-planning-mig-prod-complex-app}

具有共用多寫入器 VMDK 的 VM，例如 Oracle RAC 或 MS Exchange / SQL 叢集或具有原始裝置對映的 VM，都是移轉前需要額外考量的 VM 範例。

## 網路擺盪 (Network Swing)
{: #hcxclient-planning-net-swing}

當來源端網路上的 VM 撤除完成，且雲端上的網路設計 / 實作完成之後，即會發生網路擺盪 (Network Swing)。配置 HCX 在移轉浪潮中把所完成之 VM 的相關網路取消延伸，可讓移轉的 VM 能夠使用雲端 NSX 基礎架構遞送網路資料流量。

## 支援的用戶端平台
{: #hcxclient-planning-client-platforms}

對於網路延伸，只支援具有 vSphere 虛擬分散式交換器 (vDS) 的埠群組。這還意味著不支援獨立式 ESXi 主機，因為 ESXi 主機由 vCenter 進行管理時，只能有一個 vDS。
- vSphere 5.1（指令行僅透過 API 使用於 vCenter 5.1）
- vSphere 5.5（在 vCenter 5.5u3 及更新版本上支援 Web 用戶端使用者介面）
- vSphere 6.0
- vSphere 6.5（vDS 必須是 6.0 層次）

## 支援的雲端平台
{: #hcxclient-planning-cloud-platforms}

HCX 雲端是由 {{site.data.keyword.cloud_notm}} 自動化佈建。

## 連線功能選項
{: #hcxclient-planning-connect-options}

### 標準 HCX 連線功能
{: #hcxclient-planning-standard-connect}

由於是透過 {{site.data.keyword.vmwaresolutions_short}} 自動化所部署，依預設，HCX 雲端安裝會配置為透過公用網際網路連接。

## 相關鏈結
{: #hcxclient-planning-related}

* [HCX 元件和術語的名詞解釋](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [HCX 用戶端部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 內部部署服務網](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合雲端移轉](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [監視參數及元件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
