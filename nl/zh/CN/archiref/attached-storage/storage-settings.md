---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 存储设置

此设计支持仅通过 NFS V3 来连接共享存储器。不支持 NFS V4 和 V4.1。

此设计的所有连接存储器仅限于 vCenter Server 解决方案所在的 {{site.data.keyword.CloudDataCent_notm}} 中可用的 {{site.data.keyword.cloud_notm}} 存储器。此外，缺省情况下，存储到数据存储的所有虚拟磁盘均为自动精简配置。
{:note}

体系结构指定使用 DNS 名称将 NFS V3 数据存储从 {{site.data.keyword.cloud_notm}} 存储器连接到共享。此外，还会将 NFS 共享连接到 vCenter Server 集群中的所有主机，并放置在已启用 Storage DRS 的数据存储集群中。

## vSphere 存储器分布式资源调度程序 (Storage DRS)

使用 Storage DRS，可以管理数据存储集群的聚集资源。启用 Storage DRS 后，其会针对虚拟机 (VM) 磁盘放置和迁移提供一些建议，以使数据存储集群中各数据存储上的空间和 I/O 资源均衡。

启用 Storage DRS 时，以下功能可用：
* 数据存储集群中各数据存储之间的空间负载均衡
* 数据存储集群中各数据存储之间的 I/O 负载均衡
* 基于空间和 I/O 工作负载确定虚拟磁盘的初始位置。

在此设计中，Storage DRS 为启用状态，且自动化级别设置为**完全自动化**。因此，会自动迁移文件来优化数据集群上的资源使用情况。因为集群已完全自动化，因此所有其他 Storage DRS 选项均设置为**使用集群设置**。

## NFS v3 的 Storage DRS 运行时设置

Storage DRS 的积极性可通过指定所使用空间和 I/O 等待时间的阈值来进行确定。Storage DRS 会收集数据存储集群中数据存储的资源使用情况信息。vCenter Server 使用此信息来生成有关在数据存储上如何放置虚拟磁盘的建议。

如果为数据存储集群设置了低积极性级别，Storage DRS 仅会在必要时提供有关 Storage vMotion 迁移的建议，例如当 I/O 负载、空间利用率或它们的不平衡度较高的时候。如果为数据存储集群设置了高积极性级别，只要数据存储集群能够从空间或 I/O 负载均衡中获益，Storage DRS 即会提供迁移建议。

以下阈值类别适用于数据存储集群：

* 空间利用率：当数据存储上的空间利用率百分比高于您在 vSphere Web Client 中设置的阈值时，Storage DRS 会生成建议或执行迁移。
* I/O 等待时间：当一天内针对数据存储测量的第 90 个百分位的 I/O 等待时间高于阈值时，Storage DRS 会生成建议或执行迁移。

在此设计中，Storage DRS 运行时设置为启用状态，且阈值均为其各自的缺省值。强烈建议您根据工作负载 I/O 需求和等待时间敏感度来更改这些值。

下表显示了 VMware vSphere Web Client 中的设置。

表 1. Storage DRS 运行时设置

|设置|值|
|:--------------- |:------ |
|启用 I/O 度量以获取 SDRS 建议|已选|
|已利用的空间|已选，设置为 80% |
|I/O 等待时间阈值|15 毫秒|

有关在 vSphere Web Client 中配置这些设置的更多信息，请参阅 [Set Storage DRS Runtime Rules in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html)。

## NFS v3 的 Storage I/O Control

在环境中启用 SIOC (Storage I/O Control) 后，SIOC 会更改单个 VM 的设备队列长度。更改设备队列长度会使所有 VM 的存储阵列队列的份额和调速限制减少到与存储队列的相同。仅当资源受到约束且存储器 I/O 等待时间超过定义的阈值时，SIOC 才会起作用。

SIOC 需要有定义的阈值，才能确定存储设备何时拥堵或受到约束。不同存储类型的拥堵阈值等待时间是不同的。此设计会建议并实施 10 毫秒的阈值等待时间。

您还可以限制各个 VM 的单个虚拟磁盘，或向其授予针对 SIOC 的不同份额。通过限制磁盘和授予不同份额，可以将环境与具有所获取文件存储卷 IOPS 数的工作负载相匹配。此限制由 IOPS 设置，但您可以设置其他权重或份额。

份额设置为**高**（2,000 个份额）的虚拟磁盘收到的 I/O 是设置为**正常**（1,000 个份额）的磁盘的 2 倍，是设置为**低**（500 个份额）的磁盘的 4 倍。**正常**是所有 VM 的缺省值，因此您应当为需要该值的 VM 调整**正常**设置。

## 使用 NFS v3 时的存储器添加

由于空间不足或等待时间较长而需要向环境添加更多存储器时，可以通过控制台订购另一个 NFS 共享。订购该共享后，请将相应的导出连接到集群中的 vSphere ESXi 主机，并将其放置在存储器集群中。将新的 NFS 共享放置在存储器集群中可以有效且无缝地扩展与环境相关联的存储器，而无需进行存储器级别的迁移。

## 高级配置参数

此设计会添加 {{site.data.keyword.cloud_notm}} 建议的高级配置参数。因此，在连接到 {{site.data.keyword.cloud_notm}} NFS 共享的每个 vSphere ESXi 主机上，会设置以下参数。

表 2. NFS 高级配置参数

|参数|值|
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures |10|
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MazQueueDepth | 64 |

### 相关链接

* [解决方案概述](../solution/solution_overview.html)
