---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-08"

---

# 1.4 版的版本注意事項

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之其他要訣的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Cloud Foundation 實例的元件更新項目

下列是新的或更新的元件：

* VC/PSC (vCenter/Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* 已為 Microsoft Active Directory (AD) 及 DNS（網域名稱系統）服務訂購新的 Windows VSI（虛擬伺服器實例），此版本的多站台配置支援需要這些服務。此 VSI 具有下列規格：Windows 2012 R2（8 GB RAM/2 CPU 核心/100 GB 磁碟/Dual 1 Gbps 專用上行鏈路）。

如需相關資訊，請參閱 [Cloud Foundation 概觀](../sddc/sd_cloudfoundationoverview.html)。

## vCenter Server 實例的元件更新項目

下列是新的或更新的元件：

### VMware NSX for vSphere 6.2.4

依預設，現在 VMware NSX for vSphere 6.2.4 i 會安裝在所有 vCenter Server 實例上（先前僅安裝在 Cloud Foundation 實例上）。

在 NSX 安裝過程中，會在已部署的所有新實例上安裝及授權 NSN Manager。此外，會針對實例管理建立一個 NSX Edge，但如有需要，您可以建立自己的 NSX Edge 元件。如需 NSX Edge 的相關資訊，請參閱此頁面上的 _VMware NSX Edge_ 小節。

**附註**：NSX Controller 未安裝在 vCenter Server 實例上（像它安裝在 Cloud Foundation 實例上那樣）。如果您是針對 vCenter Server 實例使用 VXLAN 或分散式邏輯路由器，則必須自行安裝 NSX Controller。

如需 VMware NSX for vSphere 6.2.4 所引進之加強功能、它的需求和已知問題等相關資訊，請參閱 [NSX for vSphere 6.2.4 版本注意事項](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}。

### VMware NSX Edge

現在，NSX Edge 已包含成為您訂購的新 vCenter Server 實例的一部分。NSX Edge 提供網路 Edge 安全及閘道服務，以隔離虛擬化網路。

在實例部署期間，由 IBM 部署 Management VMware NSX Edge Services Gateway (ESG)。IBM 管理虛擬機器利用此 ESG，來和與自動化相關的特定外部 IBM 管理元件進行通訊。所部署的這個 ESG 包含兩個介面：一個介面連接至 IBM Cloud 專用 VLAN，另一個介面連接至 IBM Cloud 公用 VLAN。

為了確保安全，已設置防火牆規則，僅容許管理虛擬機器所起始的出埠 HTTPS 通訊。這個 ESG 部署在「大型」配置中，只有「IBM 支援中心」才能修改此配置。如需相關資訊，請參閱：

* [vCenter Server 技術規格](../vcenter/vc_vcenterserveroverview.html)
* [管理服務 NSX Edge 是否造成安全風險？](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX 文件](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### NSX 授權

訂購每個節點的 VMware NSX Base for Service Providers Edition 授權。

### 新的子網路位址區塊

訂購每個節點 16 個公用可攜式位址的子網路區塊。

## 服務計費模型更新

服務計費模型已簡化：

* 對於 Cloud Foundation 實例，會停止 _VMware Cloud Foundation 實例服務_、_VMware Cloud Foundation 儲存服務_及
   _VMware Solutions Hypervisor_ 費用。
* 對於 vCenter Server 實例，會停止 _VMware vCenter Server 實例_和 _VMware Solutions Hypervisor_ 費用。
* 針對這兩個實例類型，會產生新的_支援和服務_費用，這是每一個節點的月費。

## 實例網路拓蹼的更新項目

此版本包括您實例的下列拓蹼加強功能：

* 對於 Cloud Foundation 實例和 vCenter Server 實例：最佳化網路配置，也就是說，只有 SoftLayer® 指派的主要公用和專用 IP 位址會連接至 ESXi 伺服器。對於管理資料流量，不再部署可攜式專用位址。
* 僅適用於 Cloud Foundation 實例：Windows AD SSO (Active Directory Single Sign-On) 和「網域名稱系統 (DNS)」伺服器

**附註**：由於這些變更，您無法在現行版本中使用您現有的 1.4 版之前的實例。若要重複使用現有實例的配置，您必須將它們升級至現行版本。如需相關資訊，請參閱[升級 1.4 版之前的實例](movinginstances.html)。

## Cloud Foundation 實例的多站台配置支援

您現在可以部署單一 Cloud Foundation 實例，就像先前的版本一樣，或者，也可以部署已連接至主要實例的次要實例。多站台配置模型使用中心與分支拓蹼來搭配一個主要站台及最多七個次要站台。

如需相關資訊，請參閱[Cloud Foundation 實例的多站台配置](../sddc/sd_multisite.html)。

## Zerto 災難回復部署的加強功能

* 對於 Cloud Foundation 實例，會自動部署 Zerto 災難回復，而不必透過支援問題單來處理。預估成本會列出所有 Zerto 元件，例如專用可攜式子網路、Windows VSI（虛擬服務實例）及 Zerto 授權費用，讓您在下訂單之前先檢閱。
* 對於 vCenter Server 實例，會透過支援問題單（如同在舊版中）來執行 Zerto 災難回復的部署。不過，不再需要 NSX Edge 和公用可攜式子網路，因為它們現在已包含在基本部署中。專用可攜式子網路、Windows VSI（虛擬服務實例）及 Zerto 授權仍然要收費。

如需相關資訊，請參閱 [Zerto 災難回復](../services/addingzertodr.html)。

## 實例訂購處理程序

實例訂購處理程序大幅簡化：

* 對於 Cloud Foundation 實例及 vCenter Server 實例，在訂購處理程序期間，不再顯示「SoftLayer 認證」頁面。依預設，會使用定義在「設定」頁面上的 SoftLayer 認證，唯有當認證不符合需求時，才會提示您更新它們。
* 此外，對於 vCenter Server 實例，現在僅**硬體**類型的**大型**選項，及**上行鏈路埠速度**的 **10 Gbps Dual **設定可供使用，這會減少訂購時要指定的設定數量。

如需相關資訊，請參閱：

* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)

## 實例管理

實例管理程序的新增特性及改進項目：

* 對於 Cloud Foundation 實例，您可以在實例詳細資料頁面上，檢視各種實例元件的使用者名稱及密碼。如需相關資訊，請參閱[檢視 Cloud Foundation 實例](../sddc/sd_viewinginstances.html)。
* 對於 vCenter Server 實例，您現在可以直接從主控台安裝 IBM 元件的軟體更新項目及修補程式。如需相關資訊，請參閱[將更新及修補程式套用至 vCenter Server 實例](../vcenter/vc_applyingupdates.html)。

## 主控台通知

您現在可以在**設定**頁面上配置主控台通知。依預設，已啟用此設定，這表示您會在主控台中收到所有事件的通知。您也可以在**設定**頁面上停用主控台的通知。

如需相關資訊，請參閱：

* [使用者帳戶及設定](useraccount.html)
* [通知](notifications.html)
