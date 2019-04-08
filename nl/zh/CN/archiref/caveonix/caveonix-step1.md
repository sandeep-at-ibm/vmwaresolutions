---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

# 步骤 1 - 初始规划和先决条件
{: #caveonix-step1}

每个 Caveonix RiskForesight 应用程序组件都是松散耦合的，但集中进行管理。因此，可以通过“一体化”虚拟机 (VM) 部署模式来部署这些组件，或者应用程序组件可以“横向扩展”并部署在多个 VM 上，以提高可用性、性能和容量。

部署模式基于可用性需求和数据保留大小调整。RiskForesight 部署节点的特征如下：

-	基本 VM - 基本 VM 托管由于数据保留而不缩放的应用程序组件。这些组件包括：RiskForesight UI、RiskForesight 应用程序、RiskForesight 插件、中央收集器、远程收集器、索引数据存储、消息传递数据存储和关系数据存储。
-	横向扩展 VM - 横向扩展 VM、数据库和数据索引根据资产数和所需的数据保留量进行扩展，从而创造需求来增加横向扩展硬盘空间，从而增加横向扩展 VM。

有三个 Caveonix RiskForesight 部署模型：

-	“一体化”- 自动部署和配置 1 个 VM，用于托管所有应用程序组件：
  - 所有应用程序组件安装在一个 VM 上。
  - 远程收集器可以安装在单独的 VM 上。
  - 小型部署 - 最多 100 个资产，包含 7 到 30 天的索引。
-	部分分布式 - 自动部署完成后，可以通过在初始 VM 中增加 RAM 和磁盘，并添加三个横向扩展 VM 来手动横向扩展。
  - UI、应用程序、插件、中央收集器、远程收集器、索引数据存储、消息传递数据存储和关系数据存储部署在 1 个 VM 上。
  - 远程收集器安装在单独的 VM 上。
  -	索引数据节点部署在单独的 VM 上。
  -	小型到中型部署 - 最多 500 个资产，包含 30 天的索引。
- 完全分布式 - 根据资产数和数据保留需求，添加更多基本 VM 和横向扩展 VM：
  - 应用程序组件分布到不同的 VM 以方便缩放。
  -	随着资产数量增加（范围为 500 - 100,000），需要部署模式。
  -	远程收集器安装在单独的 VM 上。
  -	UI 安装在多个 VM 上。
  -	应用程序和插件安装在多个 VM 上。
  -	中央收集器在集群中进行配置。
  -	关系数据存储部署在主/辅助模型中。
  -	消息传递数据存储部署在集群中。
  -	索引数据存储部署在主节点和数据节点中。
  -	随着资产数量增加，增加用于横向扩展的数据节点。

在任何 VM 部署之前，所有组件都必须具有 FQDN 并已在 DNS 中注册。此步骤由 IBM Cloud for VMware Solutions 自动化针对初始“一体化”部署执行，但在缩放部署时是您的责任。

## 相关链接
{: #caveonix-step1-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
