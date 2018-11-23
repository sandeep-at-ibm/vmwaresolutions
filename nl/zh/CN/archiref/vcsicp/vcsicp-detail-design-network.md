---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# 网络访问和流

## 容器应用程序访问 - ICP

有三种主要方法可以获取外部流量/对 Kubernetes 集群应用程序的访问：
- NodePort
- LoadBalancer
- Ingress

### NodePort
NodePort 是一种用于公开工作负载外部访问权以进行初始开发和测试的简单方法，但建议不要用于生产环境。对于生产环境，建议使用 Ingress 或 LoadBalancer。

### LoadBalancer
目前，ICP 平台支持外部负载均衡器用于应用程序工作负载。

### Ingress
Ingress 是允许入站连接访问集群服务的规则的集合。Ingress 可以配置为向服务提供外部可访问的 URL，对流量进行负载均衡，终止 SSL 以及提供基于名称的虚拟托管等。ICP 基础架构中的代理节点可执行此功能。

## 容器应用程序访问 - IKS
有三种主要方法可以获取外部流量/对 Kubernetes 集群应用程序的访问：
- NodePort
- LoadBalancer
- Ingress

### NodePort
NodePort 是一种用于公开工作负载外部访问权以进行初始开发和测试的简单方法，但建议不要用于生产环境。对于生产环境，建议使用 Ingress 或 LoadBalancer。

### LoadBalancer
每个 IKS 集群都供应有公共/专用应用程序负载均衡器 (ALB)。ALB 使用安全的唯一公共或专用入口点将入局请求路由到应用程序。

### Ingress
Ingress 是允许入站连接访问集群服务的规则的集合。Ingress 可以配置为向服务提供外部可访问的 URL，对流量进行负载均衡，终止 SSL 以及提供基于名称的虚拟托管等。

## 流量流
将描述以下流量流：
- 从因特网上的外部用户到 ICP 的容器中托管的 Web 层。
- 从 ICP 的容器中托管的 Web 层到 VCS 的 VM 中托管的数据库层。
- 企业网络上的企业用户对 VCS 中 VM 的访问。

### 从因特网上的外部用户到 ICP 的容器中托管的 Web 层
1. 外部用户使用 URL 向 Web 层发出请求。
2.	DNS 用于确定 IP 地址。此 IP 地址将是可移植子网上已分配给 VCS 实例的 {{site.data.keyword.cloud}} 公共地址。
3.	公用网络自动将请求转发到托管 ESG 的 vSphere ESXi 主机。
4.	ESG 将请求转发到 ALB 或 Ingress 服务的内部集群 IP 地址和端口号。如果 ESG 和 ALB 或 Ingress 服务位于不同的 vSphere ESXi 主机上，那么 IP 包将封装在 VXLAN 帧中。此内部集群 IP 地址仅在集群内可访问。
5.	在工作程序节点中，kube-proxy 将请求路由到 ALB 或 Ingress 服务。
6.	如果应用程序位于同一工作程序节点上，那么将使用 iptables 来确定哪个内部接口用于转发请求。如果应用程序位于其他工作程序节点上，那么 Calico vRouter 会使用 IP-in-IP 封装来路由到适用的工作程序节点。IP-in-IP 包将封装在 VXLAN 帧中，以传输到工作程序节点所在的 vSphere ESXi 主机。

### 从 ICP 的容器中托管的 Web 层到 VCS 的 VM 中托管的数据库层
ESG 和 vRouter 中的路由表填充方式取决于集成方法。请参阅“ICP 和 VCS 集成”。
1.	在 ICP 的容器中运行的 Web 层向在同一 VCS 实例中的 VM 上运行的数据库发出请求。
2.	DNS 用于将请求解析为数据库的 IP 地址。
3.	容器将请求发送到 Calico vRouter。
4.	vRouter 使用在 VCS 实例上托管的 IP 地址范围来填充其路由表。
5.	vRouter 转发该请求，但会使用 SNAT 将源 IP 地址从 pod 的 IP 地址更改为工作程序节点的 IP 地址。
6.	托管 vRouter 的工作程序节点将请求发送给 ESG。
7.	ESG 随后将该请求转发到 DLR。
8.	DLR 将请求置于必需的 VXLAN 上。
9.	数据库 VM 收到请求。

### 	企业网络上的企业用户对 VCS 中 VM 的访问。
1.	连接到企业内部网络的企业用户向 VCS 中托管的 VM 上的资源发出请求。
2.	DNS 用于确定 VM 的 IP 地址。此 IP 地址位于延伸到 {{site.data.keyword.cloud_notm}} 的网络上。
3.	内部部署路由器将流量定向到托管 L2 集中器的 vSphere 主机。
4.	L2 集中器将请求封装在安全隧道中，然后通过内部部署路由器，使用分配给设备的专用可移植子网 IP 地址将该请求转发到 {{site.data.keyword.cloud_notm}} 中托管的远程 L2 集中器。
5.	内部部署路径在其路由表中进行查找，并识别到远程 L2 集中器的 IP 地址需要发送到 WAN 接口，然后会通过 BCR 经由 {{site.data.keyword.cloud_notm}} XCR 路由器在 WAN 中进行转发。
6.	L2 集中器收到请求，并将其置于托管延伸网络的 VXLAN 上。
7.	VM 收到请求。

## 公共访问网络
缺省情况下，ICP 和 CAM 需要因特网连接才能检索 Docker 映像、Helm 图表、Terraform 模板以及操作系统软件包管理器。在最新发行版中，现在支持基于代理的安装，可实现不直接连接到因特网的安装，并具有以脱机方式安装的选项。

###	NSX 防火墙
ICP NSX Edge 防火墙配置有允许执行以下操作的规则：
*	启用从 VXLAN 网络访问权到公共访问权的转换。
*	启用从 VXLAN 网络访问权到专用 {{site.data.keyword.cloud_notm}} 网络访问权的转换。
*	启用对 VXLAN 网络的专用 {{site.data.keyword.cloud_notm}} 网络访问权。

### NSX NAT
ICP NSX NAT 配置有以下 NAT：
*	用于从 VXLAN 网络访问权转换为公共访问权的 SNAT
*	用于从 VXLAN 网络访问权转换为专用 {{site.data.keyword.cloud_notm}} 网络访问权的 SNAT。
*	用于 ICP 集群 vIP 的 DNAT。

### 相关链接

* [VCS Hybridity Bundle 概述](../vcs/vcs-hybridity-intro.html)
