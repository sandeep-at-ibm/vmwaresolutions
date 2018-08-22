---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# VMware Federal on IBM Cloud 概觀

除了將保護已部署 vCenter Server 實例安全的選項提供給 US Federal Government 機構之外，VMware Federal on {{site.data.keyword.cloud}} 也支援訂購基本 vCenter Server 實例。選取保護已部署實例的選項，會移除針對該實例所儲存的機密性資訊，並移除開啟的管理連線，以持續存取該實例來執行管理功能，例如新增及移除主機和叢集。選取保護選項之後，除了完整實例刪除之外，會停用所有管理功能。

如需 vCenter Server on {{site.data.keyword.cloud_notm}} 及 vCenter Server 架構的相關資訊，請參閱 [vCenter Server 概觀](vc_vcenterserveroverview.html)。

**注意：**VMware Federal on {{site.data.keyword.cloud_notm}} 僅提供 vCenter Server 供應項目的子集。多站台配置、預先配置的 {{site.data.keyword.cloud_notm}} Bare Metal Server、自帶授權 (BYOL)，以及訂購其他服務的選項不受支援。

## VMware Federal on IBM Cloud 實例的技術規格

包括下列元件：

### Bare Metal Server

您可以使用下列其中一項配置，訂購兩部以上的自訂 {{site.data.keyword.baremetal_short}}：

* 2-CPU Intel Broadwell Generation（Intel Xeon E5-2600 v4 系列）
* 2-CPU Intel Skylake Generation（Intel Xeon 4100/5100/6100 系列）

對於 NFS 儲存空間配置，建議的 {{site.data.keyword.baremetal_short}} 數目是設為預設值 3。

**附註：**如果您選取 vSAN 儲存空間，則配置需要四個 {{site.data.keyword.baremetal_short}}。

### 網路

訂購了下列網路元件：
*  三個 VLAN（虛擬 LAN）：一個公用 VLAN 和兩個專用 VLAN
*  在連接至第 2 層 (L2) 網路的本端工作負載之間，用於潛在東西向通訊（水平通訊）的一個具有 DLR（分散式邏輯路由器）的 VXLAN (Virtual eXtensible LAN)。VXLAN 是部署成一個遞送拓蹼範例，您可以在其中修改、建置或移除它。您也可以將其他 VXLAN 連接到 DLR 上的新邏輯介面，來新增安全區域。
*  兩個 VMware NSX Edge Services Gateway：
  * 用於出埠 HTTPS 管理資料流量的安全管理服務 VMware NSX Edge Services Gateway (ESG)，IBM 將它部署為管理網路拓蹼的一部分。IBM 管理虛擬機器利用此 ESG，來和與自動化相關的特定外部 IBM 管理元件進行通訊。如需相關資訊，請參閱[將您的網路配置成使用客戶管理的 ESG](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)。

    **重要事項**：您無法存取此 ESG，因此無法使用它。如果您修改它，則可能無法從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 vCenter Server 實例。此外，請注意，使用防火牆或停用外部 IBM 管理元件的 ESG 通訊，將導致 {{site.data.keyword.vmwaresolutions_short}} 變成無法使用。
  * 用於出埠和入埠 HTTPS 工作負載資料流量的安全客戶管理 VMware NSX Edge Services Gateway，IBM 將它部署為範本，您可以修改它來提供 VPN 存取或公用存取。如需相關資訊，請參閱[客戶管理的 NSX Edge 是否造成安全風險](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)。

  **附註**：在執行保護已部署的 VMware Federal 實例的動作時，會移除用於出埠 HTTPS 管理資料流量的 VMware NSX Edge Services (ESG)。如需相關資訊，請參閱[維護 VMware Federal 實例的安全](vc_fed_securinginstance.html)。

### 虛擬伺服器實例

已訂購下列 VSI（虛擬伺服器實例）：
* IBM CloudBuilder 的 VSI，在完成實例部署之後會關閉它。
* （適用於實例 2.3 版及更新版本）您可以選擇在管理叢集中部署單一 Microsoft Windows Server VSI for Microsoft Active Directory (AD) 或兩個高可用性 Microsoft Windows VM，以協助加強安全及穩健性。
* （適用於 2.2 版實例）已部署並可查閱 Microsoft Windows Server VSI for Microsoft Active Directory (AD)（其充當已登錄主機及虛擬機器之實例的 DNS）。

### 儲存空間

在起始部署期間，您可以選擇 vSAN 和 NFS 儲存空間選項。

vSAN 選項提供自訂的配置，以及磁碟類型和數量的各種選項：
* 磁碟數量：2、4、6 或 8。
* 儲存磁碟：960 GB SSD SED、1.9 TB SSD SED 或 3.8 TB SSD SED。

  此外，還訂購了每部主機 2 個快取磁碟 (960 GB)。

NFS 選項為工作負載提供自訂的共用檔案層次儲存空間，以及大小和效能的各種選項：
* 大小：1、2、4、8 或 12 TB。
* 效能：2、4 或 10 IOPS/GB。
* 個別配置檔案共用。

如果您選擇 NFS 選項，則會訂購用於管理元件的一個 2 TB、4 IOPS/GB 檔案共用。

### IBM 提供的授權及費用

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.4
* （針對 vSAN 叢集）VMware vSAN Advanced 或 Enterprise 6.6

## VMware Federal on IBM Cloud 擴充節點的技術規格

每一個 vCenter Server 擴充節點將部署下列元件，並在您的 {{site.data.keyword.cloud_notm}} 帳戶中收取其費用。

### 擴充節點的硬體

一部具有 [VMware Federal on {{site.data.keyword.cloud_notm}} 實例的技術規格](vcenter/vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances)中所呈現之配置的 Bare Metal Server。

### 擴充節點的授權與費用

* 一個 VMware vSphere Enterprise Plus 6.5u1
* 一個 VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.4
* （針對 vSAN 叢集）VMware vSAN Advanced 或 Enterprise 6.6

**重要事項**：您必須從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 {{site.data.keyword.cloud_notm}} 帳戶中所建立的 {{site.data.keyword.vmwaresolutions_short}} 元件，而不是在主控台以外的 {{site.data.keyword.slportal}} 或透過任何其他方法進行管理。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更這些元件，則變更不會與主控台同步。

**警告**：從 {{site.data.keyword.vmwaresolutions_short}} 主控台以外管理已在訂購實例時安裝至 {{site.data.keyword.cloud_notm}} 帳戶的任何 {{site.data.keyword.vmwaresolutions_short}} 元件，可能會讓您的環境不穩定。這些管理活動包括：
*  新增、修改、退回或移除元件
*  透過新增或移除 ESXi 伺服器來擴充或縮減實例容量
*  關閉元件電源

   這些活動的例外包括從 {{site.data.keyword.slportal}} 管理共用儲存空間檔案共用。這類活動包括：訂購、刪除（這可能會影響已裝載的資料儲存庫）、授權及裝載共用儲存空間檔案共用。

### 相關鏈結

* [vCenter Server 軟體資料清單](vc_bom.html)
* [VMware Federal 實例的需求與規劃](vc_fed_planning.html)
* [訂購 VMware Federal 實例](vc_fed_orderinginstance.html)
* [維護 VMware Federal 實例的安全](vc_fed_securinginstance.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [{{site.data.keyword.cloud_notm}} file and block storage](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
