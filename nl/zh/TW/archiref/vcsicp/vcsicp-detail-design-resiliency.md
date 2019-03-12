---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# 備份、災難回復及可調整性
{: #vcsicp-detail-design-resiliency}

## 備份及 DR
{: #vcsicp-detail-design-resiliency-backup-dr}

### VMware vCenter Server on IBM Cloud 備份
{: #vcsicp-detail-design-resiliency-vcs-backup}

在 {{site.data.keyword.vmwaresolutions_full}} 中，可以選擇性地使用 VMware 叢集以外的「{{site.data.keyword.cloud_notm}} 耐久性儲存空間」，將 Veeam 備份軟體部署至 {{site.data.keyword.cloud_notm}} 虛擬伺服器實例 (VSI)。此軟體的目的是要備份此解決方案中的管理元件。

### NSX 備份
{: #vcsicp-detail-design-resiliency-nsx-backup}

發生故障時，所有 NSX 元件的適當備份對於將系統還原到工作狀態而言十分重要。備份 NSX 虛擬機器 (VM) 還不夠。相反地，必須使用 NSX Manager 內的 NSX 備份功能，才能進行適當的備份。必須指定 FTP 或 SFTP 伺服器作為 NSX 備份資料的儲存庫。
NSX Manager 備份包含所有 NSX 配置，其中包括控制器、邏輯切換和遞送實體、安全、防火牆規則，以及您在 NSX Manager 使用者介面或 API 中配置的其他所有項目。vCenter 資料庫以及虛擬交換器之類的相關元素必須個別備份。NSX 配置必須隨著 vCenter 備份一起備份。

### IBM Cloud Private 的備份及 DR
{: #vcsicp-detail-design-resiliency-backup-dr-icp}

發生故障時，{{site.data.keyword.icpfull_notm}} 部署的備份對於將系統還原到其工作狀態而言十分重要。除了傳統 VM 備份之外，每個 {{site.data.keyword.icpfull_notm}} 主節點都會執行 etcd。etcd 文件清楚地表示不要使用傳統 VM 備份來進行還原。

針對平台層次的 {{site.data.keyword.icpfull_notm}}，您需要備份下列元件：
- **Etcd** - 用來儲存 Kubernetes 資源及 Calico 狀態資訊。
- **Docker 登錄** - 專用映像檔登錄，用來將容器映像檔儲存在映像檔儲存庫中。
- **MongoDB** - 計量服務、Helm 儲存庫伺服器、Helm API 伺服器、LDAP 配置、承租戶（名稱空間）和 team/user/usergroup 角色配置所使用的資料庫。
- **MariaDB** - OIDC 所使用的資料庫。
- **Elasticsearch** - 儲存系統和應用程式日誌。
- **Prometheus** - 儲存用於監視的資料。
- **持續性儲存空間** - 用於使用 {{site.data.keyword.icpfull_notm}} 或「Kubernetes 持續性磁區」和儲存空間提供者的管理服務。您可以使用由儲存空間提供者所提供的備份或還原技術。類似的程序也可以延伸到使用者的應用程式中。

### CAM 的備份及 DR
{: #vcsicp-detail-design-resiliency-backup-dr-cam}

發生故障時，CAM 部署的備份對於將系統還原到工作狀態而言十分重要。CAM 備份需要客戶備份下列元件：
- **Mongo 資料庫**是主要 CAM 資料庫。
- **Maria 資料庫**是 CAM Blueprint Designer 所使用的資料庫。
- **NFS/GlusterFS** 是 CAM 資料位於四個持續性磁區的位置。

### IBM Cloud Kubernetes Service 的備份及 DR
{: #vcsicp-detail-design-resiliency-backup-dr-iks}

etcd 資料庫的備份會隨受管理服務提供給客戶，您必須自行備份任何應用程式資料。

## 可調整性
{: #vcsicp-detail-design-resiliency-scalability}

### VCS 可調整性
{: #vcsicp-detail-design-resiliency-vcs-scalability}

部署起始主機之後，使用者可以從 {{site.data.keyword.cloud_notm}} for VMware 入口網站內橫向擴充運算容量。

此環境橫向擴充遵循以下三種路徑之一：
- 新增由個別 vCenter Server 管理的新站台。
- 新增叢集。
- 新增主機至現有叢集。

#### 多站台部署
{: #vcsicp-detail-design-resiliency-multi-site}

VMware on {{site.data.keyword.cloud_notm}} 可以使用 IBM Cloud 的全球資料中心呈現及整合式網路骨幹，讓各種跨地理位置使用案例的部署及運作時間，只需要從頭開始建置這類基礎架構時的一小部分。

#### 使用新叢集進行橫向擴充
{: #vcsicp-detail-design-resiliency-scale-out-new}

使用者可以從主控台內建立新的叢集、訂購主機，並且新主機將自動新增至叢集，以橫向擴充運算容量。此選項會在環境中建立個別的叢集，讓使用者能夠在實體上和邏輯上將管理工作負載與應用程式工作負載隔離、能夠根據其他性質（例如，Microsoft SQL 資料庫叢集）來隔離工作負載，並且能夠以高可用性拓蹼來部署應用程式。

#### 橫向擴充現有叢集
{: #vcsicp-detail-design-resiliency-scale-out-existing}

使用者可以從主控台內訂購主機以橫向擴充現有叢集，新主機將會自動新增至叢集。使用者可能需要根據其保留需求來調整叢集的 HA 保留原則。

### IBM Cloud Private 可調整性
{: #vcsicp-detail-design-resiliency-icp-scalability}

根據內部部署或雲端位置可用的運算容量，使用者可以從起始部署的啟動節點橫向擴充節點架構。

環境的橫向擴充如下：
- 擴充 {{site.data.keyword.icpfull_notm}} 工作者節點。
- 擴充並使用 {{site.data.keyword.containerlong_notm}} 供應項目。

#### IBM Cloud Private 擴充
{: #vcsicp-detail-design-resiliency-icp-expansion}

會調整 {{site.data.keyword.icpfull_notm}} 工作者節點的 VM 節點，以擴充運算或應用程式：
- 客戶會在部署 {{site.data.keyword.icpfull_notm}} 的相同 VXLAN 中，佈建新的 VM。
- 客戶可以藉由佈建新的 VM，然後登入啟動節點並執行指令，將新節點帶入叢集，來調整工作者節點。
- 使用 CAM 以自動佈建 VM 並執行指令，以新增至「{{site.data.keyword.icpfull_notm}} 叢集」。

###  IBM Cloud Kubernetes Service 擴充
{: #vcsicp-detail-design-resiliency-iks-expansion}

使用者可以透過 {{site.data.keyword.cloud_notm}} 入口網站來佈建 {{site.data.keyword.containerlong_notm}} 環境，以擴充或使用容器環境。

請將下列用於 {{site.data.keyword.containerlong_notm}} 中的應用程式部署：
- 在 CAM 中開發 {{site.data.keyword.containerlong_notm}} 連線或服務，並發佈至 {{site.data.keyword.icpfull_notm}} 型錄。
- 未來加強 Multi-Cloud Manager，以管理 {{site.data.keyword.containerlong_notm}} 實例。
- Helm 指令行介面。
- 使用多區域叢集來增加高可用性。

## 相關鏈結
{: #vcsicp-detail-design-resiliency-related}

* [新增或移除叢集節點](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [調整現有工作者節點儲存區的大小來新增工作者節點](/docs/containers?topic=containers-clusters)
* [如何備份及還原 {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [{{site.data.keyword.icpfull_notm}} 備份 GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
