---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# IBM Cloud for VMware Solutions に関する一般的なよくある質問

{{site.data.keyword.vmwaresolutions_full}} に関するよくある質問への回答をご覧ください。

## IBM Cloud for VMware Solutions にはどのようなユーザー・アカウントが必要ですか?

* **IBMid アカウント**。 {{site.data.keyword.vmwaresolutions_short}} コンソールにアクセスするためには、このアカウントが必要です。 このコンソールは、{{site.data.keyword.slportal_full}}とは別のスタンドアロンのユーザー・インターフェースです。 詳しくは、[概説](../index.html)を参照してください。
* **{{site.data.keyword.cloud_notm}} アカウント**。 プロビジョニングにはこのアカウントが必要です。 {{site.data.keyword.cloud_notm}} アカウントを登録するには、**IBMid アカウント**を従量課金 (PAYG) アカウントにアップグレードします。 使用する {{site.data.keyword.cloud_notm}} アカウントは、特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの登録](signing_softlayer_account.html)および [{{site.data.keyword.cloud_notm}} アカウントの要件](slaccountrequirement.html)を参照してください。

## IBM Cloud インフラストラクチャーの資格情報を IBM Cloud for VMware Solutions コンソールに関連付けるにはどうすればよいですか?

初めてインスタンスを注文するときに、{{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報ページの指示に従い、{{site.data.keyword.slportal}}で {{site.data.keyword.cloud_notm}} のユーザー名と API キーを見つけてコピーしてください。 {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報は、最初の注文の後に {{site.data.keyword.vmwaresolutions_short}} コンソールに保管されます。 それ以降の注文では、保管された資格情報が自動的に使用されます。

## VMware 仮想プラットフォームの使用料はどのように請求されますか?

物理インフラストラクチャーと仮想インフラストラクチャー、インスタンスで使用しているライセンスにかかるすべてのコストは、{{site.data.keyword.cloud_notm}} アカウントに課金されます。 インスタンスを注文するときには、{{site.data.keyword.cloud_notm}} アカウントが必要で、アカウントに関連付けられている {{site.data.keyword.slapi_short}} キーを入力する必要があります。

## vCenter Server インスタンスと Cloud Foundation インスタンスと VMware vSphere クラスターの違いはどこにありますか?

どのインスタンス・タイプでも、VMware 仮想環境のデプロイメント方法を選択できます。 違いは、カスタマイズと自動化の程度にあります。

* VMware vCenter Server インスタンスを注文した場合は、カスタマイズしたコンピュート、ストレージ、ネットワークのリソースを備えた VMware 仮想環境がデプロイされます。 デプロイされるコンポーネントについて詳しくは、[vCenter Server の概要](../vcenter/vc_vcenterserveroverview.html)の『_vCenter Server の技術仕様_』セクションを参照してください。
* VMware Cloud Foundation インスタンスを注文した場合は、統一されたソフトウェア定義データ・センター (SDDC) プラットフォームがデプロイされます。 デプロイされるコンポーネントについて詳しくは、[Cloud Foundation インスタンスのコンポーネント](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-instance-components)を参照してください。
* VMware vSphere クラスターを注文すると、ホスト対象の VMware 環境を、VMware 互換ハードウェアを組み込みながら設計して構築するための柔軟性が最大化されます。 ただし、{{site.data.keyword.cloud_notm}} では、VMware vSphere クラスターのオプションの VMware コンポーネントのインストールや構成や起動が自動化されません。
* vCenter Server インスタンスと Cloud Foundation インスタンスと vSphere クラスターでは、サポートされている機能がそれぞれ違います。 詳しくは、[オファリングの比較表](inst_comp_chart.html)を参照してください。

## vCenter Server インスタンスには何が含まれていますか?

詳しくは、[vCenter Server の概要](../vcenter/vc_vcenterserveroverview.html)の『_vCenter Server の技術仕様_』セクションを参照してください。

## Cloud Foundation インスタンスには何が含まれていますか?

詳しくは、[Cloud Foundation インスタンスのコンポーネント](../sddc/sd_cloudfoundationoverview.html)を参照してください。

## vSphere クラスターには何が含まれていますか?
詳しくは、[VMware vSphere on IBM Cloud のコンポーネント](../vsphere/vs_vsphereclusteroverview.html)を参照してください。

## 2 ノードの vCenter Server インスタンスの可用性は高いですか?

実動ワークロードは、3 ノード以上の環境にデプロイすることを強くお勧めします。

VMware vSphere の DRS (Distributed Resource Scheduler) と VMware HA (High Availability) がデフォルトで有効になりますが、VMware のベスト・プラクティスでは、3 つある NSX コントローラーを、各ノードに 1 つずつ配置することが推奨されています。

2 ノードのみの最小デプロイメントでは、一方のノードに NSX コントローラーを 1 つ配置し、もう一方のノードに NSX コントローラーを 2 つ配置します。 NSX コントローラーを 2 つ配置したノードがダウンすると、NSX コントローラーの動作は読み取り専用モードになり、新規 VM (仮想マシン) または vMotion VM でネットワークの問題が発生する可能性があります。

2 ノード・クラスターに 3 つ目のノードを追加すると、vCenter Server が 3 つのノードの間で 3 つの NSX コントローラーを自動的に再調整するので、可用性の高い環境になります。

## VMware vCenter 6.5 HA 構成をセットアップすることはできますか?

いいえ、推奨されません。 {{site.data.keyword.vmwaresolutions_short}} 機能に障害が発生する可能性があります。

## クラスターの名前は変更できますか?

vCenter Server インスタンスの場合、デプロイ時に作成される最初のクラスターのデフォルト名は **cluster1** です。 VMware vSphere Client でデフォルト・クラスターの名前を変更できます。 vCenter Server インスタンスに新規クラスターを追加するときに、{{site.data.keyword.vmwaresolutions_short}} コンソールで任意の名前を指定できます。

**注**: Cloud Foundation インスタンスの場合、デフォルトのクラスター名は変更できません。

##パッチはどのように管理されていますか?

IBM は、IBM CloudDriver コンポーネントについては、継続的な更新を {{site.data.keyword.cloud_notm}} for VMware Solutions コンソールを通して提供しています。 Zerto on {{site.data.keyword.cloud_notm}} や Veeam on {{site.data.keyword.cloud_notm}} などのアドオン・サービスについては、継続的な更新を提供していません。 これらの更新は、お客様が入手してインストールしてください。

VMware の更新は、デプロイした VMware インスタンスのタイプに応じて異なる方法で適用されます。

* VMware Cloud Foundation インスタンスの場合は、vSphere ESXi、NSX、vCenter、Platform Services Controller、および SDDC Manager コンポーネントの更新が、{{site.data.keyword.vmwaresolutions_short}} コンソールから提供されます。
* VMware vCenter Server インスタンスの場合
  * V2.1 以上でデプロイまたは V2.1 以上にアップグレードしたインスタンスの場合、新しくデプロイされる ESXi サーバーとクラスターには、VMware から提供される新しい (最新とは限りません) ESXi 更新が適用されます。
  * 新しくデプロイした ESXi サーバーとクラスターに、必要な最新の更新がすべて適用されていることを確認する作業を含め、VMware コンポーネントのその他のすべての更新はお客様が行ってください。
  * V2.0 以上でデプロイしたインスタンスの場合は、VMware Update Manager (VUM) が vCenter Server に統合されています。 VMware から ESXi の更新をダウンロードするように VUM を構成できます。

詳しくは、以下を参照してください。
* [VMware サポート](https://www.vmware.com/support.html)
* [vCenter Server インスタンスへの更新の適用](../vcenter/vc_applyingupdates.html)
* [Cloud Foundation インスタンスへの更新の適用](../sddc/sd_applyingupdates.html)

## 管理サービスの NSX Edge にはセキュリティーのリスクがありますか?

管理サービスの VMware NSX Edge はパブリック・サブネット上に配置されますが、セキュリティーのリスクが生じないようにセキュリティー対策が適用されます。 それらの対策を次に示します。
*  NSX Edge ファイアウォールは、管理仮想マシンから開始された発信 HTTPS (TCP ポート 443) トラフィックだけを許可するように構成されます。
*  プライベート IP アドレスがプライベート・ネットワークの外部に見えないように、SNAT (送信元ネットワーク・アドレス変換) が使用されます。
*  管理サービスの NSX Edge アプライアンスのリモート・アクセスは無効になっています。
*  プライベート・ネットワークから管理サービスの NSX Edge にアクセスするためのパスワードはランダム化され、暗号化されます。

## ユーザー管理の NSX Edge にはセキュリティーのリスクがありますか?

ユーザー管理の NSX Edge はパブリック VLAN に接続されますが、セキュリティーのリスクが生じないようにセキュリティー対策が適用されます。 それらの対策を次に示します。
*  プライベート・サブネット範囲の IP アドレスからの発信トラフィックだけを許可するようにファイアウォール・ルールが適用されます。
*  プライベート・サブネットのすべての IP アドレスをパブリック・サブネット上の単一の IP アドレスに変換するように SNAT (送信元ネットワーク・アドレス変換) ルール (デフォルトでは無効) が適用されます。
*  ユーザー管理の NSX Edge アプライアンスのリモート・アクセスは無効になっています。
*  プライベート・ネットワークからユーザー管理の NSX Edge にアクセスするためのパスワードはランダム化され、暗号化されます。

## インスタンスのデータ・センターを選択するにはどうすればよいですか?

インスタンスのデプロイメントには、物理インフラストラクチャーに関する厳密な要件があります。ただし、具体的な要件は、{{site.data.keyword.CloudDataCents_notm}}ごとに違います。 インスタンスの注文時に、各地域で利用できるデータ・センターのリストが表示され、そのリストの中から 1 つを選択できます。

詳しくは、以下の資料にある『_IBM Cloud データ・センターの使用可否_』セクションを参照してください。
* [vCenter Server インスタンスの要件と計画](../vcenter/vc_planning.html)
* [vCenter Server with Hybridity Bundle インスタンスの要件と計画](../vcenter/vc_hybrid_planning.html)
* [Cloud Foundation インスタンスの要件と計画](../sddc/sd_planning.html)
* [VMware vSphere on IBM Cloud の要件と計画](../vsphere/vs_planning.html)
* [NetApp ONTAP Select インスタンスの要件と計画](../netapp/np_planning.html)
* [VMware Federal インスタンスの要件と計画](../vcenter/vc_fed_planning.html)

## インスタンスのデプロイにはどのくらいの時間がかかりますか?

インスタンスのデプロイメントの状況を、{{site.data.keyword.vmwaresolutions_short}} コンソールのインスタンスの詳細ページでデプロイメント履歴を参照して確認できます。

## VMware vSphere on IBM Cloud では自動化機能を使用して VMware スタックがインストール、構成、起動されますか?

いいえ。VMware vSphere on {{site.data.keyword.cloud_notm}} では、Cloud Foundation および vCenter Server プラットフォームに含まれる高度な自動化機能は利用されません。 注文内容に基づいて、プラットフォームから、オプションの VMware ライセンス、ESXi サーバー、オプションで FortiGate 物理ファイアウォールの HA ペアが用意されます。 新規クラスターが作成されると、3 つの新規 VLAN (パブリック VLAN 1 つ、プライベート VLAN 2 つ) もプロビジョンされます。

VMware ESXi は各ベア・メタル・サーバーに自動的にインストールされますが、vCenter Server や NSX などの追加の VMware コンポーネントのインストールはお客様が行ってください。 vSphere on {{site.data.keyword.cloud_notm}} は、選択された VMware コンポーネントに基づいて VMware 互換ハードウェアを注文することを保証しますが、VMware 環境の構成と機能を自動実行しません。 IBM でホストされる環境を設計して構築する作業は、お客様が行ってください。

## すべての通知のリストを表示するにはどうすればよいですか?

完全な通知履歴を表示するには、左側のナビゲーション・ペインから**「通知」**をクリックします。

## IBM Cloud for VMware Solutions に問題がある場合はどうすればよいですか?

{{site.data.keyword.vmwaresolutions_short}} のサポートが必要な場合は、いずれかのサポート・チャネルを使用して IBM サポートに連絡してください。 詳しくは、[IBM サポートへのお問い合わせ](trbl_support.html)を参照してください。

### 関連リンク

* [通知](notifications.html)
* [Cloud Foundation インスタンス](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server インスタンス](../vcenter/vc_vcenterserveroverview.html)
* [コンソールへのアクセス](loginmethod.html)
* [ユーザー・アカウントと設定](useraccount.html)
