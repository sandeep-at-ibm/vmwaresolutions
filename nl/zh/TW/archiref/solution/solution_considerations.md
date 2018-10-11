---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# VMware 實例的部署後考量

{{site.data.keyword.vmwaresolutions_full}}、VMware vCenter Server 及 VMware Cloud Foundation 供應項目不是受管理服務。您負責配置、保護、管理及監視所有軟體元件。您具備對解決方案的完整管理存取權，因此擁有非常強大的能力和彈性，但需要跨各種領域的大量技術、管理及作業專門知識。在 {{site.data.keyword.cloud_notm}} 中管理 VMware 實例，需要與規劃內部部署實例相同的規劃及專門知識。VMware NSX 及 VMware vSAN 這類軟體定義的技術可大幅簡化實例管理的某些方面，但可能需要適當地管理及操作新的技能及工具。結合 {{site.data.keyword.cloud_notm}} 自動化 VMware 部署的能力、速度和可靠性與適當的作業規劃和測試，確保可快速且成功地導覽至混合式雲端。

請檢閱下列考量，以瞭解您在部署實例前後管理及操作實例的責任。 

**附註：**下列並非完整清單。如需相關資訊，請參閱 [IBM 的受管理服務](../../services/managing_imi.html)。

## IBM Cloud 帳戶存取

為了管理您 {{site.data.keyword.cloud_notm}} 帳戶的存取權，請允許您團隊的其他成員在 {{site.data.keyword.vmwaresolutions_short}} 主控台中存取您的實例。如需相關資訊，請參閱[邀請使用者存取服務及資源](../../vmonic/iamuserinvite.html)。

## 限制

請充分瞭解您實例的下列限制：

- [變更 vCenter 構件的影響](../../vcenter/vcenter_chg_impact.html)
- [網路考量及限制](../../vcenter/vc_networkingonvcenterserver.html)
- [常見問題](../../vmonic/faq.html)

## 網路設計及連線功能

完成下列步驟，以管理對您 {{site.data.keyword.cloud_notm}} 網路及 VMware 管理元件的存取，並規劃 {{site.data.keyword.cloud_notm}} 網路拓蹼。

- 使用 [{{site.data.keyword.cloud_notm}} VPN](https://www.softlayer.com/vpn-access) 或 [{{site.data.keyword.cloud_notm}} Direct-Link 連線](https://www.ibm.com/cloud/direct-link)來存取實例管理端點。
- 設計您實例內的公用網路連線功能策略。您的選項包括：範例客戶 VMware NSX Edge Services Gateway (ESG)、閘道應用裝置（例如 Vyatta 和 FortiGate），以及在 {{site.data.keyword.cloud_notm}} 網路中或透過 DirectLink 存取的專屬網路上所部署的 Proxy 伺服器。
- 規劃要在具有 [{{site.data.keyword.cloud_notm}} 可攜式 IP 位址](https://console.bluemix.net/docs/infrastructure/subnets/getting-started.html)的 {{site.data.keyword.cloud_notm}} VLAN 上部署工作負載，還是[在 NSX 邏輯交換器 (VXLAN) 上使用您自己的 IP 位址](../nsx/nsx_overview.html)來部署工作負載。請注意，使用 NSX 軟體定義網路 (SDN) 可讓您具有在 {{site.data.keyword.cloud_notm}} 中管理及保護工作負載網路的最大彈性。
- 使用 NSX ESG、[IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance) 及 DirectLink 對等作業，來規劃與工作負載（網址轉換、虛擬專用網路、遞送）的連線功能。
- 如果實作「跨 vCenter NSX」，請先確定本端區段 ID 範圍未重疊，再部署任何本端工作負載。

## 安全規劃及強化

您負責保護、加密及監視 VMware 實例和工作負載，以符合公司、產業及法規標準。請完成下列步驟，以確保適當的安全性。

- 變更 {{site.data.keyword.vmwaresolutions_short}} 主控台中顯示的所有密碼，並使用您自己的密碼管理系統。請注意，IBM 會保留進行自動化及支援所需的特殊使用者 ID。
- 檢閱所有元件的密碼原則（例如複雜性及有效期限）。
- 檢閱所有元件的加密設定。
- 規劃並實作適當的實體或虛擬防火牆解決方案（例如 NSX Distributed Firewall (DFW)、NSX ESG、[Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../../services/fortinetvm_considerations.html) 及 [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance)）。
- 規劃並實作適當的應用程式負載平衡及安全解決方案（例如 [F5 on {{site.data.keyword.cloud_notm}}](../../services/f5_considerations.html)）。
- 規劃並實作適當的安全資訊及事件管理 (SIEM) 解決方案（例如 [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence)）。
- 規劃並實作適當的漏洞掃描。
- 使用 [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../../services/htcc_considerations.html) 這類解決方案，規劃並實作您實例的適當變更管理、核准、審核及存取控制。

## 自訂

請完成下列步驟來自訂基本 VMware 實例安裝，以符合您的需求。

- 使用您自己的憑證管理中心 (CA) 來產生元件（例如 vCenter、VMware Platform Services Controller (PSC) 及 NSX Manager）的憑證。
- 配置已部署的服務。例如：
  - 針對 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}，配置 AD 整合、存取控制、「簡易郵件傳送通訊協定 (SMTP)」設定及規範原則。
  - 針對 Zerto on {{site.data.keyword.cloud_notm}}，規劃 IP 定址及遞送「Zerto Virtual Replication 應用裝置 (VRA)」通訊，因為不支援網址轉換器 (NAT) 遍訪。請考量通道處理或重新部署您的 VRA，以進行適當的定址及遞送。
  - 針對備份服務（例如 Veeam on {{site.data.keyword.cloud_notm}} 及 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}），配置備份工作，並選擇性地配置其他儲存空間，然後配置監視警示。
  - 針對網路及安全服務（例如 F5 on {{site.data.keyword.cloud_notm}} 及 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}），根據您的網路拓蹼及其他需求來配置網路介面、憑證、高可用性 (HA) 配置和規則。

