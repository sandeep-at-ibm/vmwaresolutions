---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# VMware Federal インスタンスの保護

デプロイした VMware Federal インスタンスを保護する (つまり、そのインスタンスへの継続的なアクセスのために開いた状態になっている管理接続を除去する) には、以下の手順を実行します。

## 始める前に

以下の情報を参照し、デプロイされた VMware Federal インスタンスを保護するとどうなるかを理解してください。

* この手順を実行する前に、お客様の環境に必要な資格情報を記録して保存してください。 保護アクションを呼び出すと、現在の環境のすべての資格情報が {{site.data.keyword.vmwaresolutions_full}} データベースから消去され、取得できなくなります。
* 保護アクションを呼び出すと、インスタンスの完全削除を除くすべての管理機能が無効になります。

## 手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、保護するインスタンスをクリックします。
3. **vCenter コンソール**の右側にあるオーバーフロー・メニュー・アイコンをクリックします。
4. **「インスタンスを保護」**をクリックします。
5. **「OK」**をクリックして、インスタンスを自動化から切り離すことを確認します。

  **注**: この手順を実行する前に、『**始める前に**』セクションにある重要な情報を確認してください。

6. 公開される管理サービス VMware NSX Edge Services Gateway (ESG) をご使用の環境から削除します。オプションで、自動化時にデプロイされるクライアント管理の ESG を削除します。
7. IBM 自動化で使用されるすべてのアカウントのパスワードまたはキーをリセットします。 追加情報については、「[How can I secure my environment to remove access by IBM automation and support?](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/)」を参照してください。

## 結果

インスタンスの状況が**「変更中」**に変わります。

インスタンスが正常に保護されると、インスタンスの状況が**「保護済み」**に変更され、インスタンスのプロパティーとデプロイメント履歴のみが使用可能になります。

### 関連リンク

* [VMware Federal on {{site.data.keyword.cloud_notm}} の概要](vc_fed_overview.html)
* [VMware Federal インスタンスの注文](vc_fed_orderinginstance.html)
* [VMware Federal インスタンスの表示](vc_fed_viewinginstance.html)
* [VMware Federal インスタンスの削除](vc_fed_deletinginstance.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
