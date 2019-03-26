---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 2.3 版的版本注意事項
{: #relnotes_v23}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 及 Meltdown 補救
{: #relnotes_v23-spectre}

{{site.data.keyword.vmwaresolutions_short}} 發行來自 VMware 的修補程式，以回應已知的 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 及 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware vCenter Server on IBM Cloud with Hybridity Bundle
{: #relnotes_v23-vcs-hybrid}

此版本引進 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 供應項目。vCenter Server with Hybridity Bundle 是一種受管理的專用雲端，有助於快速且輕鬆地將內部部署基礎架構擴充到雲端。VMware 環境根據 IBM 提供的「VMware 軟體定義資料中心」授權，並包括 VMware HCX on {{site.data.keyword.cloud_notm}} 服務，以透過內部部署方式輕鬆且安全地連接 vSphere 5.0+ 環境與 {{site.data.keyword.cloud_notm}} 站台，來獲得無縫的基礎架構混合及實際應用程式行動性。

只有透過 vCenter Server with Hybridity Bundle 實例才能取得 HCX on {{site.data.keyword.cloud_notm}} 服務。在第一次套用基礎 vCenter Server 2.3 版軟體更新之後，您可以將現有 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例。如需相關資訊，請參閱[將更新套用至 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)。

如需 vCenter Server with Hybridity Bundle 的相關資訊，請參閱下列主題：

* [vCenter Server with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [vCenter Server with Hybridity Bundle 實例的需求及規劃](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [訂購 vCenter Server with Hybridity Bundle 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## 刪除 vCenter Server 及 Cloud Foundation 實例的叢集支援
{: #relnotes_v23-delete-cluster}

您現在不需要刪除整個實例，就可以從實例刪除叢集。對於部署在 2.2 版或更早版本實例的叢集，您必須將實例升級至 2.3 版，才能刪除您新增至實例的叢集。

如需相關資訊，請參閱[新增、檢視及刪除 vCenter Server 實例的叢集](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances#deleting-clusters-from-vcenter-server-instances)。

## VMware vCenter Server 實例的更新
{: #relnotes_v23-vcs}

此版本會套用下列升級及改善：
*	VMware vSphere ESXi 6.5 U1g（已套用修補程式層次 ESXi650-201803001 的 ESXi 6.5u1）
*	VMware vCenter Server 6.5 Update 1g

從 2.3 版開始，當您選擇**自訂**的 Bare Metal Server 設定時，即可使用下列新的 CPU 型號以供部署：
* 雙重 Intel Xeon Silver 4110 處理器 / 總計 16 核心，2.1 GHz
* 雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，2.2 GHz

如需相關資訊，請參閱下列主題：

* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [新增、檢視及刪除 vCenter Server 實例的叢集](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

## VMware Cloud Foundation 實例的更新
{: #relnotes_v23-vcf}

此版本會套用下列升級及改善：
*	VMware vSphere ESXi 6.5 U1g（已套用修補程式層次 ESXi650-201803001 的 ESXi 6.5u1）
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## 附加服務的更新
{: #relnotes_v23-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v23-htcc}

現在，HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務可用於執行 vSphere 6.5 以及部署於或升級至 2.3 版或更新版本的 VMware Cloud Foundation 實例及 VMware vCenter Server 實例。此服務會施行並控制是否符合安全標準，並提供角色型存取控制 (RBAC)。與 HyTrust DataControl 結合時，此服務可確保虛擬機器及工作負載資料不會離開 {{site.data.keyword.cloud_notm}} 資料中心內的特定地區、叢集或 ESXi 伺服器。

您可以在訂購實例時訂購包含此服務的實例，或稍後將此服務新增至現有實例。

如需相關資訊，請參閱下列主題：
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 的元件及考量](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [管理 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)

### HyTrust DataControl on IBM Cloud
{: #relnotes_v23-htdc}

現在，HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務可用於執行 vSphere 6.5 以及部署於或升級至 2.3 版或更新版本的 VMware Cloud Foundation 實例及 VMware vCenter Server 實例。此服務提供具有整合式金鑰管理的高度加密，在工作負載的整個生命週期內保護其安全。此服務可以提供作業系統層次及資料層次的加密，表示可以加密及解密工作負載內的任何目錄、資料夾或檔案。

您可以在訂購實例時訂購包含此服務的實例，或稍後將此服務新增至現有實例。

如需相關資訊，請參閱下列主題：
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} 的元件及考量](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [管理 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v23-spp}

現行版本會將 IBM Spectrum Protect&trade; Plus 10.1.1 版當成預設備份服務安裝至所有新部署的實例。如需 IBM Spectrum Protect Plus 10.1.1 版中新增特性的相關資訊，請參閱 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}。

## 新文件與更新的文件
{: #relnotes_v23-new-docs}

有新的 developerWorks 秘訣可供使用，其包含的逐步指示有關如何在部署之後將儲存空間新增至 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}。如需相關資訊，請參閱 [Adding storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)。

## 使用者介面更新和加強功能
{: #relnotes_v23-ui}

使用者介面已更新，並提供下列加強功能：
* **一致性**：使用者介面現在提供與 {{site.data.keyword.cloud_notm}} 上其他服務一致的外觀與操作方式。
* **容易存取**：您現在可以直接從 {{site.data.keyword.cloud_notm}} **型錄**存取 VMware 供應項目。
* **流暢且及簡化的訂購體驗**：您現在可以在單一介面中完成訂購 VMware 實例並部署其附加程式服務。此外，還會計算預估成本，並將其立即顯示在相同的介面中，讓您可以根據成本方案來調整配置。
* 「事業夥伴」使用者無法使用訂購實例或新增叢集時的「自帶授權 (BYOL)」選項。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
