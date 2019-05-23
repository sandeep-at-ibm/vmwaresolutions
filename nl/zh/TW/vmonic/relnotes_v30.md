---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# 3.0 版的版本注意事項
{: #relnotes_v30}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VMware Cloud Foundation on IBM Cloud 終止支援
{: #relnotes_v30-vcf-eos}

為了致力於整合產品與服務來為客戶提供更好的體驗，從 2019 年 5 月 13 日起，{{site.data.keyword.vmwaresolutions_short}} 平台將不再提供 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 支援。

在此之後，所有客戶將被導向至 VMware vCenter Server on {{site.data.keyword.cloud_notm}}，這是我們在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 上的旗艦 VMware Software-Defined Data Center 解決方案。

使用 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的現有客戶將在 2019 年 5 月 13 日終止支援之前，獲得轉換為 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的相關協助。

5 月 13 日之後，VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的管理能力將凍結而無法在 {{site.data.keyword.vmwaresolutions_short}} 主控台中使用，直到它們轉換為 VMware vCenter Server on {{site.data.keyword.cloud_notm}}。選擇不要將其 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 實例移轉至或轉換為 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的客戶，可從 {{site.data.keyword.cloud_notm}} 基礎架構主控台存取其實例。

## 已移除 Broadwell 2-CPU 伺服器的支援
{: #relnotes_v30-broadwell}

從 3.0 版開始，Broadwell 2-CPU 伺服器無法再用於部署新的 vCenter Server、vCenter Server with Hybridity Bundle、vCenter Server with NSX-T，以及 vSphere on {{site.data.keyword.cloud_notm}} 實例和叢集。您仍可以將伺服器新增至現有叢集。

## 網路檔案系統作業加強功能
{: #relnotes_v30-nfs}

從 3.0 版開始，您可以在叢集中同時新增或移除 NFS 儲存空間及**備妥使用**狀態的 ESXi 伺服器。例如，您可以在一個叢集裡新增或移除 ESXi 伺服器，然後在另一個叢集裡新增或移除 NFS 儲存空間。這適用於所有 vCenter Server 及 vCenter Server with NSX-T 實例。

## VMware vCenter Server 實例的更新
{: #relnotes_v30-vcs}

此版本會套用下列升級及改善：

* vSphere ESXi 6.7 Update 1（建置 6.7.0-13004448）
* vSphere ESXi 6.5 Update 2（建置 6.5.0-13004031）
* vCenter Server Appliance 6.7 Update 1b（建置 6.7.0-11727113）
* Platform Services Controller 6.7 Update 1b（建置 6.7.0-11727113）

如需相關資訊，請參閱 [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

針對 Microsoft Active Directory (AD) 及 DNS（網域名稱系統）服務訂購的 Windows 軟體，會針對這兩個配置選項升級至 Windows Server 2016：VSI（虛擬伺服器實例）及兩個高可用性 Windows VM。如需選取 VMware 元件的相關資訊，請參閱 [Software BOM for vCenter Server 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software)。

### vSAN 儲存空間加強功能
{: #relnotes_v30-vcs-vsan}

* 使用 vSAN 儲存空間時，您可以訂購的 Bare Metal Server 數目現在可以大於四。這適用於所有 vCenter Server、vCenter Server with Hybridity，以及 vCenter Server with NSX-T 實例。
* 從 3.0 版開始，M.2 固態磁碟機會隨您的 vSAN 儲存空間實例一起訂購。如果您選取 **Intel Optane 的高效能**選項，則最多可以訂購 10 個容量磁碟或總共 12 個容量磁碟。

如需相關資訊，請參閱下列主題中的*儲存空間儲存* 小節：
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [訂購 vCenter Server with Hybridity Bundle 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [訂購 vCenter Server with NSX-T 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## 附加服務的更新項目
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

在現行版本中，HyTrust CloudControl 5.5 安裝在所有新部署的實例上。如需 HyTrust CloudControl 5.5 中新增特性的相關資訊，請參閱 [HyTrust CloudControl 5.5 版的新增功能](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}。

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

現行版本會將 HyTrust DataControl 4.3 安裝在所有新部署的實例。如需 HyTrust DataControl 4.3 中新增特性的相關資訊，請參閱 [KeyControl 及 DataControl 4.3 版的新增功能](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}。

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

現行版本會將 HyTrust KeyControl 4.3 安裝在所有新部署的實例。如需 HyTrust KeyControl 4.3 中新增特性的相關資訊，請參閱 [KeyControl 及 DataControl 4.3 版的新增功能](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}。

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

現行版本會將 {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 與 {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 一起安裝在所有新部署的實例上。

如需 {{site.data.keyword.cloud_notm}} Private 3.1.2 版中新增特性的相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} Private 3.1.2 版的新增功能](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}。
如需 {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 中新增特性的相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 的新增功能](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}。

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

現在，倫敦及美國東部的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務提供兩個新的端點。如需相關資訊，請參閱 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務配置](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config)。

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

現行版本會將 IBM Spectrum Protect™ Plus 10.1.3 版安裝在所有新部署的實例。如需 IBM Spectrum Protect Plus 10.1.3 版中新增特性的相關資訊，請參閱 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}。

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

現在，您可以在僅限專用的實例上新增 Zerto on {{site.data.keyword.cloud_notm}}。如果您選擇將 Zerto 安裝在僅限專用的實例上，則必須設定您自己的 Proxy 伺服器，同時配置 Zerto 的 Call Home 特性。如需相關資訊，請參閱[訂購 Zerto on {{site.data.keyword.cloud_notm}}，以取得僅限專用網路的實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only)。

## 新文件與更新的文件

* 現在有可用的文件，協助您將 {{site.data.keyword.vmwaresolutions_short}} 元件升級至 VMware vSphere 6.7。如果您想要繼續從 {{site.data.keyword.vmwaresolutions_short}} 自動化獲益，則需要此升級。如需相關資訊，請參閱[將 vCenter Server vSphere 軟體從 VMware vSphere 6.5 升級至 6.7](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade)。
* 現在有可用的參考文件，提供您 {{site.data.keyword.vmwaresolutions_short}} 維護的使用者 ID，以供 {{site.data.keyword.cloud_notm}} 自動化使用。顯示在實例歷程日誌中的可能訊息也可供您檢閱。如需相關資訊，請參閱 [IBM 使用者 ID](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) 和[實例歷程訊息](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages)。
* **重新開機/控制**許可權已新增至表格，說明 IBM Cloud 基礎架構帳戶的必要許可權。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 基礎架構帳戶的許可權](/docs/services/vmwaresolutions/services?topic=vmware-solutions-slaccountrequirement#slaccountrequirement-permissions)。
* 下列 API 提供了新的參考文件。如需相關資訊，請參閱 [API 參考資料](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}。
  * 列出所指定 VMware vCenter Server 實例的所有歷程訊息
  * 將共用儲存空間新增至指定的叢集
  * 從指定的叢集中刪除 NFS 儲存空間

## 使用者介面更新和加強功能
{: #relnotes_v30-ui}

使用者介面已更新，並提供下列加強功能：

* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
