---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.4 のリリース・ノート
{: #relnotes_v24}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Spectre および Meltdown への対処
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} は、Spectre および Meltdown と呼ばれる脆弱性 (CVE-2017-5753、CVE-2017-5715、CVE-2017-5754) に対して VMware から提供されたパッチをリリースしました。

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## 各国語サポート
{: #relnotes_v24-nls}

V2.4 リリースから、{{site.data.keyword.vmwaresolutions_short}} に各国語サポート (NLS) が組み込まれました。
コンソールのすべての機能やユーザー資料を複数の言語で利用できるようになっています。

英語のほかに以下の言語がサポートされています。
* 　ドイツ語
* スペイン語
* フランス語
* イタリア語
* 　日本語
* 韓国語
* ブラジル・ポルトガル語
* 中国語 (簡体字)
* 中国語 (繁体字)

## Skylake Xeon CPU のサポート
{: #relnotes_v24-skylake}

V2.4 リリースから、VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} と VMware vSphere on {{site.data.keyword.cloud_notm}} のインスタンスとクラスターのデプロイメントで、以下の新しいベアメタル・サーバー CPU モデルを利用できるようになりました。

* Dual Intel Skylake Xeon Silver 4110 プロセッサー / 合計 16 コア、2.1 GHz
* Dual Intel Skylake Xeon Gold 5120 プロセッサー / 合計 28 コア、2.2 GHz
* Dual Intel Skylake Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz

詳しくは、[新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)の『*ベアメタル・サーバーの設定*』セクションを参照してください。

## VMware vCenter Server インスタンスの更新
{: #relnotes_v24-vcs}

### ネットワーク・ファイル・システムのパフォーマンスの強化
{: #relnotes_v24-nfs}

ワークロードが非常に大きいタイプの処理に合わせて設計されている 10 IOPS/GB のパフォーマンス・レベルが、特定の {{site.data.keyword.CloudDataCent_notm}}に制限されずに、すべてのデータ・センターで利用できるようになりました。 詳しくは、[vCenter Server の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#technical-specifications-for-vcenter-server-instances)の『*ストレージ*』セクションを参照してください。

## アドオン・サービスの更新
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

現行リリースでは、新しくデプロイするすべてのインスタンスで、IBM Spectrum Protect&trade; Plus V10.1.1 パッチ 1 がインストールされます。 IBM Spectrum Protect Plus V10.1.1 パッチ 1 の新機能について詳しくは、[IBM Spectrum Protect Plus の更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}を参照してください。

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

新しいオプションが用意され、このサービスの注文時に、HCX 相互接続のためにパブリック・ネットワークとプライベート・ネットワークのいずれかを選択できるようになりました。 詳しくは、[VMware HCX on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)を参照してください。

## 新規資料および更新された資料
{: #relnotes_v24-new-docs}

### リファレンス・アーキテクチャー資料
{: #relnotes_v24-ref-archi}

{{site.data.keyword.vmwaresolutions_short}} のアーキテクチャー資料が、ユーザー資料の『*リファレンス*』セクションに用意されています。 詳しくは、[ソリューションの概要](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)を参照してください。

### サービスの資料
{: #relnotes_v24-docs-services}

サービスの資料が再編成され、サービスの注文時に関連情報を簡単に見つけられるようにナビゲーション機能が改善されています。

詳しくは、以下のトピックを参照してください。

* [F5 on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [Hytrust CloudControl on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Hytrust DataControl on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering) の注文
* [Veeam on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Zerto on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## ユーザー・インターフェースの更新と向上
{: #relnotes_v24-ui}

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* クラスターの追加とサービスの追加のためのペインがページ形式になり、レイアウトの編成が改善された結果、タスクをより効率的に実行できるようになっています。
* **「リソース」**ページの機能が強化され、検索機能、ページ編集機能、ソート機能が追加されています。 こうした機能強化によって、インスタンスを素早く見つけ出せるようになりました。
* インスタンスの詳細ページの左側にナビゲーション・メニューが付いたので、インスタンス情報へのアクセスがより簡単になりました。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
