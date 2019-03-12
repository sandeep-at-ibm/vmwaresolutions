---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-08"

---

# 2.8 版的版本注意事項
{: #relnotes_v28}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## 單一節點試用版移轉及應用程式現代化實例
{: #relnotes_v28-single-node-trial}

「單一節點試用版移轉及應用程式現代化」是一種快速方式，用來測試磁碟機 {{site.data.keyword.cloud_notm}} 以將 VMware 工作負載移轉至 {{site.data.keyword.cloud_notm}}，然後使用容器來現代化工作負載。此試用版是 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 上的 {{site.data.keyword.icpfull_notm}} Hosted 版本，提供容器的 Kubernetes 管理平台，以及可使用與內部部署環境相同之熟悉工具所管理的單一承租戶 VMware 平台。

如需相關資訊，請參閱[單一節點試用版移轉及應用程式現代化概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-single-node-trial-for-migration-and-app-modernization-overview)。

## 新增及移除網路檔案系統儲存空間
{: #relnotes_v28-nfs}

從 2.8 版開始，您現在可以將網路檔案系統 (NFS) 儲存空間共用新增至現有 NFS 或 vSAN vCenter Server 叢集，以及從現有 vCenter Server 叢集移除 NFS 檔案共用。

現在提供下列自訂共用檔案層次儲存空間選項：

* 開始於 20GB 且最多為 12TB 的 NFS 共用大小，且具有單一 GB 增量
* 0.25 IOPS/GB 

如需相關資訊，請參閱[擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances)中的*將 NFS 儲存空間新增至 vCenter Server 實例* 及*從 vCenter Server 實例移除 NFS 儲存空間* 小節。

## SAP 認證的 Broadwell E5-2690 及 E7-8890 伺服器支援
{: #relnotes_v28-broadwell-e5-e7}

從 2.8 版開始，下列新的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 型號可用於部署 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 及 VMware vSphere on {{site.data.keyword.cloud_notm}} 實例和叢集：

* 雙重 Intel Xeon E5-2690 v4 處理器 / 總計 28 核心，2.60 GHz / 512 GB RAM
* 四重 Intel Xeon E7-8890 v4 處理器 / 總計 96 核心，2.20 GHz / 1024 GB RAM
* 四重 Intel Xeon E7-8890 v4 處理器 / 總計 96 核心，2.20 GHz / 2048 GB RAM
* 四重 Intel Xeon E7-8890 v4 處理器 / 總計 96 核心，2.20 GHz / 4096 GB RAM

如需相關資訊，請參閱下列主題中的 *{{site.data.keyword.baremetal_short_sing}} 設定* 小節：
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Broadwell E7-4820 及 E7-4850 伺服器支援
{: #relnotes_v28-broadwell-e7}

從 2.8 版開始，下列新的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 型號可用於部署 vCenter Server、vCenter Server with Hybridity Bundle、Cloud Foundation 及 vSphere on {{site.data.keyword.cloud_notm}} 實例和叢集：

* 四重 Intel Xeon E7-4820 v4 / 總計 40 核心，2.0 GHz 
* 四重 Intel Xeon E7-4850 v4 / 總計 64 核心，2.1 GHz 

如需相關資訊，請參閱下列主題中的 *{{site.data.keyword.baremetal_short_sing}} 設定* 小節：
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [訂購 vCenter Server with Hybridity Bundle 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#bare-metal-server-settings)
* [訂購 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance#bare-metal-server-settings)
* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## 內嵌的 Platform Services Controller
{: #relnotes_v28-psc}

從 2.8 版開始，vCenter Server 部署成具有內嵌的 PSC (Platform Services Controller)，亦即，vCenter Server、vCenter Server 元件及 PSC 部署至單一虛擬機器。此變更會套用至所有新部署的 vCenter Server、vCenter Server with Hybridity 及 NetApp 實例。

對於從舊版本升級至 2.8 版的實例，PSC 不會內嵌在 vCenter Server 中。如果您要使用內嵌的 PSC，則必須自行從外部轉換為內嵌的 PSC。

在主要實例為將 PSC 從外部手動轉換為內嵌之已升級實例的多站台配置中，任何新部署的 2.8 版次要實例都會有內嵌的 PSC。

如需相關資訊，請參閱 [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vcenter-server-architecture)中的 *vCenter Server 架構* 小節。

## VMware vCenter Server 實例的更新
{: #relnotes_v28-vcs}

此版本會套用下列升級及改善：

* vSphere ESXi 6.5 Update P3（建置 6.5.0-10884925）
* vCenter Server 6.5 U2d（建置 6.5.0-10964411）
* Platform Services Controller 6.5 U2d（建置 6.5.0-10964411）

## VMware Cloud Foundation 實例的更新
{: #relnotes_v28-cf}

此版本會套用下列升級及改善：

* vSphere ESXi 6.5 Update EP11（建置 6.5.0-10719125）
* vCenter Server 6.5 U2c（建置 6.5.0-9451637）
* Platform Services Controller 6.5 U2c（建置 6.5.0-9451637）

## 附加服務的更新
{: #relnotes_v28-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v28-spp}

現行版本會將 IBM Spectrum Protect™ Plus 10.1.2 版安裝至所有新部署的實例。如需 IBM Spectrum Protect Plus 10.1.2 版中新增特性的相關資訊，請參閱 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}。

### KMIP for VMware on IBM Cloud
{: #relnotes_v28-kmip}

先前，您可以訂購一個包含 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務的 Cloud Foundation 實例或 vCenter Server 實例，或在初次部署之後，將該服務新增至現有的 Cloud Foundation 實例或 vCenter Server 實例。

從 2.8 版開始，在未關聯至 VMware 實例的情況下，該服務提供為獨立式服務。每個服務實例都可以提供一個以上的 Cloud Foundation 實例、vCenter Server 實例或 vSphere 叢集。

如需相關資訊，請參閱 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)。

## 參照架構文件
{: #relnotes_v28-ref}

（2019 年 2 月 8 日更新）現在可於使用者說明文件的*參照* 小節中取得下列技術文件：

* [{{site.data.keyword.vmwaresolutions_short}} 與 NSX-T 架構](/docs/services/vmwaresolutions/archiref/vcsarch?topic=vmware-solutions-vcsarch-overview)
* [Caveonix RiskForesight 參照架構](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-on-vcs)
* [HCX on {{site.data.keyword.cloud_notm}} 部署及作業手冊](/docs/services/vmwaresolutions/archiref/vcshcx?topic=vmware-solutions-vcshcx-intro)

## 使用者介面更新和加強功能
{: #relnotes_v28-ui}

使用者介面已更新，並提供下列加強功能：

* 提供各種錯誤訊息及工具提示加強功能，以協助您在使用者介面上選取適當的設定。
