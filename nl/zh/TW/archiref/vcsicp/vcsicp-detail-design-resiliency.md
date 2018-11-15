---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# 備份、災難回復及可調整性

## 備份及 DR

###	VCS 備份

在 IBM Cloud for VMware Solutions 中，可以選擇使用 VMware 叢集外部的 IBM Cloud Endurance Storage，將 Veeam 備份軟體部署在 IBM Cloud 虛擬伺服器實例 (VSI) 上。此軟體的目的是要備份此解決方案中的管理元件。

### NSX 備份

發生故障時，所有 NSX 元件的適當備份對於將系統還原為工作狀態而言十分重要。備份 NSX VM 還不夠，必須使用 NSX Manager 中的 NSX 備份功能，才能進行適當的備份。這需要為 NSX 備份資料的儲存庫指定 FTP 或 SFTP 伺服器。NSX Manager 備份包含所有 NSX 配置，其中包括控制器、邏輯切換和遞送實體、安全、防火牆規則，以及您在 NSX Manager 使用者介面或 API 中配置的其他所有項目。vCenter 資料庫以及虛擬交換器之類的相關元素需要個別備份。NSX 配置應隨著 vCenter 備份一起備份。

###	IBM Cloud Private 的備份及 DR

發生故障時，ICP 部署的備份對於將系統還原為工作狀態而言十分重要。在傳統 VM 備份之上有一個障礙點，每個 ICP 主要節點都會執行 etcd，而 etcd 文件清楚地表示不要使用傳統 VM 備份來進行還原。

IBM Cloud Private 在平台層次，您必須備份以下元件：

-	**Etcd** — 用來儲存 Kubernetes 資源以及 Calico 狀態資訊。
-	**Docker 登錄** — 專用映像檔登錄，用來將容器映像檔儲存在映像檔儲存庫中。
-	**MongoDB** — 計量服務、Helm 儲存庫伺服器、Helm API 伺服器、LDAP 配置、承租戶（名稱空間）和 team/user/usergroup 角色配置所使用的資料庫。
-	**MariaDB** — OIDC 所使用的資料庫。
-	**Elasticsearch** — 儲存系統和應用程式日誌。
-	**Prometheus** — 儲存用於監視的資料。
-	**持續性儲存空間** — 用於運用 ICP 或 Kubernetes 持續性磁區和儲存空間提供者的管理服務。您可以使用由儲存空間提供者所提供的備份或還原技術。類似的程序也可以延伸到使用者的應用程式中。

###	CAM 的備份及 DR
發生故障時，CAM 部署的備份對於將系統還原為工作狀態而言十分重要。CAM 備份需要客戶備份下列元件：
-	**Mongo 資料庫** – 主要 CAM 資料庫。
-	**Maria 資料庫** - 供 CAM Blueprint Designer 使用。
-	**NFS/GlusterFS** - CAM 資料位於四個持續性磁區中。

### IKS 的備份及 DR
etcd 資料庫的備份會隨受管理服務提供給客戶，您必須自行備份任何應用程式資料。

## 可調整性

### VCS 可調整性

部署起始主機之後，使用者可以從 IBM Cloud for VMware 入口網站內橫向擴充運算容量。

此環境橫向擴充遵循以下三種路徑之一：
- 新增由個別 vCenter Server 管理的新站台
- 新增叢集。
- 新增主機至現有叢集。

####	多站台部署
VMware on IBM Cloud 可以運用 IBM Cloud 的全球資料中心顯示狀態及整合式網路骨幹，讓各種跨地理位置使用案例在一段時間內部署及運作，以從頭開始建置這類基礎架構。

####	使用新叢集進行橫向擴充
使用者也可以選擇從主控台內建立新的叢集、訂購主機，並且新主機將自動新增至叢集，以橫向擴充運算容量。此選項會在環境中建立個別的叢集，讓使用者能夠在實體上和邏輯上將管理工作負載與應用程式工作負載隔離、能夠根據其他性質（例如，Microsoft SQL 資料庫叢集）來隔離工作負載，並且能夠以高可用性拓蹼來部署應用程式。

####	橫向擴充現有叢集
使用者可以從主控台內訂購主機，並且新主機將自動新增至叢集，以橫向擴充現有叢集。請注意，使用者可能需要根據其保留需求來調整叢集的 HA 保留原則。

### ICP 可調整性
根據內部部署或雲端位置可用的運算容量，使用者能夠從起始部署的啟動節點橫向擴充節點架構。

環境的橫向擴充如下：
- 擴充 ICP 工作者節點。
- 擴充並使用 IKS 供應項目。

####	ICP 擴充
調整 ICP 工作者節點虛擬機器節點，以擴充運算/應用程式：
  - 客戶會在部署 ICP 的相同 VXLAN 中，佈建新的虛擬機器。
  - 客戶可以藉由佈建新的虛擬機器來調整工作者節點，然後登入啟動節點並執行指令，以將新節點帶入叢集中。
  - 使用 CAM 以自動佈建 VM 並執行指令，以新增至「ICP 叢集」。


###  IKS 擴充
使用者可以透過 IBM Cloud 入口網站來佈建 IKS 環境，以擴充/運用容器環境。

可以透過以下方式完成將應用程式部署至 IKS：
- 在 CAM 中開發 IKS 連線/服務，並發佈至 ICP 型錄。
- 未來加強 Multi-Cloud Manager，以管理 IKS 實例
- Helm 指令行。
- 使用多區域叢集來增加高可用性。

### 相關鏈結
* [新增或移除叢集節點](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [調整現有工作者節點儲存區的大小來新增工作者節點](https://console.bluemix.net/docs/containers/cs_clusters.html#add_workers)
* [如何備份及還原 IBM Cloud Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [ICP 備份](https://github.com/ibm-cloud-architecture/icp-backup/)
* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
