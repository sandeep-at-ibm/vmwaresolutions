---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-10"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vSphere on IBM Cloud 概觀
{: #vs_vsphereclusteroverview}

VMware vSphere on {{site.data.keyword.cloud}} 是 VMware 的簡化與最佳化訂購平台。使用此平台，您可以根據所選取的 VMware 元件來自訂及訂購 VMware 相容硬體，以建置您自己的 IBM 代管 VMware 環境。

{{site.data.keyword.vmwaresolutions_short}} 主控台會根據您選取的 VMWare 元件而自動過濾硬體。例如，當您建立新的全快閃記憶體 VMware SAN 叢集時，只會呈現根據 [VMware 相容性手冊](https://www.vmware.com/resources/compatibility/search.php)所驗證的硬體。此外，至少需要四部 ESXi 伺服器。

VMware vSphere on {{site.data.keyword.cloud_notm}} 不會使選用的 VMware 元件的安裝、配置及啟動自動化。平台容許最大的彈性來設計及建置代管的 VMware 環境，同時納入 VMware 相容的硬體。

使用此供應項目來建立 ESXi 伺服器的新叢集，或在 {{site.data.keyword.CloudDataCent_notm}} 中擴充 ESXi 伺服器的現有叢集。視您選取的 VMware 元件而定，您可以只從一部 ESXi 伺服器開始，稍後再視需要擴充叢集。

## VMware vSphere on IBM Cloud 叢集的技術規格
{: #vs_vsphereclusteroverview-specs}

檢閱 VMware vSphere on {{site.data.keyword.cloud_notm}} 的元件。

標準化硬體配置的可用性及定價可能會根據選取以用於部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。
{:note}

### VMware 元件
{: #vs_vsphereclusteroverview-specs-vmware-components}

請選取下列 VMware 元件的授權（IBM 提供或 BYOL）：
* VMware vSphere Enterprise Plus 6.7 U1 或 6.5 U2
* 以下是選用的 VMware 元件：
   * VMware vCenter Server Standard
   * VMware NSX（Base、Advanced 或 Enterprise）
   * VMware vSAN（Advanced 或 Enterprise）
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server
{: #vs_vsphereclusteroverview-specs-bare-metal}

您可以訂購具有下列其中一個配置的一個以上的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}：
* **Skylake**：2-CPU Intel Skylake 產生伺服器（Intel Xeon 4100/5100/6100 系列），搭配您選取的 CPU 型號及 RAM 大小。
* **SAP 認證**：Intel Skylake 或 Intel Broadwell 產生伺服器（Intel Xeon 6140/E5-2690/E7-8890 系列），搭配您選取的 CPU 型號。
* **Broadwell**：4-CPU Intel Broadwell 世代伺服器（Intel Xeon E7-4800 系列），搭配您選取的 CPU 型號及 RAM 大小。

可用的選項取決於您是否已選取 VMware vSAN 元件。

此外，下列磁碟和網路規格：
* 10 Gbps 雙重公用及專用網路上行鏈路
* 一個 RAID 磁碟控制器

### 網路
{: #vs_vsphereclusteroverview-specs-network}

* 一個 VLAN（虛擬 LAN）公用 VLAN 及兩個專用 VLAN
* （選用）一組 HA 的 FortiGate Security Appliance 裝置

### Storage
{: #vs_vsphereclusteroverview-specs-storage}

選取 VMware vSAN 元件時用於 vSAN 配置的使用者自訂儲存空間：
* 儲存空間磁碟選項：960 GB SSD SED、1.9 TB SSD SED 或 3.8 TB SSD SED
* 磁碟數量選項：2、4、6 或 8

  此外，還為每部主機訂購 2 個 960 GB 的快取磁碟。

  當 3.8 TB SSD（固態硬碟）磁碟機在正式發行至資料中心時，就會予以支援。
  {:note}
* 「高效能 Intel Optane」選項，提供 2 個額外容量磁碟機槽來放置共 10 個容量磁碟。這個選項取決於 CPU 型號。

## vSphere 叢集擴充節點的技術規格
{: #vs_vsphereclusteroverview-expansion-node-specs}

每個 vSphere 叢集擴充節點會部署下列元件，並在您的 {{site.data.keyword.slportal}} 帳戶中收取其費用。

### 擴充節點的硬體
{: #vs_vsphereclusteroverview-expansion-node-specs-hardware}

一部具有 [VMware vSphere on {{site.data.keyword.cloud_notm}} 叢集的技術規格](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs)中所呈現之硬體配置的 {{site.data.keyword.cloud_notm}} Bare Metal Server。

### 擴充節點的網路
{: #vs_vsphereclusteroverview-expansion-node-specs-network}

一部具有 [VMware vSphere on {{site.data.keyword.cloud_notm}} 叢集的技術規格](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs)中所呈現之網路配置的 {{site.data.keyword.cloud_notm}} Bare Metal Server。

### 擴充節點的 VMware 元件
{: #vs_vsphereclusteroverview-expansion-node-specs-vmware-components}

* 一個具有 VMware vSphere Enterprise Plus 6.7u1 或 6.5u2 的 {{site.data.keyword.cloud_notm}} Bare Metal Server。  
* 在 [VMware vSphere on {{site.data.keyword.cloud_notm}} 叢集的技術規格](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs)中所呈現的選用 VMWare 元件。

您只能從 {{site.data.keyword.slportal}} 管理 ESXi 伺服器、選用的 VMware 元件和其他已訂購及遞送至您的 {{site.data.keyword.cloud_notm}} 帳戶中的硬體。在 {{site.data.keyword.vmwaresolutions_short}} 主控台中建立新的叢集之後，您可以回到主控台，並使用已儲存的資訊來擴充新的叢集。如需相關資訊，請參閱[擴充現有 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)。
{:important}

## 相關鏈結
{: #vs_vsphereclusteroverview-related}

* [VMware vSphere 軟體資料清單](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
* [規劃 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [訂購 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [擴充現有的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
