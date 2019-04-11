---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial for vCenter Server on IBM Cloud のための HCX on IBM Cloud アーキテクチャー設計
{: #vc_trial_hcx_arch}

VMware HCX on {{site.data.keyword.cloud}} with Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}} は、{{site.data.keyword.vmwaresolutions_short}} インスタンスとオンプレミスの VMware 仮想化データ・センターをシームレスに接続する新しいオファリングです。 vCenter Server では最小 3 ノードが推奨されていますが、この単一ノードによるトライアルを利用すれば、安価にハイブリッド・クラウドの実装を試して利点を体験することができます。

{{site.data.keyword.vmwaresolutions_short}} では、{{site.data.keyword.cloud_notm}} に vCenter Server 構成を完全に自動で迅速にデプロイできます。 Single-node Trial for vCenter Server オファリングは、オンプレミスのインフラストラクチャーを補完し、既存のワークロードと将来のワークロードを変換なしで {{site.data.keyword.cloud_notm}} で実行できるようにします。 このオファリングでは、オンプレミスで使用されるのと同じツール、スキル、プロセスが使用されます。 {{site.data.keyword.vmwaresolutions_short}} オファリングについて詳しくは、[IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture) を参照してください。

HCX on {{site.data.keyword.cloud_notm}} サービスは、シームレスにネットワークを拡張し、ワークロードを双方向にマイグレーションできるようにして、vCenter Server インスタンスとオンプレミスの既存の仮想化データ・センターを融合させます。 {{site.data.keyword.cloud_notm}} VMware ターゲット・サイトに仮想マシン (VM) としてデプロイされる HCX on IBM Cloud コンポーネントが、ピアであるオンプレミスのソース・サイトにインストールされる HCX on {{site.data.keyword.cloud_notm}} コンポーネントとの接続の確立を可能にします。

図 1. HCX のアーキテクチャー

![HCX のアーキテクチャー](hcx-architecture.svg "HCX のアーキテクチャー")

以下の情報は、HCX on {{site.data.keyword.cloud_notm}} サービス実装の設計を示しています。 ターゲット側の {{site.data.keyword.vmwaresolutions_short}} インスタンスのコンポーネントと、オンプレミスに存在するソースにデプロイされるコンポーネントの両方が含まれています。

