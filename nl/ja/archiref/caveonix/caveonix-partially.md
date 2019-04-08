---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# 部分分散
{: #caveonix-partially}

自動デプロイメントの完了後に、手動でスケールアウトすることができます。これは、初期仮想マシン (VM) の RAM とディスクを増やし、3 つのスケールアウト VM を追加することによって行います。 Riskforesight 構成スクリプトを実行することで、4 つのすべての VM 上のアプリケーション・コンポーネントを有効にし、構成することができます。

このデプロイメント・モデルでは、最大 500 個の資産と、最大 30 日分のデータの索引作成が可能です。

{{site.data.keyword.cloud}} プライベート・ポータブル・サブネットから、次に使用可能な IP アドレスを選択します。 ADDNS で FQDN 名を構成します。

VM のサイズは以下のとおりです。

表 1. 基本パラメーター

|パラメーター	|値|
|---|---|
|タイプ	|基本|
|VM の数	|1|
|vCPU	|16|
|RAM	|64 GB|
|ディスク	|1000 GB|
|OS	|CentOS 7|
|インストールされるアプリケーション・コンポーネント	|UI、アプリ、プラグイン、Central Collector、Index Datastore、Messaging Datastore、Relational Datastore、Remote Collector|

スケールアウト VM の詳細は以下のとおりです。

表 2. スケールアウト・パラメーター

| パラメーター	| 値 |
|---|---|
| タイプ	| スケールアウト |
| VM の数	| 3 |
| vCPU	| 8 |
| RAM	| 16 GB |
| ディスク	| 4 TB |
| OS	| CentOS 7 |
| インストールされるアプリケーション・コンポーネント	| データ・ノード (スケールアウト) |

Remote Collector VM の詳細を以下の表に示します。

表 3. Remote Collector のパラメーター

|パラメーター	|値|
|---|---|
|VM の数	|必要に応じた値|
|vCPU	|8|
|RAM	|8 GB|
|ディスク	|1 TB|
|OS	|CentOS 7|
|インストールされるアプリケーション・コンポーネント	|Remote Collector|

## 関連リンク
{: #caveonix-partially-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
