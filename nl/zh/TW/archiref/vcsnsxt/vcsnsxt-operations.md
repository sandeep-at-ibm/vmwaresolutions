---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# vCenter Server 網路的作業考量
{: #vcsnsxt-operations}

## 備份
{: #vcsnsxt-operations-backup}

### VMware vCenter Server on IBM Cloud 備份
{: #vcsnsxt-operations-vcs-backup}

在 {{site.data.keyword.vmwaresolutions_full}} 中，可以選擇性地使用 VMware 叢集以外的「{{site.data.keyword.cloud_notm}} 耐久性」儲存空間，將 Veeam 備份軟體部署至 {{site.data.keyword.cloud_notm}} 虛擬伺服器實例 (VSI)。此軟體的目的是要備份該解決方案中的管理元件。[Veeam on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)提供供應項目的詳細資料。

發生故障時，所有 NSX 元件的備份對於將系統還原到工作狀態而言十分重要。備份 NSX 虛擬應用裝置還不夠，必須使用 NSX Manager 內的 NSX 備份功能，才能進行有效的備份。此作業需要指定 FTP 或 SFTP 伺服器作為 NSX 備份資料的儲存庫。

NSX Manager 備份包含所有 NSX 配置，其中包括控制器、邏輯切換和遞送實體、安全、防火牆規則，以及您在 NSX Manager 使用者介面或 API 中配置的其他所有項目。vCenter 資料庫以及虛擬交換器之類的相關元素需要個別備份。如需詳細資料，請參閱 [NSX 檔案型備份](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#nsx-file-based-backup)。NSX 配置應該隨著 [vCenter 檔案型備份](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#vcenter-file-based-backup)一起備份。

### IBM Cloud Private 的備份及災難回復
{: #vcsnsxt-operations-backup-dr-icp}

發生故障時，{{site.data.keyword.icpfull_notm}} 部署的備份對於將系統還原到其工作狀態而言十分重要。對於傳統 VM 備份，有一個障礙點：每個 {{site.data.keyword.icpfull_notm}} 主節點都會執行 *etcd* 服務，而 *etcd* 文件清楚地表示不要使用傳統 VM 備份來進行還原。

針對平台層次的 {{site.data.keyword.cloud_notm}} Private，您需要備份下列元件。
- **etcd** - etcd 用來儲存 Kubernetes 資源及 Calico 狀態資訊。
- **Docker 登錄** - 此專用映像檔登錄用來儲存容器映像檔。
- **MongoDB** - 計量服務、Helm 儲存庫伺服器、Helm API 伺服器、LDAP 配置、承租戶（名稱空間）及 team/user/usergroup 角色配置會使用此資料庫。
- **MariaDB** - OIDC 使用此資料庫。
-	**Elasticsearch** - 儲存系統和應用程式日誌。
-	**Prometheus** - 儲存用於監視的資料。
-	**持續性儲存空間** - 用於使用 {{site.data.keyword.cloud_notm}} Private 或 Kubernetes 持續性磁區和儲存空間提供者的管理服務。

您可以使用由儲存空間提供者所提供的備份或還原技術。類似的程序也可以延伸到使用者的應用程式中。如需相關資訊，請參閱[如何備份及還原 {{site.data.keyword.cloud_notm}} Private 部落格](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)或 [icp-backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)。

### CAM 的備份及災難回復
{: #vcsnsxt-operations-backup-dr-cam}

發生故障時，CAM 部署的備份對於將系統還原到工作狀態而言十分重要。CAM 備份需要客戶備份下列元件：
-	**Mongo 資料庫** - 主要 CAM 資料庫。
-	**Maria 資料庫** - 供 CAM Blueprint Designer 使用。
-	**NFS/Gluster 檔案系統** - CAM 資料位於四個持續性磁區中。

### IBM Cloud Kubernetes Service 的備份及 DR
{: #vcsnsxt-operations-backup-dr-iks}

etcd 資料庫的備份會隨受管理服務提供給客戶，不過，客戶必須自行備份任何應用程式資料。

## 可調整性
{: #vcsnsxt-operations-scalability}

### vCenter Server 可調整性
{: #vcsnsxt-operations-vcs-scalability}

部署起始主機之後，使用者可以從 {{site.data.keyword.cloud_notm}} for VMware 入口網站內橫向擴充運算容量。

橫向擴充環境遵循下列其中一個路徑：
-	新增由個別 vCenter Server 管理的新站台。
-	新增叢集。
-	新增主機至現有叢集。

#### 多站台部署
{: #vcsnsxt-operations-multi-site}

VMware on {{site.data.keyword.cloud_notm}} 可以使用 {{site.data.keyword.cloud_notm}} 全球資料中心呈現及整合式網路骨幹，讓各種跨地理位置使用案例的部署及運作時間，只需要從頭開始建置這類基礎架構時的一小部分。您可以在 [vCenter Server on {{site.data.keyword.cloud_notm}} 實例的多站台配置](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)找到進一步資訊。

#### 使用新叢集進行橫向擴充
{: #vcsnsxt-operations-scale-out-new-cluster}

使用者也可以從主控台內建立新的叢集、訂購主機，並且新主機將自動新增至叢集，以橫向擴充運算容量。此選項會在環境中建立個別的叢集，讓使用者能夠在實體上和邏輯上將管理工作負載與應用程式工作負載隔離、能夠根據其他性質（例如，Microsoft SQL 資料庫叢集）來隔離工作負載，並且能夠以高可用性拓蹼來部署應用程式。如需相關資訊，請參閱[訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)。

#### 橫向擴充現有叢集
{: #vcsnsxt-operations-scale-out-existing-cluster}

使用者可以從主控台內訂購主機以橫向擴充現有叢集，新主機將會自動新增至叢集。如需相關資訊，請參閱[擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)以取得詳細資料。您可能需要根據其保留需求來調整叢集的 HA 保留原則。

### IBM Cloud Private 及 IBM Cloud Kubernetes Service 可調整性
{: #vcsnsxt-operations-icp-iks-scalability}

根據內部部署或雲端位置可用的運算容量，使用者可以從起始部署的啟動節點橫向擴充節點架構。若要橫向擴充環境，請執行下列動作：
-	擴充 {{site.data.keyword.icpfull_notm}} 工作者節點。
-	擴充並使用 {{site.data.keyword.containerlong_notm}} 供應項目。

#### IBM Cloud Private 擴充
{: #vcsnsxt-operations-icp-expansion}

會調整 {{site.data.keyword.icpfull_notm}} 工作者節點虛擬機器節點，以擴充運算及應用程式：
- 客戶會在部署 {{site.data.keyword.icpfull_notm}} 的相同 VXLAN 中，佈建新的虛擬機器。
- 客戶可以藉由佈建新的虛擬機器，然後登入啟動節點並執行指令，將新節點帶入叢集裡，來調整工作者節點。如需進一步詳細資料，請參閱[新增或移除叢集節點](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)。
- 使用 CAM 以自動佈建 VM 並執行指令，以將它新增至「{{site.data.keyword.icpfull_notm}} 叢集」。

#### IBM Cloud Kubernetes Service 擴充
{: #vcsnsxt-operations-iks-expansion}

使用者可以使用「{{site.data.keyword.cloud_notm}} 入口網站」來佈建 {{site.data.keyword.containerlong_notm}} 環境，以擴充及使用容器環境。如需相關資訊，請參閱[跨 {{site.data.keyword.cloud_notm}} Private 及 {{site.data.keyword.cloud_notm}} 的混合式加強功能](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us)。

使用下列方法，可以將應用程式部署至 {{site.data.keyword.containerlong_notm}}：
-	在 CAM 中開發 {{site.data.keyword.containerlong_notm}} 連線及服務，並發佈至 {{site.data.keyword.icpfull_notm}} 型錄。
-	未來加強 Multi Cloud Manager，以管理 {{site.data.keyword.containerlong_notm}} 實例。
-	Helm 指令行。

## 相關鏈結
{: #vcsnsxt-operations-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
