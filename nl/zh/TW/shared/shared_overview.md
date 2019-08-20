---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: vmware solutions shared, get started shared, tech specs shared

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud for VMware Solutions Shared 概觀
{: #shared_overview}

{{site.data.keyword.vmwaresolutions_full}} Shared 提供為實驗性的供應項目。
{:note}

使用「VMware 虛擬資料中心」，您可以快速、無縫地將 VMware 工作負載移轉或部署至基於專業管理的 VMware 基礎架構的雲端。IBM 提供一個自助式隨需應變 VMware 雲端運算平台，其中 vCloud Director 在 {{site.data.keyword.cloud_notm}} 上執行。此基礎架構即服務 (IaaS) 隨收隨付制供應項目容許使用者根據需要使用特定 vCPU、儲存空間、vRAM、網路和 IP。

{{site.data.keyword.vmwaresolutions_short}} 有三種「基礎架構即服務」(IaaS) 訂閱服務類型：
- 多方承租戶保留虛擬資料中心
- 多方承租戶隨收隨付制虛擬資料中心
- 單一承租戶專用虛擬資料中心

客戶使用 {{site.data.keyword.vmwaresolutions_short}} 供應項目來管理虛擬資料中心的生命週期。不論透過 Web 使用者介面還是公用 API，都支援下列功能：
- 建立虛擬資料中心
- 虛擬資料中心彈性
- 刪除虛擬資料中心
- 新增和移除 VMware 服務
- 隨需應變 Windows 授權
- 隨需應變 Red Hat 授權

所有這三種「{{site.data.keyword.cloud_notm}} 虛擬資料中心」供應項目依標準都會隨附「NSX Edge 服務閘道」上的五個公用 IP 位址，可透過公用網路無限制進入。

虛擬資料中心會發生下列元件的費用：
- 基於儲存空間效能的分層定價的儲存空間配置
- 虛擬 CPU 用量
- 虛擬記憶體用量
- 公用網路連線功能上的輸出
- 使用的商業作業系統授權
- 選用 VMware 服務

## IBM Cloud for VMware Solutions Shared 架構
{: #shared_overview-archi}

下圖說明 {{site.data.keyword.vmwaresolutions_short}} Shared 部署的高階架構及元件。

![{{site.data.keyword.vmwaresolutions_short}} Shared 架構](../images/vclouddirector-architecture-public.svg "{{site.data.keyword.vmwaresolutions_short}} Shared 架構")

### VMware vCloud Director
{: #shared_overview-vcloud-dir}

此層代表管理介面。VMware® vCloud Director 會提供對 Web 型承租戶入口網站的角色型存取，容許組織成員與組織的資源互動，以建立和使用 vApp 和虛擬機器 (VM)。

### 組織 
{: #shared_overview-org}

組織是使用者、群組和運算資源集合的管理單位。使用者在組織層次進行鑑別，提供的是建立或匯入使用者時由組織管理者建立的認證。組織管理者負責管理組織使用者、群組和型錄。

### 使用者和原則
{: #shared_overview-users-policies}

組織可以包含任意數目的使用者和群組。使用者可以由組織管理者在本端建立，也可以從 LDAP 這類目錄服務匯入。組織內的許可權透過向使用者和群組指派權限和角色進行控制。

### 型錄
{: #shared_overview-cat}

組織使用型錄來儲存 vApp 範本和媒體檔案。有權存取型錄的組織成員可以使用型錄的 vApp 範本和媒體檔案來建立自己的 vApp。組織管理者可以將公用型錄中的項目複製到自己的組織型錄。

### 虛擬資料中心
{: #shared_overview-vc}

組織虛擬資料中心為組織提供資源。虛擬資料中心提供可以儲存、部署和操作虛擬系統的環境。虛擬資料中心還可為虛擬 CD 和 DVD 媒體提供儲存空間。一個組織可以有多個虛擬資料中心。

![{{site.data.keyword.cloud_notm}} 的虛擬資料中心架構](../images/virtual-datacenter-architecture-public.svg "{{site.data.keyword.cloud_notm}} 的虛擬資料中心架構")

## IBM Cloud for VMware Solutions Shared 的技術規格
{: #shared_overview-specs}

{{site.data.keyword.cloud_notm}} 中包含下列元件：

### 運算
{: #shared_overview-specs-comp}

運算處理以虛擬 CPU (vCPU) 為增量配置給虛擬資料中心。每個 vCPU 增量都代表一個 2.0 GHz 核心。運算記憶體以 GB 為增量進行配置。

### 網路
{: #shared_overview-specs-net}

依預設，每個虛擬資料中心都配置有一個邊緣閘道，該閘道具有五個公用 IP 位址和一個專用服務 IP 位址。邊緣閘道可供客戶配置，因此可以進行自訂。

公用位址可用於面向公眾的 vApp，以處理入埠或出埠公用網際網路資料流量。

服務位址可用於存取 IBM Cloud 內部專用網路上的 IBM Cloud 基礎架構服務，包括下列服務：
- 
NTP

- Windows 作業系統授權和更新
- Red Hat 作業系統授權和更新
- Cloud Object Storage

### Storage
{: #shared_overview-specs-storage}

建立或部署 vApp 或 VM 時，將選取儲存空間原則。有 4 個不同的儲存空間層級可用，具體取決於所需的儲存空間效能：

- NFS Platinum：此儲存空間層級的傳輸量上限為 10 IOPS/GB，效能最高
- NFS Gold：此儲存空間層級的傳輸量上限為 4 IOPS/GB
- NFS Silver：此儲存空間層級的傳輸量上限為 2 IOPS/GB
- NFS Bronze：此儲存空間層級的傳輸量上限為 0.25 IOPS/GB

## 相關鏈結
{: #shared_overview-related}

* [訂購 Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [訂購 Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [管理 {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-74C9E10D-9197-43B0-B469-126FFBCB5121.html){:external}
