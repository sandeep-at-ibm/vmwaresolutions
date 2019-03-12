---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl on IBM Cloud 概觀
{: #htdc_considerations}

HyTrust DataControl on {{site.data.keyword.cloud}} 服務提供具有整合式金鑰管理的高度加密，在工作負載的整個生命週期內保護其安全。此服務提供作業系統層次及資料層次的加密。這可以加密及解密工作負載內的任何目錄、資料夾或檔案。

只有執行 vSphere 6.5 以及部署在（或升級至）2.3 版或更新版本的實例，才能使用此服務。目前安裝的 HyTrust DataControl 版本為 4.2.1。
{:note}

## HyTrust DataControl on IBM Cloud 的技術規格
{: #technical-specifications-for-hytrust-datacontrol-on-ibm-cloud}

下列元件已訂購並包括在 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務中：

### HyTrust DataControl 應用裝置
{: #htdc_considerations-appliance}

* CPU：2 個 vCPU
* RAM：8 GB
* 磁碟：在聚合叢集的 vSAN 上常駐 20 GB VMDK
* 網路：放置於指定用於管理之 VLAN 支援的專用可攜式網路上

### 高可用性
{: #htdc_considerations-ha}

在主動-主動配置中部署兩個 DataControl 應用裝置。

### 授權及費用
{: #htdc_considerations-licenses}

每部主機授權：針對環境中的每部主機訂購 HyTrust DataControl 授權。

## 移除 HyTrust DataControl on IBM Cloud 時的考量
{: #htdc_considerations-remove}

先使用 DataControl 取消連結所有用戶端，再移除 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務。在您移除服務之後，可能會刪除金鑰，而且您可能會遭鎖定而無法使用 VM。

## 相關鏈結
{: #htdc_considerations-related}

* [訂購 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [管理 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust 網站](https://www.hytrust.com/)
