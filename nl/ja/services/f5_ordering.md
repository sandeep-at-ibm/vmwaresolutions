---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: F5 license activation, F5 configuration, order F5

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# F5 on IBM Cloud の注文
{: #f5_ordering}

F5 on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの F5 on IBM Cloud の注文
{: #f5_ordering-new}

以下のいずれかの方法を使用して、新しいインスタンスで F5 on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「F5 on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「F5 on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの F5 on IBM Cloud の注文
{: #f5_ordering-existing}

以下のいずれかの方法を使用して、既存のインスタンスに F5 on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「F5 on IBM Cloud」**を選択し、サービス設定を指定し、**「既存のインスタンスに追加」**を選択します。

## プライベート・インスタンスでの F5 on IBM Cloud の注文
{: #f5_ordering-private}

パブリック・インターフェースで設定されていないインスタンスに対して F5 on {{site.data.keyword.cloud_notm}} を注文する場合は、プロキシー・サーバーを指定してインストールを完了する必要があります。 F5 {{site.data.keyword.cloud_notm}} のインストールを開始する前に、HTTP プロキシー・サーバーを設定し、Virtual Routing and Forwarding (VRF) で使用可能にする必要があります。

BigIP Virtual Edition (VE) エンドポイントは、作動可能になる前にライセンスをアクティブ化できる必要があります。 BigIP VE エンドポイントのインストール後は、プロキシー・サーバーを使用する必要はなくなります。

F5 on {{site.data.keyword.cloud_notm}} サービスのインストール時には、プロキシー・サーバーが機能していないとサービスを追加できません。
{:note}

## F5 on IBM Cloud サービスの構成
{: #f5_ordering-config}

このサービスを注文する際には、以下の設定を行います。

### F5 ライセンス・アクティベーション接続
{: #f5_ordering-config-license}

ライセンスのアクティベーションには**「パブリック・ネットワーク」**または**「プライベート・ネットワーク」**を選択します。 ターゲット・クラスターがプライベート専用ネットワーク・インターフェースで構成されている場合、**「プライベート・ネットワーク」**オプションのみが使用可能です。 この選択により、F5 仮想サーバーが F5 ライセンス・サーバーに接続する方法が決まり、ワークロード・データ・プレーンには影響しません。

**「Private network」**を選択した場合は、以下の設定を指定します。
* **プロキシー IP アドレス (Proxy IP Address)**: プロキシー・サーバーの IPv4 アドレス。
* **プロキシー・ポート番号 (Proxy Port Number)**: プロキシー・サーバーのポート番号 (一般に 8080 または 3128)。

認証済みプロキシーはサポートされていません。
{:note}

### 名前
{: #f5_ordering-config-name}

サービス名を入力します。

### 最大帯域幅
{: #f5_ordering-config-bandwidth}

F5 BIG–IP アプライアンスの最大スループットを指定します。

### ライセンス・モデル
{: #f5_ordering-config-license-model}

F5 on {{site.data.keyword.cloud_notm}} サービスのライセンス・モデルには、以下のオプションがあります。
<dl class="dl">
        <dt class="dt dlterm">Good</dt>
        <dd class="dd">このオファーでは、フルプロキシー・アーキテクチャーとして機能する BIG-IP Local Traffic Manager™ (LTM) VE を利用して、ローカル・トラフィックをインテリジェントに管理し、SSL トラフィックを完全に可視化し、分析とヘルス・モニタリングを行うことによって、ユーザーが常にアプリケーション・サーバーを使用できるようにします。</dd>
        <dt class="dt dlterm">Better</dt>
        <dd class="dd">このオファーは**「Good」**オプションの利点をベースに構築されており、BIG-IP DNS™、BIG-IP Advanced Firewall Manager™ (AFM)、BIG-IP Application Acceleration Manager™ (AAM) の各モジュールが追加されています。 グローバル・トラフィック管理サービス、アプリケーション・パフォーマンス最適化機能、高機能ネットワーク・ファイアウォール機能、分散型サービス妨害 (Distributed Denial of Service: DDoS) 緩和機能を備えています。</dd>
        <dt class="dt dlterm">Best</dt>
        <dd class="dd">**「Good」**と**「Better」**のオファーに加えて、BIG-IP Application Security Manager™ (ASM) が L7 DDoS、Open Web Application Security Project (OWASP) の上位 10 の脅威、一般的なアプリケーション脆弱性に対して、総合的にアプリケーションを保護します。 SSO (シングル・サインオン) や MFA (多要素認証) などのフィーチャーが取り込まれた BIG-IP Access Policy Manager™ (APM) を使用することにより、ユーザーは、マルチクラウド環境内に置かれたアプリケーションに安全かつ簡単にアクセスできます。</dd>
</dl>

サービスのインストール後にライセンス・モデルを変更することはできません。 ライセンス・モデルを変更するには、既存のサービスを削除し、別のライセンス・モデルを選択してサービスを再インストールする必要があります。
{:important}

## 関連リンク
{: #f5_ordering-releated}

* [F5 on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [F5 on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [F5 Deployment Guides](https://www.f5.com/services/resources/deployment-guides){:new_window}
