---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-02"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Activity Tracker 事件
{: #at-events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服務可追蹤使用者和應用程式如何與 {{site.data.keyword.cloud_notm}} 中的 {{site.data.keyword.vmwaresolutions_short}} 互動。

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄由使用者起始並且會變更 {{site.data.keyword.cloud_notm}} 中服務狀態的活動。如需相關資訊，請參閱[關於 IBM® Cloud Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#gs_ov)。

## Activity Tracker 事件表格
{: #at-events-table}

如需 Activity Tracker 事件表格中直欄的說明，請檢查下表。

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
{: caption="表 1. Activity Tracker 事件表格的說明" caption-side="top"}

如需相關資訊，請參閱[事件欄位](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-event)。

## 追蹤實例管理事件
{: #at-events-instance-mgmt}

當您在 {{site.data.keyword.vmwaresolutions_short}} 中管理使用者帳戶、實例、叢集及服務時，會在 Activity Tracker 中產生事件，並將其傳送至**帳戶網域**。

請檢查下表，以取得產生並傳送管理事件至 Activity Tracker 的動作。

| 動作 |說明              | 結果 |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` |將更新帳戶的基礎架構 API 金鑰。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.account-notification.update` | 將更新帳戶的通知設定。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | 將抹除實例安全資料。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	實例會移轉到 BSS 帳戶。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.create` |將建立 vCenter Server 實例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.delete`                |將刪除 vCenter Server 實例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.add` |主機將新增到 vCenter Server 實例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.remove` |主機將從 vCenter Server 實例中移除。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.update`	| 將更新 vCenter Server 實例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.create`	| 將為 vCenter Server 實例建立叢集。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete`	| 將為 vCenter Server 實例刪除叢集。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update`	| 將為 vCenter Server 實例更新 NSX 授權。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add`	| 將為 vCenter Server 實例更新 Hybridity Bundle。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove`	| 將為 vCenter Server 實例移除 Hybridity Bundle。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add`	| NFS 儲存空間將新增到 vCenter Server 實例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove`	| NFS 儲存空間將從 vCenter Server 實例中移除。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-plan.update`	| 將更新 vCenter Server 實例的方案。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.create`	|將建立 vSphere 實例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.update`	| 將更新 vSphere 實例。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss-template.remove` |將移除 vSphere 範本。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.create`	|將建立服務。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.delete`	|將刪除服務。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` |Hybridity Bundle 將升級到 `version`。|`pending`<br>`success`<br>`failure` |
{: caption="表 2. 產生管理事件之動作的說明" caption-side="top"}

## 追蹤 KMIP for VMware on IBM Cloud 服務的事件
{: #at-events-kmip}

當您管理 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務的金鑰時，會在 Activity Tracker 中產生事件，並將其傳送至**帳戶網域**。

請檢查下表，以取得產生並傳送 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務事件的動作。

| 動作 |說明       | 結果 |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` |將建立 KMIP 金鑰。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` |將擷取 KMIP 金鑰。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` |將擷取 KMIP 金鑰的屬性。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.activate` |將啟動 KMIP 金鑰。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` |將撤銷 KMIP 金鑰。|`pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` |將破壞 KMIP 金鑰。|`pending`<br>`success`<br>`failure` |
{: caption="表 3. 產生 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務事件之動作的說明" caption-side="top"}

## 事件的檢視位置
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} 事件位於 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**中，而此帳戶網域位於產生事件的 {{site.data.keyword.cloud_notm}} 地區中。

使用 {{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA 來檢視實例。如需相關資訊，請參閱[檢視事件](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events)。

## 相關鏈結
{: #at-events-related}

* [佈建實例](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [導覽至 Web 使用者介面](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
