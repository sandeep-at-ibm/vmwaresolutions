---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# HyTrust DataControl on IBM Cloud の概要

HyTrust DataControl on {{site.data.keyword.cloud}} サービスでは、鍵管理機能が組み込まれた強い暗号を使用して、ワークロードをライフサイクルにわたって保護できます。 このサービスは、オペレーティング・システム・レベルとデータ・レベルの両方で暗号化を実行できます。つまり、ワークロード内で任意のディレクトリー、フォルダー、またはファイルを暗号化/復号できます。

**利用可否:** このサービスは、vSphere 6.5 を実行する、V2.3 以降のリリースでデプロイ (または V2.3 以降のリリースにアップグレード) されたインスタンスでのみ利用可能です。

## HyTrust DataControl on IBM Cloud のコンポーネント

アクティブ-アクティブ・モードでは、デフォルトのクラスターに HyTrust DataControl (HTDC) アプライアンスの高可用性 (HA) ペアがデプロイされます。HyTrust KeyControl 機能をワークロードに提供するために、HTDC アプライアンスのライセンスが付与されています。

HTDC アプライアンスの各ペアは、NSX Manager、vCenter Server Appliance、Platform Services Controller などの管理仮想マシン (VM) に指定したポータブル・サブネットと同じサブネットにデプロイされます。 このアプライアンスは、{{site.data.keyword.cloud_notm}} バックエンド・カスタマー・ルーター (BCR) 経由でルーティングを行い、管理 VM サブネットに関連付けられているゲートウェイに割り当てられます。また、このアプライアンスは、デフォルト・クラスターのデフォルト・ストレージに配置されます。

## HyTrust DataControl on IBM Cloud を削除する際の考慮事項

HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスを削除する前に、DataControl のすべてのディスクを暗号化またはバックアップしたことを確認してください。 サービスを削除した後に、鍵が削除されて、VM からロックアウトされる可能性があります。

## 関連リンク

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} の注文](htdc_ordering.html)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} の管理](managinghtcc.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust Web サイト](https://www.hytrust.com/)
