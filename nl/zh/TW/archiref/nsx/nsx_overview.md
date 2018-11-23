---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-21"

---

# 關於 NSX Edge Services Gateway

VMware NSX Edge Services Gateway (ESG) 解決方案是 {{site.data.keyword.cloud_notm}} 上目前可用的 VMware Cloud Foundation on {{site.data.keyword.cloud}} 及 vCenter Server on {{site.data.keyword.cloud_notm}} 供應項目的延伸。Cloud Foundation 及 vCenter Server 的解決方案架構詳述解決方案的元件，以及本設計中每個元件的高階配置。

如需 Cloud Foundation 及 vCenter Server 設計的相關資訊，請參閱[解決方案概觀](../solution/solution_overview.html)。

## NSX Edge Services Gateway 概觀

NSX Edge Services Gateway 會提供一般閘道服務（例如「動態主機配置通訊協定 (DHCP)」、「虛擬專用網路 (VPN)」、「網址轉換 (NAT)」、動態遞送及負載平衡），以將隔離的 Stub 網路連接至共用（上行鏈路）網路。NSX Edge 的一般部署包括非管制區 (DMZ)、VPN Extranets 及多方承租戶雲端環境，而在這些環境中，NSX Edge 會建立每個承租戶、工作負載或管理元件的虛擬界限。NSX Edge Services Gateway 內提供下列特性。

表格 1. NSX Edge Services Gateway 提供的特性

| 特性 |說明              |
|:------- |:----------- |
| NSX Edge Service Routing | 提供第 2 層播送網域之間的必要轉遞資訊，因此可讓您降低第 2 層播送網域，並改善網路效率及擴充。NSX 將這項智慧擴充至工作負載所在的位置，以提供「東西向」遞送。這容許更多的直接虛擬機器對虛擬機器通訊，而不需要昂貴或及時地擴充中繼站。同時，NSX 也提供「南北向」連線功能，進而讓承租戶存取公用網路。|
| 防火牆 | 防火牆所支援的規則包括 IP 5 值組配置，其中具有所有通訊協定之有狀態檢驗的 IP 及埠範圍。|
| NAT | 提供來源及目的地 IP 位址的個別控制項，以及埠轉換。|
| DHCP | 提供 IP 儲存區、閘道、DNS 伺服器及搜尋網域的配置。|
| 站台對站台 VPN | 使用標準化 IPSec 通訊協定設定，與所有主要 VPN 供應商進行交互作業。|
| L2VPN | 可讓您跨越 L3 拓蹼延伸 L2 網路。|
| SSL VPN-Plus | SSL VPN-Plus 可讓遠端使用者安全地連接至受 NSX Edge 閘道保護的專用網路。|
|負載平衡| 提供簡單及動態可配置的虛擬 IP 位址及伺服器群組。|
| 高可用性 | 確保網路上有作用中的 NSX Edge，以免主要 NSX Edge 虛擬機器無法使用。|

### 相關鏈結

* [解決方案概觀](../solution/solution_overview.html)
