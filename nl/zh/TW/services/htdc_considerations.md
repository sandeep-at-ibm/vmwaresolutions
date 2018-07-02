---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# HyTrust DataControl on IBM Cloud 概觀

HyTrust DataControl on {{site.data.keyword.cloud}} 服務提供具有整合式金鑰管理的高度加密，來保護其整個生命週期的工作負載安全。此服務可以提供作業系統層次及資料層次的加密，表示可以加密及解密工作負載內的任何目錄、資料夾或檔案。

**可用性：**只有執行 vSphere 6.5 並且部署或升級至 2.3 版或更新版本的實例，才能使用此服務。

## HyTrust DataControl on IBM Cloud 的元件

以「主動-主動」模式將 HyTrust DataControl (HTDC) 應用裝置的高可用性 (HA) 配對部署至預設叢集。已授權 HTDC 應用裝置，將 HyTrust KeyControl 功能提供給工作負載。

每一對 HTDC 應用裝置都會部署至針對管理虛擬機器 (VM)（例如 NSX Manager、vCenter Server Appliance 及 Platform Services Controller）所指定的相同可攜式子網路。應用裝置透過 {{site.data.keyword.cloud_notm}} 後端客戶路由器 (BCR) 遞送，並指派給與管理 VM 子網路相關聯的閘道。此外，應用裝置會放在預設叢集的預設儲存空間上。

## 移除 HyTrust DataControl on IBM Cloud 時的考量

請確定您已加密或備份 DataControl 中的所有磁碟，再移除 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務。在您移除服務之後，可能會刪除金鑰，致使您可能會遭鎖定而無法使用 VM。

## 相關鏈結

* [訂購 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [管理 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [HyTrust 網站](https://www.hytrust.com/)
