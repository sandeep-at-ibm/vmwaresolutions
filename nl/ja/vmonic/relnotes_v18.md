---

copyright:

  years:  2016, 2018

lastupdated: "2017-08-28"

---

# V1.8 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのその他のヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Fortinet on IBM Cloud サービス

Fortinet on {{site.data.keyword.cloud_notm}} サービスを、Cloud Foundation と vCenter Server の両方のインスタンスで使用できるようになりました。 このサービスは、高可用性モードの FortiGate Security Appliance (FSA) 300 シリーズ・デバイスのペアをデプロイして、ファイアウォール、ルーティング、NAT、および VPN サービスを提供し、インスタンスのパブリック VLAN 上のすべてのサーバーと仮想マシンを保護します。 Fortinet サービスを組み込んだ形でインスタンスを注文することも、後からインスタンスの詳細ページで既存のインスタンスにこのサービスを追加することもできます。

Fortinet サービスが正常にインストールされたら、FortiGate コンソールから FSA のファイアウォール・ルールを管理および構成できます。 インターネットを介して IBM Bluemix® の外部管理データベースと通信するために IBM CloudDriver 仮想マシンや Zerto Virtual Manager などの管理コンポーネントが開始するアウトバウンド HTTPS 通信を許可するように、FSA ファイアウォール・ルールが定義されていることを確認する必要があります。 アウトバウンド HTTPS 通信は、インスタンス内の管理サービス VMware NSX Edge Services Gateway (ESG) のパブリック IP アドレスから発信されます。

詳しくは、以下のトピックを参照してください。
* [Fortinet on {{site.data.keyword.cloud_notm}} の概要](../services/fsa_considerations.html)
* [Fortinet on {{site.data.keyword.cloud_notm}} の管理](../services/managingfsa.html)

## Veeam on IBM Cloud サービス

このリリースでは、管理コンポーネントとワークロードの両方をバックアップできる Veeam on {{site.data.keyword.cloud_notm}} サービスが導入されました。 この新しいサービスは、管理コンポーネントだけをバックアップするために V1.8 より前のリリースに組み込まれていた従来の Veeam VSI に置き換わるものです。

この変更により、V1.8 より前のインスタンスの Veeam VSI は機能し続けますが、{{site.data.keyword.vmwaresolutions_short}} コンソールではインスタンスのバックアップ・ポイントを使用できなくなるので、サポート・チケットを作成してリストアの支援を要請する必要があります。

また、V1.8 より前の Veeam VSI のライセンスは、2017 年 10 月 14 日に失効します。 したがって、可能な限り早く古い Veeam VSI を新しい Veeam サービスに置き換える必要があります。

詳しくは、以下のトピックを参照してください。
* [Veeam on {{site.data.keyword.cloud_notm}} の概要](../services/veeam_considerations.html)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](../services/managingveeam.html)

## VMware Cloud Foundation インスタンスの更新

### Cloud Foundation インスタンスを注文する際の VMware ライセンスの持ち込み (BYOL)

V1.8 リリース以降、Cloud Foundation インスタンスを注文する際に vSphere、vCenter Server、NSX、vSAN などのインスタンスの VMware コンポーネントのライセンスを適用する方法は 2 つあります。 自動的に購入される新規ライセンスを使用することを選択できます。

所有している VMware ライセンスをコンポーネントに使用することもできます。そのためにはライセンス・キーを提供する必要があります。 この場合、ライセンスを提供した VMware コンポーネントのサポートは、IBM サポートからではなく VMware から提供されます。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンスの注文](../sddc/sd_orderinginstance.html)
* [BYOL に関するよくある質問](faq_byol.html)

## VMware vCenter Server インスタンスの更新

### インスタンスの CPU とメモリーのカスタマイズ

事前に構築され、テストされた「スモール」、「ミディアム」、「ラージ」オプションのほか、カスタマイズ可能なサーバーのオプションも用意されています。 デュアル CPU ベースの VMware HCL 互換サーバー、コアの合計数、RAM の容量をリストから選択できます。 ローカル・ストレージはカスタマイズできません。

詳しくは、以下のトピックを参照してください。
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)
* [vCenter Server インスタンスのクラスターの追加と表示](../vcenter/vc_addingviewingclusters.html)

### 7 つを超える NFS ファイル共有を追加するためのサポート

 クラスター内のすべての ESXi サーバーで最大 32 個のファイル共有を接続できます。

 詳しくは、以下のトピックを参照してください。
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)
* [vCenter Server インスタンスのクラスターの追加と表示](../vcenter/vc_addingviewingclusters.html)

### データ・センターの更新

デプロイメントに利用できる新しいデータ・センターは、**DAL-09、DAL-12、DAL-13 - ダラス**、**LON-04、LON-06 - ロンドン**、**SJC-04 - サンノゼ**、**WDC-06、WDC-07 - ワシントン、DC** です。

詳しくは、[vCenter Server インスタンスの要件と計画](../vcenter/vc_planning.html)を参照してください。

## 使いやすさの向上

ユーザー・インターフェース全体が以下のように改善されました。
* 左側のナビゲーション・ペインの**「開始」**ページで、サービスの内容を確認してインスタンスを注文できます。 {{site.data.keyword.cloud_notm}} Secure Virtualization サービスのアーキテクチャーについて詳しくは、[セキュリティーとコンプライアンス - HyTrust](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/hytrust) を参照してください。
* インスタンスの詳細ページでオーバーフロー・メニューを使用して、**「使用可能」**状態のインスタンスを削除できます。
* NSX ライセンス・エディションをアップグレードするオプションが、**「更新およびパッチ」**タブに追加されました。 ライセンスをアップグレードすると、IBM SoftLayer アカウントの既存の NSX ライセンスがすべて新規ライセンスに置き換えられます。
* インスタンスの詳細ページの**「バックアップとリストア」**タブがなくなりました。
* 複数のサービスを選択して、注文の開始時にデプロイできます。 Zerto on {{site.data.keyword.cloud_notm}} サービスに加えて、Veeam on {{site.data.keyword.cloud_notm}} サービスと Fortinet on {{site.data.keyword.cloud_notm}} サービスも選択できます。
* インスタンスの詳細ページの**「サービス」**タブの**「使用可能なサービス」**タブが、**「サービスの追加」**という名前に変更されました。
