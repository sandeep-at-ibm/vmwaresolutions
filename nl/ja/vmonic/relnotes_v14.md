---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-08"

---

# V1.4 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのその他のヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Cloud Foundation インスタンスのコンポーネントの更新

以下のコンポーネントが新規追加または更新されました。

* VC/PSC (vCenter/Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* このリリースのマルチサイト構成サポートに必要な Microsoft Active Directory (AD) サービスと DNS (ドメイン・ネーム・システム) サービス用に、新しい Windows VSI (仮想サーバー・インスタンス) が注文されます。 この VSI の仕様は、Windows 2012 R2 (8 GB RAM / 2 CPU コア / 100 GB ディスク / デュアル 1 Gbps プライベート・アップリンク) です。

詳しくは、[Cloud Foundation の概要](../sddc/sd_cloudfoundationoverview.html)を参照してください。

## vCenter Server インスタンスのコンポーネントの更新

以下のコンポーネントが新規追加または更新されました。

### VMware NSX for vSphere 6.2.4

すべての vCenter Server インスタンスにデフォルトで VMware NSX for vSphere 6.2.4 がインストールされるようになりました (これまでは Cloud Foundation インスタンスにのみインストールされていました)。

NSX インストールの一環として、デプロイしたすべての新しいインスタンスに、NSX Manager がインストールされ、ライセンスされます。 さらに、インスタンス管理のために NSX Edge が作成されますが、必要に応じて独自の NSX Edge コンポーネントを作成することもできます。 NSX Edge について詳しくは、このページの『_VMware NSX Edge_』セクションを参照してください。

**注**: NSX Controller は、vCenter Server インスタンスにはインストールされません (Cloud Foundation インスタンスにはインストールされます)。 vCenter Server インスタンスで VXLAN または分散論理ルーターを使用する場合は、NSX Controller をユーザーがインストールする必要があります。

VMware NSX for vSphere 6.2.4 で導入された拡張機能、要件、および既知の問題については、[NSX for vSphere 6.2.4 リリース・ノート](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}を参照してください。

### VMware NSX Edge

NSX Edge が、注文した新しい vCenter Server インスタンスに含まれようになりました。 NSX Edge は、ネットワーク・エッジ・セキュリティーとゲートウェイ・サービスを提供して、仮想化ネットワークを分離します。

インスタンスのデプロイメント中に、IBM が Management VMware NSX Edge Services Gateway (ESG) をデプロイします。 この ESG は、IBM 管理仮想マシンが、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。 この ESG は、2 つのインターフェースを含むようにデプロイされます。一方のインターフェースは {{site.data.keyword.cloud_notm}} のプライベート VLAN に接続され、もう一方のインターフェースは {{site.data.keyword.cloud_notm}} のパブリック VLAN に接続されます。

セキュリティーを確保するため、管理仮想マシンから開始されたアウトバウンド HTTPS 通信のみを許可するようにファイアウォール・ルールが適用されます。 この ESG は「ラージ」構成でデプロイされ、IBM サポートのみが構成を変更できます。 詳しくは、以下を参照してください。

* [vCenter Server 技術仕様](../vcenter/vc_vcenterserveroverview.html)
* [管理サービスの NSX Edge にはセキュリティーのリスクがありますか?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX 資料](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### NSX ライセンス

ノードごとに VMware NSX Base for Service Providers Edition ライセンスが 1 つ注文されます。

### 新しいサブネット・アドレス・ブロック

ノードごとに 16 個のパブリック・ポータブル・アドレスを含むサブネット・ブロックが 1 つ注文されます。

## サービス料金モデルの更新

サービス料金モデルがシンプルになりました。

* Cloud Foundation インスタンスについては、_VMware Cloud Foundation インスタンス・サービス_、_VMware Cloud Foundation ストレージ・サービス_、および _VMware Solutions Hypervisor_ の料金が廃止されました。
* vCenter Server インスタンスについては、_VMware vCenter Server インスタンス_および _VMware Solutions Hypervisor_ の料金が廃止されました。
* 両方のインスタンス・タイプに、新しい「_サポートとサービス_」の料金が導入されました。これは、各ノードに適用される月単位の料金です。

## インスタンス・ネットワーキング・トポロジーの更新

このリリースには、インスタンスの以下のトポロジー機能拡張が含まれています。

* Cloud Foundation インスタンスと vCenter Server インスタンスの両方: 最適化されたネットワーク構成。SoftLayer® によって割り当てられたプライマリーのパブリック IP アドレスとプライベート IP アドレスのみが ESXi サーバーに接続されます。 管理トラフィック用にポータブル・プライベート・アドレスがデプロイされることはなくなりました。
* Cloud Foundation インスタンスのみ: Windows AD SSO (Active Directory シングル・サインオン) およびドメイン・ネーム・システム (DNS) サーバー

**注**: これらの変更により、現行リリースで V1.4 より前の既存のインスタンスを使用することはできません。 既存のインスタンスの構成を再利用するには、それらを現行バージョンにアップグレードする必要があります。 詳しくは、[V1.4 より前のインスタンスのアップグレード](movinginstances.html)を参照してください。

## Cloud Foundation インスタンスのマルチサイト構成のサポート

以前のリリースと同様に、単一の Cloud Foundation インスタンスをデプロイすることも、プライマリー・インスタンスに接続されたセカンダリー・インスタンスをデプロイすることもできます。 マルチサイト構成モデルでは、ハブ・アンド・スポーク・トポロジーでプライマリー・サイトと最大 7 つのセカンダリー・サイトを使用します。

詳しくは、[Cloud Foundation インスタンスのマルチサイト構成](../sddc/sd_multisite.html)を参照してください。

## Zerto 災害復旧のデプロイメントの機能拡張

* Cloud Foundation インスタンスの Zerto 災害復旧のデプロイメントが、サポート・チケットによって処理されるのではなく、自動化されました。 プライベート・ポータブル・サブネット、Windows VSI (仮想サービス・インスタンス)、Zerto ライセンス料など、すべての Zerto コンポーネントが見積もりコストにリストされるので、注文前に確認することができます。
* vCenter Server インスタンスについては、前のリリースと同様に、サポート・チケットを使用して Zerto 災害復旧のデプロイメントを行います。 ただし、NSX Edge とパブリック・ポータブル・サブネットは、基本デプロイメントに含まれるようになったため、不要になりました。 プライベート・ポータブル・サブネット、Windows VSI (仮想サービス・インスタンス)、および Zerto ライセンスの料金は引き続き適用されます。

詳しくは、[Zerto 災害復旧](../services/addingzertodr.html)を参照してください。

## インスタンスの注文プロセス

インスタンスの注文プロセスが非常にシンプルになりました。

* Cloud Foundation インスタンスと vCenter Server インスタンスのどちらも、注文プロセス中に SoftLayer 資格情報ページが表示されなくなりました。 「設定」ページで定義した SoftLayer 資格情報がデフォルトで使用され、要件を満たしていない場合にのみ、資格情報を更新するプロンプトが表示されます。
* また、vCenter Server インスタンスの場合は、**「ハードウェア」**タイプの**「ラージ」**オプションと**「アップリンク・ポート速度」**の**「10 Gbps デュアル」**設定のみが表示されるようになり、注文時に指定する設定の数が減りました。

詳しくは、以下を参照してください。

* [Cloud Foundation インスタンスの注文](../sddc/sd_orderinginstance.html)
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)

## インスタンス管理

インスタンス管理プロセスの新機能と改善点は以下のとおりです。

* Cloud Foundation インスタンスの場合、インスタンスの詳細ページでさまざまなインスタンスのコンポーネントのユーザー名とパスワードを表示できます。 詳しくは、[Cloud Foundation インスタンスの表示](../sddc/sd_viewinginstances.html)を参照してください。
* vCenter Server インスタンスの場合は、コンソールから直接、IBM コンポーネントのソフトウェアの更新とパッチをインストールできます。 詳しくは、[vCenter Server インスタンスへの更新とパッチの適用](../vcenter/vc_applyingupdates.html)を参照してください。

## コンソール通知

コンソール通知を**「設定」**ページで構成できるようになりました。 デフォルトでは、この設定が有効になっています。つまり、すべてのイベントに関する通知がコンソールに表示されます。 また、**「設定」**ページでコンソールの通知を無効にすることもできます。

詳しくは、以下を参照してください。

* [ユーザー・アカウントと設定](useraccount.html)
* [通知](notifications.html)
