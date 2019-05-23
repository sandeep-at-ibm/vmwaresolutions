---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 單一節點試用版移轉及應用程式現代化概觀
{: #cloud_modern_bundle_overview}

「單一節點試用版移轉及應用程式現代化」可讓您測試磁碟機 {{site.data.keyword.cloud_notm}} 以將 VMware 工作負載移轉至 {{site.data.keyword.cloud}}，然後使用容器來現代化簡單工作負載。

「單一節點試用版」是 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 上的 {{site.data.keyword.cloud_notm}} Private Hosted 試用版本，提供容器的 Kubernetes 管理平台，以及可使用與內部部署環境相同之工具所管理的單一承租戶 VMware 平台。您可以充分運用雲端的速度及規模，同時維護在內部部署提供之相同層次的控制權及可見性。

試用版設計成使用 vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 來移轉最多 20 個簡單開發或測試工作負載，以及使用 Kubernetes 型 {{site.data.keyword.cloud_notm}} Private Hosted 應用程式開發平台來容器化這些工作負載。自動化將會在 {{site.data.keyword.cloud_notm}} 中安裝及配置 VMware HCX，提供內部部署 HCX 啟動金鑰，然後只要數小時就能安裝及配置 {{site.data.keyword.cloud_notm}} Private Hosted 的小型開發/測試拓蹼。

「單一節點試用版移轉及應用程式現代化」僅用於概念證明 (POC)。不要在此環境中執行正式作業工作負載。新增及移除主機和叢集、訂購附加服務，以及套用更新項目這類管理功能皆不受支援。
{:important}

若要充分了解「單一節點試用版」實例，您可以從可協助您將 VMware 工作負載移轉至 {{site.data.keyword.cloud_notm}} 的 [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:new_window}，使用 [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:new_window}。此外，[{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:new_window} 還可協助您透過最新的雲端原生作法來加速應用程式現代化。

此試用版最多可使用 90 天。完成試用後，您可以刪除此環境，然後佈建符合您容量需求的新環境。
{:note}

## 單一節點試用版移轉及應用程式現代化實例的技術規格
{: #cloud_modern_bundle_overview-tech-specs}

下列元件內含在「單一節點試用版移轉及應用程式現代化」實例中。

標準化硬體配置的可用性及定價可能會根據選取以用於部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。
{:note}

### Bare Metal Server
{: #cloud_modern_bundle_overview-bare-metal}

雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，含 384 GB RAM 的 2.2 GHz，最多大約 20 部 VM

#### CPU 過度確認
{: #cloud_modern_bundle_overview-cpu}

* 16:1 CPU 過度確認，適用於 vCenter Server 管理、HCX 及 20 部客戶工作負載 VM
* 11:1 CPU 過度確認，適用於 {{site.data.keyword.cloud_notm}} Private

#### RAM 過度確認
{: #cloud_modern_bundle_overview-ram}

* 1.22:1 RAM 過度確認，適用於各含 8 GB 之 20 部工作負載 VM 的客戶部署
* 1:1（無過度確認），適用於各含 8 GB 之 9 部工作負載 VM 的客戶部署

### NFS 儲存空間
{: #cloud_modern_bundle_overview-nfs-storage}

* 2 TB 用於管理
* 1 TB 用於客戶工作負載（適用於 20 部客戶 VM）
* 4 TB 用於 {{site.data.keyword.cloud_notm}} Private Hosted

### 單一節點試用版移轉及應用程式現代化實例的網路規格
{: #cloud_modern_bundle_overview-networking-specs}

訂購了下列網路元件：
*  10 Gbps 雙重公用及專用網路上行鏈路
*  三個 VLAN（虛擬 LAN）：一個公用 VLAN 和兩個專用 VLAN
*  一個具有 DLR（分散式邏輯路由器）的 VXLAN (Virtual eXtensible LAN)，以便在連接至第 2 層 (L2) 網路的本端工作負載之間，進行潛在的東西向通訊。VXLAN 是部署成一個遞送拓蹼範例，您可以加以修改、在其上進行建置，或是移除它。您也可以藉由將其他 VXLAN 連接到 DLR 上的新邏輯介面，來新增安全區域。
*  兩個 VMware NSX Edge Services Gateway：
  * 用於出埠 HTTPS 管理資料流量的安全管理服務 VMware NSX Edge Services Gateway (ESG)，IBM 將它部署為管理網路拓蹼的一部分。IBM 管理 VM 使用此 ESG，以與跟自動化相關的特定外部 IBM 管理元件進行通訊。

您無法存取此 ESG，因此無法使用它。如果您修改它，則可能無法從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理「單一節點試用版移轉及應用程式現代化」實例。此外，請注意，使用防火牆或停用與外部 IBM 管理元件的 ESG 通訊，將導致 {{site.data.keyword.vmwaresolutions_short}} 變成無法使用。
{:important}
  * 用於出埠和入埠 HTTPS 工作負載資料流量的安全客戶管理 VMware NSX Edge Services Gateway，IBM 將它部署為範本，您可以修改它來提供 VPN 存取或公用存取。

### 虛擬伺服器實例
{: #cloud_modern_bundle_overview-vsi}

已訂購下列虛擬伺服器實例 (VSI)：

* IBM CloudBuilder 的 VSI，在完成實例部署之後會取消它。
* 已部署並可查閱 Microsoft Windows Server VSI for Microsoft Active Directory (AD)。VSI 是作為登錄主機及 VM 之實例的 DNS。

### IBM 提供的授權及費用
{: #cloud_modern_bundle_overview-license-and-fee}

「單一節點試用版移轉及應用程式現代化」實例訂購隨附下列授權。

* VMware vSphere Enterprise Plus 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

「單一節點試用版移轉及應用程式現代化」實例不支援「自帶授權」。
{:note}

## VMware HCX on IBM Cloud 的技術規格
{: #cloud_modern_bundle_overview-hcx-tech-specs}

「單一節點試用版移轉及應用程式現代化」包括 HCX on {{site.data.keyword.cloud_notm}}。下列元件已訂購並包括在 HCX on {{site.data.keyword.cloud_notm}} 服務中。

內部部署 HCX 實例只包括授權及啟動。
{:note}

### 用於 HCX 管理的 VMware NSX Edge Services Gateway 主動/被動配對
{: #cloud_modern_bundle_overview-esg}

* CPU：6 個 vCPU
* RAM：8 GB
* 磁碟：3 GB VMDK

### HCX 管理應用裝置 - 虛擬機器
{: #cloud_modern_bundle_overview-hcx-mgmt-appliance}

* CPU：4 個 vCPU
* RAM：12 GB
* 磁碟：60 GB VMDK

視需要，在配置進行 L2 連線功能、WAN 最佳化及閘道連線期間，會部署其他的 HCX 應用裝置。

### HCX on IBM Cloud 的網路規格
{: #cloud_modern_bundle_overview-hcx-networking-specs}

* 一個具有 16 個 IP 位址的公用可攜式子網路
* 兩個具有 64 個 IP 位址的專用可攜式子網路
* 來自專用可攜式 vMotion 子網路的八個 IP 位址

## IBM Cloud Private Hosted 的技術規格
{: #cloud_modern_bundle_overview-icp-tech-specs}

{{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 是使用「開發/測試」拓蹼安裝在所有「單一節點試用版移轉及應用程式現代化」實例上。如需 {{site.data.keyword.cloud_notm}} Private Hosted 的相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} Private Hosted 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)。

## IBM Cloud Automation Manager 的技術規格
{: #cloud_modern_bundle_overview-cam-tech-specs}

{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 是使用「開發/測試」拓蹼安裝在所有「單一節點試用版移轉及應用程式現代化」實例上。如需 {{site.data.keyword.cloud_notm}} Automation Manager 的相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} Automation Manager 文件](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: new_window}。

## 相關鏈結
{: #cloud_modern_bundle_overview-related}

* [vCenter Server 和 {{site.data.keyword.cloud_notm}} Private 手冊](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [開立 {{site.data.keyword.cloud_notm}} Private 的問題單](https://www.ibm.com/mysupport/s/?language=en_US){:new_window}
* [VMware HCX 資源](https://hcx.vmware.com/#/docs){:new_window}
* [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:new_window}
