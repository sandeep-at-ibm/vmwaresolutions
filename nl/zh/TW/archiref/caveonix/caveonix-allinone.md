---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

subcollection: vmware-solutions


---

# 全功能部署
{: #caveonix-allinone}

管理所有 RiskForesight 應用程式元件的單一虛擬機器 (VM) 的自動化部署及配置。此部署模型適合小型部署，最多 100 個資產（有 7 - 30 天的檢索）。下表顯示「全功能」VM 詳細資料：

表 1. 全功能參數

|參數	| 值  |
|---|---|
|類型	| 基本 |
|VM 數量	|1 |
|vCPU	|16 |
|RAM	|32 GB|
|磁碟 |80 GB|
|OS	|CentOS 7|
|已安裝的應用程式元件|	使用者介面、應用程式、外掛程式、中央收集器、索引資料儲存庫、傳訊資料儲存庫、關聯式資料儲存庫、索引資料儲存庫、遠端收集器|

下表顯示其他的「遠端收集器」VM 詳細資料。

表 2. 遠端收集器

|參數	| 值  |
|---|---|
|VM 數量	|視需要|
|vCPU	| 8                                   |
|RAM	| 8 GB          |
|磁碟 |1 TB|
|OS	|CentOS 7|
|已安裝的應用程式元件|遠端收集器|

## 相關鏈結
{: #caveonix-allinone-related}

*   [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
