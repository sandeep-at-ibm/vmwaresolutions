---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: vCenter Server Hybridity delete instance, delete vCenter Server Hybridity, remove vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle インスタンスの削除
{: #vc_hybrid_deletinginstance}

VMware vCenter Server with Hybridity Bundle インスタンスで注文したコンポーネントを解放するには、インスタンスを削除します。

vCenter Server with Hybridity Bundle インスタンスを削除すると、以下のコンポーネントが順次解放されます。
1. デプロイされたすべてのサービス
2. サポートとサービスの料金
3. VMware 製品ライセンス
4. ESXi サーバー
5. サブネット
6. VLAN

リソースに依存関係があるため、インスタンスのコンポーネントは、インスタンスを削除してもすぐには解放されません。 例えば、{{site.data.keyword.cloud}} インフラストラクチャーの請求サイクルの終わりに、ESXi サーバーが {{site.data.keyword.cloud_notm}} によって完全に回収されるまで、サブネットと VLAN は削除できません。 {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常は 30 日) の最後に、サブネットと VLAN が削除され、インスタンスの削除が完了します。

削除したインスタンスについての {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
{:note}

## 「リソース」ページからインスタンスを削除する手順
{: #vc_hybrid_deletinginstance-procedure1}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、削除するインスタンスを見つけます。
3. **「アクション」**列で削除アイコンをクリックします。
   インスタンスの状況が**「削除中」**に変わります。 インスタンスが正常に削除されると、インスタンスのコンポーネントが解放され、インスタンスの状況が**「削除済み」**に変わります。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンス・レコードを削除する場合は、以下の手順を実行します。
   1. **「アクション」**列で削除アイコンをもう一度クリックします。
   2. **「インスタンスの削除」**ウィンドウで**「OK」**をクリックします。

## インスタンスの詳細ページからインスタンスを削除する手順
{: #vc_hybrid_deletinginstance-procedure2}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、削除するインスタンスをクリックします。
3. **vCenter コンソール**の横にあるオーバーフロー・メニュー・アイコンをクリックしてから、**「インスタンスの削除」**をクリックします。
   インスタンスの状況が**「削除中」**に変わります。 インスタンスが正常に削除されると、インスタンスのコンポーネントが解放され、インスタンスの状況が**「削除済み」**に変わります。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンス・レコードを削除する場合は、以下の手順を実行します。
   1. **vCenter コンソール**の横にあるオーバーフロー・メニュー・アイコンをもう一度クリックしてから、**「インスタンスの削除」**をクリックします。
   2. **「インスタンスの削除」**ウィンドウで**「OK」**をクリックします。

## 関連リンク
{: #vc_hybrid_deletinginstance-related}

* [マルチサイト構成での Hybridity Bundle インスタンスを使用した vCenter Server の削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance_multi)
* [vCenter Server with Hybridity Bundle インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [vCenter Server with Hybridity Bundle インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [仮想サーバーのキャンセル](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
