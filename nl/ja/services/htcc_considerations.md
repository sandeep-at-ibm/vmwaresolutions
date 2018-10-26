---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# HyTrust CloudControl on IBM Cloud の概要

HyTrust CloudControl on {{site.data.keyword.cloud}} サービスは、役割ベースのアクセス制御 (RBAC)、承認、および監査を含むセキュリティー規格に対するコンプライアンスを実行および制御します。このサービスを HyTrust DataControl と組み合わせると、仮想マシンとワークロードのデータを特定の地域、クラスター、または {{site.data.keyword.CloudDataCent_notm}} の ESXi サーバーから外に出さないようにすることができます。

**利用可否:** このサービスは、vSphere 6.5 を実行する、V2.3 以降のリリースでデプロイ、または V2.3 以降のリリースにアップグレードされたインスタンスでのみ利用できます。

## HyTrust CloudControl on IBM Cloud の技術仕様

以下のコンポーネントが注文され、HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### HyTrust CloudControl アプライアンス

* CPU: 4 vCPU
* RAM: 16 GB
* ディスク: コンバージド・クラスター内の vSAN に常駐する 70 GB VMDK
* ネットワーク: 管理用に指定された VLAN-backed プライベート・ポータブル・ネットワーク上に配置されます

### 高可用性

アクティブ-パッシブ構成で、2 つの CloudControl アプライアンスがデプロイされます。

### ライセンスと料金

ホストごとのライセンス: HyTrust CloudControl ライセンスは、環境内のホストごとに注文されます。

## HyTrust CloudControl on IBM Cloud を削除する際の考慮事項

HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスを削除する前に、**Root Password Vaulting** を構成していた場合は無効にし、すべての保護ホストを HyTrust CloudControl から削除してください。

### 関連リンク

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} の注文](htcc_ordering.html)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} の管理](managinghtcc.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust Web サイト](https://www.hytrust.com/)
