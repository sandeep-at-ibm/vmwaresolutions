---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation インスタンスの削除

VMware Cloud Foundation インスタンス内で注文したコンポーネントを解放するには、このインスタンスを削除します。

Cloud Foundation インスタンスを削除すると、以下のコンポーネントが順次解放されます。
1. デプロイされたすべてのサービス
2. サポートとサービスの料金
3. VMware 製品ライセンス
4. ESXi サーバー
5. サブネット
6. VLAN

リソースに依存関係があるため、インスタンスのコンポーネントは、インスタンスを削除してもすぐには解放されません。 例えば、サブネットと VLAN は、{{site.data.keyword.cloud}} インフラストラクチャーによって ESXi サーバーが完全にレクラメーション処理されるまで削除できませんが、この処理は {{site.data.keyword.cloud_notm}} 請求処理サイクルの終わりに行われます。 {{site.data.keyword.cloud_notm}} 請求処理サイクル (標準的には 30 日) の終わりに、サブネットと VLAN は削除され、インスタンスの削除が完了します。

削除対象のインスタンスに関する請求は、{{site.data.keyword.cloud_notm}} 請求処理サイクルの終わりまで行われます。
{:note}

## 「デプロイ済みインスタンス」ページからインスタンスを削除する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「Cloud Foundation インスタンス」**の表で、削除するインスタンスを見つけます。
3. **「アクション」**列で削除アイコンをクリックします。
   インスタンスの状況が**「削除中」**に変わります。 インスタンスが正常に削除されると、インスタンスのコンポーネントが解放され、インスタンスの状況が**「削除済み」**に変わります。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンス・レコードを削除する場合は、以下の手順を実行します。
   1. **「アクション」**列で削除アイコンをもう一度クリックします。
   2. **「インスタンスの削除」**ウィンドウで**「OK」**をクリックします。

## インスタンスの詳細ページからインスタンスを削除する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「Cloud Foundation インスタンス」**の表で、削除するインスタンスをクリックします。
3. **vCenter コンソール**の横にあるオーバーフロー・メニュー・アイコンをクリックしてから、**「インスタンスの削除」**をクリックします。
   インスタンスの状況が**「削除中」**に変わります。 インスタンスが正常に削除されると、インスタンスのコンポーネントが解放され、インスタンスの状況が**「削除済み」**に変わります。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンス・レコードを削除する場合は、以下の手順を実行します。
   1. **vCenter コンソール**の横にあるオーバーフロー・メニュー・アイコンをもう一度クリックしてから、**「インスタンスの削除」**をクリックします。
   2. **「インスタンスの削除」**ウィンドウで**「OK」**をクリックします。

### 関連リンク

* [マルチサイト構成での Cloud Foundation インスタンスの削除](sd_deletinginstance_multi.html)
* [Cloud Foundation インスタンスの注文](sd_orderinginstance.html)
* [Cloud Foundation インスタンスの表示](sd_viewinginstances.html)
* [Cloud Foundation インスタンスの容量の拡張と縮小](sd_addingremovingservers.html)
* [マルチサイト構成の削除](sd_deletinginstance_multi.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
