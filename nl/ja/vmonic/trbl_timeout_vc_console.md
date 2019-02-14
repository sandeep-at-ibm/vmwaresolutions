---

copyright:

  years:  2016, 2019

lastupdated: "2018-08-16"

---

# VMware vSphere Web Client に接続中にタイムアウトになる

## 問題
vSphere Web Client に接続しようとすると、次のタイムアウト・エラーが表示されることがあります。

`The server at <IP_address> is taking too long to respond.`

## 解決方法
この問題を調査して解決するには、以下の手順を使用します。

1. **「vCenter コンソール」**ボタンにマウスオーバーすると表示されるツールチップの手順を実行したことを確認します。 参考までに、それらの手順も以下にリストします。   
   1. 使用するブラウザー用の Adobe Flash Player プラグインをインストールします。   
   2. {{site.data.keyword.slportal_full}}から VPN パスワードを作成します。    
   3. {{site.data.keyword.cloud_notm}} インフラストラクチャー VPN 資格情報を使用して、データ・センターの VPN ポータルにログインします。    
   4. 次の形式を使用して、PSC (Platform Services Controller) の IP アドレスとホスト名のマッピングを hosts ファイルに追加します。

      ```javascript
      IPAddress              HostName
      ```

2. 表示された IP アドレスをメモします。この後の手順でこの IP アドレスが必要になります。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャー VPN に対するアクセス権限があることを確認します。 {{site.data.keyword.slportal}}で以下の手順を実行します。
   1. **「アカウント」>「VPN アクセス」**をクリックします。
   2. **「VPN アクセス」**列の**「SSL リンク」**をクリックします。
   3. **「ユーザー名の VPN アクセス」**ページで、**「サブネットのアクセス」**オプションを**「手動」**に設定します。
   4. 同じページで、IP アドレスとホスト名のペアに対応するサブネットを見つけます。 詳しくは、**ステップ 2**を参照してください。    

      例えば、インスタンスの IP アドレスが `xx.yyy.zz.15` で、vCenter の IP アドレスが `xx.yyy.zz.10` の場合は、サブネット `xx.yyy.zz.0/26` に対するアクセス権限を付与する必要があります。

   5. そのサブネットに対して**「アクセス権限の付与」**チェック・ボックスを選択して、**「保存」**をクリックします。
