---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-17"

---

# 存储设置

此设计支持通过 NFS v3 和 NFS v4.1 的共享存储器连接（不支持 NFS v4）。在订购 VMware vCenter Server on {{site.data.keyword.cloud}} 后，确定要用于环境的 NFS 版本。

虽然 NFS v4.1 通过负载均衡和多路径引入更优秀的性能和可用性，但其不会限制利用 vSphere 功能，包括 Storage DRS、Storage I/O Control 和使用Site Recovery Manager。

下表列出在使用 vSphere 6.0 时针对 vSphere 功能的 NFS 协议和支持。

表 1. NFS 协议和 vSphere 功能

| vSphere 功能| NFS v3 | NFS v4.1 |
|:--------------- |:------ |:-------- |
|vMotion 和 Storage vMotion|是|是|
|高可用性 (HA)|是|是|
|容错 (FT)|是|是|
|分布式资源调度程序 (DRS)|是|是|
|主机概要文件|是|是|
|Storage DRS|是|否|
|Storage I/O Control (SIOC) |是|否|
|Site Recovery Manager |是|否|
|虚拟卷|是|否|

**注**：此设计的所有连接的存储器限于与 vCenter Server 解决方案相同的 {{site.data.keyword.CloudDataCent_notm}} 中提供的 {{site.data.keyword.cloud_notm}} 存储器。此外，使用相同的 NFS 版本在所有主机上安装 NFS v3 和 4.1 数据存储，并且缺省情况下自动精简存储到数据存储的所有虚拟磁盘。

## 将 NFS v3 用于连接的存储器

在选择 NFS v3 作为首选方法以连接 NFS 共享时，体系结构为使用来自 {{site.data.keyword.cloud_notm}} 存储器的单个 IP 地址以连接到共享。此外，NFS 共享连接到 vCenter Server 集群中的所有主机，并放置在启用 Storage DRS 的数据存储集群中。

### vSphere 存储器分布式资源调度程序 (Storage DRS)

Storage DRS 允许管理数据存储集群的聚集资源。在启用 Storage DRS 时，其针对虚拟机 (VM) 磁盘放置和迁移提供建议以均衡数据存储集群中数据存储上的空间的 I/O资源。

在开启 Storage DRS 时，以下功能适用：
* 数据存储集群中数据集存储之间的空间负载均衡
* 数据存储集群中数据集存储之间的 I/O 负载均衡
* 基于空间和 I/O 工作负载的虚拟磁盘的初始位置。

在此设计中，启用 Storage DRS 并且自动化级别设置为“完全自动化”。因此，不会自动迁移文件以优化数据集群上的资源使用情况。请注意，所有其他 Storage DRS 选项设置为“使用集群设置”，因为集群完全自动化。

### NFS v3 的 Storage DRS 运行时设置

通过指定使用的空间阈值和 I/O 等待时间，确定 Storage DRS 的积极性。Storage DRS 收集数据存储集群中数据存储的使用情况信息。vCenter Server 使用此信息以针对数据存储上虚拟磁盘的放置生成建议。

在针对数据存储集群设置低积极性级别时，Storage DRS 建议仅在必要时进行 Storage vMotion 迁移，例如，如果 I/O 负载、空间利用率或其不平衡度过高。在针对数据存储集群设置高积极性级别时，Storage DRS 建议一旦数据存储集群可从空间或 I/O 负载均衡获益即进行迁移。

以下阈值类别适用于数据存储集群：

* 空间利用率：在数据存储上的空间利用率百分比高于在 vSphere Web Client 中设置的阈值时，Storage DRS 生成建议或执行迁移。
* I/O 等待时间：一天内数据存储上度量的 90% 的 I/O 等待时间高于阈值时，Storage DRS 生成建议或执行迁移。

在此设计中，启用 Storage DRS“运行时设置”并且阈值保留为各自的缺省值。强烈建议根据工作负载 I/O 需求和等待时间敏感度更改这些值。

下表显示 VMware vSphere Web Client 中的设置。

表 2. Storage DRS 运行时设置

|设置|值|
|:--------------- |:------ |
|针对 SDRS 建议启用 I/O 度量|已选
|
|已用空间|已选，设置为 80% |
| I/O 等待时间阈值|15 毫秒|

有关在 vSphere Web Client 中配置这些设置的更多信息，请参阅[在 vSphere Web Client 中设置 Storage DRS 运行时规则](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html)。

### Storage I/O Control for NFS v3

在环境中启用 SIOC 时，其针对单个 VM 更改设备队列长度。对设备队列长度的更改会使所有 VM 的存储阵列队列的份额和调速减少到与存储器队列的相同。仅当资源受到约束且存储器 I/O 等待时间超过定义的阈值时，SIOC 才会起作用。

为了使 SIOC 能够确定存储设备何时拥堵或受到约束，SIOC 需要有定义的阈值。对于不同的存储类型，拥堵阈值等待时间不同。此设计建议并实施 10 毫秒阈值等待时间。

您还可以限制各个 VM 的单个虚拟盘，或者向其授予针对 SIOC 的不同份额。通过限制磁盘和授予不同份额，可以将环境与具有所获取的文件存储卷 IOPS 数的工作负载相匹配。此限制由 IOPS 设置，并且可以设置其他权重或“份额”。

份额设置为“高”（2,000 个份额）的虚拟盘收到的 I/O 是设置为“正常”（1,000 个份额）的磁盘的 2 倍，是设置为“低”（500 个份额）的磁盘的 4 倍。“正常”是所有 VM 的缺省值，因此需要针对需要其的 VM 调整为高于或低于“正常”的值。

### NFS v3 的更多存储器

当由于空间不足或高等待时间而需要向环境添加更多存储器时，可通过控制台订购其他 NFS 共享。在订购共享后，自动将导出连接到集群中的 vSphere ESXi 主机，并将其放置在先前提及的存储器集群上。将新的 NFS 共享放置在存储集群中可有效且无缝地扩展与环境相关联的存储器，而不会使负担存储器级别迁移。

## 将 NFV v4.1 用于连接的存储器

在选择 NFS v4.1 作为首选方法以连接 NFS 共享时，体系结构为使用来自 {{site.data.keyword.cloud_notm}} 存储器的多个 IP 地址以连接到共享。在将共享连接到 vCenter Server 集群中的所有主机时，由于将 Storage DRS 与 NFS v4.1 一起使用的 vSphere 限制，不会将其放置在数据存储集群中。

**注**：使用 vSphere 6.0 的 NFS 4.1 不支持硬件加速。此限制不允许在 NFS v4.1 数据存储上创建厚虚拟盘。

### NFV v4.1 的更多存储器

当由于空间不足或高等待时间而需要向环境添加更多存储器时，可通过控制台订购其他 NFS 共享。在订购共享后，自动将导出连接到集群中的 vSphere ESXi 主机。然后，必须迁移 VM 并对数据存储进行负载均衡，从而正确地使用空间并且满足等待时间需求。

## 高级配置参数

无论是选择 NFS v3 还是 NFS v4.1，此设计都会添加 {{site.data.keyword.cloud_notm}} 建议的高级配置参数。因此，在连接到 {{site.data.keyword.cloud_notm}} NFS 共享的每个 vSphere ESXi 主机上设置以下参数。

表 3. NFS 高级配置参数

|参数|值|
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MazQueueDepth | 64 |

### 相关链接

* [解决方案概述](../solution/solution_overview.html)
