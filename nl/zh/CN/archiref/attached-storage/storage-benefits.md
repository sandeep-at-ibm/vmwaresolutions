---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# 关于 vCenter Server 的连接存储器

连接的存储器是 VMware vCenter Server on {{site.data.keyword.cloud}} 产品的扩展。VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的连接存储器解决方案体系结构详细说明了设计中解决方案的组件以及每个组件的高级配置。

有关 vCenter Server 设计的更多信息，请参阅[解决方案概述](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)。

## vCenter Server 的连接存储器的主要优点

虽然连接的存储器并不是 VMware 环境的必备设备，但将其用作共享存储设备可为用户进行 IT 操作提供许多好处。使用共享存储设备后，您可以通过启用下表中描述的 vSphere 功能，实现高可用性、启用分布式资源调度程序、高效利用存储容量以及简化管理。

表 1. vCenter Server 的连接存储器的功能描述

|功能|描述|
|:------- |:----------- |
|vSphere 分布式资源调度程序和资源池|使用此功能，可以通过配置负载均衡和虚拟机 (VM) 对资源进行灵活的抽象化管理。资源池可按层次结构分组，并且可用于按层次结构分配可用 CPU 和内存资源。|
|vSphere 高可用性|此功能可通过汇聚 VM 来为 VM 提供 HA，还可为集群中的主机提供 HA。系统会监视集群中的主机。如果发生故障，即会在备用主机上重新启动发生故障的主机上的 VM。|
|vSphere 数据存储集群|此功能提供一个数据存储集合，这些存储具有共享的资源和共享的管理界面。|
|vSphere 容错|此功能通过消除停机时间和中断来提供持续的 VM 可用性，即使主机完全故障，也是如此。|

### 相关链接

* [解决方案概述](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
