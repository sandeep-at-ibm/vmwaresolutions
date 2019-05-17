---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 新增、檢視及刪除 KMIP for VMware on IBM Cloud 實例的憑證
{: #kmip_standalone_addingdeletingcert}

在您的 KMIP for VMware on {{site.data.keyword.cloud}} 實例就緒之後，您必須在其中新增憑證。當您不再需要憑證時，請將它從實例中刪除。

## 將憑證新增至 KMIP for VMware on IBM Cloud 實例的程序
{: #kmip_standalone_addingdeletingcert-add}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，從左導覽窗格按一下**資源**。
2. 向下捲動至 **KMIP for VMware on IBM Cloud 實例**表格，按一下您要為其新增憑證的實例。
3. 按一下**新增**。
4. 在**新增用戶端 SSL 憑證**視窗中，輸入憑證名稱及內容。

   憑證名稱不能在選取的實例內重複使用。憑證內容必須有效，並且包含 BEGIN CERTIFICATE 及 END CERTIFICATE 標籤，而且憑證不能在已部署實例的選取地區內重複使用。
   {:note}
5. 按一下**新增**。

## 檢視 KMIP for VMware on IBM Cloud 實例憑證的程序
{: #kmip_standalone_addingdeletingcert-view}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，從左導覽窗格按一下**資源**。
2. 向下捲動至 **KMIP for VMware on IBM Cloud 實例**表格，按一下要檢視其憑證的實例。
3. 檢視**用戶端 SSL 憑證**區段下的已新增憑證清單。
4. 若要檢視特定憑證的內容，請按一下**下載**。

## 從 KMIP for VMware on IBM Cloud 實例刪除憑證的程序
{: #kmip_standalone_addingdeletingcert-delete}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，從左導覽窗格按一下**資源**。
2. 向下捲動至 **KMIP for VMware on IBM Cloud 實例**表格，按一下您要從中刪除憑證的實例。
3. 在**用戶端 SSL 憑證**表格中，找出您要刪除的憑證，然後按一下**刪除**圖示。

   基於加密及解密資料或備份資料，用戶端會立即遺失所有金鑰的存取權。若要讓用戶端重新取得存取權，您必須再次新增用戶端 SSL 憑證。
   {:note}

## 相關鏈結
{: #kmip_standalone_addingdeletingcert-related}

* [檢視 KMIP for VMware on IBM Cloud 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [訂購 KMIP for VMware on IBM Cloud 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [刪除 KMIP for VMware on IBM Cloud 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker 事件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
