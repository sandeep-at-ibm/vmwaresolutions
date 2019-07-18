---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: IBM Cloud Object Storage, ICOS configuration, order Cloud Object Storage

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購及配置 IBM Cloud Object Storage 與 Veeam
{: #icos_ordering}

推出 Veeam Availability Suite 9.5 Update 4 後，Veeam 即可與 IBM Cloud Object Storage (ICOS) 相容。訂購 Veeam on IBM Cloud 時，不會自動訂購 IBM Cloud Object Storage，但可以在部署後新增 IBM Cloud Object Storage。

若要訂購 IBM Cloud Object Storage，請依指定的順序完成下列作業。

## 建立 Object Storage 實例
{: #icos_ordering-obj}

若要建立 Object Storage 實例，請參閱[建立新服務實例](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance)。請遵循這些步驟並回到本節，以繼續執行下列作業。

## 建立儲存區
{: #icos_ordering-bucket}

若要建立儲存區，請參閱[建立一些儲存區來儲存資料](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets)。請遵循這些步驟並回到本節，以繼續執行下列作業。

## 建立服務認證
{: #icos_ordering-service-cred}

若要建立服務認證（包括 HMAC 認證），請參閱[服務認證](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials)。請遵循這些步驟並回到本節，以繼續執行下列作業。

## 新增橫向擴充儲存庫
{: #icos_ordering-scale-repo}

* 作為 Veeam 服務安裝和配置的一部分，將建立一個名為 `IC4V 橫向擴充儲存庫`的橫向擴充備份儲存庫。`IC4V 預設 VM 備份儲存庫`將作為範圍新增到橫向擴充儲存庫。
* 建立備份工作時，必須選取 `IC4V 橫向擴充儲存庫`作為備份儲存庫，而不是選取 `IC4V 預設配置備份儲存庫`。IC4V 預設配置備份儲存庫是用於 Veeam 配置備份。
* 您可以將更多儲存庫新增到此預設儲存庫，例如，類型為 Object Storage 的備份儲存庫。如需相關資訊，請參閱 [Adding Scale-Out Repositories](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:external}。請遵循這些步驟並回到本節，以繼續執行下列作業。

## 維護及管理雲端層級
{: #icos_ordering-manage-cloud}

如需相關資訊，請參閱 [Managing Capacity Tier Data](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:external}。

## 相關鏈結
{: #icos_ordering-related}

* [Veeam on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [訂購 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Managed Services for Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
