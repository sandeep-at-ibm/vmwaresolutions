---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# WebSphere Application Server の Stock Trader からコンテナーの Stock Trader への変換
{: #vcscontent-stocktrmod}

Stock Trader のモダナイゼーション・ジャーニーの次の段階は、ワークロードを仮想マシン (VM) ではなくコンテナーで実行するように変換することです。

手始めに、Todd と Jane は、Transformation Advisor を実行して Stock Trader のワークロードを分析し、マイグレーションの問題を検出し、変更内容を推奨します。 準備ができたら、Transformation Advisor を使用して、{{site.data.keyword.icpfull_notm}} で実行される Liberty コンテナーの中に Stock Trader をデプロイします。

## IBM Cloud Private の準備
{: #vcscontent-stocktrmod-prep-icp}

Todd はまず、{{site.data.keyword.icpfull_notm}} をインストールする必要があります。 既に VMware on {{site.data.keyword.cloud_notm}} 環境があるので、Todd は、{{site.data.keyword.cloud_notm}} Private Hosted オファリングを使用して、{{site.data.keyword.cloud_notm}} の VMware VM で実行される完全な {{site.data.keyword.icpfull_notm}} インスタンスを作成することにしました。

デフォルトのダッシュボードに装備されている総合的なユーザー・インターフェースで、Kubernetes クラスター、セキュリティー、ストレージ、およびカタログからのデプロイを管理できます。

### ストレージの準備
{: #vcscontent-stocktrmod-prep-storage}

{{site.data.keyword.cloud_notm}} Private Hosted は、すぐに使用できるように GlusterFS が構成されていて、VM 間で専用の GlusterFS ノードとしてファイル・ストレージを利用できるようになっています。 GlusterFS の価値は、動的プロビジョニングが可能である点です。 Todd は、必要に応じて追加の VM を NFS サーバーとしてセットアップできます。

Todd は自分用の NFS サーバーが必要だったので、「toddnfs」という VM を指定し、次の
[手順](https://help.ubuntu.com/community/SettingUpNFSHowTo)を実行しました。

Todd は次のコマンドを実行して新しい NFS サーバーを作成します。

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

次の行を追加します。

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

次に、各 VM で以下のコマンドを実行してすべての {{site.data.keyword.icpfull_notm}} ワーカー VM に NFS をインストールします。

`sudo apt-get update`

`sudo apt-get install nfs-common`

以下のコマンドを実行して、インストールされたバージョンを確認します。

`apt-cache policy nfs-common`

新たに NFS ボリュームが必要になったら、その都度以下のコマンドを実行して新しい NFS ボリュームを作成します。

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### イメージのセキュリティーの準備
{: #vcscontent-stocktrmod-prep-img-sec}

{{site.data.keyword.icpfull_notm}} V3.1 では、イメージ・ポリシーを適用していないと {{site.data.keyword.icpfull_notm}} インスタンスにイメージをプルできないという仕組みにより、セキュリティーが強化されています。 この強化により、IBM イメージが存在する場所、*dockerhub/ibmcom* および Docker Store のイメージ・ポリシーを追加する必要があります。

デフォルトで用意されている ibmcloud-default-cluster-image-policy が、docker.io/ibmcom/\* のすべての IBM イメージをカバーしていますが、Db2 と他の IBM コンテンツが Docker Store にあるので、Docker Store  *docker.io/store/ibmcorp/* 用の別のイメージ・ポリシーが必要です。

また、ポッドへの特定のアクセスを許可するためにポッド・セキュリティー・ポリシーを設定しなければならないコンテンツもあります。 例えば、Db2 は、「デフォルト」以外の名前空間で Db2 を実行するクライアントのためのポリシーが必要です。

詳しくは、[IBM Knowledge
Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html)を参照してください。

## Transformation Advisor と Microclimate のデプロイ
{: #vcscontent-stocktrmod-deploy-tam}

{{site.data.keyword.icpfull_notm}} を稼働させたら、Todd は Transformation Advisor と Microclimate をインストールします。 [カタログ](https://www.ibm.com/cloud/private/developer)を開き、使用可能なすべてのコンテンツを確認します。

Transformation Advisor と Microclimate を探し、Helm チャートをクリックし、用意されている readme ファイルの説明に従ってそれらをインストールします。

### Transformation Advisor の実行
{: #vcscontent-stocktrmod-run-trans-advisor}

Transformation Advisor を実行するために、Jane は WebSphere で Stock Trader を実行している VM にデータ・コレクターを追加し、[Transformation
Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/) ユーザー・インターフェースを開き、結果を表示します。

Jane が Stock Trader をクリックすると、Liberty で各 war ファイルを実行することを推奨するメッセージが表示されます。また、マイグレーションのほとんどは中程度の 1 回のマイグレーションという単純なものであることがわかります。 Jane が「マイグレーションの詳細 (Migration Details)」をクリックすると、マイグレーションの実行に使用できるデプロイメント・ファイルが Transformation Advisor から提供されることが表示されます。 Jane がバイナリー・ファイルをアップロードすると、Transformation Advisor が、Microclimate から提供される API を使用して、Liberty コンテナーをデプロイします。

最終的には、次のどちらかの Stock Trader レイアウトになります。
* 単一 Liberty コンテナー - Jane が Liberty ランタイムを 1 つデプロイし、その単一コンテナーに Stock Trader アプリを追加した場合。
* 複数 Liberty コンテナー - Stock Trader に関する Transformation Advisor の推奨どおりに .war ファイルごとにコンテナー 1 つ。

この変換の段階では、Todd はデータ・ソースを変更しませんでした。 Transformation Advisor が WebSphere Application Server Network Deployment データ・ソース構成を取得し、それを Liberty コンテナーの server.xml に追加します。
{:important}

## 関連リンク
{: #vcscontent-stocktrmod-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
