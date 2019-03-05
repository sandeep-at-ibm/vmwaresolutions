---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Virtual Appliance on IBM Cloud 概觀

FortiGate Virtual Appliance on {{site.data.keyword.cloud}} 服務會將一組 FortiGate Virtual Appliance 部署到您的環境，以協助您在虛擬基礎架構內實作重要安全控制來降低風險。

您可以視需要安裝此服務的多個實例。您可以透過 SSH 使用 FortiOS Web Client 或指令行介面，來管理此服務。

只有在 2.0 版或更新版本中部署的實例，才能使用此服務。目前安裝的服務版本為 6.0.3。
{:note}

## FortiGate Virtual Appliance on IBM Cloud 的技術規格

下列元件已訂購並包括在 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務中：

### 虛擬機器

* 所有選項都包括虛擬機器的高可用性 (HA) 配對。
* 每部虛擬機器有 2、4 或 8 個 vCPU（視部署大小及訂閱類型而定）。
* 每部虛擬機器有 4、6 或 12 GB RAM（視部署大小及訂閱類型而定）。

### 高可用性

已部署並備妥兩部虛擬機器，用於進行 HA 或「虛擬路由器備援通訊協定 (VRRP)」配置。

### 網路

透過專用管理網路即可存取 FortiGate® 主控台。

### 授權及費用

每部虛擬機器的授權費用都會套用至每個計費週期，取決於選取的部署大小及每月訂閱授權模型。

您無法在安裝服務之後變更授權層次。若要變更授權層次，您必須移除現有服務，然後使用不同的授權選項來重新安裝服務。{:important}

## 安裝 FortiGate Virtual Appliance on IBM Cloud 時的考量

請先檢閱下列考量，再安裝 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務：
* FortiGate 虛擬機器 (VM) 只會部署至預設叢集。
* 也會保留兩部 FortiGate VM 的 100% CPU 及 RAM，因為這些 VM 位在網路通訊的資料平面中，而且資源仍然可供它們使用是相當重要的。

  若要計算單一 FortiGate VM 的 CPU 及 RAM 保留，請使用下列公式：
   * `CPU 保留 = ESXi 伺服器的 CPU 速度 * vCPU 數目`
   * `RAM 保留 = RAM 大小`
* 當您將 FortiGate Virtual Appliance 的 HA 配對部署至實例時，已在「管理 NSX Edge Services Gateway (ESG)」上定義 SNAT 及防火牆規則以及 FortiGate Virtual Appliance 上的靜態路徑，以容許從實例到公用網路的出埠 HTTPS 通訊來啟動授權，以及取得最新安全原則及內容。
* 您無法在安裝服務之後變更授權層次。若要變更授權層次，您必須移除現有服務，然後選取不同的授權選項來重新安裝服務。
* 您必須滿足下列需求，才能避免 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 失敗：
   * 至少有兩部作用中 ESXi 伺服器，可使用在個別伺服器上保留 VM 的反親緣性規則來部署兩部 FortiGate VM。
   * 兩部作用中 ESXi 伺服器具有足夠的可用資源，因此，可以在具有 100% CPU 及 RAM 保留的每一部 ESXi 伺服器上管理一部 FortiGate VM。
   * VMware vSphere HA 具有足夠的資源，可管理兩部具有 100% CPU 及 RAM 的 FortiGate VM。

  基於這些需求，您必須仔細規劃 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 所需的空間。必要的話，在訂購 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 之前，請將 1-2 部 ESXi 伺服器新增至實例，以及（或）減少 vSphere HA CPU 保留以進行失效接手。

## FortiGate Virtual Appliance on IBM Cloud 訂購範例

您使用下列配置來訂購具有 2 部 ESXi 伺服器的 VMware vCenter Server **小型**實例：16 個 2.10 GHz 的核心，各有 128 GB RAM。針對 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}，您為部署大小及任何訂閱授權模型選取**大型**（8 個 vCPU/12 GB RAM）。

在此情況下，每一部伺服器上都需要單一 FortiGate VM：
* 2.1 GHz * 8 個 vCPU = 16.8 GHz 的 CPU，及
* 12 GB RAM

兩部 FortiGate VM 總共有 33.6 GHz CPU 及 24 GB RAM。

每一部 ESXi 伺服器都有「16 個核心 * 2.1 GHz = 33.6 GHz」的容量，因此，如果兩部伺服器都作用中，而且每部伺服器上都至少有 16.8 GHz 的 CPU 及 12 GB RAM 可用，則符合前兩項需求。

不過，依預設，在一開始部署 2 部 ESXi 伺服器的 vCenter Server 實例上，vSphere HA 會保留 50% 的 CPU 及 RAM 以進行失效接手，因此，我們只會有：

`50% 的 2 * 16 個核心 * 2.1 GHz = 33.6 GHz 可用`

因為使用這些資源的 ESXi 伺服器（例如，VMware vCenter Server、VMware NSX Controller 或 VMware NSX Edge）上有其他工作負載，所以我們無法滿足第三項需求。這是因為兩部 FortiGate VM 需要 33.6 GHz 的 CPU 及 24 GB RAM。

在此情況下，FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 安裝可能會失敗，除非將至少一部 ESXi 伺服器新增至環境，並且適當地更新 vShpere HA 失效接手保留，以確保有足夠的資源可供兩部 FortiGate VM 使用。

如果需要額外的資源執行 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務，您可以先新增其他 ESXi 伺服器，再安裝服務。

## 移除 FortiGate Virtual Appliance on IBM Cloud 時的考量

在您移除 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務之前，請確定已正確地移除現有 FortiGate Virtual Appliance 的配置。具體而言，網路資料流量必須遞送至 FortiGate Virtual Appliance，而不是透過 FortiGate Virtual Appliance 遞送。否則，您環境內的現有資料流量可能會受到影響。

### 相關鏈結

* [訂購 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_ordering.html)
* [管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managingfortinetvm.html)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [常見問題](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Fortinet 網站](https://www.fortinet.com/){:new_window}
* [Fortinet 文件庫](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
