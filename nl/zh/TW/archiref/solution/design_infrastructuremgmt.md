---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-13"

---

# 基礎架構管理設計

基礎架構管理是指管理 VMware 基礎架構的元件。此設計使用單一外部 Platform Services Controller (PSC) 實例及單一 vCenter Server 實例：
* vCenter Server 是用於管理 vSphere 環境的集中化平台，並且是此解決方案中的其中一個基礎元件。
* 此解決方案中運用 PSC 以提供一組基礎架構服務（包括 VMware vCenter Single Sign On、授權服務、查閱服務及「VMware 憑證管理中心」）。

PSC 實例及 vCenter Server 實例是不同的虛擬機器 (VM)。

## PSC 設計

此設計會在與管理 VM 相關聯之專用 VLAN 的可攜式子網路上，將單一外部 PSC 部署為虛擬應用裝置。其預設閘道設為後端客戶路由器 (BCR)。虛擬應用裝置已配置下表中的規格。

**附註**：這些值是在部署時設定的，無法變更。

表 1. Platform Services Controller 規格

| 屬性                         | 規格                           |
|------------------------------|--------------------------------|
|Platform Services Controller    | 虛擬應用裝置                   |
| vCPU 數目                    |2 |
|記憶體| 4 GB                           |
| 磁碟                         | 本端 VMFS 資料儲存庫上 114 GB|
| 磁碟類型                     | 精簡佈建                     |

位於主要實例的 PSC 會獲指派預設 SSO 網域 `vsphere.local`。

## vCenter Server 設計

vCenter Server 也會部署為虛擬應用裝置。此外，vCenter Server 會安裝在與管理 VM 相關聯之專用 VLAN 的可攜式子網路上。其預設閘道設為該特定子網路之 BCR 上所指派的 IP 位址。虛擬應用裝置已配置下表中的規格。

表 2. vCenter Server Appliance 規格

| 屬性                         | 規格                                |
|------------------------------|-------------------------------------|
|vCenter Server | 虛擬應用裝置                   |
| 應用裝置安裝大小             | 中型（最多 400 部主機、4,000 部 VM）|
|Platform Services Controller    | 外部                                |
| vCPU 數目                    | 8                                   |
|記憶體| 24 GB                               |
| 磁碟                         | 本端資料儲存庫上 400 GB             |
| 磁碟類型                     | 精簡佈建                            |

### vCenter Server 資料庫

vCenter Server 配置會使用應用裝置隨附的本端內嵌 PostgreSQL 資料庫。內嵌資料庫用來移除任何與外部資料庫及授權的相依關係。

### vCenter Server 叢集規格

此設計可讓您叢集處理透過解決方案所佈建的 vSphere ESXi 主機。不過，建立叢集之前，會先建立資料中心物件，用於表示 vSphere ESXi 主機的位置以及資料中心內的 Pod。建立資料中心物件之後，會建立叢集。叢集已部署啟用「VMware vSphere 高可用性 (HA)」及「VMware vSphere 分散式資源排程器 (DRS)」。

### vSphere 分散式資源排程器

此設計使用起始叢集裡的「vSphere 分散式資源排程 (DRS)」來放置 VM，並在其他叢集裡使用 DRS 動態移轉 VM，以達到平衡的叢集。自動化層次設為完全自動化，以由 vSphere 自動執行起始放置及移轉建議。此外，移轉臨界值設為 moderate，因此 vCenter 將在叢集的負載平衡中套用優先順序 1、2、3 建議，以達到至少適當的改善。

**附註：**在此設計中，不使用透過**分散式電源管理**特性的電源管理。

### vSphere 高可用性

此設計使用起始叢集及其他叢集裡的「vSphere 高可用性 (HA)」來偵測運算失敗，以及回復在叢集內執行的 VM。已配置此設計中的 vSphere HA 特性，在叢集內啟用**主機監視**及**許可控制**選項。此外，起始叢集會保留其中一個節點的資源，作為許可控制原則的備用容量。

**附註**：稍後展開或收合叢集時，您負責調整許可控制原則。

