---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: vCenter Server NSX-T, NSX-T, tech specs vCenter Server NSX-T

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with NSX-T 概觀
{: #vc_nsx-t_overview}

VMware vCenter Server with NSX-T on {{site.data.keyword.cloud}} 是一個受管理的專用雲端，可將 VMware vSphere 堆疊作為服務來進行遞送。VMWare 環境建置在至少三部的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 上，可提供共用網路連接儲存空間以及專用軟體定義儲存空間選項，而且包含自動部署及配置採用 VMware NSX-T 技術的容易管理的邏輯 Edge 防火牆。

在許多情況下，整個環境可以在一天內佈建完成，且裸機基礎架構可以快速而彈性地擴充運算容量，並依需要擴增及縮減。

部署後，您可以藉由從 {{site.data.keyword.slportal}} 訂購其他「網路檔案系統 (NFS)」檔案共用，以及將它們手動連接至叢集中的所有 ESXi 伺服器，來增加共用儲存空間。

VMware vSAN 也以專用儲存空間選項提供。若要增加 vSAN 叢集的 vSAN 型儲存空間容量，您可以在部署後新增更多 ESXi 伺服器。

vCenter Server with NSX-T 實例僅用於概念證明 (POC) 或沙盤推演測試。不要在此環境中執行正式作業工作負載。不受支援訂購附加服務及套用更新項目等的管理功能。
{:important}

## vCenter Server with NSX-T 架構
{: #vc_nsx-t_overview-archi}

下圖說明三節點 vCenter Server with NSX-T 部署的高階架構和元件。

![vCenter Server with NSX-T 架構](../images/vc_nsx-t_architecture.svg "vCenter Server with NSX-T 架構")

### 實體基礎架構
{: #vc_nsx-t_overview-physical-infras}

這層提供要供虛擬基礎架構使用的實體基礎架構（運算、儲存空間及網路資源）。

### 虛擬化基礎架構（運算及網路）
{: #vc_nsx-t_overview-virtualization-infras}

這層透過不同的 VMware 產品來將實體基礎架構虛擬化：
* VMware vSphere 將實體運算資源虛擬化。
* VMware NSX 是提供邏輯網路元件和虛擬網路的網路虛擬化平台。

### 虛擬化管理
{: #vc_nsx-t_overview-virtualization-mgmt}

這一層由附有內嵌 Platform Services Controller (PSC) 的 vCenter Server Appliance (vCSA)、三個 NSX 節點、三個 NSX Edge Services Gateway (ESG)，以及 IBM CloudDriver 虛擬伺服器實例 (VSI) 所組成。針對將主機新增至環境這類特定作業，視需要依需求部署 CloudDriver VSI。

基礎供應項目與 vCenter Server Appliance 一起部署，其大小調整後可支援最多 400 部主機及最多 4000 部 VM 的環境。相同的 vSphere API 相容工具及 Script 可用來管理 IBM 管理的 VMware 環境。

基本供應項目總共需要 38 個 vCPU 和 128 GB vRAM 保留給虛擬化管理層。VM 的其餘主機容量由多個因素決定，例如，超訂閱率、虛擬機器 (VM) 大小調整，以及工作負載效能需求。

如需架構的相關資訊，請參閱 [{{site.data.keyword.vmwaresolutions_short}} 架構參考資料](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)。

## vCenter Server with NSX-T 實例的技術規格
{: #vc_nsx-t_overview-specs}

下列元件已包含在 vCenter Server with NSX-T 實例中。

標準化硬體配置的可用性及定價可能會根據選取以用於部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。
{:note}

### Bare Metal Server
{: #vc_nsx-t_overview-bare-metal}

您可以使用下列其中一項配置，訂購三部以上的 {{site.data.keyword.baremetal_short}}：
* **Skylake**：2-CPU Intel Skylake 世代伺服器（Intel Xeon 4100/5100/6100 系列），搭配您選取的 CPU 型號及 RAM 大小。  
* **Broadwell**：4-CPU Intel Broadwell 世代伺服器（Intel Xeon E7-4800 系列），搭配您選取的 CPU 型號及 RAM 大小。

如果您計劃使用 vSAN 儲存空間，則配置需要至少四個 {{site.data.keyword.baremetal_short}}。
{:note}

### 網路
{: #vc_nsx-t_overview-networking}

訂購了下列網路元件：
*  10 Gbps 雙重公用及專用網路上行鏈路
*  三個 VLAN（虛擬 LAN）：一個公用 VLAN 和兩個專用 VLAN
* 一個具有 T1 和 T0 路由器的層疊網路，以因應連接至第 2 層 (L2) 網路之間的潛在東西向通訊。它已部署成一個遞送拓蹼範例，您可以加以修改、在其上進行建置，或是移除。
*  三個 VMware NSX-T Edge Services Gateway：
  * 一個用於出埠 HTTPS 管理資料流量的安全管理服務 VMware NSX ESG，由 IBM 部署為管理網路拓撲的一部分。IBM 管理 VM 使用此 ESG，以與跟自動化相關的特定外部 IBM 管理元件進行通訊。如需相關資訊，請參閱[配置網路以使用客戶管理的 NSX ESG 來搭配您的 VM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config)。
  * 兩個客戶管理的 VMware NSX ESG，用於出埠和入埠 HTTPS 工作負載資料流量。IBM 將此閘道部署為範本，您可以修改它來提供 VPN 存取或公用存取。如需相關資訊，請參閱[客戶管理的 NSX Edge 是否造成安全風險？](/docs/services/vmwaresolutions?topic=vmware-solutions-faq#faq-customer-nsx)

  此 ESG 名為 **mgmt-nsx-edge0**。您無法存取此 ESG，也無法使用它。如果您修改它，則可能無法從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 vCenter Server 實例。此外，使用防火牆或停用與外部 IBM 管理元件的 ESG 通訊，可能會導致 {{site.data.keyword.vmwaresolutions_short}} 變成無法使用。
  {:important}

### 虛擬伺服器實例
{: #vc_nsx-t_overview-vsi}

已訂購下列虛擬伺服器實例 (VSI)：
* IBM CloudBuilder 的 VSI，在完成實例部署之後會關閉它。
* 您可以選擇在管理叢集裡部署單一 Microsoft Windows Server VSI for Microsoft Active Directory (AD) 或兩部高可用性 Microsoft Windows VM，以協助加強安全及穩健性。

### Storage
{: #vc_nsx-t_overview-storage}

在起始部署期間，您可以選擇 vSAN 和 NFS 儲存空間選項。

部署之後，您可以將 NFS 儲存空間共用新增至現有 NFS 或 vSAN 叢集。如需相關資訊，請參閱[擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)中的*將 NFS 儲存空間新增至 vCenter Server 實例* 小節。
{:note}

#### vSAN 儲存空間
{: #vc_nsx-t_overview-vsan-storage}

vSAN 選項提供自訂的配置，以及磁碟類型、大小和數量的各種選項：
* 磁碟數量：2、4、6 或 8
* 儲存空間磁碟：960 GB SSD SED、1.9 TB SSD SED 或 3.8 TB SSD SED。

  此外，還為每部主機訂購 2 個 960 GB 的快取磁碟。

  當 3.8 TB SSD（固態硬碟）磁碟機在正式發行至資料中心時，就會予以支援。
  {:note}
* 「高效能 Intel Optane」選項，提供 2 個額外容量磁碟機槽來放置共 12 個容量磁碟。這個選項取決於 CPU 型號。

#### NFS 儲存空間
{: #vc_nsx-t_overview-nfs-storage}

NFS 選項為工作負載提供自訂的共用檔案層次儲存空間，以及大小和效能的各種選項：
* 大小：20 GB 到 24 TB
* 效能：0.25、2、4 或 10 IOPS/GB
* 檔案共用的個別配置

  10 IOPS/GB 效能層次限制為每個檔案共用的容量上限為 4 TB。
  {:note}

如果您選擇 NFS 選項，則會訂購用於管理元件的一個 2 TB 及 4 IOPS/GB 檔案共用。

### 授權（IBM 提供或 BOYL）與費用
{: #vc_nsx-t_overview-license-and-fee}

* VMware vSphere Enterprise Plus 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.4（僅限 IBM 所提供）
* （針對 vSAN 叢集）VMware vSAN Advanced 或 Enterprise 6.6
* 支援與服務費用（一個節點一份授權）

## vCenter Server with NSX-T 擴充節點的技術規格
{: #vc_nsx-t_overview-expansion-node-specs}

每個 vCenter Server with NSX-T 擴充節點都會針對下列元件進行部署，並在您的 {{site.data.keyword.cloud_notm}} 帳戶中產生費用。

### 擴充節點的硬體
{: #vc_nsx-t_overview-expansion-node-hardware}

一個其配置呈現在 [vCenter Server with NSX-T 實例的技術規格](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_overview#vc_nsx-t_overview-specs)中的 Bare Metal Server。

### 擴充節點的授權與費用
{: #vc_nsx-t_overview-expansion-node-license-and-fee}

* 一個 VMware vSphere Enterprise Plus 6.7u1
* 一個 VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.4
* 一筆支援與服務費用
* （針對 vSAN 叢集）VMware vSAN Advanced 或 Enterprise 6.6

您只能從 {{site.data.keyword.vmwaresolutions_short}} 主控台，而不能從 {{site.data.keyword.slportal}} 或透過主控台以外的任何其他方法，來管理在 {{site.data.keyword.cloud_notm}} 帳戶中建立的 {{site.data.keyword.vmwaresolutions_short}} 元件。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更這些元件，則變更不會與主控台同步。從 {{site.data.keyword.vmwaresolutions_short}} 主控台以外管理在訂購實例時已安裝至 {{site.data.keyword.cloud_notm}} 帳戶的任何 {{site.data.keyword.vmwaresolutions_short}} 元件，可能會讓您的環境不穩定。這些管理活動包括：
*  新增、修改、退回或移除元件
*  透過新增或移除 ESXi 伺服器來擴充或縮減實例容量
*  關閉元件電源
*  重新啟動服務
   這些活動的例外包括從 {{site.data.keyword.slportal}} 管理共用儲存空間檔案共用。這類活動包括：訂購、刪除（這可能會影響已裝載的資料儲存庫）、授權及裝載共用儲存空間檔案共用。
   {:important}

## 相關鏈結
{: #vc_nsx-t_overview-related}

* [vCenter Server 軟體資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [規劃 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [訂購 vCenter Server with NSX-T 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [vCenter Server 的連接儲存空間](/docs/services/vmwaresolutions/services?topic=vmware-solutions-storage-benefits#storage-benefits)
* [擴充檔案共用容量](/docs/infrastructure/FileStorage?topic=FileStorage-expandCapacity#expandCapacity)
