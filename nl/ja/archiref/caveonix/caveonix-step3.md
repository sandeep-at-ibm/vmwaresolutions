---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# ステップ 3 - アプリケーションの構成
{: #caveonix-step3}

このステップでは、Caveonix RiskForesight の構成スクリプトを使用します。 「オールインワン」デプロイメントでは、IBM Cloud for VMware Solutions の自動処理によってこのスクリプトが開始されます。

スケーリングの場合は、部分分散トポロジーまたは完全分散トポロジーをプロビジョンするためにクライアント側でこのスクリプトを呼び出す必要があります。 このスクリプトによって、RiskForesight の以下のサービスが構成されます。
- Caveonix アプリ (API、Central Collector)
- Elastic Search
- PostgresSQL
- Remote Collector
- UI
- Kafka
- Kibana
- すべてのサービスの証明書

このステップが終了すると、必要な仮想マシン (VM) にアプリケーション・コンポーネントがインストールされます。
