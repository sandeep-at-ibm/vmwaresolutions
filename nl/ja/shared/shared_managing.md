---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 共有リソースの管理
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} Shared は試験的オファリングとして提供されます。
{:note}

お客様は、{{site.data.keyword.vmwaresolutions_short}} オファリングを使用して、仮想データ・センターのライフサイクルを管理します。

以下の機能は、Web UI またはパブリック API のいずれかを使用してサポートされます。
- 仮想データ・センター・インスタンスの表示
- vCloud Management Console へのアクセス
- 仮想データ・センター・インスタンスのサイズ変更
- 仮想データ・センター・インスタンスの削除
- 仮想データ・センター・インスタンスでの VMware サービスの追加および削除 (**将来**)

## 仮想データ・センター・インスタンスの表示
{: #shared_managing-viewing}

1 つのユーザー・アカウントについてプロビジョンされたすべての仮想データ・センター・インスタンスのサマリーを表示するには、以下の手順を実行します。

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. コンソール・バナーのユーザー・アカウント・アイコンをクリックし、**「アカウント」**フィールドをクリックして、インスタンスの確認対象となるユーザー・アカウントを選択します。  
3. **「IBM Cloud VMware Solutions Shared」**の表で、選択されたユーザー・アカウントでプロビジョンされたインスタンスのリストを表示します。

| 項目        | 説明       |  
|:------------- |:------------- |
| 名前 | インスタンスの名前 |
| タイプ | 仮想データ・センターのタイプ |
| ロケーション | インスタンスがホストされている {{site.data.keyword.CloudDataCent_notm}}。 |  
| 作成時間 | インスタンスが作成された日時 |
| 状況 | インスタンスの状況 |

{: caption="表 1. 仮想データ・センター・インスタンスの項目" caption-side="top"}

インスタンスにはさまざまな状況があります。

| 状況        | 説明       |
|:------------- |:------------- |
| 作成中 | インスタンスは作成中です。 |
| 使用可能 | インスタンスは使用可能です。 |
| 変更中 | インスタンスは変更中です。 |
| Deleting | インスタンスは削除中です。 |
| 削除済み | インスタンスは削除されました。 |

{: caption="表 2. 仮想データ・センター・インスタンスの状況の説明" caption-side="top"}

## 仮想データ・センターの詳細を表示する手順
{: #vc_viewinginstances-procedure-view-vdc-details}

インスタンスのプロパティーの詳細を表示するには、次の手順を実行します。

1. **「IBM Cloud VMware Solutions Shared」**テーブルで、インスタンス名をクリックします。
2. **「プロパティー」**の下で、インスタンスの詳細を確認します。

| プロパティー        | 説明       |
|:------------- |:------------- |
| 名前 | インスタンスの名前。 |
| タイプ | 仮想データ・センターのタイプ。 |
| ロケーション | インスタンスがホストされている {{site.data.keyword.CloudDataCent_notm}}。 |
| ID | インスタンスの ID。 |
| 作成時間 | インスタンスが作成された日時。これは請求処理が開始するときでもあります。|
| vCPU | 仮想データ・センターがいつでも使用できる CPU の制限または予約済みのサイズ。|
| RAM | 仮想データ・センターがいつでも使用できるメモリーの制限または予約済みのサイズ。|
| パブリック IP | すべての仮想データ・センターには、vApp や VM をインターネットに接続するために使用できる、5 つのパブリック IP アドレスが付属しています。|

{: caption="表 3. 仮想データ・センターのプロパティー" caption-side="top"}

## vCloud Director Management Console へのアクセス
{: #shared_managing-accessing}

vCloud Director Management Console を使用して仮想データ・センターを管理します。

vCloud Director Management Console への最初のアクセスは、**admin** 資格情報を使用して行われます。**「ロケーション・パスワードのリセット (Reset Location Password)」**リンクを使用して、仮想データ・センターの詳細ページでパスワードを生成します。このアクションにより、いつでも再設定が可能な、最初の複合ランダム・パスワードが生成されます。

{{site.data.keyword.vmwaresolutions_short}} オファリングは、**admin** パスワードを保管しません。パスワードが生成された後に、それを取り込む必要があります。パスワードを失った場合には、新規パスワードを生成する必要があります。

同じロケーションにあるすべての仮想データ・センターは、同じ **admin** パスワードを持ちます。仮想データ・センター・インスタンスでパスワードをリセットすると、同じロケーションにある、すべての仮想データ・センターの vCloud Director Management Console にアクセスするため **admin** パスワードもリセットされます。

最初の **admin** パスワードが生成された後に、詳細ページの右上隅で**「vCloud Director Portal」**ボタンが使用可能になります。**「vCloud Director Portal」**をクリックして vCloud Director Management Console にアクセスします。ログインするには、ユーザー名 **admin** および**「ロケーション・パスワードのリセット (Reset Location Password)」**リンクから取得したパスワードを使用します。

## 仮想データ・センター・インスタンスのサイズ変更
{: #shared_managing-resizing}

仮想データ・センター・インスタンスが**「使用可能」**状態のときはいつでも、仮想データ・センターに割り当てられるリソースの量を変更できます。 

仮想データ・センターの詳細ページで、仮想データ・センター・インスタンスの vCPU または RAM リソースをサイズ変更します。詳細ページで**「リソース」**の横にある鉛筆アイコンをクリックして、vCPU または RAM プロパティーの値を変更します。

最後に、構成および費用の見積もりを確認してから注文を実行します。

  vCPU および RAM リソースを縮小する際にそれらが使用中であると、構成の変更は失敗します。仮想データ・センターのリソースは、現在アクティブなリソースの使用量よりも低いレベルに縮小することができないためです。{:note}

仮想データ・センター・インスタンスは、変更が行われている際には**「変更中」**状態になります。リソースを使用する準備ができると、状況は**「使用可能」**に変わります。

## 仮想データ・センター・インスタンスの削除
{: #shared_managing-deleting}

仮想データ・センター・インスタンスが**「使用可能」**状態のときには、そのインスタンスを削除できます。削除操作は、仮想データ・センターの詳細ページまたは IBM Cloud VMware Solutions Shared Resource テーブルから実行します。

詳細ページからは、詳細ページの右上隅近くにあるオーバーフロー・メニュー・オプションの**「削除」**アイコンをクリックします。その後、インスタンスの削除を確認します。

IBM Cloud VMware Solutions Shared Resource テーブルからは、削除するインスタンスを見つけて、**「アクション」**列にある**「削除」**アイコンをクリックします。その後、インスタンスの削除を確認します。

## 関連リンク
{: #shared_managing-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Shared On-demand の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Shared Reserved の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
