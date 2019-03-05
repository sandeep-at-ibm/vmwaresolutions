---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# F5 on IBM Cloud 概觀

F5 on {{site.data.keyword.cloud}} 服務 (F5 BIG-IP® Virtual Edition) 提供區域和廣域範圍的智慧型 L4-L7 負載平衡及資料流量管理服務、健全網路及 Web 應用程式防火牆保護，以及安全和聯合應用程式存取。

您可以視需要安裝此服務的多個實例。

只有在 1.9 版或更新版本中部署的實例，才能使用此服務。目前安裝的 BIG-IP VE 版本為 13.1.1.2 版。
{:note}

## F5 on IBM Cloud 的技術規格

F5 on {{site.data.keyword.cloud_notm}} 服務隨附下列元件：

### 虛擬機器
* 兩部具有所有可用選項的虛擬機器 (VM)。
* 每部虛擬機器有 2、4 或 8 個 vCPU（視授權選項而定）。
* 每部虛擬機器有 4、8 或 16 GB RAM（視授權選項而定）。

### 網路
* 進行高可用性 (HA) 同步化的專用虛擬可延伸 LAN (VXLAN)。
* 透過專用管理網路存取「資料流量管理 Shell (TMSH)」及「管理主控台」。

### 授權及費用
每部 VM 的授權費用都會套用至每個計費週期，取決於授權選項（「良好」、「更佳」或「最佳」）及選取的頻寬。

您無法在安裝服務之後變更授權層次。若要變更授權層次，您必須移除現有服務，然後使用不同的授權選項來重新安裝服務。{:important}

## F5 on IBM Cloud 的安裝考量

在您安裝 F5 on {{site.data.keyword.cloud_notm}} 服務之前，請檢閱下列考量。

根據您選取的授權模型及頻寬，使用下列配置來部署兩部 BIG-IP VE VM（虛擬機器）：

表 1. 不同頻寬及授權模型選取項目的 CPU 和 RAM 部署

|頻寬上限          |授權模型：良好      |授權模型：更佳        |授權模型：最佳      |
|:------------------|:--------------------|:----------------------|:--------------------|
|25 Mbps           |2 個 vCPU、4 GB RAM |4 個 vCPU、8 GB RAM   |8 個 vCPU、16 GB RAM|
|200 Mbps          |2 個 vCPU、4 GB RAM |4 個 vCPU、8 GB RAM   |8 個 vCPU、16 GB RAM|
|1 Gbps            |2 個 vCPU、4 GB RAM |4 個 vCPU、8 GB RAM   |8 個 vCPU、16 GB RAM  |
|3 Gbps            |8 個 vCPU、16 GB RAM|8 個 vCPU、16 GB RAM|8 個 vCPU、16 GB RAM  |
|5 Gbps            |8 個 vCPU、16 GB RAM|8 個 vCPU、16 GB RAM|8 個 vCPU、16 GB RAM|
|10 Gbps           |8 個 vCPU、16 GB RAM|8 個 vCPU、16 GB RAM|8 個 vCPU、16 GB RAM|

### 其他考量

* F5 BIG-IP 會根據您選擇的頻寬上限來限制應用裝置傳輸量。因為網路效能會受到許多因素的影響，所以並非所有配置及拓蹼都可以達到您選擇的頻寬上限。
* BIG-IP VE VM 的 HA（高可用性）配對只會部署至預設叢集。

  此外，也會保留兩部 BIG-IP VE VM 的 100% CPU 及 RAM，因為這些 VM 位在網路通訊的資料平面中，而且資源仍然可供它們使用是相當重要的。

  若要計算單一 BIG-IP VE VM 的 CPU 及 RAM 保留，請使用下列公式：

  `CPU 保留 = ESXi 伺服器的 CPU 速度 * vCPU 數目`（從表 1）

  `RAM 保留 = RAM 大小`（從表 1）

### 規劃考量
您必須滿足下列需求，才能避免 F5 on {{site.data.keyword.cloud_notm}} 失敗：
* 至少有兩部作用中 ESXi 伺服器，可使用在個別伺服器上保留 VM 的反親緣性規則來部署兩部 BIG-IP VE VM。
* 兩部作用中 ESXi 伺服器具有足夠的可用資源，因此，可以在具有 100% CPU 及 RAM 保留的每一部 ESXi 伺服器上管理一部 BIG-IP VE VM。
* VMware vSphere HA 具有足夠的資源，可管理兩部具有 100% CPU 及 RAM 的 BIG-IP VM。

基於這些需求，您必須規劃 F5 on {{site.data.keyword.cloud_notm}} 所需的空間。必要的話，在您訂購 F5 on {{site.data.keyword.cloud_notm}} 之前，請將 1-2 部 ESXi 伺服器新增至實例，以及（或）減少 vSphere HA CPU 保留以進行失效接手。

## F5 on IBM Cloud 訂購範例

您使用下列配置來訂購具有 2 部 ESXi 伺服器的 VMware vCenter Server **小型**實例：16 個 2.10 GHz 的核心，各有 128 GB RAM。針對 F5 on {{site.data.keyword.cloud_notm}}，您選取**最佳**授權模型，而且**頻寬上限**的值為 5 Gbps。

在此情況下，每一部伺服器上都需要單一 BIG-IP VM：
* 2.1 GHz * 8 個 vCPU = 16.8 GHz 的 CPU，及
* 16 GB RAM

兩部 BIG-IP VM 總共有 33.6 GHz CPU 及 32 GB RAM。

每一部 ESXi 伺服器都有「16 個核心 * 2.1 GHz = 33.6 GHz」的容量，因此，如果兩部伺服器都作用中，而且每部伺服器上都至少有 16.8 GHz 的 CPU 及 16 GB RAM 可用，則符合前兩項需求。

不過，依預設，在一開始部署 2 部 ESXi 伺服器的 vCenter Server 實例上，vSphere HA 會保留 50% 的 CPU 及 RAM 以進行失效接手。在此範例中，可以使用下列項目：

`50% 的 2 * 16 個核心 * 2.1 GHz = 33.6 GHz 可用`

由於使用這些資源的 ESXi 伺服器（例如，VMware vCenter Server、VMware NSX Controller、VMware NSX Edge）上有其他工作負載，我們無法滿足第三項需求，因為兩部 BIG-IP VM 需要 33.6 GHz 的 CPU 及 32 GB RAM。

在此情況下，F5 on {{site.data.keyword.cloud_notm}} 安裝可能會失敗，除非將至少一部 ESXi 伺服器新增至環境，並且適當地更新 vShpere HA 失效接手保留，確保有足夠的資源可供兩部 BIG-IP VE VM 使用。如果需要額外的資源執行 F5 on {{site.data.keyword.cloud_notm}} 服務，您可以先新增其他 ESXi 伺服器，再安裝 F5 on {{site.data.keyword.cloud_notm}}。

## 移除 F5 on IBM Cloud 時的考量

在您移除 F5 on {{site.data.keyword.cloud_notm}} 服務之前，請確定已正確地移除現有 BIG-IP VE 配置。具體而言，網路資料流量必須遞送至 BIG-IP VE，而不是透過 BIG-IP VE 遞送。否則，您環境中的現有資料流量可能會受到影響。

### 相關鏈結

* [訂購 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/f5_ordering.html)
* [管理 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managing_f5.html)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [常見問題](/docs/services/vmwaresolutions/vmonic/faq.html)
* [F5 網站](https://f5.com/){:new_window}
