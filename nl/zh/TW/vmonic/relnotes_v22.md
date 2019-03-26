---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-19"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 2.2 版的版本注意事項
{: #relnotes_v22}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 及 Meltdown 補救
{: #relnotes_v22-spectre}

{{site.data.keyword.vmwaresolutions_short}} 發行來自 VMware 的修補程式，以回應已知的 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 及 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## IBM CloudDriver 虛擬機器升級
{: #relnotes_v22-cloud-driver}

在 2.2 版升級程序期間，IBM CloudDriver 虛擬機器使用 CentOS Linux 7.4.1708 版進行重新部署。此外，在 IBM CloudDriver 上，所有新佈建的實例都包括 CentOS Linux 7.4.1708 版。

**重要事項：**

* 如果您使用的備份解決方案參照 IBM CloudDriver 虛擬機器，則在升級至 2.2 版之後，請確定備份解決方案參照新的 IBM CloudDriver 虛擬機器。
* 在升級至 2.2 版之前，請確定您已將 Legacy Veeam VSI 取代為 Veeam on {{site.data.keyword.cloud_notm}} 服務。在 2.2 版和未來的版本中不再支援 Legacy Veeam，因此，與 Legacy Veeam 相關聯的管理元件備份無法進行還原。

如需使用 Veeam on {{site.data.keyword.cloud_notm}} 服務的相關資訊，請參閱下列主題：
* [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) 的元件及考量
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## ESXi 伺服器上的進階配置設定
{: #relnotes_v22-config-esxi}

對於 2.2 版或更新版本，訂購新的實例時會搭配 ESXi 伺服器的一組新的進階配置設定。
如果是從舊版升級到 2.2 版或更新版本的實例，部分設定需要重新啟動 ESXi 伺服器。因此，只會自動套用一部分的配置設定。

建議您將其餘的配置設定變更為新值，以保持所有實例的一致性，並支援充足的儲存空間擴充。IBM 打算只針對所有 {{site.data.keyword.cloud_notm}} for VMware Solutions 未來版本測試這些新設定。

如需相關資訊，請參閱 [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#advanced-configuration-settings-for-esxi-servers)中的 _ESXi 伺服器的進階配置設定_。

## 對於起始叢集支援最多 51 部 ESXi 伺服器，對於其他叢集支援最多 59 部 ESXi 伺服器
{: #relnotes_v22-esxi-cluster}

對於 2.2 版以及更新版本，您現在可以將 ESXi 伺服器的數目增加至起始叢集的上限 51，並將其他叢集增加到最多 59。

如果是部署在 2.1 版或更早版本中的實例，您必須啟用必要的 vSAN 支援，才能將叢集大小增加到超過 32。如需增加 ESXi 伺服器數目之步驟的相關資訊，請參閱[關於 ESXi 伺服器的常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi#how-many-esxi-servers-can-i-add-to-a-cluster-)中的_我可以新增多少部 ESXi 伺服器至叢集？_。{:important}

## vCenter Server 及 Cloud Foundation 實例的其他網路配置選項
{: #relnotes_v22-network-config}

對於 vCenter Server 及 Cloud Foundation 實例訂單，您現在可以為網路配置重複使用現有公用及專用 VLAN。當現有的 VLAN 無法使用時，您可以訂購一個新的公用和兩個新的專用 VLAN。

如需選取現有 VLAN 之前的重要考量，請參閱[訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)中的*網路介面設定* 小節。

## VMware vCenter Server 實例的更新
{: #relnotes_v22-vcs}

### NSX 元件及埠群組配置設定更新
{: #relnotes_v22-nsx}

現行版本會套用 VMware NSX for vSphere 6.3.5 元件更新。如需元件的相關資訊，請參閱 [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

對於已部署在 2.2 版或更新版本的 VMware vCenter Server 實例，NSX 及埠群組配置設定已變更。如需相關資訊，請參閱 [vCenter Server 軟體資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#nsx-and-port-group-configuration-settings)的 *NSX 及埠群組配置設定*小節。

### DNS 配置的新選項
{: #relnotes_v22-dns}

您現在可以選擇在管理叢集裡部署適用於 Microsoft Active Directory (AD) 的單一 Microsoft Windows Server 虛擬伺服器實例 (VSI)，或兩部高可用性 Microsoft Windows 虛擬機器。在 2.2 版之前的版本，依預設，會自動部署單一 Microsoft Windows VSI for Microsoft AD。可選取兩部 Microsoft Windows 虛擬機器的新選項提供更多隱私權，並可選擇使用 Veeam 服務來備份及還原虛擬機器。

如果您將實例配置為使用兩部 Microsoft Windows 虛擬機器，則必須提供 2 份 Microsoft Windows Server 2012 R2 授權。請使用 Microsoft Windows Server 2012 R2 Standard 版本授權及/或 Microsoft Windows Server 2012 R2 Datacenter 版本授權。您有 30 天的時間可啟動 (activate) 虛擬機器。{:note}

如需相關資訊，請參閱[訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#system-settings)中的 *系統設定*區段。

### 已增加每個實例的叢集數目
{: #relnotes_v22-clusters-per-inst}

您現在可以將最多 10 個叢集新增至已部署於或升級至 2.2 版以及更新版本的 VMware vCenter Server 實例。如需相關資訊，請參閱[新增及檢視 vCenter Server 實例的叢集](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

## VMware vSphere 叢集的更新
{: #relnotes_v22-vss}

### 可提供給「事業夥伴」客戶的元件授權組合
{: #relnotes_v22-license-bundles}

在訂購新的 vSphere 叢集時，「事業夥伴」使用者現在可以從四個元件授權組合中選取。可選擇 Standard with Management、Advanced、Advanced with Networking 或 Advanced with Networking and Management。您也可以在訂單中包括其他 VMware 元件。然而，無法使用「自帶授權」的選項。

如需相關資訊，請參閱[訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)中的*授權設定* 小節。

## NetApp ONTAP Select 實例的更新
{: #relnotes_v22-netapp}

現行版本會套用 NetApp ONTAP Select 9.3 的更新。

### 已增加高容量 IBM Cloud Bare Metal Servers 的 SATA 磁碟機數目
{: #relnotes_v22-sata-drives}

現在 NetApp ONTAP Select 高容量 {{site.data.keyword.baremetal_short}} 有 34 個 SATA 磁碟機可供使用。如需相關資訊，請參閱 [NetApp ONTAP Select 實例的技術規格](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs)。

## 附加服務的更新項目
{: #relnotes_v22-services}

### 已增加 F5 on IBM Cloud 的頻寬選項
{: #relnotes_v22-bandwidth}

當您在對 Cloud Foundation 和 vCenter Server 實例安裝 F5 on {{site.data.keyword.cloud_notm}} 服務時，您現在可以選取頻寬上限 10 Gbps。如需相關資訊，請參閱 [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) 的考量。

### KMIP for VMware on IBM Cloud
{: #relnotes_v22-kmip}

您現在可以訂購一個包含 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務的 Cloud Foundation 實例或 vCenter Server 實例，或在初次部署之後，將該服務新增至現有的 Cloud Foundation 實例或 vCenter Server 實例。

此服務提供全年無休的服務，來管理 VMware 在 {{site.data.keyword.cloud_notm}} 中使用的加密金鑰。此服務提供運行環境功能，以容許客戶建立、擷取、啟動、撤銷及刪除加密金鑰。此外，此服務也提供管理功能來維護用戶端認證與這些加密金鑰之間的關聯。

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v22-spp}

現在，已部署於（或升級至）2.2 版或更新版本中的實例，可以使用 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務。

此服務提供有效率且可調式解決方案，以進行虛擬環境的資料保護、資料重複使用及資料回復。您可以將它當成獨立式解決方案來實作，或與 IBM Spectrum Protect&trade; Plus 環境整合以卸載副本，進行長期儲存及資料控管。

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務僅為工作負載 VM 提供資料保護。

如需相關資訊，請參閱[管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)。

### 受管理服務
{: #relnotes_v22-managed-services}

現在，Veeam on {{site.data.keyword.cloud_notm}} 及 Zerto on {{site.data.keyword.cloud_notm}} 的受管理服務可用於 VMware vCenter Server 及 VMware Cloud Foundation 實例。如果您不要管理自己的解決方案和環境的複雜性，則請要求這些受管理服務。

Veeam on {{site.data.keyword.cloud_notm}} 服務與 VMware Hypervisor 無縫整合，以協助您的企業達到高可用性 (HA)。可以使用 Veeam 備份軟體及「IBM Resiliency 備份即服務」來部署完全受管理的備份環境。

Zerto on {{site.data.keyword.cloud_notm}} 服務提供抄寫及災難回復功能，其可整合到部署供應項目中，以保護及回復 {{site.data.keyword.cloud_notm}} 上位於您的 VMware 虛擬環境中的資料。可以使用 Zerto DR 軟體及「IBM Resiliency 服務」來部署完全受管理的災難回復 (DR) 環境。

您可以從**開始使用**頁面要求實例的受管理服務，作法是建立新的實例訂單，或將該服務新增至現有的實例。

如需相關資訊，請參閱下列主題：
* [對於 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services) 要求服務
* [對於 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services) 要求服務

## 新文件與更新的文件
{: #relnotes_v22-new-docs}

* 現在文件中提供 Cloud Foundation 實例及 vCenter Server 實例與 VMware vSphere 叢集的受支援功能的比較表格。您可以一眼看出每一種類型的實例所提供的功能之間的差異。如需相關資訊，請參閱[提供比較圖表](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart)。

* 現在文件中提供 Cloud Foundation、vCenter Server 及 VMware vSphere 叢集的 VLAN 和軟體資料清單 (BOM)。

  如需相關資訊，請參閱下列主題：

  * [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
  * [VMware vSphere 資料清單](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)

## 使用者介面更新和加強功能
{: #relnotes_v22-ui}

在整個使用者介面中進行了改善：

* 訂購實例時，現在會依位置過濾所有硬體選項，而無法使用的選項會顯示為已停用狀態。
* 當您根據現有配置來訂購 vSphere 叢集時，現在會自動移入 **{{site.data.keyword.baremetal_short}}** 配置。您可以根據需求來更新配置。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
