---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# 2.3 版的版本注意事項

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之其他要訣的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 及 Meltdown 補救

{{site.data.keyword.vmwaresolutions_short}} 發行來自 VMware 的修補程式，以回應已知的 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 及 CVE-2017-5754）。

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

如需相關資訊，請參閱[處理 Spectre 及 Meltdown 漏洞](../vmonic/trbl_fix_spectre.html)。

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

此版本引進 VMware vCenter Server on IBM Cloud with Hybridity Bundle 供應項目。vCenter Server with Hybridity Bundle 是一種受管理的專用雲端，有助於快速且輕鬆地將內部部署基礎架構擴充到雲端。VMware 環境根據 IBM 提供的「VMware 軟體定義資料中心」授權，並包括 VMware HCX on {{site.data.keyword.cloud_notm}} 服務，以透過內部部署方式輕鬆且安全地連接 vSphere 5.0+ 環境與 IBM Cloud 站台，來獲得無縫的基礎架構混合及實際應用程式行動性。

只有透過 vCenter Server with Hybridity Bundle 實例才能取得 HCX on {{site.data.keyword.cloud_notm}} 服務。在第一次套用基本 vCenter Server 2.3 版軟體更新之後，您可以將現有 vCenter Server 實例升級至 vCenter Server with Hybridity Bundle 實例。如需相關資訊，請參閱[將更新套用至 vCenter Server 實例](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html)。

如需 vCenter Server with Hybridity Bundle 的相關資訊，請參閱：

* [vCenter Server with Hybridity Bundle 概觀](../vcenter/vc_hybrid_overview.html)
* [vCenter Server with Hybridity Bundle 實例的需求及規劃](../vcenter/vc_hybrid_planning.html)
* [訂購 vCenter Server with Hybridity Bundle 實例](../vcenter/vc_hybrid_orderinginstance.html)

## 刪除 vCenter Server 及 Cloud Foundation 實例的叢集支援

您現在不需要刪除整個實例，就可以從實例中刪除叢集。對於部署在 2.2 版或更早版本實例的叢集，您必須將實例升級至 2.3 版，才能刪除您新增至實例的叢集。

如需相關資訊，請參閱：

