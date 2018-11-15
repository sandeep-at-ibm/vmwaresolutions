---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# vCenter Server 實例的需求及規劃

在訂購 VMware vCenter Server 實例之前，請先檢閱下列需求。請根據 {{site.data.keyword.CloudDataCent}} 位置、工作負載容量需求及附加程式服務需求來規劃實例。

## IBM Cloud 帳戶需求

您使用的 {{site.data.keyword.cloud_notm}} 帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 帳戶的需求](../vmonic/slaccountrequirement.html)。

## IBM Cloud Data Center 可用性

vCenter Server 部署具有嚴格的實體基礎架構需求。因此，您只能在符合需求的 {{site.data.keyword.CloudDataCents_notm}} 中部署實例。下列 {{site.data.keyword.CloudDataCents_notm}} 可用於 vCenter Server 部署：

表 1. vCenter Server 實例可用的 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |位置|地區           |伺服器選項     |
|:----------------------|:---------|:-------|:---------------|
|AMS03 |阿姆斯特丹|歐洲| Skylake、Broadwell |
|CHE01 |清奈|亞太地區| Skylake、Broadwell |
|DAL09 |達拉斯|NA 南部| Skylake、Broadwell |
|DAL10 |達拉斯|NA 南部| Skylake、Broadwell、小型、中型、大型 |
|DAL12 |達拉斯|NA 南部| Skylake、Broadwell |
|DAL13 |達拉斯|NA 南部| Skylake、Broadwell |
|FRA02 |法蘭克福|歐洲| Skylake、Broadwell、小型、中型、大型 |
|FRA04 |法蘭克福|歐洲| Skylake、Broadwell |
|HKG02 |香港|亞太地區| Skylake、Broadwell |
|LON02 |倫敦|歐洲| Skylake、Broadwell |
|LON04 |倫敦|歐洲| Skylake、Broadwell |
|LON06 |倫敦|歐洲| Skylake、Broadwell、小型、中型、大型 |
|MEL01 |墨爾本|亞太地區| Skylake、Broadwell |
|MEX01 |克雷塔羅|NA 南部| Skylake、Broadwell |
|MIL01 |米蘭|歐洲| Skylake、Broadwell |
|MON01 |蒙特婁|NA 東部| Skylake、Broadwell |
|OSL01 |奧斯陸|歐洲| Skylake、Broadwell |
|PAR01 |巴黎|歐洲| Skylake、Broadwell |
|SAO01 |聖保羅|南美洲| Skylake、Broadwell |
|SEO01 |首爾|亞太地區| Skylake、Broadwell |
|SJC03 |聖荷西|NA 西部| Skylake、Broadwell、小型、中型、大型 |
|SJC04 |聖荷西|NA 西部| Skylake、Broadwell |
|SNG01 |新加坡|亞太地區| Skylake、Broadwell |
|SYD01 |雪梨|亞太地區| Skylake、Broadwell |
|SYD04 |雪梨|亞太地區| Skylake、Broadwell |
|TOK02 |東京|亞太地區| Skylake、Broadwell |
|TOR01 |多倫多|NA 東部| Skylake、Broadwell、小型、中型、大型 |
|WDC04 |華盛頓特區|NA 東部| Skylake、Broadwell、小型、中型、大型 |
|WDC06 |華盛頓特區|NA 東部| Skylake、Broadwell |
|WDC07 |華盛頓特區|NA 東部| Skylake、Broadwell |

部分 {{site.data.keyword.CloudDataCents_notm}} 提供預先配置的**小型**、**中型**及**大型** Bare Metal Server 選項。根據可用性及庫存供應，{{site.data.keyword.CloudDataCents_notm}} 可能會在 {{site.data.keyword.vmwaresolutions_short}} 主控台中顯示狀態指示器，以協助您規劃部署。

表 2. 訂購 vCenter Server 實例時 {{site.data.keyword.CloudDataCents_notm}} 的狀態指示器

|狀態|狀態詳細資料|
|:------------------------------|:--------------------------------------------------|
|即將推出                   |目前並未提供 {{site.data.keyword.CloudDataCent_notm}}。|
|暫時沒有庫存                  |目前並未提供 {{site.data.keyword.CloudDataCent_notm}}。|
|庫存受限             |{{site.data.keyword.CloudDataCent_notm}} 的可用性受限，可能無法完成訂單。|

## 管理元件的備份

您負責維護及確保所有實例元件的可用性。強烈建議您規劃所有管理元件的備份或高可用性。如需相關資訊，請參閱[備份元件](../archiref/solution/solution_backingup.html)。

## 適用於 vCenter Server 實例的服務

您可以根據需要來訂購實例基礎的附加程式服務（例如災難回復）。如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server 實例的服務](vc_addingremovingservices.html)。

## 容量考量

如需容量考量的相關資訊，請參閱[調整容量](../archiref/solution/solution_scaling.html)。

### 相關鏈結

* [vCenter Server 概觀](vc_vcenterserveroverview.html)
* [訂購 vCenter Server 實例](vc_orderinginstance.html)
* [擴充及縮減 vCenter Server 實例的容量](vc_addingremovingservers.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](vc_addingremovingservices.html)
