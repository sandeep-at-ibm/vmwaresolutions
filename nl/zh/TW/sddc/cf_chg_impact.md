---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# 變更 Cloud Foundation 構件的考量

變更保留給 {{site.data.keyword.vmwaresolutions_full}} 的使用者、資源或子網路，可能會影響 VMware Cloud Foundation 實例的管理作業。

**重要事項：**請不要在 VMware vSphere Web Client 的**使用者和群組**頁面中，變更 **ic4v-vCenter** 群組的廣域許可權。下列範例是廣域許可權變更：變更使用者名稱、刪除使用者或變更其密碼。

## 服務特定使用者帳戶

每一個服務都會在 vCenter Server 中建立內部使用者帳戶。此帳戶是必要的，因此與服務相關聯的管理作業可以連接至 vCenter Server，以在服務上執行作業。

**重要事項：**若要防止中斷及連線問題，如果您變更此使用者帳戶的使用者 ID、密碼或密碼有效期限設定，則請確定您同時更新了關聯服務中的資訊。

此帳戶的使用者 ID 格式為 `<service_name>-<truncated service_uuid>@test.local` 或 `<service_name>-<truncated service_uuid>@example-domain.local`。例如，Veeam on {{site.data.keyword.cloud_notm}} 服務用來連接至 vCenter Server 以執行排定備份的使用者 ID 為 `Veeam-<Veeam_uuid>@test.local`。

**附註：**`<service_name>` 與 `<service_uuid>` 一起使用會截斷為 20 個字元。

## Cloud Foundation 實例的 VMware 資源

下表列出在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更 VMware 資源時可能會受到影響的作業。如果有可用的回復解決方案，則也會提供它。

表 1. SSO 管理者（客戶）受到影響的作業

|嘗試的變更        |受影響的作業         |嚴重性    |回復方法         |
|:------------- |:------------- |:--------------|:--------------|
|變更 VMware 虛擬資料中心名稱。|新增 VMware 資料中心可能失敗，因為新的 ESXi 伺服器無法加入已變更的資料中心。|重要|將 VMware 虛擬資料中心名稱變更回原始名稱。|
|變更任何埠群組名稱。|新增 ESXi 伺服器可能失敗。|重要|將埠群組名稱變更回原始名稱。|
|變更叢集名稱。|新增 ESXi 伺服器可能失敗。|重要|將叢集名稱變更回原始名稱。
|變更公用或專用「分散式虛擬交換器 (DVS)」名稱。|新增 ESXi 伺服器可能失敗。|重要|將 DVS 名稱變更回原始名稱。
|變更 VSAN 資料儲存庫名稱。|新增 ESXi 伺服器可能失敗。<br><br>升級實例可能會失敗。|重要|將 VSAN 資料儲存庫名稱變更回原始名稱 **vsanDatastore**。
|變更實例名稱或網域名稱。|實例無法使用。|嚴重 |N/A

## Cloud Foundation 實例的管理子網路

下列資訊討論 {{site.data.keyword.vmwaresolutions_short}} 所訂購的子網路，並提供選項讓您訂購額外子網路以供您自己使用。

**警告：**請不要將這些元件用於其他用途，否則，您環境的穩定性會受到嚴重影響。

在每一張 {{site.data.keyword.cloud_notm}} Bare Metal Server 訂單中，依預設，會訂購下列 IP 位址範圍：

*  32 個 IP 位址的主要公用範圍
*  64 個 IP 位址的主要專用範圍

此外，也會保留下列管理子網路供 {{site.data.keyword.vmwaresolutions_short}} 使用：

*  第一個 VLAN 上有兩個含 64 個 IP 位址的可攜式專用子網路：一個用於管理，另一個用於 VTEPS。
*  第二個 VLAN 上有兩個含 64 個 IP 位址的可攜式專用子網路：一個用於 vMotion，一個用於 vSAN。
*  公用 VLAN 上有 16 個 IP 位址的公用可攜式子網路。

如果您需要使用更多子網路，您可以用下列其中一種方式取得要使用的 IP 位址：

* **選項 1（建議）：**使用 VMware NSX 虛擬網路覆蓋。訂購時會提供範例 VXLAN 範本。此 VXLAN 範本可以用作建置 SDN 的起點。
* **選項 2：**訂購您自己的可攜式公用或專用子網路來取得 IP 位址。若要區別您訂購的子網路與管理子網路，您可以將附註新增至您訂購的所有子網路。
