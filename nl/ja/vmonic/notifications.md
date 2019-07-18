---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: notifications console, filter notifications, system notification

subcollection: vmware-solutions


---

# システム通知の管理
{: #notifications}

システムまたはユーザーによる操作の状況の通知を確認できます。 この情報を使用して、発生する可能性のある問題を調査することもできます。

## 通知の表示
{: #notifications-view}

1. {{site.data.keyword.vmwaresolutions_full}} コンソールで、左側のナビゲーション・ペインの**「通知」**をクリックします。
2. すべての通知に関するサマリーを表示します。

| 列 | 説明 |
|:------ |:----------- |
| 重大度 | 通知で報告されるイベントの重大度。<br>**重大**: 重大なイベントによってシステム全体またはサービス全体が影響を受けている可能性があります。<br>**エラー**: 操作時にエラー・イベントが発生しました。管理者またはユーザーの介入が必要である可能性があります。<br>**警告**: コンポーネントに障害が発生したか、コンポーネントが正常に機能しません。しかし、この障害でコンポーネントの進行中の処理が中断されることはありません。<br>**通知**: システムまたはユーザーによる操作が完了しました。情報の通知を報告する代表的なイベントを次に示します。<br>サービスがインストールされた。<br>サービスがアップグレードされた。<br>サービスが削除された。<br>追加された ESXi サーバーのすべてのサービスが再構成された。<br>削除された ESXi サーバーのすべてのサービスが再構成された。 |
| タイプ | イベントが報告されたコンポーネントのタイプ: vCenter Server インスタンス、サービス、システム |
| リソース | 通知を送信したインスタンスまたはサービスの名前。 |
| 説明 | 通知の簡単な説明。 |
| 日付 | 通知が送信された日時。 |
{: caption="表 1. 通知履歴" caption-side="top"}

3. 通知の行をクリックすると、通知の詳細が表示されます。

## 通知のフィルタリング
{: #notifications-filter}

デフォルトでは、すべての未読の通知が表示されます。 状況、重大度、タイプで通知をフィルタリングできます。 通知をフィルタリングするには、**「Status」**、**「Severity」**、**「Type」**のリストで、表示する項目のチェック・ボックスだけを選択します。

## 関連リンク
{: #notifications-related}

* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [ユーザー・アカウントと設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
