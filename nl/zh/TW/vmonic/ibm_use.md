---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 實例的 IBM 使用者 ID 及部署歷程訊息
{: #ibm_use}

{{site.data.keyword.cloud}} 需要存取您的帳戶，以用於自動化及作業記載。

## 使用者 ID
{: #ibm_use-user-ids}

{{site.data.keyword.vmwaresolutions_short}} 會在您的帳戶中維護一組使用者，以在您執行將主機、叢集或儲存空間新增至 VMware 實例這類作業時，供 {{site.data.keyword.cloud_notm}} 自動化使用。請檢閱下列小節，以取得 {{site.data.keyword.cloud_notm}} 自動化使用者 ID。

如果 IBM 使用者 ID 已刪除、停用或變更其密碼，則 VMware 實例作業會失敗。
{:important}

### vCenter 及 Platform Services Controller 使用者 ID
{: #ibm_use-user-ids-vcenter-psc}

從 2.5 版開始，{{site.data.keyword.vmwaresolutions_short}} 會使用下列使用者 ID，將身分來源新增（依預設內嵌）至 vCenter。

表 1. vCenter 及 Platform Services Controller 使用者 ID

| 使用者 | 使用者 ID      | 方法 |說明              |
|:---------|:-------------|:-------|:------------|
|IBM          | root         | SSH | 用於 VMware 配置，例如設定「VMware 高可用性」及建立分散式交換器。使用後置部署來配對主要與次要 vCenter Server 實例。|
|客戶 | customerroot | SSH | 僅供客戶使用而建立。|
|IBM          | automation@``root_domain``<br/>（Active Directory 使用者）| HTTP | 使用後置部署來新增及移除主機與叢集，並且部署及配置附加程式服務的虛擬機器。|
|客戶 | Administrator@vsphere.local | HTTP | 僅供客戶使用而建立。|

HTTP 用於 vCenter 設定及配置，以及 VMware 作業（例如，新增主機、叢集或儲存空間，用於 vCenter 資源管理）。
{:note}

### NSX Manager 使用者 ID
{: #ibm_use-user-ids-nsx-mgr}

NSX Manager 使用者 ID 用來新增服務的 ESB 規則。

表 2. NSX Manager 使用者 ID

| 使用者 | 使用者 ID      |說明              |
|:---------|:-------------|:------------|
|IBM          | automation@``root_domain``<br/>（Active Directory 使用者）| 使用後置部署來管理 NSX VTEP IP 位址、在新增及移除主機和叢集時管理主機與叢集配置，以及管理附加程式服務的 ESG 配置，這些服務需要存取公用網路，才能授權、啟動或產生報告用量。|
|客戶 |管理者| 僅供客戶使用而建立。|

### ESXi 主機使用者 ID
{: #ibm_use-user-ids-esxi}

ESXi 主機使用者 ID 用來新增儲存空間、修補、配置 vSAN 叢集，以及執行所有伺服器驗證碼。

表 3. ESXi 主機使用者 ID

| 使用者 | 使用者 ID      |說明              |
|:---------|:-------------|:------------|
|IBM          | ic4vroot     | 使用後置部署來新增其他 NFS 儲存空間，並配置該儲存空間的路徑。|
|客戶 | root         | 僅供客戶使用而建立。|

### Microsoft Active Directory 使用者 ID
{: #ibm_use-user-ids-ad}

Active Directory 使用者 ID 用來設定 DNS 項目。

表 4. Active Directory 使用者 ID

| 使用者 | 使用者 ID      |說明              |
|:---------|:------------- |:------------|
|IBM          | automation    | 用來新增主機、新增服務的虛擬機器，以及設定 Active Directory 和 DNS 項目。|
|客戶 | 管理者 | 僅供客戶使用而建立。|

## 實例歷程訊息
{: #ibm_use-msgs}

{{site.data.keyword.cloud_notm}} 針對 VMware 實例執行的所有作業，都會記載在實例歷程中。您可以使用實例歷程作為參照，來檢閱這些作業。如需檢閱實例歷程的相關資訊，請參閱[檢視 vCenter Server 實例部署歷程的程序](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history)。

下列各節提供可以發出至實例歷程的所有可能訊息。

### 一般實例歷程訊息
{: #ibm_use-msgs-general}

{{site.data.keyword.vmwaresolutions_short}} 會針對一般動作發出下列訊息：

* ``開始建立實例使用者及必要服務...``
* ``實例使用者及必要服務建立已完成。``
* ``正在訂購 vCenter Server 授權...``
* ``正在訂購 VMware 授權...``
* ``已完成 VMware 授權的訂購。``
* ``正在訂購 <quantity> 附加費用...``
* ``正在啟動 <environment> 安裝與配置...``
* ``<environment> 安裝與配置已完成。``
* ``正在啟動 VMware 元件...``
* ``開始部署實例...``
* ``<instance_name> 實例已備妥可供使用。``
* ``開始升級至 <version>...``
* ``升級至 <version> 已完成。``
* ``VMware 元件升級已完成。``
* ``正在啟動 <instance_name> 實例刪除...``
* ``<instance_name> 實例已順利刪除。``
* ``安全清除實例已完成。``
* ``正在取消 vCenter 授權...``
* ``正在取消實例使用者及必要服務...``
* ``正在取消 <environment> 附加費用...``
* ``VMware 授權取消進行中...``
* ``VMware 授權取消已完成。``
* ``SoftLayer 訂購失敗或逾時。``

### 叢集歷程訊息
{: #ibm_use-msgs-cluster}

{{site.data.keyword.vmwaresolutions_short}} 會針對 vCenter Server 叢集發出下列訊息：

* ``正在啟動叢集配置...``
* ``正在啟動 <cluster_name> 的叢集配置...``
* ``叢集配置已完成。``
* ``<cluster_name> 叢集已備妥可供使用。``
* ``正在新增叢集至 vCenter...``
* ``已新增叢集至 vCenter。``
* ``正在啟動 <cluster_name> 的叢集刪除...``
* ``正在從 vCenter 中刪除 <cluster_name> 叢集...``
* ``已從 vCenter 中刪除 <cluster_name> 叢集。``
* ``已刪除 <cluster_name> 叢集。``

### 虛擬伺服器實例歷程訊息
{: #ibm_use-msgs-vsi}

{{site.data.keyword.vmwaresolutions_short}} 會針對「虛擬伺服器實例 (VSI)」發出下列訊息：

* ``正在訂購 IBM CloudDriver 的新虛擬伺服器實例...``
* ``已佈建 <ip_address> IBM CloudDriver 虛擬伺服器實例。``
* ``正在取消 <ip_address> IBM CloudDriver 虛擬伺服器實例...``
* ``開始訂購 Microsoft Active Directory/DNS 的 Microsoft Windows 虛擬伺服器實例...``
* ``正在驗證 Active Directory/DNS 的 Microsoft Windows 虛擬伺服器實例訂購...``
* ``Active Directory/DNS 的 Microsoft Windows 虛擬伺服器實例已備妥。``
* ``虛擬伺服器實例取消進行中...``
* ``正在取消關聯的虛擬伺服器實例...``
* ``虛擬伺服器實例取消已完成。``

### IBM CloudDriver 歷程訊息
{: #ibm_use-msgs-clouddriver}

{{site.data.keyword.vmwaresolutions_short}} 會針對 IBM CloudDriver 發出下列訊息：

* ``正在準備 IBM CloudDriver...``
* ``IBM CloudDriver 已備妥。``
* ``<ip_address> IBM CloudDriver 已備妥可供使用。``
* ``正在檢查 IBM CloudDriver 狀態...``
* ``正在重複使用現有的 <ip_address> IBM CloudDriver...``
* ``正在重複使用現有的 IBM CloudDriver（佈建中）...``
* ``正在核發 IBM CloudDriver...``
* ``正在核發 <ip_address> IBM CloudDriver...``
* ``正在啟動 IBM CloudDriver 刪除...``
* ``已完成 IBM CloudDriver 刪除。``

### ESXi 伺服器歷程訊息
{: #ibm_use-msgs-esxi}

{{site.data.keyword.vmwaresolutions_short}} 會針對 ESXi 伺服器發出下列訊息：

* ``開始訂購 <quantity> 部 ESXi 伺服器...``
* ``正在驗證 ESXi 伺服器訂購...``
* ``具有 <ip_addresses> 專用 IP 位址的 ESXi 伺服器已備妥。``
* ``已收回所有 ESXi 伺服器。``
* ``正在將 ESXi 伺服器新增至 vCenter Server 實例...``
* ``ESXi 伺服器已順利更新。``
* ``開始訂購叢集的 ESXi 伺服器...``
* ``開始為 <Cluster Name> 叢集訂購 <quantity> 部 ESXi 伺服器...``
* ``叢集的 ESXi 伺服器已備妥。``
* ``具有 <ip_addresses> 專用 IP 位址的 ESXi 伺服器已備妥，可供叢集使用。``
* ``ESXi 伺服器已備妥。``
* ``ESXi 伺服器配置已完成。``
* ``已順利新增 ESXi 伺服器與內容。``
* ``新增 ESXi 伺服器的所有要求已順利完成。``
* ``正在新增 ESXi 伺服器...``
* ``正在訂購 ESXi 伺服器的 Bare Metal Server...``
* ``新的 ESXi 伺服器已新增至 vCenter。``
* ``開始將服務新增至新的 ESXi 伺服器...``
* ``已順利取消所選取的 ESXi 伺服器。``
* ``已佈建新的 ESXi 伺服器。``
* ``新的 ESXi 伺服器已驗證並備妥。``
* ``開始為 <cluster_name> 叢集訂購 <quantity> 部新的 ESXi 伺服器...``
* ``已從 vCenter Server 中移除選取的 ESXi 伺服器。``
* ``開始移除服務以移除 ESXi 伺服器...``
* ``正在驗證 <cluster_name> 叢集的 ESXi 伺服器...``
* ``新的叢集 ESXi 伺服器已順利通過驗證。``
* ``正在驗證新的 ESXi 伺服器訂購...``
* ``ESXi 伺服器訂購的驗證失敗。``
* ``正在分割批次新增 ESXi 伺服器要求。``
* ``已順利完成移除 ESXi 伺服器的所有要求。``
* ``已順利新增主機。``
* ``已順利移除主機。``
* ``Bare Metal Server 取消進行中...``
* ``Bare Metal Server 取消已完成。``
* ``正在從 vCenter Server 實例中移除 ESXi 伺服器...``
* ``正在移除 ESXi 伺服器。``
* ``正在移除 <server_id> ESXi 伺服器。``
* ``正在從 vCenter Server 中移除選取的 ESXi 伺服器...``
* ``正在取消 ESXi 伺服器...``
* ``正在取消選取的 ESXi 伺服器...``

### IBM CloudBuilder 歷程訊息
{: #ibm_use-msgs-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} 會針對 IBM CloudBuilder 發出下列訊息：

* ``正在驗證 IBM CloudBuilder 虛擬伺服器實例訂購...``
* ``開始訂購 IBM CloudBuilder 虛擬伺服器實例...``
* ``IBM CloudBuilder 虛擬伺服器實例已備妥。``
* ``IBM CloudBuilder 已備妥可供服務使用。``
* ``正在解除 IBM CloudBuilder 虛擬伺服器實例...``

### 儲存空間歷程訊息
{: #ibm_use-msgs-storage}

{{site.data.keyword.vmwaresolutions_short}} 會針對儲存空間設定發出下列訊息：

* ``正在訂購 vSAN 授權...``
* ``正在取消 vSAN 授權...``
* ``VSAN 授權取消已完成。``
* ``正在為 <cluster_name> 叢集訂購 <quantity> 個 NFS 儲存空間。``
* ``已新增 NFS 儲存空間且備妥可供使用。``
* ``正在取消管理 NFS 共用儲存空間...``
* ``已刪除選取的 NFS 儲存空間。``
* ``開始訂購耐久性儲存空間...``
* ``正在取消耐久性儲存空間...``

### 網路歷程訊息
{: #ibm_use-msgs-network}

{{site.data.keyword.vmwaresolutions_short}} 會針對網路設定發出下列訊息：

* ``開始訂購公用 VLAN...``
* ``已順利完成 VLAN 配置。``
* ``正在訂購其他專用 VLAN...``
* ``已佈建其他專用 VLAN。``
* ``已佈建其他專用 VLAN 虛擬伺服器實例。``
* ``正在使用幹線將其他專用 VLAN 連接至 Bare Metal Server...``
* ``已順利使用幹線將其他專用 VLAN 連接至 Bare Metal Server。``
* ``正在取消其他專用 VLAN 虛擬伺服器實例...``
* ``正在取消 VLAN...``
* ``VLAN 取消進行中...``
* ``VLAN 取消已完成。`
* ``正在訂購雙 Socket <type> NSX 授權...``
* ``新叢集的 NSX 配置已完成。``
* ``正在取消雙 Socket NSX 授權...``
* ``已順利取消 NSX 授權。``
* ``開始訂購子網路...``
* ``子網路已備妥。``
* ``可攜式專用子網路已備妥。``
* ``正在將新的子網路存取權授與 NFS 儲存空間...``
* ``正在取消子網路...``
* ``子網路取消進行中...``
* ``正在取消客戶可攜式專用子網路 ...``
* ``正在取消客戶可攜式公用子網路 ...``
* ``正在取消耐久性儲存空間專用子網路 ...``
* ``正在取消可攜式公用子網路...``
* ``可攜式公用子網路已備妥。``
* ``開始訂購可攜式公用子網路...``
* ``子網路取消已完成。``
* ``正在取消網路儲存空間...``

### 服務歷程訊息
{: #ibm_use-msgs-services}

{{site.data.keyword.vmwaresolutions_short}} 會針對服務發出下列訊息：

* ``正在啟動管理服務設定...``
* ``正在訂購服務項目...``
* ``已完成服務項目的訂購。``
* ``IBM 作業服務正在執行中。``
* ``正在啟用預設服務...``
* ``預設服務已順利啟用。``
* ``服務項目取消進行中...``
* ``服務項目取消已完成。``

### vCenter Server with Hybridity Bundle 歷程訊息
{: #ibm_use-msgs-hybridity}

{{site.data.keyword.vmwaresolutions_short}} 會針對 vCenter Server with Hybridity Bundle 實例發出下列訊息：

* ``正在訂購 vCenter Server with Hybridity Bundle 授權...``
* ``正在啟動 vCenter Server with Hybridity Bundle 轉換...``
* ``vCenter Server with Hybridity Bundle 轉換已完成。``
* ``正在移除 vCenter Server with Hybridity Bundle...``
* ``已順利移除 vCenter Server with Hybridity Bundle。``
* ``正在取消 vCenter Server with Hybridity Bundle 轉換...``

### Cloud Foundation 歷程訊息
{: #ibm_use-msgs-cf}

{{site.data.keyword.vmwaresolutions_short}} 會針對 Cloud Foundation 實例發出下列訊息：

* ``開始訂購 Cloud Foundation 實例...``
* ``已收到 Cloud Foundation 訂購。``
* ``正在處理 Cloud Foundation 訂購...``
* ``正在訂購要用於 Cloud Foundation 配置的虛擬伺服器...``
* ``已完成訂購要用於 Cloud Foundation 配置的虛擬伺服器。``
* ``已驗證要用於 Cloud Foundation 配置之虛擬伺服器的訂購。``
* ``正在訂購要用於 Cloud Foundation 配置的 Bare Metal Server...``
* ``已完成訂購要用於 Cloud Foundation 配置的 Bare Metal Server。``
* ``正在配置 Cloud Foundation 網路...``
* ``已完成 Cloud Foundation 網路的配置。``
* ``正在訂購 Cloud Foundation 子網路...``
* ``已完成訂購 Cloud Foundation 子網路``
* ``正在配置 Cloud Foundation 實例...``
* ``正在自訂並最佳化 Cloud Foundation 實例元件...``
* ``Cloud Foundation 清理進行中...``
* ``Cloud Foundation 清理已完成。``
* ``Cloud Foundation 實例已備妥可供使用。``
* ``正在自訂並最佳化 Cloud Foundation 實例...``
* ``Cloud Foundation 實例配置已完成。``
* ``自訂並最佳化 Cloud Foundation 實例已完成。``
* ``Cloud Foundation 元件訂購已完成。``
* ``Cloud Foundation 實例刪除已完成。``
* ``刪除 Cloud Foundation 實例已完成。``

### 錯誤訊息
{: #ibm_use-msgs-error}

{{site.data.keyword.vmwaresolutions_short}} 會發出下列實例歷程錯誤訊息：

* ``訂購用於 Cloud Foundation 配置的虛擬伺服器時發生錯誤。請開立服務問題單，以取得協助。``
* ``錯誤：SoftLayer 無法佈建要用於 Cloud Foundation 配置的虛擬伺服器。請開立服務問題單，以取得協助。``
* ``訂購用於 Cloud Foundation 配置的 Bare Metal Server 時發生錯誤。請開立服務問題單，以取得協助。``
* ``訂購要用於 Cloud Foundation 配置的 VLAN 時發生錯誤。請開立服務問題單，以取得協助。``
* ``配置 Cloud Foundation 網路時發生錯誤。請開立服務問題單，以取得協助。``
* ``訂購 Cloud Foundation 子網路時發生錯誤。請開立服務問題單，以取得協助。``
* ``建立 Cloud Foundation 實例的管理服務時發生錯誤。請開立服務問題單，以取得協助。``
* ``訂購 VMware 授權時發生錯誤。請開立服務問題單，以取得協助。``
* ``訂購子網路時發生錯誤。請開立服務問題單，以取得協助。``
* ``配置 Cloud Foundation 實例時發生錯誤。請開立服務問題單，以取得協助。``
* ``自訂並最佳化 Cloud Foundation 實例時發生錯誤。請開立服務問題單，以取得協助。``
* ``錯誤：SoftLayer API 金鑰無效。請開立服務問題單，以取得協助。``
* ``錯誤：SoftLayer 資料中心無效。請開立服務問題單，以取得協助。``
* ``在提供的 SoftLayer 帳戶中使用共用映像檔時發生錯誤。請開立服務問題單，以取得協助。``
* ``訂購服務項目時發生錯誤。請開立服務問題單，以取得協助。``
* ``訂購子網路時發生錯誤。請開立服務問題單，以取得協助。``
* ``訂購授權時發生錯誤。請開立服務問題單，以取得協助。``
* ``訂購服務時發生錯誤。請開立服務問題單，以取得協助。``


## 相關鏈結
{: #ibm_use-related}

* [變更 vCenter Server 構件的考量](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker 事件](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
