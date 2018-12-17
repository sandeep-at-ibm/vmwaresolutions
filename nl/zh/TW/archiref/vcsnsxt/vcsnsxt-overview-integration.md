---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-12"

---

# 整合、IP 定址及網路流量

## ICP 與 VCS 整合

{{site.data.keyword.cloud}} Private 是安裝在 VCS 實例的數個虛擬機器上。在 VCS 實例內，會使用專用 NSX Edge Services Gateway (ESG) 及「分散式邏輯路由器 (DLR)」來部署 ICP 實例，並使用 VXLAN。

ESG 配置成具有 SNAT 規則以容許出埠資料流量，並啟用網際網路連線功能以下載 ICP 必要條件，以及連接至 GitHub 及 Docker。如果需要，可以使用 Web Proxy 伺服器來提供網際網路連線功能。ESG 配置成使用專用連線功能來存取 DNS 及 NTP 服務。ESG 也配置成具有 DNAT 規則以從 {{site.data.keyword.cloud_notm}} 10.x 網路存取 ICP Master 及 Proxy vIP。

## IKS 與 VCS 整合

目前，有下列情境可整合 IKS 及 VCS 網路：
- **一般 VLAN** - 這需要 IKS 工作者節點部署至與 VCS 實例相同的 VLAN。這可讓 ESG 成為工作者節點的 BGP 對等節點。
- **strongSwan VPN** - 此情境使用標準 IKS 對企業連線功能解決方案。strongSwan 容器提供一個 VPN 閘道，供叢集透過 IPSec 通道將封包轉遞至遠端網路，再轉遞至遠端閘道。此遠端閘道是 VCS 實例上的 ESG。在閘道上，路徑配置成將所有叢集及服務 IP 範圍傳送至 strongSwan 容器，並將所有 VCS BYOIP 位址傳送至 ESG。閘道的目標 IP 位址是指派給 strongSwan 容器之負載平衡器服務的專用可攜式 IP 位址以及 ESG 的專用可攜式 IP 位址。
- **靜態路徑及 NAT**。
- **BGP 對等作業** - BGP 對等作業不是 {{site.data.keyword.cloud_notm}} 中的預設供應項目，而且必須予以要求及核准。啟用之後，BGP 對等作業可讓 Calico vRouter 及 ESG 向 BCR 通告路徑。

## IKS 與 ICP 整合

IKS 及 ICP 整合使用與 ICP 及 IKS 中 strongSwan 容器的 strongSwan VPN 連線功能。

## IP 位址配置

從管理角度來看，本參照架構具有下列概念性網路範圍：
-	**IKS Pod 網路** - 所有部署至工作者節點的 Pod 都會獲指派 172.30.0.0/16 範圍中的專用 IP 位址，並只在工作者節點之間遞送。為了避免衝突，請勿在與工作者節點進行通訊的任何節點上使用此 IP 範圍。使用專用 IP 位址，工作者節點及 Pod 可以在專用網路上安全地進行通訊。不過，Pod 損毀或需要重建工作者節點時，會指派新的專用 IP 位址。
-	**IKS 服務網路** - IKS 在叢集內使用 172.21.0.0/16 作為服務位址。有兩個其他 IP 位址範圍：
    - 公用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的公用可攜式子網路。此 IP 位址範圍用來透過 ALB 或 Ingress 服務向網際網路公開應用程式。
    - 專用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的專用可攜式子網路。此 IP 位址範圍用來透過 ALB 或 Ingress 服務向專用網路公開應用程式。
- **IKS 工作者節點網路** - 有兩個工作者節點網路 IP 位址範圍：
    - 公用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的公用主要子網路。
    - 專用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的專用主要子網路。
-	**VCS 主機網路** - 有兩個 VCS 主機網路 IP 位址範圍：
    - 公用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的公用主要子網路。
    - 專用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的專用主要子網路。
