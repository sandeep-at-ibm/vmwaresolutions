---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# HyTrust KeyControl on IBM Cloud の概要

HyTrust KeyControl on {{site.data.keyword.cloud}} サービスは、暗号化ワークロードの管理を単純化します。 このサービスは、鍵の保管、鍵の配布、鍵のローテーション、鍵の失効など、暗号鍵のライフサイクルを自動化および単純化します。FIPS 140-2 準拠の暗号化を使用すると、企業で簡単に暗号鍵を一括して管理できるようになります。 

**利用可否:** このサービスは、vSphere 6.5 を実行する、V2.5 以降のリリースでデプロイ (または V2.5 以降にアップグレード) されたインスタンスでのみ利用できます。

## HyTrust KeyControl on IBM Cloud の技術仕様

以下のコンポーネントが注文され、HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### HyTrust KeyControl アプライアンス

* CPU: 2 vCPU
* RAM: 8 GB
* ディスク: 終息したクラスター内の vSAN に常駐する 20 GB VMDK
* ネットワーク: 管理用に指定された VLAN-backed プライベート・ポータブル・ネットワーク上に配置されます

### 高可用性

デフォルトでは、アクティブ-アクティブ・クラスター構成で、2 つの KeyControl アプライアンスがデプロイされます。

オプションで、2 つの KeyControl アプライアンスをスタンドアロンのクラスター化されていない構成でデプロイするように指定できます。

### ライセンスと料金

HyTrust KeyControl ライセンスは、インスタンスのインストールごとに注文します。

## HyTrust KeyControl on IBM Cloud を削除する際の考慮事項

HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスを削除する前に、KeyContol を使用しないようにすべてのクライアントを分離したことを確認してください。 サービスを削除した後に、鍵が削除されて、VM からロックアウトされる可能性があります。

### 関連リンク

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} の注文](htkc_ordering.html)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} の管理](managinghtkc.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust Web サイト](https://www.hytrust.com/)
