---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# HCX 元件和術語的名詞解釋
{: #hcxclient-components}

HCX 是由一個雲端（目標或 VCD 環境）及一個以上的用戶端（來源）所組成。每個 vCenter 必須部署一個 HCX 實例，即使部署 HCX 的 vCenter 是鏈結到用戶端或雲端上的相同 SSO 網域亦然。HCX 支援的配置有：一對一、一對多、多對一及多對多。

## 目標端和用戶端
{: #hcxclient-components-cloud-client-side}

HCX 是雲端（目標或 VCD 環境）及用戶端（來源）的概念。

- 目標端 - HCX Cloud Manager 預先部署並配置了網路和運算設定檔，可隨時用於建立服務網。  
- 用戶端 - 任何符合安裝與作業之必要條件的 vSphere 實例。HCX 的用戶端是主節點，它透過其 vCenter Web 用戶端使用者介面 (UI) 嵌入式管理單元，來控制雲端從屬實例。

## HCX Manager
{: #hcxclient-components-hcx-manager}

- 雲端 - HCX Cloud Manager 配置是為了接聽送入的用戶端登錄、管理及控制資料流量。
- 用戶端 - HCX Enterprise Manager 是用戶端特有的 OVA 映像檔，提供用於管理及操作 HCX 的使用者介面功能。用戶端 HCX Manager 負責向雲端 HCX Manager 登錄，以及在用戶端和雲端之間建立管理平面。此外，它還負責將服務網部署在用戶端，並指示雲端執行相同動作。

## 服務網元件
{: #hcxclient-components-fleet}

「HCX 服務網」元件負責建立用戶端與雲端之間的資料和控制平面。在鏡映配對中部署為虛擬機器 (VM) 的服務網是由下列元件組成：

- 交互連接應用裝置 (HCX-IX) - 交互連接應用裝置建立支援 vMotion 和抄寫（大量移轉）資料流量的加密通道。
- WAN Optimizer 應用裝置 (HCX-WAN) - HCX 包含選用擇部署的 Silver Peak™ WAN 最佳化應用裝置。它部署為 VM 應用裝置。部署後，CGW 通道資料流量會被重新導向，以遍訪「WAN 最佳化程式」。由於 WAN 最佳化工具會大幅降低 WAN（通常看到是 3:1 到 6:1）的資料流量，同時增加連線可靠性，因此建議一律使用 CGW 來部署 WAN 最佳化工具。部署 WAN 最佳化工具的另一個好處延伸為限制 VM 移轉資料流量耗用的 WAN 頻寬。依預設，不會配置 WAN 最佳化工具管理介面。
- 網路延伸 (HX-NE) - 提供第 2 層網路延伸功能，啟用內部部署位置和 vSphere 環境之間的移轉（需要將 IP 位址重新指派給 VM）。
- Proxy ESXi 主機 - 每當 HCX-IX 配置為連接至雲端 HCX 網站時，Proxy ESXi 主機會出現在 vCenter 的任何叢集之外。此 ESXi 主機的管理和 vMotion IP 位址與對應的 HCX-IX 應用裝置相同。這可讓用戶端及雲端的 vSphere 環境運作，就像執行本端 vMotion 一樣。此方法的好處：
  - 任一端的管理 IP 範圍可能重疊，但功能不受損。
  - 雲端對用戶端沒有任何 vSphere 可見性，因此更加安全。

## HCX 使用者入口網站
{: #hcxclient-components-hcx-user-portals}

- 用戶端 Web 使用者介面 - HCX 用戶端 Web 入口網站是 HCX 的主要使用者介面。用戶端 HCX Manager 在安裝之後，會顯示為 vCenter Web 使用者介面的嵌入式管理單元。它控制遠端雲端 HCX 登錄（網站配對）、機群元件部署、網路延伸，以及進出雲端的 VM 移轉。
- 雲端使用者介面 - 可透過提供給 HCX 用戶端登錄的公用登錄 URL，來存取雲端 HCX 使用者介面。依預設，會使用雲端 vCenter Admin 認證 `administrator@vsphere.local`。它通常是用來升級安裝及修改部分網路配置。

## 相關鏈結
{: #hcxclient-components-related}

* [VMware HCX on IBM Cloud 的埠存取需求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [準備安裝環境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 用戶端部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 內部部署服務網](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合雲端移轉](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [監視參數及元件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
