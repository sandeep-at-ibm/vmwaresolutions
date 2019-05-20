---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-19"

subcollection: vmware-solutions


---

# ソリューション・コンポーネント
{: #vcsicp-arch-overview-solution}

## VMware vCenter Server on IBM Cloud のコンポーネント
{: #vcsicp-arch-overview-solution-vcs-comp}

図 1. vCenter Server 環境図
![VCS 環境](vcsicp-vcsenv.svg)

### Platform Service Controller
{: #vcsicp-arch-overview-solution-psc}

vCenter Server デプロイメントでは、管理仮想マシン (VM) に関連付けられたプライベート VLAN 内のポータブル・サブネット上にインストールされた単一の外部プラットフォーム・サービス・コントローラーを使用します。 このデフォルト・ゲートウェイは、バックエンド・カスタマー・ルーター (BCR) に設定されます。

### vCenter Server
{: #vcsicp-arch-overview-solution-vcs}

プラットフォーム・サービス・コントローラーと同様に、vCenter Server はアプライアンスとしてデプロイされます。 さらに、vCenter Server は、管理 VM に関連付けられたプライベート VLAN 上のポータブル・サブネット上にインストールされます。 そのデフォルト・ゲートウェイは、その特定のサブネットの BCR に割り当てられた IP アドレスに設定されます。

### NSX Manager
{: #vcsicp-arch-overview-solution-nsx-manager}

NSX Manager は初期クラスター内にデプロイされます。 さらに、管理コンポーネント用に指定されたプライベート・ポータブル・アドレス・ブロックから VLAN–backed IP アドレスが NSX Manager に割り当てられ、DNS サーバーと NTP サーバーが構成されます

### NSX Controller
{: #vcsicp-arch-overview-solution-nsx-controllers}

{{site.data.keyword.cloud}} の自動化機能によって、初期クラスター内に 3 つの NSX Controller がデプロイされます。 管理コンポーネント用に指定されたプライベート・ポータブル・サブネットから VLAN–backed IP アドレスがコントローラーに割り当てられます。

### NSX Edge / DLR
{: #vcsicp-arch-overview-solution-nsx-edge}

NSX Edge Services Gateway (ESG) のペアがデプロイされます。 すべての場合において、プライベート・ネットワークに常駐する自動化コンポーネントからのアウトバウンド・トラフィックにゲートウェイ・ペアが 1 つ使用されます。 vCenter Server と {{site.data.keyword.icpfull_notm}} のための 2 つ目のゲートウェイ ({{site.data.keyword.icpfull_notm}} 管理エッジと呼ばれる) がデプロイされ、パブリック・ネットワークへのアップリンクとプライベート・ネットワークに割り当てられたインターフェースが構成されます。 分散論理ルーター (DLR)、論理スイッチ、ファイアウォールなどの必要な NSX コンポーネントは、管理者が構成できます。 [vCenter Server ネットワーキング・ガイド](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro)に、ネットワーク設計に関する詳細情報があります。

次の表は、{{site.data.keyword.icpfull_notm}} ESG/DLR の仕様を要約したものです。

表 1. {{site.data.keyword.icpfull_notm}} ESG の仕様

属性  |  仕様
--|--
Edge Service Gateway  |  仮想アプライアンス
Edge サイズ「大」 |   vCPU 数	2
メモリー	| 1-GB ディスク	| ローカル・データストアに 1000 GB

表 2. {{site.data.keyword.icpfull_notm}} DLR の仕様

属性  |  仕様
--|--|
分散論理ルーター | 	仮想アプライアンス
Edge サイズ「コンパクト」 | vCPU 数	1
メモリー	| 512-MB ディスク	| ローカル・データストアに 1000 GB

## IBM Cloud Private コンポーネント
{: #vcsicp-arch-overview-solution-icp-comp}

{{site.data.keyword.icpfull_notm}} は、オンプレミスのコンテナー化されたアプリケーションを開発および管理するためのアプリケーション・プラットフォームです。 これは、コンテナー・オーケストレーター Kubernetes、プライベート・イメージ・リポジトリー、管理コンソール、モニター・フレームワークを含む、コンテナーを管理するための統合環境です。

図 2. vCenter Server を含めた仮想 {{site.data.keyword.icpfull_notm}} のデプロイメント
![VCS を含めた仮想 {{site.data.keyword.icpfull_notm}} のデプロイメント](vcsicp-virtual-icp-deployment-vcs.svg)

###	ブート・ノード
{: #vcsicp-arch-overview-solution-boot-node}

ブート (ブートストラップ) ノード (オプション) は、インストール、構成、ノード・スケーリング、クラスター更新の実行に使用されます。 クラスターに必要なブート・ノードは 1 つのみです。 単一ノードをマスターとブートの両方に使用できます。

### マスター・ノード
{: #vcsicp-arch-overview-solution-master-node}

マスター・ノードは管理サービスを提供し、クラスター内のワーカー・ノードを制御します。 マスター・ノードは、リソース割り振り、状態保守、スケジューリング、モニターを行うプロセスをホストします。 高可用性 (HA) 環境には複数のマスター・ノードが含まれているため、先行マスター・ノードで障害が発生した場合は、フェイルオーバー・ロジックによって別のノードが自動的にマスター役割にプロモートされます。 マスターとして機能できるホストは、マスター候補と呼ばれます。

###	ワーカー・ノード
{: #vcsicp-arch-overview-solution-worker-node}

ワーカー・ノードは、タスクを実行するためのコンテナー化された環境を提供するノードです。 要求の増加に対応してパフォーマンスと効率を向上させるために、クラスターにさらにワーカー・ノードを簡単に追加できます。 クラスターには任意の数のワーカー・ノードを含めることができますが、少なくとも 1 つのワーカー・ノードが必要です。

### プロキシー・ノード
{: #vcsicp-arch-overview-solution-proxy-node}

プロキシー・ノードは、クラスター内で作成されたサービスに外部要求を送信するノードです。 高可用性 (HA) 環境には複数のプロキシー・ノードが含まれているため、先行プロキシー・ノードで障害が発生した場合は、フェイルオーバー・ロジックによって別のノードが自動的にプロキシー役割にプロモートされます。 単一ノードをマスターとプロキシーの両方として使用できますが、マスター・ノードの負荷を軽減するために専用プロキシー・ノードを使用します。 クラスター内でロード・バランシングが必要な場合は、少なくとも 1 つのプロキシー・ノードがクラスターになければなりません。

### 管理ノード
{: #vcsicp-arch-overview-solution-mgmt-node}

管理ノードは、モニター、課金、ロギングなどの管理サービスのみをホストするオプション・ノードです。 専用の管理ノードを構成することにより、マスター・ノードが過負荷になることを防止できます。 管理ノードを有効にできるのは、{{site.data.keyword.icpfull_notm}} のインストール時のみです。

###	脆弱性アドバイザー・ノード
{: #vcsicp-arch-overview-solution-va-node}

脆弱性アドバイザー・ノードは、脆弱性アドバイザー・サービスの実行に使用されるオプション・ノードです。 脆弱性アドバイザー・サービスはリソース集中型です。 脆弱性アドバイザー・サービスを使用する場合は、専用の VA ノードを指定してください。

高可用性 {{site.data.keyword.icpfull_notm}} インスタンスに必要な VM の仕様は次のとおりです。

表 3. {{site.data.keyword.icpfull_notm}} 仮想マシンの仕様

ノード | 	インスタンス	| IP	| CPU	| RAM (GB)	| ディスク (GB)
:-----|------------:|:----|----:|----------:|----------:|
マスター|	3	| IP (x3) VIP (x1)	| 4	| 64	| 200
管理	|3	| IP (x3)	|8	|64	|500
プロキシー	| 3	| IP (x3) VIP (x1)	|2	|4	|150
脆弱性アドバイザー	|3	| IP (x3)	| 4	| 16	|500
GlusterFS	| 3	| IP (x3)	|8	|16	|150
ワーカー	| 3-6	| IP (x3)	|4-8	|4	|150

CAM が機能するためには、ワーカー・ノードの vCPU とメモリーの構成を大きくする必要があります。

表 4. {{site.data.keyword.icpfull_notm}} 仮想マシンの仕様

ノード | 	インスタンス	| IP	| CPU	| RAM (GB)	| ディスク (GB)
:-----|------------:|:----|----:|----------:|----------:|
ワーカー  |  3 | IP (x3)  |  4-8 |16-20   |  150

## CAM コンポーネント
{: #vcsicp-arch-overview-solution-cam-comp}

{{site.data.keyword.cloud_notm}} Automation Manager (CAM) は、{{site.data.keyword.icpfull_notm}} 上で実行されるマルチクラウド・セルフサービス管理プラットフォームであり、開発者と管理者がビジネス要求に対応できるようにします。

図 3. CAM コンポーネント・リファレンス</br>
![CAM コンポーネント・リファレンス](vcsicp-cam-component-ref.svg)

### CAM プロキシー
{: #vcsicp-arch-overview-solution-cam-proxy}

CAM への nginx プロキシー・アクセスを提供します。

### CAM ユーザー・インターフェース
{: #vcsicp-arch-overview-solution-cam-ui}

ユーザー・インターフェース・コンポーネントは、複数のコンテナーに分かれています。 これらのコンポーネントはクラウド接続ユーザー・インターフェース、テンプレート・ライブラリー・ユーザー・インターフェース、デプロイ済みインスタンスのユーザー・インターフェースに入っています。

### CAM API
{: #vcsicp-arch-overview-solution-cam-api}

CAM API は複数のコンテナーに分かれています。

### Helm
{: #vcsicp-arch-overview-solution-helm}

Helm チャートを Kubernetes クラスターにデプロイするために必要なバイナリーを入れたコンテナー。

### Terraform
{: #vcsicp-arch-overview-solution-terraform}

Terraform リソースを複数のクラウドにデプロイするために必要なバイナリーを入れたコンテナー。

### ログ
{: #vcsicp-arch-overview-solution-logs}

コンテナー・ログのロケーション。

### Mongo データベース
{: #vcsicp-arch-overview-solution-mongo-db}

CAM アプリケーションのコア・データベース。

### Redis
{: #vcsicp-arch-overview-solution-redis}

Redis データベースは、セッションのキャッシュとロックを CAM 内に保管するために使用されます。

### Template Designer
{: #vcsicp-arch-overview-solution-template-designer}

Terraform テンプレートを作成するためのグラフィカル・ユーザー・インターフェース。Terraform モジュールのドラッグ機能を備えています。

### Maria データベース
{: #vcsicp-arch-overview-solution-maria-db}

Template Designer アプリケーションのデータベース。

## 関連リンク
{: #vcsicp-arch-overview-solution-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
