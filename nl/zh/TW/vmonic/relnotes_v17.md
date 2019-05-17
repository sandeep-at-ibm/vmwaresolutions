---

copyright:

  years:  2016, 2017

lastupdated: "2017-07-05"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 1.7 版的版本注意事項
{: #relnotes_v17}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VMware Cloud Foundation 實例的更新
{: #relnotes_v17-vcf}

此更新會套用下列升級和改善：
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* IBM CloudDriver 元件的穩定性改善
* 在升級時位於 V3 伺服器的預先存在的 VMware 部署上，已啟用 EVC 模式（基於 Intel "Haswell" 2690-V3 處理器）。

  V4 伺服器上的任何現有部署或新部署，都未啟用 EVC 模式。
  {:note}

* 在實例中新增節點時，在 5 月 22 日之前部署因而使用 V3 伺服器的 VMware Cloud Foundation 部署，現在將訂購 V4 伺服器。這些伺服器有 256 GB 記憶體；如果需要 512 GB 記憶體，在新增伺服器之後，請開立支援問題單來要求伺服器升級至 512 GB 記憶體。如需與「IBM 支援中心」聯絡的相關資訊，請參閱[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。

### 更新程序需求
{: #relnotes_v17-update-process}

視 Cloud Foundation 實例部署的複雜性以及您是否具有多站台配置而定，此更新程序可能需要一系列步驟，您必須依照主控台上的**更新及修補程式**標籤上所顯示來完成這些步驟。

## VMware vCenter Server 實例的更新
{: #relnotes_v17-vcs}

### 叢集支援
{: #relnotes_v17-cluster}

從 1.7 版開始，您可以使用叢集來管理 vCenter Server 實例中的 ESXi 伺服器，以取得更好的資源管理和高可用性。依預設，您訂購實例時所配置的 ESXi 伺服器會分組為 **cluster1**。您可以透過實例詳細資料頁面上新建立的**基礎架構**標籤檢視叢集詳細資料，或將最多五個叢集新增至實例。當您擴充或縮減實例的容量時，您可以選取要將 ESXi 伺服器新增至哪一個叢集，或從中移除 ESXi 伺服器。如需相關資訊，請參閱[新增、檢視及刪除 vCenter Server 實例的叢集](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)。

### Zerto 災難回復部署的加強功能
{: #relnotes_v17-zerto}

現在 Zerto 災難回復的部署已自動化，而不必透過支援問題單來處理。預估成本會列出所有 Zerto 元件，例如專用可攜式子網路、Windows VSI（虛擬服務實例）及 Zerto 授權費用，讓您在下訂單之前先檢閱。如需相關資訊，請參閱 [Zerto 災難回復的部署程序](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)。

### NSX 授權升級功能
{: #relnotes_v17-nsx}

您可以從 vCenter Server 實例的**摘要**標籤升級 NSX 授權版本。授權升級會以新的授權取代您帳戶中的所有現有 NSX SoftLayer 授權。如需相關資訊，請參閱[檢視 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)。

## 可用性加強功能
{: #relnotes_v17-ui}

在整個使用者介面中進行了改善：
* Cloud Foundation 實例詳細資料頁面上的**內容**標籤重新命名為**摘要**。您現在可以檢視實例的詳細資料、實例相關元件的存取資訊，以及此標籤上的實例部署歷程。
* Cloud Foundation 實例詳細資料頁面上建立了新的**基礎架構**標籤。您可以在此標籤上檢視、新增或移除 ESXi 伺服器。
* {{site.data.keyword.vmwaresolutions_short}} 的文件具有新的格式，現在連同 Bluemix 文件集，已完全整合至 Bluemix 型錄中。您可以使用下列其中一種方式來存取文件：
  * 從 {{site.data.keyword.vmwaresolutions_short}} 中，按一下橫幅左側的**文件**。
  * 從 Bluemix 文件型錄中，向下捲動到**運算 & 服務**區段，然後按一下 **{{site.data.keyword.vmwaresolutions_short}}**。
