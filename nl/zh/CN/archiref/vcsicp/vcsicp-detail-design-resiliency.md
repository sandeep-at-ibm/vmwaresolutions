---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# 备份、灾难恢复和可扩展性

## 备份和 DR

###	VCS 备份

Veeam 备份软件是 {{site.data.keyword.vmwaresolutions_full}} 的一部分，可使用 VMware 集群外部的 {{site.data.keyword.cloud_notm}} 耐久性存储器选择性部署在 {{site.data.keyword.cloud_notm}} 虚拟服务器实例 (VSI) 上。此软件的用途是备份此解决方案中的管理组件。

### NSX 备份

妥善备份所有 NSX 组件至关重要，这样才能在发生故障时将系统复原到其正常运行状态。光备份 NSX VM 是不够的，必须利用 NSX Manager 中的 NSX 备份功能才能实现妥善备份。这需要指定 FTP 或 SFTP 服务器用于 NSX 备份数据的存储库。NSX Manager 备份包含所有 NSX 配置（包括控制器、逻辑交换和路由实体、安全性、防火墙规则以及在 NSX Manager UI 或 API 中配置的其他所有项）。vCenter 数据库以及虚拟交换机等相关元素需要单独备份。NSX 配置应该与 vCenter 备份一起备份。

###	IBM Cloud Private 的备份和 DR

备份 ICP 部署至关重要，这样才能在发生故障时将系统复原到其正常运行状态。对于传统 VM 备份，存在一个症结：每个 ICP 主节点都运行 etcd，但 etcd 文档明确指出不要使用传统 VM 备份来对其进行复原。

对于平台级别的 {{site.data.keyword.cloud_notm}} Private，需要备份以下组件：

-	**Etcd** — 用于存储 Kubernetes 资源以及 Calico 状态信息。
-	**Docker 注册表** — 专用映像注册表，用于将容器映像文件存储在映像存储库中。
-	**MongoDB** — 由测量服务、Helm 存储库服务器、Helm API 服务器、LDAP 配置、租户（名称空间）和 team/user/usergroup 角色配置使用的数据库。
-	**MariaDB** — OIDC 使用的数据库。
-	**Elasticsearch** — 用于存储系统日志和应用程序日志。
-	**Prometheus** — 用于存储数据以供监视。
-	**持久性存储器** — 用于利用 ICP 或 Kubernetes 持久性卷和存储器提供者的管理服务。您可以使用存储器提供者提供的备份或复原技术。也可以将类似的流程扩展到您用户的应用程序中。

###	CAM 的备份和 DR
备份 CAM 部署至关重要，这样才能在发生故障时将系统复原到其正常运行状态。CAM 备份需要客户备份以下组件：
-	**Mongo 数据库** - 主 CAM 数据库。
-	**Maria 数据库** - CAM Blueprint Designer 使用的数据库。
-	**NFS/GlusterFS** - CAM 数据位于 4 个持久性卷中。

### IKS 的备份和 DR
作为受管服务的一部分，会向客户提供 etcd 数据库的备份，但任何应用程序数据都必须由您自行备份。

## 可扩展性

### VCS 可扩展性

部署初始主机后，用户能够在 {{site.data.keyword.cloud_notm}} for VMware 门户网站中向外扩展计算容量。

对环境的这种向外扩展操作采用下列三种方法中的一种方法：
- 添加由单独 vCenter Server 管理的新站点。
- 添加新集群。
- 向现有集群添加新主机。

####	多站点部署
VMware on {{site.data.keyword.cloud_notm}} 可以利用 IBM Cloud 遍布全球的数据中心和集成网络主干，支持部署并运行各种跨地理位置的用例，所用时间只是从头开始构建此类基础架构所需时间的零头。

####	利用新集群向外扩展
用户还可选择通过在控制台中创建新集群和订购主机（新主机会自动添加到新集群）来向外扩展计算容量。此选项将在环境中创建一个单独的集群，并使用户能够在物理和逻辑上将管理工作负载与应用程序工作负载相隔离，能够根据其他特征（例如，Microsoft SQL 数据库集群）来隔离工作负载，并且能够采用高可用性拓扑部署应用程序。

####	向外扩展现有集群
用户可以通过在控制台中订购主机（新主机会自动添加到集群）来向外扩展现有集群。请注意，用户可能需要根据其预留需求来调整集群的 HA 预留策略。

### ICP 可扩展性
根据内部部署或云位置的可用计算容量，用户能够从最初部署的引导节点向外扩展节点体系结构。

向外扩展环境的方法如下：
- 扩展 ICP 工作程序节点。
- 扩展并利用 IKS 产品。

####	ICP 扩展
ICP 工作程序虚拟机节点将扩展为增加计算/应用程序：
  - 客户在部署 ICP 的同一 VXLAN 中供应新的虚拟机。
  - 客户可以通过供应新虚拟机，然后登录到引导节点并运行命令将新节点添加到集群中，从而扩展工作程序节点。
  - 利用 CAM 自动供应 VM 并运行命令以添加到 ICP 集群。


###  IKS 扩展
用户可以通过 {{site.data.keyword.cloud_notm}} 门户网站来供应 IKS 环境，以扩展/利用容器环境。

可通过以下方式将应用程序部署到 IKS：
- IKS 连接/服务在 CAM 中开发，然后发布到 ICP 目录。
- Multi-Cloud Manager 未来会有管理 IKS 实例的增强功能
- Helm 命令行。
- 使用多专区集群来提升高可用性。

### 相关链接
* [添加或除去集群节点](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [通过调整现有工作程序池的大小来添加工作程序节点](../../../../containers/cs_clusters.html#resize_pool)
* [如何备份和复原 {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [ICP 备份 GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [VCS Hybridity Bundle 概述](../vcs/vcs-hybridity-intro.html)
