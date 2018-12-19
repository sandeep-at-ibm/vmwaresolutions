---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-12"

---

# 集成、IP 寻址和网络流

## ICP 和 VCS 集成

{{site.data.keyword.cloud}} Private 安装在一个 VCS 实例上的多个虚拟机上。在 VCS 实例中，ICP 实例会部署有专用 NSX Edge 服务网关 (ESG) 和分布式逻辑路由器 (DLR)，并使用 VXLAN。

ESG 配置了 SNAT 规则以允许出站流量，支持因特网连接以下载 ICP 必备软件，以及连接到 GitHub 和 Docker。如果需要，可以使用 Web 代理服务器来提供因特网连接。ESG 配置为使用专用连接来访问 DNS 和 NTP 服务。ESG 还配置了 DNAT 规则，用于支持通过 {{site.data.keyword.cloud_notm}} 10.x 网络来访问 ICP 主节点和代理 vIP。

## IKS 和 VCS 集成

目前，有以下方案可用于集成 IKS 和 VCS 联网：
- **通用 VLAN** - 这需要 IKS 工作程序节点部署到与 VCS 实例相同的 VLAN 上。这允许 ESG 成为工作程序节点的 BGP 同级。
- **strongSwan VPN** - 此方案使用标准 IKS 实现企业连接解决方案。strongSwan 容器为集群提供 VPN 网关，用于将包通过远程网关的 IPSec 隧道转发到远程网络。此远程网关是 VCS 实例上的 ESG。在网关上，路由会配置为将所有集群和服务 IP 范围发送到 strongSwan 容器，并将所有 VCS BYOIP 地址发送到 ESG。网关的目标 IP 地址是分配给 strongSwan 容器的 LoadBalancer 服务的专用可移植 IP 地址，以及 ESG 的专用可移植 IP 地址。
- **静态路由和 NAT**。
- **BGP 对等连接** - BGP 对等连接不是 {{site.data.keyword.cloud_notm}} 中的缺省产品，因此必须请求该产品并得到核准。BGP 对等连接启用后，允许 Calico vRouter 和 ESG 将路径公布到 BCR。

## IKS 和 ICP 集成

IKS 和 ICP 集成将使用与 ICP 和 IKS 中 strongSwan 容器的 strongSwan VPN 连接。

## IP 地址分配

从管理角度而言，参考体系结构具有以下概念性网络范围：
-	**IKS pod 网络** - 部署到工作程序节点的所有 pod 都会分配有一个位于 172.30.0.0/16 范围内的专用 IP 地址，并且这些 pod 仅在工作程序节点之间进行路由。为了避免冲突，不要在与工作程序节点通信的任何节点上使用此 IP 范围。工作程序节点和 pod 可以使用专用 IP 地址在专用网络上进行安全通信。但是，pod 崩溃或需要重新创建工作程序节点时，会分配新的专用 IP 地址。
-	**IKS 服务网络** - IKS 将 172.21.0.0/16 用于集群内的服务地址。另外还有两个 IP 地址范围：
    - 公共 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的公用可移植子网。此 IP 地址范围用于通过 ALB 或 Ingress 服务将应用程序公开到因特网。
    - 专用 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的专用可移植子网。此 IP 地址范围用于通过 ALB 或 Ingress 服务将应用程序公开到专用网络。
- **IKS 工作程序节点网络** - 有两个工作程序节点网络 IP 地址范围：
    - 公共 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的公用主子网。
    - 专用 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的专用主子网。
-	**VCS 主机网络** - 有两个 VCS 主机网络 IP 地址范围：
    - 公共 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的公用主子网。
    - 专用 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的专用主子网。
-	**VCS ESG 网络** - 有两个 VCS ESG 网络 IP 地址范围：
    - 公共 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的公用可移植子网。
    - 专用 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的专用可移植子网。
-	**VCS VM 网络** - 一个企业 IP 地址范围，使用与 {{site.data.keyword.cloud_notm}} 提供的任何子网都不冲突的 BYOIP 范围。
-	**ICP pod 网络** - 一个企业 IP 地址范围，使用与 {{site.data.keyword.cloud_notm}} 提供的任何子网都不冲突的 BYOIP 范围。可以在 cluster/config.yaml 中配置 pod 和服务 IP 地址范围。
-	**ICP 服务网络** - 一个企业 IP 地址范围，使用与 {{site.data.keyword.cloud_notm}} 提供的任何子网都不冲突的 BYOIP 范围。可以在 cluster/config.yaml 中配置 pod 和服务 IP 地址范围。
-	**ICP 工作程序节点网络** - 一个企业 IP 地址范围，使用与 {{site.data.keyword.cloud_notm}} 提供的任何子网都不冲突的 BYOIP 范围。

## 网络流量流

下面描述了流量流：
-	从因特网上的外部用户到 IKS 的容器中托管的 Web 层。
-	从因特网上的外部用户到 ICP 的容器中托管的 Web 层。
-	从 IKS 的容器中托管的 Web 层到 VCS 的 VM 中托管的数据库层。
-	从 ICP 的容器中托管的 Web 层到 VCS 的 VM 中托管的数据库层。
-	企业网络上的企业用户对 VCS 中 VM 的访问。

