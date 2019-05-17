---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# IBM Cloud Private
{: #vcsnsxt-overview-icp}

{{site.data.keyword.icpfull_notm}} 是一個應用程式平台，用於開發及管理容器化應用程式。這是整合環境，其中包括容器編排程式 Kubernetes、專用映像檔儲存庫、管理主控台、監視架構和圖形使用者介面，您可以集中在此介面中部署、管理、監視及調整應用程式。

{{site.data.keyword.cloud_notm}} Private 具有下列特性：
-	**統一安裝程式** - 透過使用 Ansible 型安裝程式，安裝程式可以利用主節點、工作者節點及 Proxy 節點來快速設定 Kubernetes 型叢集。
-	**{{site.data.keyword.cloud_notm}} Private 管理主控台** - 從單一、集中且安全的管理主控台來管理、監視及疑難排解應用程式和叢集。
-	**Private Docker 映像檔登錄** - 此本端登錄的所有特性都與 Docker Hub 相同，但也可讓您限制哪些使用者可以檢視或取回映像檔。
-	**容器化軟體及服務的型錄** - 此型錄提供集中位置，您可以從中瀏覽套件及將套件安裝至叢集。您可以從策劃的儲存庫取得有額外 IBM 產品的套件，而這些儲存庫包含在預設 {{site.data.keyword.cloud_notm}} Private 儲存庫清單中。
-	**隔離的承租戶網路** - Calico 容許提高您叢集內的效能及網路隔離。使用 Calico，您可以為叢集內的每個專案建立隔離的子網路。此網路隔離可提高您在資料傳輸期間的安全，並減少危及應用程式及其資料的機會。Calico 也有助於建立新的網路原則，而這些原則可以對單一名稱空間內的物件共用啟用精細控制。
-	**使用 ELK 堆疊的健全監視及記載** - {{site.data.keyword.cloud_notm}} Private 使用 Elasticsearch、Logstash、Filebeat 及 Heapster 來收集、儲存及查詢日誌和度量值。此監視及記載處理程序會為所有日誌及度量值提供一個集中儲存庫，以及在您存取及查詢日誌和度量值時，提供較佳的效能並增加穩定性。

## IBM Cloud Private 元件
{: #vcsnsxt-overview-icp-comp}

{{site.data.keyword.cloud_notm}} Private 叢集具有四個主要類別的節點：啟動、主節點、工作者節點及 Proxy。您可以選擇性地在叢集中指定管理、「漏洞警告器 (VA)」及 etcd 節點。
-	**啟動節點** - 啟動節點用於執行安裝、配置、節點調整及叢集更新。
-	**主節點** - 主節點提供管理服務，並且控制叢集中的工作者節點。主節點會管理負責資源配置、狀態維護、排程及監視的處理程序。
-	**工作者節點** - 工作者節點的功能是提供用來執行作業的容器化環境。隨著需求的增加，您可以輕鬆地將更多的工作者節點新增至您的叢集，以改善效能和效率。
-	**Proxy 節點** - Proxy 節點的功能是將外部要求傳輸至在叢集內建立的服務。
-	**管理節點** - 管理節點是選用性節點，只用來管理監視、計量及記載這類管理服務。配置專用的管理節點可以防止主節點超載。
-	**漏洞警告器 (VA) 節點** - VA 節點是選用性節點，可用來執行「漏洞警告器」服務。
-	**etcd** 節點 - etcd 節點是選用性節點，可用來執行 etcd 分散式鍵值儲存庫。

## IBM Cloud Private 網路
{: #vcsnsxt-overview-icp-networking}

使用 Calico 可促進 {{site.data.keyword.icpfull_notm}} 網路管理。Calico 使用 Open System Interconnection (OSI) 模型的第 3 層或網路層。Calico 使用「邊界閘道通訊協定 (BGP)」來建置遞送表，以促進代理程式節點之間的通訊。

如需 Calico 網路的相關資訊，請參閱 [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-overview-iks)。

## 相關鏈結
{: #vcsnsxt-overview-icp-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
