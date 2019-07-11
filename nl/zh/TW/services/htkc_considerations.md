---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: HyTrust KeyControl, HTKC, tech specs HTKC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust KeyControl on IBM Cloud 概觀
{: #htkc_considerations}

HyTrust KeyControl on {{site.data.keyword.cloud}} 服務簡化加密工作負載的管理。此服務會自動化及簡化加密金鑰的生命週期，包括金鑰儲存空間、金鑰配送、金鑰輪替及金鑰撤銷。使用符合 FIPS 140-2 標準的加密，企業可以輕鬆地大規模管理加密金鑰。

只有執行 vSphere 6.5 以及部署在（或升級至）2.5 版和更新版本的實例，才能使用此服務。現行安裝的 HyTrust KeyControl 版本為 4.3.2。
{:note}

## HyTrust KeyControl on IBM Cloud 的技術規格
{: #htkc_considerations-specs}

下列元件已訂購並包括在 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服務中：

### HyTrust KeyControl 應用裝置
{: #htkc_considerations-appliance}

* CPU：2 個 vCPU
* RAM：8 GB
* 磁碟：在聚合叢集的 vSAN 上常駐 20 GB VMDK
* 網路：放置於指定用於管理之 VLAN 支援的專用可攜式網路上

### 高可用性
{: #htkc_considerations-ha}

依預設，在主動-主動叢集配置中部署兩個 KeyControl 應用裝置。

您可以選擇性地指定在獨立式非叢集配置中部署兩個 KeyControl 應用裝置。

### 授權及費用
{: #htkc_considerations-licenses}

針對每個實例安裝，訂購 HyTrust KeyControl 授權。

## 移除 HyTrust KeyControl on IBM Cloud 時的考量
{: #htkc_considerations-remove}

請確定您已使用 KeyContol 取消連結所有用戶端，再移除 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服務。在您移除服務之後，可能會刪除金鑰，而且您可能會遭鎖定而無法使用 VM。

## 相關鏈結
{: #htkc_considerations-related}

* [訂購 HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_ordering)
* [管理 HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust 網站](https://www.hytrust.com/)
