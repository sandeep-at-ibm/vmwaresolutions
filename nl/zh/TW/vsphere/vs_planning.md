---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

keywords: planning vSphere, data center, vSphere data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vSphere on IBM Cloud 的需求及規劃
{: #vs_planning}

在訂購 VMware vSphere on {{site.data.keyword.cloud}} 之前，請檢閱下列需求。根據 {{site.data.keyword.CloudDataCent_notm}} 位置及工作負載容量需求來規劃 VMware vSphere 叢集。

部署 ESXi 伺服器之後，您要負責設定環境、安裝和配置各種 VMware 元件。下列範例是 VMware 元件：VMware vCenter Server、VMware NSX 及 VMware vSAN。
{:note}

## IBM Cloud 帳戶需求
{: #vs_planning-account-req}

您使用的 {{site.data.keyword.cloud_notm}} 帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 帳戶的需求](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)。

## IBM Cloud Data Center 可用性
{: #vs_planning-dc-availability}

vSphere 部署對實體基礎架構有嚴格的需求。因此，您只能在符合需求的 {{site.data.keyword.CloudDataCents_notm}} 中部署叢集。下列 {{site.data.keyword.CloudDataCent_notm}} 可用於 vSphere 部署。

如果您選取 vSAN 元件，則會依 SSD（固態硬碟）可用性來過濾位置清單。
{:note}

表 1. vSphere 叢集可用的 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |位置|地區           |
|:----------------------|:---------|:---------------|
|AMS03 |阿姆斯特丹|歐洲|
|CHE01 |清奈|亞太地區|
|DAL09 |達拉斯|NA 南部|
|DAL10 |達拉斯|NA 南部|
|DAL12 |達拉斯|NA 南部|
|DAL13 |達拉斯|NA 南部|
|FRA02 |法蘭克福|歐洲|
|FRA04 |法蘭克福|歐洲|
|FRA05 |法蘭克福|歐洲|
|HKG02 |香港|亞太地區|
|LON02 |倫敦|歐洲|
|LON04 |倫敦|歐洲|
|LON05 |倫敦|歐洲|
|LON06 |倫敦|歐洲|
|MEL01 |墨爾本|亞太地區|
|MEX01 |克雷塔羅|NA 南部|
|MIL01 |米蘭|歐洲|
|MON01 |蒙特婁|NA 東部|
|OSL01 |奧斯陸|歐洲|
|PAR01 |巴黎|歐洲|
|SAO01 |聖保羅|南美洲|
|SEO01 |首爾|亞太地區|
|SJC03 |聖荷西|NA 西部|
|SJC04 |聖荷西|NA 西部|
|SNG01 |新加坡|亞太地區|
|SYD01 |雪梨|亞太地區|
|SYD04 |雪梨|亞太地區|
|TOK02 |東京|亞太地區|
| TOK04 |東京|亞太地區|
|TOR01 |多倫多|NA 東部|
|WDC04 |華盛頓特區|NA 東部|
|WDC06 |華盛頓特區|NA 東部|
|WDC07 |華盛頓特區|NA 東部|

## 相關鏈結
{: #vs_planning-related}

* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [擴充現有的叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [擴充在主控台以外建立的叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
