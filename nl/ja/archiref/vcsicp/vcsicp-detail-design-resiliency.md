---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# バックアップ、災害復旧 (DR)、およびスケーラビリティー
{: #vcsicp-detail-design-resiliency}

## バックアップおよび DR
{: #vcsicp-detail-design-resiliency-backup-dr}

### VMware vCenter Server on IBM Cloud のバックアップ
{: #vcsicp-detail-design-resiliency-vcs-backup}

{{site.data.keyword.vmwaresolutions_full}} の一部として、VMware クラスター外部の {{site.data.keyword.cloud_notm}} Endurance Storage を使用する Veeam バックアップ・ソフトウェアが {{site.data.keyword.cloud_notm}} 仮想サーバー・インスタンス (VSI) にオプションでデプロイされます。 このソフトウェアの目的は、このソリューションの管理コンポーネントをバックアップすることです。

### NSX のバックアップ
{: #vcsicp-detail-design-resiliency-nsx-backup}

障害が発生した場合にシステムをその動作状態にリストアするためには、すべての NSX コンポーネントを適切にバックアップしておくことが不可欠です。 NSX 仮想マシン (VM) をバックアップするだけでは不十分です。 NSX VM をバックアップするだけでは不十分です。適切なバックアップを行うためには NSX Manager 内の NSX バックアップ機能を使用する必要があります。 NSX バックアップ・データのリポジトリーとして FTP サーバーまたは SFTP サーバーを指定する必要があります。
NSX Manager のバックアップの対象となるのは、すべての NSX 構成です。これにはコントローラー、論理スイッチング・エンティティー、論理ルーティング・エンティティー、セキュリティー、ファイアウォール・ルール、および NSX Manager ユーザー・インターフェースまたは API 内で構成するその他すべての項目が含まれます。 vCenter データベースおよびその関連エレメント (仮想スイッチなど) を別途バックアップする必要があります。 NSX 構成は vCenter バックアップと共にバックアップする必要があります。

### IBM Cloud Private のバックアップおよび DR
{: #vcsicp-detail-design-resiliency-backup-dr-icp}

障害が発生した場合にシステムをその動作状態にリストアするためには、{{site.data.keyword.icpfull_notm}} のデプロイメントをバックアップしておくことが不可欠です。 従来の VM バックアップに加えて、すべての {{site.data.keyword.icpfull_notm}} マスター・ノードは etcd を実行します。 etcd の文書には、リストアを行う際に従来の VM バックアップを使用してはならないと明確に記載されています。

プラットフォーム・レベルの {{site.data.keyword.icpfull_notm}} では、以下のコンポーネントをバックアップする必要があります。
- **Etcd** は Kubernetes リソースおよび Calico 状態情報を補完するために使用されます。
- **Docker レジストリー** イメージ・リポジトリーにコンテナー・イメージ・ファイルを保管するために使用されるプライベート・イメージ・レジストリー。
- **MongoDB** 課金サービス、Helm リポジトリー・サーバー、Helm API サーバー、LDAP 構成、テナント (名前空間)、およびチーム/ユーザー/ユーザー・グループ役割の構成によって使用されるデータベース。
- **MariaDB** OIDC によって使用されるデータベース。
- **Elasticsearch** システム・ログおよびアプリケーション・ログを保管します。
- **Prometheus** モニタリング用のデータを保管します。
- **永続ストレージ**は、{{site.data.keyword.icpfull_notm}} または Kubernetes の永続ボリュームとストレージ・プロバイダーを利用する管理サービスで使用されます。 ストレージ・プロバイダーが提供するバックアップ・テクノロジーまたはリストア・テクノロジーを使用できます。 同様のプロセスをユーザーのアプリケーションに拡張することもできます。

### CAM のバックアップおよび DR
{: #vcsicp-detail-design-resiliency-backup-dr-cam}

障害が発生した場合にシステムをその動作状態にリストアするためには、CAM のデプロイメントをバックアップしておくことが不可欠です。 CAM のバックアップでは、お客様は以下のコンポーネントをバックアップする必要があります。
- **Mongo データベース**は、メインの CAM データベースです。
- **Maria データベース**は、CAM Blueprint Designer で使用されるデータベースです。
- **NFS/GlusterFS** は、4 つの永続ボリュームに CAM データがある場所です。

### IBM Cloud Kubernetes Service のバックアップおよび DR
{: #vcsicp-detail-design-resiliency-backup-dr-iks}

etcd データベースのバックアップは、管理対象サービスの一部としてお客様に提供されます。アプリケーション・データはすべて、自身でバックアップする必要があります。

## スケーラビリティー
{: #vcsicp-detail-design-resiliency-scalability}

### VCS のスケーラビリティー
{: #vcsicp-detail-design-resiliency-vcs-scalability}

初期ホストをデプロイした後に、ユーザーは {{site.data.keyword.cloud_notm}} for VMware ポータルで計算容量をスケールアウトできます。

環境のこのスケールアウトは、以下の 3 つの方法のいずれかを使用します。
- 別々の vCenter Server が管理する新規サイトを追加する。
- 新規クラスターを追加する。
- 既存クラスターに新規ホストを追加する。

#### マルチサイト・デプロイメント
{: #vcsicp-detail-design-resiliency-multi-site}

VMware on {{site.data.keyword.cloud_notm}} は、IBM Cloud の世界規模のデータ・センターおよび統合されたネットワーク・バックボーンを使用して、地域をまたがるさまざまなユース・ケースをデプロイし、インフラストラクチャーを最初から構築するよりもずっと短時間で機能できるようにします。

#### 新規クラスターによるスケールアウト
{: #vcsicp-detail-design-resiliency-scale-out-new}

ユーザーはコンソールで新規クラスターを作成し、ホストを注文することで計算容量をスケールアウトできます。新しいホストは、新規クラスターに自動的に追加されます。 このオプションを採用すると、別個のクラスターが環境内に作成されます。ユーザーは、管理ワークロードをアプリケーション・ワークロードから物理的および論理的に分離できるようになりますし、その他の特性 (例えば、Microsoft SQL データベース・クラスターなど) に基づいてワークロードを分離したり、高可用性トポロジーにアプリケーションをデプロイしたりできるようになります。

#### 既存のクラスターのスケールアウト
{: #vcsicp-detail-design-resiliency-scale-out-existing}

ユーザーは、コンソール内からホストを注文することによって既存のクラスターをスケールアウトできます。新しいホストは、当該クラスターに自動的に追加されます。 場合によっては、ユーザーはその予約要件に基づいて、クラスターの HA 予約ポリシーを調整する必要があります。

### IBM Cloud Private のスケーラビリティー
{: #vcsicp-detail-design-resiliency-icp-scalability}

オンプレミスまたはクラウドのロケーションの空き計算容量に応じて、ユーザーは最初にデプロイしたブート・ノードからノード・アーキテクチャーをスケールアウトできます。

環境のスケールアウトは以下の方法で行います。
- {{site.data.keyword.icpfull_notm}} ワーカー・ノードを拡張する。
- {{site.data.keyword.containerlong_notm}} オファリングを展開して使用する。

#### IBM Cloud Private の拡張
{: #vcsicp-detail-design-resiliency-icp-expansion}

以下のように、{{site.data.keyword.icpfull_notm}} ワーカーの VM ノードをスケーリングして、コンピュートまたはアプリケーションを拡張できます。
- お客様は {{site.data.keyword.icpfull_notm}} がデプロイされている VXLAN に新規 VM をプロビジョンします。
- お客様は、新規 VM をプロビジョニングしてからブート・ノードにログインし、新規ノードをクラスターに追加するコマンドを実行することによって、ワーカー・ノードをスケーリングできます。
- CAM を使用して、VM のプロビジョニング、および {{site.data.keyword.icpfull_notm}} クラスターへの追加を行うコマンドの実行を自動化します。

###  IBM Cloud Kubernetes Service の拡張
{: #vcsicp-detail-design-resiliency-iks-expansion}

ユーザーは、{{site.data.keyword.cloud_notm}} Portal を介して {{site.data.keyword.containerlong_notm}} 環境をプロビジョンし、コンテナー環境を拡張または使用することができます。

{{site.data.keyword.containerlong_notm}} へのアプリケーション・デプロイメントには、以下を使用します。
- {{site.data.keyword.containerlong_notm}} 接続またはサービスを CAM で開発して、{{site.data.keyword.icpfull_notm}} カタログに公開する。
- {{site.data.keyword.containerlong_notm}} インスタンスを管理するための Multi-Cloud Manager の今後の機能拡張
- Helm コマンド・ライン・インターフェース。
- 高可用性を向上させるためのマルチゾーン・クラスターの使用。

## 関連リンク
{: #vcsicp-detail-design-resiliency-related}

* [クラスター・ノードの追加または削除](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [既存のワーカー・プールのサイズを変更してワーカー・ノードを追加する](/docs/containers?topic=containers-clusters)
* [How to back up and restore {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [{{site.data.keyword.icpfull_notm}} バックアップ GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
