---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: VMware HCX, HCX, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud の概要
{: #hcx_considerations}

HCX on {{site.data.keyword.cloud}} サービスは、オンプレミス・データ・センターのネットワークを {{site.data.keyword.cloud_notm}} にシームレスに拡張できます。これにより、変換や変更を行わずに仮想マシン (VM) を {{site.data.keyword.cloud_notm}} との間で移行できるようになります。 HCX は、セキュアに拡張されたネットワークによって、アプリケーション・モビリティーとインフラストラクチャーのハイブリッド化を可能にする抽象化層を作成します。VMware 環境を vSphere 5.1 から最新の vSphere バージョンにモダナイズする処理は、HCX によるシームレスな変換が可能なので、既存のアプリケーションを屈折または変更することなく簡単に行うことができます。HCX により、IP サブネットの範囲を {{site.data.keyword.cloud_notm}} に移行できます。これにより、ハイブリッド・デプロイメントに際して IP の整合性を確保でき、エンドツーエンド Suite B 暗号化を使用した高水準のセキュリティーを提供できます。

HCX on {{site.data.keyword.cloud_notm}} では、BYOL (Bring Your Own License) を使用して、{{site.data.keyword.cloud_notm}} または同等のバージョンを介して NSX Advanced または Enterprise を取り込む必要があります。VMware HCX on {{site.data.keyword.cloud_notm}} サービスを注文する際は、12 カ月間のコミットメントが必要です。HCX を最初にデプロイした後に、12 カ月連続で課金が発生します。追加のノードがあれば、それも最初のプロビジョニング有効期限に含まれます。12 カ月のコミットメント期間が満了した後は、HCX on {{site.data.keyword.cloud_notm}} サービスのインストールとアンインストール、およびホストやクラスターの追加と削除を制限なしで行うことができます。アカウントには 1 カ月単位で料金が請求されます。また、アカウントは随時、キャンセルできます。

12 カ月のコミットメント満了日は、HCX on {{site.data.keyword.cloud_notm}} の詳細ページに示されています。サービス詳細の表示について詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure)を参照してください。
{:note}

vCenter Server with HCX on {{site.data.keyword.cloud_notm}} インスタンスでは、オンプレミス・サイトからの同時接続が 3 つまでに制限されています。

HCX on {{site.data.keyword.cloud_notm}} は、以下のプラットフォームでサポートされています。

* vSphere 5.1 (vCenter 5.1 では API を使用したコマンド・ラインだけ)
* vSphere 5.5 (vCenter 5.5u3 以上では Web クライアント UI に対応)
* vSphere 6.0
* vSphere 6.5 (vDS は 6.0 レベルであることが必要)
* vSphere 6.7

## HCX on IBM Cloud の技術仕様
{: #hcx_considerations-specs}

以下のコンポーネントが注文されて HCX on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

オンプレミスの HCX インスタンスには、ライセンス交付とアクティベーションのみが含まれます。
{:note}

### HCX 管理用の VMware NSX Edge Services Gateways のアクティブ/パッシブ・ペア
{: #hcx_considerations-nsx}

* CPU: 6 vCPU
* RAM: 8 GB
* ディスク: 3 GB VMDK

### HCX 管理アプライアンス - 仮想マシン
{: #hcx_considerations-vm}

* CPU: 4 vCPU
* RAM: 12 GB
* ディスク: 60 GB VMDK

構成時には必要に応じて、L2 接続、WAN 最適化、およびゲートウェイ接続のために追加の HCX アプライアンスがデプロイされます。

### ネットワーキング
{: #hcx_considerations-networking}

* 16 個の IP アドレスを持つ 1 つのパブリック・ポータブル・サブネット
* 64 個の IP アドレスを持つ 2 つのプライベート・ポータブル・サブネット
* プライベート・ポータブル vMotion サブネットからの 8 個の IP アドレス

## HCX on IBM Cloud をインストールする際の考慮事項
{: #hcx_considerations-install}

HCX on {{site.data.keyword.cloud_notm}} をインストールしようとする前に、以下の考慮事項を確認してください。

### ESXi サーバーの数に関する要件
{: #hcx_considerations-esxi-servers}

デフォルト・クラスターに 51 台を超える ESXi サーバーがあるインスタンスに HCX on {{site.data.keyword.cloud_notm}} サービスをインストールすることはできません。 HCX on {{site.data.keyword.cloud_notm}} は、デフォルト・クラスターの vMotion サブネット内に 8 つの IP アドレスを必要とするため、ESXi サーバーの数が 51 を超えると、HCX on {{site.data.keyword.cloud_notm}} で使用できる vMotion サブネット内の IP アドレスがなくなります。

### ファイアウォール・ルールに関する要件
{: #hcx_considerations-firewall}

HCX on {{site.data.keyword.cloud_notm}} サービスをインストールする前に、HCX Manager 仮想アプライアンス (HCX Manager) が自己登録できるように、すべてのアウトバウンド HTTPS トラフィックを許可するファイアウォール・ルールを既存のファイアウォールに追加する必要があります。 HCX Manager のインストールが完了したら、ファイアウォール・ルールを除去してもかまいません。 さらに、HCX を適切に機能させるためのファイアウォール・ルールを構成する必要があります。 詳しくは、[VMware HCX on {{site.data.keyword.cloud_notm}} のポート・アクセス要件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req#hcx-archi-port-req)を参照してください。

## HCX on IBM Cloud を削除する際の考慮事項
{: #hcx_considerations-delete}

HCX on {{site.data.keyword.cloud_notm}} サービスを削除する前に、以下の考慮事項を確認してください。
* オンプレミス・ソース・サイトと {{site.data.keyword.cloud_notm}} ターゲット・サイトの間の相互接続と拡張ネットワークを削除しておきます。 相互接続と拡張ネットワークを削除するには、オンプレミスの VMware vSphere Web Client で HCX ユーザー・インターフェースを使用します。
* オンプレミス・ソース・サイトと {{site.data.keyword.cloud_notm}} ターゲット・サイトの間のサイト・ペアを削除しておきます。 サイト・ペアを削除するには、オンプレミスの VMware vSphere Web Client で HCX ユーザー・インターフェースを使用します。
* HCX on {{site.data.keyword.cloud_notm}} の削除は自動的に行われます。 このサービスを正しく削除するためには、以下の手順を実行します。
   * クラウド・サイドの HCX Manager 用に注文した HCX ライセンスが非アクティブになります。
   * HCX Manager が削除されます。
   * HCX 用に予約されていた vMotion IP アドレスが解放されます。
   * 空の場合、HCX 関連のリソース・プールが除去されます。
   * 空の場合、HCX 関連のフォルダーが除去されます。
   * HCX 管理エッジ・アプライアンスが削除されます。

## 関連リンク
{: #hcx_considerations-related}

* [HCX on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)
* [HCX on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [VMware HCX on IBM Cloud ガイド付きデモ: HCX を使用した VM の移行方法の学習](https://www.ibm.com/cloud/garage/dte/producttour/vmware-hcx-ibm-cloud-guided-demo-learn-how-migrate-vm-using-hcx){:external}
* [HCX の用語集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [VMware Hybrid Cloud Extension の概要](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension の資料](https://cloud.vmware.com/vmware-hcx/resources){:external}