-	**VCS ESG 網路** - 有兩個 VCS ESG 網路 IP 位址範圍：
    - 公用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的公用可攜式子網路。
    - 專用 - 具有 {{site.data.keyword.cloud_notm}} 所提供 IP 位址範圍的專用可攜式子網路。
-	**VCS VM 網路** - 使用未與任何 {{site.data.keyword.cloud_notm}} 所提供子網路衝突之 BYOIP 範圍的企業 IP 位址範圍。
-	**ICP Pod 網路** - 使用未與任何 {{site.data.keyword.cloud_notm}} 所提供子網路衝突之 BYOIP 範圍的企業 IP 位址範圍。Pod 及服務 IP 位址範圍可以配置於 cluster/config.yaml 中。
-	**ICP 服務網路** - 使用未與任何 {{site.data.keyword.cloud_notm}} 所提供子網路衝突之 BYOIP 範圍的企業 IP 位址範圍。Pod 及服務 IP 位址範圍可以配置於 cluster/config.yaml 中。
-	**ICP 工作者節點網路** - 使用未與任何 {{site.data.keyword.cloud_notm}} 所提供子網路衝突之 BYOIP 範圍的企業 IP 位址範圍。

## 網路資料流量

會說明下列資料流量：
-	網際網路上的外部使用者到 IKS 容器中管理的 Web 層級。
-	網際網路上的外部使用者到 ICP 容器中管理的 Web 層級。
-	IKS 容器中管理的 Web 層級到 VCS 的 VM 中管理的資料庫層級。
-	ICP 容器中管理的 Web 層級到 VCS 的 VM 中管理的資料庫層級。
-	組織網路上的企業使用者對 VCS 中 VM 的存取。

### 網際網路上的外部使用者到 IKS 容器中管理的 Web 層級

1.	外部使用者使用 URL 向 Web 層級提出要求。
2.	DNS 用來判斷 IP 位址。此 IP 位址是已指派給 ALB 或「Ingress 服務」之可攜式子網路上的 {{site.data.keyword.cloud_notm}} 公用位址。
3.	公用網路會自動將要求轉遞至管理 ALB 或「Ingress 服務」的工作者節點。
4.	工作者節點會將要求轉遞至 ALB 或「Ingress 服務」的內部叢集 IP 位址及埠號。這個內部叢集 IP 位址只能在叢集內部存取。
5.	在工作者節點內，kube-proxy 會將要求遞送至 ALB 或 Ingress 服務。
6.	如果應用程式位於同一個工作者節點上，則會使用 iptables 來判定用來轉遞要求的內部介面。如果應用程式位於不同的工作者節點，則只有在工作者節點位於不同的子網路時，Calico vRouter 才會使用 IP-in-IP 封裝遞送至適用的工作者節點。

### 網際網路上的外部使用者到 ICP 容器中管理的 Web 層級

1.	外部使用者使用 URL 向 Web 層級提出要求。
2.	DNS 用來判斷 IP 位址。這個 IP 位址將會是已指派給「VCS 實例」之可攜式子網路上的 {{site.data.keyword.cloud_notm}} 公用位址。
3.	公用網路會自動將要求轉遞至管理 ESG 的 vSphere ESXi 主機。
4.	ESG 會將要求轉遞至 ALB 或 Ingress 服務的內部叢集 IP 位址和埠號。如果 ESG 和 ALB 或 Ingress 服務在不同的 vSphere ESXi 主機上，則會將 IP 封包封裝在 VXLAN 訊框中。這個內部叢集 IP 位址只能在叢集內部存取。
5.	在工作者節點內，kube-proxy 會將要求遞送至 ALB 或 Ingress 服務。
6.	如果應用程式位於同一個工作者節點上，則會使用 iptables 來判定用來轉遞要求的內部介面。如果應用程式位於不同的工作者節點，則 Calico vRouter 會使用 IP-in-IP 封裝遞送至適用的工作者節點。IP-in-IP 封包會封裝在 VXLAN 訊框中，以傳輸至工作者節點所在的 vSphere ESXi 主機。

