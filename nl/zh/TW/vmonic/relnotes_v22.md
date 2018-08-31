---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-18"

---

# 2.2 版的版本注意事項

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之其他要訣的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 及 Meltdown 補救

{{site.data.keyword.vmwaresolutions_short}} 發行來自 VMware 的修補程式，以回應已知的 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 及 CVE-2017-5754）。

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

如需相關資訊，請參閱[處理 Spectre 及 Meltdown 漏洞](../vmonic/trbl_fix_spectre.html)。

## IBM CloudDriver 虛擬機器升級

在 2.2 版升級程序期間，IBM CloudDriver 虛擬機器使用 CentOS Linux 7.4.1708 版進行重新部署。此外，在 IBM CloudDriver 上，所有新佈建的實例都包括 CentOS Linux 7.4.1708 版。

**重要事項：**

* 如果您使用的備份解決方案參照 IBM CloudDriver 虛擬機器，則在升級至 2.2 版之後，請確定備份解決方案參照新的 IBM CloudDriver 虛擬機器。
* 在升級至 2.2 版之前，請確定您已將 Legacy Veeam VSI 取代為 Veeam on {{site.data.keyword.cloud_notm}} 服務。在 2.2 版和未來的版本中不再支援 Legacy Veeam，因此，與 Legacy Veeam 相關聯的管理元件備份無法進行還原。

如需使用 Veeam on {{site.data.keyword.cloud_notm}} 服務的相關資訊，請參閱下列主題：
* [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html) 的元件及考量
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html)

## VMware Federal on IBM Cloud 的支援

VMware Federal on {{site.data.keyword.cloud_notm}} 支援在 WDC03 Federal on {{site.data.keyword.CloudDataCent_notm}} 中訂購基本 vCenter Server 實例。除了支援 vCenter Server 實例供應項目子集之外，VMware Federal on {{site.data.keyword.cloud_notm}} 還提供選項讓美國聯邦政府機關維護已部署的 VMware vCenter Server 實例的安全。選取保護已部署實例的選項，會移除針對該實例所儲存的機密性資訊，並移除開啟的管理連線，以持續存取該實例來執行管理功能，例如新增及移除主機和叢集。選取保護選項之後，除了完整實例刪除之外，會停用所有管理功能。

有關維護 VMware Federal 實例安全之前的重要考量，請參閱[維護 VMware Federal 實例安全](../vcenter/vc_fed_securinginstance.html)。

（在 2018 年 4 月 2 日更新）您現在可以透過新增或移除 ESXi 伺服器，來擴充或縮減 VMware Federal 實例的容量。此選項僅適用於未受保護的 VMware Federal 實例。

如需相關資訊，請參閱下列主題：

* [VMware Federal on {{site.data.keyword.cloud_notm}} 概觀](../vcenter/vc_fed_overview.html)
* [新增、檢視及刪除 VMware Federal 實例的叢集](../vcenter/fed_addviewdeleteclusters.html)
* [擴充及縮減 VMware Federal 實例的容量](../vcenter/vc_fed_addingremovingservers.html)

## ESXi 伺服器上的進階配置設定

對於 2.2 版或更新版本，訂購新的實例時會搭配 ESXi 伺服器的一組新的進階配置設定。
如果是從舊版升級到 2.2 版或更新版本的實例，有些設定需要重新啟動 ESXi 伺服器，因此，只會自動套用一部分的配置設定。

建議您將其餘的配置設定變更為新值，以保持所有實例的一致性，並支援充足的儲存空間擴充。IBM 打算只針對所有 {{site.data.keyword.cloud_notm}} for VMware Solutions 未來版本測試這些新設定。