* [新增、檢視及刪除 vCenter Server 實例的叢集](../vcenter/vc_addingviewingclusters.html#deleting-clusters-from-vcenter-server-instances)
* [新增、檢視及刪除 Cloud Foundation 實例的叢集](../sddc/sd_addingviewingclusters.html#deleting-clusters-from-cloud-foundation-instances)

## VMware vCenter Server 實例的更新

此版本會套用下列升級及改進項目：
*	VMware vSphere ESXi 6.5 U1g（已套用修補程式層次 ESXi650-201803001 的 ESXi 6.5u1）
*	VMware vCenter Server 6.5 Update 1g

### vCenter Server 實例及叢集的加強功能

從 2.3 版開始，當您選擇**自訂**的 Bare Metal Server 設定時，即可使用下列新的 CPU 型號以供部署：
* 雙重 Intel Xeon Silver 4110 處理器/總計 16 核心，2.1 GHz
* 雙重 Intel Xeon Gold 5120 處理器/總計 28 核心，2.2 GHz

如需相關資訊，請參閱：

* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [新增、檢視及刪除 vCenter Server 實例的叢集](../vcenter/vc_addingviewingclusters.html)

## VMware Cloud Foundation 實例的更新項目

此版本會套用下列升級及改進項目：
*	VMware vSphere ESXi 6.5 U1g（已套用修補程式層次 ESXi650-201803001 的 ESXi 6.5u1）
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## VMware Federal 實例的更新項目

### VMware Federal 實例的 DNS 配置

現在，您可以選擇在管理叢集中選取適用於 Microsoft Active Directory (AD) 的單一 Microsoft Windows Server 虛擬伺服器實例 (VSI)，或兩部高可用性 Microsoft Windows 虛擬機器的部署。對於 2.2 版，依預設，會自動部署適用於 Microsoft AD 的單一 Microsoft Windows VSI。能選取兩部 Microsoft Windows 虛擬機器的新選項提供更多隱私權，並可選擇使用 Veeam 服務來備份及還原虛擬機器。

**附註：**如果您將實例配置為使用兩部 Microsoft Windows 虛擬機器，則必須提供兩個 Microsoft Windows Server 2012 R2 授權。請使用 Microsoft Windows Server 2012 R2 Standard 版本授權及/或 Microsoft Windows Server 2012 R2 Datacenter 版本授權。您有 30 天的時間可啟動虛擬機器。

如需相關資訊，請參閱[訂購 VMware Federal 實例](../vcenter/vc_fed_orderinginstance.html#network-interface-settings)中的*網路介面設定* 小節。

### 新增及刪除 VMware Federal 實例的叢集支援

您現在可以使用叢集來管理在 2.3 版及更新版本中部署的 VMware Federal 實例中的 ESXi 伺服器，以獲得更好的資源管理和高可用性。依預設，您訂購實例時所配置的 ESXi 伺服器會分組為 **cluster1**。您可以在實例概觀頁面上檢視叢集詳細資料，或最多將總計 10 個叢集新增至一個實例。當您擴充或縮減實例的容量時，您可以選取要將 ESXi 伺服器新增至哪一個叢集，或從中移除 ESXi 伺服器。

您也可以選擇從實例中刪除一個以上的叢集，而不刪除整個實例。

如需相關資訊，請參閱[新增、檢視及刪除 VMware Federal 實例的叢集](../vcenter/fed_addviewdeleteclusters.html)。

## 附加服務的更新項目

### HyTrust CloudControl on IBM Cloud

現在，HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務可用於執行 vSphere 6.5 以及部署於或升級至 2.3 版或更新版本的 VMware Cloud Foundation 實例及 VMware vCenter Server 實例。此服務會施行並控制是否符合安全標準，並提供角色型存取控制 (RBAC)。與 HyTrust DataControl 結合時，此服務可確保虛擬機器及工作負載資料不會離開 {{site.data.keyword.cloud_notm}} 資料中心內的特定地區、叢集或 ESXi 伺服器。

您可以在訂購實例時訂購包含此服務的實例，或稍後將此服務新增至現有實例。

如需相關資訊，請參閱：
* [HyTrust CloudControl on IBM Cloud 的元件及考量](../services/htcc_considerations.html)
* [管理 HyTrust CloudControl on IBM Cloud](../services/managinghtcc.html)

### HyTrust DataControl on IBM Cloud

現在，HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務可用於執行 vSphere 6.5 以及部署於或升級至 2.3 版或更新版本的 VMware Cloud Foundation 實例及 VMware vCenter Server 實例。此服務提供具有整合式金鑰管理的高度加密，來保護其整個生命週期的工作負載安全。此服務可以提供作業系統層次及資料層次的加密，表示可以加密及解密工作負載內的任何目錄、資料夾或檔案。

您可以在訂購實例時訂購包含此服務的實例，或稍後將此服務新增至現有實例。

如需相關資訊，請參閱：
* [HyTrust DataControl on IBM Cloud 的元件及考量](../services/htdc_considerations.html)
* [管理 HyTrust DataControl on IBM Cloud](../services/managinghtdc.html)

### IBM Spectrum Protect Plus on IBM Cloud

現行版本會將 IBM Spectrum Protect&trade; Plus 10.1.1 版當成預設備份服務安裝至所有新部署的實例。如需 IBM Spectrum Protect Plus 10.1.1 版中新增特性的相關資訊，請參閱 [IBM Spectrum Protect Plus 更新項目](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}。

## 新的及更新的文件

有新的 developerWorks 秘訣可供使用，其包含的逐步指示有關如何將儲存空間新增至 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 後置部署。如需相關資訊，請參閱[將儲存空間新增至 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 後置部署](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)。

## 使用者介面更新和加強功能

會更新使用者介面，並提供下列加強功能：
* **一致性**：使用者介面現在提供與 IBM Cloud 上其他服務一致的外觀與操作方式。
* **容易存取**：您現在可以直接從 IBM Cloud **型錄**存取 VMware 供應項目。
* **流暢且及簡化的訂購體驗**：您現在可以在單一介面中完成訂購 VMware 實例並部署其附加程式服務。此外，還會計算預估成本，並將其立即顯示在相同的介面中，讓您可以根據成本方案來調整配置。
* 「事業夥伴」使用者無法使用訂購實例或新增叢集時的「自帶授權 (BYOL)」選項。
* 已提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
