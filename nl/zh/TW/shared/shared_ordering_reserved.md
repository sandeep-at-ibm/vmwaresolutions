---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resources, order reserved shared, order reserved resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購 Shared Reserved
{: #shared_ordering_reserved}

{{site.data.keyword.vmwaresolutions_full}} Shared 提供為實驗性的供應項目。
{:note}

對於 Shared Reserved，已預先分配 vCPU 和 RAM 虛擬資料中心保留，並且保證其可用性。
* 按月計算完整保留的成本，並以虛擬資料中心的配置大小為基礎。
* vCPU 及 RAM 資源可以視需要增加和減少。
* 虛擬資料中心中可以配置及使用的儲存空間量沒有限制。費用會根據已配置儲存空間的 GB 數按小時計算。
* 入埠及出埠公用網路作業量沒有限制。公用頻寬是按每 GB 收費。

## IBM Cloud for VMware Solutions Shared 的需求
{: #shared_ordering_reserved-req}

### IBM Cloud 基礎架構帳戶
{: #shared_ordering_reserved-account-req}

若要使用 {{site.data.keyword.vmwaresolutions_short}} 來訂購 IBM Cloud for VMware Solutions Shared，您必須有**隨收隨付制**或**訂閱**的 {{site.data.keyword.cloud_notm}} 帳戶。所訂購資源的費用會向該 {{site.data.keyword.cloud_notm}} 帳戶收取。

### 虛擬資料中心名稱需求
{: #shared_ordering_reserved-vdc-name-req}

虛擬資料中心名稱*應該* 符合下列需求。未來將施行命名需求。
* 只容許小寫英文字母、數字及橫線 (-) 字元。
* 名稱的開頭必須是小寫英文字母。
* 名稱的結尾必須是小寫英文字母或數值字元。
* 虛擬資料中心名稱的長度上限為 10 個字元。
* 虛擬資料中心名稱在您的帳戶中必須是唯一的。

## 訂購 Shared Reserved 的程序
{: #shared_ordering-procedure}

1. 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格中的 **VMware** 圖示，然後按一下 **VMware 虛擬資料中心**區段中的 **IBM Cloud for VMware Solutions Shared** 卡。
2. 在 **IBM Cloud for VMware Solutions Shared** 頁面上，按一下 **Reserved** 卡，然後按一下**建立**。
3. 在 **IBM Cloud for VMware Solutions Shared - Reserved** 頁面上，輸入虛擬資料中心名稱。
4. 選擇用於保留資源的時間承諾。會預先選取有提供供應項目的 {{site.data.keyword.CloudDataCent_notm}}。
5. 指定資源保留：
    * 選取**預先配置**時，請選取其中一個預設配置。
    * 選取**自訂**時，指定 vCPU 和 RAM 保留。
6. 在**訂單摘要**窗格上，先驗證配置及預估成本，然後才下訂單。
7. 按一下**佈建**。

## 訂購 Shared Reserved 後的結果
{: #shared_ordering_reserved-results}

* 資源的部署會自動啟動，且您會收到確認，指出正在處理該訂單。您可以檢查部署狀態，包括可能需要注意的任何問題，方法是檢視**虛擬資料中心狀態**。
* 順利部署資源之後，會在您的 VMware 虛擬平台上安裝 [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared 的技術規格](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs)中所說明的元件。
* 資源備妥可用時，狀態會變更為**備妥使用**。

## 相關鏈結
{: #shared_ordering_reserved-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [訂購 Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [管理 {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
