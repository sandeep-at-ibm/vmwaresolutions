---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# 2.9 版的版本注意事項
{: #relnotes_v29}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VMware vCenter Server on IBM Cloud with NSX-T
{: #relnotes_v29-vcs-nsx-t}

此版本引進 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T 供應項目，作為概念證明或沙盤推演測試供應項目。vCenter Server with NSX-T 是專用的受管理雲端，可讓您測試驅動 VMWare 新一代網路平台 NSX-T。

如需相關資訊，請參閱下列主題：

* [vCenter Server with NSX-T 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [訂購 vCenter Server with NSX-T 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## VMware Cloud Foundation on IBM Cloud 終止支援
{: #relnotes_v29-vcf-eos}

為了整合產品與服務來為客戶提供更好的體驗，{{site.data.keyword.cloud_notm}} 將從 2019 年 5 月 13 日起停止對 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 提供支援。在此之後，所有客戶將被導向至 VMware vCenter Server on {{site.data.keyword.cloud_notm}}，提供更靈活而有彈性的儲存空間和授權選項。使用 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的現有客戶將在 2019 年 5 月 13 日終止支援之前，獲得移轉至 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的相關協助。

5 月 13 日之後，VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的相關管理功能將會從 {{site.data.keyword.vmwaresolutions_short}} 主控台移除。尚未移轉至 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的實例可以透過 IBM Cloud 基礎架構主控台來存取。

{{site.data.keyword.cloud_notm}} 支援中心將會在 2019 年 3 月 25 日之前聯絡客戶以開始移轉 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}。如需現有客戶移轉選項的相關資訊，請參閱 [{{site.data.keyword.vmwaresolutions_short}} Wiki 頁面](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}。客戶可以在 [{{site.data.keyword.vmwaresolutions_short}} 主控台](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted)上檢視自己的現有 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 實例。

## VMware vSphere 6.7 Update 1 支援
{: #relnotes_v29-vsphere}

您現在可以選擇訂購 VMware vSphere 6.7 版 Update 1（具有 VMware vCenter Server）、VMware vCenter Server（具有 Hybridity Bundle），以及 VMware vSphere on {{site.data.keyword.cloud_notm}} 實例。

此外，「單一節點試用版移轉及應用程式現代化」實例現在要和 vSphere Enterprise Plus 6.7u1 一起訂購。

vSphere Enterprise Plus 6.7u1 僅適用於 Broadwell 及 Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}。

如需相關資訊，請參閱下列主題中的_授權設定_小節：

* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [訂購 vCenter Server with Hybridity Bundle 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## VLAN Spanning 終止支援
{: #relnotes_v29-vlan}

從 2019 年 8 月起，{{site.data.keyword.vmwaresolutions_short}} 將不再支援 VLAN Spanning。在 2019 年 7 月底之前，您必須將您的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶轉換至「虛擬遞送及轉遞 (VRF)」並為您的帳戶啟用「服務端點」。

如需相關資訊，請參閱：

* [IBM Cloud 上的虛擬遞送及轉遞 (VRF) 概觀](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [使用 IBM Cloud CLI 啟用可使用服務端點的帳戶](/docs/services/service-endpoint?topic=services/service-endpoint-cs_cli_install_steps)

## 支援應用程式設計介面
{: #relnotes_v29-api}

應用程式設計介面 (API) 珼在已可用於部署實例、刪除實例，以及新增和移除 ESXi 伺服器和叢集。

使用者說明文件中的*參照*區段中也提供了 REST API 文件。如需相關資訊，請參閱 [{{site.data.keyword.vmwaresolutions_short}} API](https://console.bluemix.net/apidocs/vmware-solutions)。

## VMware vCenter Server 實例的更新
{: #relnotes_v29-vcs}

此版本會套用下列升級及改善：

* vSphere ESXi 6.7 Update 1（建置 6.7.0-11675023）
* vSphere ESXi 6.5 Update 2（建置 6.5.0-11925212）
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1（建置 6.7.0-10244745）
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4（建置 11197766）
* NSX-T for vSphere 2.4

如需選取 VMWare 元件的相關資訊，請參閱 [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

### ESXi 伺服器加強功能
{: #relnotes_v29-vcs-esxi}

* 現在，ESXi 伺服器已經在交付之前停用「安全 Shell (SSH) 通訊協定」。
* 從 2.9 版開始，可用的 ESXi 伺服器作業如下：

   * 在伺服器處於維護模式將新的 ESXi 伺服器新增至現有叢集。在您從維護模式移除虛擬機器之前，虛擬機器不會移轉至新的伺服器。
   * 在實例中跨越多個叢集同時新增或移除 ESXi 伺服器。

如需相關資訊，請參閱[擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)。

### 網路檔案系統儲存空間大小
{: #relnotes_v29-vcs-nfs}

對於 vCenter Server 實例訂單，您現在可以為效能層次 0.25、2 和 4 IOPS/GB 最多新增 24 TB 的「網路檔案系統 (NFS)」共用儲存體。

10 IOPS/GB 效能層次仍然限制為每個檔案共用的容量上限為 4 TB。
{:note}

## 附加服務的更新
{: #relnotes_v29-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v29-services-caveonix}

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服務現在已可用於部署在（或升級至）2.9 版或更新版本的 VMware vCenter Server 實例。此服務可以透過主動監視和自動化防禦控制來防範威脅及因應業界或政府規章，以協助管理網路和法規遵循風險。

您可以訂購內含 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服務的 vCenter Server 實例，也可以在以後從實例詳細資料頁面上的**服務**標籤，將此服務新增至您的現有 vCenter Server 實例。

您也可以訂購獨立式 Caveonix RiskForesight 授權而不要使其與任何 VMWare 實例相關聯，以進行內部部署工作負載的授權和啟動。

如需相關資訊，請參閱：
* [Considerations for Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 的考量](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [訂購 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Caveonix 授權的考量](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [訂購 Caveonix 授權](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

在現行版本中，F5-BigIP VE V14.1.0.2 安裝在新部署的實例上。如需 F5-BigIP VE V14.1.0.2 新增特性的相關資訊，請參閱[版本注意事項：BIG-IP 14.1.0 新增與安裝](https://support.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window}.

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

在現行版本中，HyTrust CloudControl 5.4.2 安裝在所有新部署的實例上。如需 HyTrust CloudControl 5.4.2 版的新增特性相關資訊，請參閱 [HyTrust CloudControl 5.4.2 版版本注意事項](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

現在，雪梨的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務提供兩個新的端點。如需相關資訊，請參閱 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務配置](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config)。

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

在現行版本中，Veeam Backup and Replication 9.5 Update 4 安裝在所有新部署的實例上，如需 Veeam 9.5u4 中新增特性的相關資訊，請參閱 [Veeam Backup and Replication 9.5 Update 4 的版本資訊](https://www.veeam.com/kb2878){:new_window}。

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

在現行版本中，Zerto Virtual Replication 6.5 Update 3 安裝在所有新部署的實例上。如需 Zerto Virtual Replication 6.5 Update 3 中新增特性的相關資訊，請參閱 [Zerto Virtual Replication V6.5 Update 3 的版本注意事項](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window}。

## 使用者介面更新和加強功能
{: #relnotes_v29-ui}

使用者介面已更新，並提供下列加強功能：

* 在**基礎架構**頁面上，新的**網路介面**表格提供 VLAN 子網路以及您的叢集的 IP 位址詳細資料。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
