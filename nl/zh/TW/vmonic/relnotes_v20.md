---

copyright:

  years:  2016, 2018

lastupdated: "2017-11-20"

---

# 2.0 版的版本注意事項

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之其他要訣的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## FortiGate Virtual Appliance on IBM Cloud

現在，FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務可用於 2.0 版以及更新版本的 VMware Cloud Foundation 實例及 VMware vCenter Server 實例。此服務會將一組高可用性 (HA) 的 FortiGate Virtual Appliance 部署到您的環境中，讓您可以在虛擬基礎架構內實作重要安全控制來降低風險。

您可以在訂購實例時訂購內含 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務的實例，或稍後透過實例詳細資料頁面的**服務**標籤，將此服務新增至現有的實例。視您的需求而定，您可以為此服務選取三種部署大小和授權選項的其中之一。在順利安裝此服務之後，您可以從 FortiGate 主控台管理及配置 FortiGate Virtual Appliance 的防火牆規則。

如需相關資訊，請參閱：
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的元件及考量](../services/fortinetvm_considerations.html)
* [管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html)

## F5 on IBM Cloud 及 FortiGate Virtual Appliance on IBM Cloud 的多重服務安裝

您現在可以針對 Cloud Foundation 實例或 vCenter Server 實例，安裝 F5 on {{site.data.keyword.cloud_notm}} 服務及 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務的多個實例。當您在實例訂購期間選取 F5 服務或 FortiGate 服務時，您必須指定服務實例的名稱，以區別它與您後來安裝的其他服務實例。

完成實例部署之後，您可以在實例詳細資料頁面的**新增服務**標籤上安裝服務，以新增 F5 或 FortiGate 服務的更多實例。您一次只能新增一個服務實例，而且您必須針對您要為服務新增的所有實例重複該程序。

如需相關資訊，請參閱：
* [訂購、檢視及移除 Cloud Foundation 實例的服務](../sddc/sd_addingremovingservices.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](../vcenter/vc_addingremovingservices.html)

## FortiGate Security Appliance on IBM Cloud 的更新項目

在此版本中，Fortinet on {{site.data.keyword.cloud_notm}} 服務已重新命名為 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}，而且，依預設，該服務的一組 FortiGate Security Appliance (FSA) 在部署至實例時已安全配置。
* 如果您將一組 FSA 部署為新的 Cloud Foundation 實例或 vCenter Server 實例的一部分，則 FSA 是配置為僅容許從實例到公用網路的必要出埠通訊，並拒絕所有其他通訊。
* 如果您將一組 FSA 部署為現有 Cloud Foundation 實例或 vCenter Server 實例的一部分，則會使用明確規則來配置 FSA，以容許從實例到公用網路的所有必要出埠管理通訊，同時也會以其他規則配置 FSA 容許所有其他通訊，以確保您現有的應用程式資料流量不會中斷。

無論如何，您都必須小心管理 FSA 配置，以僅容許必要的通訊，並拒絕所有其他通訊。

## 完整網域名稱格式一致性

所有實例的完整網域名稱 (FQDN) 現在會以一致的方式來表示。下訂單時，您可以輸入自己的子網域字首和主機名稱字首。這可確保遵循 FQDN 格式的業界慣例，例如：`host-name-prefix<n>.subdomain-prefix.domain-name`。

如需相關資訊，請參閱：
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [訂購新的 vSphere 叢集](../vsphere/vs_orderinginstances.html)

## 在實例訂購期間的工作負載及儲存空間預估

* 在 VMware vSphere on {{site.data.keyword.cloud_notm}} 訂單期間，會提供您可以在所訂購的實例上執行的虛擬機器數目的預估。
* 在 Cloud Foundation 和 vCenter Server 訂單期間，會提供您所訂購的實例的可用儲存空間容量的預估。

如需相關資訊，請參閱：
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [訂購新的 vSphere 叢集](../vsphere/vs_orderinginstances.html)

