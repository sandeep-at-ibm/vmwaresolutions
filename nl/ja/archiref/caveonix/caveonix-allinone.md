---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# オールインワン・デプロイメント
{: #caveonix-allinone}

すべての RiskForesight アプリケーション・コンポーネントをホストする単一の仮想マシン (VM) のデプロイメントと構成が自動で行われます。このデプロイメント・モデルは、資産数が 100 個以下で、索引作成の期間が 7 日から 30 日分である、小規模なデプロイメントに適しています。この「オールインワン」VM の詳細は以下の表に示されています。

表 1. オールインワン・パラメーター

|パラメーター	|値|
|---|---|
|タイプ	|基本|
|VM の数	|1|
|vCPU	|16|
|RAM	|32 GB|
|ディスク	|80 GB|
|OS	|CentOS 7|
|インストールされるアプリケーション・コンポーネント|	UI、アプリ、プラグイン、Central Collector、Index Datastore、Messaging Datastore、Relational Datastore、Index Datastore、Remote Collector|

Remote Collector VM のその他の詳細は以下の表に示されています。

表 2. Remote collector

|パラメーター	|値|
|---|---|
|VM の数	|必要に応じた値|
|vCPU	|8|
|RAM	|8 GB|
|ディスク	|1 TB|
|OS	|CentOS 7|
|インストールされるアプリケーション・コンポーネント|Remote Collector|

## 関連リンク
{: #caveonix-allinone-related}

*   [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
