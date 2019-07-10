---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-17"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Activity Tracker イベント
{: #at-events}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用すると、ユーザーおよびアプリケーションが {{site.data.keyword.cloud_notm}} の {{site.data.keyword.vmwaresolutions_short}} とどのような対話を行っているかを追跡できます。

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.cloud_notm}} 内のサービスの状態を変更するユーザー開始アクティビティーを記録します。 詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} の紹介](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)を参照してください。

## Activity Tracker イベント・テーブル
{: #at-events-table}

次の表に、Activity Tracker イベント・テーブルの各列の説明をまとめます。

表 1. Activity Tracker イベント・テーブルの説明

| 列                | 値のタイプ | 説明 |
|:----------------------|:-----------|:------------|
| 時刻                  | N/A        | イベントが作成された日時。 |
| initiator.name        | ストリング     | アクションを開始したユーザーの IBMid。 |
| target_name           | ストリング     | アクションの実行ターゲットのリソース。 |
| target.typeURI        | ストリング     | アクションの実行ターゲットの Universally Unique Identifier (UUID)。 |
| アクション (action)                | ストリング     | イベントをトリガーしたアクション。 有効な値は `create`、`update`、および `delete` です。 |
| outcome               | ストリング     | アクションの結果。 値は `success`、`failure`、または `pending` です。 |
| reason_reasonCode     | 整数    | 結果の理由コード。 |
| initiator_host_address| ストリング     | 要求の発行元の IP アドレス。 |

詳しくは、[Activity Tracker イベントのフィールド](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event)を参照してください。

## インスタンス管理イベントの追跡
{: #at-events-instance-mgmt}

{{site.data.keyword.vmwaresolutions_short}} でユーザー・アカウント、インスタンス、クラスター、およびサービスの管理を行うと、イベントが生成され、Activity Tracker の**アカウント・ドメイン**に送信されます。

次の表に、管理イベントが生成され、Activity Tracker に送信されるアクションをまとめます。

表 2. 管理イベントを生成するアクションの説明

| アクション                                   | 説明 | 結果 |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` |	アカウントのインフラストラクチャー API キーが更新されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.account-notification.update` | アカウントの通知設定が更新されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | インスタンス・セキュア・データがワイプされます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	インスタンスが BSS アカウントにマイグレーションされます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.create` |	vCenter Server インスタンスが作成されます。 |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.delete` |	vCenter Server インスタンスが削除されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.add` |	ホストが vCenter Server インスタンスに追加されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.remove` |	ホストが vCenter Server インスタンスから削除されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.update`	| vCenter Server インスタンスが更新されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.create`	| クラスターが vCenter Server インスタンス用に作成されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete`	| vCenter Server インスタンス用のクラスターが削除されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update`	| vCenter Server インスタンス用の NSX ライセンスが更新されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add`	| vCenter Server インスタンス用の Hybridity Bundle がアップグレードされます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove`	| vCenter Server インスタンスから Hybridity Bundle が削除されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add`	| vCenter Server インスタンスに NFS ストレージが追加されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove`	| vCenter Server インスタンスから NFS ストレージが削除されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-plan.update`	| vCenter Server インスタンスのプランが更新されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.create`	| vSphere インスタンスが作成されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.update`	| vSphere インスタンスが更新されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss-template.remove` |	 vSphere テンプレートが削除されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.create`	| サービスが作成されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.delete`	| サービスが削除されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` | Hybridity Bundle が `version` にアップグレードされます。 | `pending`<br>`success`<br>`failure` |

## KMIP for VMware on IBM Cloud サービスのイベントの追跡
{: #at-events-kmip}

KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスで鍵の管理を行うと、イベントが生成され、Activity Tracker の**アカウント・ドメイン**に送信されます。

次の表に、KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのイベントが生成され、送信されるアクションをまとめます。

表 3. KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのイベントを生成するアクションの説明

| アクション                                      | 説明                               | 結果 |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` |	KMIP キーが作成されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` |	KMIP キーが取得されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` |	KMIP キーの属性が取得されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.activate` |	KMIP キーがアクティブ化されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` |	KMIP キーが取り消されます。 | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` |	KMIP キーが破棄されます。 | `pending`<br>`success`<br>`failure` |

## イベントの表示先
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、イベントが生成された {{site.data.keyword.cloud_notm}} 地域で使用可能な {{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**で確認できます。

## 関連リンク
{: #at-events-related}

* [Activity Tracker のプロビジョン](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [{{site.data.keyword.cloud_notm}} コンソールでの Activity Tracker ダッシュボードへのナビゲート](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
