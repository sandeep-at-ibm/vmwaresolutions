---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud 概觀

HCX on {{site.data.keyword.cloud}} 服務會將內部部署資料中心的網路無縫地擴充至 {{site.data.keyword.cloud_notm}}，這容許您將虛擬機器 (VM) 移轉至 {{site.data.keyword.cloud_notm}} 或從該處移轉，而不需要進行任何轉換或變更。

只有部署在 2.3 版及更新版本中的 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 實例，才能使用此服務。{:note}

您可以將現有 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例。如需升級實例以及部署 HCX on {{site.data.keyword.cloud_notm}} 服務的相關資訊，請參閱[升級至 vCenter Server with Hybridity Bundle 實例](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html#upgrading-to-the-vcenter-server-with-hybridity-bundle-instance)。

**附註：**包含 HCX on {{site.data.keyword.cloud_notm}} 的 vCenter Server 實例限制為來自內部部署站台的三個同時連線。

## HCX on IBM Cloud 的技術規格

下列元件已訂購並包括在 HCX on {{site.data.keyword.cloud_notm}} 服務中。

**附註：**內部部署 HCX 實例僅包括授權及啟動。

### 用於 HCX 管理的 VMware NSX Edge Services Gateway 主動/被動配對

* CPU：6 個 vCPU
* RAM：8 GB
* 磁碟：3 GB VMDK

### HCX 管理應用裝置 - 虛擬機器

* CPU：4 個 vCPU
* RAM：12 GB
* 磁碟：60 GB VMDK

視需要，在配置進行 L2 連線功能、WAN 最佳化及閘道連線期間，會部署其他的 HCX 應用裝置。

### 網路

* 一個具有 16 個 IP 位址的公用可攜式子網路
* 兩個具有 64 個 IP 位址的專用可攜式子網路
* 來自專用可攜式 vMotion 子網路的八個 IP 位址

### 授權及費用

* 基礎授權費用：需要的服務費用
* 受管理 VM 費用：根據每月移轉的 VM 收費

## 安裝 HCX on IBM Cloud 時的考量

請先檢閱下列考量，再嘗試安裝 HCX on {{site.data.keyword.cloud_notm}}。

### ESXi 伺服器數目的需求

HCX on {{site.data.keyword.cloud_notm}} 服務無法安裝至預設叢集具有超過 51 部 ESXi 伺服器的實例。因為 HCX on {{site.data.keyword.cloud_notm}} 在預設叢集的 vMotion 子網路中需要八個 IP 位址，所以如果 ESXi 伺服器數目超過 51，則 vMotion 子網路中沒有適用於 HCX on {{site.data.keyword.cloud_notm}} 的 IP 位址。

### 防火牆規則的需求

安裝 HCX on {{site.data.keyword.cloud_notm}} 服務之前，您必須先將防火牆規則新增至任何現有防火牆，以容許所有出埠 HTTPS 資料流量，讓 HCX Manager 虛擬應用裝置 (HCX Manager) 可以登錄它自己。完成 HCX Manager 安裝之後，即可移除防火牆規則。此外，您還必須配置防火牆規則，以容許 HCX 正常運作。如需相關資訊，請參閱 [HCX on {{site.data.keyword.cloud_notm}} 架構](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)中的*附錄 A - 埠存取需求*。

## 移除 HCX on IBM Cloud 時的考量

請先檢閱下列考量，再移除 HCX on {{site.data.keyword.cloud_notm}} 服務：
* 確定已移除內部部署來源站台與 {{site.data.keyword.cloud_notm}} 目標站台之間的交互連接及延伸網路。若要移除交互連接及延伸網路，請使用內部部署 VMware vSphere Web Client 中的 HCX 使用者介面。
* 確定已移除內部部署來源站台與 {{site.data.keyword.cloud_notm}} 目標站台之間的站台配對。若要移除站台配對，請使用內部部署 VMware vSphere Web Client 中的 HCX 使用者介面。
* 會自動移除 HCX on {{site.data.keyword.cloud_notm}}。順利移除此服務會完成下列程序：
   * 取消啟動針對雲端 HCX Manager 訂購的 HCX 授權。
   * 刪除 HCX Manager。
   * 釋放保留給 HCX 的 vMotion IP 位址。
   * 移除空的 HCX 相關資源儲存區。
   * 移除空的 HCX 相關資料夾。
   * 刪除 HCX 管理邊緣應用裝置。

### 相關鏈結

* [訂購 HCX on {{site.data.keyword.cloud_notm}}](hcx_ordering.html)
* [管理 HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [HCX 術語名詞解釋](hcx_glossary.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension 概觀](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension 文件](https://hcx.vmware.com/#vm-documentation)
