---

copyright:

  years:  2016, 2018

lastupdated: "2017-07-05"

---

# V1.7 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのその他のヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## VMware Cloud Foundation インスタンスの更新

この更新では、以下のアップグレードと機能改善が適用されます。
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* IBM CloudDriver コンポーネントの安定性の向上
* (Intel「Haswell」2690-V3 プロセッサーをベースとする) EVC モードが、アップグレード時に V3 サーバー上の既存の VMware デプロイメントで有効になります。

  **注**: V4 サーバーでは、EVC モードは、既存のデプロイメントでも新規のデプロイメントでも有効になりません。

* 5 月 22 日より前にデプロイされたために V3 サーバーを使用している VMware Cloud Foundation デプロイメントで、新規ノードをインスタンスに追加すると V4 サーバーが注文されます。 これらのサーバーのメモリーは 256 GB です。512 GB のメモリーが必要な場合は、サーバーを追加した後、サポート・チケットをオープンして、512 GB のメモリーへのサーバー・アップグレードを要求してください。 IBM サポートへの問い合わせについては、[IBM サポートへのお問い合わせ](trbl_support.html)を参照してください。

コンポーネントについて詳しくは、[Cloud Foundation インスタンスの技術仕様](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)を参照してください。

### 更新処理の要件

Cloud Foundation インスタンスのデプロイメントの複雑さと、マルチサイト構成かどうかに応じて、更新処理ではコンソールの**「更新およびパッチ」**タブに表示される一連の手順を実行する必要があります。 詳しくは、[Cloud Foundation インスタンスへの更新の適用](../sddc/sd_applyingupdates.html#applying-updates-to-cloud-foundation-instances)を参照してください。

## VMware vCenter Server インスタンスの更新

### クラスター・サポート

V1.7 リリース以降、vCenter Server インスタンスではクラスターを使用して ESXi サーバーを管理できるので、リソース管理と可用性が向上します。 インスタンスの注文時に構成した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。 インスタンスの詳細ページに新しく導入された**「インフラストラクチャー」**タブで、クラスターの詳細を表示したり、最大 5 つのクラスターをインスタンスに追加したりできます。 インスタンスの容量を拡張または縮小する場合は、ESXi サーバーを追加または削除するクラスターを選択できます。 詳しくは、[vCenter Server インスタンスのクラスターの追加と表示](../vcenter/vc_addingviewingclusters.html)を参照してください。

### Zerto 災害復旧のデプロイメントの機能拡張

Zerto 災害復旧のデプロイメントが、サポート・チケットによって処理されるのではなく、自動化されました。 プライベート・ポータブル・サブネット、Windows VSI (仮想サービス・インスタンス)、Zerto ライセンス料など、すべての Zerto コンポーネントが見積もりコストにリストされるので、注文前に確認することができます。 詳しくは、[Zerto 災害復旧のデプロイメント・プロセス](../services/addingzertodr.html)を参照してください。

### NSX ライセンス・アップグレード機能

vCenter Server インスタンスの**「サマリー」**タブから NSX ライセンス・エディションをアップグレードできます。 ライセンスをアップグレードすると、アカウント内の既存の NSX SoftLayer ライセンスがすべて新しいライセンスに置き換えられます。 詳しくは、[vCenter Server インスタンスの表示](../vcenter/vc_viewinginstances.html)を参照してください。

## 使いやすさの向上

ユーザー・インターフェース全体が以下のように改善されました。
* Cloud Foundation インスタンスの詳細ページの**「プロパティー」**タブの名前が**「サマリー」**に変更されました。 このタブで、インスタンスの詳細、インスタンス関連コンポーネントのアクセス情報、インスタンスのデプロイメント履歴を確認できるようになりました。
* Cloud Foundation インスタンスの詳細ページに新しく**「インフラストラクチャー」**タブが導入されました。 このタブで ESXi サーバーを表示、追加、または削除できます。
* {{site.data.keyword.vmwaresolutions_short}} の資料の形式が一新され、Bluemix 資料セットとともに、Bluemix カタログに完全に統合されました。 以下のいずれかの方法で資料にアクセスできます。
  * {{site.data.keyword.vmwaresolutions_short}} から、バナーの左側にある**「資料」**をクリックします。
  * Bluemix 資料カタログを、**「計算およびサービス」**セクションまでスクロールダウンし、**「{{site.data.keyword.vmwaresolutions_short}}」**をクリックします。
