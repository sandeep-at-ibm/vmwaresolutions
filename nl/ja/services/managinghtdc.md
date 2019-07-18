---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HTDC WebGUI, HTDC console, enable internet HTDC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl on IBM Cloud の管理
{: #managinghtdc}

HyTrust DataControl on {{site.data.keyword.cloud}} サービス (HTDC) を管理するには、{{site.data.keyword.vmwaresolutions_short}} コンソールから HTDC WebGUI にアクセスするか、vSphere Web Client から HTDC コンソールにアクセスします。

## IBM Cloud for VMware Solutions コンソールから HyTrust DataControl WebGUI へのアクセス
{: #managinghtdc-accessing-webgui}

プライマリーまたはセカンダリーの HTDC アプライアンスの WebGUI にログインするには、HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスの詳細ページに記されている WebGUI の資格情報を使用します。

## vSphere Web Client から HyTrust DataControl コンソールへのアクセス
{: #managinghtdc-accessing-console}

vSphere Web Client から HTDC コンソールにアクセスするには、次の手順を使用してください。
1. vSphere Web Client で、**「KC1」**と**「KC2」**という名前の仮想マシンを見つけます。
2. **「KC1」**または**「KC2」**を右クリックし、**「コンソールを開く」**をクリックします。
3. HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスの詳細ページに表示されるコンソール資格情報を使用してコンソールにログインします。

詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)を参照してください。

## HyTrust DataControl VM のインターネット・アクセスの有効化
{: #managinghtdc-internet-access}

HTDC 4.3.2 以降の場合、{{site.data.keyword.vmwaresolutions_short}} は、コール・ホーム機能が有効になっている HyTrust ライセンスの自動更新サポートを提供します。 プライベート専用ではない vCenter Server インスタンスの場合、HTDC は、管理サービス ESG **mgmt-nsx-edge** で定義されたファイアウォールおよび SNAT (送信元ネットワーク・アドレス変換) ルールを使用してデプロイされます。

これらのルールにより、HyTrust 仮想マシン (VM) のインターネット・アクセスを有効にすることができます。 インターネット・アクセスが有効になっていない場合、HTDC インストール済み環境に適用されるライセンスは 1 年後に有効期限が切れます。

プライベート専用 vCenter Server 環境の場合、VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge** が追加されないため、ファイアウォールおよび SNAT のルールは定義されません。 その結果、プライベート専用インスタンスのインターネット接続性を有効化できず、HyTrust ライセンスは毎年有効期限が切れます。
{:note}

### 定義されたファイアウォール規則および SNAT 規則を見つける手順
{: #managinghtdc-proc-find-firewall}

1. VMware vSphere Web Client (FLEX) にログインし、ESG **mgmt-nsx-edge** を見つけます。
2. **「ホーム」>「ネットワークとセキュリティー」>「NSX Edges」**をクリックします。
3. ESG **mgmt-nsx-edge** をダブルクリックし、**「管理」**タブをクリックします。
4. **「ファイアウォール」**タブに移動し、HyTrust 規則を見つけます。 送信元 IP アドレスをメモします。 これらが HyTrust VM の IP アドレスです。
5. **「NAT」**タブに移動し、HyTrust VM 用に作成された SNAT 規則を見つけます。 送信元 IP アドレスが、前のステップでメモした IP アドレスと一致するはずです。

### HTDC のインターネット接続を有効にする手順
{: #managinghtdc-proc-enable-internet}

1. 前の手順のステップ 1 から 3 を実行します。
2. **「設定」**をクリックし、**「インターフェース」**をクリックします。 プライベート・アップリンクの IP アドレスをメモします。 このアドレスが新しいデフォルト・ゲートウェイになります。
3. **「ホーム」>「ホストおよびクラスター (Hosts and Clusters)」**をクリックし、HyTrust VM を見つけます。 VM の 1 つを右クリックし、**「コンソールを開く」**をクリックします。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールの HyTrust DataControl on IBM Cloud サービスの詳細ページに表示されるコンソール資格情報を使用してコンソールにログインします。
5. VM から現在のデフォルト・ゲートウェイ IP アドレスを取得するには、**「ネットワーク設定の管理 (Manage Network Settings)」>「現在のネットワーク構成の表示 (Show Current Network Configuration)」**をクリックします。 **「ゲートウェイ」**にリストされている IP アドレスをメモします。 このアドレスが、静的ルートに使用されるゲートウェイになります。
6. VM の静的ルートを設定するには、**「ネットワーク設定の管理 (Manage Network Settings)」>「静的経路の管理 (Manage Static Routes)」>「静的経路の追加 (Add Static Route)」**をクリックします。 **「ネットワーク・アドレス」**を `10.0.0.0/8` に、**「ゲートウェイ」**を前のステップでメモした IP アドレスに設定します。
7. VM のデフォルト・ゲートウェイ IP を設定するには、**「ネットワーク設定の管理 (Manage Network Settings)」>「現在のネットワーク構成の変更 (Change Current Network Configuration)」**をクリックします。 警告メッセージが表示されたら、**「OK」**をクリックし、**「カスタム構成 (Custom Configuration)」**をクリックします。 **「ゲートウェイ」**フィールドを、ステップ 2 でメモしたプライベート・アップリンク IP アドレスに設定し、**「OK」**をクリックします。 新しいネットワーク構成がインストールされ、ネットワーク・サービスが再始動するまで待ちます。
8. HyTrust SecureOS の再認証を求めるメッセージが表示されたら、**「OK」**をクリックし、このインストールの他の HyTrust VM の IP アドレスを入力します。 16 文字のパスフレーズを要求された場合は、Enter キーを押してメインメニューに戻ります。 現在のネットワーク構成を調べて、変更が適用されていることを確認します。
9. VM がインターネットにアクセスできることを確認するには、パブリック IP アドレスまたは Web サイトに ping します。 **「ネットワーク設定の管理 (Manage Network Settings)」>「ネットワーク診断ツール (Network Diagnostic Tools)」>「他のサーバーのインバウンド・ポートのテスト (Test Inbound Ports of Another Server)」**をクリックします。パブリック Web サイト・アドレス (例: `www.ibm.com`) を入力し、**「OK」**をクリックし、ポートに `80 443` (またはテストするその他のポート) と入力すると、`80 (OK) 443 (OK)` のようなメッセージでインバウンド・ポートを示す応答が即時に返されます。
10. 他の HyTrust VM について、ステップ 3 から 9 を繰り返します。


## 関連リンク
{: #managinghtdc-related}

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Web サイト](https://www.hytrust.com/){:external}