## VMware Cloud Foundation 實例的更新項目

現行版本會針對新的部署，套用下列元件更新項目及改進項目：

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware SDDC Manager 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5, Patch Release ESXi650-201710401-BG：更新 esx-base、esx-tboot、vsan 及 vsanhealth VIB (2151061)。如需修補程式詳細資料，請參閱 [VMware vCenter Server Appliance Photon OS 安全修補程式](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}。

**附註**：現有實例（來自 1.9 版及更舊版本）無法升級至此清單中的元件版本。

如需元件的相關資訊，請參閱 [Cloud Foundation 概觀](../sddc/sd_cloudfoundationoverview.html)。

### Cloud Foundation 實例的叢集支援

您現在可以使用叢集來管理在 2.0 版以及更新版本中部署的 Cloud Foundation 實例中的 ESXi 伺服器，以獲得更好的資源管理和高可用性。依預設，您訂購實例時所配置的 ESXi 伺服器會分組為 **SDDC-Cluster**。

您可以在實例詳細資料頁面上的**基礎架構**標籤上檢視叢集詳細資料，或將最多五個叢集新增至實例。當您擴充或縮減實例的容量時，您可以選取要將 ESXi 伺服器新增至哪一個叢集，或從中移除 ESXi 伺服器。如需相關資訊，請參閱[新增及檢視 Cloud Foundation 實例的叢集](../sddc/sd_addingviewingclusters.html)。

### Cloud Foundation 實例的自訂 vSAN 儲存空間的支援

您現在可以在實例訂單中選取 vSAN 儲存空間硬碟的數目和大小，以自訂 vSAN 儲存空間配置。

如需相關資訊，請參閱：
* [Cloud Foundation 概觀](../sddc/sd_cloudfoundationoverview.html)
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)

### Cloud Foundation 實例的 VMware vSAN 授權版本的選擇：Advanced 或 Enterprise

您現在可以在 Cloud Foundation 實例訂單期間，選取您想要的 vSAN 授權版本。您可以購買該授權作為訂單的一部分，或「自帶授權 (BYOL)」。如需相關資訊，請參閱[訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)。

### Cloud Foundation 實例的新標準化 IBM Bare Metal Server 配置

下列 Bare Metal Server 配置設定現在可供使用：
* 小型（雙重 Intel Xeon E5-2650 v4 /總計 24 核心，2.2 GHz / 128 GB RAM / 12 個磁碟）
* 大型（雙重 Intel Xeon E5-2690 v4 /總計 28 核心，2.6 GHz / 512 GB RAM / 12 個磁碟）

**附註**：機箱有 12 個磁碟的空間，但並非所有插槽都已填滿。**小型**配置提供兩個 1.9 TB Micron 5100 MAX 磁碟機，**大型**配置提供四個 3.8 TB Micron 5100 PRO 磁碟機。

如需相關資訊，請參閱：
* [Cloud Foundation 概觀](../sddc/sd_cloudfoundationoverview.html)
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)

## VMware vCenter Server 實例的更新

現行版本會針對新部署套用下列元件更新項目：

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

**附註：** vCenter Server 自訂的訂單不管有沒有 VMware vSAN 元件，一律會包括 12 磁碟機箱伺服器，這在價格預估 PDF 中反映了 {{site.data.keyword.baremetal_short}} 對於非 vSAN 訂單案例的成本略高。

如需元件的相關資訊，請參閱 [vCenter Server 概觀](../vcenter/vc_vcenterserveroverview.html)。

### vCenter Server 實例的多站台配置支援

除了連接至主要實例的次要實例之外，您現在還可以部署單一 vCenter Server 實例。多站台配置模型使用中心與分支拓蹼來搭配一個主要站台及最多七個次要站台。

如需相關資訊，請參閱 [vCenter Server 實例的多站台配置](../vcenter/vc_multisite.html)。

### vCenter Server 實例的自訂 vSAN 儲存空間支援

