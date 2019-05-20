---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.1 のリリース・ノート
{: #relnotes_v21}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Spectre および Meltdown への対処
{: #relnotes_v21-spectre}

{{site.data.keyword.vmwaresolutions_short}} は、Spectre および Meltdown と呼ばれる脆弱性 (CVE-2017-5753、CVE-2017-5715、CVE-2017-5754) に対して VMware から提供されたパッチをリリースしました。

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware HCX on IBM Cloud
{: #relnotes_v21-hcx}

V2.1 以降のリリースでデプロイまたは V2.1 以降のリリースにアップグレードされた VMware Cloud Foundation インスタンスと VMware vCenter Server インスタンスで vSphere 6.5 を実行する場合、HCX on {{site.data.keyword.cloud_notm}} サービスを使用できるようになりました。 このサービスは、オンプレミスのデータ・センター・ネットワークをシームレスに {{site.data.keyword.cloud_notm}} に拡張するサービスです。これにより、オンプレミスのデータ・センターと {{site.data.keyword.cloud_notm}} の間で仮想マシン (VM) の双方向マイグレーションを変更なしで行えます。 レイヤー 2 のブリッジを構築することで、HCX は WAN 最適化、重複排除、圧縮、暗号化を使用して、より速く、より安全に、Direct Link または VPN トンネルを介してデータをマイグレーションします。 VM の一括マイグレーションは、VMware vSphere 5.1 以上の下位製品に対応しています。 vSphere 6.0 以上をオンプレミスで使用している場合は、オンプレミスから {{site.data.keyword.CloudDataCent_notm}}に VM をライブで (電源をオンにしたまま) vMotion できます。 HCX 使用時に VMware NSX がデータ・センターにインストールされている必要はありません。

HCX on {{site.data.keyword.cloud_notm}} サービスを組み込んだ形で Cloud Foundation や vCenter Server のインスタンスを注文することも、後からインスタンスの詳細ページの**「サービス」**タブで既存のインスタンスにこのサービスを追加することもできます。

オンプレミスの HCX インスタンスを注文し、オンプレミス HCX インストールのライセンスを適用してアクティベーションすることもできます。

詳しくは、以下のトピックを参照してください。
* [HCX on {{site.data.keyword.cloud_notm}} に関する考慮事項](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [HCX on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [オンプレミス HCX インスタンスに関する考慮事項](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_considerations)
* [オンプレミス HCX インスタンスの注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances)

## より柔軟になった VMware Cloud Foundation と vCenter Server のライセンス持ち込みモデル
{: #relnotes_v21-byol}

V2.1 以降の VMware Cloud Foundation インスタンスと VMware vCenter Server インスタンスでは、新規クラスターの作成時に、ライセンス持ち込み (BYOL) を利用することも IBM 提供のサブスクリプション・ライセンスを購入することもできます。 これらのオプションでは、既存のコンポーネント・キーを使用することも、IBM のライセンスを賃借することも可能です。 V2.1 より前は、BYOL を使用する場合、特定の VMware コンポーネント用に IBM 提供ライセンスを購入することはできませんでした。 現在、クラスター単位でライセンスを適用できるのは、VMware vSphere と VMware vSAN だけです。

また、キーを使用してライセンスを適用したクラスターにノードを追加するときに、ノード数がそのキーの容量を超える場合は、新しいライセンス・キーを指定するように求めるプロンプトがコンソールに表示されます。

詳しくは、以下のトピックを参照してください。

* [vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)
* [BYOL に関するよくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_byol)

## Zerto on IBM Cloud サービスのコンポーネントの更新
{: #relnotes_v21-zerto}

V2.1 以降の Cloud Foundation インスタンスと vCenter Server インスタンスに Zerto on {{site.data.keyword.cloud_notm}} サービスをデプロイすると、Zerto Virtual Replication 5.5u2 がプロビジョンされます。 Zerto 仮想レプリケーション・アプライアンス (VRA) は、パフォーマンス上の理由により、ローカル・データ・ストアではなく、管理データ・ストア (vSAN またはエンデュランスのどちらか) にデプロイされるようになりました。 既存の VRA がある場合は、パフォーマンス向上のために、そのストレージを管理データ・ストアにマイグレーションすることを検討してください。

詳しくは、[Zerto on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)を参照してください。

## VMware vCenter Server インスタンスの更新
{: #relnotes_v21-vcs}

### ネットワーク MTU の構成設定
{: #relnotes_v21-mtu}

V2.1 以降のリリースでは、新しい vCenter Server インスタンスは、パブリックの分散仮想スイッチ (DVS) が MTU 1500 (デフォルト) の設定で注文されます。 詳しくは、[vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)の_ネットワーク MTU の構成設定_を参照してください。

### VMware ESXi のパッチと更新のホストへの自動適用
{: #relnotes_v21-esxi-patches}

V2.0 以前の VMware vCenter Server インスタンスでは、クラスターに追加した ESXi ホストにパッチは自動適用されませんでした。

V2.1 以降のインスタンスでは、新しい ESXi ホストにパッチが自動適用されるので、初期インスタンスをプロビジョンしたときのパッチ・レベルと同じパッチ・レベルになります。 それ以降のパッチと更新は手動で適用する必要があります。
今後のリリースで VMware のパッチや更新が提供された場合は、既存インスタンスの ESXi ホストが自動的にスキャンされ、最新のパッチや更新を手動で適用することを促すリマインダーが E メールで送信されます。

詳しくは、[vCenter Server インスタンスへの更新の適用](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)を参照してください。

### VMware NSX ライセンスのアップグレードの見積もり価格
{: #relnotes_v21-nsx-license}

VMware NSX の Advanced または Enterprise エディションにアップグレードする注文を送信する前に、見積もり価格を確認できるようになりました。 見積もり価格は、vCenter Server インスタンス内の ESXi ホストの数に基づいています。 この購入では、NSX ライセンス・キーのみが変更され、VMware NSX の Base エディションが Advanced エディションまたは Enterprise エディションにアップグレードされます。 購入によって NSX ソフトウェアのバージョンがアップグレードされるわけではありません。

詳しくは、[vCenter Server の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)を参照してください。

### 1 クラスターあたりの最大サーバー数が 32 以上に
{: #relnotes_v21-max-clusters}

インスタンス内のデフォルト・クラスターについては、最大 51 サーバーまでデプロイまたは拡張できます。 インスタンス内の 2 つ目以降のすべてのクラスターについては、最大 59 サーバーまでデプロイまたは拡張できます。 詳しくは、[vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)を参照してください。

この機能は、V2.1 以降でデプロイされたインスタンスでのみ利用可能です。 V2.1 より前のリリースから V2.1 にアップグレードされたインスタンスには、このオプションはありません。
{:note}

### ユーザー・カスタマイズ型の IBM Cloud ベア・メタル・サーバーの構成オプション
{: #relnotes_v21-bare-metal}

ユーザー・カスタマイズ型のベア・メタル・サーバー構成に、Dual Intel Xeon Gold 6140 (合計 36 コア、2.3 GHz) が追加されました。

詳しくは、以下のトピックを参照してください。
* [vCenter Server の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)

### 個別の NFS ファイル共有構成
{: #relnotes_v21-nfs}

NFS ファイル共有を個々に構成できるようになりました。 ファイル共有ごとにファイル・サイズとパフォーマンス・レベルを選択するか、注文するすべてのファイル共有に同じファイル・サイズとパフォーマンス・レベルを選択します。

詳しくは、以下のトピックを参照してください。
* [vCenter Server の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)

## ユーザー・インターフェースの更新と向上
{: #relnotes_v21-ui}

ユーザー・インターフェース全体が以下のように改善されました。

* 左側のナビゲーション・ペインの**「インスタンスの注文」**オプションは使用できなくなりました。 インスタンスを注文する手順を実行するには、**「開始」**をクリックしてください。
* インスタンスを注文するときの**「基本」**ページの**「サブドメイン接頭部」**フィールドの名前が**「サブドメイン・ラベル」**に変更されました。
* プライマリーまたはセカンダリーの vCenter Server インスタンスあるいは Cloud Foundation インスタンスを注文するときに**「サマリー」**ページに見積もりコストが表示されるほか、インスタンスの注文の詳細を指定するすべてのページで見積もりコストを計算できるようになりました。
* ナビゲーションの代替方法として、**「リソース」**ページに階層リンク・ナビゲーションが追加されたため、少ない手数で親ページに到達できるようになりました。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。

## 新規資料および更新された資料
{: #relnotes_v21-new-docs}

NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} を使用して既存の {{site.data.keyword.vmwaresolutions_full}} デプロイメントに専用ストレージを接続する方法を段階的に説明した新しい developerWorks レシピが用意されています。 詳しくは、[Steps to attach dedicated storage to VMware Solutions on IBM Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/) を参照してください。
