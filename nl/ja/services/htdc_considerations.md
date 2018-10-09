---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-18"

---

# HyTrust DataControl on IBM Cloud の概要

HyTrust DataControl on {{site.data.keyword.cloud}} サービスでは、鍵管理機能が組み込まれた強い暗号を使用して、ワークロードをライフサイクルにわたって保護できます。 このサービスは、オペレーティング・システム・レベルとデータ・レベルの両方で暗号化を実行できます。つまり、ワークロード内で任意のディレクトリー、フォルダー、またはファイルを暗号化/復号できます。

**利用可否:** このサービスは、vSphere 6.5 を実行する、V2.3 以降のリリースでデプロイ (または V2.3 以降のリリースにアップグレード) されたインスタンスでのみ利用できます。

## HyTrust DataControl on IBM Cloud の技術仕様

以下のコンポーネントが注文され、HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### HyTrust DataControl アプライアンス
* CPU: 2 vCPU
* RAM: 8 GB
* ディスク: 終息したクラスター内の vSAN に常駐する 20 GB VMDK
* ネットワーク: 管理用に指定された VLAN-backed プライベート・ポータブル・ネットワーク上に配置されます

### 高可用性
アクティブ-アクティブ構成で、2 つの DataControl アプライアンスがデプロイされます。

### ライセンスと料金

ホストごとのライセンス: HyTrust DataControl ライセンスは、環境内のホストごとに注文されます。

## HyTrust DataControl on IBM Cloud を削除する際の考慮事項

HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスを削除する前に、DataControl を使用しないようにすべてのクライアントを分離したことを確認してください。サービスを削除した後に、鍵が削除されて、VM からロックアウトされる可能性があります。

### 関連リンク

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} の注文](htdc_ordering.html)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} の管理](managinghtdc.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust Web サイト](https://www.hytrust.com/)
