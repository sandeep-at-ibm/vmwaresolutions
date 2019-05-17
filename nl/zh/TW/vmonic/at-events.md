---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-03"

subcollection: vmware-solutions


---

# Activity Tracker 事件
{: #at-events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服務，追蹤使用者及應用程式如何在 {{site.data.keyword.Bluemix_notm}} 中與 {{site.data.keyword.vmwaresolutions_short}} 互動。

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄由使用者起始並且會變更 {{site.data.keyword.Bluemix_notm}} 中服務狀態的活動。如需相關資訊，請參閱[關於 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)。

## Activity Tracker 事件表格
{: #at-events-table}

如需 Activity Tracker 事件表格中直欄的說明，請檢查下表。

表 1. Activity Tracker 事件表格的說明

|直欄| 值類型 |說明              |
|:----------------------|:-----------|:------------|
| Time                  | N/A        | 建立事件的日期和時間。|
| initiator.name        | 字串     | 起始動作之使用者的 IBM ID。|
| target_name           | 字串     | 對其執行動作的資源。|
| target.typeURI        | 字串     | 對其執行動作之目標的「通用唯一 ID (UUID)」。|
| action                | 字串     | 觸發事件的動作。有效值為 `create`、`update` 及 `delete`。|
| outcome               | 字串     | 動作的結果。值為 `success`、`failure` 或 `pending`。|
| reason_reasonCode     | 整數     | 結果的原因碼。|
| initiator_host_address| 字串     | 要求來自的 IP 位址。|

如需相關資訊，請參閱 [Activity Tracker 事件欄位](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event)。

## 追蹤實例管理事件
{: #at-events-instance-mgmt}

當您在 {{site.data.keyword.vmwaresolutions_short}} 中管理使用者帳戶、實例、叢集及服務時，會在 Activity Tracker 中產生事件，並將其傳送至**帳戶網域**。

請檢查下表，以取得產生並傳送管理事件至 Activity Tracker 的動作。

表 2. 產生管理事件之動作的說明

| 動作 |說明              | 結果 |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.user_account.update`    | <ul><li>接收到更新使用者帳戶的要求。</li><li>已回應更新使用者帳戶的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>接收到更新通知的要求。</li><li>已答覆更新通知的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>接收到清除安全資料的要求。</li><li>已答覆清除安全資料的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>接收到移轉至 bss 帳戶的要求。</li><li>已答覆移轉至 bss 帳戶的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>接收到訂購 vCenter Server 實例的要求。</li><li>已答覆訂購 vCenter Server 實例的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>接收到刪除 vCenter Server 實例的要求。</li><li>已答覆刪除 vCenter Server 實例的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>接收到將 ESXi 伺服器新增至 vCenter Server 實例的要求。</li><li>已答覆將 ESXi 伺服器新增至 vCenter Server 實例的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>接收到從 vCenter Server 實例刪除 ESXi 伺服器的要求。</li><li>已答覆從 vCenter Server 實例刪除 ESXi 伺服器的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>接收到為 vCenter Server 實例排定更新的要求。</li><li>已答覆為 vCenter Server 實例排定更新的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>接收到為 vCenter Server 實例建立叢集的要求。</li><li>已答覆為 vCenter Server 實例建立叢集的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>接收到從 vCenter Server 實例刪除叢集的要求。</li> <li>已答覆從 vCenter Server 實例刪除叢集的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>接收到更新 VMware NSX 授權的要求。</li><li>已答覆更新 VMware NSX 授權的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>接收到將 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例的要求。</li><li>已答覆將 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>接收到訂購 vSphere 叢集的要求。</li><li>已答覆訂購 vSphere 叢集的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>接收到更新 vSphere 叢集的要求。</li><li>已答覆更新 vSphere 叢集的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>接收到儲存 vSphere 叢集配置的要求。</li><li>已答覆儲存 vSphere 叢集配置的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>接收到訂購 NetApp ONTAP Select 實例的要求。</li><li>已答覆訂購 NetApp ONTAP Select 實例的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>接收到刪除 NetApp ONTAP Select 實例的要求。</li><li>已答覆刪除 NetApp ONTAP Select 實例的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>接收到更新服務配置的要求。</li><li>已答覆更新服務配置的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>接收到訂購實例服務的要求。</li><li>已答覆訂購實例服務的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>接收到從實例刪除服務的要求。</li><li>已答覆從實例刪除服務的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>接收到將現有 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例的要求。</li><li>已答覆將現有 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.service.deploy` | 執行在實例上部署服務的動作。| `success` |
| `vmware-solutions.service.undeploy` | 執行從實例移除服務的動作。| `success` |

## 追蹤 KMIP for VMware on IBM Cloud 服務的事件
{: #at-events-kmip}

當您管理 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務的金鑰時，會在 Activity Tracker 中產生事件，並將其傳送至**帳戶網域**。

請檢查下表，以取得產生並傳送 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務事件的動作。

表 3. 產生 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務事件之動作的說明

| 動作 |說明       | 結果 |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>接收到建立金鑰的要求。</li><li>已答覆建立金鑰的要求。</li></ul> | <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>接收到取得金鑰內容的要求。</li><li>已答覆取得金鑰內容的要求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>接收到取得金鑰屬性的要求。</li><li>已答覆取得金鑰屬性的要求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>接收到啟動金鑰的要求。</li><li>已答覆啟動金鑰的要求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>接收到撤銷金鑰的要求。</li><li>已答覆撤銷金鑰的要求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>接收到毀損金鑰的要求。</li><li>已答覆毀損金鑰的要求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>接收到尋找 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務版本的要求。</li><li>已答覆尋找 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務版本的要求。</li></ul> |  <ul><li>`pending`</li><li>`success` 或 `failure`</li></ul> |

## 事件的檢視位置
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} 事件位於 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**中，而此帳戶網域位於產生事件的 {{site.data.keyword.Bluemix_notm}} 地區中。

## 相關鏈結
{: #at-events-related}

* [佈建 Activity Tracker](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [導覽至 {{site.data.keyword.cloud_notm}} 主控台中的 Activity Tracker 儀表板](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
