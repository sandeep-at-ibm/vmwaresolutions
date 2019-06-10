---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# 配置作業
{: #opsprocs-configure}

佈建 vCenter Server 實例之後，系統管理者可能需要執行許多配置作業，以便根據其企業需要來量身打造起始環境，以及回應未來的服務要求。為了方便使用，我們將它們分類如下：

* 實例及叢集指引
* 虛擬機器 (VM) 程序
* vCenter 程序
* vSphere ESXi 主機程序
* 儲存空間程序
* 網路程序

## 實例及叢集指引
{: #opsprocs-configure-instance}

表 1. vCenter Server 實例及叢集

|標題|說明       |
|---|---|
|命名慣例|其中一個首要作業是為 vCenter Server 實例採用命名慣例。您可以延伸組織使用的現有命名慣例，或建立一個命名慣例。如需相關資訊，請參閱 [Naming Convention in VMware Validated Design 4.1](https://docs.vmware.com/en/VMware-Validated-Design/4.1/com.vmware.vvd.sddc-upgrade.doc/GUID-FCA126F1-E429-454E-B3BA-226525742DC1.html){:new_window}。請參閱[變更 vCenter Server 構件的考量](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact){:new_window}，然後才採用命名慣例並變更 vCenter Server 實例中的任何名稱。|
|連接至 vCenter Server 實例|在佈建之後，請連接至 vCenter。一開始有兩種方法可以做到。您可以部署「跳板」伺服器，以便可以使用網際網路連接至跳板，然後使用專用網路從跳板連接至 vCenter。第二種方法是使用 {{site.data.keyword.cloud_notm}} VPN，它是從您的位置到 {{site.data.keyword.cloud_notm}} Private 網路的 VPN 連線，容許頻外管理及 vCenter 存取。如需相關資訊，請參閱[開始使用虛擬專用網路 (VPN)](/docs/infrastructure/iaas-vpn?topic=VPN-gettingstarted-with-virtual-private-networking){:new_window}。|
|配置名稱解析|若要使用 vCenter 中的特性，請根據您的連線方法，將 vCenter Server 元件的名稱解析新增至工作站或跳板。/etc/hosts 或 c:\Windows\System32\Drivers\etc\hosts 檔案需要 Platform Services Controller (PSC)、vCenter 及 vSphere ESXi 主機的項目。如需相關資訊，請參閱[使用 VMware vSphere Web Client 部署 OVF 檔案](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_deploy_ovf#trbl_deploy_ovf){:new_window}。|
| RBAC |如需 vSphere 環境中常見作業所需專用權的相關資訊，請參閱 [Required Privileges for Common Tasks](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-4D0F8E63-2961-4B71-B365-BBFA24673FDB.html){:new_window}。|
|使用憑證管理中心簽署的自訂憑證|如需將 vSphere 6.x 機器 SSL 憑證取代為自訂憑證管理中心 (CA) 簽署憑證的相關資訊，請參閱 [Replacing a vSphere 6.x Machine SSL certificate with a Custom Certificate Authority Signed Certificate (2112277)](https://kb.vmware.com/s/article/2112277){:new_window}。|
|配置 vSphere 監視|vSphere 包含使用者可配置的事件及警示子系統，它會追蹤 vSphere 元件的事件並將資料儲存在日誌檔及 vCenter 資料庫中。事件是在 vSphere 物件上發生之使用者或系統動作的記錄。有三種類型的事件：「資訊」、「警告」和「錯誤」。警示是為了回應事件、一組條件或 vSphere 物件狀態而啟動的通知。警示具有下列嚴重性層次：正常 - 綠色、警告 - 黃色，以及警示 - 紅色。警示動作是為了回應警示而發生的作業，例如，傳送電子郵件通知。如需如何配置及使用 vSphere 監視的相關資訊，請參閱 [Monitoring Events, Alarms, and Automated Actions](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}。|
|新增、檢視及刪除叢集|您的 vCenter Server 實例已部署 vSphere ESXi 主機的叢集。您可以將其他叢集新增至您的實例，以擴充運算及儲存空間容量。如需相關資訊，請參閱[新增、檢視及刪除 vCenter Server 實例的叢集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters){:new_window}。|
| vCenter Server 容量|您可以根據商業需要，藉由新增或移除 vSphere ESXi 伺服器或是網路檔案系統 (NFS) 儲存空間來擴充或縮減 VMware vCenter Server 實例的容量。如需相關資訊，請參閱[擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers){:new_window}。|
| vCenter Server 實例服務|部署 vCenter Server 實例之後，您可以從我們的組合新增服務，例如災難回復、嚴重性或備份解決方案。當您不再需要這些服務時，可以從實例移除它們。如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices){:new_window}。|
| vCenter Server 實例更新|如需如何將更新套用至 vCenter Server 實例的相關資訊，請參閱[將 IBM 管理元件更新套用至 vCenter Server 實例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_applyingupdates#vc_applyingupdates)。只會針對管理元件自動進行這個將修補程式及更新套用至 vCenter Server 實例的處理程序。如需系統管理者手動套用 VMware 產品更新的相關資訊，請參閱 [vCenter Server on IBM Cloud with Hybridity Bundle 概觀](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-hybridity-intro#vcs-hybridity-intro){:new_window}。|
|多站台配置|多站台配置特性會搭配使用中心及分支拓蹼與主要站台及最多七個次要站台。如需配置 vCenter Server on {{site.data.keyword.cloud_notm}} 實例的多站台配置相關資訊，請參閱 [vCenter Server on IBM Cloud 實例的多站台配置](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_multisite#vc_multisite){:new_window}。如需在多站台配置中刪除 vCenter Server 實例的步驟相關資訊，請參閱[刪除多站台配置中的 vCenter Server 實例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_deletinginstance_multi#vc_deletinginstance_multi){:new_window}。|
|使用 VMware Update Manager |部署之後，您的系統管理者會更新 VMware 產品。如需系統管理者如何在 vCenter Server 實例中使用 VUM 的相關資訊，請參閱 [VMware Update Manager 簡介](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro){:new_window}。|
|重要 vCenter Server 實例元件備份|您的系統管理者負責配置、管理及監視 vCenter Server 實例的所有軟體元件（包括管理基礎架構及工作負載的備份和可用性）。在解決方案當中，您可以選擇部署 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}} 附加程式服務。Veeam 及 IBM Spectrum Protect Plus 可協助您滿足備份管理元件的需求。如需備份機制和要備份之重要元件的相關資訊，請參閱[備份元件](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html#vcenter-file-based-backup){:new_window}。|
|收集 VMware 產品的診斷資訊|VMware 技術支援中心在處理支援要求時，會定期要求診斷資訊。這項診斷資訊包含適用於該狀況的產品特定日誌、配置檔及資料。如需 VMware Knowledgebase 文章的 URL 及收集此資訊的詳細逐步作業等相關資訊，請參閱 [Collecting diagnostic information for VMware products (1008524)](https://kb.vmware.com/s/article/1008524?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。如需針對 VMware NSX Edge 裝置收集必要診斷資訊之程序的相關資訊，請參閱 [Collecting diagnostic information for VMware NSX Edge (2079380)](https://kb.vmware.com/s/article/2079380?lang=en_US#q=Collecting%20diagnostic%20information%20for%20VMware%20NSX%20Edge%20){:new_window}。|

## VM 程序
{: #opsprocs-configure-vm}

表 2. VM 程序

|標題|說明       |
|---|---|
|建立 VM |如需建立新 VM 的相關資訊，請參閱 [Create a Virtual Machine with the New Virtual Machine Wizard](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-AE8AFBF1-75D1-4172-988C-378C35C9FAF2.html?hWord=N4IghgNiBcIMICcCmYAuSAEYMDUCWCqArpBgLJgDGAFngHaYDueq1GrmAcko7gcaQo16mAOp4AXmAQATEAF8gA)。|
|配置 VM |如需配置 VM 硬體的相關資訊，請參閱 [Configuring Virtual Machine Hardware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-4AB8C63C-61EA-4202-8158-D9903E04A0ED.html){:new_window}。|
|在 VM 上安裝來賓 OS|如需將來賓 OS 安裝在 VM 上之程序的相關資訊，請參閱 [Installing a Guest Operating System](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-90E7F734-D699-4603-B222-AF4DE84459C7.html){:new_window}。|
|建立 Snapshot |Snapshot 會在您擷取 Snapshot 時擷取 VM 的整個狀態。您可以在 VM 開啟電源、關閉電源或暫停時擷取 Snapshot。如需相關資訊，請參閱 [Take a Snapshot in the VMware Host Client](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.html.hostclient.doc/GUID-A0D8E8E7-629B-466D-A50C-38705ACA7613.html){:new_window}。|
|回復 Snapshot |如需將 VM 狀態還原到 Snapshot 開始時之先前狀態的相關資訊，請參閱 [Restoring Snapshots](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E0080795-C2F0-4F05-907C-2F976433AC0D.html){:new_window}。|
|移除及新增 VM 和範本|如需從 vCenter 庫存移除 VM 及 VM 範本，或從磁碟刪除它們的相關資訊，請參閱 [Removing and Reregistering VMs and VM Templates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-376174FE-F936-4BE4-B8C2-48EED42F110B.html){:new_window}。|
| 升級 VM / 工具|如需將 VM 升級至更高相容性層次和更高 VMware 工具版本的相關資訊，請參閱 [Upgrading Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE77B0A9-F8FF-4785-BEAD-B6F04EE04492.html){:new_window}。|
|磁碟新增|如需將磁碟新增至現有 VM 的相關資訊，請參閱 [Add a Hard Disk to a Virtual Machine](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-79116E5D-22B3-4E84-86DF-49A8D16E7AF2.html){:new_window}。|
|磁碟收縮|如需將磁碟收縮至現有 VM 的相關資訊，請參閱 [Growing, thinning, and shrinking virtual disks for VMware ESX and ESXi (1002019)](https://kb.vmware.com/s/article/1002019){:new_window}。|
|磁碟擴充|如需為 VM 擴充現有磁碟大小的相關資訊，請參閱 [Change the Virtual Disk Configuration](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E1D541D1-DF96-467A-89B7-E84F83B2563D.html){:new_window}。|
|熱移轉|如需如何在相同叢集的 vSphere 主機之間，對 VM 進行 vMotion 的相關資訊，請參閱 [Managing Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-B7023DD7-F790-4DF8-89B4-FF09DA3DBFB1.html?hWord=N4IghgNiBcIBYHsAuACAtgSwOYCcxIFMUA3NEAXyA){:new_window}。|
|冷移轉|如需在 vCenter Server 實例之間移轉 VM 的相關資訊，請參閱 [Migrate a Powered Off or Suspended Virtual Machine](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E8DE930E-8079-4AC0-AEC2-B6EA1604F4E3.html){:new_window}。|
|移除 VM|如需移除 VM 的相關資訊，請參閱 [Remove VMs or VM Templates from vCenter Server or from the Datastore](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-27E53D26-F13F-4F94-8866-9C6CFA40471C.html){:new_window}。|
|磁碟移除|如需從 VM 移除磁碟的相關資訊，請參閱 [Remove a Hard Disk from a Virtual Machine](https://pubs.vmware.com/vsphere-4-esx-vcenter/index.jsp?topic=/com.vmware.vsphere.webaccess.doc_41/configuring_virtual_machine_options_and_resources/t_remove_an_existing_hard_disk.html){:new_window}。|
|VM 工具|如需更新 VM 工具的程序相關資訊，請參閱 [Creating baselines and attaching to inventory objects](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-baselines#vum-baselines)。|
|決定虛擬磁碟格式，並將虛擬磁碟從精簡佈建格式轉換成完整佈建格式|如需將 VM 磁碟轉換成完整佈建格式（如果它是以精簡佈建格式建立為虛擬磁碟）的程序相關資訊，請參閱 [Determine the Virtual Disk Format and Convert a Virtual Disk from the Thin Provision Format to a Thick Provision Format](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E8F50BEC-F575-4AB1-BC77-D9A13CDBDCF7.html){:new_window}。|
|AD/DNS 伺服器 OS 更新|Microsoft Active Directory (AD) / 網域名稱伺服器 (DNS) 自動設定為只下載更新。如需相關資訊，請參閱 [Windows 自動安裝更新](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_limitations#trbl_limitations-windows-update)。|

## vCenter 程序
{: #opsprocs-configure-vcenter}

表 3. vCenter 程序

|標題|說明       |
|---|---|
|備份 VCSA|如需相關資訊，請參閱 [vCenter Server Appliance 6.7 File-Based Backup and Restore Walkthroughs](https://blogs.vmware.com/vsphere/2018/05/vcenter-server-appliance-6-7-file-based-backup-and-restore-walkthroughs.html){:new_window}。|
| VSCA/PSC 修補|如需相關資訊，請參閱 [Patching the vCenter Server Appliance and Platform Services Controller Appliance](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-043EF6BD-78F7-412F-837F-CBDF844F850C.html){:new_window}。|
|停止、啟動或重新啟動 VCSA 服務|為了疑難排解和維護，有時需要變更 VMware vCenter Server Appliance (VCSA) 服務的狀態。如需相關資訊，請參閱 [Stopping, starting, or restarting VMware vCenter Server Appliance 6.x services (2109887)](https://kb.vmware.com/s/article/2109887?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。|
|VCSA 備份及還原選項的概觀|	如需相關資訊，請參閱 [Overview of Backup and Restore options in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window}。|
|配置 vCenter 電子郵件通知|如需配置電子郵件通知，以便在針對已定義的警示及自訂建立的警示觸發特定條件時，傳送至電子郵件位址的相關資訊，請參閱 [Configuring an email alert for the vCenter Server alarm (2123925)](https://kb.vmware.com/s/article/2123925?lang=en_US){:new_window}。|

## vSphere ESXi 主機程序
{: #opsprocs-configure-host}

表 4. vSphere ESXi 主機程序

|標題|說明       |
|---|---|
| vSphere 主機維護|當需要執行維護作業，例如升級或實體裝置更換時，會將主機置於維護模式。僅在系統管理者要求時，主機才會進入或離開維護模式。在進入維護模式的主機上執行的 VM 需要（以手動方式或由 DRS 自動）移轉至另一部主機，或將它關閉。如需相關資訊，請參閱 [Place a Host in Maintenance Mode](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html?hWord=N4IghgNiBcIG4GUAOALApgJzQAgBIHsBnAF2wFkwBLAO2LWrGoGM0QBfIA){:new_window}。|
|新增 vSphere ESXi 主機|如需相關資訊，請參閱[將 ESXi 伺服器新增至 vCenter Server 實例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-adding){:new_window}。
|移除 vSphere ESXi 主機|	如需相關資訊，請參閱[移除 ESXi 伺服器的程序](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing-procedure){:new_window}。|
| Bare Metal Server 韌體修補|如需相關資訊，請參閱[裸機伺服器韌體過時怎麼辦？](/docs/bare-metal/faq.html#what-if-my-bare-metal-server-has-out-of-date-firmware-){:new_window}。|
| vSphere ESXi 主機修補|如需使用 VMware Update Manager (VUM) 更新 vSphere ESXi 主機和若干其他 vCenter Serer 實例元件的相關資訊，請參閱 [VMware Update Manager 簡介](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro){:new_window}。|
|測試主機網路連線|如需驗證 vSphere ESXi 主機實體網路配接卡與實體交換器之間網路鏈結是否已啟動且可供使用的相關資訊，請參閱 [Verifying network links (1003724)](https://kb.vmware.com/s/article/1003724?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。|
|判斷 ESXi 中的網路/儲存空間韌體和驅動程式版本|如需相關資訊，請參閱 [Determining Network/Storage firmware and driver version in ESXi 4.x and later (1027206)](https://kb.vmware.com/s/article/1027206?lang=en_US#q=network%20interface%20card%20error){:new_window}。|
|疑難排解 ESXi 的網路及 TCP/UDP 埠連線功能問題|如需相關資訊，請參閱 [Troubleshooting network and TCP/UDP port connectivity issues on ESX/ESXi (2020669)](https://kb.vmware.com/s/article/2020669?lang=en_US#q=network%20interface%20card%20error){:new_window}。|

## 儲存空間程序
{: #opsprocs-configure-storage}

表 5. 儲存空間程序

|標題|說明       |
|---|---|
|新增 {{site.data.keyword.cloud_notm}} 耐久性 NFS 儲存空間|如需將 {{site.data.keyword.cloud_notm}} 耐久性 NFS 共用新增至現有叢集的相關資訊，請參閱[將 NFS 儲存空間新增至 vCenter Server 實例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances){:new_window}。|
|移除 {{site.data.keyword.cloud_notm}} 耐久性 NFS 儲存空間|如需將 {{site.data.keyword.cloud_notm}} 耐久性 NFS 共用從現有叢集移除的相關資訊，請參閱[從 vCenter Server 實例移除 NFS 儲存空間](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing-nfs-storage){:new_window}。
|加大 {{site.data.keyword.cloud_notm}} 耐久性 NFS 儲存空間|如需將額外容量新增至 {{site.data.keyword.cloud_notm}} 耐久性 NFS 共用的相關資訊，請參閱[擴充 Block Storage 容量](/docs/infrastructure/BlockStorage?topic=BlockStorage-expandingcapacity#expandingcapacity){:new_window}。|
|收縮 {{site.data.keyword.cloud_notm}} 耐久性 NFS 儲存空間|如需將收縮容量新增至 {{site.data.keyword.cloud_notm}} 耐久性 NFS 共用的相關資訊，請參閱[擴充 Block Storage 容量](/docs/infrastructure/BlockStorage?topic=BlockStorage-expandingcapacity#expandingcapacity){:new_window}。|
|vSAN 原則最佳作法建議|如需相關資訊，請參閱 [vSAN 原則設計](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure#design_virtualinfrastructure-storage-policy){:new_window}。|
|啟用 vSAN 性能檢查|如需相關資訊，請參閱[啟用 vSAN 線上性能工作流程](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vsan#vum-updating-vsan-enable-vsan-workflow){:new_window}及 [vSAN Health Check Information (2114803)](https://kb.vmware.com/s/article/2114803){:new_window}。|
|啟用加密|	如需使用 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務啟用加密的相關資訊，請參閱 [KMIP for VMware on IBM Cloud 概觀](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations)。如需啟用 VM 加密的相關資訊，請參閱 [Virtual Machine Encryption](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.security.doc/GUID-E6C5CE29-CD1D-4555-859C-A0492E7CB45D.html){:new_window}。如需使用靜態資料加密保護 vSAN 叢集裡的資料的相關資訊，請參閱 [Using Encryption on a vSAN Cluster](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-F3B2714F-3406-48E7-AC2D-3677355C94D3.html){:new_window}。|
|新增其他 vSAN 儲存空間|如需將其他 vSphere ESXi 主機新增至現有 vSAN 叢集的相關資訊，請參閱[將 ESXi 伺服器新增至 vCenter Server 實例](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-adding){:new_window}。新增其他主機會將 CPU、RAM 及儲存空間增加到您的叢集。如需 vSAN 技術的相關資訊，請參閱 [Expanding a vSAN Cluster](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-666D9839-2726-4936-8C0F-94476ECE0606.html){:new_window}。|
|移除 vSAN 儲存空間|如需從 vSAN 叢集移除儲存空間的相關資訊，請參閱[從 vCenter Server 實例移除 ESXi 伺服器](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing){:new_window}。移除主機會減少您叢集裡的 CPU、RAM 及儲存空間。|
|使用預設的 vSAN 警示|預設的 vSAN 警示可用來監視叢集、主機及現有 vSAN 授權。在對應於警示的事件受到啟動時，或是符合警示中指定的其中一個或所有條件時，會自動觸發這些警示。您無法編輯預設警示的條件或刪除預設警示。若要配置您需求特有的警示，請為 vSAN 建立自訂警示。請參閱「建立 vSAN 事件的 vCenter Server 警示」。如需監視警示、事件、編輯現有警示設定以及使用預設 vSAN 警示來監視叢集、主機、分析任何新事件，以及評量整體叢集性能的相關資訊，請參閱 [Using the vSAN Default Alarms](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-E7885CDE-654D-4732-A5FE-31D0AB2B2F57.html){:new_window}。|
|啟用 SIOC|依預設，已停用「儲存空間 IO 控制 (SIOC)」。如果資料儲存庫中的 VM 效能不佳，您可以啟用 SIOC，以協助設定儲存空間資源的優先順序。只有在有儲存空間競用時才會啟動 SIOC，以確保每部 VM 都能取得儲存空間資源的公平份額。使用 VM 儲存空間原則，並將該原則指派給 VM 或 VMDK 可達到這點。如需相關資訊，請參閱 [Managing Storage I/O Resources](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-7686FEC3-1FAC-4DA7-B698-B808C44E5E96.html){:new_window}。|
|配置資料儲存庫叢集|資料儲存庫叢集是含有共用資源的資料儲存庫，以及共用管理介面的集合。資料儲存庫叢集對於資料儲存庫而言，就如同叢集對於主機。建立資料儲存庫叢集時，您可以使用 vSphere Storage DRS 來管理儲存空間資源。將資料儲存庫新增至資料儲存庫叢集時，資料儲存庫的資源會變成資料儲存庫叢集資源的一部分。您可以使用資料儲存庫叢集來聚集儲存空間資源，這可讓您在資料儲存庫叢集層次支援資源配置原則。下列資源管理功能也可用於每個資料儲存庫叢集。如需相關資訊，請參閱 [Creating a Datastore Cluster](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-598DF695-107E-406B-9C95-0AF961FC227A.html){:new_window}。|


## 網路程序
{: #opsprocs-configure-networks}

表 6. 網路程序

|標題|說明       |
|---|---|
|網路考量|如需相關資訊，請參閱 [vCenter Server 實例的網路考量](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_networkingonvcenterserver){:new_window}. |
|HCX 的規劃|VMware 混合雲端服務 (HCX) 可讓 vSphere 軟體定義的資料中心 (SDDC) 的不同實例在各種網路類型之間交互作業。HCX 設計的宗旨是要解決安全、相容性、複雜性和效能問題，當您嘗試達到多重實例、多網站部署 vSphere，跨越內部部署和雲端提供者界限進行延伸時，會遇到這些問題。如需相關資訊，請參閱[部署前的規劃](/docs/services/vmwaresolutions?topic=vmware-solutions-vcshcx-planning#vcshcx-planning){:new_window}。|
|起始 NSX 配置|在部署 vCenter Server 實例時，會有一個範例客戶網路可用，它包含專用子網路、公用子網路、NSX 邏輯交換器、分散式邏輯路由器，並且會部署並配置 NSX Edge 應用裝置以執行網址轉換。如需為 VM 配置此範例客戶網路的步驟，請參閱[配置網路以使用客戶管理的 NSX ESG 來搭配您的 VM](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_esg_config#vc_esg_config){:new_window}。|
|新增邏輯交換器|邏輯交換器類似於 VLAN，因為它們提供網路連線，而您可以將 VM 連接至這些網路連線。如果 VM 連接至相同的邏輯交換器，則 VM 便可以透過 VXLAN 彼此通訊。當您新增邏輯交換器時，請務必記住您要建置的特定拓蹼。如需相關資訊，請參閱 [Add a Logical Switch](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-DD31D6BC-2E56-4E91-B45F-FCA3E80FF786.html){:new_window}。|
|新增 DLR|「分散式邏輯路由器 (DLR)」是在連接的邏輯交換器之間，進行遞送的虛擬應用裝置（東西向資料流量）。如需相關資訊，請參閱 [Add a Distributed Logical Router](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-E825C0C7-F4CC-4B26-90AF-A2167AC519DB.html){:new_window}。|
|新增 ESG|「外部服務閘道 (ESG)」是在實體網路與邏輯網路之間，進行遞送的虛擬應用裝置（南北向資料流量）。如需相關資訊，請參閱 [Add an Edge Services Gateway](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-B9A97F20-4996-4E16-822C-0B98DDE70571.html){:new_window}。|
|配置 NSX 邊緣防火牆規則|邊緣防火牆會監視南北向資料流量，以提供周邊安全功能，包括防火牆、網址轉換 (NAT) 以及站台對站台的 IPSec 和 SSL VPN 功能。只有管理及/或上行鏈路介面上的防火牆規則會適用。如需相關資訊，請參閱 [Working with NSX Edge Firewall Rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-178B11B8-FEB1-49B8-B6FF-D069C41EEB32.html){:new_window}。|
|分散式防火牆|分散式防火牆是內嵌了 Hypervisor 核心的防火牆，可提供 VM 的網路存取控制。建立存取控制原則時請根據 VMware vCenter 物件，例如資料中心、叢集、VM 名稱、IP、VLAN（DVS 埠群組）、VXLAN（邏輯交換器）、安全群組以及來自 Active Directory 的使用者群組身分。防火牆規則會在每部 VM 的 vNIC 層次施行，以便即使 VM 被執行 vMotion 的情況下也能提供一致的存取控制。如需相關資訊，請參閱 [Distributed Firewall](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-95600C1C-FE9A-4652-821B-5BCFE2FD8AFB.html){:new_window}。|
|配置 NAT 規則|NSX Edge 提供「網址轉換 (NAT)」服務，以指派不同的來源或目的地 IP 位址給 VM 或 VM 群組。NAT 服務配置會分成「來源 NAT (SNAT)」及「目的地 NAT (DNAT)」規則。如需相關資訊，請參閱 [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}。|
|配置 NSX 負載平衡器|NSX Edge 負載平衡器能啟用高可用性服務，並將網路資料流量負載分散在多部 VM。它會將送入的服務要求平均分散在多部 VM 之間，讓使用者不會察覺負載分散。負載平衡有助於達到最佳資源使用率、傳輸量最大化、回應時間縮至最短，並且避免超載。NSX Edge 提供最高第 7 層的負載平衡。您可以將外部或公用 IP 位址對映至一組內部 VM 以進行負載平衡。負載平衡器會在外部 IP 位址上接受 TCP、UDP、HTTP 或 HTTPS 要求，並決定要使用的內部伺服器。埠 80 是 HTTP 的預設埠，而埠 443 是 HTTPS 的預設埠。在 NSX 中有兩種類型的負載平衡服務可用：單臂模式（Proxy 模式）或行內模式（透通模式）。如需相關資訊，請參閱 [Logical Load Balancer](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-152982CF-108F-47A6-B86A-0F0F6A56D628.html){:new_window}。|
|變更 NSX 密碼|如需相關資訊，請參閱[防火牆考量](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_networkingonvcenterserver#vc_networkingonvcenterserver-firewall-considerations)。|
|部署 Juniper vSRX 應用裝置|[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)會將一組 FortiGate Virtual Appliance 部署到您的環境，以協助您在虛擬基礎架構內實作重要安全控制來降低風險。不過，如果這項服務不適合您，則您可以視需要自行實作協力廠商解決方案，請將 vSRX 閘道新增至 vCenter Server 實例。如需相關資訊，請參閱 [Installing vSRX with VMware vSphere Web Client](https://www.juniper.net/documentation/en_US/vsrx/topics/task/installation/security-vsrx-vsphere-client-installing.html){:new_window}。|
|部署 Palo Alto VM-Series 防火牆|[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)會將一組 FortiGate Virtual Appliance 部署到您的環境，以協助您在虛擬基礎架構內實作重要安全控制來降低風險。不過，如果這項服務不適合您，則您可以視需要自行實作協力廠商解決方案。如需將 Palo Alto VM-Series 防火牆新增至 vCenter Server 實例的相關資訊，請參閱 [Set Up a VM-Series Firewall on an ESXi Server](https://docs.paloaltonetworks.com/vm-series/8-0/vm-series-deployment/set-up-a-vm-series-firewall-on-an-esxi-server.html#){:new_window}。|
|部署 Cisco Firepower 應用裝置|[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)會將一組 FortiGate Virtual Appliance 部署到您的環境，以協助您在虛擬基礎架構內實作重要安全控制來降低風險。不過，如果這項服務不適合您，則您可以視需要自行實作協力廠商解決方案。如需將 Cisco Firepower 應用裝置新增至 vCenter Server 實例的相關資訊，請參閱 [Deploy the Firepower Threat Defense Virtual Using the VMware vSphere Web Client or vSphere Hypervisor](https://www.cisco.com/c/en/us/td/docs/security/firepower/quick_start/vmware/ftdv/ftdv-vmware-qsg.html#17970){:new_window}。|
|Direct Link|在部署 vCenter Server 實例之後，您的系統管理者可以透過 {{site.data.keyword.cloud_notm}} 管理 VPN 連接至您的實例。然後您的系統管理者便可以為您的工作負載配置網際網路存取。不過，您可能想要使用直接連線，而不是網際網路。{{site.data.keyword.cloud_notm}} Direct Link 是四項 {{site.data.keyword.cloud_notm}} Network 供應項目的套組，提供於全球各地的位置。每一個都可讓客戶在其遠端網路環境與 {{site.data.keyword.cloud_notm}} 部署之間建立直接的專用連線，而不必使用公用網際網路。一般而言，這些供應項目的實作目的是支援混合式工作負載、跨提供者的工作負載、大量或頻繁的資料傳送、專用工作負載，或簡化 {{site.data.keyword.cloud_notm}} 環境的管理。如需相關資訊，請參閱[開始使用 IBM Cloud Direct Link](/docs/infrastructure/direct-link?topic=direct-link-get-started-with-ibm-cloud-direct-link#get-started-with-ibm-cloud-direct-link){:new_window}。如需只能使用專用網路存取之 vCenter Server 實例的相關資訊，請參閱[公用或專用網路](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-public-private-network){:new_window}。|
|部署 Web Proxy|	部署 VMware Server 實例時，vCenter Server Appliance (VCSA) 無法直接存取 VMware 儲存庫，以啟用 vSAN 性能檢查的更新。如需部署 Squid Web Proxy VM 以啟用這些儲存庫，請參閱[起始配置](/docs/services/vmwaresolutions/archiref/vum/vum-init-config.html#install-and-configure-squid){:new_window}。此程序也與不同供應商的其他 Proxy 應用程式相關。|
|防火牆記載|NSX 邊緣和分散式防火牆會產生並儲存日誌檔，例如審核日誌、規則訊息日誌，以及系統事件日誌。您必須為已啟用防火牆的每個叢集配置 syslog 伺服器。如需相關資訊，請參閱 [Firewall Logs](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-6F9DC53E-222D-464B-8613-AB2D517CE5E3.html){:new_window}。{{site.data.keyword.cloud_notm}} 中的 Operations Management 包含 vRealize Log Insights，它充當 syslog 伺服器。|
|NSX 記載及系統事件|如需針對 NSX 元件配置 syslog 伺服器的相關資訊，以及系統事件、警示、審核日誌及收集技術支援日誌的相關資訊，請參閱 [NSX 記載及系統事件](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.logging.doc/GUID-3F08DC2E-2D82-4C89-8829-EF1EA0160B13.html){:new_window}。|
|部署 HCX（內部部署）|如需相關資訊，請參閱[內部部署 VMware HCX on IBM Cloud 實例的考量](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_considerations#standalone_considerations){:new_window}。|
|HCA 檢查|HCX on {{site.data.keyword.cloud_notm}} 服務會將內部部署資料中心的網路無縫地擴充至 {{site.data.keyword.cloud_notm}}，這容許您將 VM 移轉至 {{site.data.keyword.cloud_notm}} 或從該處移轉，而不需要進行任何轉換或變更。如需存取 HCX Cloud Management 主控台及將更新套用至 HCX on {{site.data.keyword.cloud_notm}} 的相關資訊，請參閱[管理 VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx#managing-vmware-hcx-on-ibm-cloud)。|


## 相關鏈結
{: #opsprocs-configure-links}

* [VMware vSphere 文件](https://docs.vmware.com/en/VMware-vSphere/index.html){:new_window}
* [NSX Installation Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-DD31D6BC-2E56-4E91-B45F-FCA3E80FF786.html){:new_window}
* [NSX Administration Guide ](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-B5C70003-8194-4EC3-AB36-54C848508818.html){:new_window}
* [VMware vSAN Administration Guide](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-AEF15062-1ED9-4E2B-BA12-A5CE0932B976.html){:new_window}
* [變更 vCenter Server 構件的考量](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
