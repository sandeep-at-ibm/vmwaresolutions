---

copyright:

  years:  2016, 2017

lastupdated: "2017-07-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V1.7 のリリース・ノート
{: #relnotes_v17}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## VMware Cloud Foundation インスタンスの更新
{: #relnotes_v17-vcf}

この更新では、以下のアップグレードと機能改善が適用されます。
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* IBM CloudDriver コンポーネントの安定性の向上
* (Intel「Haswell」2690-V3 プロセッサーをベースとする) EVC モードが、アップグレード時に V3 サーバー上の既存の VMware デプロイメントで有効になります。

  V4 サーバーでは、EVC モードは、既存のデプロイメントでも新規のデプロイメントでも有効になりません。
  {:note}

* 5 月 22 日より前にデプロイされたために V3 サーバーを使用している VMware Cloud Foundation デプロイメントで、新規ノードをインスタンスに追加すると V4 サーバーが注文されます。 これらのサーバーのメモリーは 256 GB です。512 GB のメモリーが必要な場合は、サーバーを追加した後、サポート・チケットをオープンして、512 GB のメモリーへのサーバー・アップグレードを要求してください。 IBM サポートへの連絡について詳しくは、[IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)を参照してください。

### 更新処理の要件
{: #relnotes_v17-update-process}

Cloud Foundation インスタンスのデプロイメントの複雑さと、マルチサイト構成かどうかに応じて、更新処理ではコンソールの**「更新およびパッチ」**タブに表示される一連の手順を実行する必要があります。

## VMware vCenter Server インスタンスの更新
{: #relnotes_v17-vcs}

### クラスター・サポート
{: #relnotes_v17-cluster}

V1.7 リリース以降、vCenter Server インスタンスではクラスターを使用して ESXi サーバーを管理できるので、リソース管理と可用性が向上します。 インスタンスの注文時に構成した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。 インスタンスの詳細ページに新しく導入された**「インフラストラクチャー」**タブで、クラスターの詳細を表示したり、最大 5 つのクラスターをインスタンスに追加したりできます。 インスタンスの容量を拡張または縮小する場合は、ESXi サーバーを追加または削除するクラスターを選択できます。 詳しくは、[vCenter Server インスタンスのクラスターの追加と表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)を参照してください。

### Zerto 災害復旧のデプロイメントの機能拡張
{: #relnotes_v17-zerto}

Zerto 災害復旧のデプロイメントが、サポート・チケットによって処理されるのではなく、自動化されました。 プライベート・ポータブル・サブネット、Windows VSI (仮想サービス・インスタンス)、Zerto ライセンス料など、すべての Zerto コンポーネントが見積もりコストにリストされるので、注文前に確認することができます。 詳しくは、[Zerto 災害復旧のデプロイメント・プロセス](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)を参照してください。

### NSX ライセンス・アップグレード機能
{: #relnotes_v17-nsx}

vCenter Server インスタンスの**「サマリー」**タブから NSX ライセンス・エディションをアップグレードできます。 ライセンスをアップグレードすると、アカウント内の既存の NSX SoftLayer ライセンスがすべて新しいライセンスに置き換えられます。 詳しくは、[vCenter Server インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)を参照してください。

## 使いやすさの向上
{: #relnotes_v17-ui}

ユーザー・インターフェース全体が以下のように改善されました。
* Cloud Foundation インスタンスの詳細ページの**「プロパティー」**タブの名前が**「サマリー」**に変更されました。 このタブで、インスタンスの詳細、インスタンス関連コンポーネントのアクセス情報、インスタンスのデプロイメント履歴を確認できるようになりました。
* Cloud Foundation インスタンスの詳細ページに新しく**「インフラストラクチャー」**タブが導入されました。 このタブで ESXi サーバーを表示、追加、または削除できます。
* {{site.data.keyword.vmwaresolutions_short}} の資料の形式が一新され、Bluemix 資料セットとともに、Bluemix カタログに完全に統合されました。 以下のいずれかの方法で資料にアクセスできます。
  * {{site.data.keyword.vmwaresolutions_short}} から、バナーの左側にある**「資料」**をクリックします。
  * Bluemix 資料カタログを、**「計算およびサービス」**セクションまでスクロールダウンし、**「{{site.data.keyword.vmwaresolutions_short}}」**をクリックします。
