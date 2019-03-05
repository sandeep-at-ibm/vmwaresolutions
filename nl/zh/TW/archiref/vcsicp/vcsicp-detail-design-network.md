---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# 網路存取和流程

## 容器應用程式存取 - IBM Cloud Private

有三種主要方式可以讓外部資料流量及存取進到您的 Kubernetes 叢集應用程式：

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Private

Nodeport 很簡單便可以公開對工作負載的外部存取，它適用於起始開發和測試，但不建議用於正式作業。建議採用 Ingress 或負載平衡器的路徑。

### LoadBalancer - IBM Cloud Private

目前，「{{site.data.keyword.icpfull_notm}} 平台」可針對應用程式工作負載支援外部「負載平衡器」。

### Ingress - IBM Cloud Private

Ingress 是讓入埠連線聯繫叢集服務的規則集合。它可以配置為提供服務可外部聯繫的 URL、為資料流量進行負載平衡、終止 SSL、提供以名稱為基礎的虛擬主機作業等等。{{site.data.keyword.icpfull_notm}} 基礎架構中的 Proxy 節點會執行此功能。

## 容器應用程式存取 - IBM Cloud Kubernetes Service

有三種主要方式可以讓外部資料流量及存取進到您的 Kubernetes 叢集應用程式：

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Kubernetes Service

Nodeport 很簡單便可以公開對工作負載的外部存取，它適用於起始開發和測試，但不建議用於正式作業。建議採用 Ingress 或負載平衡器的路徑。

### LoadBalancer - IBM Cloud Kubernetes Service

每個「{{site.data.keyword.containerlong_notm}} 叢集」都會佈建一個公用或專用「應用程式負載平衡器 (ALB)」。ALB 使用安全且唯一的公用或專用進入點，將送入的要求遞送至您的應用程式。

### Ingress - IBM Cloud Kubernetes Service

Ingress 是讓入埠連線聯繫叢集服務的規則集合。它可以配置為提供服務可外部聯繫的 URL、為資料流量進行負載平衡、終止 SSL、提供以名稱為基礎的虛擬主機作業等等。

## 資料傳輸流

會說明下列資料流量：

- 網際網路上的外部使用者到 {{site.data.keyword.icpfull_notm}} 容器中管理的 Web 層級。
- {{site.data.keyword.icpfull_notm}} 容器中管理的 Web 層級到 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的虛擬機器 (VM) 中管理的資料庫層級。
- 組織網路上的企業使用者對 vCenter Server 中 VM 的存取。

### 網際網路上的外部使用者到 IBM Cloud Private 容器中管理的 Web 層級

1. 外部使用者使用 URL 向 Web 層級提出要求。
2.	DNS 用來判斷 IP 位址。此 IP 位址是指派給 vCenter Server 實例之可攜式子網路上的 {{site.data.keyword.cloud_notm}} 公用位址。
3.	公用網路會自動將要求轉遞至管理 ESG 的 vSphere ESXi 主機。
4.	ESG 會將要求轉遞至 ALB 或「Ingress 服務」的內部叢集 IP 位址及埠號。如果 ESG 和 ALB 或「Ingress 服務」位在不同的 vSphere ESXi 主機上，則會將 IP 封包封裝在 VXLAN 訊框中。這個內部叢集 IP 位址只能在叢集內部存取。
5.	在工作者節點內，kube-proxy 會將要求遞送至 ALB 或 Ingress 服務。
6.	如果應用程式位於同一個工作者節點上，則會使用 iptables 來判定用來轉遞要求的內部介面。如果應用程式位於不同的工作者節點，則 Calico vRouter 會使用 IP-in-IP 封裝遞送至適用的工作者節點。IP-in-IP 封包會封裝在 VXLAN 訊框中，以傳輸至工作者節點所在的 vSphere ESXi 主機。

### IBM Cloud Private 容器中管理的 Web 層級到 vCenter Server 的 VM 中管理的資料庫層級

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

### 	組織網路上的企業使用者對 vCenter Server 中 VM 的存取

1.	連接至企業內部網路的企業使用者向 vCenter Server 中管理之 VM 上的資源提出要求。
2.	DNS 用來判斷 VM 的 IP 位址。此 IP 位址位於延伸至 {{site.data.keyword.cloud_notm}} 的網路上。
3.	內部部署路由器將資料流量導向管理「L2 集中器」的 vSphere 主機。
4.	L2 集中器將要求封裝在安全通道中，並透過內部部署路由器，使用指派給裝置的專用可攜式子網路 IP 位址，將要求轉遞至 {{site.data.keyword.cloud_notm}} 中所管理的遠端 L2 集中器。
5.	內部部署路徑會查看其遞送表，並分辨出遠端「L2 集中器」的 IP 位址需要傳送至 WAN 介面，因此藉由 BCR 透過 {{site.data.keyword.cloud_notm}} XCR 路由器在 WAN 上轉遞。
6.	L2 集中器收到要求，並將其置於管理延伸網路的 VXLAN 上。
7.	VM 接收要求。

## 公用存取網路

依預設，{{site.data.keyword.icpfull_notm}} 和 CAM 需要網際網路連線功能，才能擷取 Docker 映像檔、Helm 圖表、Terrform 範本和作業系統套件管理程式。在最新版本中，針對未直接連接至網際網路，且可選擇以離線模式進行安裝的安裝環境，現在可以支援以 Proxy 為基礎的安裝。

###	NSX 防火牆

{{site.data.keyword.icpfull_notm}} NSX Edge 防火牆配置的規則可以：
*	讓 VXLAN 網路存取公用存取。
*	讓 VXLAN 網路存取專用 {{site.data.keyword.cloud_notm}} 網路存取。
*	讓專用 {{site.data.keyword.cloud_notm}} 網路存取 VXLAN 網路。

### NSX NAT

{{site.data.keyword.icpfull_notm}} NSX NAT 配置下列 NAT：
*	SNAT，讓 VXLAN 網路存取公用存取。
*	SNAT，讓 VXLAN 網路存取專用 {{site.data.keyword.cloud_notm}} 網路存取。
*	DNAT，適用於「{{site.data.keyword.icpfull_notm}} 叢集 vIP」。

### 相關鏈結

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
