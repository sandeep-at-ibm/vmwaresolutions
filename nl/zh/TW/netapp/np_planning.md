---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# NetApp ONTAP Select 實例的需求及規劃
{: #np_planning}

請先檢閱下列需求，再訂購 NetApp ONTAP Select 實例。根據 {{site.data.keyword.CloudDataCent}} 位置以及工作負載效能及容量需求，來規劃實例。

## IBM Cloud 帳戶需求
{: #np_planning-account-req}

您使用的 {{site.data.keyword.cloud_notm}} 帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 帳戶的需求](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement)。

## IBM Cloud Data Center 可用性
{: #np_planning-dc-availability}

NetApp ONTAP Select 部署具有嚴格的實體基礎架構需求。因此，您只能在符合需求的 {{site.data.keyword.CloudDataCents_notm}} 中部署實例。下列 {{site.data.keyword.CloudDataCents_notm}} 適用於 NetApp ONTAP Select 部署：

表 1. NetApp ONTAP Select 實例的可用 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |位置|地區           |伺服器選項     |
|:------|:----------------|:----------------|:---------------------------|
|AMS03 |阿姆斯特丹|歐洲|高效能（中型）、高效能（大型）、高容量
|CHE01 |清奈|亞太地區|高容量
|DAL09 |達拉斯|NA 南部|高效能（中型）、高效能（大型）、高容量
|DAL10 |達拉斯|NA 南部|高效能（中型）、高效能（大型）、高容量
|DAL12 |達拉斯|NA 南部|高效能（中型）、高效能（大型）、高容量
|DAL13 |達拉斯|NA 南部|高效能（中型）、高效能（大型）、高容量
|FRA02 |法蘭克福|歐洲|高效能（中型）、高效能（大型）、高容量
|FRA04 |法蘭克福|歐洲|高效能（中型）、高效能（大型）、高容量
|HKG02 |香港|亞太地區|高效能（中型）、高效能（大型）、高容量
|LON02 |倫敦|歐洲|高效能（中型）、高效能（大型）、高容量
|LON04 |倫敦|歐洲|高效能（中型）、高效能（大型）、高容量
|LON06 |倫敦|歐洲|高效能（中型）、高效能（大型）、高容量
|MEL01 |墨爾本|亞太地區|高效能（中型）、高容量
|MEX01 |克雷塔羅|NA 南部|高效能（中型）、高效能（大型）、高容量
|MIL01 |米蘭|歐洲|高效能（中型）、高容量
|MON01 |蒙特婁|NA 東部|高效能（中型）、高效能（大型）、高容量
|OSL01 |奧斯陸|歐洲|高效能（中型）、高效能（大型）、高容量
|PAR01 |巴黎|歐洲|高效能（中型）、高效能（大型）、高容量
|SAO01 |聖保羅|南美洲|高效能（大型）、高容量
|SEO01 |首爾|亞太地區|高效能（大型）、高容量
|SJC03 |聖荷西|NA 西部|高效能（中型）、高效能（大型）、高容量
|SJC04 |聖荷西|NA 西部|高效能（中型）、高效能（大型）、高容量
|SNG01 |新加坡|亞太地區|高效能（中型）、高效能（大型）、高容量
|SYD01 |雪梨|亞太地區|高效能（中型）、高效能（大型）、高容量
|SYD04 |雪梨|亞太地區|高效能（中型）、高效能（大型）、高容量
|TOK02 |東京|亞太地區|高效能（大型）、高容量
|TOR01 |多倫多|NA 東部|高效能（中型）、高效能（大型）、高容量
|WDC04 |華盛頓特區|NA 東部|高效能（中型）、高效能（大型）、高容量
|WDC06 |華盛頓特區|NA 東部|高效能（中型）、高效能（大型）、高容量
|WDC07 |華盛頓特區|NA 東部|高效能（中型）、高效能（大型）、高容量

## 相關鏈結
{: #np_planning-related}

* [NetApp ONTAP Select 概觀](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)
* [訂購 NetApp ONTAP Select 實例](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