如需相關資訊，請參閱下列的 _ESXi 伺服器的進階配置設定_：
* [vCenter Server 資料清單](../vcenter/vc_bom.html#advanced-configuration-settings-for-esxi-servers)
* [Cloud Foundation 資料清單](../sddc/sd_bom.html#advanced-configuration-settings-for-esxi-servers)

## 對於起始叢集支援最多 51 部 ESXi 伺服器，對於其他叢集支援最多 59 部 ESXi 伺服器

對於 2.2 版以及更新版本，您現在可以將 ESXi 伺服器的數目增加至起始叢集的上限 51，並將其他叢集增加到最多 59。

**重要事項：**如果是部署在 2.1 版或更舊版本中的實例，您必須啟用必要的 vSAN 支援，將叢集大小增加到超過 32。如需增加 ESXi 伺服器數目的相關資訊和步驟，請參閱[關於 ESXi 伺服器的常見問題](../vmonic/faq_esxi.html#how-many-esxi-servers-can-i-add-to-a-cluster-)中的_我可以新增多少部 ESXi 伺服器至叢集？_。

## vCenter Server 實例及 Cloud Foundation 實例的其他網路配置選項

對於 vCenter Server 及 Cloud Foundation 實例訂單，您現在可以選擇為網路配置重複使用現有的公用和專用 VLAN。當現有的 VLAN 無法使用時，您可以繼續選擇訂購一個新的公用和兩個新的專用 VLAN。

如需選取現有 VLAN 之前的重要考量，請參閱下列項目中的*網路介面設定* 小節：
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)

## VMware vCenter Server 實例的更新

### NSX 元件及埠群組配置設定更新

現行版本會套用 VMware NSX for vSphere 6.3.5 元件更新項目。如需元件的相關資訊，請參閱 [vCenter Server 資料清單](../vcenter/vc_bom.html)。

若為 2.2 版或更新版本中部署的 VMware vCenter Server 實例，則 NSX 及埠群組配置設定已變更。如需相關資訊，請參閱 [vCenter Server 軟體資料清單](../vcenter/vc_bom.html#nsx-and-port-group-configuration-settings)的 *NSX 及埠群組配置設定*小節。

### DNS 配置的新選項

現在，您可以選擇在管理叢集中選取適用於 Microsoft Active Directory (AD) 的單一 Microsoft Windows Server 虛擬伺服器實例 (VSI)，或兩部高可用性 Microsoft Windows 虛擬機器的部署。對於 2.2 版之前的版本，依預設，會自動部署適用於 Microsoft AD 的單一 Microsoft Windows VSI。能選取兩部 Microsoft Windows 虛擬機器的新選項提供更多隱私權，並可選擇使用 Veeam 服務來備份及還原虛擬機器。

**附註：**如果您將實例配置為使用兩部 Microsoft Windows 虛擬機器，則必須提供兩個 Microsoft Windows Server 2012 R2 授權。請使用 Microsoft Windows Server 2012 R2 Standard 版本授權及/或 Microsoft Windows Server 2012 R2 Datacenter 版本授權。您有 30 天的時間可啟動虛擬機器。

如需相關資訊，請參閱[訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html#system-settings)中的 *系統設定*區段。

### 已增加每個實例的叢集數目

您現在可以將最多 10 個叢集新增至已部署於或升級至 2.2 版以及更新版本的 VMware vCenter Server 實例。如需相關資訊，請參閱[新增及檢視 vCenter Server 實例的叢集](../vcenter/vc_addingviewingclusters.html)

## VMware vSphere 叢集的更新項目

### 可提供給「事業夥伴」客戶的元件授權組合

在訂購新的 vSphere 叢集時，「事業夥伴」使用者現在可以從四個元件授權組合中選取。可選擇 Standard with Management、Advanced、Advanced with Networking 或 Advanced with Networking and Management。您也可以在訂單中包括其他 VMware 元件。然而，無法使用「自帶授權」的選項。

如需相關資訊，請參閱[訂購新的 vSphere 叢集](../vsphere/vs_orderinginstances.html)中的*授權設定* 小節。

## NetApp ONTAP Select 實例的更新項目

現行版本會套用 NetApp ONTAP Select 9.3 的更新項目。

### 已增加高容量 IBM Cloud Bare Metal Servers 的 SATA 磁碟機數目

現在 NetApp ONTAP Select 高容量 {{site.data.keyword.baremetal_short}} 有 34 個 SATA 磁碟機可供使用。如需相關資訊，請參閱 [NetApp ONTAP Select 實例的技術規格](../netapp/np_netappoverview.html#technical-specifications-for-netapp-ontap-select-instances)。

## 附加服務的更新項目

### 已增加 F5 on IBM Cloud 的頻寬選項

在對 Cloud Foundation 實例和 vCenter Server 實例安裝 F5 on {{site.data.keyword.cloud_notm}} 服務時，您現在可以選取頻寬上限 10 Gbps。如需相關資訊，請參閱 [F5 on {{site.data.keyword.cloud_notm}}](../services/f5_considerations.html) 的考量。

### KMIP for VMware on IBM Cloud

您現在可以訂購一個包含 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務的 Cloud Foundation 實例或 vCenter Server 實例，或在初次部署之後，將該服務新增至現有的 Cloud Foundation 實例或 vCenter Server 實例。

此服務提供全年無休的服務，來管理 VMware 在 {{site.data.keyword.cloud_notm}} 中使用的加密金鑰。此服務提供運行環境功能以讓客戶建立、擷取、啟動、撤銷及毀損加密金鑰，同時提供管理功能來維護用戶端認證與這些加密金鑰之間的關聯。

如需相關資訊，請參閱 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 的考量](../services/kmip_considerations.html)。

### IBM Spectrum Protect Plus on IBM Cloud

現在，已部署於（或升級至）2.2 版或更新版本中的實例，可以使用 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務。

此服務提供有效率且可調式解決方案，以進行虛擬環境的資料保護、資料重複使用及資料回復。您可以將它當成獨立式解決方案來實作，或與 IBM Spectrum Protect&trade; Plus 環境整合以卸載副本，進行長期儲存及資料控管。

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務僅為工作負載 VM 提供資料保護。

如需相關資訊，請參閱[管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html)。

### 受管理服務

現在，Veeam on {{site.data.keyword.cloud_notm}} 及 Zerto on {{site.data.keyword.cloud_notm}} 的受管理服務可用於 VMware vCenter Server 及 VMware Cloud Foundation 實例。如果您不想管理自己的解決方案和環境的複雜性，則您可能想要求受管理服務。

Veeam on {{site.data.keyword.cloud_notm}} 服務與 VMware Hypervisor 無縫整合，以協助您的企業達到高可用性 (HA)。可以使用 Veeam 備份軟體及「IBM Resiliency 備份即服務」來部署完全受管理的備份環境。

Zerto on {{site.data.keyword.cloud_notm}} 服務提供抄寫及災難回復功能，其可整合到部署供應項目中，以保護及回復 {{site.data.keyword.cloud_notm}} 上位於您的 VMware 虛擬環境中的資料。可以使用 Zerto DR 軟體及「IBM Resiliency 服務」來部署完全受管理的災難回復 (DR) 環境。

您可以從**開始使用**頁面要求實例的受管理服務，作法是建立新的實例訂單，或將該服務新增至現有的實例。

如需相關資訊，請參閱下列主題：
* [對於 Veeam on {{site.data.keyword.cloud_notm}}](../services/managing_veeam_services.html) 要求服務
* [對於 Zerto on {{site.data.keyword.cloud_notm}}](../services/managing_zerto_services.html) 要求服務

## 新的及更新的文件

* 現在文件中提供 Cloud Foundation 實例及 vCenter Server 實例與 VMware vSphere 叢集的受支援功能的比較表格。您可以一眼看出每一種類型的實例所提供的功能之間的差異。如需相關資訊，請參閱[提供比較圖表](../vmonic/inst_comp_chart.html)。

* 現在文件中提供 Cloud Foundation 實例及 vCenter Server 實例與 VMware vSphere 叢集的 VLAN 和軟體資料清單 (BOM)。

  如需相關資訊，請參閱下列主題：

  * [vCenter Server 資料清單](../vcenter/vc_bom.html)
  * [Cloud Foundation 資料清單](../sddc/sd_bom.html)
  * [VMware vSphere 資料清單](../vsphere/vs_bom.html)

## 使用者介面更新和加強功能

在整個使用者介面中進行了改善：

* 訂購實例時，現在會依位置過濾所有硬體選項，而無法使用的選項會顯示為已停用狀態。
* 當您根據現有配置來訂購 vSphere 叢集時，現在會自動移入 **{{site.data.keyword.baremetal_short}}** 配置。您可以根據需求來更新配置。
* 已提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
