---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Zerto on IBM Cloud の削除プロセス

Zerto on {{site.data.keyword.cloud}} サービスの削除プロセスは自動的に行われます。 Zerto on {{site.data.keyword.cloud_notm}} サービスを正しく削除するためには、以下の手順を実行します。

## Zerto on IBM Cloud を削除する方法

1. 左側のナビゲーション・ペインから**「デプロイ済みインスタンス」**をクリックして、サービスを削除する対象となるインスタンスをクリックします。
2. **「サービス」**タブをクリックします。
3. **「インストール済みサービス」**タブで、サービス・カード右上のオーバーフロー・メニュー・アイコンをクリックしてから、**「サービスの削除」**をクリックします。
4. **「サービスの削除」**ウィンドウで、考慮事項または警告が示されているなら、それを確認します。 **「了解」**をクリックします。
5. サービスの削除要求が受け入れられると、サービス状況が**「削除中」**に変更され、以下の削除ステップが実行されます。   
   1. すべての ESXi サーバーにデプロイされていた Zerto Virtual Replication Appliance を削除します。
   2. Zerto Virtual Replication をアンインストールします。
   3. Zerto Virtual Replication がインストールされていた Windows VSI (Virtual Service Instance) を削除します。
   4. {{site.data.keyword.cloud_notm}} インフラストラクチャーへの Zerto Virtual Replication 通信のために注文したプライベート・ポータブル・サブネットを返却します。   
   5. お客様の {{site.data.keyword.cloud_notm}} 請求書から Zerto 災害復旧サービスの料金を削除します。

      **注**: 削除対象の Zerto 災害復旧サービスに関する請求は、請求処理サイクルの終わりまで行われます。

## 結果

サービスの削除が正常に完了すると、E メールで通知され、**「インストール済みサービス」**タブからそのサービス項目が削除されます。

### 関連リンク

* [Zerto on {{site.data.keyword.cloud_notm}} の注文](zerto_ordering.html)
* [Zerto on {{site.data.keyword.cloud_notm}} の管理](managingzertodr.html)
* [Cloud Foundation インスタンス](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server インスタンス](../vcenter/vc_vcenterserveroverview.html)
* [zerto.com Web サイト](https://www.zerto.com){:new_window}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
