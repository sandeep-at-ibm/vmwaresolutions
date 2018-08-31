---

copyright:

  years:  2016, 2018

lastupdated: "2017-08-28"

---

# 1.8 版的版本注意事項

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之其他要訣的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Fortinet on IBM Cloud 服務

現在，Fortinet on {{site.data.keyword.cloud_notm}} 服務可用於 Cloud Foundation 實例及 vCenter Server 實例。此服務會以高可用性模式部署一組 FortiGate Security Appliance (FSA) 300 系列裝置，能提供防火牆、遞送、NAT及 VPN 服務，以維護您實例的公用 VLAN 上的所有伺服器及虛擬機器。您可以在訂購實例時訂購包含 Fortinet 服務的實例，或稍後透過實例詳細資料頁面將此服務新增至現有實例。

在順利安裝 Fortinet 服務之後，您可以從 FortiGate 主控台管理及配置 FSA 的防火牆規則。您必須確定已定義 FSA 防火牆規則為容許由管理元件（例如 IBM CloudDriver 虛擬機器或 Zerto Virtual Manager）起始的出埠 HTTPS 通訊，透過網際網路與 IBM Bluemix® 上的外部管理資料庫通訊。出埠 HTTPS 通訊來自實例中管理服務 VMware NSX Edge Services Gateway (ESG) 的公用 IP 位址。

如需相關資訊，請參閱下列主題：
* [Fortinet on {{site.data.keyword.cloud_notm}} 概觀](../services/fsa_considerations.html)
* [管理 Fortinet on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html)

## Veeam on IBM Cloud 服務

此版本引進 Veeam on {{site.data.keyword.cloud_notm}} 服務，它可同時備份管理元件及工作負載。這項新服務取代先前的 Veeam VSI（其已整合至 1.8 版之前的版本），並僅適用於管理元件的備份。

雖然 1.8 版之前的實例中的 Veeam VSI 會繼續運作，但因為這項變更，{{site.data.keyword.vmwaresolutions_short}} 主控台中不再提供實例的備份點，您必須建立支援問題單，才能獲得還原的協助。

此外，1.8 版之前的實例中的 Veeam VSI 的授權會在 2017 年 10 月 14 日到期。因此，您必須儘早將先前的 Veeam VSI 取代為新的 Veeam 服務。

如需相關資訊，請參閱下列主題：
* [Veeam on {{site.data.keyword.cloud_notm}} 概觀](../services/veeam_considerations.html)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html)

## VMware Cloud Foundation 實例的更新項目

### 訂購 Cloud Foundation 實例時，自帶 VMware 授權 (BYOL)

從 1.8 版開始，當您訂購 Cloud Foundation 實例時，會向您提供兩個選項來為實例的 VMware 元件進行授權，包括 vSphere、vCenter Server、NSX 和 vSAN。您可以選擇使用要代表您購買的新授權。

您也可以選擇對元件使用您自己的 VMware 授權，在此情況下，您需要提供授權碼。在此情況下，針對您提供授權的 VMware 元件，將由 VMware 提供支援，而不是由 IBM 支援中心提供。

如需相關資訊，請參閱下列主題：
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [關於 BYOL 的常見問題](faq_byol.html)

## VMware vCenter Server 實例的更新

### 自訂實例 CPU 及記憶體

可自訂的伺服器選項可與預先建置及測試的「小型」、「中型」及「大型」選項搭配使用。除了 RAM 數量之外，您還可以根據雙 CPU 和核心數目總計，從 VMware HCL 相容伺服器清單中選取。本端儲存空間不可自訂。

如需相關資訊，請參閱下列主題：
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [新增及檢視 vCenter Server 實例的叢集](../vcenter/vc_addingviewingclusters.html)

### 支援新增超過 7 個的 NFS 檔案共用

 在叢集的所有 ESXi 伺服器之間，您最多可以連接 32 個檔案共用。

 如需相關資訊，請參閱下列主題：
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [新增及檢視 vCenter Server 實例的叢集](../vcenter/vc_addingviewingclusters.html)

### 資料中心的更新

下列新的資料中心可用於部署：**DAL-09, DAL-12, DAL-13 - 達拉斯**、**LONG-04, LON-06 - 倫敦**、**SJC-04 - 聖荷西**、**WDC-06, WDC-07 - 華盛頓特區**

如需相關資訊，請參閱 [vCenter Server 實例的需求及規劃](../vcenter/vc_planning.html)

## 可用性加強功能

在整個使用者介面中進行了改善：
* 您可以從左導覽窗格的**開始使用**頁面瞭解服務及訂購實例。如需 {{site.data.keyword.cloud_notm}} Secure Virtualization 服務架構的相關資訊，請參閱[安全及法規遵循 - HyTrust](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/hytrust)。
* 使用實例詳細資料頁面上的溢位功能表來刪除**備妥使用**狀態的實例。
* 現在，**更新及修補程式**標籤提供了升級 NSX 授權版本的選項。授權升級會將您的 IBM SoftLayer 帳戶中所有現有的 NSX 授權取代為新的授權。
* 實例詳細資料頁面上的**備份及還原**標籤不再可用。
* 您可以在訂單開頭選取多個要部署的服務。除了 Zerto on {{site.data.keyword.cloud_notm}} 服務之外，還提供可選取 Veeam on {{site.data.keyword.cloud_notm}} 服務及 Fortinet on {{site.data.keyword.cloud_notm}} 服務的選項。
* 實例詳細資料頁面中**服務**標籤上的**可用的服務**標籤會重新命名為**新增服務**。
