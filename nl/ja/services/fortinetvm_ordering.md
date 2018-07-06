---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-15"

---

# FortiGate Virtual Appliance on IBM Cloud の注文

FortiGate Virtual Appliance on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの FortiGate Virtual Appliance on IBM Cloud の注文

以下のいずれかの方法を使用して、新しいインスタンスで FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_full}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「FortiGate Virtual Appliance on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「FortiGate Virtual Appliance on IBM Cloud service」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの FortiGate Virtual Appliance on IBM Cloud の注文

以下のいずれかの方法を使用して、既存のインスタンスに FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「サービスの追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「FortiGate Virtual Appliance on IBM Cloud service」**を選択し、サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## FortiGate Virtual Appliance on IBM Cloud サービスの構成

このサービスを注文する際には、以下の設定を行います。

### 名前

サービス名を入力します。

### デプロイメント・サイズ

IBM Cloud では、デプロイメント・サイズに関して以下のオプションがあります。
* スモール (2 vCPU / 4 GB RAM)
* ミディアム (4 vCPU / 6 GB RAM)
* ラージ (8 vCPU / 12 GB RAM)

### ライセンス・モデル

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} のライセンス・モデルには、以下のオプションがあります。
<dl class="dl">
        <dt class="dt dlterm">標準 FW</dt>
        <dd class="dd">このバンドルには、ステートフル・パケット・インスペクション、VLAN の保護と詳細ロギング、入口/出口ファイアウォール・ルール、
SSL/IPSec VPN 終端、24 時間 365 日サポートが含まれています。</dd>
        <dt class="dt dlterm">標準 FW + UTM</dt>
        <dd class="dd">このバンドルには、NGFW IPS と Web フィルタリング、アンチウィルスとアンチスパム、IP & ドメイン評価、コア FortiCare セキュリティー・サービスに加えて、標準的なファイアウォール・サービスがすべて含まれています。</dd>
        <dt class="dt dlterm">標準 FW + Enterprise</dt>
        <dd class="dd">このバンドルには、FortiSandbox Cloud とモバイル・セキュリティーに加えて、標準的なファイアウォール・サービスと UTM サービスがすべて含まれています。</dd>
</dl>

**重要**: サービスのインストール後にライセンス・モデルを変更することはできません。 ライセンス・モデルを変更するには、既存のサービスを削除し、別のライセンス・オプションを選択してサービスを再インストールする必要があります。

## 関連リンク

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の概要](fortinetvm_considerations.html)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の管理](managingfortinetvm.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet Web サイト](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
