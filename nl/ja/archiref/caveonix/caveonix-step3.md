---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# ステップ 3 - アプリケーションの構成
{: #caveonix-step3}

このステップでは、Caveonix RiskForesight の構成スクリプトを使用します。 「オールインワン」デプロイメントでは、IC4VS の自動処理によってこのスクリプトが開始されます。 スケーリングの場合は、部分分散デプロイメントまたは完全分散デプロイメントでトポロジーをデプロイするためにクライアント側でこのスクリプトを呼び出す必要があります。 このスクリプトによって、RiskForesight の以下のサービスが構成されます。
-	Caveonix アプリ (API、Central Collector)
-	Elastic Search
- PostgresSQL
-	Remote Collector
-	UI
-	Kafka
-	Kibana
-	すべてのサービスの証明書

このステップが終了すると、必要な仮想マシン (VM) にアプリケーション・コンポーネントがインストールされます。

## 関連リンク
{: #caveonix-step3-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
