---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust KeyControl on IBM Cloud の概要
{: #htkc_considerations}

HyTrust KeyControl on {{site.data.keyword.cloud}} サービスは、暗号化ワークロードの管理を単純化します。 このサービスは、鍵の保管、鍵の配布、鍵のローテーション、鍵の失効など、暗号鍵のライフサイクルを自動化および単純化します。 FIPS 140-2 準拠の暗号化を使用すると、企業で簡単に暗号鍵を一括して管理できるようになります。

このサービスは、vSphere 6.5 を実行する、V2.5 以降でデプロイまたは V2.5 以降にアップグレードされたインスタンスでのみ利用できます。 現在インストールされている HyTrust KeyControl のバージョンは 4.2 です。
{:note}

## HyTrust KeyControl on IBM Cloud の技術仕様
{: #htkc_considerations-specs}

以下のコンポーネントが注文され、HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### HyTrust KeyControl アプライアンス
{: #htkc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* ディスク: 終息したクラスター内の vSAN に常駐する 20 GB VMDK
* ネットワーク: 管理用に指定された VLAN-backed プライベート・ポータブル・ネットワーク上に配置されます

### 高可用性
{: #htkc_considerations-ha}

デフォルトでは、アクティブ-アクティブ・クラスター構成で、2 つの KeyControl アプライアンスがデプロイされます。

オプションで、2 つの KeyControl アプライアンスをスタンドアロンのクラスター化されていない構成でデプロイするように指定できます。

### ライセンスと料金
{: #htkc_considerations-licenses}

HyTrust KeyControl ライセンスは、インスタンスのインストールごとに注文します。

## HyTrust KeyControl on IBM Cloud を削除する際の考慮事項
{: #htkc_considerations-remove}

HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスを削除する前に、KeyContol を使用しないようにすべてのクライアントを分離したことを確認してください。 サービスを削除した後に、鍵が削除されて、VM からロックアウトされる可能性があります。

## 関連リンク
{: #htkc_considerations-related}

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_ordering)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Web サイト](https://www.hytrust.com/)
