---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust DataControl on IBM Cloud 概觀

HyTrust DataControl on {{site.data.keyword.cloud}} 服務提供具有整合式金鑰管理的高度加密，來保護其整個生命週期的工作負載安全。此服務可以提供作業系統層次及資料層次的加密，表示可以加密及解密工作負載內的任何目錄、資料夾或檔案。

**可用性：**只有執行 vSphere 6.5 並且部署在（或升級至）2.3 版或更新版本的實例，才能使用此服務。

## HyTrust DataControl on IBM Cloud 的技術規格

下列元件已訂購並包括在 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務中：

### HyTrust DataControl 應用裝置
* CPU：2 個 vCPU
* RAM：8 GB
* 磁碟：在聚合叢集的 vSAN 上常駐 20 GB VMDK
* 網路：放置於指定用於管理之 VLAN 支援的專用可攜式網路上

### 高可用性
在主動-主動配置中部署兩個 DataControl 應用裝置。

### 授權及費用

每部主機授權：針對環境中的每部主機訂購 HyTrust DataControl 授權。

## 移除 HyTrust DataControl on IBM Cloud 時的考量

請確定您已加密或備份 DataControl 中的所有磁碟，再移除 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務。在您移除服務之後，可能會刪除金鑰，致使您可能會遭鎖定而無法使用 VM。

### 相關鏈結

* [訂購 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [管理 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [HyTrust 網站](https://www.hytrust.com/)
