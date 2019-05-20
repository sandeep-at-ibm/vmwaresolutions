---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# ネットワーク・アクセスおよびフロー
{: #vcsicp-detail-design-network}

## コンテナー・アプリケーション・アクセス – IBM Cloud Private
{: #vcsicp-detail-design-network-container-icp}

外部トラフィックを取得して Kubernetes クラスター・アプリケーションにアクセスするには、主に 3 つの方法があります。

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Private
{: #vcsicp-detail-design-network-nodeport-icp}

NodePort は、初期開発とテストの際にワークロードへの外部アクセス権限を付与するための簡単な方法ですが、実動には推奨されません。 Ingress またはロード・バランサーが、推奨されるパスです。

### LoadBalancer - IBM Cloud Private
{: #vcsicp-detail-design-network-loadbalancer-icp}

{{site.data.keyword.icpfull_notm}} プラットフォームは現在、アプリケーション・ワークロード用に外部ロード・バランサーをサポートしています。

### Ingress - IBM Cloud Private
{: #vcsicp-detail-design-network-ingress-icp}

Ingress は、インバウンド接続がクラスター・サービスに到達できるようにするルールの集合です。 サービスへの外部到達可能 URL の提示、トラフィックのロード・バランシング、SSL の終了、名前ベースの仮想ホスティングの提供などを行うように構成できます。  この機能は、{{site.data.keyword.icpfull_notm}} インフラストラクチャー内のプロキシー・ノードによって実行されます。

## コンテナー・アプリケーション・アクセス – IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-network-container-iks}

外部トラフィックを取得して Kubernetes クラスター・アプリケーションにアクセスするには、主に 3 つの方法があります。

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-network-nodeport-iks}

NodePort は、初期開発とテストの際にワークロードへの外部アクセス権限を付与するための簡単な方法ですが、実動には推奨されません。 Ingress またはロード・バランサーが、推奨されるパスです。

### LoadBalancer - IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-network-loadbalancer-iks}

どの {{site.data.keyword.containerlong_notm}} Cluster にも、パブリックまたはプライベート Application Load Balancer (ALB) がプロビジョンされます。 ALB は、保護された固有のパブリック・エントリー・ポイントまたはプライベート・エントリー・ポイントを使用して、着信要求をアプリケーションにルーティングします。

### Ingress - IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-network-ingress-iks}

Ingress は、インバウンド接続がクラスター・サービスに到達できるようにするルールの集合です。 サービスへの外部到達可能 URL の提示、トラフィックのロード・バランシング、SSL の終了、名前ベースの仮想ホスティングの提供などを行うように構成できます。

## トラフィック・フロー
{: #vcsicp-detail-design-network-traffic-flows}

以下のトラフィック・フローについて説明します。

- インターネット上の外部ユーザーから {{site.data.keyword.icpfull_notm}} のコンテナーでホストされる Web 層まで。
- {{site.data.keyword.icpfull_notm}} のコンテナーでホストされる Web 層から、VMware vCenter Server on {{site.data.keyword.cloud_notm}} の仮想マシン (VM) でホストされるデータベース層まで。
- 企業ネットワーク・アクセスが可能なエンタープライズ・ユーザーから vCenter Server の VM まで。

### インターネット上の外部ユーザーから IBM Cloud Private のコンテナーでホストされる Web 層まで
{: #vcsicp-detail-design-network-external-user}

1. 外部ユーザーが URL を使用して Web 層に要求を出します。
2.	DNS を使用して IP アドレスが判別されます。 この IP アドレスは、vCenter Server インスタンスに割り当てられるポータブル・サブネット上の {{site.data.keyword.cloud_notm}} パブリック・アドレスです。
3.	パブリック・ネットワークは、ESG をホストする vSphere ESXi ホストに、要求を自動的に転送します。
4.	ESG が要求を ALB または Ingress サービスの内部クラスター IP アドレスおよびポート番号に転送します。 ESG と ALB または Ingress サービスが別々の vSphere ESXi ホスト上にある場合、IP パケットは VXLAN フレームにカプセル化されます。 この内部クラスター IP アドレスはクラスター内でのみアクセス可能です。
5.	ワーカー・ノード内で、kube-proxy が要求を ALB または Ingress サービスにルーティングします。
6.	同じワーカー・ノード上にアプリケーションがある場合は、iptables を使用して、要求の転送に使用される内部インターフェースが判別されます。 別のワーカー・ノード上にアプリケーションがある場合は、Calico vRouter が IP-in-IP カプセル化を使用して、該当するワーカー・ノードにルーティングします。 IP-in-IP パケットは、ワーカー・ノードが置かれている vSphere ESXi ホストへの転送のために、VXLAN フレームにカプセル化されます。

### IBM Cloud Private のコンテナーでホストされる Web 層から vCenter Server の VM でホストされるデータベース層まで
{: #vcsicp-detail-design-network-web-tier}

ESG と vRouter 内の経路テーブルにどのようにデータが取り込まれるかは、統合方式によって異なります。 「{{site.data.keyword.icpfull_notm}} と vCenter Server の統合」を参照してください。

1.	{{site.data.keyword.icpfull_notm}} のコンテナーで実行されている Web 層が、同じ vCenter Server インスタンス内の VM 上で実行されているデータベースに要求を出します。
2.	DNS を使用して、要求がデータベースの IP アドレスとして解決されます。
3.	コンテナーが Calico vRouter に要求を送信します。
4.	vRouter の経路テーブルには、vCenter Server インスタンスでホストされている IP アドレス範囲が取り込まれています。
5.	vRouter が要求を転送しますが、SNAT を使用して、ソース IP アドレスをポッドの IP アドレスからワーカー・ノードの IP アドレスに変更します。
6.	vRouter をホストするワーカー・ノードが要求を ESG に送信します。
7.	その後 ESG は DLR に転送します。
8.	DLR が要求を必要な VXLAN 上に置きます。
9.	データベース VM が要求を受け取ります。

### 企業ネットワーク・アクセスが可能なエンタープライズ・ユーザーから vCenter Server の VM まで
{: #vcsicp-detail-design-network-enterprise-user}

1.	企業の社内ネットワークに接続されているエンタープライズ・ユーザーが、vCenter Server でホストされている VM 上のリソースの要求を行います。
2.	DNS を使用して VM の IP アドレスが判別されます。 この IP アドレスは、{{site.data.keyword.cloud_notm}} に拡張されるネットワーク上にあります。
3.	オンプレミス・ルーターが、L2 コンセントレーターをホストしている vSphere ホストにトラフィックを送信します。
4.	L2 コンセントレーターがセキュア・トンネルで要求をカプセル化し、{{site.data.keyword.cloud_notm}} でホストされているリモート L2 コンセントレーターにオンプレミス・ルーター経由で転送します。このとき、デバイスに割り当てられたプライベート・ポータブル・サブネット IP アドレスが使用されます。
5.	オンプレミス経路では、そのルーティング・テーブルを調べて、リモート L2 コンセントレーターの IP アドレスを WAN インターフェースに送信する必要があることを認識し、BCR 経由で  {{site.data.keyword.cloud_notm}} XCR ルーターを介して WAN 上で転送します。
6.	L2 コンセントレーターが要求を受信し、拡張ネットワークをホストする VXLAN 上に置きます。
7.	VM が要求を受け取ります。

## パブリック・アクセス・ネットワーク
{: #vcsicp-detail-design-network-public-access-net}

{{site.data.keyword.icpfull_notm}} と CAM は、Docker イメージ、Helm チャート、Terraform テンプレート、オペレーティング・システムのパッケージ・マネージャーを取得するために、デフォルトでインターネット接続を必要とします。
最新リリースでは、インターネットに直接接続されていない、オフライン・モードでインストールするオプションがあるインストール環境のためのプロキシー・ベースのインストールがサポートされるようになりました。

###	NSX ファイアウォール
{: #vcsicp-detail-design-network-nsx-firewall}

{{site.data.keyword.icpfull_notm}} NSX Edge ファイアウォールには、以下を許可するルールが構成されます。
*	パブリック・アクセスへの VXLAN ネットワーク・アクセスを有効にする。
*	プライベート {{site.data.keyword.cloud_notm}} ネットワーク・アクセスへの VXLAN ネットワーク・アクセスを有効にする。
*	VXLAN ネットワークへのプライベート {{site.data.keyword.cloud_notm}} ネットワーク・アクセスを有効にする。

### NSX NAT
{: #vcsicp-detail-design-network-nsx-nat}

{{site.data.keyword.icpfull_notm}} NSX NAT には、以下の NAT が構成されます。
*	パブリック・アクセスへの VXLAN ネットワーク・アクセスのための SNAT。
*	プライベート {{site.data.keyword.cloud_notm}} ネットワーク・アクセスへの VXLAN ネットワーク・アクセスのための SNAT。
*	{{site.data.keyword.icpfull_notm}} クラスター vIP のための DNAT。

## 関連リンク
{: #vcsicp-detail-design-network-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
