---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl on IBM Cloud の管理
{: #managinghtcc}

HyTrust CloudControl on {{site.data.keyword.cloud}} サービス (HTCC) を管理するには、{{site.data.keyword.vmwaresolutions_short}} コンソールから HTCC WebGUI にアクセスするか、vSphere Web Client から HTCC コンソールにアクセスします。

## IBM Cloud for VMware Solutions コンソールから HyTrust CloudControl WebGUI へのアクセス
{: #managinghtcc-accessing-webgui}

プライマリーまたはセカンダリーの HTCC アプライアンスの WebGUI にログインするには、HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスの詳細ページに記されている WebGUI の資格情報を使用します。

## vSphere Web Client から HyTrust CloudControl コンソールへのアクセス
{: #managinghtcc-accessing-console}

vSphere Web Client から HTCC コンソールにアクセスするには、次の手順を使用してください。
1. vSphere Web Client で、**「CC1」**と**「CC2」**という名前の仮想マシンを見つけます。
2. **「CC1」**または**「CC2」**を右クリックし、**「コンソールを開く」**をクリックします。
3. HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスの詳細ページに表示されるコンソールの資格情報を使用して、コンソールにログインします。

詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)を参照してください。

## HyTrust CloudControl VM のインターネット・アクセスの有効化
{: #managinghtcc-internet-access}

HTCC 5.5.1 以降の場合、{{site.data.keyword.vmwaresolutions_short}} は、コール・ホーム機能が有効になっている HyTrust ライセンスの自動更新サポートを提供します。プライベート専用ではない vCenter Server インスタンスの場合、HTCC は、管理サービス ESG **mgmt-nsx-edge** で定義されたファイアウォールおよび SNAT (送信元ネットワーク・アドレス変換) ルールを使用してデプロイされます。

これらのルールにより、HyTrust 仮想マシン (VM) のインターネット・アクセスを有効にすることができます。インターネット・アクセスが有効になっていない場合、HTCC インストール済み環境に適用されるライセンスは 1 年後に有効期限が切れます。

プライベート専用 vCenter Server 環境の場合、VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge** が追加されないため、ファイアウォールおよび SNAT のルールは定義されません。その結果、プライベート専用インスタンスのインターネット接続性を有効化できず、HyTrust ライセンスは毎年有効期限が切れます。
{:note}

### 定義されたファイアウォール規則および SNAT 規則を見つける手順
{: #managinghtcc-proc-find-firewall}

1. VMware vSphere Web Client (FLEX) にログインし、 ESG **mgmt-nsx-edge** を見つけます。
2. **「ホーム」>「ネットワークとセキュリティー」>「NSX Edges」**をクリックします。
3. ESG **mgmt-nsx-edge** をダブルクリックし、**「管理」**タブをクリックします。
4. **「ファイアウォール」**タブに移動し、HyTrust 規則を見つけます。送信元 IP アドレスをメモします。これらが HyTrust VM の IP アドレスです。
5. **「NAT」**タブに移動し、HyTrust VM 用に作成された SNAT 規則を見つけます。送信元 IP アドレスが、前のステップでメモした IP アドレスと一致するはずです。

### HTCC のインターネット接続を有効にする手順
{: #managinghtcc-enable-internet}

以下のステップは、ライセンスのアップグレードに使用されるプライマリー仮想マシン (VM) の HTCC ネットワーク設定の更新に適用されます。セカンダリー VM の設定を更新する必要はありません。
{:note}

1. 前の手順のステップ 1 から 3 を実行します。
2. **「設定」**をクリックし、**「インターフェース」**をクリックします。プライベート・アップリンクの IP アドレスをメモします。これが新しいデフォルト・ゲートウェイになります。
3. HyTrust CloudControl on IBM Cloud サービスの詳細ページに移動し、**「HTCC Web UI の表示 (View HTCC Web UI)」**をクリックして、サービス詳細ページの資格情報を使用してログインします。
4. 既存のデフォルト・ゲートウェイをメモします。例えば HTCC 5.5.1 の場合、**「構成」>「ネットワーク」**をクリックします。リストされているゲートウェイ IP アドレスをメモします。これは、静的ルートのゲートウェイになります。
5. 静的ルートを追加します。例えば HTCC 5.5.1 の場合、**「構成」>「静的ルート (Static Routes)」**をクリックします。**「追加」**をクリックして以下の情報を入力し、**「OK」**をクリックします。

  ```
  ネットワーク・アドレス: 10.0.0.0
  マスク: 255.0.0.0
  ゲートウェイ: ステップ 4 でメモした IP
  デバイス: ネットワーク 1
  ```

6. デフォルト・ゲートウェイを変更します。例えば HTCC 5.5.1 の場合、**「構成」>「ネットワーク」**をクリックし、**「ゲートウェイ」**フィールドの IP アドレスを手順 3 でメモした IP アドレスに置き換え、**「保存」**をクリックします。

  デフォルト・ゲートウェイを変更する前に、静的ルートを設定したことを確認してください。そうしないと、Web コンソールに到達できなくなる可能性があります。
  {:important}

  これで、プライマリー VM がインターネットにアクセスできるようになります。

7. プライマリー VM がインターネットにアクセスできることを確認するには、パブリック IP アドレスまたは Web サイトに対して `ping` コマンドを実行します。これを行うには、vCenter に戻り、**「CC1」>「コンソールを開く」**を右クリックします。HyTrust CloudControl on IBM Cloud サービスの詳細ページにあるコンソールの資格情報を使用して、コンソールにログインします。`ping` コマンド (例えば `ping www.ibm.com` など) を実行すると、すぐに応答が返ってくるはずです。`Ctrl + C` を押して ping を終了し、パケット・ロスが 0% であることを確認します。

## 関連リンク
{: #managinghtcc-related}

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Web サイト](https://www.hytrust.com/)
