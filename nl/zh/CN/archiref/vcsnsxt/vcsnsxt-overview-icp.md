---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# IBM Cloud Private

{{site.data.keyword.icpfull_notm}} 是一种用于开发和管理容器化应用程序的应用程序平台。ICP 是一个集成环境，包含容器编排器 Kubernetes、专用映像存储库、管理控制台、监视框架和图形用户界面，该界面提供了一个集中位置来部署、管理、监视和扩展应用程序。

{{site.data.keyword.cloud_notm}} Private 具有以下功能：
-	**统一的安装程序** - 安装程序使用基于 Ansible 的安装程序，快速设置包含主节点、工作程序节点和代理节点的基于 Kubernetes 的集群。
-	**{{site.data.keyword.cloud_notm}} Private 管理控制台** - 在一个集中、安全的管理控制台中对应用程序和集群进行管理、监视和故障诊断。
-	**专用 Docker 映像注册表** - 此本地注册表具有 Docker Hub 的所有功能，除此之外还允许您限制哪些用户可以查看或拉出映像。
-	**容器化的软件和服务的目录** - 此目录提供一个集中位置，您可以在其中浏览并安装集群中的软件包。额外 IBM 产品的软件包可从缺省 {{site.data.keyword.cloud_notm}} Private 存储库列表中包含的受监管存储库中获取。
-	**隔离的租户网络** - Calico 支持提高集群内的性能和网络隔离。通过 Calico，您可以为集群内的每个项目创建一个隔离的子网。借助这种网络隔离，数据传输期间的安全性更高，并降低了影响应用程序及其数据的机率。通过 Calico 还能更方便地创建新的网络策略，以用于支持对单个名称空间内的对象共享进行细颗粒度控制。
-	**使用 ELK 堆栈实现稳健的监视和日志记录** - {{site.data.keyword.cloud_notm}} Private 使用 Elasticsearch、Logstash、Filebeat 和 Heapster 来收集、存储和查询日志与度量值。此监视和日志记录过程为所有日志和度量值提供集中存储，并在访问和查询日志和度量值时提高性能和增加稳定性。

## IBM Cloud Private 组件

{{site.data.keyword.cloud_notm}} Private 集群有四种主要的节点类：引导节点、主节点、工作程序节点和代理节点。您可以选择在集群中指定管理节点、漏洞顾问程序 (VA) 节点和 etcd 节点。
-	**引导节点** - 引导节点用于运行安装、配置、节点扩展和集群更新。
-	**主节点** - 主节点提供管理服务，并控制集群中的工作程序节点。主节点托管负责资源分配、状态维护、安排和监视的进程。
-	**工作程序节点** - 工作程序节点是提供容器化环境以运行任务的节点。随着需求的增长，可以轻松地将更多工作程序节点添加到集群以提高性能和效率。
-	**代理节点** - 代理节点是将外部请求传输到集群内部创建的服务的节点。
-	**管理节点** - 管理节点是可选节点，仅托管管理服务，例如监视、测量和日志记录。通过配置专用的管理节点，可以避免主节点超负荷。
-	**漏洞顾问程序 (VA) 节点** - VA 节点是可选节点，用于运行漏洞顾问程序服务。
-	**etcd 节点** - etcd 节点是可选节点，用于运行 etcd 分布式密钥值存储。

## IBM Cloud Private 联网

使用 Calico 可方便地进行 {{site.data.keyword.icpfull_notm}} 网络管理。Calico 使用开放式系统互连 (OSI) 模型的第 3 层，即网络层。Calico 使用边界网关协议 (BGP) 来构建路由表，以便于代理程序节点之间进行通信。

有关 Calico 联网的更多信息，请参阅 [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt/vcsnsxt-overview-iks.html)。

### 相关链接

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
