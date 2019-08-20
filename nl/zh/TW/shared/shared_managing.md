---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 Shared 資源
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} Shared 提供為實驗性的供應項目。
{:note}

客戶使用 {{site.data.keyword.vmwaresolutions_short}} 供應項目來管理虛擬資料中心的生命週期。

不論使用 Web 使用者介面還是公用 API，都支援下列功能：
- 檢視虛擬資料中心實例
- 存取 vCloud 管理主控台
- 調整虛擬資料中心實例大小
- 刪除虛擬資料中心實例
- 在虛擬資料中心實例中新增和移除 VMware 服務（**未來**）

## 檢視虛擬資料中心實例
{: #shared_managing-viewing}

若要檢視針對使用者帳戶佈建之所有 Virtual Data Center 實例的摘要，請完成下列步驟：

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，從左導覽窗格按一下**資源**。
2. 從主控台橫幅，按一下您的使用者帳戶圖示，然後按一下**帳戶**欄位，以選取您要檢查其實例的使用者帳戶。  
3. 在 **IBM Cloud VMware Solutions Shared** 表格中，檢視佈建在所選取使用者帳戶中的實例清單。

|項目        |說明       |  
|:------------- |:------------- |
|名稱 |實例的名稱|
|類型      |虛擬資料中心的類型|
|位置|管理實例所在的 {{site.data.keyword.CloudDataCent_notm}} |  
|建立時間|建立實例的日期和時間|
|狀態|實例的狀態|

{: caption="表 1. 虛擬資料中心實例項目" caption-side="top"}

實例可以具有一定範圍的狀態。

|狀態|說明       |
|:------------- |:------------- |
|正在建立|正在建立實例。|
|備妥使用|實例已備妥可供使用。|
|正在修改|正在修改實例。|
|正在刪除|正在刪除實例。|
|已刪除|已刪除實例。|

{: caption="表 2. 虛擬資料中心實例的狀態說明" caption-side="top"}

## 檢視虛擬資料中心詳細資料的程序
{: #vc_viewinginstances-procedure-view-vdc-details}

若要檢視實例的內容詳細資料，請執行下列動作：

1. 在 **IBM Cloud VMware Solutions Shared** 表格中，按一下實例名稱。
2. 在**內容**下，檢視實例的詳細資料。

|內容            |說明       |
|:------------- |:------------- |
|名稱 |實例的名稱。|
|類型      |虛擬資料中心類型。|
|位置|管理實例所在的 {{site.data.keyword.CloudDataCent_notm}}。|
|ID |實例的 ID。|
|建立時間|建立實例的日期和時間，這也是計費開始時的日期和時間。|
| vCPU |虛擬資料中心可以隨時使用的 CPU 限制或保留數量。|
| RAM       |虛擬資料中心可以隨時使用的記憶體限制或保留數量。|
|公用 IP|每個虛擬資料中心都隨附 5 個公用 IP 位址，可用於將 vApp 和 VM 連接至網際網路。|

{: caption="表 3. 虛擬資料中心內容" caption-side="top"}

## 存取 vCloud Director 管理主控台
{: #shared_managing-accessing}

透過「vCloud Director 管理主控台」來管理虛擬資料中心。

對「vCloud Director 管理主控台」的首次存取是使用 **admin** 認證所完成。在「虛擬資料中心」詳細資料頁面中，使用**重設位置密碼**鏈結來產生密碼。此動作會產生初始複雜隨機密碼，該密碼可隨時重設。

{{site.data.keyword.vmwaresolutions_short}} 供應項目不會儲存 **admin** 密碼。產生密碼之後，您必須擷取它。如果密碼遺失，則應該產生新密碼。

同一位置的所有虛擬資料中心都具有相同的 **admin** 密碼。重設虛擬資料中心實例上的密碼會重設 **admin** 密碼，此密碼供同一位置中的所有虛擬資料中心實例存取「vCloud Director 管理主控台」。

產生第一個 **admin** 密碼後，詳細資料頁面右上角的 **vCloud Director 入口網站**按鈕會變為可用。按一下 **vCloud Director 入口網站**可存取「vCloud Director 管理主控台」。若要登入，請使用使用者名稱 **admin** 以及透過**重設位置密碼**鏈結取得的密碼。

## 調整虛擬資料中心實例大小
{: #shared_managing-resizing}

虛擬資料中心實例處於**可供使用**狀態時，可以隨時變更指派給虛擬資料中心的資源數量。 

在「虛擬資料中心」詳細資料頁面中，調整虛擬資料中心實例的 vCPU 或 RAM 資源的大小。按一下詳細資料頁面上**資源**旁邊的「鉛筆」圖示，然後變更 vCPU 或 RAM 內容的值。

最後，先驗證配置及預估成本，再下訂單。

  如果在正在使用 vCPU 和 RAM 資源時下調其大小，則配置變更會失敗，因為無法將「虛擬資料中心」資源下調到低於目前作用中資源用量的層次。
  {:note}

進行變更時，「虛擬資料中心」實例會進入**正在修改**狀態。資源備妥可用時，狀態會變更為**備妥使用**。

## 刪除虛擬資料中心實例
{: #shared_managing-deleting}

「虛擬資料中心」實例處於**可供使用**狀態時，可以將其刪除。在「虛擬資料中心」詳細資料頁面或「IBM Cloud VMware Solutions Shared 資源」表格中執行刪除作業。

在詳細資料頁面中，按一下詳細資料頁面右上角的溢位功能表選項中的**刪除**圖示。然後，確認您想要刪除實例。

在「IBM Cloud VMware Solutions Shared 資源」表格中，找出您要刪除的實例，然後按一下**動作**直欄中的**刪除**圖示。然後，確認您想要刪除實例。

## 相關鏈結
{: #shared_managing-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [訂購 Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [訂購 Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
