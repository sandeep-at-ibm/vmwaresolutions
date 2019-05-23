---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM 使用者 ID
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}} 會在您的帳戶中維護一組使用者，以在您執行將主機、叢集或儲存空間新增至 VMware 實例這類作業時，供 {{site.data.keyword.cloud_notm}} 自動化使用。請檢閱下列小節，以取得 {{site.data.keyword.cloud_notm}} 自動化使用者 ID。

如果 IBM 使用者 ID 已刪除、停用或變更其密碼，則 VMware 實例作業會失敗。
{:important}

## vCenter 及 Platform Services Controller 使用者 ID
{: #audit_user_ids-vcenter-psc}

從 2.5 版開始，{{site.data.keyword.vmwaresolutions_short}} 會使用下列使用者 ID，將身分來源新增（依預設內嵌）至 vCenter。

表 1. vCenter 及 Platform Services Controller 使用者 ID

| 使用者 | 使用者 ID      | 方法 |說明       |
|:---------|:-------------|:-------|:------------|
|IBM          | root         | SSH | 用於 VMware 配置，例如設定「VMware 高可用性」及建立分散式交換器。使用後置部署來配對主要與次要 vCenter Server 實例。|
|客戶 | customerroot | SSH | 僅供客戶使用而建立。|
|IBM          | automation@``root_domain``<br/>（Active Directory 使用者）| HTTP | 使用後置部署來新增及移除主機與叢集，並且部署及配置附加程式服務的虛擬機器。|
|客戶 | Administrator@vsphere.local | HTTP | 僅供客戶使用而建立。|

HTTP 用於 vCenter 設定及配置，以及 VMware 作業（例如，新增主機、叢集或儲存空間，用於 vCenter 資源管理）。
{:note}

## NSX Manager 使用者 ID
{: #audit_user_ids-nsx-mgr}

表 2. NSX Manager 使用者 ID

| 使用者 | 使用者 ID      |說明       |
|:---------|:-------------|:------------|
|IBM          | automation@``root_domain``<br/>（Active Directory 使用者）| 使用後置部署來管理 NSX VTEP IP 位址、在新增及移除主機和叢集時管理主機與叢集配置，以及管理附加程式服務的 ESG 配置，這些服務需要存取公用網路，才能授權、啟動或產生報告用量。|
|客戶 |管理者| 僅供客戶使用而建立。|

## ESXi 主機使用者 ID
{: #audit_user_ids-esxi}

表 3. ESXi 主機使用者 ID

| 使用者 | 使用者 ID      |說明       |
|:---------|:-------------|:------------|
|IBM          | ic4vroot     | 使用後置部署來新增其他 NFS 儲存空間，以配置該儲存空間的路徑，及執行所有伺服器驗證程式碼。|
|客戶 | root         | 僅供客戶使用而建立。|

## Microsoft Active Directory 使用者 ID
{: #audit_user_ids-ad}

表 4. Active Directory 使用者 ID

| 使用者 | 使用者 ID      |說明       |
|:---------|:------------- |:------------|
|IBM          | automation    | 用來新增主機、新增服務的虛擬機器，以及設定 Active Directory 和 DNS 項目。|
|客戶 | 管理者 | 僅供客戶使用而建立。|

## 相關鏈結
{: #audit_user_ids-related}

* [變更 vCenter Server 構件的考量](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker 事件](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
