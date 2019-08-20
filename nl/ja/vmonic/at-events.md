---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Activity Tracker イベント
{: #at-events}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用すると、ユーザーおよびアプリケーションが {{site.data.keyword.cloud_notm}} の {{site.data.keyword.vmwaresolutions_short}} とどのような対話を行っているかを追跡できます。

{{site.data.keyword.at_full_notm}} は、{{site.data.keyword.cloud_notm}} 内のサービスの状態を変更するユーザー開始アクティビティーを記録します。 このサービスを使用すると、異常なアクティビティーや重要なアクションを調査できます。また、法規制の監査要件にも準拠できます。さらに、アクションの発生時にアラートを受けることも可能です。収集されるイベントは、クラウド監査データ・フェデレーション (CADF) 標準に準拠しています。詳しくは、[{{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) を参照してください。

## インスタンス管理イベントの追跡
{: #at-events-instance-mgmt}

{{site.data.keyword.vmwaresolutions_short}} でユーザー・アカウント、インスタンス、クラスター、サービスの管理を行うと、イベントが生成されて、グローバル・ドメインに送信されるか、サービスがプロビジョンされているロケーションにあるサービス・インスタンスに送信されます。詳しくは、[グローバル・イベントとロケーション・ベースのイベントのモニター](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type)を参照してください。

次の表に記載するアクションにより、管理イベントが生成されて Activity Tracker に送信されます。

| アクション                                   | 説明 |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` | アカウントのインフラストラクチャー API キーが更新されます。 |
| `vmware-solutions.account-notification.update` | アカウントの通知設定が更新されます。 |
| `vmware-solutions.instance-secure-data.wipe` | インスタンス・セキュア・データがワイプされます。 |
| `vmware-solutions.instance-bss-account.migrate` |	インスタンスが BSS アカウントにマイグレーションされます。 |
| `vmware-solutions.vcs.create` | vCenter Server インスタンスが作成されます。 |
| `vmware-solutions.vcs.delete` | vCenter Server インスタンスが削除されます。 |
| `vmware-solutions.vcs-host.add` | ホストが vCenter Server インスタンスに追加されます。 |
| `vmware-solutions.vcs-host.remove` | ホストが vCenter Server インスタンスから削除されます。 |
| `vmware-solutions.vcs.update` | vCenter Server インスタンスが更新されます。 |
| `vmware-solutions.vcs-cluster.create` | クラスターが vCenter Server インスタンス用に作成されます。 |
| `vmware-solutions.vcs-cluster.delete` | vCenter Server インスタンス用のクラスターが削除されます。 |
| `vmware-solutions.vcs-nsx-license.update` | vCenter Server インスタンス用の NSX ライセンスが更新されます。 |
| `vmware-solutions.vcs-nfs-storage.add` | vCenter Server インスタンスに NFS ストレージが追加されます。 |
| `vmware-solutions.vcs-nfs-storage.remove` | vCenter Server インスタンスから NFS ストレージが削除されます。 |
| `vmware-solutions.vcs-plan.update` | vCenter Server インスタンスのプランが更新されます。 |
| `vmware-solutions.vss.create` | vSphere インスタンスが作成されます。 |
| `vmware-solutions.vss.update` | vSphere インスタンスが更新されます。 |
| `vmware-solutions.vss-template.remove` | vSphere テンプレートが削除されます。 |
| `vmware-solutions.service.create` | サービスが作成されます。 |
| `vmware-solutions.service.delete` | サービスが削除されます。 |
{: caption="表 1. 管理イベントを生成するアクションの説明" caption-side="top"}

## KMIP for VMware on IBM Cloud サービスのイベントの追跡
{: #at-events-kmip}

KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスの鍵の管理を行うと、イベントが生成されて、グローバル・ドメインに送信されるか、サービスがプロビジョンされているロケーションにあるサービス・インスタンスに送信されます。詳しくは、[グローバル・イベントとロケーション・ベースのイベントのモニター](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type)を参照してください。

次の表に記載するアクションにより、KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのイベントが生成され、送信されます。

| アクション                                      | 説明                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` | KMIP キーが作成されます。 |
| `vmware-solutions.kmip-key.retrieve` | KMIP キーが取得されます。 |
| `vmware-solutions.kmip-key-attributes.retrieve` | KMIP キーの属性が取得されます。 |
| `vmware-solutions.kmip-key.activate` | KMIP キーがアクティブ化されます。 |
| `vmware-solutions.kmip-key.revoke` | KMIP キーが取り消されます。 |
| `vmware-solutions.kmip-key.destroy` | KMIP キーが破棄されます。 |
{: caption="表 2. KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのイベントを生成するアクションの説明" caption-side="top"}

## イベントの表示先
{: #at-events-viewing}

イベントが使用可能になるロケーションは、**フランクフルト**です。

ロケーションごとの {{site.data.keyword.at_full_notm}} インスタンスの数は 1 つのみです。イベントを表示するには、ロケーション **EU-DE** 内の {{site.data.keyword.at_full_notm}} サービスの Web UI にアクセスする必要があります。詳しくは、[IBM Cloud UI を使用した Web UI の起動](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2)を参照してください。

## 関連リンク
{: #at-events-related}

* [インスタンスのプロビジョニング](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Web UI へのナビゲート](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
