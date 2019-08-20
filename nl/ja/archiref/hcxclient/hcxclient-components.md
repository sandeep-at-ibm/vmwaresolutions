---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# HCX のコンポーネントと用語集
{: #hcxclient-components}

HCX は、1 つのクラウド・サイド (ターゲットまたは VCD 環境) と 1 つ以上のクライアント (ソース) で構成されます。 HCX のインスタンスを各 vCenter に 1 つずつデプロイしてください。HCX をデプロイする vCenter がクライアント・サイドまたはクラウド・サイドの同じ SSO ドメインにリンクされている場合でも、そうする必要があります。 HCX では、1 対 1、1 対多、多対 1、多対多の構成がサポートされています。

## ターゲット・サイドとクライアント・サイド
{: #hcxclient-components-cloud-client-side}

HCX には、クラウド・サイド (ターゲットまたは VCD 環境) とクライアント・サイド (ソース) という概念があります。

- ターゲット・サイド - HCX Cloud Manager は事前にデプロイされていて、サービス・メッシュの作成に使用できるように、ネットワーク・プロファイルとコンピュート・プロファイルを使用して構成されています。  
- クライアント・サイド - インストールと運用の前提条件を満たした vSphere インスタンス。 HCX のクライアント・サイドは、
vCenter Web Client ユーザー・インターフェース (UI) スナップインによってクラウド・サイドのスレーブ・インスタンスを制御するマスターになります。

## HCX Manager
{: #hcxclient-components-hcx-manager}

- クラウド・サイド - HCX Cloud Manager は、クライアント・サイドの登録、管理、制御の着信トラフィックを listen するように構成されます。
- クライアント・サイド - HCX Enterprise Manager は、HCX の管理と運用のための UI 機能を提供するクライアント・サイド固有の OVA イメージ・ファイルです。 クライアント・サイドの HCX Manager は、
クラウド・サイドの HCX Manager への登録と、
クライアント・サイドとクラウド・サイドの間に配置する管理プレーンの作成を担当します。 加えて、クライアント・サイドにサービス・メッシュをデプロイする操作と、その同じ操作を実行する命令をクラウド・サイドに送信する操作も担当します。

## サービス・メッシュ・コンポーネント
{: #hcxclient-components-fleet}

HCX サービス・メッシュ・コンポーネントは、データの作成と、クライアント・サイドとクラウド・サイドの間に配置するコントロール・プレーンの作成を担当します。 ミラー・ペア構成の仮想マシン (VM) としてデプロイするサービス・メッシュには、以下のコンポーネントがあります。

- 相互接続アプライアンス (HCX-IX) - 相互接続アプライアンスは、vMotion とレプリケーション (一括マイグレーション) のトラフィックをサポートする暗号化トンネルを作成します。
- WAN オプティマイザー・アプライアンス (HCX-WAN) - HCX には、オプションとしてデプロイできる Silver Peak™ WAN 最適化アプライアンスが組み込まれています。 デプロイする場合は、VM アプライアンスとしてのデプロイになります。 デプロイすると、
CGW トンネルのトラフィックが WAN オプティマイザーをトラバースするようにリダイレクトされます。 WAN オプティマイザーを使用すると、WAN のトラフィックが大幅に (通常は 3:1 から 6:1 に) 減少し、
接続の信頼性が高まるので、CGW と一緒に常に WAN オプティマイザーをデプロイすることをお勧めします。 WAN オプティマイザーをデプロイすると、
VM のマイグレーション・トラフィックによって消費される WAN 帯域幅が限定されるという利点もあります。 WAN オプティマイザーの管理インターフェースは、デフォルトでは構成されません。
- ネットワーク拡張 (HCX-NE) - レイヤー 2 ネットワーク拡張機能を提供し、オンプレミス・ロケーションと vSphere 環境の間のマイグレーションを可能にします。VM に IP アドレスを再割り当てする必要があります。
- プロキシー ESXi ホスト - HCX-IX をクラウド・サイドの HCX サイトに接続するように構成すると、
プロキシー ESXi ホストがクラスター外部にある vCenter に
表示されます。 この ESXi ホストの管理用と vMotion 用の IP アドレスは、対応する HCX-IX アプライアンスのアドレスと同じです。 したがって、
クライアント・サイドとクラウド・サイドの両方の vSphere 環境が 1 つのローカル vMotion を実行しているような感覚で機能します。 この方式には以下のような利点があります。
  - 両サイドの管理用の IP 範囲がオーバーラップしても機能が失われません。
  - クラウド・サイドの vSphere からはクライアント・サイドを表示できないので、よりセキュアな環境になります。

## HCX ユーザー・ポータル
{: #hcxclient-components-hcx-user-portals}

- クライアント Web UI – HCX クライアント Web ポータルが HCX の主な UI になります。 クライアント・サイドの HCX Manager をインストールすると、この UI が vCenter Web UI のスナップインとして表示されます。 リモート・クラウドの HCX の登録 (サイト・ペアリング)、フリート・コンポーネントのデプロイメント、ネットワーク・ストレッチ、クラウドへの VM マイグレーション、クラウドからの VM マイグレーションを制御できます。
- クラウド・サイド UI – クラウド・サイド HCX UI には、HCX クライアント登録のために付与される公開の登録 URL からアクセスできます。 デフォルトでは、クラウド・サイドの vCenter Admin 資格情報 (` administrator@vsphere.local`) が使用されます。 通常は、インストール環境のアップグレードやネットワーク構成の変更のためにこの機能を使用します。

## 関連リンク
{: #hcxclient-components-related}

* [VMware HCX on IBM Cloud のポート・アクセスの要件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [インストール環境の準備](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX クライアントのデプロイメント](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX オンプレミスのサービス・メッシュ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud のマイグレーション](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [パラメーターとコンポーネントのモニター](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX のトラブルシューティング](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
