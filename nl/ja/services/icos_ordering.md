---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: IBM Cloud Object Storage, ICOS configuration, order Cloud Object Storage

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

Object Storage インスタンスを作成するには、[新しいサービス・インスタンスの作成](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance)を参照してください。 その手順を実行してから、このセクションに戻って以下の作業を続けます。

## バケットの作成
{: #icos_ordering-bucket}

バケットを作成するには、[データを保存するためのバケットをいくつか作成する](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets)を参照してください。 その手順を実行してから、このセクションに戻って以下の作業を続けます。

## サービス資格情報の作成
{: #icos_ordering-service-cred}

サービス資格情報 (HMAC 資格情報など) を作成するには、[サービス資格情報](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials)を参照してください。 その手順を実行してから、このセクションに戻って以下の作業を続けます。

## スケールアウト・リポジトリーの追加
{: #icos_ordering-scale-repo}

* Veeam サービスのインストールおよび構成の一部として、`IC4V Scale-Out Repository` という名前のスケールアウト・バックアップ・リポジトリーが作成されます。`IC4V Default VM Backup Repository` が、スケールアウト・リポジトリーにエクステントとして追加されます。
* バックアップ・ジョブを作成するときは、`IC4V Default Config Backup Repository` ではなく、`IC4V Scale-Out Repository` をバックアップ・リポジトリーとして選択する必要があります。`IC4V Default Config Backup Repository` は、Veeam 構成バックアップ用です。
* このデフォルト・リポジトリーには、Object Storage タイプのバックアップ・リポジトリーなどをさらに追加することができます。詳しくは、[Adding scale-Out repositories](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window} を参照してください。その手順を実行してから、このセクションに戻って以下の作業を続けます。

## クラウド層の保守と管理
{: #icos_ordering-manage-cloud}

詳しくは、[Managing capacity tier data](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window} を参照してください。

## 関連リンク
{: #icos_ordering-related}

* [Veeam on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [Veeam on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Veeam on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
