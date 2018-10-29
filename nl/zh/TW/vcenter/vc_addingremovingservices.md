---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# 訂購、檢視及移除 vCenter Server 實例的服務

您可以訂購 VMware vCenter Server 實例的服務，例如災難回復解決方案。當您不再需要這些服務時，可以從實例移除它們。

## vCenter Server 實例可用的服務

下表顯示可用於 vCenter Server 實例的服務。

表 1. vCenter Server 實例的可用服務

| 服務名稱                                                                               | 版本號碼 | 實例版本 |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](../services/f5_considerations.html)                                 | BIG-IP VE 13.1 版 | 1.9 版以及更新版本 |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html)       | 300 系列 | 2.0 版以及更新版本 |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | 5.6 | 2.0 版以及更新版本 |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)              | 5.4.0 | 2.3 版以及更新版本 |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)              | 4.2.1 | 2.3 版以及更新版本 |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/htkc_considerations.html)              | 4.2 | 2.5 版以及更新版本 |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](../services/spp_considerations.html)         | 10.1.1 Patch 1 | 2.2 版以及更新版本 |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html)                  |   | 2.2 版以及更新版本 |
| [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)                          | 9.5u3 | 1.8 版以及更新版本 |
| [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html)                                 | 5.5u4 Patch 2 | 1.2 版以及更新版本 |

## 將服務新增至 vCenter Server 實例的程序

若要將服務新增至 vCenter Server 實例，請按一下前一個表格中的適當服務鏈結以檢閱該服務的考量，然後檢查所部署的元件。然後，遵循服務訂購主題中的指示，將服務新增至實例。

### 服務安裝結果

順利完成服務的安裝之後，會透過電子郵件通知您，且該服務會顯示在實例的**服務**頁面上，且狀態為**已安裝**。

## 檢視 vCenter Server 實例服務的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格上的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要檢視服務的實例。
3. 在左導覽窗格上，按一下**服務**。
4. 在**服務**頁面上，按一下服務以檢閱其相關資訊（例如服務狀態及其他詳細資料）。
5. 根據所檢視的服務，您可以使用服務詳細資料上所提供的認證來存取服務主控台，並可從這裡管理服務。

## 移除 vCenter Server 實例服務的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要移除服務的實例。
3. 在左導覽窗格上，按一下**服務**。
4. 在**服務**頁面上，找出您要移除的服務實例，然後按一下**刪除**圖示。
5. 在**刪除服務**視窗中，檢閱是否有任何考量或警告。選取**我瞭解**，然後按一下**刪除**。

### 服務移除結果

接受服務移除的要求之後，服務狀態會變更為**正在移除**。

順利完成服務的移除之後，會透過電子郵件通知您，且會從實例的**服務**頁面移除服務。

**注意：**將向您收取已移除的服務到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。

### 相關鏈結

* [常見問題](../vmonic/faq.html)
