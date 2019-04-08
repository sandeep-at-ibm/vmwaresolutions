---

copyright:

  years:  2016, 2017

lastupdated: "2017-10-13"

subcollection: vmwaresolutions


---

# 1.9 版的版本注意事項
{: #relnotes_v19}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VMware vSphere on IBM Cloud
{: #relnotes_v19-vss}

此版本引進 VMware vSphere on {{site.data.keyword.cloud_notm}} 供應項目。此供應項目可讓您透過根據選取的 VMware 元件自訂及訂購 VMware 相容運算、儲存空間及網路資源，來建置您自己的 IBM 代管 VMware 虛擬環境。vSphere on {{site.data.keyword.cloud_notm}} 不會自動安裝、配置及開啟選用的 VMware 元件，但您具有最大的彈性來設計及建構最符合您商業需要的環境。一開始，建立 ESXi 伺服器的新 vSphere 叢集，或在 {{site.data.keyword.CloudDataCent_notm}} 擴充現有的 vSphere 叢集。

如需相關資訊，請參閱下列主題：
* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [擴充現有的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)

## NetApp ONTAP Select on IBM Cloud
{: #relnotes_v19-netapp}

此版本引進 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} 供應項目，這是用於軟體定義儲存空間的虛擬應用裝置，它在 IBM Cloud 的專用 {{site.data.keyword.baremetal_short}} 上以服務實作 NetApp ONTAP Select。我們以高效能（所有 SSD）及高容量（所有 SATA）兩種配置提供 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}。
此供應項目在專用的基礎架構上管理您的儲存空間，並提供 NetApp 功能，例如刪除重複、壓縮及加密靜止中資料。佈建儲存空間資源時具備敏捷性和彈性，同時使用進階資料管理功能來保護資料。例如，使用快速且有效率的 NetApp Snapshot® 複製、FlexClone® 複製及 SnapMirror® 抄寫。

如需相關資訊，請參閱下列主題：
* [NetApp ONTAP Select 概觀](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)
* [訂購 NetApp ONTAP Select 實例](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## F5 on IBM Cloud 服務
{: #relnotes_v19-f5}

現在，F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} 服務可用於 VMware Cloud Foundation 實例及 VMware vCenter Server 實例。本服務以區域和全球規模、健全網路及 Web 應用程式防火牆保護、安全及聯合應用程式存取，來提供智慧型 L4-L7 負載平衡與資料流量管理服務。
在訂購實例時，請訂購內含 F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} 服務的實例，或稍後透過 {{site.data.keyword.vmwaresolutions_short}} 主控台的實例內容詳細資料頁面的**服務**標籤，將此服務新增至現有的實例。視您的需求而定，您可以為 BIG-IP VE 選取三個授權選項的其中一項。

如需相關資訊，請參閱下列主題：
* [F5 on {{site.data.keyword.cloud_notm}} 的考量](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [管理 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)

## 來自 IBM-Integrated Managed Infrastructure 的受管理服務
{: #relnotes_v19-imi}

來自 IBM-Integrated Managed Infrastructure (IMI) 的受管理服務現在可用於 VMWare Cloud Foundation 實例。IMI 可以使用模組化服務來簡化 VMware 虛擬基礎架構管理，並可作為單一信任的提供者，以減少監視及管理虛擬 IT 基礎架構的複雜性。將每日例行作業卸載至 IMI（例如監視），以便能專注在更高價值的方案。

您隨時可以從**開始使用**頁面中要求商議和預估。
如需相關資訊，請參閱[從 IMI 要求受管理服務](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_imi#requesting-managed-services-from-imi)。

## vCenter Server 及 NetApp ONTAP Select 實例的實例名稱限制
{: #relnotes_v19-inst-name}

當您訂購實例時，在 {{site.data.keyword.vmwaresolutions_short}} 上輸入的實例名稱不能含有特殊字元（例如橫線字元）。僅容許英數字元。此限制不適用於 Cloud Foundation 實例。

如需相關資訊，請參閱下列主題：
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [訂購 NetApp ONTAP Select 實例](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## VMware Cloud Foundation 實例的更新
{: #relnotes_v19-vcf}

### 自訂實例 CPU 及記憶體
{: #relnotes_v19-custom-cpu}

使用者自訂的伺服器選項可與預先建置及測試的「小」及「標準」選項搭配使用。為了能夠更符合工作負載對 VMware 相容硬體的 CPU 與 RAM 比例，您現在可以獨立選取雙 CPU 伺服器上的核心總數，以及 RAM 數量。本端儲存空間不可自訂。

## VMware vCenter Server 實例的更新
{: #relnotes_v19-vcs}

### 跨資料中心叢集支援
{: #relnotes_v19-cross-dc}

為了加強擴充受管理的 VMware 環境，您現在可以在不同的 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) Pod 中，或在與實例中已部署的起始叢集不同的 {{site.data.keyword.CloudDataCent_notm}} 內建立新叢集。

如需相關資訊，請參閱[新增及檢視 vCenter Server 實例的叢集](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)。

### 變更元件
{: #relnotes_v19-change-comp}

當單一登入 (SSO) 管理者從原生 VMware 工具變更某些 vCenter Server 資源時，這個版本會消除對 {{site.data.keyword.vmwaresolutions_short}} 主控台中的作業所造成的影響。例如，您現在可以從 VMware vSphere Web Client 修改 VMware 虛擬資料中心、叢集、交換器、埠群組及資料儲存庫名稱，以自訂符合公司或個人命名慣例的部署，而不對 {{site.data.keyword.vmwaresolutions_short}} 主控台內的作業造成任何下游影響。

如需相關資訊，請參閱[變更 vCenter Server 實例元件的影響](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact)。

### 其他 RAM 大小
{: #relnotes_v19-ram-sizes}

訂購 vCenter Server 實例或新增 vCenter Server 實例的叢集時，您現在有更多的 RAM 大小可進行選擇，以協助符合工作負載對硬體的 CPU 與 RAM 比例。從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購伺服器時，**使用者自訂**配置選項中有下列選項可用：64 GB、128 GB、256 GB、384 GB、512 GB、768 GB、1.5 TB。

如需相關資訊，請參閱[訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)。

### 網路檔案系統版本更新

「網路檔案系統 (NFS) 4.1 版」無法再作為使用者介面中的儲存空間設定。所有 vCenter Server 實例都會以 NFS 第 3 版部署。雖然 NFS 第 3 版是較舊的通訊協定版本，但它在 VMware 環境中啟用加強特性，支援「VMware 儲存空間分散式資源排程器 (SDRS)」及「儲存空間 I/O 控制 (SIOC)」。

如需相關資訊，請參閱[訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)。

### 單一站台網域名稱伺服器網域名稱
{: #relnotes_v19-single-site-dns}

您現在可以於訂單期間提供 vCenter Server 實例的「網域名稱伺服器 (DNS) 」網域名稱。Microsoft Windows Server 虛擬伺服器實例 (VSI) 已部署並可查閱，此實例充當已登錄主機及虛擬機器之實例的 DNS。Microsoft Active Directory (AD) 也設定在 Microsoft Windows VSI 上，且 DNS 網域名稱是 AD 網域樹系根。此 Microsoft Windows VSI 僅適用於 1.9 版以及更新版本。

如需相關資訊，請參閱下列主題：
* [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [檢視 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)

## 對於 Windows Server 自動安裝更新的需求
{: #relnotes_v19-win-server}

Microsoft Active Directory (AD) / 網域名稱伺服器 (DNS) 自動設定為只下載更新。它不會自動安裝並重新啟動這些更新。您必須在排定的時間手動安裝更新並重新啟動，以避免中斷進行中的 Active Directory 伺服器配置及其他備份工作。若要套用 Windows 更新，請手動安裝更新。

## 新文件與更新的文件
{: #relnotes_v19-new-docs}

* 瞭解如何保護專用多站台 Cloud Foundation 實例的安全，同時延伸 VMware 應用程式來使用公用 {{site.data.keyword.cloud_notm}} 服務。如需相關資訊，請參閱[在 {{site.data.keyword.cloud_notm}} 中安全地連接專用 VMware 工作負載](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}。
* 提供其他文件來配置防火牆，以允許來自 IBM CloudDriver 和 SDDC Manager 虛擬機器的所有通訊協定通訊。如需相關資訊，請參閱 [Fortinet on {{site.data.keyword.cloud_notm}} 的元件及考量](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)。
