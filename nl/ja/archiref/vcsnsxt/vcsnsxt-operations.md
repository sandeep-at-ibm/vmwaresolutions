---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# 操作上の考慮事項

## バックアップ

### VCS のバックアップ

Veeam バックアップ・ソフトウェアは、{{site.data.keyword.vmwaresolutions_full}} の一部 (オプション) として、VMware クラスター外の {{site.data.keyword.cloud_notm}} エンデュランス・ストレージを使用して {{site.data.keyword.cloud_notm}} 仮想サーバー・インスタンス (VSI) にデプロイされます。 このソフトウェアの目的は、ソリューションの管理コンポーネントをバックアップすることです。 [Veeam on {{site.data.keyword.cloud_notm}} の概要](../../services/veeam_considerations.html)に、オファリングに関する詳細を記載しています。

障害が発生した場合にシステムをその動作状態にリストアするためには、すべての NSX コンポーネントをバックアップしておくことが不可欠です。 NSX 仮想アプライアンスをバックアップするだけでは不十分です。有効なバックアップを取るためには、NSX マネージャー内の NSX バックアップ機能を使用する必要があります。この操作では、NSX バックアップ・データのリポジトリーとして FTP サーバーまたは SFTP サーバーを指定する必要があります。

NSX Manager のバックアップの対象となるのはすべての NSX 構成です。これには、コントローラー、論理スイッチング・エンティティー、論理ルーティング・エンティティー、セキュリティー、ファイアウォール・ルール、および NSX Manager ユーザー・インターフェースまたは API 内で構成するその他すべての項目が含まれます。 vCenter データベースおよびその関連エレメント (仮想スイッチなど) は、別個にバックアップする必要があります。 詳しくは、[NSX のファイル・ベースのバックアップ](../solution/solution_backingup.html#nsx-file-based-backup)を参照してください。 NSX 構成は、[vCenter のファイル・ベースのバックアップ](../solution/solution_backingup.html#vcenter-file-based-backup)と一緒にバックアップする必要があります。

### IBM Cloud Private のバックアップおよび災害復旧

障害が発生した場合にシステムをその動作状態にリストアするためには、ICP のデプロイメントをバックアップしておくことが不可欠です。 従来の VM バックアップには問題点があります。ICP マスター・ノードはすべて *etcd* サービスを実行するのに、*etcd* の文書には従来の VM バックアップを使用してリストアしないように明記されているという問題です。

プラットフォーム・レベルの {{site.data.keyword.cloud_notm}} Private の場合は、以下のコンポーネントをバックアップする必要があります。
- **etcd** - etcd は、Kubernetes リソースおよび Calico 状態情報を保管するために使用されます。
- **Docker レジストリー** - このプライベート・イメージ・レジストリーは、コンテナー・イメージ・ファイルを保管するために使用されます。
- **MongoDB** - このデータベースは、課金サービス、Helm リポジトリー・サーバー、Helm API サーバー、LDAP 構成、テナント (名前空間)、およびチーム/ユーザー/ユーザー・グループ役割の構成によって使用されます。
- **MariaDB** -このデータベースは OIDC によって使用されます。
-	**Elasticsearch** - システム・ログおよびアプリケーション・ログを保管します。
-	**Prometheus** - モニタリング用のデータを保管します。
-	**永続ストレージ** - {{site.data.keyword.cloud_notm}} Private または Kubernetes の永続ボリュームとストレージ・プロバイダーを使用する管理サービスで使用されます。

ストレージ・プロバイダーが提供するバックアップ・テクノロジーまたはリストア・テクノロジーを使用できます。 同様のプロセスをユーザーのアプリケーションに拡張することもできます。 詳しくは、[How to back up and restore {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8) のブログ、または [icp-backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/) を参照してください。

### CAM のバックアップおよび災害復旧

障害が発生した場合にシステムを正常な状態にリストアするためには、CAM デプロイメントのバックアップが不可欠です。 CAM のバックアップでは、お客様は以下のコンポーネントをバックアップする必要があります。
-	**Mongo データベース** – メインの CAM データベース。
-	**Maria データベース** - CAM Blueprint Designer で使用されます。
-	**NFS/Gluster ファイル・システム** - CAM データは 4 つの永続ボリュームに存在します。

### IKS のバックアップおよび DR

etcd データベースのバックアップは、マネージド・サービスの一部としてお客様に提供されますが、アプリケーション・データはすべて、お客様がバックアップする必要があります。

## スケーラビリティー

### VCS のスケーラビリティー

初期ホストをデプロイした後に、ユーザーは {{site.data.keyword.cloud_notm}} for VMware ポータルで計算容量をスケールアウトできます。

環境をスケールアウトするには、次の 3 つの方法があります。
-	別の vCenter Server が管理する新規サイトを追加する。
-	新規クラスターを追加する。
-	既存クラスターに新規ホストを追加する。

#### マルチサイト・デプロイメント

VMware on {{site.data.keyword.cloud_notm}} では、{{site.data.keyword.cloud_notm}} の世界中に配置されたデータ・センターや組み込まれたネットワーク・バックボーンを活用して、さまざまな地域横断的なユース・ケースをデプロイして機能させることができます。同じようなインフラストラクチャーをゼロから構築した場合にかかる時間に比べれば、ごくわずかな時間で構築できます。詳しくは、[vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスのマルチサイト構成](../../vcenter/vc_multisite.html)を参照してください。

#### 新規クラスターによるスケールアウト

ユーザーはコンソールで新規クラスターを作成し、ホストを注文することで計算容量をスケールアウトすることもできます。新規ホストは、新規クラスターに自動的に追加されます。このオプションを採用すると、別個のクラスターが環境内に作成されます。ユーザーは、管理ワークロードをアプリケーション・ワークロードから物理的および論理的に分離できるようになりますし、その他の特性 (例えば、Microsoft SQL データベース・クラスターなど) に基づいてワークロードを分離したり、高可用性トポロジーにアプリケーションをデプロイしたりできるようになります。 詳しくは、[vCenter Server インスタンスの注文](../../vcenter/vc_orderinginstance.html)を参照してください。

#### 既存のクラスターのスケールアウト

ユーザーは、コンソール内からホストを注文することによって既存のクラスターをスケールアウトできます。新しいホストは、当該クラスターに自動的に追加されます。 詳しくは、[vCenter Server インスタンスの容量の拡張と縮小](../../vcenter/vc_addingremovingservers.html)を参照してください。予約要件に基づいてクラスターの HA 予約ポリシーを調整しなければならない場合があります。

### ICP と IKS のスケーラビリティー

オンプレミスまたはクラウドのロケーションの空き計算容量に応じて、ユーザーは最初にデプロイしたブート・ノードからノード・アーキテクチャーをスケールアウトできます。環境をスケールアウトするには、以下のようにします。
-	ICP ワーカー・ノードを拡張する。
-	IKS オファリングを展開して使用する。

#### ICP の拡張

以下のように ICP ワーカー仮想マシン・ノードをスケーリングして、コンピュートまたはアプリケーションを拡張します。
- お客様は ICP がデプロイされている VXLAN に新規仮想マシンをプロビジョンします。
- お客様は、新規仮想マシンをプロビジョニングしてからブート・ノードにログインし、新規ノードをクラスターに追加するコマンドを実行することによって、ワーカー・ノードをスケーリングできます。 詳しくは、[クラスター・ノードの追加または削除](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)を参照してください。
- CAM を使用すると、VM をプロビジョニングし、コマンドを実行して ICP クラスターに追加する処理を自動化できます。

#### IKS の拡張

{{site.data.keyword.cloud_notm}} Portal を使用して IKS 環境をプロビジョンし、コンテナー環境を拡張して使用することができます。詳しくは、[Hybrid enhancements across {{site.data.keyword.cloud_notm}} Private and {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us) を参照してください。

IKS へのアプリケーション・デプロイメントは、以下の方法で行えます。
-	IKS 接続およびサービスを CAM で開発して、ICP カタログに公開する。
-	IKS インスタンスを管理する拡張機能である Multi Cloud Manager。
-	Helm コマンド・ライン。

### 関連リンク

* [VCS Hybridity Bundle の概要](../vcs/vcs-hybridity-intro.html)
