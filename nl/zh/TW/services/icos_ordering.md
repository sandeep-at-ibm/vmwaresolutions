---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-20"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購及配置 IBM Cloud Object Storage 與 Veeam
{: #icos_ordering}

推出 Veeam Availability Suite 9.5 Update 4 後，Veeam 即可與 IBM Cloud Object Storage (ICOS) 相容。在 IBM Cloud 上訂購 Veeam 時，並不會自動訂購 IBM Cloud Object Storage，但在部署之後可以新增它。

若要訂購 IBM Cloud Object Storage，請依指定的順序完成下列作業。

## 建立 Object Storage 實例
{: #icos_ordering-obj}

若要建立 Object Storage 實例，請參閱[建立新的服務實例](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-order-storage#creating-a-new-service-instance)。請遵循這些步驟並回到本節，以繼續執行下列作業。

## 建立儲存區
{: #icos_ordering-bucket}

若要建立儲存區，請參閱[步驟 1：建立一些儲存區來儲存資料](https://cloud.ibm.com/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-getting-started-console-#create-buckets)。請遵循這些步驟並回到本節，以繼續執行下列作業。

## 建立服務認證
{: #icos_ordering-service-cred}

若要建立服務認證（包括 HMAC 認證），請參閱[服務認證](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials)。請遵循這些步驟並回到本節，以繼續執行下列作業。

## 新增橫向擴充儲存庫
{: #icos_ordering-scale-repo}

若要在 Veeam 內新增橫向擴充儲存庫，請參閱[新增橫向擴充儲存庫](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window}。請遵循這些步驟並回到本節，以繼續執行下列作業。

## 維護及管理雲端層級
{: #icos_ordering-manage-cloud}

如需維護及管理雲端層級的相關資訊，請參閱[管理容量層級資料](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window}。