### IKS 容器中管理的 Web 層級到 VCS 的 VM 中管理的資料庫層級

ESG 和 vRouter 中的路徑表格移入方式，取決於整合的方法。請參閱「IKS 與 VCS 整合」。
1.	在 IKS 容器中執行的 Web 層級向在 VCS 實例之 VM 上執行的資料庫提出要求。
2.	DNS 用來將要求解析成資料庫的 IP 位址。
3.	容器將要求傳送至 Calico vRouter。
4.	vRouter 在其路徑表格中移入 VCS 實例上所管理的 IP 位址範圍。
5.	vRouter 轉遞要求，但使用 SNAT 將來源 IP 位址從 Pod 的 IP 位址變更為工作者節點的 IP 位址。
6.	管理 vRouter 的工作者節點將要求傳送至 BCR。
7.	BCR 將要求轉遞至 ESG。
8.	然後，ESG 轉遞至 DLR。
9.	DLR 將要求置於必要的 VXLAN 上。
10.	資料庫 VM 收到要求。

### ICP 容器中管理的 Web 層級到 VCS 的 VM 中管理的資料庫層級

ESG 和 vRouter 中的路徑表格移入方式，取決於整合的方法。請參閱「ICP 與 VCS 整合」。
1.	在 ICP 的容器中執行的 Web 層級向在相同 VCS 實例中之 VM 上執行的資料庫提出要求。
2.	DNS 用來將要求解析成資料庫的 IP 位址。
3.	容器將要求傳送至 Calico vRouter。
4.	vRouter 在其路徑表格中移入 VCS 實例上所管理的 IP 位址範圍。
5.	vRouter 轉遞要求，但使用 SNAT 將來源 IP 位址從 Pod 的 IP 位址變更為工作者節點的 IP 位址。
6.	管理 vRouter 的工作者節點將要求傳送至 ESG。
7.	然後，ESG 轉遞至 DLR。
8.	DLR 將要求置於必要的 VXLAN 上。
9.	資料庫 VM 收到要求。

### 組織網路上的企業使用者存取 VCS 中的 VM

1.	連接至企業內部網路的企業使用者向位在 VCS 中管理之 VM 上的資源提出要求。
2.	DNS 用來判斷 VM 的 IP 位址。這個 IP 位址位於已延伸到 {{site.data.keyword.cloud_notm}} 的網路上。
3.	內部部署路由器將資料流量導向管理「L2 集中器」的 vSphere 主機。
4.	L2 集中器將要求封裝在安全通道中，並透過內部部署路由器，使用指派給裝置的專用可攜式子網路 IP 位址，將要求轉遞至 {{site.data.keyword.cloud_notm}} 中所管理的遠端 L2 集中器。
5.	內部部署路徑會查看其遞送表，並分辨出遠端 L2 集中器的 IP 位址需要被傳送至 WAN 介面，因此藉由 BCR 透過 {{site.data.keyword.cloud_notm}} XCR 路由器在 WAN 上轉遞。
6.	L2 集中器收到要求，並將其置於管理延伸網路的 VXLAN 上。
7.	VM 接收要求。

### 其他資源

* [{{site.data.keyword.cloud_notm}} 網路](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [容器白皮書](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf)（PDF 下載）
* [VMware HCX on {{site.data.keyword.cloud_notm}} 部落格](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [VMware HCX on {{site.data.keyword.cloud_notm}} 資料工作表](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [NSX for vSphere 6.4.3 配置上限](https://configmax.vmware.com/guest)
* [{{site.data.keyword.cloud_notm}} 平台文件](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.cloud_notm}} Kubernetes 服務](https://console.bluemix.net/docs/containers/container_index.html#container_index)
* [Project Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)
