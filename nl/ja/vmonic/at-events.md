---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-12"

---

# Activity Tracker イベント
{: #at-events}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用すると、ユーザーおよびアプリケーションが {{site.data.keyword.Bluemix_notm}} の {{site.data.keyword.vmwaresolutions_short}} とどのような対話を行っているかを追跡できます。

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.Bluemix_notm}} 内のサービスの状態を変更するユーザー開始アクティビティーを記録します。 詳細については、[{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla) を参照してください。

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
| `vmware-solutions.user_account.update`    | <ul><li>ユーザー・アカウントの更新要求を受信しました。</li><li>ユーザー・アカウントの更新要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>通知の更新要求を受信しました。</li><li>通知の更新要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>セキュア・データのワイプ要求を受信しました。</li><li>セキュア・データのワイプ要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>bss アカウントへのマイグレーション要求を受信しました。</li><li>bss アカウントへのマイグレーション要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcf.delete`                | <ul><li>Cloud Foundation インスタンスの削除要求を受信しました。</li><li>Cloud Foundation インスタンスの削除要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcf.add_hosts`             | <ul><li>Cloud Foundation インスタンスへの ESXi サーバーの追加要求を受信しました。</li><li>Cloud Foundation インスタンスへの ESXi サーバーの追加要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcf.remove_hosts`          | <ul><li>Cloud Foundation インスタンスからの ESXi サーバーの削除要求を受信しました。</li><li>Cloud Foundation インスタンスからの ESXi サーバーの削除要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcf.create_cluster`        | <ul><li>Cloud Foundation インスタンスのクラスターの作成要求を受信しました。</li> <li>Cloud Foundation インスタンスのクラスターの作成要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcf.delete_cluster`        | <ul><li>Cloud Foundation インスタンスからのクラスターの削除要求を受信しました。</li><li>Cloud Foundation インスタンスからのクラスターの削除要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcf.schedule_update`       | <ul><li>Cloud Foundation インスタンスの更新のスケジュール設定要求を受信しました。</li><li>Cloud Foundation インスタンスの更新のスケジュール設定要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>vCenter Server インスタンスの注文要求を受信しました。</li><li>vCenter Server インスタンスの注文要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>vCenter Server インスタンスの削除要求を受信しました。</li><li>vCenter Server インスタンスの削除要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>vCenter Server インスタンスへの ESXi サーバーの追加要求を受信しました。</li><li>vCenter Server インスタンスへの ESXi サーバーの追加要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>vCenter Server インスタンスからの ESXi サーバーの削除要求を受信しました。</li><li>vCenter Server インスタンスからの ESXi サーバーの削除要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>vCenter Server インスタンスの更新のスケジュール設定要求を受信しました。</li><li>vCenter Server インスタンスの更新のスケジュール設定要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>vCenter Server インスタンスのクラスターの作成要求を受信しました。</li><li>vCenter Server インスタンスのクラスターの作成要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>vCenter Server インスタンスからのクラスターの削除要求を受信しました。</li> <li>vCenter Server インスタンスからのクラスターの削除要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>VMware NSX ライセンスの更新要求を受信しました。</li><li>VMware NSX ライセンスの更新要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>vCenter Server インスタンスから vCenter Server with Hybridity Bundle インスタンスへのアップグレード要求を受信しました。</li><li>vCenter Server インスタンスから vCenter Server with Hybridity Bundle インスタンスへのアップグレード要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>vSphere クラスターの注文要求を受信しました。</li><li>vSphere クラスターの注文要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>vSphere クラスターの更新要求を受信しました。</li><li>vSphere クラスターの更新要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>vSphere クラスターの構成の保存要求を受信しました。</li><li>vSphere クラスターの構成の保存要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>NetApp ONTAP Select インスタンスの注文要求を受信しました。</li><li>NetApp ONTAP Select インスタンスの注文要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>NetApp ONTAP Select インスタンスの削除要求を受信しました。</li><li>NetApp ONTAP Select インスタンスの削除要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>サービスの構成の更新要求を受信しました。</li><li>サービスの構成の更新要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>インスタンスのサービスの注文要求を受信しました。</li><li>インスタンスのサービスの注文要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>インスタンスのサービスの削除要求を受信しました。</li><li>インスタンスのサービスの削除要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>既存の vCenter Server インスタンスから vCenter Server with Hybridity Bundle インスタンスへのアップグレード要求を受信しました。</li><li>既存の vCenter Server インスタンスから vCenter Server with Hybridity Bundle インスタンスへのアップグレード要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.service.deploy` | サービスをインスタンスにデプロイするアクションが実行されました。 | `success` |
| `vmware-solutions.service.undeploy` | インスタンスからサービスを削除するアクションが実行されました。 | `success` |

## KMIP for VMware on IBM Cloud サービスのイベントの追跡
{: #at-events-kmip}

KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスで鍵の管理を行うと、イベントが生成され、Activity Tracker の**アカウント・ドメイン**に送信されます。

次の表に、KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのイベントが生成され、送信されるアクションをまとめます。

表 3. KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのイベントを生成するアクションの説明

| アクション                                      | 説明                               | 結果 |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>鍵の作成要求を受信しました。</li><li>鍵の作成要求に応答しました。</li></ul> | <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>鍵の内容の取得要求を受信しました。</li><li>鍵の内容の取得要求に応答しました。</li></ul> |  <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>鍵の属性の取得要求を受信しました。</li><li>鍵の属性の取得要求に応答しました。</li></ul> |  <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>鍵の活動化要求を受信しました。</li><li>鍵の活動化要求に応答しました。</li></ul> |  <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>鍵の無効化要求を受信しました。</li><li>鍵の無効化要求に応答しました。</li></ul> |  <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>鍵の破棄要求を受信しました。</li><li>鍵の破棄要求に応答しました。</li></ul> |  <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのバージョンの検出要求を受信しました。</li><li>KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのバージョンの検出要求に応答しました。</li></ul> |  <ul><li>`pending`</li><li>`success` または `failure`</li></ul> |

## イベントの表示先
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、イベントが生成された {{site.data.keyword.Bluemix_notm}} 地域で使用可能な {{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**で確認できます。

## 関連リンク
{: #at-events-related}

* [Activity Tracker のプロビジョン](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [{{site.data.keyword.cloud_notm}} コンソールでの Activity Tracker ダッシュボードへのナビゲート](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
