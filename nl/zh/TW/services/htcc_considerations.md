---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust CloudControl on IBM Cloud 概觀

HyTrust CloudControl on {{site.data.keyword.cloud}} 服務會施行並控制是否符合安全標準，並提供詳細角色型存取控制 (RBAC)、核准及審核功能。與 HyTrust DataControl 結合時，此服務可確保虛擬機器及工作負載資料不會離開 {{site.data.keyword.CloudDataCent_notm}} 內的特定地區、叢集或 ESXi 伺服器。

**可用性：**只有執行 vSphere 6.5 並且部署在（或升級至）2.3 版或更新版本的實例，才能使用此服務。

## HyTrust CloudControl on IBM Cloud 的技術規格

下列元件已訂購並包括在 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務中：

### HyTrust CloudControl 應用裝置

* CPU：4 個 vCPU
* RAM：16 GB
* 磁碟：在聚合叢集的 vSAN 上常駐 70 GB VMDK
* 網路：放置於指定用於管理之 VLAN 支援的專用可攜式網路上

### 高可用性

在主動-被動配置中部署兩個 CloudControl 應用裝置。

### 授權及費用

每部主機授權：針對環境中的每部主機訂購 HyTrust CloudControl 授權。

## 移除 HyTrust CloudControl on IBM Cloud 時的考量

請確定您停用已配置的 **Root 密碼加密配置檔**，並且已從 HyTrust CloudControl 中刪除所有受保護主機，再移除 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務。

### 相關鏈結

* [訂購 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [管理 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [HyTrust 網站](https://www.hytrust.com/)
