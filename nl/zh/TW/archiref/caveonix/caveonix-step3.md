---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 步驟 3 - 應用程式配置
{: #caveonix-step3}

此步驟使用 Caveonix RiskForesight 配置 Script。以「全功能」部署而言，這個 Script 是透過 IC4VS 自動化來啟動。如果要進行擴充，用戶端需要呼叫 Script，以部署局部或完全分散的部署拓蹼。這個 Script 會配置 RiskForesight 服務：
-	Caveonix 應用程式（API、中央收集器）
-	彈性搜尋
- PostgresSQL
-	遠端收集器
-	使用者介面
-	Kafka
-	Kibana
-	所有服務的憑證

在此步驟結束時，應用程式元件已安裝在必要的虛擬機器 (VM) 上。

## 相關鏈結
{: #caveonix-step3-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
