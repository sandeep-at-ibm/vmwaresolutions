---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-08"

---

# IBM Cloud アカウントへの V2.5 より前の vCenter Server インスタンスのマイグレーション

V2.5 以降のリリースで {{site.data.keyword.cloud}} アカウントにデプロイされた VMware vCenter Server インスタンスは、自動的にアカウントに追加されて、{{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) によって管理されます。

V2.4 以前のリリースでデプロイされたインスタンスの場合、それらを IAM 対応のユーザー管理のために指定の {{site.data.keyword.cloud_notm}} アカウントにマイグレーションできます。


## 手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. コンソールの右上隅でアバターをクリックし、**「アカウント」**フィールドをクリックして、インスタンスのマイグレーション先となるユーザー・アカウントを選択します。
3. **「vCenter Server インスタンス」**の表で、V2.5 より前のインスタンスを見つけます。
4. **「アクション」**列でオーバーフロー・メニュー・アイコンをクリックし、**「アカウントへのインスタンスのマイグレーション (Migrate Instance to Account)」**をクリックします。
5. **「アカウントへのインスタンスのマイグレーション (Migrate Instance to Account)」**ウィンドウで、インスタンスのマイグレーション先のアカウントを確認してから**「マイグレーション」**をクリックします。

## 結果

1. 指定された {{site.data.keyword.cloud_notm}} アカウントへのインスタンスのマイグレーション要求が受け入れられたことを示すコンソール通知が表示されます。
2. インスタンスのマイグレーションが完了すると、マイグレーション先のアカウントの下の**「デプロイされたインスタンス (Deployed Instances)」**ページにインスタンスが表示されます。 マイグレーション済みのインスタンスは、マイグレーション元のアカウントには表示されなくなります。

### 関連リンク

* [IAM でのユーザー・アクセスの管理](../vmonic/iam.html)
* [サービスとリソースにアクセスするようにユーザーを招待する](../vmonic/iamuserinvite.html)
* [IBM Cloud IAM とは](../../../iam/index.html)
