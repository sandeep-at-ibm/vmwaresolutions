---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server インスタンスのライセンスのアップグレード
{: #vc_upgrade-lic}

VMware vCenter Server インスタンスを vCenter Server with Hybridity Bundle にアップグレードできるのは、V2.3 以降のインスタンスのみです。

IBM ビジネス・パートナーのユーザーには、Hybridity Bundle にアップグレードするためのオプションは提供されません。
{:note}

## Hybridity Bundle にライセンスをアップグレードする前に
{: #vc_upgrade-lic-upgrade-prereq}

Hybridity Bundle へのアップグレード時に実行される以下のアクションを確認してください。

* vCenter Server インスタンスに VMware NSX Base エディションがインストールされている場合は、NSX ライセンスが NSX Advanced エディションに自動的にアップグレードされます。
* vCenter Server インスタンスに NFS ストレージがある場合、VMware vSAN ストレージについては課金されません。ただし、Hybridity Bundle に含まれている vSAN ライセンスについては課金されます。

## Hybridity Bundle にアップグレードする手順 (V2.3 以降のインスタンス)
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、Hybridity Bundle にアップグレードするインスタンスをクリックします。
3. **「サマリー」**ページで、インスタンスのすべての詳細情報が正しく表示されていることを確認します。 その後、左側のナビゲーション・ペインにある**「インフラストラクチャー」**をクリックし、**「インフラストラクチャー」**ページの詳細情報を確認します。

   詳細が表示されない場合は、ファイアウォールのルールや他のネットワーキングの問題が原因で IBM CloudDriver VSI との接続に問題が生じている可能性があります。 問題を解決してから次のステップを続行してください。解決しないと、アップグレードが失敗する可能性があります。

4. 左側のナビゲーション・ペインの**「更新およびパッチ」**をクリックします。
5. Hybridity Bundle ライセンス・アップグレードを適用するには、**「ライセンス・アップグレード」**テーブルで、**「アクション」**列の**「アップグレード」**をクリックします。見積もりコストを確認し、**「アップグレード」**をクリックします。
6. オプションで、VMware HCX on {{site.data.keyword.cloud_notm}} サービスをデプロイできます。 **「ライセンス・アップグレード**テーブルで Hybridity Bundle を有効にした場合は、以下の手順を実行します。
  1. **「ライセンス・アップグレード」**テーブルで、**「アクション」**列の**「HCX on {{site.data.keyword.cloud_notm}} のデプロイ」**をクリックします。
  2. **「HCX on {{site.data.keyword.cloud_notm}}」**カードまでスクロールし、**「サービスの選択」**をクリックします。
  3. スクロールダウンしてサービスに必要な設定を指定し、**「次へ」**をクリックします。
  4. サービスに適用される使用条件を確認し、見積もりコストを確認して、**「注文」**をクリックします。

## NSX ライセンスをアップグレードする手順 (V2.1 以降のインスタンス)
{: #vc_upgrade-lic-nsx}

この手順は、V2.1 以降でデプロイされたインスタンスに適用されます。 V2.0 以前でデプロイされたインスタンスの場合は、NSX ライセンスを手動でアップグレードする必要があります。

インスタンスの NSX ライセンスを新しいエディションにアップグレードできます。ライセンス・エディションのダウングレードはサポートされていません。

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、NSX ライセンスをアップグレードするインスタンスをクリックします。
3. **「サマリー」**ページで、インスタンスのすべての詳細情報が正しく表示されていることを確認します。 その後、左側のナビゲーション・ペインにある**「インフラストラクチャー」**をクリックし、**「インフラストラクチャー」**ページの詳細情報を確認します。

   詳細が表示されない場合は、ファイアウォールのルールやネットワーキングの問題が原因で IBM CloudDriver 仮想サーバー・インスタンス (VSI) との接続に問題が生じている可能性があります。 問題を解決してから次のステップを続行してください。解決しないと、アップグレードが失敗する可能性があります。

4. 左側のナビゲーション・ペインの**「更新およびパッチ」**をクリックして、**「アップグレード」**をクリックします。**「NSX License Edition のアップグレード (Upgrade NSX License Edition)」**ウィンドウで、アップグレードするエディションを選択し、**「アップグレード」**をクリックします。

   ライセンスをアップグレードすると、インスタンス上の既存の NSX ライセンスがすべて置き換えられます。 請求サイクルの途中でアップグレードすると、旧ライセンスと新ライセンスの重複により追加料金が発生することがあります。 追加料金を避けるために、請求サイクルの最後にライセンスをアップグレードすることをお勧めします。
   {:note}

## 関連リンク
{: #vc_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