### 从因特网上的外部用户到 IKS 的容器中托管的 Web 层

1.	外部用户使用 URL 向 Web 层发出请求。
2.	DNS 用于确定 IP 地址。此 IP 地址是可移植子网上已分配给 ALB 或 Ingress 服务的 {{site.data.keyword.cloud_notm}} 公共地址。
3.	公用网络自动将请求转发到托管 ALB 或 Ingress 服务的工作程序节点。
4.	工作程序节点将请求转发到 ALB 或 Ingress 服务的内部集群 IP 地址和端口号。此内部集群 IP 地址仅在集群内可访问。
5.	在工作程序节点中，kube-proxy 将请求路由到 ALB 或 Ingress 服务。
6.	如果应用程序位于同一工作程序节点上，那么将使用 iptables 来确定哪个内部接口用于转发请求。如果应用程序位于其他工作程序节点上，那么仅当工作程序节点位于不同子网上时，Calico vRouter 会使用 IP-in-IP 封装来路由到适用的工作程序节点。

### 从因特网上的外部用户到 ICP 的容器中托管的 Web 层

1.	外部用户使用 URL 向 Web 层发出请求。
2.	DNS 用于确定 IP 地址。此 IP 地址将是可移植子网上已分配给 VCS 实例的 {{site.data.keyword.cloud_notm}} 公共地址。
3.	公用网络自动将请求转发到托管 ESG 的 vSphere ESXi 主机。
4.	ESG 将请求转发到 ALB 或 Ingress 服务的内部集群 IP 地址和端口号。如果 ESG 和 ALB 或 Ingress 服务位于不同的 vSphere ESXi 主机上，那么 IP 包将封装在 VXLAN 帧中。此内部集群 IP 地址仅在集群内可访问。
5.	在工作程序节点中，kube-proxy 将请求路由到 ALB 或 Ingress 服务。
6.	如果应用程序位于同一工作程序节点上，那么将使用 iptables 来确定哪个内部接口用于转发请求。如果应用程序位于其他工作程序节点上，那么 Calico vRouter 会使用 IP-in-IP 封装来路由到适用的工作程序节点。IP-in-IP 包将封装在 VXLAN 帧中，以传输到工作程序节点所在的 vSphere ESXi 主机。

### 从 IKS 的容器中托管的 Web 层到 VCS 的 VM 中托管的数据库层

ESG 和 vRouter 中的路由表填充方式取决于集成方法。请参阅“IKS 和 VCS 集成”。
1.	在 IKS 中的容器中运行的 Web 层向在 VCS 实例中的 VM 上运行的数据库发出请求。
2.	DNS 用于将请求解析为数据库的 IP 地址。
3.	容器将请求发送到 Calico vRouter。
4.	vRouter 使用在 VCS 实例上托管的 IP 地址范围来填充其路由表。
5.	vRouter 转发该请求，但会使用 SNAT 将源 IP 地址从 pod 的 IP 地址更改为工作程序节点的 IP 地址。
6.	托管 vRouter 的工作程序节点将请求发送给 BCR。
7.	BCR 将请求转发到 ESG。
8.	ESG 随后将该请求转发到 DLR。
9.	DLR 将请求置于必需的 VXLAN 上。
10.	数据库 VM 收到请求。

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

### 企业网络上的企业用户对 VCS 中 VM 的访问。

1.	连接到企业内部网络的企业用户向 VCS 中托管的 VM 上的资源发出请求。
2.	DNS 用于确定 VM 的 IP 地址。此 IP 地址位于延伸到 {{site.data.keyword.cloud_notm}} 的网络上。
3.	内部部署路由器将流量定向到托管 L2 集中器的 vSphere 主机。
4.	L2 集中器将请求封装在安全隧道中，然后通过内部部署路由器，使用分配给设备的专用可移植子网 IP 地址将该请求转发到 {{site.data.keyword.cloud_notm}} 中托管的远程 L2 集中器。
5.	内部部署路径在其路由表中进行查找，并识别到远程 L2 集中器的 IP 地址需要发送到 WAN 接口，然后会通过 BCR 经由 {{site.data.keyword.cloud_notm}} XCR 路由器在 WAN 中进行转发。
6.	L2 集中器收到请求，并将其置于托管延伸网络的 VXLAN 上。
7.	VM 收到请求。

### 更多资源

* [{{site.data.keyword.cloud_notm}} 网络](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [容器白皮书](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf)（下载 PDF）
* [VMware HCX on {{site.data.keyword.cloud_notm}} 博客](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [VMware HCX on {{site.data.keyword.cloud_notm}} 数据表](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [VMware HCX on {{site.data.keyword.cloud_notm}} 解决方案体系结构](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [NSX for vSphere 6.4.3 配置最大值](https://configmax.vmware.com/guest)
* [{{site.data.keyword.cloud_notm}} 平台文档](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.cloud_notm}} Kubernetes Service](https://console.bluemix.net/docs/containers/container_index.html#container_index)
* [Project Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)
