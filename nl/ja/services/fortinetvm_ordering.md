---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Virtual Appliance on IBM Cloud の注文

FortiGate Virtual Appliance on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの FortiGate Virtual Appliance on IBM Cloud の注文

以下のいずれかの方法を使用して、新しいインスタンスで FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「FortiGate Virtual Appliance on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「FortiGate Virtual Appliance on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの FortiGate Virtual Appliance on IBM Cloud の注文

以下のいずれかの方法を使用して、既存のインスタンスに FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「FortiGate Virtual Appliance on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## FortiGate Virtual Appliance on IBM Cloud サービスの構成

このサービスを注文する際には、以下の設定を行います。

### FortiGuard ネットワーク接続

FortiGuard に**「パブリック・ネットワーク」**または**「プライベート・ネットワーク」**を選択します。ターゲット・クラスターがプライベート専用ネットワーク・インターフェースで構成されている場合、**「プライベート・ネットワーク」**オプションのみが使用可能です。この選択により、FortiGuard が Fortinet ライセンス・サーバーに接続してライセンスをアクティブにする方法と、セキュリティー・パッチをダウンロードする方法が決まり、ワークロード・データ・プレーンには影響しません。

**「Private network」**を選択した場合は、以下の設定を指定します。
* **プロキシー IP アドレス (Proxy IP Address)**: プロキシー・サーバーの IPv4 アドレス。
* **プロキシー・ポート番号 (Proxy Port Number)**: プロキシー・サーバーのポート番号 (一般に 8080 または 3128)。
* **プロキシー・ユーザー名 (Proxy User Name)**: プロキシー認証が必要な場合は、プロキシー・サーバーのユーザー名を入力してください。
* **プロキシー・パスワード (Proxy Password)**: プロキシー認証が必要な場合は、プロキシー・サーバーのパスワードを入力してください。

### 名前

サービス名を入力します。

### デプロイメント・サイズ

{{site.data.keyword.cloud_notm}} では、デプロイメント・サイズに関して以下のオプションがあります。
* スモール (2 vCPU / 4 GB RAM)
* ミディアム (4 vCPU / 6 GB RAM)
* ラージ (8 vCPU / 12 GB RAM)

### ライセンス・モデル

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} のライセンス・モデルには、以下のオプションがあります。
<dl class="dl">
        <dt class="dt dlterm">標準 FW</dt>
        <dd class="dd">このバンドルには、ステートフル・パケット・インスペクション、VLAN の保護と詳細ロギング、入り口/出口ファイアウォール・ルール、SSL/IPSec VPN 終端、24 時間 365 日サポートが含まれています。</dd>
        <dt class="dt dlterm">標準 FW + UTM</dt>
        <dd class="dd">このバンドルには、すべての標準ファイアウォール・サービスに加え、Advanced Malware Protection (AMP) サービス (アンチウィルス、ボットネット IP/ドメイン・サービス、モバイル・マルウェア・セキュリティー、FortiSandbox クラウド、ウィルス発生保護サービス、コンテンツ無害化と再構築など)、Web フィルタリング、IPS、アンチスパム、アプリケーション制御、および FortiCare サービスが含まれています。</dd>
        <dt class="dt dlterm">標準 FW + Enterprise</dt>
        <dd class="dd">このバンドルには、標準的なファイアウォール・サービスと UTM サービスすべてに加えて、以下のサービスが含まれています。<ul><li>Cloud Access Security Broker (CASB): このサービスはクラウド・ベース・サービスの可視性、コンプライアンス、データ・セキュリティー、および脅威防御の各機能を提供します。</li><li>産業用セキュリティー: このサービスは、一般的な ICS/SCADA プロトコルに対してシグニチャーを提供します。</li><li>セキュリティーの格付け: このサービスは、重大な脆弱性と構成の脆弱性を特定してベスト・プラクティス推奨事項を実施するために監査機能を提供します。</li></ul></dd>
</dl>

2018 年第 3 四半期に、Fortinet はエンタープライズ・バンドルに 3 つの新しいサービス (CASB、産業用セキュリティー、およびセキュリティーの格付け) を追加しました。これらのサービスは FortiGate 6.0 でのみ使用可能です。
{:note}

サービスのインストール後にライセンス・モデルを変更することはできません。 ライセンス・モデルを変更するには、既存のサービスを削除し、別のライセンス・オプションを選択してサービスを再インストールする必要があります。
{:important}

### 関連リンク

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の概要](fortinetvm_considerations.html)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の管理](managingfortinetvm.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet Web サイト](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
