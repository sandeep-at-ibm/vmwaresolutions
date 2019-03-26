---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl on IBM Cloud の概要
{: #htdc_considerations}

HyTrust DataControl on {{site.data.keyword.cloud}} サービスでは、鍵管理機能が組み込まれた強い暗号を使用して、ワークロードをライフサイクルにわたって保護できます。 このサービスは、オペレーティング・システム・レベルとデータ・レベルの両方で暗号化を実行します。 これにより、ワークロード内で任意のディレクトリー、フォルダー、またはファイルを暗号化/復号できます。

このサービスは、vSphere 6.5 を実行する、V2.3 以降でデプロイ、または V2.3 以降にアップグレードされたインスタンスでのみ利用できます。 現在インストールされている HyTrust DataControl のバージョンは 4.2.1 です。
{:note}

## HyTrust DataControl on IBM Cloud の技術仕様
{: #htdc_considerations-specs}

以下のコンポーネントが注文され、HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### HyTrust DataControl アプライアンス
{: #htdc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* ディスク: 終息したクラスター内の vSAN に常駐する 20 GB VMDK
* ネットワーク: 管理用に指定された VLAN-backed プライベート・ポータブル・ネットワーク上に配置されます

### 高可用性
{: #htdc_considerations-ha
}
アクティブ-アクティブ構成で、2 つの DataControl アプライアンスがデプロイされます。

### ライセンスと料金
{: #htdc_considerations-licenses}

ホストごとのライセンス: HyTrust DataControl ライセンスは、環境内のホストごとに注文されます。

## HyTrust DataControl on IBM Cloud を削除する際の考慮事項
{: #htdc_considerations-remove}

HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスを削除する前に、DataControl を使用しないようにすべてのクライアントを分離します。 サービスを削除した後に、鍵が削除されて、VM からロックアウトされる可能性があります。

## 関連リンク
{: #htdc_considerations-related}

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Web サイト](https://www.hytrust.com/)
