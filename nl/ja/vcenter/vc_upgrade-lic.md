---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-24"

keywords: NSX license upgrade, upgrade license hybridity, hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server インスタンスのライセンスのアップグレード
{: #vc_upgrade-lic}

V2.1 以降のインスタンスの NSX ライセンスをアップグレードできます。

## NSX ライセンスをアップグレードする手順
{: #vc_upgrade-lic-nsx}

この手順は、V2.1 以降でデプロイされたインスタンスに適用されます。 V2.0 以前でデプロイされたインスタンスの場合は、手動で NSX ライセンスをアップグレードする必要があります。

インスタンスの NSX ライセンスをその後のエディションにアップグレードできます。 ライセンス・エディションのダウングレードはサポートされていません。

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、NSX ライセンスをアップグレードするインスタンスをクリックします。
3. **「サマリー」**ページで、インスタンスのすべての詳細情報が正しく表示されていることを確認します。 その後、左側のナビゲーション・ペインにある**「インフラストラクチャー」**をクリックし、**「インフラストラクチャー」**ページの詳細情報を確認します。

   詳細が表示されない場合は、ファイアウォールのルールやネットワーキングの問題が原因で IBM CloudDriver 仮想サーバー・インスタンス (VSI) との接続に問題が生じている可能性があります。 問題を解決してから次のステップに進んでください。そうしないと、アップグレードが失敗する可能性があります。

4. 左側のナビゲーション・ペインの**「更新およびパッチ」**をクリックし、**「アップグレード」**をクリックします。 **「NSX License Edition のアップグレード (Upgrade NSX License Edition)」**ウィンドウで、アップグレード先のエディションを選択し、**「アップグレード」**をクリックします。

   ライセンスをアップグレードすると、インスタンス上の既存の NSX ライセンスがすべて置き換えられます。 請求サイクルの途中でアップグレードすると、旧ライセンスと新ライセンスの重複により追加料金が発生することがあります。 追加料金を避けるために、請求サイクルの最後にライセンスをアップグレードすることをお勧めします。
   {:note}

## 関連リンク
{: #vc_upgrade-lic-related}

* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
