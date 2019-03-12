---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl on IBM Cloud の概要
{: #htcc_considerations}

HyTrust CloudControl on {{site.data.keyword.cloud}} サービスは、役割ベースのアクセス制御 (RBAC)、承認、および監査を含むセキュリティー規格に対するコンプライアンスを実行および制御します。 このサービスを HyTrust DataControl と組み合わせると、仮想マシンとワークロードのデータを特定の地域、クラスター、または {{site.data.keyword.CloudDataCent_notm}} の ESXi サーバーから外に出さないようにすることができます。

このサービスは、vSphere 6.5 を実行する、V2.3 以降でデプロイ、または V2.3 以降にアップグレードされたインスタンスでのみ利用できます。 現在インストールされている HyTrust CloudControl のバージョンは 5.4.0 です。
{:note}

## HyTrust CloudControl on IBM Cloud の技術仕様
{: #technical-specifications-for-hytrust-cloudcontrol-on-ibm-cloud}

以下のコンポーネントが注文され、HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### HyTrust CloudControl アプライアンス
{: #htcc_considerations-appliance}

* CPU: 4 vCPU
* RAM: 16 GB
* ディスク: コンバージド・クラスター内の vSAN に常駐する 70 GB VMDK
* ネットワーク: 管理用に指定された VLAN-backed プライベート・ポータブル・ネットワーク上に配置されます

### 高可用性
{: #htcc_considerations-ha}

アクティブ-パッシブ構成で、2 つの CloudControl アプライアンスがデプロイされます。

### ライセンスと料金
{: #htcc_considerations-licenses}

ホストごとのライセンス: HyTrust CloudControl ライセンスは、環境内のホストごとに注文されます。

## HyTrust CloudControl on IBM Cloud を削除する際の考慮事項
{: #htcc_considerations-remove}

HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスを削除する前に、**Root Password Vaulting** を構成していた場合は無効にし、すべての保護ホストを HyTrust CloudControl から削除してください。

## 関連リンク
{: #htcc_considerations-related}

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Web サイト](https://www.hytrust.com/)
