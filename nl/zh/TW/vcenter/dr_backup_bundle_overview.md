---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

keywords: single-node trial, data protection DR, tech specs data protection DR

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Data Protection and Disaster Recovery 單一節點試用版概觀
{: #dr_backup_bundle_overview}

利用 Data Protection and Disaster Recovery 單一節點試用版，容許您測試 {{site.data.keyword.cloud}} 以將 VMware 工作負載移轉和回復到 {{site.data.keyword.cloud_notm}}。此外，Data Protection and Disaster Recovery 單一節點試用版包含 Veeam on {{site.data.keyword.cloud_notm}}、VMware HCX on {{site.data.keyword.cloud_notm}} 和 Zerto on {{site.data.keyword.cloud_notm}} 服務。

單一節點試用版是 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的試用版，提供了單一承租戶 VMware 平台，可使用與內部部署環境中相同的工具來管理該平台。您可以充分運用雲端的速度及規模，同時維護在內部部署提供之相同層次的控制權及可見性。

該試用版旨在使用 vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 來移轉最多 20 個簡單的開發或測試工作負載。自動化功能將在 {{site.data.keyword.cloud_notm}} 中安裝和配置 VMware HCX，提供內部部署 HCX 啟動鍵，並在幾小時內安裝 Veeam on {{site.data.keyword.cloud_notm}} 和 Zerto on {{site.data.keyword.cloud_notm}}。您可以使用 Veeam on {{site.data.keyword.cloud_notm}} 和 Zerto on {{site.data.keyword.cloud_notm}} 來備份和抄寫 20 個虛擬機器 (VM)。

Data Protection and Disaster Recovery 單一節點試用版僅用於概念驗證 (POC)。不要在此環境中執行正式作業工作負載。新增及移除主機和叢集、訂購其他附加程式服務，以及套用更新項目等管理功能皆不受支援。
{:important}

部署單一節點試用版實例之後，可以使用 [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:external} 提供的 [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:external} 來輔助使用實例。此外，[{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:external} 還可協助您透過最新的雲端原生作法來加速應用程式現代化。

此試用版最多可使用 90 天。每月週期性計費會根據您的計費排定來計費，而不是在訂購實例時計費。如果在計費週期的最後一天或之前未取消實例，將向您收取下個月的費用。90 天試用可能會收取四個月的費用，除非在第四個月開始之前完成取消。
{:note}

完成試用後，您可以刪除此環境，然後佈建符合您容量需求的新環境。


## Data Protection and Disaster Recovery 單一節點試用版實例的技術規格
{: #dr_backup_bundle_overview-tech-specs}

Data Protection and Disaster Recovery 單一節點試用版實例中包含下列元件。

標準化硬體配置的可用性及定價可能會根據選取以用於部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。
{:note}

### Bare Metal Server
{: #dr_backup_bundle_overview-bare-metal}

Skylake 雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，含 384 GB RAM 的 2.2 GHz，最多大約 20 部 VM

#### CPU 過度確認
{: #dr_backup_bundle_overview-cpu}

16:1 CPU 過度確認，適用於 vCenter Server 管理、HCX 及 20 部客戶工作負載 VM

#### RAM 過度確認
{: #dr_backup_bundle_overview-ram}

* 1.22:1 RAM 過度確認，適用於各含 8 GB 之 20 部工作負載 VM 的客戶部署
* 1:1（無過度確認），適用於各含 8 GB 之 9 部工作負載 VM 的客戶部署

### NFS 儲存空間
{: #dr_backup_bundle_overview-nfs-storage}

* 2 TB 用於管理
* 1 TB 用於客戶工作負載（適用於 20 部客戶 VM）

### Data Protection and Disaster Recovery 單一節點試用版實例的網路連線功能規格
{: #dr_backup_bundle_overview-networking-specs}

訂購了下列網路元件：
*  10 Gbps 雙重公用及專用網路上行鏈路
*  三個 VLAN（虛擬 LAN）：一個公用 VLAN 和兩個專用 VLAN
*  一個具有 DLR（分散式邏輯路由器）的 VXLAN (Virtual eXtensible LAN)，以便在連接至第 2 層 (L2) 網路的本端工作負載之間，進行潛在的東西向通訊。VXLAN 是部署成一個遞送拓蹼範例，您可以加以修改、在其上進行建置，或是移除它。您也可以藉由將其他 VXLAN 連接到 DLR 上的新邏輯介面，來新增安全區域。
*  兩個 VMware NSX Edge Services Gateway：
  * 用於出埠 HTTPS 管理資料流量的安全管理服務 VMware NSX Edge Services Gateway (ESG)，IBM 將它部署為管理網路拓蹼的一部分。IBM 管理 VM 使用此 ESG，以與跟自動化相關的特定外部 IBM 管理元件進行通訊。

    您無法存取此 ESG，因此無法使用它。如果您修改它，則可能無法從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 Data Protection and Disaster Recovery 單一節點試用版實例。此外，請注意，使用防火牆或停用與外部 IBM 管理元件的 ESG 通訊，將導致 {{site.data.keyword.vmwaresolutions_short}} 變成無法使用。
    {:important}
  * 用於出埠和入埠 HTTPS 工作負載資料流量的安全客戶管理 VMware NSX Edge Services Gateway，IBM 將它部署為範本，您可以修改它來提供 VPN 存取或公用存取。

### 虛擬伺服器實例
{: #dr_backup_bundle_overview-vsi}

已訂購下列虛擬伺服器實例 (VSI)：

* IBM CloudBuilder 的 VSI，在完成實例部署之後會取消它。
* 已部署並可查閱 Microsoft Windows Server VSI for Microsoft Active Directory (AD)。VSI 是作為登錄主機及 VM 之實例的 DNS。
* Zerto on {{site.data.keyword.cloud_notm}} 的 VSI - Zerto Virtual Manager。
* 具有 Veeam Backup and Replication 9.5 附加程式和 Veeam Availability Suite 9.5 的 VSI。

### IBM 提供的授權及費用
{: #dr_backup_bundle_overview-license-and-fee}

Data Protection and Disaster Recovery 單一節點試用版實例訂單中包含下列授權。

* vCenter Server with Hybridity Bundle 授權：
  * VMware vSphere Enterprise Plus 6.7u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Data Protection and Disaster Recovery 單一節點試用版實例不支援「自帶授權」。
{:note}

## VMware HCX on IBM Cloud 的技術規格
{: #dr_backup_bundle_overview-hcx-tech-specs}

Data Protection and Disaster Recovery 單一節點試用版包含 HCX on {{site.data.keyword.cloud_notm}}。下列元件已訂購並包括在 HCX on {{site.data.keyword.cloud_notm}} 服務中。

內部部署 HCX 實例只包括授權及啟動。
{:note}

### 用於 HCX 管理的 VMware NSX Edge Services Gateway 主動/被動配對
{: #dr_backup_bundle_overview-esg}

* CPU：6 個 vCPU
* RAM：8 GB
* 磁碟：3 GB VMDK

### HCX 管理應用裝置 - 虛擬機器
{: #dr_backup_bundle_overview-hcx-mgmt-appliance}

* CPU：4 個 vCPU
* RAM：12 GB
* 磁碟：60 GB VMDK

視需要，在配置進行 L2 連線功能、WAN 最佳化及閘道連線期間，會部署其他的 HCX 應用裝置。

### HCX on IBM Cloud 的網路規格
{: #dr_backup_bundle_overview-hcx-networking-specs}

* 一個具有 16 個 IP 位址的公用可攜式子網路
* 兩個具有 64 個 IP 位址的專用可攜式子網路
* 來自專用可攜式 vMotion 子網路的八個 IP 位址

## Veeam on {{site.data.keyword.cloud_notm}} 的技術規格
{: #dr_backup_bundle_overview-veeam-tech-specs}

Data Protection and Disaster Recovery 單一節點試用版包含 Veeam on {{site.data.keyword.cloud_notm}}。Veeam on {{site.data.keyword.cloud_notm}} 服務中訂購並包含了下列元件。

* Veeam Availability Suite 的 25 個套件授權
* 4000 GB 儲存空間
* 0.25 IOPS/GB 儲存空間效能
* Windows Server 2016 Standard Edition（64 位元）
* 4 x 2.0 GHz 核心
* 8 GB RAM
* 1 Gbps 專用網路上行鏈路
* 100 GB 磁碟 (SAN)

## Zerto on {{site.data.keyword.cloud_notm}} 的技術規格
{: #dr_backup_bundle_overview-zerto-tech-specs}

Data Protection and Disaster Recovery 單一節點試用版包含 Zerto on {{site.data.keyword.cloud_notm}}。下列元件已訂購並包括在 Zerto on {{site.data.keyword.cloud_notm}} 服務中。

* Zerto Virtual Replication 6.5u3 版授權
* 一個虛擬服務實例 (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz 核心
* 4 GB RAM
* Windows Server 2016 Standard Edition（64 位元）
* 100 GB (SAN) 磁碟

## IBM Cloud Automation Manager 的技術規格
{: #dr_backup_bundle_overview-cam-tech-specs}

在所有 Data Protection and Disaster Recovery 單一節點試用版實例上，都會使用開發/測試拓蹼安裝 {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2。如需 {{site.data.keyword.cloud_notm}} Automation Manager 的相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} Automation Manager 文件](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: external}。

## 相關鏈結
{: #dr_backup_bundle_overview-related}

* [VMware HCX 資源](https://hcx.vmware.com/#/docs){:external}
* [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [管理 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)
