---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: NSX license, upgrade license, Hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle インスタンスの NSX ライセンスのアップグレード
{: #vc_hybrid_upgrade-lic}

インスタンスの VMware NSX ライセンスを新しいエディションにアップグレードできます。 ライセンスのエディションのダウングレードはサポートされていません。

## NSX ライセンスをアップグレードする手順
{: #vc_hybrid_upgrade-lic-nsx}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、NSX ライセンスをアップグレードするインスタンスをクリックします。
3. **「サマリー」**ページで、インスタンスのすべての詳細情報が正しく表示されていることを確認します。 その後、左側のナビゲーション・ペインにある**「インフラストラクチャー」**をクリックし、**「インフラストラクチャー」**ページの詳細情報を確認します。

   詳細が表示されない場合は、ファイアウォールのルールやネットワーキングの問題が原因で IBM CloudDriver 仮想サーバー・インスタンス (VSI) との接続に問題が生じている可能性があります。 問題を解決してから次のステップを続行してください。解決しないと、アップグレードが失敗する可能性があります。

4. 左側のナビゲーション・ペインの**「更新およびパッチ」**をクリックし、**「アップグレード」**をクリックします。 **「NSX License Edition のアップグレード (Upgrade NSX License Edition)」**ウィンドウで、アップグレードするエディションを選択し、**「アップグレード」**をクリックします。

   ライセンスをアップグレードすると、インスタンス上の既存の NSX ライセンスがすべて置き換えられます。 請求サイクルの途中でアップグレードすると、旧ライセンスと新ライセンスの重複により追加料金が発生することがあります。 追加料金を避けるために、請求サイクルの最後にライセンスをアップグレードすることをお勧めします。
   {:note}

## 関連リンク
{: #vc_hybrid_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