依預設，**VM 重新啟動優先順序**選項設為 medium，並停用**主機隔離回應**選項。此外，還會停用 **VM 監視**，而且**資料儲存庫活動訊號**特性配置成包括任何叢集資料儲存庫。此方式會使用 NAS 資料儲存庫（如果它們已存在）。

## 自動化

這些解決方案的基礎是自動化。自動化具有下列優點：
* 減少部署的複雜性。
* 大幅減少部署時間。
* 確定以一致的方式部署 VMware 實例。

{{site.data.keyword.IBM}} CloudBuilder、IBM CloudDriver 及 SDDC Manager VM 搭配運作，以啟動新的 VMware 實例，並執行生命週期管理功能。

### IBM CloudBuilder 及 IBM CloudDriver

IBM CloudBuilder 及 IBM CloudDriver 虛擬伺服器實例 (VSI) 是您無法存取的 IBM 開發元件。
* IBM CloudBuilder 是一個暫時的 {{site.data.keyword.cloud_notm}} 虛擬伺服器實例 (VSI)，可引導部署、配置及驗證已佈建之裸機 ESXi 主機內的解決方案元件。
* IBM CloudDriver VSI 是針對實例建立部署，然後視需要定期使用最新的 {{site.data.keyword.cloud_notm}} for VMware 程式碼來進行部署其他節點、叢集或服務這類作業。IBM CloudDriver 透過專為實例管理所部署的 VMware NSX Edge Services Gateway 與 {{site.data.keyword.vmwaresolutions_short}} 主控台通訊，並作為維護實例的代理程式。IBM CloudDriver 負責進行中的動作，例如將新的裸機主機新增至叢集，以及將附加程式服務部署至實例。對於 Cloud Foundation 實例，IBM CloudDriver 會與 VMware SDDC Manager VM 通訊，以執行主機新增及修補這類功能。

使用者可能會刪除或損壞下列各節所述的 VM。VM 在移除、關閉或無法作業時，會岔斷 {{site.data.keyword.vmwaresolutions_short}} 主控台上的下列 Cloud Foundation 或 vCenter Server 作業：
* 檢視實例或主機狀態
* 新增或移除叢集
* 新增或移除 ESXi 主機
* 新增或移除服務
* 修補

### SDDC Manager                             

對於 Cloud Foundation 實例，SDDC Manager VM 是 VMware 所開發及維護的元件。在實例的整個生命週期期間，它仍然會保留為實例的一部分。它負責下列實例生命週期功能：
* 管理 VMware 元件：vCenter Server、Platform Services Controller (PSC)、vSAN 及 NSX（包括 IP 位址配置及主機名稱解析）。
* 在叢集內擴充及重新擷取 ESXi 主機，包括任何受影響的服務（例如 NSX VTEP、vSAN、資源儲存區）。

對於 vCenter Server 實例，IBM CloudDriver 會執行這些活動，因為沒有 SDDC Manager。

### 自動化流程

下列程序說明透過 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購 VMware 實例時的事件順序：
1.  從 {{site.data.keyword.cloud_notm}} 訂購 VLAN 及子網路來連接網路。
2.  訂購已安裝 vSphere Hypervisor 的 {{site.data.keyword.baremetal_short}}。
3.  訂購 Microsoft Windows Virtual Server Instance (VSI) 以作為 Active Directory 網域控制站（適用時）。
4.  驗證網路及已部署的硬體。
5.  單一節點 vSAN 的起始配置（適用時）。
6.  部署及配置兩部 Microsoft Windows 虛擬機器，以作為 Active Directory 網域控制站（適用時）。
7.  部署及配置 vCenter、PSC 和 NSX。
8.  叢集處理剩餘的 ESXi 節點、擴充 vSAN（適用時），以及配置 NSX 元件 (VTEP)。
9.  部署 VMware Cloud Foundation SDDC Manager VM（適用時）及 IBM CloudDriver VSI。
10.  驗證環境的安裝及配置。
11. 移除 CloudBuilder VSI。
12. 部署選用服務（例如備份伺服器及儲存空間）。

### 相關鏈結

* [實體基礎架構設計](design_physicalinfrastructure.html)
* [虛擬基礎架構設計](design_virtualinfrastructure.html)
* [常見服務設計](design_commonservice.html)
