---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-29"

---

# VMware vSphere on IBM Cloud 概觀

VMware vSphere on {{site.data.keyword.cloud}} 是 VMware 的簡化與最佳化訂購平台，可讓您根據所選取的 VMware 元件，自訂及訂購 VMware 相容硬體，以建置您自己的 IBM 代管 VMware 環境。

{{site.data.keyword.vmwaresolutions_short}} 主控台會根據您選取的 VMWare 元件而自動過濾硬體。例如，在建立新的全快閃記憶體 VMware SAN 叢集時，只會呈現根據 [VMware 相容性手冊](https://www.vmware.com/resources/compatibility/search.php)所驗證的硬體，且至少需要 4 部 ESXi 伺服器。

VMware vSphere on {{site.data.keyword.cloud_notm}} 不會使選用的 VMware 元件的安裝、配置及啟動自動化，它容許最大的彈性來設計及建置代管的 VMware 環境，同時納入 VMware 相容的硬體。

使用此供應項目來建立 ESXi 伺服器的新叢集，或在 {{site.data.keyword.CloudDataCent_notm}} 中擴充 ESXi 伺服器的現有叢集。視您選取的 VMware 元件而定，您可以只從一部 ESXi 伺服器開始，稍後再視需要擴充叢集。

## VMware vSphere on IBM Cloud 的元件

檢閱 VMware vSphere on {{site.data.keyword.cloud_notm}} 的元件。

**附註**：標準化硬體配置的可用性和定價可能會根據所選取用於部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。

### VMware 元件

下列 VMware 元件的授權（IBM 提供或 BYOL）：
* VMware vSphere Enterprise Plus 6.0u2 或 6.5u1
* 選用的 VMware 元件：
   * VMware vCenter Server Standard
   * VMware NSX（Base、Advanced 或 Enterprise）
   * VMware vSAN（Advanced 或 Enterprise）
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

具有所選取 CPU 型號及 RAM 大小的一個以上 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}：
* 2-CPU Intel Broadwell Generation（Intel Xeon E5-2600 v4 系列）
* 2-CPU Intel Skylake Generation（Intel Xeon 4100/5100/6100 系列）

可用的選項取決於您是否已選取 VMware vSAN 元件。

此外，下列磁碟和網路規格：
* 10 Gbps 雙重公用及專用網路上行鏈路
* 一個 RAID 磁碟控制器

### 網路

* 三個 VLAN（虛擬 LAN）：一個公用 VLAN 和兩個專用 VLAN
* （選用）一組 HA 的 FortiGate Security Appliance 裝置

### 儲存空間

選取 VMware vSAN 元件時用於 vSAN 配置的使用者自訂儲存空間：
* 儲存空間磁碟選項：960 GB SSD SED、1.9 TB SSD SED 或 3.8 TB SSD SED
* 磁碟數量選項：2、4、6 或 8

**附註：**當 3.8 TB SSD（固態硬碟）磁碟機在正式發行至資料中心時就會予以支援。

## vSphere 叢集擴充節點的元件

每一個 vSphere 叢集擴充節點將部署下列元件，並在您的 {{site.data.keyword.slportal}} 帳戶中收取其費用。

### 擴充節點的硬體

一部具有 [VMware vSphere on IBM Cloud 的元件](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)中所呈現之硬體配置的 IBM Cloud Bare Metal Server。

### 擴充節點的網路

一部具有 [VMware vSphere on IBM Cloud 的元件](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)中所呈現之網路配置的 IBM Cloud Bare Metal Server。

### 擴充節點的 VMware 元件

* 一部具有 VMware vSphere Enterprise Plus 6.0u2 或 6.5u1 的 IBM Cloud Bare Metal Server  
* 在 [VMware vSphere on IBM Cloud 的元件](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)中所呈現的選用 VMWare 元件。

**重要事項**：您只能從 {{site.data.keyword.slportal}} 管理 ESXi 伺服器、選用的 VMware 元件和其他已訂購及遞送至您的 {{site.data.keyword.cloud_notm}} 帳戶中的硬體 。在 {{site.data.keyword.vmwaresolutions_short}} 主控台中建立新的叢集之後，您可以回到主控台，利用已儲存的配置來擴充新的叢集。如需相關資訊，請參閱[擴充現有叢集](vs_scalingexistingclusters.html)。

## 相關鏈結

* [VMware vSphere 軟體資料清單](vs_bom.html)
* [規劃 vSphere 叢集](vs_planning.html)
* [訂購 vSphere 叢集](vs_orderinginstances.html)
* [擴充現有的 vSphere 叢集](vs_scalingexistingclusters.html)
