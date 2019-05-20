---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select インスタンスの削除
{: #np_deletinginstance}

NetApp ONTAP Select インスタンスを削除すると、以下のコンポーネントが順次解放されます。
1. デプロイ済みの NetApp ONTAP Select クラスター化 VM (仮想マシン) と NetApp ONTAP Select Deploy VM
2. サポートとサービスの料金
3. VMware 製品ライセンス
4. ESXi サーバー
5. サブネット
6. VLAN

リソースに依存関係があるため、インスタンスのコンポーネントは、インスタンスを削除してもすぐには解放されません。 例えば、サブネットと VLAN は、{{site.data.keyword.cloud}} インフラストラクチャーによって ESXi サーバーが完全にレクラメーション処理されるまで削除できませんが、この処理は {{site.data.keyword.cloud_notm}} 請求処理サイクルの終わりに行われます。 請求処理サイクル (標準的には 30 日) の終わりに、サブネットと VLAN はレクラメーション処理され、インスタンスの削除が完了します。

削除対象のインスタンスに関する請求は、請求処理サイクルの終わりまで行われます。
{:note}

## 「リソース」ページからインスタンスを削除する手順
{: #np_deletinginstance-procedure1}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「NetApp ONTAP Select インスタンス」**の表で、削除するインスタンスを見つけます。
3. **「アクション」**列で削除アイコンをクリックします。
   インスタンスの状況が**「削除中」**に変わります。 インスタンスが正常に削除され、状況が**「削除済み」**に変更されたら、**「アクション」**列で削除アイコンを再度クリックします。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンス・レコードを削除する場合は、以下の手順を実行します。
   1. **「アクション」**列で削除アイコンをもう一度クリックします。
   2. **「インスタンスの削除」**ウィンドウで**「OK」**をクリックします。

## インスタンスの詳細ページからインスタンスを削除する手順
{: #np_deletinginstance-procedure2}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「NetApp ONTAP Select インスタンス」**テーブルで、削除するインスタンスをクリックします。
3. **NetApp コンソール**の横にあるオーバーフロー・メニュー・アイコンをクリックしてから、**「インスタンスの削除」**をクリックします。
   インスタンスの状況が**「削除中」**に変わります。 インスタンスが正常に削除されると、インスタンスのコンポーネントが解放され、インスタンスの状況が**「削除済み」**に変わります。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンス・レコードを削除する場合は、以下の手順を実行します。
   1. **vCenter コンソール**の横にあるオーバーフロー・メニュー・アイコンをもう一度クリックしてから、**「インスタンスの削除」**をクリックします。
   2. **「インスタンスの削除」**ウィンドウで**「OK」**をクリックします。

## 関連リンク
{: #np_deletinginstance-related}

* [NetApp ONTAP Select インスタンスの注文](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
* [NetApp ONTAP Select インスタンスの表示](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
