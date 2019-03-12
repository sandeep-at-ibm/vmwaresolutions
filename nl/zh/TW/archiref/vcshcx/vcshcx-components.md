---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# HCX 元件和術語的名詞解釋
{: #vcshcx-components}

HCX 是由一個雲端（目標）及一個以上的用戶端（來源）所組成。每個 vCenter 必須部署一個 HCX 實例，即使部署 HCX 的 vCenter 是鏈結到用戶端或雲端上的相同 SSO 網域亦然。HCX 支援的配置有：一對一、一對多、多對一及多對多。

## 雲端和用戶端
{: #vcshcx-components-cloud-client-side}

HCX 是雲端（目標）及用戶端（來源）的概念。
- 雲端 - vCenter Server on 	{{site.data.keyword.cloud}} with Hybridity Bundle。HCX 的雲端是 HCX 用戶端對雲端關係中的從屬實例。它由用戶端控制。
- 用戶端 - 任何符合安裝與作業之必要條件的 vSphere 實例。HCX 的用戶端是主節點，它透過其 vCenter Web 用戶端使用者介面 (UI) 嵌入式管理單元，來控制雲端從屬實例。

## HCX Manager
{: #vcshcx-components-hcx-manager}

- 雲端 HCX Manager 是經由 {{site.data.keyword.vmwaresolutions_short}} 自動化而部署在雲端上之 HCX 安裝的第一部分。一開始，它是單一已部署的 OVA 映像檔（為雲端所特有）以及針對 HCX 角色特別配置的 NSX 邊緣負載平衡器防火牆。HCX Manager 的配置是為了接聽送入的用戶端登錄、管理及控制資料流量。
- 用戶端 HCX Manager 是用戶端特有的 OVA 映像檔，其提供使用者介面功能來管理及操作 HCX。用戶端 HCX Manager 負責向雲端 HCX Manager 登錄，以及在用戶端和雲端之間建立管理平面。此外，它還負責將機群元件部署在用戶端，並指示雲端執行相同動作。

## 機群元件
{: #vcshcx-components-fleet}

「HCX 機群」元件負責建立用戶端與雲端之間的資料和控制平面。在鏡映配對中部署為虛擬機器 (VM) 的機群是由下列元件組成：

- 雲端閘道 (CGW) -「雲端閘道」是一個選用元件，負責建立支援 vMotion 及抄寫（大量移轉）資料流量的加密通道。每個鏈結的 HCX 網站只有一個配對。
- 第 2 層集中器 (L2C) - 第 2 層集中器是一個選用元件，負責建立對應於延伸第 2 層資料流量的資料與控制平面的加密通道。每一個 L2C 配對最多可以處理 4096 個延伸網路。可視需要部署更多 L2C 配對。頻寬功能限制為 ~4 Gbps，因此，如果外部頻寬容量大於 4 Gbps，則使用更多 L2C 配對可以提高基礎網路的使用率。
- WAN 最佳化工具 - HCX 包括一個選擇性部署的 Silver Peak™ WAN 最佳化應用裝置。它部署為 VM 應用裝置。部署時，CGW 通道資料流量會重新導向，以遍訪 WAN 最佳化工具配對。由於 WAN 最佳化工具會大幅降低 WAN（通常看到是 3:1 到 6:1）的資料流量，同時增加連線可靠性，因此建議一律使用 CGW 來部署 WAN 最佳化工具。部署 WAN 最佳化工具的另一個好處延伸為限制 VM 移轉資料流量耗用的 WAN 頻寬。依預設，不會配置 WAN 最佳化工具管理介面。
- Proxy ESX 主機 - 每當 CGW 配置為連接至雲端 HCX 網站時，Proxy ESXi 主機會出現在 vCenter 的任何叢集之外。此 ESXi 主機與對應的 CGW 應用裝置具有相同的管理及 vMotion IP 位址。這可讓用戶端及雲端的 vSphere 環境運作，就像執行本端 vMotion 一樣。此方法的好處：
    - 任一端的管理 IP 範圍可能重疊，但功能不受損。
    - 雲端對用戶端沒有任何 vSphere 可見性，因此更加安全。

## HCX 使用者入口網站
{: #vcshcx-components-hcx-user-portals}

- 用戶端 Web 使用者介面 - HCX 用戶端 Web 入口網站是 HCX 的主要使用者介面。安裝用戶端 HCX Manager 之後，它會顯示為 vCenter Web 使用者介面的嵌入式管理單元。它控制遠端雲端 HCX 登錄（網站配對）、機群元件部署、網路延伸，以及進出雲端的 VM 移轉。

- 雲端使用者介面 - 可透過提供給 HCX 用戶端登錄的公用登錄 URL，來存取雲端 HCX 使用者介面。依預設，它會使用雲端 vSphere SSO 登入 (`administrator@vsphere.local`)。它通常是用來升級安裝及修改部分網路配置。它也用於 HCX 中建置虛擬網路。

- 用戶端 / 雲端 HCX Manager 應用裝置管理使用者介面 - 透過 vCenter 中所看見的 VM 專用 IP 位址，存取雲端的或用戶端的應用裝置管理使用者介面。`https://<hcxmanager_IP>:9443`. ID（通常是“admin”）和密碼是透過 {{site.data.keyword.vmwaresolutions_short}} 入口網站提供。此管理使用者介面是用來啟動和停止 HCX Manager 服務、配置日誌監視、基本網路配置、手動升級、當 Web 使用者介面不能發揮作用時支援日誌收集、登錄 vSphere 元件（vCenter、PSC、NSX Manager）及憑證管理。

## 相關鏈結
{: #vcshcx-components-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
