---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# 3.2 版的版本注意事項
{: #relnotes_v32}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}。

## VMware HCX for IBM Cloud 可用性
{: #relnotes_v32-HCX}

從 3.2 版開始，您現在可以選擇隨 VMware vCenter Server 實例一起訂購 VMware HCX on {{site.data.keyword.cloud_notm}} 服務。先前，您只能透過 VMware vCenter Server with Hybridity Bundle 實例訂購 HCX on {{site.data.keyword.cloud_notm}} 服務。vCenter Server with Hybridity Bundle 實例不再可用。

當您訂購 HCX on {{site.data.keyword.cloud_notm}} 服務時，需要 12 個月的承諾。12 個月的承諾到期之後，您可以安裝及解除安裝 HCX on {{site.data.keyword.cloud_notm}} 服務，且可以新增及移除主機和叢集而不受限制。然後會按月向您的帳戶收取費用，且您可以隨時取消。

如需相關資訊，請參閱 [VMware HCX on IBM Cloud 概觀](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations)。

## VMware vSphere 6.7 Update 2 支援
{: #relnotes_v32-vsphere-v67}

您現在可以選擇隨 VMware vCenter Server、VMware vCenter Server with NSX-T 和 VMware vSphere on IBM Cloud 實例一起訂購 VMware vSphere V6.7 Update 2。vSphere Enterprise Plus 6.7u2 取代隨新實例一起訂購 vSphere Enterprise Plus 6.7u1 的選項。此外，Single-node Trial for Migration and App Modernization 實例和 Single-node Trial for Data Protection and Disaster Recovery 實例現在隨 vSphere Enterprise Plus 6.7u2 一起訂購。

vSphere Enterprise Plus 6.7u2 僅可用於 Skylake、Cascade 和 Broadwell {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}。


如果您有使用 vSphere Enterprise Plus 6.7u1 的現有實例，則可以選擇新增使用 vSphere Enterprise Plus 6.7u1 或 vSphere Enterprise Plus 6.7u2 的新主機。但是，新增新的 6.7u1 主機並不安全。建議您盡快將主機更新為最新的 ESXi 伺服器版本。
{:note}

## Cascade Lake 支援
{: #relnotes_v32-cascade}

從 3.2 版開始，下列新的 {{site.data.keyword.baremetal_short_sing}} CPU 型號可用於部署套用 VMware vSphere 6.7 Update 2 的實例和叢集。這適用於 vCenter Server、vCenter Server with NSX-T 和 VMware vSphere。

* 雙重 Intel Xeon Gold 4210 處理器 / 總計 20 核心，2.3 GHz
* 雙重 Intel Xeon Gold 5218 處理器 / 總計 32 核心，2.3 GHz
* 雙重 Intel Xeon Gold 6248 處理器 / 總計 40 核心，2.5 GHz

Cascade Lake {{site.data.keyword.baremetal_short}} 提供於多區域地區的 {{site.data.keyword.CloudDataCents_notm}}。如需相關資訊，請參閱[多區域地區 (MZR) 概觀](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview)。

如需 {{site.data.keyword.baremetal_short_sing}} 設定的相關資訊，請參閱：

* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [訂購 vCenter Server with NSX-T 實例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## VMware vCenter Server 實例的更新
{: #relnotes_v32-vcs}

本版本對新部署的實例、叢集和主機套用了下列升級和改進：

* VMware NSX for vSphere 6.4.5（建置 13282012）
* vSphere ESXi 6.7 EP 10（建置 6.7.0-13981272）
* vCenter Server Appliance 6.7 Update 2b (6.7.0.-13843469)
* 平台 Services Controller 6.7 Update 2b (6.7.0.-13843469)

如需相關資訊，請參閱 [vCenter Server 資料清單](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

### 初始叢集命名
{: #relnotes_v32-vcs-initial-cluster}

現在，在下實例訂單的同時，可以指定要建立的初始叢集的名稱。如需相關資訊，請參閱：

* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [訂購 vCenter Server with NSX-T 實例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## VMware vSphere 實例的更新
{: #relnotes_v32-vss}

訂購僅具有專用網路的新 vSphere 叢集時，不再需要公用 VLAN。

如需相關資訊，請參閱[訂購新的 vSphere 叢集](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings) 中的*網路介面設定* 小節。

## 附加服務的更新項目
{: #relnotes_v32-services}

此版本在新部署的實例上安裝下列服務版本：

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Update 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Update 4

### VMware vRealize Operations 及 vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} 服務現在已可用於部署在（或升級至）3.2 版或更新版本的 VMware vCenter Server 實例。

此服務提供與 vRealize Operations Manager (vROps) 整合的 VMware vRealize Log Insight (vRLI)，以協助您監視和主動管理虛擬化環境的性能和效能，以及透過過濾和搜尋日誌來對問題的主要原因進行分析。

您可以訂購包含 vRealize Operations 及 vRealize Log Insight on {{site.data.keyword.cloud_notm}} 服務的 vCenter Server 實例，也可以在以後從實例詳細資料頁面的「服務」標籤中將此服務新增至現有實例。

您還可以將自己的企業 vRealize Operations 及 vRealize Log Insight 授權帶到雲端（根據 CPU 或 OSI），也可以向 IBM Cloud 租用授權。

如需相關資訊，請參閱 [VMware vRealize Operations 及 vRealize Log Insight on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview)。

## 新文件與更新的文件
{: #relnotes_v32-updated-doc}

* Activity Tracker 文件已更新。如需相關資訊，請參閱 [Activity Tracker 事件](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events)。

## 使用者介面更新和加強功能
{: #relnotes_v32-ui}

使用者介面已更新，並提供下列加強功能：

* 已變更實例名稱需求。如需相關資訊，請參閱您訂購之實例類型的適當主題。
* 已變更完整 ESXi 伺服器的格式。如需相關資訊，請參閱您訂購之實例類型的適當主題。
* 在主機和叢集名稱中新增前導零，以容許正確排序。
* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
