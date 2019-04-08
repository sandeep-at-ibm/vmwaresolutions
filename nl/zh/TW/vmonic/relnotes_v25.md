---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-30"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 2.5 版的版本注意事項
{: #relnotes_v25}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 及 Meltdown 補救
{: #relnotes_v25-spectre}

{{site.data.keyword.vmwaresolutions_short}} 發行來自 VMware 的修補程式，以回應已知的 Spectre 及 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 及 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## NSX 元件更新
{: #relnotes_v25-nsx}

針對 VMware vCenter Server on {{site.data.keyword.cloud_notm}}、VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 及 NetApp ONTAP Select 的新部署，此版本會安裝 VMware NSX for vSphere 6.4.1。

## 移除預設備份配置
{: #relnotes_v25-default-backup}

{{site.data.keyword.vmwaresolutions_short}} 提供兩個適用於備份的整合式附加程式服務：IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 及 Veeam on {{site.data.keyword.cloud_notm}}。使用這些服務，您可以規劃及提供管理基礎架構與工作負載的回復。此外，IBM Resiliency Services 還會提供 Veeam 備份的受管理服務。

從 2.5 版開始，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 及 Veeam on {{site.data.keyword.cloud_notm}} 服務，在部署時將不再預先配置任何 VM 的備份。此變更容許您確保適當地配置備份工作的所有層面，包括排程、保留期間、使用刪除重複、監視和警示，以及加密金鑰的管理。此外，IBM CloudDriver VM 不再配置為 NSX 備份的持續性檔案伺服器。

您負責配置、管理及監視所有軟體元件（包括管理基礎架構及工作負載的備份和可用性）。如需相關資訊，請參閱[備份元件](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#backing-up-components)。

此變更不會影響 2.5 版之前所部署並且已安裝 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}} 服務的實例。
{:note}

## IBM CloudDriver 備援
{: #relnotes_v25-cloud-driver}

對於 2.5 版或更新版本中部署的實例或升級至 2.5 版或更新版本的實例，IBM CloudDriver 元件將不再配置為 vSphere 叢集內的虛擬機器 (VM)。相反地，它會視需要部署為 {{site.data.keyword.cloud_notm}} 基礎架構虛擬伺服器實例 (VSI)，並使用最新的 {{site.data.keyword.cloud_notm}} for VMware 程式碼來進行部署更多節點、叢集或服務這類作業。此外，IBM CloudDriver 已變更為使用 {{site.data.keyword.cloud_notm}} 專用網路與 {{site.data.keyword.cloud_notm}} 管理平面通訊。由於此項變更，已移除允許 IBM CloudDriver 往外與公用網路通訊的管理 NSX Edge Services Gateway (ESG) 防火牆及網路位址轉譯 (NAT) 規則。

部分附加程式服務（例如 F5 on {{site.data.keyword.cloud_notm}}、FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 及 Zerto on {{site.data.keyword.cloud_notm}}）仍然需要公用網路存取權，因此管理 NSX ESG 還是會部署在所有實例中。

## 已啟用 IAM 功能的使用者及存取管理
{: #relnotes_v25-iam}

從 2.5 版開始，{{site.data.keyword.vmwaresolutions_short}} 已與 IBM Identity and Access Management (IAM) 整合，以提供在您的 {{site.data.keyword.cloud_notm}} 帳戶內管理使用者帳戶及使用者存取權的統一方法。因為：
* 您現在可以將多位使用者新增至您的 {{site.data.keyword.cloud_notm}} 帳戶以進行協同作業，而且可以藉由將不同的平台存取角色指派給他們，來管理他們對您帳戶中所佈建服務及資源的存取權。  
* 在 2.5 版及更新版本中部署的實例，會自動鏈結至訂購實例時所使用的使用者帳戶。
* 對於已部署在 2.4 版及舊版中的實例，您可以將它們移轉至指定的 {{site.data.keyword.cloud_notm}} 帳戶，然後使用 IAM 來管理它們。

如需相關資訊，請參閱下列主題：
* [邀請使用者存取服務及資源](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [利用 IAM 管理使用者存取](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam)

## VMware vCenter Server 及 VMware Cloud Foundation 實例的使用者帳戶及群組變更
{: #relnotes_v25-user-acct}

已在 Microsoft Active Directory 伺服器上建立 **ic4v-vCenter** 使用者群組，並將其新增至 NSX Manager 之 vCenter Server 及使用者群組的廣域許可權。此群組包含 vCenter Server 實例的**自動化**使用者帳戶，以及 vCenter Server 和 Cloud Foundation 實例的服務特定使用者帳戶。

請不要在 VMware vSphere Web Client 的**使用者和群組**頁面中，編輯 **ic4v-vCenter** 群組的廣域許可權。這樣做會影響管理作業。

對於 Cloud Foundation 實例，請使用 **customerroot** 主機使用者 ID 來取代 **root** 主機使用者 ID。

針對 vCenter Server 實例，繼續使用 **root** 主機使用者 ID。已建立 **ic4vroot** 主機使用者 ID，僅供 IBM 使用。

如需使用者帳戶的相關資訊，請參閱[有關變更 vCenter Server 構件的考量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact)。

## 附加服務的更新
{: #relnotes_v25-services}

### IBM Cloud Private Hosted（在 2018 年 8 月 30 日更新）
{: #relnotes_v25-scp-hosted}

{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} 服務現在可用於部署在（或升級至）2.5 版或更新版本的 vCenter Server 實例。

{{site.data.keyword.cloud_notm}} Private Hosted 為您在 {{site.data.keyword.cloud_notm}} 上的 VMware 環境帶來微服務及容器的功能。使用此服務，您可以將熟悉的相同 VMware 與 {{site.data.keyword.cloud_notm}} Private 作業模型和工具，從內部部署延伸到 {{site.data.keyword.cloud_notm}}。

訂購 vCenter Server 實例之後便可以要求此服務。

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v25-spp}

從 2.5 版開始，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務會根據最佳作法部署為兩部不同的 VM，其中一部 VM 執行 IBM Spectrum Protect Plus 伺服器，另一部 VM 執行 vSnap 伺服器及 VADP Proxy。

您現在最多可以訂購 10 個備份資料儲存庫，而且最多容許 120 TB 的備份儲存空間。根據您選取的備份儲存空間大小以及根據 [IBM Spectrum Protect Plus 藍圖](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)中的資訊，來調整 vSnap 及 VADP VM 的大小。

### KMIP for VMware on IBM Cloud
{: #relnotes_v25-kmip}

德國的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務現已推出新的端點。

## 新文件與更新的文件
{: #relnotes_v25-new-docs}

### 連接儲存空間文件
{: #relnotes_v25-docs-storage}

vCenter Server on IBM Cloud 連接儲存空間技術文件現在位於使用者文件的*參照* 小節中。如需相關資訊，請參閱 [vCenter Server on IBM Cloud 的連接儲存空間](/docs/services/vmwaresolutions/archiref/attached-storage?topic=vmware-solutions-storage-benefits)。

### 技術規格
{: #relnotes_v25-docs-tech-specs}

使用者文件中現已提供所有實例類型及服務類型的技術規格，而且可以從使用者介面中進行鏈結。如需相關資訊，請參閱實例及服務的適當概觀主題。

### 服務文件
{: #relnotes_v25-docs-services}

已改良服務資訊，可根據它的版本號碼輕鬆地識別服務支援。

如需相關資訊，請參閱下列主題：

* [vCenter Server 實例可用的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices#available-services-for-vcenter-server-instances)
* [vCenter Server with Hybridity Bundle 實例的可用服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances)

## 使用者介面更新和加強功能
{: #relnotes_v25-ui}

使用者介面已更新，並提供下列加強功能：

* 如果您的 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶鏈結至 {{site.data.keyword.cloud_notm}} 帳戶，您現在可以按一下**設定**頁面上新增的**擷取**按鈕，以自動取得 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶的使用者名稱及 API 金鑰。
* 在實例詳細資料頁面的左導覽窗格上新增**部署歷程**標籤，供您檢查實例的部署歷程。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
