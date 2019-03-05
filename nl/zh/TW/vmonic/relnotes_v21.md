---

copyright:

  years:  2016, 2019

lastupdated: "2018-04-16"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 2.1 版的版本注意事項

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 及 Meltdown 補救

{{site.data.keyword.vmwaresolutions_short}} 發行來自 VMware 的修補程式，以回應已知的 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 及 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

如需相關資訊，請參閱[處理 Spectre 及 Meltdown 漏洞](/docs/services/vmwaresolutions/vmonic/trbl_fix_spectre.html)。

## VMware HCX on IBM Cloud

現在，HCX on {{site.data.keyword.cloud_notm}} 服務可用於執行 vSphere 6.5 以及部署於或升級至 2.1 版或更新版本的 VMware Cloud Foundation 實例及 VMware vCenter Server 實例。此服務可將內部部署資料中心的網路無縫延伸至 {{site.data.keyword.cloud_notm}}，這容許在內部部署資料中心與 {{site.data.keyword.cloud_notm}} 之間雙向移轉虛擬機器 (VM)，而不需要任何變更。透過建立第 2 層橋接器，HCX 使用 WAN 最佳化、刪除重複、壓縮及加密，能更快速且安全地透過 Direct Link 或 VPN 通道來移轉資料。VM 的大量移轉與 VMware vSphere 5.1 以上的舊版相容。如果您在內部部署中使用 vSphere 6.0 以上的版本，則可以將 vMotion 即時（已開啟電源）VM 從內部部署移轉至 {{site.data.keyword.CloudDataCent_notm}}。使用 HCX 時，您不需要在資料中心安裝 VMware NSX。

您可以在訂購實例時訂購包含 HCX on {{site.data.keyword.cloud_notm}} 服務的 Cloud Foundation 或 vCenter Server 實例，或稍後透過實例詳細資料頁面的**服務**標籤，將此服務新增至現有的實例。

您也可以訂購內部部署 HCX 實例，以進行內部部署 HCX 安裝的授權和啟動。

如需相關資訊，請參閱下列主題：
* [HCX on {{site.data.keyword.cloud_notm}} 的考量](/docs/services/vmwaresolutions/services/hcx_considerations.html)
* [管理 HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managinghcx.html)
* [內部部署的 HCX 實例的考量](/docs/services/vmwaresolutions/services/standalone_considerations.html)
* [訂購內部部署的 HCX 實例](/docs/services/vmwaresolutions/services/standalone_orderingserviceinstances.html)

## 對於 VMware Cloud Foundation 和 vCenter Server 更有彈性的「自帶授權」模型

現在，建立新叢集時，「自帶授權 (BYOL)」或購買 IBM 提供的訂閱授權適用於 2.1 版及更新版本的 VMware Cloud Foundation 實例及 VMware vCenter Server 實例。這些選項可讓您使用現有的元件金鑰，或向 IBM 租用授權。在 2.1 版之前，如果您是 BYOL，則無法針對特定 VMware 元件購買 IBM 提供的授權。目前，每個叢集僅 VMware vSphere 及 VMware vSAN 可用於授權。

此外，當您將節點新增至使用您的金鑰所授權的叢集時，如果節點數目超出金鑰容量，主控台會提示您提供新的授權碼。

如需相關資訊，請參閱下列主題：

* [新增及檢視 Cloud Foundation 實例的叢集](/docs/services/vmwaresolutions/sddc/sd_addingviewingclusters.html)
* [新增及檢視 vCenter Server 實例的叢集](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)
* [關於 BYOL 的常見問題](/docs/services/vmwaresolutions/vmonic/faq_byol.html)

## Zerto on IBM Cloud 服務元件更新

對於部署在 2.1 版及更新版本 Cloud Foundation 實例及 vCenter Server 實例中的 Zerto on {{site.data.keyword.cloud_notm}} 服務，會佈建 Zerto Virtual Replication 5.5u2。基於效能理由，Zerto 虛擬抄寫應用裝置 (VRA) 現在是部署到管理資料儲存庫（vSAN 或「耐久性」）而不是本端資料儲存庫。如果您有現有的 VRA，則請考慮將其儲存空間移轉至管理資料儲存庫，以獲得更好的效能。