## Active Directory

請完成下列步驟，以確保適當的單一登入 (SSO) 配置及管理。

- 配置 Active Directory (AD) 伺服器更新及重新開機排程。
- 如果您已選擇將 AD 伺服器部署至 vSphere 叢集，請提供伺服器的 Microsoft Windows 授權及啟動，以確保相符性及可用性。
- 建立實例與內部部署 AD 伺服器之間的相互信任。
- 整合 NSX VPN（適用時）與 AD SSO。
- 整合 ESXi 主機與 AD SSO。

## 維護規劃

請完成下列步驟，以確保適當的軟體維護規劃。

- 透過 Proxy 設定 VMware Update Manager (VUM)，以取得 VMware 更新項目。
- 適用時，透過 Proxy 設定 vSAN，以維護「vSAN 硬體相容性清單 (HCL)」資料庫。
- 規劃定期維護 VUM 不支援的 VMware 元件。例如，VMware vCenter、PSC 及 NSX。
- 檢閱「vSphere 加強型 vMotion 相容性 (EVC)」配置。如果 vSphere 的現行版本不支援硬體層次的 EVC，則可能無法配置已啟用 EVC 的叢集。
- 規劃定期維護附加程式服務（例如 Veeam on {{site.data.keyword.cloud_notm}}、Zerto on {{site.data.keyword.cloud_notm}} 及 F5 on {{site.data.keyword.cloud_notm}}）。

## 監視

確定規劃並實作下列解決方案，以監視您的實例及實例元件。

- 記載伺服器，包括所有實例元件的日誌轉遞或收集以及足夠的日誌保留。
- 警示基礎架構，包括配置 SMTP 伺服器及短訊服務 (SMS) 閘道（視需要）。
- 主動監視主機、磁碟機、管理軟體及網路。
- vSAN 監視（適用時）。
- 容量監視及規劃。您可以從 {{site.data.keyword.vmwaresolutions_short}} 主控台，在實例中[新增及移除叢集](../../vcenter/vc_addingviewingclusters.html)以及[新增及移除主機](../../vcenter/vc_addingremovingservers.html)。
- 監視備份基礎架構及備份工作。

## 企業永續及可用性

您的 VMware 實例是在 {{site.data.keyword.cloud_notm}} 的 Bare Metal Server 上執行。請完成下列步驟，以確保您對高可用性和企業永續進行足夠的規劃。

- 根據您的需求，檢閱 vSphere HA 及「vSphere 分散式資源排程器 (DRS)」配置。
- 根據您的需求，檢閱網路及儲存空間 I/O 控制配置。
- 根據您的需求，配置虛擬機器啟動順序。
- 視需要，配置管理及工作負載的資源儲存區。
- 規劃、實作及監視[實例管理元件](solution_backingup.html)和工作負載的備份解決方案。
- 規劃實例管理的高可用性（包括多個實例、多個叢集、vCenter HA 及 PSC HA 的可能性）。
- 使用 [Zerto 災難回復](../../services/addingzertodr.html)、[Veeam Backup and Replication](../../services/veeam_considerations.html) 及 [IBM Spectrum Protect Plus](../../services/spp_considerations.html) 這類解決方案，規劃您工作負載的企業永續。

## 儲存空間規劃

除了容量規劃之外，也請完成下列動作，以確保您的儲存空間配置符合您的效能及可用性需求。

- 儲存空間效能取決於各種因素，包括 RAID 配置及磁碟分段；網路配置；區塊大小；網路連接儲存空間的已配置 IOPS（每秒輸入/輸出作業）；儲存空間連接的 VM 硬體配置及方法；叢集處理及抄寫方法；以及使用儲存空間原則（例如加密、刪除重複資料及壓縮）。規劃時間，以測試及調整配置來符合儲存空間效能需求。
- 檢閱 vSAN 儲存空間原則
  - 針對容易發生的循序失敗（例如較短的重建時間），RAID-1 提供比 RAID-5 更佳的效能及更短的時間範圍。不過，RAID-5 的儲存空間額外負擔較少。
  - 相較於 RAID-5 的 4 部主機，RAID-6 提供對雙重失敗的保護，但最少需要 6 部主機。
- 若要將更多儲存空間新增至 vSAN 叢集，您必須將新的主機新增至叢集，或改為新增「{{site.data.keyword.cloud_notm}} 耐久性」NFS 儲存空間。目前不支援將磁碟新增至現有主機。
- 如果您將額外的「{{site.data.keyword.cloud_notm}} 耐久性」NFS 儲存空間裝載至叢集，請確定遵循架構指引，並使用 `SDDC-DPortGroup-NFS` 埠群組位址，將主機路徑配置到儲存空間。您必須將這些位址（而非主機本身）授權給儲存空間。如需相關資訊，請參閱[連接儲存空間基礎架構管理](../attached-storage/storage-infra-mgmt.html#vsphere-host-static-routing)。另請參閱 developerWorks 秘訣，其使用 IBM Spectrum Protect Plus 作為範例顯示如何[將更多耐久性儲存空間新增至 VMware 叢集](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)。

### 相關鏈結

* [解決方案概觀](solution_overview.html)
* [設計概觀](design_overview.html)
* [調整容量](solution_scaling.html)

