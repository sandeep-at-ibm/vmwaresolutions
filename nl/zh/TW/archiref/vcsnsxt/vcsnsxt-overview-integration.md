---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

# 整合、IP 定址及網路流量
{: #vcsnsxt-overview-integration}

## IBM Cloud Private 及 VMware vCenter Server on IBM Cloud 整合
{: #vcsnsxt-overview-integration-icp-vcs-integration}

{{site.data.keyword.cloud}} Private 安裝在 vCenter Server 實例的數部虛擬機器 (VM) 上。在 vCenter Server 實例內，會使用專用 NSX Edge Services Gateway (ESG) 及「分散式邏輯路由器 (DLR)」來部署 {{site.data.keyword.icpfull_notm}} 實例，並使用 VXLAN。

ESG 配置成具有來源 NAT 規則 (SNAT) 以容許出埠資料流量，這會啟用網際網路連線功能來下載 {{site.data.keyword.icpfull_notm}} 必要條件，以及連接至 GitHub 及 Docker。或者，您也可以使用 Web Proxy 來提供網際網路連線功能。ESG 配置成使用專用連線功能來存取 DNS 及 NTP 服務。ESG 也配置成具有 DNAT 規則，以從 {{site.data.keyword.cloud_notm}} 10.x 網路存取 {{site.data.keyword.icpfull_notm}} Master 及 Proxy vIP。

## IBM Cloud Kubernetes Service 與 vCenter Server 整合
{: #vcsnsxt-overview-integration-iks-vcs-integration}

目前，下列情境整合 {{site.data.keyword.containerlong_notm}} 與 vCenter Server 網路：
- **一般 VLAN** - 需要 {{site.data.keyword.containerlong_notm}} 工作者節點部署至與 vCenter Server 實例相同的 VLAN。「一般 VLAN」可讓 ESG 成為工作者節點的 BGP 對等節點。
- **strongSwan VPN** - 此情境使用標準 {{site.data.keyword.containerlong_notm}} 對企業連線功能解決方案。strongSwan 容器提供一個 VPN 閘道，供叢集透過 IPSec 通道將封包轉遞至遠端網路，再轉遞至遠端閘道。此遠端閘道是 vCenter Server 實例上的 ESG。在閘道上，路徑配置成將所有叢集及服務 IP 範圍傳送至 strongSwan 容器，並將所有 vCenter Server BYOIP 位址傳送至 ESG。閘道的目標 IP 位址是指派給 strongSwan 容器之負載平衡器服務的專用可攜式 IP 位址以及 ESG 的專用可攜式 IP 位址。
- **靜態路徑及 NAT**。
- **BGP 對等作業** - BGP 對等作業不是 {{site.data.keyword.cloud_notm}} 中的預設供應項目，而且必須予以要求及核准。啟用之後，BGP 對等作業可讓 Calico vRouter 及 ESG 向 BCR 通告路徑。

## IBM Cloud Kubernetes Service 與 IBM Cloud Private 整合
{: #vcsnsxt-overview-integration-iks-icp-integration}

{{site.data.keyword.containerlong_notm}} 及 {{site.data.keyword.icpfull_notm}} 整合使用與 {{site.data.keyword.icpfull_notm}} 及 {{site.data.keyword.containerlong_notm}} 中 strongSwan 容器的 strongSwan VPN 連線功能。

## IP 位址配置
{: #vcsnsxt-overview-integration-ip-address-allocation}

從管理角度來看，本參照架構具有下列概念性網路範圍：
-	**{{site.data.keyword.containerlong_notm}} Pod 網路** - 所有部署至工作者節點的 Pod 都會獲指派 172.30.0.0/16 範圍中的專用 IP 位址，並只在工作者節點之間遞送。為了避免衝突，請勿在與工作者節點進行通訊的任何節點上使用此 IP 範圍。使用專用 IP 位址，工作者節點及 Pod 可以在專用網路上安全地進行通訊。不過，Pod 損毀或需要重建工作者節點時，會指派新的專用 IP 位址。
-	**{{site.data.keyword.containerlong_notm}} 服務網路** - {{site.data.keyword.containerlong_notm}} 在叢集內使用 172.21.0.0/16 作為服務位址。以下是兩個其他 IP 位址範圍：
    - 公用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的公用可攜式子網路。此 IP 位址範圍用來透過 ALB 或 Ingress 服務向網際網路公開應用程式。
    - 專用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的專用可攜式子網路。此 IP 位址範圍用來透過 ALB 或 Ingress 服務向專用網路公開應用程式。
- **{{site.data.keyword.containerlong_notm}} 工作者節點網路** - 有兩個工作者節點網路 IP 位址範圍：
    - 公用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的公用主要子網路。
    - 專用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的專用主要子網路。
-	**vCenter Server 主機網路** - 有兩個 vCenter Server 主機網路 IP 位址範圍：
    - 公用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的公用主要子網路。
    - 專用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的專用主要子網路。
-	**vCenter Server ESG 網路** - 有兩個 vCenter Server ESG 網路 IP 位址範圍：
    - 公用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的公用可攜式子網路。
    - 專用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的專用可攜式子網路。
-	**vCenter Server VM 網路** - 使用未與任何 {{site.data.keyword.cloud_notm}} 所提供子網路衝突之 BYOIP 範圍的企業 IP 位址範圍。
-	**{{site.data.keyword.icpfull_notm}} Pod 網路** - 使用未與任何 {{site.data.keyword.cloud_notm}} 所提供子網路衝突之 BYOIP 範圍的企業 IP 位址範圍。Pod 及服務 IP 位址範圍可以配置於 cluster/config.yaml 中。
-	**{{site.data.keyword.icpfull_notm}} 服務網路** - 使用未與任何 {{site.data.keyword.cloud_notm}} 所提供子網路衝突之 BYOIP 範圍的企業 IP 位址範圍。Pod 及服務 IP 位址範圍可以配置於 cluster/config.yaml 中。
-	**{{site.data.keyword.icpfull_notm}} 工作者節點網路** - 使用未與任何 {{site.data.keyword.cloud_notm}} 所提供子網路衝突之 BYOIP 範圍的企業 IP 位址範圍。

## 網路資料流量
{: #vcsnsxt-overview-integration-net-traffic-flows}

會說明下列資料流量：
-	網際網路上的外部使用者到 {{site.data.keyword.containerlong_notm}} 容器中管理的 Web 層級。
-	網際網路上的外部使用者到 {{site.data.keyword.icpfull_notm}} 容器中管理的 Web 層級。
-	{{site.data.keyword.containerlong_notm}} 容器中管理的 Web 層級到 vCenter Server 的 VM 中管理的資料庫層級。
-	{{site.data.keyword.icpfull_notm}} 容器中管理的 Web 層級到 vCenter Server 的 VM 中管理的資料庫層級。
-	組織網路上的企業使用者對 vCenter Server 中 VM 的存取。

### 網際網路上的外部使用者到 IBM Cloud Kubernetes Service 容器中管理的 Web 層級
{: #vcsnsxt-overview-integration-web-tier-iks}

1.	外部使用者使用 URL 向 Web 層級提出要求。
2.	DNS 用來判斷 IP 位址。此 IP 位址是指派給 ALB 或「Ingress 服務」之可攜式子網路上的 {{site.data.keyword.cloud_notm}} 公用位址。
3.	公用網路會自動將要求轉遞至管理 ALB 或「Ingress 服務」的工作者節點。
4.	工作者節點會將要求轉遞至 ALB 或「Ingress 服務」的內部叢集 IP 位址及埠號。這個內部叢集 IP 位址只能在叢集內部存取。
5.	在工作者節點內，kube-proxy 會將要求遞送至 ALB 或 Ingress 服務。
6.	如果應用程式位於同一個工作者節點上，則會使用 iptables 來判定用來轉遞要求的內部介面。如果應用程式位於不同的工作者節點，則只有在工作者節點位於不同的子網路時，Calico vRouter 才會使用 IP-in-IP 封裝遞送至適用的工作者節點。

### 網際網路上的外部使用者到 IBM Cloud Private 容器中管理的 Web 層級
{: #vcsnsxt-overview-integration-web-tier-icp}

1.	外部使用者使用 URL 向 Web 層級提出要求。
2.	DNS 用來判斷 IP 位址。此 IP 位址是指派給 vCenter Server 實例之可攜式子網路上的 {{site.data.keyword.cloud_notm}} 公用位址。
3.	公用網路會自動將要求轉遞至管理 ESG 的 vSphere ESXi 主機。
4.	ESG 會將要求轉遞至 ALB 或「Ingress 服務」的內部叢集 IP 位址及埠號。如果 ESG 和 ALB 或「Ingress 服務」位在不同的 vSphere ESXi 主機上，則會將 IP 封包封裝在 VXLAN 訊框中。這個內部叢集 IP 位址只能在叢集內部存取。
5.	在工作者節點內，kube-proxy 會將要求遞送至 ALB 或 Ingress 服務。
6.	如果應用程式位於同一個工作者節點上，則會使用 iptables 來判定用來轉遞要求的內部介面。如果應用程式位於不同的工作者節點，則 Calico vRouter 會使用 IP-in-IP 封裝遞送至適用的工作者節點。IP-in-IP 封包會封裝在 VXLAN 訊框中，以傳輸至工作者節點所在的 vSphere ESXi 主機。

### IBM Cloud Kubernetes Service 容器中管理的 Web 層級到 vCenter Server 的 VM 中管理的資料庫層級
{: #vcsnsxt-overview-integration-iks-db-tier-vcs}

ESG 和 vRouter 中的路徑表格移入方式，取決於整合的方法。請參閱「{{site.data.keyword.containerlong_notm}} 與 vCenter Server 整合」。
1.	在 {{site.data.keyword.containerlong_notm}} 容器中執行的 Web 層級向在 vCenter Server 實例的 VM 上執行的資料庫提出要求。
2.	DNS 用來將要求解析成資料庫的 IP 位址。
3.	容器將要求傳送至 Calico vRouter。
4.	vRouter 在其路徑表格中移入 vCenter Server 實例上所管理的 IP 位址範圍。
5.	vRouter 轉遞要求，但使用 SNAT 將來源 IP 位址從 Pod 的 IP 位址變更為工作者節點的 IP 位址。
6.	管理 vRouter 的工作者節點將要求傳送至 BCR。
7.	BCR 將要求轉遞至 ESG。
8.	然後，ESG 轉遞至 DLR。
9.	DLR 將要求置於必要的 VXLAN 上。
10.	資料庫 VM 收到要求。

### IBM Cloud Private 容器中管理的 Web 層級到 vCenter Server 的 VM 中管理的資料庫層級
{: #vcsnsxt-overview-integration-icp-db-tier-vcs}

ESG 和 vRouter 中的路徑表格移入方式，取決於整合的方法。請參閱「{{site.data.keyword.icpfull_notm}} 與 vCenter Server 整合」。
1.	在 {{site.data.keyword.icpfull_notm}} 容器中執行的 Web 層級向在相同 vCenter Server 實例的 VM 上執行的資料庫提出要求。
2.	DNS 用來將要求解析成資料庫的 IP 位址。
3.	容器將要求傳送至 Calico vRouter。
4.	vRouter 在其路徑表格中移入 vCenter Server 實例上所管理的 IP 位址範圍。
5.	vRouter 轉遞要求，但使用 SNAT 將來源 IP 位址從 Pod 的 IP 位址變更為工作者節點的 IP 位址。
6.	管理 vRouter 的工作者節點將要求傳送至 ESG。
7.	然後，ESG 轉遞至 DLR。
8.	DLR 將要求置於必要的 VXLAN 上。
9.	資料庫 VM 收到要求。

### 組織網路上的企業使用者對 vCenter Server 中 VM 的存取
{: #vcsnsxt-overview-integration-corporate-network-vcs}

1.	連接至企業內部網路的企業使用者向 vCenter Server 中管理的 VM 上的資源提出要求。
2.	DNS 用來判斷 VM 的 IP 位址。這個 IP 位址位於已延伸到 {{site.data.keyword.cloud_notm}} 的網路上。
3.	內部部署路由器將資料流量導向管理「L2 集中器」的 vSphere 主機。
4.	L2 集中器將要求封裝在安全通道中，並透過內部部署路由器，使用指派給裝置的專用可攜式子網路 IP 位址，將要求轉遞至 {{site.data.keyword.cloud_notm}} 中所管理的遠端 L2 集中器。
5.	內部部署路徑會查看其遞送表，並分辨出遠端 L2 集中器的 IP 位址需要被傳送至 WAN 介面，因此藉由 BCR 透過 {{site.data.keyword.cloud_notm}} XCR 路由器在 WAN 上轉遞。
6.	L2 集中器收到要求，並將其置於管理延伸網路的 VXLAN 上。
7.	VM 接收要求。

## 相關鏈結
{: #vcsnsxt-overview-integration-related}

* [{{site.data.keyword.cloud_notm}} 全球資料中心](https://www.ibm.com/cloud/data-centers/){:new_window}
* [容器白皮書](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf){:new_window}（PDF 下載）
* [VMware HCX on {{site.data.keyword.cloud_notm}} 部落格](https://www.ibm.com/cloud/blog/announcements/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available){:new_window}
* [VMware HCX on {{site.data.keyword.cloud_notm}} 資料工作表](https://www.ibm.com/downloads/cas/MPVXKWNM){:new_window}
* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [NSX for vSphere 6.4.3 配置上限](https://configmax.vmware.com/guest){:new_window}
* [{{site.data.keyword.cloud_notm}} 平台文件](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html){:new_window}
* [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started#getting-started)
* [Project Calico](https://www.projectcalico.org/){:new_window}
* [GitHub-Calico](https://github.com/projectcalico/calico){:new_window}
* [Kubernetes](https://kubernetes.io/){:new_window}
* [GitHub-Flannel](https://github.com/coreos/flannel/){:new_window}
* [GitHub-Canal](https://github.com/projectcalico/canal){:new_window}
