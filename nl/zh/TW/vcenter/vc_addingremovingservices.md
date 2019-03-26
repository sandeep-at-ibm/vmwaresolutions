---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購、檢視及移除 vCenter Server 實例的服務
{: #vc_addingremovingservices}

您可以訂購 VMware vCenter Server 實例的服務，例如災難回復解決方案。當您不再需要這些服務時，可以從實例移除它們。

## vCenter Server 實例可用的服務
{: #vc_addingremovingservices-available-services}

下表顯示可用於 vCenter Server 實例的服務，以及已安裝的服務版本。

表 1. vCenter Server 實例的可用服務

| 服務名稱                                                                               | 現行服務版本 | 實例版本 |
|----------------------------------------------------------------------------------------|------------------|
| [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations) | 2.2 | 2.9 版以及更新版本 |
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)                                 | BIG-IP VE v14.1.0.2 | 1.9 版以及更新版本 |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)       | 300 系列 | 2.0 版以及更新版本 |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | 2.0 版以及更新版本 |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)              | 5.4.2 | 2.3 版以及更新版本 |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)              | 4.2.1 | 2.3 版以及更新版本 |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)              | 4.2 | 2.5 版以及更新版本 |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | 3.1 | 2.5 版以及更新版本 |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)         | 10.1.2 | 2.2 版以及更新版本 |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)                  | 2.0 |N/A    |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)                           | 9.5u4 | 1.8 版以及更新版本 |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)                                  | 6.5 Update 3 | 1.2 版以及更新版本 |

## 將服務新增至 vCenter Server 實例的程序
{: #vc_addingremovingservices-adding-procedure}

若要將服務新增至 vCenter Server 實例，請按一下前一個表格中的適當服務鏈結以檢閱該服務的考量，然後檢查所部署的元件。然後，遵循服務訂購主題中的指示，將服務新增至實例。

### 服務安裝結果
{: #vc_addingremovingservices-adding-results}

順利完成服務的安裝之後，會透過電子郵件通知您，且該服務會顯示在實例的**服務**頁面上，且狀態為**已安裝**。

## 檢視 vCenter Server 實例服務的程序
{: #vc_addingremovingservices-viewing-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要檢視服務的實例。
3. 在左導覽窗格上，按一下**服務**。
4. 在**服務**頁面上，按一下服務以檢閱其相關資訊（例如服務狀態及其他詳細資料）。
5. 根據所檢視的服務，您可以使用服務詳細資料上所提供的認證來存取服務主控台，並可從這裡管理服務。

## 移除 vCenter Server 實例服務的程序
{: #vc_addingremovingservices-removing-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下您要移除服務的實例。
3. 在左導覽窗格上，按一下**服務**。
4. 在**服務**頁面上，找出您要移除的服務實例，然後按一下**刪除**圖示。
5. 在**刪除服務**視窗中，檢閱是否有任何考量或警告。選取**我瞭解**，然後按一下**刪除**。

### 服務移除結果
{: #vc_addingremovingservices-removing-results}

接受服務移除的要求之後，服務狀態會變更為**正在移除**。

順利完成服務的移除之後，會透過電子郵件通知您，且會從實例的**服務**頁面移除服務。

將針對已移除的服務，向您收取到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。{:note}

## 相關鏈結
{: #vc_addingremovingservices-related}

* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