如需相關資訊，請參閱 [Zerto on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services/addingzertodr.html)。

## VMware vCenter Server 實例的更新

### 網路 MTU 配置設定

對於 2.1 版或更新版本，會訂購將「公用分散式虛擬交換器 (DVS)」設定為 MTU 1500（預設值）的新 vCenter Server 實例。如需相關資訊，請參閱 [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter/vc_bom.html)中的_網路 MTU 配置設定_。

### 對主機自動套用 VMware ESXi 修補程式及更新

在 2.0 版及更早版本的 VMware vCenter Server 實例中，修補程式未自動套用至已新增至叢集的 ESXi 主機。

在 2.1 版以及更新版本的實例中，自動化會將修補程式套用至新的 ESXi 主機，使該修補程式層次符合佈建起始實例時的修補程式層次。由您負責手動套用任何未來的修補程式和更新。
當未來版本中提供 VMware 修補程式及更新時，自動化會掃描您現有實例的 ESXi 主機，並以電子郵件提醒您手動套用最新的修補程式和更新。

如需相關資訊，請參閱[將更新套用至 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter/vc_applyingupdates.html)。

### VMware NSX 授權升級的價格預估

您現在可以在提交訂單或升級至 VMware NSX Advanced 或 Enterprise 版本之前，先查看價格預估。定價是根據 vCenter Server 實例中的 ESXi 主機數目。這項購買只會變更 NSX 授權碼，並將您的 VMware NSX Base 版本升級至 Advanced 或 Enterprise 版本。購買不會升級 NSX 軟體版本。

如需相關資訊，請參閱 [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html)。

### 每個叢集的伺服器數目上限從 32 開始增加

對於實例中的預設叢集，您可以部署或擴充最多 51 部伺服器。對於實例中的所有後續叢集，您可以部署或擴充最多 59 部伺服器。如需相關資訊，請參閱[新增及檢視 vCenter Server 實例的叢集](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)。

只有在 2.1 版及更新版本中部署的實例，才能使用此功能。從 2.1 版之前的版本升級至 2.1 版的實例沒有這個選項。{:note}

### 使用者自訂的 IBM Cloud Bare Metal Server 配置選項

使用者自訂的 Bare Metal Server 配置現在提供「雙重 Intel Xeon Gold 6140，總計 36 核心，2.3 GHz」。

如需相關資訊，請參閱下列主題：
* [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html)
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)

### 個別 NFS 檔案共用配置

您現在可以個別配置 NFS 檔案共用。為每一個別檔案共用選取檔案大小及效能層次，或針對您訂購的所有檔案共用，選取相同的檔案大小及效能層次。

如需相關資訊，請參閱下列主題：
* [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html)
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [新增及檢視 vCenter Server 實例的叢集](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)

## 使用者介面更新和加強功能

在整個使用者介面中進行了改善：

* 左導覽窗格中不再提供**訂購實例**選項。按一下**開始使用**來完成訂購實例的步驟。
* 訂購實例時，**基本**頁面中的**子網域字首**欄位已重新命名為**子網域標籤**。
* 訂購主要或次要 vCenter Server 或 Cloud Foundation 實例時，除了在**摘要**頁面上檢視成本預估，現在您可以提供實例訂單的詳細資料，然後在任何頁面上計算成本預估。
* 瀏覽途徑導覽會新增至**已部署的實例**頁面作為替代的導覽方法，從而減少到達母頁面所需的步驟數。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。

## 新文件與更新的文件

有新的 developerWorks 秘訣可供使用，其包含的逐步指示是關於如何使用 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}，將專用的儲存空間連接至現有的 {{site.data.keyword.vmwaresolutions_full}} 部署。如需相關資訊，請參閱 [Steps to attach dedicated storage to VMware Solutions on IBM Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)。
