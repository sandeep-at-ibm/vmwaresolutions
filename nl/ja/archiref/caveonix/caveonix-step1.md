---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

# ステップ 1 - 初期計画と前提条件
{: #caveonix-step1}

Caveonix RiskForesight の各アプリケーション・コンポーネントは、疎結合の状態で一元管理されています。 したがって、「オールインワン」の仮想マシン (VM) というデプロイメント・パターンでデプロイすることもできますし、可用性、パフォーマンス、容量を高めるためにアプリケーション・コンポーネントを「スケールアウト」して複数の VM にデプロイすることも可能です。

デプロイメント・パターンは、可用性の要件とデータ保存のサイズ見積もりに基づいて決まります。 RiskForesight のデプロイメント・ノードは、以下のような特長があります。

-	基本 VM – 基本 VM は、データ保存のための拡大が不要なアプリケーション・コンポーネントのホストになるマシンです。 そこに含まれるコンポーネントとして、RiskForesight UI、RiskForesight アプリ、RiskForesight プラグイン、Central Collector、Remote Collector、Index Datastore、Messaging Datastore、Relational Datastore があります。
-	スケールアウト VM – スケールアウト VM、データベース、データ索引は、資産の数や必要なデータ保存量に応じた拡大が必要です。その量が多くなれば、スケールアウト・ハード・ディスク・スペースがさらに必要になり、スケールアウト VM も増やさなければなりません。

Caveonix RiskForesight には、以下の 3 つのデプロイメント・モデルがあります。

-	「オールインワン」– すべてのアプリケーション・コンポーネントをホストする 1 つの VM のデプロイメントと構成が自動で行われます。
  - すべてのアプリケーション・コンポーネントが 1 つの VM にインストールされます。
  - Remote Collector は、別個の VM にインストールできます。
  - 資産数が 100 個以下で、索引作成の期間が 7 日から 30 日分である、小規模なデプロイメント向けです。
-	部分分散 – 自動デプロイメントの完了後に、手動でスケールアウトすることができます。これは、初期 VM の RAM とディスクを増やし、3 つのスケールアウト VM を追加することによって行います。
  - UI、アプリ、プラグイン、Central Collector、Remote Collector、Index Datastore、Messaging Datastore、Relational Datastore を 1 つの VM にデプロイします。
  - Remote Collector は、別個の VM にインストールします。
  -	索引データ・ノードは、別個の VM にデプロイします。
  -	資産数が 500 個以下で、索引作成の期間が 30 日分である、小規模から中規模のデプロイメント向けです。
- 完全分散 - 資産の数とデータ保存要件に応じて基本 VM とスケールアウト VM をさらに追加します。
  - アプリケーション・コンポーネントを別々の VM に分散させて、スケーリングを実施しやすくします。
  -	資産の数が 500 個から 100,000 個の範囲で増えるのに合わせて、必要なデプロイメント・パターンを構成します。
  -	Remote Collector は、別個の VM にインストールします。
  -	UI は、複数の VM にインストールします。
  -	アプリとプラグインは、複数の VM にインストールします。
  -	Central Collector は、クラスター内で構成します。
  -	Relational Datastore は、1 次 / 2 次モデルでデプロイします。
  -	Messaging Datastore は、クラスター内にデプロイします。
  -	Index Datastore は、マスター・ノードとデータ・ノードでデプロイします。
  -	資産の数が増えるのに合わせて、スケールアウトに使用されるデータ・ノードをさらに追加します。

すべてのコンポーネントに FQDN が必要です。VM のデプロイメントの前にすべてのコンポーネントを DNS に登録する必要があります。 このステップは、初期の「オールインワン」デプロイメントでは IBM Cloud for VMware Solutions の自動処理によって実行されますが、デプロイメントのスケーリングの時にはお客様の責任で行う必要があります。

## 関連リンク
{: #caveonix-step1-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
