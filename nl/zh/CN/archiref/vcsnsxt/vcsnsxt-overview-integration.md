---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

# 集成、IP 寻址和网络流
{: #vcsnsxt-overview-integration}

## IBM Cloud Private 与 VMware vCenter Server on IBM Cloud 集成
{: #vcsnsxt-overview-integration-icp-vcs-integration}

{{site.data.keyword.cloud}} Private 安装在一个 vCenter Server 实例上的多个虚拟机 (VM) 上。在 vCenter Server 实例中，{{site.data.keyword.icpfull_notm}} 实例会部署有专用 NSX Edge 服务网关 (ESG) 和分布式逻辑路由器 (DLR)，并使用 VXLAN。

ESG 配置了源 NAT (SNAT) 规则以允许出站流量，支持因特网连接以下载 {{site.data.keyword.icpfull_notm}} 必备软件，以及连接到 GitHub 和 Docker。或者，可以使用 Web 代理进行因特网连接。ESG 配置为使用专用连接来访问 DNS 和 NTP 服务。ESG 还配置了 DNAT 规则，用于支持通过 {{site.data.keyword.cloud_notm}} 10.x 网络来访问 {{site.data.keyword.icpfull_notm}} 主节点和代理 vIP。

## IBM Cloud Kubernetes Service 与 vCenter Server 集成
{: #vcsnsxt-overview-integration-iks-vcs-integration}

目前，以下方案可用于集成 {{site.data.keyword.containerlong_notm}} 与 vCenter Server 联网：
- **公共 VLAN** - 需要 {{site.data.keyword.containerlong_notm}} 工作程序节点部署到 vCenter Server 实例所在的 VLAN 上。公共 VLAN 允许 ESG 作为工作程序节点的 BGP 同级。
- **strongSwan VPN** - 此方案使用标准 {{site.data.keyword.containerlong_notm}} 实现企业连接解决方案。strongSwan 容器为集群提供 VPN 网关，用于将包通过远程网关的 IPSec 隧道转发到远程网络。此远程网关是 vCenter Server 实例上的 ESG。在网关上，路由会配置为将所有集群和服务 IP 范围发送到 strongSwan 容器，并将所有 vCenter Server BYOIP 地址发送到 ESG。网关的目标 IP 地址是分配给 strongSwan 容器的 LoadBalancer 服务的专用可移植 IP 地址，以及 ESG 的专用可移植 IP 地址。
- **静态路由和 NAT**。
- **BGP 对等连接** - BGP 对等连接不是 {{site.data.keyword.cloud_notm}} 中的缺省产品，因此必须请求该产品并得到核准。BGP 对等连接启用后，允许 Calico vRouter 和 ESG 将路径公布到 BCR。

## IBM Cloud Kubernetes Service 与 IBM Cloud Private 集成
{: #vcsnsxt-overview-integration-iks-icp-integration}

{{site.data.keyword.containerlong_notm}} 和 {{site.data.keyword.icpfull_notm}} 集成将使用与 {{site.data.keyword.containerlong_notm}} 和 {{site.data.keyword.icpfull_notm}} 中 strongSwan 容器的 strongSwan VPN 连接。

## IP 地址分配
{: #vcsnsxt-overview-integration-ip-address-allocation}

从管理角度而言，参考体系结构具有以下概念性网络范围：
-	**{{site.data.keyword.containerlong_notm}} pod 网络** - 部署到工作程序节点的所有 pod 都会分配有一个位于 172.30.0.0/16 范围内的专用 IP 地址，并且这些 pod 仅在工作程序节点之间进行路由。为了避免冲突，不要在与工作程序节点通信的任何节点上使用此 IP 范围。工作程序节点和 pod 可以使用专用 IP 地址在专用网络上进行安全通信。但是，pod 崩溃或需要重新创建工作程序节点时，会分配新的专用 IP 地址。
-	**{{site.data.keyword.containerlong_notm}} 服务网络** - {{site.data.keyword.containerlong_notm}} 将 172.21.0.0/16 用于集群内的服务地址。下面是另外两个 IP 地址范围：
    - 公共 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的公用可移植子网。此 IP 地址范围用于通过 ALB 或 Ingress 服务将应用程序公开到因特网。
    - 专用 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的专用可移植子网。此 IP 地址范围用于通过 ALB 或 Ingress 服务将应用程序公开到专用网络。
- **{{site.data.keyword.containerlong_notm}} 工作程序节点网络** - 有两个工作程序节点网络 IP 地址范围：
    - 公共 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的公用主子网。
    - 专用 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的专用主子网。
-	**vCenter Server 主机网络** - 有两个 vCenter Server 主机网络 IP 地址范围：
    - 公共 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的公用主子网。
    - 专用 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的专用主子网。
-	**vCenter Server ESG 网络** - 有两个 vCenter Server ESG 网络 IP 地址范围：
    - 公共 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的公用可移植子网。
    - 专用 - 具有 {{site.data.keyword.cloud_notm}} 提供的 IP 地址范围的专用可移植子网。
-	**vCenter Server VM 网络** - 一个企业 IP 地址范围，使用与 {{site.data.keyword.cloud_notm}} 提供的任何子网都不冲突的 BYOIP 范围。
-	**{{site.data.keyword.icpfull_notm}} pod 网络** - 一个企业 IP 地址范围，使用与 {{site.data.keyword.cloud_notm}} 提供的任何子网都不冲突的 BYOIP 范围。可以在 cluster/config.yaml 中配置 pod 和服务 IP 地址范围。
-	**{{site.data.keyword.icpfull_notm}} 服务网络** - 一个企业 IP 地址范围，使用与 {{site.data.keyword.cloud_notm}} 提供的任何子网都不冲突的 BYOIP 范围。可以在 cluster/config.yaml 中配置 pod 和服务 IP 地址范围。
-	**{{site.data.keyword.icpfull_notm}} 工作程序节点网络** - 一个企业 IP 地址范围，使用与 {{site.data.keyword.cloud_notm}} 提供的任何子网都不冲突的 BYOIP 范围。

## 网络流量流
{: #vcsnsxt-overview-integration-net-traffic-flows}

将对以下流量流进行描述：
-	从因特网上的外部用户到 {{site.data.keyword.containerlong_notm}} 的容器中托管的 Web 层
-	从因特网上的外部用户到 {{site.data.keyword.icpfull_notm}} 的容器中托管的 Web 层
-	从 {{site.data.keyword.containerlong_notm}} 的容器中托管的 Web 层到 vCenter Server 的 VM 中托管的数据库层。
-	从 {{site.data.keyword.icpfull_notm}} 的容器中托管的 Web 层到 vCenter Server 的 VM 中托管的数据库层。
-	企业网络上的企业用户对 vCenter Server 中 VM 的访问。

### 从因特网上的外部用户到 IBM Cloud Kubernetes Service 的容器中托管的 Web 层
{: #vcsnsxt-overview-integration-web-tier-iks}

1.	外部用户使用 URL 向 Web 层发出请求。
2.	使用 DNS 确定 IP 地址。此 IP 地址是可移植子网上已分配给 ALB 或 Ingress 服务的 {{site.data.keyword.cloud_notm}} 公共地址。
3.	公用网络自动将请求转发到托管 ALB 或 Ingress 服务的工作程序节点。
4.	工作程序节点将请求转发到 ALB 或 Ingress 服务的内部集群 IP 地址和端口号。此内部集群 IP 地址仅在集群内可访问。
5.	在工作程序节点中，kube-proxy 将请求路由到 ALB 或 Ingress 服务。
6.	如果应用程序位于同一工作程序节点上，那么将使用 iptables 来确定哪个内部接口用于转发请求。如果应用程序位于其他工作程序节点上，那么仅当该工作程序节点位于不同子网上时，Calico vRouter 才会使用 IP-in-IP 封装来路由到适用的工作程序节点。

### 从因特网上的外部用户到 IBM Cloud Private 的容器中托管的 Web 层
{: #vcsnsxt-overview-integration-web-tier-icp}

1.	外部用户使用 URL 向 Web 层发出请求。
2.	使用 DNS 确定 IP 地址。此 IP 地址是可移植子网上分配给 vCenter Server 实例的 {{site.data.keyword.cloud_notm}} 公共地址。
3.	公用网络自动将请求转发到托管 ESG 的 vSphere ESXi 主机。
4.	ESG 将请求转发到 ALB 或 Ingress 服务的内部集群 IP 地址和端口号。如果 ESG 和 ALB 或 Ingress 服务位于不同的 vSphere ESXi 主机上，那么 IP 包将封装在 VXLAN 帧中。此内部集群 IP 地址仅在集群内可访问。
5.	在工作程序节点中，kube-proxy 将请求路由到 ALB 或 Ingress 服务。
6.	如果应用程序位于同一工作程序节点上，那么将使用 iptables 来确定哪个内部接口用于转发请求。如果应用程序位于其他工作程序节点上，那么 Calico vRouter 会使用 IP-in-IP 封装来路由到适用的工作程序节点。IP-in-IP 包封装在 VXLAN 帧中，以传输到工作程序节点所在的 vSphere ESXi 主机。

### 从 IBM Cloud Kubernetes Service 的容器中托管的 Web 层到 vCenter Server 的 VM 中托管的数据库层
{: #vcsnsxt-overview-integration-iks-db-tier-vcs}

ESG 和 vRouter 中的路由表填充方式取决于集成方法。请参阅“{{site.data.keyword.containerlong_notm}} 与 vCenter Server 集成”。
1.	在 {{site.data.keyword.containerlong_notm}} 的容器中运行的 Web 层向在该 vCenter Server 实例中的 VM 上运行的数据库发出请求。
2.	DNS 用于将请求解析为数据库的 IP 地址。
3.	容器将请求发送到 Calico vRouter。
4.	vRouter 使用在 vCenter Server 实例上托管的 IP 地址范围来填充其路由表。
5.	vRouter 转发该请求，但会使用 SNAT 将源 IP 地址从 pod 的 IP 地址更改为工作程序节点的 IP 地址。
6.	托管 vRouter 的工作程序节点将请求发送给 BCR。
7.	BCR 将请求转发到 ESG。
8.	ESG 随后将该请求转发到 DLR。
9.	DLR 将请求置于所需的 VXLAN 上。
10.	数据库 VM 收到请求。

### 从 IBM Cloud Private 的容器中托管的 Web 层到 vCenter Server 的 VM 中托管的数据库层
{: #vcsnsxt-overview-integration-icp-db-tier-vcs}

ESG 和 vRouter 中的路由表填充方式取决于集成方法。请参阅“{{site.data.keyword.icpfull_notm}} 与 vCenter Server 集成”。
1.	在 {{site.data.keyword.icpfull_notm}} 的容器中运行的 Web 层向在同一 vCenter Server 实例中的 VM 上运行的数据库发出请求。
2.	DNS 用于将请求解析为数据库的 IP 地址。
3.	容器将请求发送到 Calico vRouter。
4.	vRouter 使用在 vCenter Server 实例上托管的 IP 地址范围来填充其路由表。
5.	vRouter 转发该请求，但会使用 SNAT 将源 IP 地址从 pod 的 IP 地址更改为工作程序节点的 IP 地址。
6.	托管 vRouter 的工作程序节点将请求发送给 ESG。
7.	ESG 随后将该请求转发到 DLR。
8.	DLR 将请求置于所需的 VXLAN 上。
9.	数据库 VM 收到请求。

### 企业网络上的企业用户对 vCenter Server 中 VM 的访问
{: #vcsnsxt-overview-integration-corporate-network-vcs}

1.	连接到企业内部网络的企业用户向 vCenter Server 中托管的 VM 上的资源发出请求。
2.	DNS 用于确定 VM 的 IP 地址。此 IP 地址位于延伸到 {{site.data.keyword.cloud_notm}} 的网络上。
3.	内部部署路由器将流量定向到托管 L2 集中器的 vSphere 主机。
4.	L2 集中器将请求封装在安全隧道中，然后通过内部部署路由器，使用分配给设备的专用可移植子网 IP 地址将该请求转发到 {{site.data.keyword.cloud_notm}} 中托管的远程 L2 集中器。
5.	内部部署路径在其路由表中进行查找，并识别到远程 L2 集中器的 IP 地址需要发送到 WAN 接口，然后会通过 BCR 经由 {{site.data.keyword.cloud_notm}} XCR 路由器在 WAN 中进行转发。
6.	L2 集中器收到请求，并将其置于托管延伸网络的 VXLAN 上。
7.	VM 收到请求。

## 相关链接
{: #vcsnsxt-overview-integration-related}

* [{{site.data.keyword.cloud_notm}} 全球数据中心](https://www.ibm.com/cloud/data-centers/){:new_window}
* [容器白皮书](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf){:new_window}（下载 PDF）
* [VMware HCX on {{site.data.keyword.cloud_notm}} 博客](https://www.ibm.com/cloud/blog/announcements/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available){:new_window}
* [VMware HCX on {{site.data.keyword.cloud_notm}} 数据表](https://www.ibm.com/downloads/cas/MPVXKWNM){:new_window}
* [VMware HCX on {{site.data.keyword.cloud_notm}} 解决方案体系结构](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [NSX for vSphere 6.4.3 配置最大值](https://configmax.vmware.com/guest){:new_window}
* [{{site.data.keyword.cloud_notm}} 平台文档](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html){:new_window}
* [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started#getting-started)
* [Project Calico](https://www.projectcalico.org/){:new_window}
* [GitHub-Calico](https://github.com/projectcalico/calico){:new_window}
* [Kubernetes](https://kubernetes.io/){:new_window}
* [GitHub-Flannel](https://github.com/coreos/flannel/){:new_window}
* [GitHub-Canal](https://github.com/projectcalico/canal){:new_window}
