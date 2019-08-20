---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight ライセンスの管理
{: #caveonix_license_managing}

スタンドアロンで使用するために注文した Caveonix RiskForesight のライセンスを表示したり、そのメモを編集したり、削除したりできます。

## Caveonix RiskForesight ライセンスを表示する手順
{: #caveonix_license_managing_procedure-view}

1. 左側のナビゲーション・ペインの**「リソース」**をクリックし、**「Caveonix RiskForesight ライセンス (Caveonix RiskForesight Licenses)」**テーブルまでスクロールダウンします。

   | 項目 | 説明 |
   |:-----|:------------|
   | 名前 | ライセンスの名前。 |
   | 作成時間 | ライセンスが作成された日時。 |
   | 状況 | ライセンスの状況: <br>変更中: ライセンスは作成されています。<br>インストール済み: ライセンスは使用できます。<br>削除中: ライセンスは削除中です。 |
   {: caption="表 1. Caveonix RiskForesight ライセンス項目の説明" caption-side="top"}

2. 特定のライセンスの詳細を表示するには、そのライセンスをクリックします。

## Caveonix RiskForesight ライセンスのメモを編集する手順
{: #caveonix_license_managing_procedure-edit}

1. 左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「Caveonix RiskForesight ライセンス (Caveonix RiskForesight Licenses)」**テーブルまでスクロールダウンして、メモを編集するライセンスをクリックします。
3. ライセンスの詳細ページで、ライセンスのメモを編集してから**「確認」**をクリックします。

## ライセンス日付の表示に関する既知の問題
{: #caveonix_license_considerations-date}

Mozilla Firefox をブラウザーとして使用している場合、開始日および終了日が、Caveonix RiskForesight コンソールで値なしで表示される可能性があります。 この問題を解決するには、ライセンス情報を Google Chrome などの別のブラウザーで表示してください。

この問題が発生し、使用できるブラウザーが Firefox だけである場合は、[Caveonix Support](https://www.caveonix.com/support/){:external} にお問い合わせください。
{:note}

## Caveonix RiskForesight ライセンスを削除する手順
{: #caveonix_license_managing_procedure-delete}

Caveonix RiskForesight ライセンスを削除しても、vCenter Server インスタンスにインストールされている Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスは削除されません。 サービスを削除するには、{{site.data.keyword.vmwaresolutions_short}} コンソールでその操作を行う必要があります。詳しくは、[vCenter Server インスタンス用サービスを削除する手順](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure)を参照してください。
{:note:}

1. 左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「Caveonix RiskForesight ライセンス (Caveonix RiskForesight Licenses)」**テーブルまでスクロールダウンして、削除するライセンスを見つけます。
3. **「アクション」**列で削除アイコンをクリックします。
4. **「ライセンスの削除 (Delete License)」**ウィンドウで**「OK」**をクリックします。
   ライセンスの状況が**「削除中」**に変更されます。 ライセンスの削除が完了すると、そのライセンスは**「Caveonix RiskForesight ライセンス (Caveonix RiskForesight Licenses)」**テーブルに表示されなくなります。

## 関連リンク
{: #caveonix_license_managing-related}

* [Caveonix RiskForesight の概要]()
* [Caveonix RiskForesight ライセンスの注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)
