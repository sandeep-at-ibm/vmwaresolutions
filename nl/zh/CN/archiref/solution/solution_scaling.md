---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 缩放容量

初始部署后，您可以从 {{site.data.keyword.vmwaresolutions_full}} 控制台扩展计算容量。本设计支持以下扩展方法：
* 添加由单独 vCenter Server 管理的新站点
* 添加新集群
* 向现有集群添加新主机

## 添加更多站点

{{site.data.keyword.vmwaresolutions_short}} 可以利用 {{site.data.keyword.cloud_notm}} 遍布全球的数据中心和集成网络主干，支持部署并运行各种跨地理位置的用例，所用时间只是从头开始构建此类基础架构所需时间的零头。

在此设计中，多站点部署的定义由以下各项组成：
* 初始或主 VMware 部署，包含要提供的新 DNS/AD 根域、子域、SSO 域和 SSO 站点名称。
* 供应到主站点 SSO 域中的单个或多个辅助站点，需要以下配置：
   * 新的 SSO 站点名称
   * 绑定到主域根目录的新 DNS 站点/子域
   * 辅助站点与主站点 AD VM 之间的 DNS 和 AD 复制设置
   * PSC 已部署并配置为与主站点 PSC 同步
   * 在“增强链接方式”下将 vCenter 设置为主站点 vCenter

此外，可以将辅助站点中的 NSX Manager 设置为主站点上 NSX Manager 的辅助 NSX Manager。

## 添加新集群

您还可以使用此方法来扩展计算容量：在 {{site.data.keyword.vmwaresolutions_short}} 控制台中创建新集群，并订购自动添加到新集群的新主机。

此方法支持您实现以下目标：
* 在环境中创建另一个单独的集群。
* 在物理和逻辑上将管理工作负载与应用程序工作负载相隔离。
* 根据其他特征（例如，Microsoft SQL 数据库集群）来隔离工作负载。
* 在高可用性拓扑中部署应用程序。

初始集群转换为仅管理集群时，现有工作负载的迁移将涉及要由用户执行的手动步骤。这可能涉及将数据存储器重新连接到新集群或轮流迁移存储器。如果新集群位于不同的 {{site.data.keyword.cloud_notm}} pod 中或分配有其他 VLAN 标识，那么可能需要更改工作负载的 IP 地址。
{:note}

## 将 ESXi 主机添加到现有集群

可以通过在 {{site.data.keyword.vmwaresolutions_short}} 控制台中订购主机来扩展现有集群。新主机会自动添加到该集群。请注意，您可能需要根据预留需求来调整集群的 HA 预留策略。

### 相关链接

* [解决方案概述](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
* [设计概述](/docs/services/vmwaresolutions/archiref/solution/design_overview.html)
* [备份组件](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html)
