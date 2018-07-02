---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# vCenter Server 實例的需求及規劃

在訂購 VMware vCenter Server 實例之前，請先檢閱下列需求。請根據 {{site.data.keyword.CloudDataCent}} 位置、工作負載容量需求及其他服務需求來規劃實例。

## IBM Cloud 帳戶需求

您使用的 {{site.data.keyword.cloud_notm}} 帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 帳戶需求](../vmonic/slaccountrequirement.html)。

## IBM Cloud Data Center 可用性

vCenter Server 部署具有嚴格的實體基礎架構需求。因此，您只能在符合需求的 {{site.data.keyword.CloudDataCents_notm}} 中部署實例。下列 {{site.data.keyword.CloudDataCents_notm}} 可用於 vCenter Server 部署：

表 1. vCenter Server 實例可用的 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |位置|地區           |伺服器選項     |
|:----------------------|:---------|:-------|:---------------|
|AMS03 |阿姆斯特丹|歐洲|自訂|
|CHE01 |清奈|亞太地區|自訂|
|DAL09 |達拉斯|NA 南部|自訂|
|DAL10 |達拉斯|NA 南部|自訂、小型、中型、大型|
|DAL12 |達拉斯|NA 南部|自訂|
|DAL13 |達拉斯|NA 南部|自訂|
|FRA02 |法蘭克福|歐洲|自訂、小型、中型、大型|
|FRA04 |法蘭克福|歐洲|自訂|
|HKG02 |香港|亞太地區|自訂|
|LON02 |倫敦|歐洲|自訂|
|LON04 |倫敦|歐洲|自訂|
|LON06 |倫敦|歐洲|自訂、小型、中型、大型|
|MEL01 |墨爾本|亞太地區|自訂|
|MEX01 |克雷塔羅|NA 南部|自訂|
|MIL01 |米蘭|歐洲|自訂|
|MON01 |蒙特婁|NA 東部|自訂|
|OSL01 |奧斯陸|歐洲|自訂|
|PAR01 |巴黎|歐洲|自訂|
|SAO01 |聖保羅|南美洲|自訂|
|SEO01 |首爾|亞太地區|自訂|
|SJC03 |聖荷西|NA 西部|自訂、小型、中型、大型|
|SJC04 |聖荷西|NA 西部|自訂|
|SNG01 |新加坡|亞太地區|自訂|
|SYD01 |雪梨|亞太地區|自訂|
|SYD04 |雪梨|亞太地區|自訂|
|TOK02 |東京|亞太地區|自訂|
|TOR01 |多倫多|NA 東部|自訂、小型、中型、大型|
|WDC04 |華盛頓特區|NA 東部|自訂、小型、中型、大型|
|WDC06 |華盛頓特區|NA 東部|自訂|
|WDC07 |華盛頓特區|NA 東部|自訂|

部分 IBM Cloud {{site.data.keyword.CloudDataCents_notm}} 提供預先配置的**小型**、**中型**及**大型** Bare Metal Server 選項。視可用性和庫存供應而定，{{site.data.keyword.CloudDataCents_notm}} 可能會在 {{site.data.keyword.vmwaresolutions_full}} 主控台中顯示狀態指示器，以協助您規劃部署。

表 2. 訂購 vCenter Server 實例時 {{site.data.keyword.CloudDataCents_notm}} 的狀態指示器

|狀態|狀態詳細資料|
|:------------------------------|:--------------------------------------------------|
|即將推出                   |目前並未提供 {{site.data.keyword.CloudDataCent_notm}}。|
|暫時沒有庫存                  |目前並未提供 {{site.data.keyword.CloudDataCent_notm}}。|
|庫存受限             |{{site.data.keyword.CloudDataCent_notm}} 的可用性受限，可能無法完成訂單。|

## 適用於 vCenter Server 實例的服務

您可以根據需要來訂購實例基礎的附加程式服務（例如災難回復）。如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server 實例的服務](vc_addingremovingservices.html)。

<!-- ## Capacity considerations

For capacity information and considerations, see the _Bill of
Materials_ document on the [Virtual reference architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page. -->

## 相關鏈結

* [vCenter Server 概觀](vc_vcenterserveroverview.html)
* [訂購 vCenter Server 實例](vc_orderinginstance.html)
* [擴充及縮減 vCenter Server 實例的容量](vc_addingremovingservers.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](vc_addingremovingservices.html)
