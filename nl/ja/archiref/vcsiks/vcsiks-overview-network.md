---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-01"

---

# ネットワーキング、バックアップ、災害復旧、およびスケーラビリティー
{: #vcsiks-overview-network}

ネットワーキング、バックアップ、災害復旧 (DR)、スケーラビリティーの考慮事項に関する情報を確認してください。

## ネットワーキング
{: #vcsiks-overview-network-networking}

{{site.data.keyword.cloud}} には 2 つのネットワークがあります。 パブリック・ネットワークによりインターネットからサーバーへのアクセスが可能になり、プライベート・ネットワークにより {{site.data.keyword.CloudDataCents_notm}}のすべての高速バックボーンを使用したサーバー間通信が可能になります。

デフォルトでは、{{site.data.keyword.containerlong_notm}} は、パブリック VLAN およびプライベート VLAN にアクセスできるクラスターをセットアップします。
- ワーカー・ノードにパブリック・ネットワーク・インターフェースを与える、各ワーカー・ノードのパブリック IP アドレス。
  - すべてのワーカー・ノードに対して、すべてのアウトバウンド・ネットワーク・トラフィックが許可されます。
  - 数個のポートを除いて、インバウンド・ネットワーク・トラフィックがブロックされます。 これらのポートは、IBM がネットワーク・トラフィックをモニターし、Kubernetes マスターのセキュリティー更新を自動的にインストールできるように開かれています。
- ワーカー・ノードにプライベート・ネットワーク・インターフェースを付与する、各ワーカー・ノードのプライベート IP アドレス
- すべてのワーカー・ノードとマスター・ノードの間の自動的で安全な OpenVPN 接続

図 1. vCenter Server と {{site.data.keyword.containerlong_notm}} のネットワーク
![vCenter Server と {{site.data.keyword.containerlong_notm}} のネットワーク図](vcsiks-networking.svg)

### IBM Cloud Kubernetes Service と vCenter Server の統合
{: #vcsiks-overview-network-iks-vcs-integration}

現在は、次のシナリオで、{{site.data.keyword.containerlong_notm}} および VMware vCenter Server on {{site.data.keyword.cloud_notm}} のネットワークを統合できます。
- **VRA ルーティング** - このシナリオでは、vCenter Server インスタンスと同じ VLAN に {{site.data.keyword.containerlong_notm}} ワーカー・ノードをデプロイする必要があります。 これにより、ESG が VRA と BGP ピアになり、vCenter Server と {{site.data.keyword.containerlong_notm}} を結ぶオーバーレイからアンダーレイ・ネットワークへのルーティングが可能になります。 これらの要求を BCR/VRA に戻して正しくルーティングするためには、{{site.data.keyword.containerlong_notm}} ワーカー・ノードに各 VXLAN ネットワーク用の静的ルートが必要です。
- **strongSwan VPN** – このシナリオでは、標準的な {{site.data.keyword.containerlong_notm}} から組織への接続ソリューションを使用します。 strongSwan コンテナーは、リモート・ゲートウェイへの IPSec トンネルを介してパケットをリモート・ネットワークに転送する VPN ゲートウェイをクラスターに提供します。 このリモート・ゲートウェイは vCenter Server インスタンス上の ESG です。 これらのゲートウェイには、すべてのクラスターとサービスの IP 範囲を StrongSwan コンテナーに送信し、すべての vCenter Server BYOIP アドレスを ESG に送信するようにルートが構成されます。 ゲートウェイのターゲット IP アドレスは、strongSwan コンテナーに割り当てられたロード・バランサー・サービスのプライベート・ポータブル IP アドレスと、ESG のプライベート・ポータブル IP アドレスです。

#### IBM Cloud Kubernetes Service ネットワーキング VLAN
{: #vcsiks-overview-network-iks-vlans}

パブリック VLAN サブネットに当てはまる情報を以下にまとめます。
- 1 次パブリック・サブネットでは、クラスター作成時にワーカー・ノードに割り当てられるパブリック IP アドレスを決定します。 同じ VLAN に参加している複数のクラスターでは、1 つの 1 次パブリック・サブネットを共有することができます。
- ポータブル・パブリック・サブネットは 1 つのクラスターだけにバインドされ、そのクラスターに 8 つのパブリック IP アドレスを提供します。 3 つの IP がネットワーク機能のために予約されています。 1 つの IP はデフォルトのパブリック Ingress ALB に使用され、4 つの IP がパブリック・ロード・バランサー・ネットワーク・サービスを作成するために使用されます。
- ポータブル・パブリック IP は固定された永続的な IP アドレスであり、このアドレスを使用して、インターネットを介してロード・バランサー・サービスにアクセスします。

プライベート VLAN サブネットに当てはまる情報を以下にまとめます。
- 1 次プライベート・サブネットでは、クラスター作成時にワーカー・ノードに割り当てられるプライベート IP アドレスを決定します。 同じ VLAN に参加している複数のクラスターでは、1 つの 1 次プライベート・サブネットを共有することができます。
- ポータブル・プライベート・サブネットは 1 つのクラスターだけにバインドされ、そのクラスターに 8 つのプライベート IP アドレスを提供します。 3 つの IP がネットワーク機能のために予約されています。 1 つの IP はデフォルトのプライベート Ingress ALB に使用され、4 つの IP がプライベート・ロード・バランサー・ネットワーク・サービスを作成するために使用されます。
- ポータブル・プライベート IP は固定された永続的な IP アドレスであり、このアドレスを使用して、インターネットを介してロード・バランサー・サービスにアクセスします。

#### Calico ネットワーク・プラグイン
{: #vcsiks-overview-network-calico}

Kubernetes クラスターはそれぞれ、Calico と呼ばれるネットワーク・プラグインを使用してセットアップされます。

{{site.data.keyword.containerlong_notm}} の各ワーカー・ノードのパブリック・ネットワーク・インターフェースを保護するために、デフォルトのネットワーク・ポリシーがセットアップされます。 固有のセキュリティー要件がある場合、または VLAN スパンニング または Virtual Routing and Forwarding (VRF) を有効にした複数ゾーン・クラスターがある場合は、Calico および Kubernetes を使用してクラスターのネットワーク・ポリシーを作成できます。 Kubernetes ネットワーク・ポリシーを使用して、クラスター内のポッドとの間で許可またはブロックするネットワーク・トラフィックを指定できます。

LoadBalancer サービスへのインバウンド (ingress) トラフィックのブロックなど、より高度なネットワーク・ポリシーを設定するには、Calico ネットワーク・ポリシーを使用します。

Kubernetes ネットワーク・ポリシーでは、ポッドが他のポッドやパブリック・ネットワーク・サービス・エンドポイントと通信する方法を指定します。トラフィックは、ポッドおよび名前空間ラベルに基づいてフィルタリングすることもできます。 Kubernetes ネットワーク・ポリシーは、kubectl コマンドまたは Kubernetes API を使用して適用されます。 これらのポリシーは、適用されると自動的に Calico ネットワーク・ポリシーに変換され、Calico によってこれらのポリシーが実施されます。

Kubernetes に関する Calico ネットワーク・ポリシーは Kubernetes ネットワーク・ポリシーのスーパーセットであり、calicoctl コマンドを使用して適用します。

Calico ポリシーは、以下の機能を追加します。
- Kubernetes ポッドのソースまたは宛先 IP アドレスや CIDR に関係なく、特定のネットワーク・インターフェース上のネットワーク・トラフィックを許可またはブロックします。
- 複数の名前空間にまたがるポッドのネットワーク・トラフィックを許可またはブロックします。
- LoadBalancer または NodePort Kubernetes サービスへのインバウンド (ingress) トラフィックをブロックします。

Calico は、Kubernetes ワーカー・ノードで Linux iptables 規則をセットアップすることにより、Calico ポリシーに自動的に変換される Kubernetes ネットワーク・ポリシーを含め、これらのポリシーを実施します。 iptables 規則はワーカー・ノードのファイアウォールとして機能し、ネットワーク・トラフィックがターゲット・リソースに転送されるために満たさなければならない特性を定義します。

### トラフィック・フロー
{: #vcsiks-overview-network-traffic-flows}

#### インターネット上の外部ユーザーから IBM Cloud Kubernetes Service のコンテナーでホストされる Web 層まで
{: #vcsiks-overview-network-web-tier-iks}

1. 外部ユーザーが URL を使用して Web 層に要求を出します。
2. DNS を使用して IP アドレスが判別されます。 この IP アドレスは、ALB または Ingress サービスに割り当てられたポータブル・サブネット上の {{site.data.keyword.cloud_notm}} パブリック・アドレスです。
3. パブリック・ネットワークは、 ALB または Ingres サービスをホストするワーカー・ノードに要求を自動的に転送します。
4. ワーカー・ノードが要求を ALB または Ingress サービスの内部クラスター IP アドレスおよびポート番号に転送します。 この内部クラスター IP アドレスはクラスター内でのみアクセス可能です。
5. ワーカー・ノード内で、kube-proxy が要求を ALB または Ingress サービスにルーティングします。
6. 同じワーカー・ノード上にアプリケーションがある場合は、iptables を使用して、要求の転送に使用される内部インターフェースが判別されます。 別のワーカー・ノード上にアプリケーションがある場合は、Calico vRouter が IP-in-IP カプセル化を使用して該当するワーカー・ノードにルーティングしますが、これは、そのワーカー・ノードが別のサブネット上にある場合に限られます。

#### IBM Cloud Kubernetes Service のコンテナーでホストされる Web 層から vCenter Server の仮想マシンでホストされるデータベース層まで
{: #vcsiks-overview-network-web-tier-vm}

外部データベース仮想マシン (VM) の詳細を含むエンドポイント・リソースが作成されます。例えば mysql データベース VM の NAT の IP アドレスやポート番号が含まれています。

- kind: Endpoints
- apiVersion: v1
- metadata:
  - name: mysqldb
- subsets:
  - addresses:
      - ip: 10.x.x.x
  - ports:
      - port: 3306

エンドポイント・リソースに複数のアドレスをリストすると、Kubernetes がそれらのアドレスの間でラウンドロビンを行います。  

サービス・リソースは、サービスの kube-dns で IP および DNS 名を作成するために使用されます。

- kind: Service
- apiVersion: v1
- metadata:
  - name: mysqldb
- labels:
  - name: mysqldb
- spec:
  - ports:
    - protocol: TCP
    - port: 3306

#### フロー
{: #vcsiks-overview-network-flow}

1. {{site.data.keyword.containerlong_notm}} のコンテナーの中で実行されている Web 層が、mysqldb を呼び出して、vCenter Server インスタンス内の VM 上で実行されているデータベースに要求を出します。 Kubernetes がその名前を IP アドレスに解決し、この要求をデータベース・サーバーの NAT 対象 IP の宛先 IP アドレス (10.x/26) とワーカー・ノードのソース IP (10.x/26) を使用してクラスターから送信します。
2. 宛先 IP アドレスがワーカー・ノードと同じサブネット上にないので、{{site.data.keyword.cloud_notm}} BCR に転送されます。
3. BCR が要求をルーティングし、customer-nsx-edge が接続されている**プライベート A** VLAN、カスタマー・ワークロード・サブネットに要求を配置します。

この NSX Edge には以下のものがあります。
- この接続を許可するファイアウォール・ルール。
- 宛先 IP アドレスを、10.x アドレスからデータベース・サーバーで使用される 192.168 アドレスに変更する DNAT ルール。
4. その後 ESG は DLR に転送します。
5. DLR が要求を必要な VXLAN 上に置きます。
6. データベース VM が要求を受け取ります。

## バックアップおよび DR
{: #vcsiks-overview-network-backup-dr}

### vCenter Server のバックアップ
{: #vcsiks-overview-network-vcs-backup}

{{site.data.keyword.vmwaresolutions_short}} の一部として、VMware クラスター外部の {{site.data.keyword.cloud_notm}} エンデュランス・ストレージを使用する Veeam バックアップ・ソフトウェアが {{site.data.keyword.cloud_notm}} 仮想サーバー・インスタンス (VSI) にオプションでデプロイされます。 このソフトウェアの目的は、このソリューションの管理コンポーネントをバックアップすることです。

### NSX のバックアップ
{: #vcsiks-overview-network-nsx-backup}

障害が発生した場合にシステムをその動作状態にリストアするためには、すべての NSX コンポーネントを適切にバックアップしておくことが不可欠です。 NSX VM をバックアップするだけでは不十分です。 適切なバックアップを行うためには、NSX Manager 内の NSX 機能を使用する必要があります。 このバックアップでは、NSX バックアップ・データのリポジトリーとして FTP サーバーまたは SFTP サーバーを指定する必要があります。 NSX Manager のバックアップの対象となるのはすべての NSX 構成です。これには、コントローラー、論理スイッチング・エンティティー、論理ルーティング・エンティティー、セキュリティー、ファイアウォール・ルール、および NSX Manager UI または API 内で構成するその他すべての項目が含まれます。 vCenter データベースおよびその関連エレメント (仮想スイッチなど) を別途バックアップする必要があります。 NSX 構成は vCenter バックアップと共にバックアップする必要があります。

### IBM Cloud Kubernetes Service のバックアップおよび DR
{: #vcsiks-overview-network-backup-dr-iks}

etcd データベースのバックアップは、管理対象サービスの一部としてお客様に提供されます。アプリケーション・データはすべて、自身でバックアップする必要があります。

## スケーラビリティー
{: #vcsiks-overview-network-scalability}

### vCenter Server のスケーラビリティー
{: #vcsiks-overview-network-vcs-scalability}

初期ホストをデプロイした後に、ユーザーは {{site.data.keyword.vmwaresolutions_short}} ポータルで計算容量をスケールアウトできます。 環境のこのスケールアウトは、以下の 3 つの方法のいずれかを使用します。
- 別々の vCenter Server が管理する新規サイトを追加する。
- 新規クラスターを追加する。
- 既存クラスターに新規ホストを追加する。

#### マルチサイト・デプロイメント
{: #vcsiks-overview-network-multi-site}

VMware on {{site.data.keyword.cloud_notm}} は、IBM Cloud の世界規模のデータ・センターおよび統合されたネットワーク・バックボーンを使用して、地域をまたがるさまざまなユース・ケースをデプロイし、インフラストラクチャーを最初から構築するよりもずっと短時間で機能できるようにします。

#### 新規クラスターによるスケールアウト
{: #vcsiks-overview-network-scale-out-new-cluster}

ユーザーはコンソールで新規クラスターを作成し、ホストを注文することで計算容量をスケールアウトすることもできます。新規ホストは、新規クラスターに自動的に追加されます。 この方法の場合は、追加のクラスターが環境内に作成されます。ユーザーは、管理ワークロードをアプリケーション・ワークロードから物理的および論理的に分離したり、その他の特性 (例えば、Microsoft SQL データベース・クラスターなど) に基づいてワークロードを分離したり、可用性の高いトポロジーでアプリケーションをデプロイしたりできるようになります。

#### 既存のクラスターのスケールアウト
{: #vcsiks-overview-network-scale-out-existing-cluster}

ユーザーは、コンソール内からホストを注文することによって既存のクラスターをスケールアウトできます。新しいホストは、当該クラスターに自動的に追加されます。
場合によっては、ユーザーはその予約要件に基づいて、クラスターの HA 予約ポリシーを調整する必要があります。

### IBM Cloud Kubernetes Service の拡張
{: #vcsiks-overview-network-iks-expansion}

ユーザーは、{{site.data.keyword.cloud_notm}} Portal を介して {{site.data.keyword.containerlong_notm}} 環境をプロビジョンし、コンテナー環境を拡張または使用することができます。 {{site.data.keyword.containerlong_notm}} へのアプリケーションのデプロイメントは、以下の方法で行うことができます。
  - {{site.data.keyword.containerlong_notm}} 接続およびサービスを CAM で開発して、{{site.data.keyword.icpfull_notm}} カタログに公開する。
  - {{site.data.keyword.containerlong_notm}} インスタンスを管理するための Multi-Cloud Manager の今後の機能拡張。
  - Helm コマンド・ライン・インターフェース。
  - 高可用性を向上させるためのマルチゾーン・クラスターの使用。

『[クラスターおよびワーカー・ノードのセットアップの計画](/docs/containers?topic=containers-plan_clusters#plan_clusters)』で、要件を満たすソリューションを設計するためのオプションとプロセスについて説明しています。

## セキュリティーとコンプライアンス
{: #vcsiks-overview-network-sec-compliance}

真のコンプライアンスを促進するために、{{site.data.keyword.cloud_notm}} はお客様に代わって業界の厳しいガイドラインを満たすための作業を既に施しています。 [Compliance on the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/compliance) では、セキュリティーおよびプライバシーのための具体的なコンプライアンス認定、グローバル規制、調整、およびフレームワークについて詳しく説明しています。 [{{site.data.keyword.containerlong_notm}} のセキュリティー](/docs/containers?topic=containers-security#security)では、{{site.data.keyword.containerlong_notm}} のセキュリティー機能について詳しく説明しています。

## 関連リンク
{: #vcsiks-overview-network-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
