---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# V2.3 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのその他のヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Spectre および Meltdown への対処

{{site.data.keyword.vmwaresolutions_short}} は、Spectre および Meltdown と呼ばれる脆弱性 (CVE-2017-5753、CVE-2017-5715、CVE-2017-5754) に対して VMware から提供されたパッチをリリースしました。

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

詳しくは、[Spectre および Meltdown 脆弱性への対処](../vmonic/trbl_fix_spectre.html)を参照してください。

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

このリリースでは、VMware vCenter Server on IBM Cloud with Hybridity Bundle オファリングが導入されました。 vCenter Server with Hybridity Bundle は、オンプレミスのインフラストラクチャーを素早く簡単にクラウドに拡張できるホステッド・プライベート・クラウドです。 この VMware 環境は、IBM 提供の VMware Software Defined Data Center ライセンスに基づくものであり、VMware HCX on {{site.data.keyword.cloud_notm}} サービスが含まれています。このサービスを使用すると、オンプレミスの vSphere 5.0+ 環境を IBM Cloud サイトに簡単かつ安全に接続して、シームレスなインフラストラクチャーのハイブリッド化と真のアプリケーション・モビリティーを実現できます。

HCX on {{site.data.keyword.cloud_notm}} サービスは、vCenter Server with Hybridity Bundle インスタンスでのみ利用可能です。 既存の vCenter Server インスタンスを vCenter Server with Hybridity Bundle インスタンスにアップグレードするには、まず基本 vCenter Server V2.3 のソフトウェア更新を適用しなければなりません。詳しくは、[vCenter Server インスタンスへの更新の適用](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html)を参照してください。

vCenter Server with Hybridity Bundle について詳しくは、以下を参照してください。

* [vCenter Server with Hybridity Bundle の概要](../vcenter/vc_hybrid_overview.html)
* [vCenter Server with Hybridity Bundle インスタンスの要件と計画](../vcenter/vc_hybrid_planning.html)
* [vCenter Server with Hybridity Bundle インスタンスの注文](../vcenter/vc_hybrid_orderinginstance.html)

## vCenter Server および Cloud Foundation インスタンスのクラスター削除のサポート

インスタンス全体を削除しなくても、インスタンスからクラスターを削除できるようになりました。 V2.2 以前のインスタンスでデプロイしたクラスターの場合に、インスタンスに追加したクラスターを削除するには、インスタンスを V2.3 にアップグレードする必要があります。

詳しくは、以下を参照してください。