## HCX on IBM Cloud の概要
{: #vc_trial_hcx_arch-ovw}

{{site.data.keyword.cloud_notm}} は、オンプレミスの vSphere vCenter ネットワークを {{site.data.keyword.vmwaresolutions_short}} デプロイメントにシームレスに統合します。 ハイブリッド・ネットワーキングによってオンプレミスの vSphere vCenter ネットワークが {{site.data.keyword.cloud_notm}} まで拡張されるので、双方向の VM モビリティーがサポートされます。

HCX は、ソースと宛先で暗号化/復号のプロセスを取ることで、セキュリティーを一貫して確保し、VM マイグレーションやネットワーク拡張などのハイブリッド・ワークフローの受け入れを許可します。 このオファリングは、拡張ネットワークのパフォーマンスを高めるために、最適化されたソフトウェア定義の広域ネットワーク (WAN) を構築し、ローカル・エリア・ネットワーク (LAN) の速度に迫るパフォーマンスを実現します。 また、双方向ワークロードおよび {{site.data.keyword.cloud_notm}} への VMware NSX セキュリティー・ポリシーのマイグレーションを可能にします。HCX は、vSphere vCenter と統合され、vSphere Web Client から管理されます。

### レイヤー 2 のネットワーク拡張
{: #vc_trial_hcx_arch-layer-2-extension}

HCX を使用すると、オンプレミスの既存の vSphere 資産のネットワークを、オンプレミスの vCenter から、VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} または vCenter Server を実行する {{site.data.keyword.CloudDataCent_notm}} まで安全に拡張できます。 この機能は、次のアイテムによって実現されています。

* HCX では、レイヤー 2 コンセントレーター (L2C) というアプライアンスが提供されます。
* 拡張されたネットワークは、vCenter Server にデプロイされた {{site.data.keyword.cloud_notm}} の NSX Edge アプライアンスに接続されます。
* オンプレミスの vCenter のスケーラビリティーとスループットの向上のために、標準のレイヤー 2 コンセントレーターを複数台デプロイできます。
* VM の IP アドレスと MAC アドレスを保持したまま、拡張されたレイヤー 2 を使用してクラウド・ゲートウェイ経由で VM をマイグレーションできます。

### 仮想マシンのマイグレーション
{: #vc_trial_hcx_arch-vm-mig}

HCX には、以下の 3 つの VM 移行方式が用意されています。

* 最小ダウン時間マイグレーション
* vSphere vMotion マイグレーション
* コールド・マイグレーション

#### 最小ダウン時間マイグレーション
{: #vc_trial_hcx_arch-low-downtime-mig}

最小ダウン時間マイグレーションは、vSphere Replication を使用するマイグレーションです。vSphere Replication は、VMware ESX または VMware ESXi ハイパーバイザーに実装されている分散テクノロジーです。 オンプレミスの HCX デプロイメントで、稼働中の VM のレプリカを {{site.data.keyword.cloud_notm}} に作成し、切り替えを実行して、ソース VM を電源オフに、マイグレーションした VM を電源オンにします。 このマイグレーション・パスは、必ずクラウド・ゲートウェイを経由します。 転送には、インターネット、レイヤー 2 拡張ネットワーク、または専用接続回線を使用できます。 VM のマイグレーションは双方向に何度でも実行できます。

#### vSphere vMotion マイグレーション
{: #vc_trial_hcx_arch-vmotion-mig}

{{site.data.keyword.cloud_notm}} まで拡張されたネットワークで vSphere vMotion マイグレーションを使用することで、稼働中の VM を転送できます。 vMotion マイグレーションは、ゼロ・ダウン時間マイグレーションまたはクラウド間 vMotion とも呼ばれます。

#### コールド・マイグレーション
{: #vc_trial_hcx_arch-cold-mig}

コールド・マイグレーションでは、レイヤー 2 コンセントレーターで構築された拡張ネットワークを介して、電源オフの状態の VM を {{site.data.keyword.cloud_notm}} に転送できます。

#### 共通のマイグレーション機能
{: #vc_trial_hcx_arch-common-feat}

3 タイプのすべてのマイグレーションで、以下の機能を使用できます。

* マイグレーションのスループットと速度を向上させるソフトウェア定義 WAN の最適化機能。
* 指定した時刻にマイグレーションするようにスケジュールを設定する。
* ホスト名または VM 名、あるいはその両方を保持する。

### ネットワーキング
{: #vc_trial_hcx_arch-network}

クラウド・ゲートウェイおよびレイヤー 2 コンセントレーターには、以下のネットワーキング機能が組み込まれています。

#### インテリジェント・フロー・ルーティング
{: #vc_trial_hcx_arch-intel-flow}

インテリジェント・フロー・ルーティングは、インターネット・パスに基づいて最適な接続を自動的に選択し、可能な限り速くワークロードを転送するために接続全体を使用して効率的に大量のデータを流します。 バックアップやレプリケーションなどの大量のフローのために CPU 競合が発生した場合は、少量のフローを比較的にビジーでない CPU にルーティングして、双方向トラフィックのパフォーマンスを高めます。

#### 近接ルーティング
{: #vc_trial_hcx_arch-prox-routing}

近接ルーティングは、拡張されたルーティング・ネットワークに接続された VM 間の転送が、オンプレミスとクラウドで対称的に行われるようにします。 この機能を使用するためには、オンプレミスとクラウドの間に動的ルーティングを構成する高度なネットワーク・サービスが必要です。

ユーザーがネットワークをクラウドまで拡張すると、レイヤー 2 接続が {{site.data.keyword.cloud_notm}} ネットワークまで拡張されます。 しかし、ルート最適化がない場合、レイヤー 3 通信要求は、ルーティングを受けるためにオンプレミスのネットワーク起点に戻されます。 このように往復することを「トロンボーン現象」または「ヘアピン現象」と呼びます。 ソース VM と宛先 VM が両方ともクラウドに存在する場合でも、ネットワーク起点とクラウドの間をパケットが往復するので、トロンボーン現象は非効率的です。

接続の両側を認識しなければならないステートフル・ファイアウォールなどのインライン装置が転送パスに含まれていると、通信できない可能性があります。 クラウドを出る送信パスが拡張レイヤー 2 ネットワークと組織のルーティング・ネットワークのどちらも経由できる場合は、ルート最適化がないと VM 通信は失敗します。 オンプレミスのネットワークは、拡張されたネットワークに「近道」があることを認識しません。 この問題は、非対称ルーティングと呼ばれます。 この問題の解決策は、オンプレミスのネットワークが {{site.data.keyword.cloud_notm}} のルートを学習できるように近接ルーティングを有効にすることです。

クラウド・ゲートウェイは、クラウド内の VM のインベントリーを保守します。 また、次のような VM の状態を認識します。

* vMotion で {{site.data.keyword.cloud_notm}} に転送された (ゼロ・ダウン時間マイグレーション)
* ホスト・ベースのレプリケーションを使用してクラウドにマイグレーションされた (最小ダウン時間マイグレーション)
* (拡張ネットワークを使用して) クラウドに作成された

#### セキュリティー
{: #vc_trial_hcx_arch-sec}

クラウド・ゲートウェイは、Suite B 準拠の AES-GCM および IKEv2、AES-NI オフロード、フロー・ベース・アドミッション制御を備えています。 また、HCX は、ソースと宛先で暗号化/復号のプロセスを取ることで、セキュリティーを一貫して確保し、VM マイグレーションやネットワーク拡張などのハイブリッド・ワークフローの受け入れを許可します。 オンプレミスの VM に割り当てられていた定義済みのセキュリティー・ポリシーを VM と一緒に {{site.data.keyword.cloud_notm}} にマイグレーションできます。

ポリシーのマイグレーションには以下の条件が必要です。

* オンプレミスのデータ・センターが NSX V6.2.2 以上を実行している。
* vSphere では、セキュリティー・ポリシーは、さまざまなルールを定義できる単一の NSX セクションである。
* ポリシーに参加する IP アドレスまたは MAC アドレスのセットの名前を指定できる。
* MAC セットまたは IP セットの名前は 218 文字を超えてはいけない。
* サポートされるルールでは、ソースまたは宛先としてレイヤー 3 の IP アドレスまたは IP セット、またはレイヤー 2 の MAC アドレスまたは MAC セットを指定している。

### HCX コンポーネント
{: #vc_trial_hcx_arch-hcx-comp}

HCX on {{site.data.keyword.cloud_notm}} サービスでは、4 つの仮想アプライアンスがデプロイされます。これらは、オンプレミス・データ・センターと IBM Cloud の両方のターゲットにインストールされ、構成されます。 ここでは、この 4 つの必要な仮想アプライアンスのそれぞれについて説明します。 実装設計によっては、オプションのエッジ・デバイスが必要になる場合があります。

#### HCX Manager
{: #vc_trial_hcx_arch-hcx-manager}

HCX Manager 仮想アプライアンスは、オンプレミスの vCenter に対する拡張機能です。 このアプライアンスは VM としてデプロイされ、ファイル構造には他のハイブリッド・サービス仮想アプライアンスが含まれています。 HCX Manager が、オンプレミスと {{site.data.keyword.cloud_notm}} の両方で、クラウド・ゲートウェイ、レイヤー 2 コンセントレーター、WAN 最適化のための仮想アプライアンスのデプロイメントと構成をすべて管理します。

#### ハイブリッド・クラウド・ゲートウェイ
{: #vc_trial_hcx_arch-hcg}

ハイブリッド・クラウド・ゲートウェイ (CGW) は、オンプレミスの vSphere 資産と {{site.data.keyword.cloud_notm}} の間にセキュアなチャネルを維持します。 HCX は強い暗号化を使用して {{site.data.keyword.cloud_notm}} へのサイト間接続をブートストラップします。 vSphere と {{site.data.keyword.cloud_notm}} の間のセキュア・チャネルによって、「ミドルマイル」というネットワーキングのセキュリティー上の問題を防止します。 双方向マイグレーションを行うために、クラウド・ゲートウェイには vSphere Replication テクノロジーも組み込まれています。

#### WAN 最適化
{: #vc_trial_hcx_arch-wan-opt}

WAN 最適化アプライアンスは、WAN の調整を行って遅延の影響を軽減するコンポーネントです。 また、これにはパケット・ロスのシナリオを回避するための Forward Error Correction と、冗長トラフィック・パターンの重複排除も組み込まれています。 これらによって帯域幅の使用量が減るので、使用可能なネットワーク容量を最大限に利用して {{site.data.keyword.cloud_notm}} との間のデータ転送を高速化できます。

VM のマイグレーションでオンプレミス vSphere と {{site.data.keyword.cloud_notm}} の間に類い希なるモビリティーを実現できるのは、クラウド・ゲートウェイと WAN 最適化アプライアンスの両方によるものです。 また、データ・パスがクラウド・ゲートウェイを経由する場合は、レイヤー 2 拡張にも WAN 最適化の効果があります。
{:important}

#### レイヤー 2 コンセントレーター
{: #vc_trial_hcx_arch-layer-2-conc}

レイヤー 2 コンセントレーター (L2C) アプライアンスは、オンプレミス vSphere データ・センターから {{site.data.keyword.cloud_notm}} へのレイヤー 2 ネットワークの拡張を可能にします。

レイヤー 2 コンセントレーターには、以下のインターフェースがあります。

* **内部トランク・インターフェース** このインターフェースでは、{{site.data.keyword.cloud_notm}} 側の拡張ネットワークとの対応付けを行う変換ブリッジ・マッピングを使用して、オンプレミスで拡張ネットワークの VM トラフィックを処理します。
* **アップリンク・インターフェース** HCX はこのインターフェースを使用して、カプセル化したオーバーレイ・トラフィックを {{site.data.keyword.cloud_notm}} との間で送信します。 アプリケーション・データはアップリンク・インターフェースを通って転送されます。

### デプロイメント・アーキテクチャー
{: #vc_trial_hcx_arch-deployment}

HCX on {{site.data.keyword.cloud_notm}} のデプロイメントについては、[VMware HCX on {{site.data.keyword.cloud_notm}} Deployment and Operations](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf) を参照してください。
