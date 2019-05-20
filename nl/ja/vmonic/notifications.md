---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

# システム通知の管理
{: #notifications}

システムまたはユーザーによる操作の状況の通知を確認できます。 この情報を使用して、発生する可能性のある問題を調査することもできます。

## 通知の表示
{: #notifications-view}

1. {{site.data.keyword.vmwaresolutions_full}} コンソールで、左側のナビゲーション・ペインの**「通知」**をクリックします。
2. すべての通知に関するサマリーを表示します。

   表 1. 通知履歴

    <table>
      <tr>
        <th>列</th>
        <th>説明</th>
      </tr>
      <tr>
        <td>重大度</td>
        <td>通知で報告されるイベントの重大度。
          <dl class="dl">
          <dt class="dt dlterm">Critical</dt>
          <dd class="dd">重大なイベントによってシステム全体またはサービス全体が影響を受けている可能性があります。</dd>
          <dt class="dt dlterm">Error</dt>
          <dd class="dd">操作時にエラー・イベントが発生しました。管理者かユーザーの介入が必要になっている可能性があります。</dd>
          <dt class="dt dlterm">警告</dt>
          <dd class="dd">コンポーネントに障害が発生したか、正常に機能しません。 しかし、この障害でコンポーネントの進行中の処理が中断されることはありません。</dd>
            <dt class="dt dlterm">情報</dt>
            <dd class="dd">システムまたはユーザーによる操作が完了しました。 情報の通知を報告する代表的なイベントを次に示します。
              <ul class="ul">
                <li class="li">サービスがインストールされた。</li>
                <li class="li">サービスがアップグレードされた。</li>
                <li class="li">サービスが削除された。</li>
                <li class="li">追加された ESXi サーバーのすべてのサービスが再構成された。</li>
                <li class="li">削除された ESXi サーバーのすべてのサービスが再構成された。</li>
              </ul>
            </dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>タイプ</td>
         <td>イベントが報告されたコンポーネントのタイプ:<ul><li>vCenter Server インスタンス</li><li>サービス</li><li>システム</li></ul></td>
       </tr>
       <tr>
         <td>リソース</td>
         <td>通知を送信したインスタンスまたはサービスの名前。</td>
       </tr>
       <tr>
         <td>説明</td>
         <td>通知の簡単な説明。</td>
       </tr>
       <tr>
         <td>日付</td>
         <td>通知が送信された日時。</td>
       </tr>
    </table>                                       

3. 通知の行をクリックすると、通知の詳細が表示されます。

## 通知のフィルタリング
{: #notifications-filter}

デフォルトでは、すべての未読の通知が表示されます。 状況、重大度、タイプで通知をフィルタリングできます。 通知をフィルタリングするには、**「Status」**、**「Severity」**、**「Type」**のリストで、表示する項目のチェック・ボックスだけを選択します。

## 関連リンク
{: #notifications-related}

* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [ユーザー・アカウントと設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
