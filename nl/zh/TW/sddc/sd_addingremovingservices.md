---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# 訂購、檢視及移除 Cloud Foundation 實例的服務

您可以訂購 VMware Cloud Foundation 實例的服務（例如災難回復解決方案）。當您不再需要這些服務時，可以從實例中移除它們。

## Cloud Foundation 實例的可用服務

下表顯示可用於 Cloud Foundation 實例的服務。

表 1. Cloud Foundation 實例的可用服務

| 服務名稱                                                                               | 可用性       |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on IBM Cloud](../services/f5_considerations.html)                                 |是|
| [FortiGate Security Appliance on IBM Cloud](../services/fsa_considerations.html)       |是|
| [FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_considerations.html) |是|
| [HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)              |是|
| [HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)              |是|
| [IBM Spectrum Protect Plus on IBM Cloud](../services/spp_considerations.html)         |是|
| [KMIP for VMware on IBM Cloud](../services/kmip_considerations.html)                  |是|
| [Veeam on IBM Cloud](../services/veeam_considerations.html)                           |是|
| [VMware HCX on IBM Cloud](../services/hcx_considerations.html)                         | 否              |
| [Zerto on IBM Cloud](../services/addingzertodr.html)                                 |是|

## 將服務新增至 Cloud Foundation 實例

若要將服務新增至 Cloud Foundation 實例，請按一下前一個表格中的適當服務鏈結以檢閱該服務的考量，然後檢查所部署的元件。然後，遵循服務訂購主題中的指示，將服務新增至實例。

### 服務安裝結果

順利完成服務的安裝之後，會透過電子郵件通知您，且該服務會顯示在狀態為**已安裝**之實例的**服務**頁面上。

## 檢視 Cloud Foundation 實例的服務

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **Cloud Foundation 實例**表格中，按一下您要檢視服務的實例。
3. 在左導覽窗格上，按一下**服務**。
4. 在**服務**頁面上，按一下服務以檢閱其相關資訊（例如服務狀態及其他詳細資料）。
5. 根據所檢視的服務，您可以使用服務詳細資料上所提供的認證來存取服務主控台，並可從這裡管理服務。

## 移除 Cloud Foundation 實例的服務

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格上的**已部署的實例**。
2. 在 **Cloud Foundation 實例**表格中，按一下您要移除服務的實例。
3. 在左導覽窗格上，按一下**服務**。
4. 在**服務**頁面上，找出您要移除的服務實例，然後按一下**刪除**圖示。
5. 在**刪除服務**視窗中，檢閱是否有任何考量或警告。選取**我瞭解**，然後按一下**刪除**。

### 服務移除結果

接受服務移除的要求之後，服務狀態會變更為**正在移除**。

順利完成服務的移除之後，會透過電子郵件通知您，且會從實例的**服務**頁面中移除服務。

**注意**：將向您收取已移除的服務到 {{site.data.keyword.cloud_notm}} 計費週期結束為止的費用。

## 相關鏈結

* [常見問題](../vmonic/faq.html)