現在，vSAN 儲存空間可用於主要實例及次要實例的 vCenter Server 實例。只有在選取使用者自訂的配置時，才能使用它。您現在可以在 vCenter Server 實例訂單期間，選取您想要的 vSAN 授權版本（Advanced 或 Enterprise）。您可以購買該授權作為訂單的一部分，或「自帶授權 (BYOL)」。

如需相關資訊，請參閱[訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)。

### VMware vCenter Server 實例的「自帶授權 (BYOL)」

現在 vCenter Server 實例可以使用 BYOL。BYOL 可讓您在訂購 vCenter Server 實例時，使用一個以上您自己的 vCenter Server、vSphere、vSAN 及 NSX VMware 授權。

如需相關資訊，請參閱：
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [訂購新的 vSphere 叢集](../vsphere/vs_orderinginstances.html)

## VMware vSphere on IBM Cloud 的更新項目

### Bare Metal Server 的新磁碟類型

對於 VMware vSAN 元件，下列磁碟類型現在可用於 {{site.data.keyword.baremetal_short}}：
* 960 GB SSD SED
* 1.9 TB SSD SED
* 3.8 TB SSD SED

**附註：**
* 當 3.8 TB SSD SED 磁碟機在正式發行至 {{site.data.keyword.CloudDataCent_notm}} 時將會予以支援。
* 訂單不管有沒有 VMware vSAN 元件，一律會包括 12 磁碟機箱伺服器，這在價格預估 PDF 中反映了 {{site.data.keyword.baremetal_short}} 對於非 vSAN 訂單案例的成本略高。

如需相關資訊，請參閱[訂購新的 vSphere 叢集](../vsphere/vs_orderinginstances.html)。

## NetApp ONTAP Select on IBM Cloud 的更新項目

### 新的 Bare Metal Server 選項

現在可以使用下列 Bare Metal Server 配置選項：
* **高效能（中型）**- 超值授權/雙重 Intel Xeon E5-2650 v4（總計 24 核心，2.2 GHz）/128 GB RAM/每個節點有 22 個 1.9 TB SSD 磁碟機容量/4 節點叢集的有效容量 - 59 TB
* **高效能（大型）**- 超值授權/雙重 Intel Xeon E5-2650 v4（總計 24 核心，2.2 GHz）/128 GB RAM/每個節點有 22 個 3.8 TB SSD 磁碟機容量/4 節點叢集的有效容量 - 118 TB
* **高容量** - 標準授權/雙重 Intel Xeon E5-2650 v4（總計 24 核心，2.2 GHz）/64 GB RAM/每個節點 10 個 4 TB SATA 磁碟機容量/4 節點叢集的有效容量 - 60 TB

**附註：**當 3.8 TB SSD 磁碟機在正式發行至 {{site.data.keyword.CloudDataCent_notm}} 時將會予以支援。

如需相關資訊，請參閱：
* [NetApp ONTAP Select 概觀](../netapp/np_netappoverview.html)
* [訂購 NetApp ONTAP Select 實例](../netapp/np_orderinginstances.html)

## 新的及更新的文件

VMware Cloud Foundation 使用者可搭配 {{site.data.keyword.cloud_notm}} 上的 VMware NSX 平台使用逐步指示，讓虛擬機器能夠彼此通訊以及與網際網路通訊。如需相關資訊，請參閱[在 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} (VCF) 上設定工作負載 VM 的 NSX](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}。

## 使用者介面更新和加強功能

* 現在，可以新增至叢集的 ESXi 伺服器數目上限已更新為 32 部伺服器。叢集數目上限仍維持 5 個。
* 在**已部署的實例**頁面上，實例摘要表格中的 **ESXi 伺服器**直欄會取代為**版本**直欄，您可以在其中尋找實例已部署於或更新至的版次。
* 現在，實例詳細資料頁面上提供了 SDDC Manager for Cloud Foundation 實例的版本。
* 已提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
