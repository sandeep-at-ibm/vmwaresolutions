---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# V2.5 以前の Cloud Foundation インスタンスの IBM Cloud アカウントへのマイグレーション

ご使用の {{site.data.keyword.cloud}} アカウントで V2.5 以降のリリースでデプロイされた VMware Cloud Foundation インスタンスは、ご使用のアカウントに自動的に追加され、{{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) によって管理されます。

V2.4 以前のリリースでデプロイされたインスタンスは、IAM 対応のユーザー管理のために指定された {{site.data.keyword.cloud_notm}} アカウントにマイグレーションできます。

## 始める前に

インスタンスのマイグレーション先となる {{site.data.keyword.cloud_notm}} アカウントが IaaS 専用アカウントでないことを確認します。IaaS 専用アカウントは、{{site.data.keyword.cloud_notm}} アカウントにリンクされていない {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントです。

IaaS 専用アカウントと PaaS アカウントをリンクする方法について詳しくは、[Follow these steps to link your IaaS and PaaS accounts](https://www.ibm.com/blogs/bluemix/2018/03/follow-steps-link-iaas-paas-accounts/) を参照してください。

## インスタンスをマイグレーションする手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. コンソール・バナーのユーザー・アカウント・アイコンをクリックし、**「アカウント」**フィールドをクリックして、インスタンスのマイグレーション先となるユーザー・アカウントを選択します。
3. **「Cloud Foundation インスタンス」**の表で、V2.5 より前のインスタンスを見つけます。
4. **「アクション」**列でオーバーフロー・メニュー・アイコンをクリックし、**「アカウントへのインスタンスのマイグレーション (Migrate Instance to Account)」**をクリックします。
5. **「アカウントへのインスタンスのマイグレーション (Migrate Instance to Account)」**ウィンドウで、インスタンスのマイグレーション先のアカウントを確認してから**「マイグレーション」**をクリックします。

## 結果

1. 指定された {{site.data.keyword.cloud_notm}} アカウントへのインスタンスのマイグレーション要求が受け入れられたことを示すコンソール通知が表示されます。
2. インスタンスのマイグレーションが完了すると、マイグレーション先のアカウントの下の**「デプロイされたインスタンス (Deployed Instances)」**ページにインスタンスが表示されます。 マイグレーション済みのインスタンスは、マイグレーション元のアカウントには表示されなくなります。

### 関連リンク

* [IAM でのユーザー・アクセスの管理](../vmonic/iam.html)
* [サービスとリソースにアクセスするようにユーザーを招待する](../vmonic/iamuserinvite.html)
* [IBM Cloud IAM とは](https://console.stage1.bluemix.net/docs/iam/index.html#iamoverview)
