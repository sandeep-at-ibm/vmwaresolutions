---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# 變更 vCenter Server 構件的考量
{: #vcenter_chg_impact}

變更已保留給 {{site.data.keyword.vmwaresolutions_full}} 的使用者、資源或子網路，會影響管理作業。

請不要在 VMware vSphere Web Client 的**使用者和群組**頁面中，編輯 **ic4v-vCenter** 群組的廣域許可權。這類變更包括：變更使用者名稱、刪除使用者或變更其密碼。請使用 **root** 主機使用者 ID。已建立 **ic4vroot** 主機使用者 ID，僅供 IBM 使用。
{:important}

## 自動化 ID
{: #vcenter_chg_impact-automation-id}
{: faq}

**自動化** ID 是一個使用者帳戶，由 {{site.data.keyword.vmwaresolutions_short}} 主控台中所提供的自動化作業使用。

適用於主控台中的自動化作業的使用者和密碼不得變更，因為仰賴那些認證的主控台作業可能會失敗。

## 服務特定使用者帳戶
{: #vcenter_chg_impact-service-usr-account}

每一個服務都會在 vCenter Server 中建立內部使用者帳戶。此帳戶是必要的，因此與服務相關聯的管理作業可以連接至 vCenter Server，以在服務上執行作業。

若要防止中斷及連線問題，如果您變更此使用者帳戶的使用者 ID、密碼或密碼有效期限設定，則請確定您也更新了關聯服務中的資訊。
{:important}

此帳戶的使用者 ID 格式為 `<service_name>-<truncated service_uuid>@test.local` 或 `<service_name>-<truncated service_uuid>@example-domain.local`。例如，Veeam on {{site.data.keyword.cloud_notm}} 服務用來連接至 vCenter Server 以執行排定備份的使用者 ID 為 `Veeam-<Veeam_uuid>@test.local`。

`<service_name>` 與 `<service_uuid>` 一起使用會截斷為 20 個字元。
{:note}

## vCenter Server 實例的 VMware 資源（第 1.9 版以及更新版本）
{: #vcenter_chg_impact-vmware-resources-for-inst-v1.9-and-later}

若為部署在 1.9 版以及更新版本中的實例，如果 vCenter Server 實例處於**備妥使用**狀態，您可以從 VMware vSphere Web Client 修改 VMware 虛擬資料中心、叢集、交換器、埠群組及客戶資料儲存庫名稱。

不過，您不得變更管理資料儲存庫名稱的預設值：vSAN 實例為 **vsanDatastore**，而「網路檔案系統 (NFS)」實例則為 **management-share**。此外，您不得變更佈建期間建立的網路上行鏈路名稱。

## vCenter Server 實例的 VMware 資源（1.8 版及更早版本）
{: #vcenter_chg_impact-vmware-resources-for-inst-v1.8-and-earlier}

下表列出當 SSO 管理者在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更 VMware vCenter Server 資源時可能受到影響的作業。如果有可用的回復解決方案，則也會提供它。

除了部署在 1.8 版及更早版本後升級至 1.9 版或更新版本的實例之外，此表格也適用於部署在 1.8 版及更早版本的實例。

表 1. 受到變更 VMware 資源影響的作業

|嘗試的變更        |受影響的作業         |嚴重性    |回復方法         |
|:------------- |:------------- |:--------------|:--------------|
|變更 VMware 虛擬資料中心名稱。|新增 VMware 虛擬資料中心可能失敗，因為新的 ESXi 伺服器無法加入已變更的虛擬資料中心。|重要|將 VMware 虛擬資料中心名稱變更回原始名稱。|
|變更任何埠群組名稱。|新增 ESXi 伺服器可能失敗。|重要|將埠群組名稱變更回原始名稱。|
|變更叢集名稱。|新增 ESXi 伺服器可能失敗。|重要|將叢集名稱變更回原始名稱。
|變更公用或專用「分散式虛擬交換器 (DVS)」名稱。|新增 ESXi 伺服器可能失敗。|重要|將公用或專用「分散式虛擬交換器 (DVS)」名稱變更回原始名稱。
|變更實例中使用 vSAN 的 vSAN 資料儲存庫名稱。|新增 ESXi 伺服器可能失敗。<br><br>升級實例可能會失敗。|重要|將 vSAN 資料儲存庫名稱變更回原始名稱 **vsanDatastore**。
|變更實例中使用 NFS 的管理 NFS 資料儲存庫名稱。|新增 ESXi 伺服器可能失敗。<br><br>升級實例可能會失敗。|重要|將 NFS 管理資料儲存庫名稱變更回原始名稱 **management-share**，並在 ESXi 伺服器上將 NFS 資料儲存庫重新裝載為唯讀。

下表列出因為各種資源而停用 SSH 或 Shell 存取時可能受到影響的作業。

表 2. 受 SSH 及 Shell 存取影響的作業（本端）

|嘗試的變更        |受影響的作業         |嚴重性    |回復方法         |
|:------------- |:------------- |:--------------|:--------------|
| 停用 vCenter Server 或 PSC 的 SSH 或 Shell 存取。| 主要及次要實例的配對可能會失敗。|重要|N/A    |
| 停用 ESXi 的 SSH 或 Shell 存取。| 在實例中新增及移除主機、服務及網路儲存空間可能會失敗。|重要|N/A    |

如果您選擇要停用 SSH 或 Shell 存取，在執行指示的作業之前您應該暫時將它重新啟用。

## vCenter Server 實例的管理子網路
{: #vcenter_chg_impact-mgmt-subnets}

下列資訊討論 {{site.data.keyword.vmwaresolutions_short}} 所訂購的子網路，並提供選項讓您訂購額外子網路以供您自己使用。

**警告：**請不要將這些元件用於其他用途，否則，您環境的穩定性會受到嚴重影響。

在每一張 {{site.data.keyword.cloud_notm}} Bare Metal Server 訂單中，依預設，會訂購下列 IP 位址範圍：
*  32 個 IP 位址的主要公用範圍
*  64 個 IP 位址的主要專用範圍

此外，也會保留下列管理子網路供 {{site.data.keyword.vmwaresolutions_short}} 使用：
*  第一個 VLAN 上有兩個包含 64 個 IP 位址的可攜式專用子網路：一個用於管理，另一個用於 VTEPS
*  第二個 VLAN 上有兩個包含 64 個 IP 位址的可攜式專用子網路：一個用於 VMotion，一個用於 vSAN
*  在公用 VLAN 上有一個包含 16 個 IP 位址的公用可攜式子網路

如果您需要使用更多子網路，您可以用下列其中一種方式取得要使用的 IP 位址：
*  **選項 1（建議）**：使用 VMware NSX 虛擬網路層疊。訂購時會提供範例的 VXLAN 範本。這個 VXLAN 可用來作為建置軟體定義網路 (SDN) 的起點。如需相關資訊，請參閱[將網路配置成使用客戶管理的 NSX Edge](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config)。
*  **選項 2**：訂購您自己的可攜式公用或專用子網路來取得 IP 位址。若要區別您訂購的子網路與管理子網路，您可以將附註新增至您訂購的所有子網路。
