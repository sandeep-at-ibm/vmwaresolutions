---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl on IBM Cloud 概觀
{: #htcc_considerations}

HyTrust CloudControl on {{site.data.keyword.cloud}} 服務會施行並控制是否符合安全標準，其中包括角色型存取控制 (RBAC)、核准及審核。此服務與 HyTrust DataControl 結合時，此服務確定虛擬機器及工作負載資料不會離開 {{site.data.keyword.CloudDataCent_notm}} 內的特定地區、叢集或 ESXi 伺服器。

只有執行 vSphere 6.5 以及部署在（或升級至）2.3 版或更新版本的實例，才能使用此服務。目前安裝的 HyTrust CloudControl 版本是 5.5。
{:note}

## HyTrust CloudControl on IBM Cloud 的技術規格
{: #htcc_considerations-specs}

下列元件已訂購並包括在 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務中：

### HyTrust CloudControl 應用裝置
{: #htcc_considerations-appliance}

* CPU：4 個 vCPU
* RAM：16 GB
* 磁碟：在聚合叢集的 vSAN 上常駐 70 GB VMDK
* 網路：放置於指定用於管理之 VLAN 支援的專用可攜式網路上

### 高可用性
{: #htcc_considerations-ha}

在主動-被動配置中部署兩個 CloudControl 應用裝置。

### 授權及費用
{: #htcc_considerations-licenses}

每部主機授權：針對環境中的每部主機訂購 HyTrust CloudControl 授權。

## 移除 HyTrust CloudControl on IBM Cloud 時的考量
{: #htcc_considerations-remove}

請確定您停用已配置的 **Root 密碼加密配置檔**，並且已從 HyTrust CloudControl 中刪除所有受保護主機，再移除 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務。

## 相關鏈結
{: #htcc_considerations-related}

* [訂購 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [管理 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust 網站](https://www.hytrust.com/)
