---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 局部分散
{: #caveonix-partially}

自動化部署完成之後，您可以在起始虛擬機器 (VM) 中增加 RAM 及磁碟，並新增三個橫向擴充 VM，來手動橫向擴充。您可以執行 Riskforesight 配置 Script，在所有四個 VM 上啟用及配置應用程式元件。

此部署模型預期可服務多達 500 個「資產」，以及最多 30 天的資料檢索。

從 {{site.data.keyword.cloud}} 專用可攜式子網路中選取下一個可用的 IP 位址。在 ADDNS 中配置 FQDN 名稱。

VM 的大小如下所示：

表 1. 基本參數

|參數	| 值  |
|---|---|
|類型	| 基本 |
|VM 數量	|1 |
|vCPU	|16 |
|RAM	|64 GB|
|磁碟 |1000 GB|
|OS	|CentOS 7|
|已安裝的應用程式元件|使用者介面、應用程式、外掛程式、中央收集器、索引資料儲存庫、傳訊資料儲存庫、關聯式資料儲存庫、遠端收集器|

橫向擴充 VM 詳細資料如下：

表 2. 橫向擴充參數

|參數	| 值  |
|---|---|
|類型	|橫向擴充 |
|VM 數量	| 3 |
| vCPU	| 8                                   |
| RAM	| 16 GB |
|磁碟 | 4 TB |
| OS	| CentOS 7 |
|已安裝的應用程式元件|資料節點（橫向擴充）|

下表顯示「遠端收集器」VM 詳細資料。

表 3. 遠端收集器參數

|參數	| 值  |
|---|---|
|VM 數量	|視需要|
|vCPU	| 8                                   |
|RAM	| 8 GB          |
|磁碟 |1 TB|
|OS	|CentOS 7|
|已安裝的應用程式元件|遠端收集器|

## 相關鏈結
{: #caveonix-partially-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
