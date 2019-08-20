---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Activity Tracker 事件
{: #at-events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服務可追蹤使用者和應用程式如何與 {{site.data.keyword.cloud_notm}} 中的 {{site.data.keyword.vmwaresolutions_short}} 互動。

{{site.data.keyword.at_full_notm}} 會記錄由使用者起始並且會變更 {{site.data.keyword.cloud_notm}} 中服務狀態的活動。您可以使用此服務來調查異常活動和關鍵動作，並符合法規審核需求。此外，您還可以在動作發生時收到警示。收集的事件符合 Cloud Auditing Data Federation (CADF) 標準。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)。

## 追蹤實例管理事件
{: #at-events-instance-mgmt}

在 {{site.data.keyword.vmwaresolutions_short}} 中管理使用者帳戶、實例、叢集和服務時，會產生事件並將其傳送到廣域網域，或者傳送到佈建服務的位置中的服務實例。如需相關資訊，請參閱[監視廣域事件和以位置為基礎的事件](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type)。

下表提供產生並傳送管理事件至 Activity Tracker 的動作。

| 動作 |說明       |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` |將更新帳戶的基礎架構 API 金鑰。|
| `vmware-solutions.account-notification.update` | 將更新帳戶的通知設定。|
| `vmware-solutions.instance-secure-data.wipe` | 將抹除實例安全資料。|
| `vmware-solutions.instance-bss-account.migrate` |	實例會移轉到 BSS 帳戶。|
| `vmware-solutions.vcs.create` |將建立 vCenter Server 實例。|
| `vmware-solutions.vcs.delete`                |將刪除 vCenter Server 實例。|
| `vmware-solutions.vcs-host.add` |主機將新增到 vCenter Server 實例。|
| `vmware-solutions.vcs-host.remove` |主機將從 vCenter Server 實例中移除。|
| `vmware-solutions.vcs.update`	| 將更新 vCenter Server 實例。|
| `vmware-solutions.vcs-cluster.create`	| 將為 vCenter Server 實例建立叢集。|
| `vmware-solutions.vcs-cluster.delete`	| 將為 vCenter Server 實例刪除叢集。|
| `vmware-solutions.vcs-nsx-license.update`	| 將為 vCenter Server 實例更新 NSX 授權。|
| `vmware-solutions.vcs-nfs-storage.add`	| NFS 儲存空間將新增到 vCenter Server 實例。|
| `vmware-solutions.vcs-nfs-storage.remove`	| NFS 儲存空間將從 vCenter Server 實例中移除。|
| `vmware-solutions.vcs-plan.update`	| 將更新 vCenter Server 實例的方案。|
| `vmware-solutions.vss.create`	|將建立 vSphere 實例。|
| `vmware-solutions.vss.update`	| 將更新 vSphere 實例。|
| `vmware-solutions.vss-template.remove` |將移除 vSphere 範本。|
| `vmware-solutions.service.create`	|將建立服務。|
| `vmware-solutions.service.delete`	|將刪除服務。|
{: caption="表 1. 產生管理事件之動作的說明" caption-side="top"}

## 追蹤 KMIP for VMware on IBM Cloud 服務的事件
{: #at-events-kmip}

管理 KMIP for VMware on {{site.data.keyword.cloud_notm}} 的金鑰時，會產生事件並將其傳送到廣域網域，或者傳送到佈建服務的位置中的服務實例。如需相關資訊，請參閱[監視廣域事件和以位置為基礎的事件](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type)。

下表提供產生並傳送 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務事件的動作。

| 動作 |說明       |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` |將建立 KMIP 金鑰。|
| `vmware-solutions.kmip-key.retrieve` |將擷取 KMIP 金鑰。|
| `vmware-solutions.kmip-key-attributes.retrieve` |將擷取 KMIP 金鑰的屬性。|
| `vmware-solutions.kmip-key.activate` |將啟動 KMIP 金鑰。|
| `vmware-solutions.kmip-key.revoke` |將撤銷 KMIP 金鑰。|
| `vmware-solutions.kmip-key.destroy` |將破壞 KMIP 金鑰。|
{: caption="表 2. 產生 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務事件之動作的說明" caption-side="top"}

## 事件的檢視位置
{: #at-events-viewing}

事件在**法蘭克福**位置可用。

每個位置只有 1 個 {{site.data.keyword.at_full_notm}} 實例。若要檢視事件，您必須存取 **EU-DE** 位置中 {{site.data.keyword.at_full_notm}} 服務的 Web 使用者介面。如需相關資訊，請參閱[透過 IBM Cloud 使用者介面啟動 Web 使用者介面](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2)。

## 相關鏈結
{: #at-events-related}

* [佈建實例](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [導覽至 Web 使用者介面](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
