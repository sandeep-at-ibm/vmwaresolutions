---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Object Storage と Veeam の注文と構成
{: #icos_ordering}

Veeam Availability Suite 9.5 アップデート 4 のリリースによって、Veeam が IBM Cloud Object Storage (ICOS) に対応するようになりました。IBM Cloud で Veeam を注文する時に IBM Cloud Object Storage の注文が自動的に処理されることはありませんが、デプロイメント後に追加することが可能です。

IBM Cloud Object Storage を注文するには、以下のタスクを指定の順序で実行します。

## Object Storage インスタンスの作成
{: #icos_ordering-obj}

Object Storage インスタンスを作成するには、[新しいサービス・インスタンスの作成](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-order-storage#creating-a-new-service-instance)を参照してください。 その手順を実行してから、このセクションに戻って以下の作業を続けます。

## バケットの作成
{: #icos_ordering-bucket}

バケットを作成するには、[Create some buckets to store your data](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-getting-started-tutorial#gs-create-buckets) を参照してください。 その手順を実行してから、このセクションに戻って以下の作業を続けます。

## サービス資格情報の作成
{: #icos_ordering-service-cred}

サービス資格情報 (HMAC 資格情報など) を作成するには、[サービス資格情報](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials)を参照してください。 その手順を実行してから、このセクションに戻って以下の作業を続けます。

## スケールアウト・リポジトリーの追加
{: #icos_ordering-scale-repo}

Veeam 内にスケールアウト・リポジトリーを追加するには、[Adding scale-Out repositories](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window} を参照してください。 その手順を実行してから、このセクションに戻って以下の作業を続けます。

## クラウド層の保守と管理
{: #icos_ordering-manage-cloud}

クラウド層の保守と管理については、[Managing capacity tier data](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window} を参照してください。
