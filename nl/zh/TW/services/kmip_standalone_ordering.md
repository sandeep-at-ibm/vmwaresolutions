---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: KMIP for VMware, order KMIP stand-alone, KMIP for VMware configuration

subcollection: vmware-solutions


---

# 訂購 KMIP for VMware on IBM Cloud 實例
{: #kmip_standalone_ordering}

您可以訂購 KMIP for VMware on {{site.data.keyword.cloud}} 實例，而未將它關聯至任何 VMware 實例，以彈性管理服務及實例。

## 開始之前
{: #kmip_standalone_ordering-req}

請確定您已完成下列作業：
* 您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。
* 您已檢閱[安裝 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例時的考量](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations-install)中的所有考量。

## 訂購 KMIP for VMware on IBM Cloud 實例的程序
{: #kmip_standalone_ordering-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**開始使用**。
2. 在**訂購其他服務**區域中，按一下 **KMIP for VMware on IBM Cloud**。
3. 在 **KMIP for VMware on IBM Cloud** 頁面上，視需要配置服務設定。
4. 按一下**佈建**。

## KMIP for VMware on IBM Cloud 服務配置
{: #kmip_standalone_ordering-config}

當您訂購此服務時，請提供下列設定：

### 實例名稱
{: #kmip_standalone_ordering-config-instance-name}

指定 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例的名稱。

### 服務位置
{: #kmip_standalone_ordering-config-service-region}

選取要管理 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例的 {{site.data.keyword.cloud_notm}} 位置。

{{site.data.keyword.cloud_notm}} 在每個可使用該服務的位置維護一個高度可用的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 網路服務端點。

表 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} 網路服務端點位置

|位置|端點|
|:---------------|:-----------------------|
|達拉斯| <<code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code><br>及<br><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code> |
|法蘭克福|<code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code><br>及<br><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code> |
|倫敦|<code>kmip-1.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code><br>及<br><code>kmip-2.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code> |
|雪梨|<code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code><br>及<br><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code> |
|東京|<code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code><br>及<br><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code> |
| 華盛頓特區    |<code>kmip-1.private.us-east.vmware-solutions.cloud.ibm.com:5696</code><br>及<br><code>kmip-2.private.us-east.vmware-solutions.cloud.ibm.com:5696</code> |

### 服務 ID 的 API 金鑰
{: #kmip_standalone_ordering-config-api-key}

輸入用來存取 Key Protect 或 Hyper Protect Crypto Services 服務實例之「{{site.data.keyword.cloud_notm}} 服務 ID」的 API 金鑰。

### 金鑰管理程式實例
{: #kmip_standalone_ordering-config-key-protect}

按一下**擷取**，以取得可用金鑰管理程式實例的清單，然後選取用於金鑰管理的實例。

### 客戶根金鑰
{: #kmip_standalone_ordering-config-root-key}

按一下**擷取**，以取得儲存在您所選取金鑰管理程式實例中的客戶根金鑰。

## 結果
{: #kmip_standalone_ordering-results}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例的訂購會自動啟動。您會收到正在處理訂單的確認，而且您可以檢視實例詳細資料來檢查訂單的狀態。

實例備妥可供使用時，實例的狀態會變更為**已安裝**，而且您會透過電子郵件收到通知。

## 下一步
{: #kmip_standalone_ordering-next}

新增所訂購 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例的用戶端憑證。如需相關資訊，請參閱[新增、檢視及刪除 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例的憑證](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)。

## 相關鏈結
{: #kmip_standalone_ordering-related}

* [檢視 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [刪除 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker 事件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