* [vCenter Server インスタンスのクラスターの追加、表示、削除](../vcenter/vc_addingviewingclusters.html#deleting-clusters-from-vcenter-server-instances)
* [Cloud Foundation インスタンスのクラスターの追加、表示、削除](../sddc/sd_addingviewingclusters.html#deleting-clusters-from-cloud-foundation-instances)

## VMware vCenter Server インスタンスの更新

このリリースでは、以下のアップグレードと機能改善が適用されます。
*	VMware vSphere ESXi 6.5 U1g (パッチ・レベル ESXi650-201803001 を適用済みの ESXi 6.5u1)
*	VMware vCenter Server 6.5 Update 1g

### vCenter Server インスタンスおよびクラスターの機能強化

V2.3 リリース以降、**カスタマイズ型** のベア・メタル設定を選択した場合に、以下の新しい CPU モデルをデプロイメントできるようになりました。
* Dual Intel Xeon Silver 4110 Processor / 合計 16 コア、2.1 GHz
* Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz

詳しくは、以下を参照してください。

* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)
* [vCenter Server インスタンスのクラスターの追加、表示、削除](../vcenter/vc_addingviewingclusters.html)

## VMware Cloud Foundation インスタンスの更新

このリリースでは、以下のアップグレードと機能改善が適用されます。
*	VMware vSphere ESXi 6.5 U1g (パッチ・レベル ESXi650-201803001 を適用済みの ESXi 6.5u1)
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## VMware Federal インスタンスの更新

### VMware Federal インスタンスの DNS 構成

管理クラスターに、Microsoft Active Directory (AD) として単一の Microsoft Windows Server 仮想サーバー・インスタンス (VSI) をデプロイするか、2 つの高可用性 Microsoft Windows 仮想マシンをデプロイするかを選択できるようになりました。 V2.2 は、デフォルトで単一の Microsoft Windows VSI が Microsoft AD として自動的にデプロイされていました。 2 つの Microsoft Windows 仮想マシンを選択する新しいオプションを使用すると、プライバシーを強化できるうえに、Veeam サービスを使用してそれらの仮想マシンをバックアップおよびリストアできます。

**注:** 2 つの Microsoft Windows 仮想マシンを使用するようにインスタンスを構成する場合は、2 つの Microsoft Windows Server 2012 R2 ライセンスを提供する必要があります。 Microsoft Windows Server 2012 R2 Standard エディションのライセンスと Microsoft Windows Server 2012 R2 Datacenter エディションのライセンスを使用してください。 仮想マシンは 30 日以内に有効にしてください。

詳しくは、[VMware Federal インスタンスの注文](../vcenter/vc_fed_orderinginstance.html#network-interface-settings)の『*ネットワーク・インターフェースの設定*』セクションを参照してください。

### VMware Federal インスタンスのクラスター・サポートの追加と削除

V2.3 以降のリリースでデプロイされた VMware Federal インスタンスでは、クラスターを使用して ESXi サーバーを管理できるので、リソース管理と可用性が向上します。 インスタンスの注文時に構成した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。 インスタンスの概要ページでクラスターの詳細を確認したり、合計 10 個のクラスターをインスタンスに追加したりできます。 インスタンスの容量を拡張または縮小する場合は、ESXi サーバーを追加または削除するクラスターを選択できます。

インスタンス全体を削除することなく 1 つ以上のクラスターをインスタンスから削除することもできます。

詳しくは、[VMware Federal インスタンスのクラスターの追加、表示、削除](../vcenter/fed_addviewdeleteclusters.html)を参照してください。

## アドオン・サービスの更新

### HyTrust CloudControl on IBM Cloud

V2.3 以降のリリースでデプロイまたは V2.3 以降のリリースにアップグレードされた VMware Cloud Foundation インスタンスと VMware vCenter Server インスタンスで vSphere 6.5 を実行する場合、HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスを使用できるようになりました。 このサービスは、セキュリティー規格を適用してコンプライアンスを統括し、役割ベースのアクセス制御 (RBAC) を提供します。 このサービスを HyTrust DataControl と組み合わせると、仮想マシンとワークロードのデータを特定の地域、クラスター、または {{site.data.keyword.cloud_notm}} データ・センターの ESXi サーバーから外に出さないようにすることができます。

このサービスを組み込んだ形でインスタンスを注文することも、後から既存のインスタンスにこのサービスを追加することもできます。

詳しくは、以下を参照してください。
* [HyTrust CloudControl on IBM Cloud のコンポーネントと考慮事項](../services/htcc_considerations.html)
* [HyTrust CloudControl on IBM Cloud の管理](../services/managinghtcc.html)

### HyTrust DataControl on IBM Cloud

V2.3 以降のリリースでデプロイまたは V2.3 以降のリリースにアップグレードされた VMware Cloud Foundation インスタンスと VMware vCenter Server インスタンスで vSphere 6.5 を実行する場合、HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスを使用できるようになりました。 このサービスでは、鍵管理機能が組み込まれた強い暗号を使用して、ワークロードをライフサイクルにわたって保護できます。 このサービスは、オペレーティング・システム・レベルとデータ・レベルの両方で暗号化を実行できます。つまり、ワークロード内で任意のディレクトリー、フォルダー、またはファイルを暗号化/復号できます。

このサービスを組み込んだ形でインスタンスを注文することも、後から既存のインスタンスにこのサービスを追加することもできます。

詳しくは、以下を参照してください。
* [HyTrust DataControl on IBM Cloud のコンポーネントと考慮事項](../services/htdc_considerations.html)
* [HyTrust DataControl on IBM Cloud の管理](../services/managinghtdc.html)

### IBM Spectrum Protect Plus on IBM Cloud

現行リリースでは、新しくデプロイされるすべてのインスタンスで、IBM Spectrum Protect&trade; Plus V10.1.1 がデフォルトのバックアップ・サービスとしてインストールされます。 IBM Spectrum Protect Plus V10.1.1 の新機能について詳しくは、[IBM Spectrum Protect Plus の更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}を参照してください。

## 新規資料および更新された資料

デプロイメントの後に IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} にストレージを追加する手順を 1 つ 1 つ説明した新しい developerWorks レシピが提供されています。 詳しくは、[デプロイメント後の IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} へのストレージの追加](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)を参照してください。

## ユーザー・インターフェースの更新と向上

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。
* **一貫性**: ユーザー・インターフェースは IBM Cloud 上の他のサービスと一貫性のある外観を提供するようになりました。
* **アクセスの容易さ**: VMware オファリングに IBM Cloud **Catalog** から直接アクセスできるようになりました。
* **合理化されて簡単になった注文の操作環境**: VMware インスタンスの注文とアドオン・サービスのデプロイを単一のインターフェースで行えるようになりました。 また、見積もりコストが計算されてすぐに同じインターフェース上に表示されるので、予算に基づいて構成を調整できます。
* ビジネス・パートナーであるユーザーは、インスタンスの注文時やクラスターの追加時にライセンス持ち込み (BYOL) オプションを使用できません。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改善が行われました。
