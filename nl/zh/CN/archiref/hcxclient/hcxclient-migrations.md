---

copyright:

  years:  2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# VMware 混合云迁移
{: #hcxclient-migrations}

供应并扩展 HCX 服务网和网络扩展后，下一步是迁移 VM。

有三种迁移类型：
  - vMotion
  - 批量迁移
  - 冷迁移

## 操作
{: #hcxclient-migrations-operation}

使用 HCX Web UI 插入式门户网站或 vSphere Web Client 上下文扩展菜单来启动跨云 vMotion。无论使用哪种方法，都会显示相同的迁移向导。对于上下文菜单，仅选择单个 VM 进行迁移操作。对于门户网站，可以选择多个 VM。

逆向迁移 VM 只能在 Web UI 门户网站中执行，方法是选中“HCX 迁移”向导中的**逆向迁移**复选框。

## vMotion
{: #hcxclient-migrations-vmotion}

HCX 中的 vMotion 功能扩展了 vSphere vMotion 功能，适用于不同版本的 vSphere、单独的 SSO 域以及因特网中各种类型的网络连接。HCX 假定用于连接的网络不安全，因此始终通过加密隧道来移动流量，而不管连接类型如何。

### vMotion 的概念和最佳实践
{: #hcxclient-migrations-best-practices-vmotion}

HCX 本质上是一个 vMotion 双向代理。每个 HCX 实例都会在任何集群外部模拟 vSphere 数据中心内的一个 ESXi 主机，该主机本身是云网关系列组件 (CGW) 的“前端”。对于链接到当前所查看站点的每个 HCX 站点，会显示代理主机。vMotion 启动到远程主机时，本地 ESXi 主机会通过 vMotion 将该 VM 移至作为 CGW 前端的本地代理 ESXi 主机，该主机还维护与远程端 CGW 的加密隧道。

同时，vMotion 在通过该隧道收到来自源 CGW 的数据时，会启动从远程 ESXi 代理主机到目标 vSphere 物理 ESXi 主机的 vMotion 迁移。应用 vMotion 时，一次只能运行一个 VM 迁移操作，这与批量迁移选项不同。因此，对于要迁移大量 VM 的情况，建议仅在不允许停机时或在重新引导 VM 有风险时，才使用 vMotion。但是，与标准 vMotion 一样，VM 在此过程中可以保持活动状态。

据观察，在 LAN 上，单个 vMotion 在约 1.7 Gbps 的速度时会达到极限，如果在 WAN 上通过 WAN Optimizer，那么在 300 到 400 Mbps 时达到极限。这并不意味着 LAN 上的 1.7 Gbps 等于 WAN 上通过 WAN Optimizer
的 400 Mbps，而只是说明在特定环境上观察到这些最大值。此类环境由 10 GB LAN vMotion 网络和 1 GB 因特网上行链路（与生产 Web 流量共享）组成。

对于以下情况，请使用 vMotion：
- VM 关闭或启动有问题，或者关闭 VM 时正常运行时间可能很长而引入风险。
- 任何需要磁盘 UUID 的集群类型应用程序，如 Oracle RAC 集群。请注意，vMotion 不会更改目标上的磁盘 UUID。
- 您希望尽快移动单个 VM。
- 不需要安排的迁移。

## 批量迁移
{: #hcxclient-migrations-bulk-mig}

### 批量迁移的概念和最佳实践
{: #hcxclient-migrations-best-practices-bulk-mig}

HCX 的批量迁移功能使用 vSphere 复制来迁移磁盘数据，同时在目标 vSphere HCX 实例上重新创建 VM。迁移 VM 会执行以下工作流程：
- 在目标端及其相应虚拟盘上创建新 VM。
- 将 VM 数据复制到新 VM。复制将在向导完成后立即启动，而不考虑切换到安排。
- 关闭原始 VM 的电源。
- 在关闭电源期间，会执行对任何数据变更的最终复制。
- 在目标端打开新 VM 的电源。
- 重命名原始 VM 并将其移至所移动到的云文件夹。

下面是通过 vMotion 进行批量迁移的优点：
- 同时迁移多个 VM。
- 带宽使用量更一致。vMotion 会导致带宽使用量波动，这在网络监视工具或 WAN Opt UI 中可显示为峰值和谷值。
- 使用批量迁移能使网络带宽能力的总体使用率高于单个 vMotion 所能实现的值。
- 安排批量迁移可在安排的中断时段内切换到新迁移的 VM。
- 允许迁移当前使用虚拟 CPU 功能（不同于云端）的 VM。在这些情况下，vMotion 迁移可能失败。

下面是批量迁移相对于 vMotion 的缺点：
- 单个 VM 迁移速度比使用 vMotion 慢得多。
- 在目标端启动新的克隆 VM 时，VM 会发生短时间停机情况。
- 依赖于磁盘订购和磁盘 UUID (Oracle RAC) 的 VM 可能存在问题，并且其磁盘因为 UUID 发生更改而产生不同，这可能会更改虚拟盘设备的操作系统路径。

## 迁移类型最佳实践
{: #hcxclient-migrations-mig-type-best-practices}

### 共享磁盘集群
{: #hcxclient-migrations-shared-disk-clusters}

Oracle RAC、MS Exchange 和 MS-SQL 集群是其中有两个或多个 VM 参与需要跨所有 VM 或集群节点共享磁盘的集群的应用程序示例。对于属于应用程序集群的磁盘（非操作系统虚拟盘），其所有 VM 节点上都需要启用 VMware 多写程序标志。对于任何虚拟盘，不支持启用了多写程序标志的 VM。

迁移启用了多写程序虚拟盘的集群：
- 使用 vMotion 作为原始 VM 磁盘并保留 UUID 映射。
- 迁移期间，集群会以降级状态（单节点）保持运行。
- 迁移开始之前和迁移完成之后，集群会产生停机时间，以便跨集群 VM 重新组合多写程序配置。

要迁移启用了多写程序磁盘的集群，请完成以下步骤：
1. 按照应用程序最佳实践关闭集群和所有节点的电源。
2. 在配置了多写程序的虚拟盘的每个节点 VM 中，记下磁盘顺序（如果应用程序需要）。
3. 对于 Oracle 和其他任何使用虚拟盘 UUID 功能的应用程序，请登录到特定 ESXi 主机，然后运行 `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` 命令以获取每个虚拟盘文件的 UUID，该文件要求为集群设置多写程序标志。如果最佳实践是使磁盘顺序与路径在操作系统中的显示方式保持一致，那么此操作是必需的。vMotion 可以对磁盘重新排序 (disk1, disk2, disk3)，但 UUID 保持不变。迁移完成后，请使用所记录的 UUID 来映射磁盘信息，重新创建磁盘命名顺序以及 SCSI 标识（如果需要）。应用程序应该以任一方式运行。这适用于 Oracle 实例具有多个虚拟盘，并已映射这些虚拟盘以便对应用程序进行故障诊断的情况。
4. 从除了主节点之外的其他所有集群 VM 中除去虚拟盘。
5. 从主集群 VM （应该是当前唯一拥有集群磁盘的节点）中除去多写程序标志。
6. 根据需要开启主集群的电源，以最大限度缩短停机时间。
7. 使用 vMotion 迁移所有集群节点。首先迁移主集群。所有其他节点在关闭电源后进行迁移。
8. 拥有主磁盘的节点完成迁移时，请关闭其电源。
9. 如果需要，请使用正确的磁盘 UUID 和 SCSI 标识来重新映射磁盘顺序。无需重新映射，应用程序即可正常运行。
10. 在主节点上重新启用多写程序标志。
11. 启动主节点并验证运行情况。
12. 在其他所有集群 VM 上映射磁盘/启用多写程序标志，然后打开这些 VM 的电源。
13. 验证其他集群运行情况。

### 常规 VM
{: #hcxclient-migrations-general-vms}

在对 HCX 的功能建立信心后，必须应用批量迁移。对于冗余应用程序，有必要执行批量迁移。例如，Web 服务器以及要将成百上千个 VM 迁移到的位置。

### 使用直接连接 NAS 的 VM
{: #hcxclient-migrations-vms-direct-nas}

NFS 通常用于在许多服务器之间共享数据，例如 Web 服务器内容。iSCSI 可以在构成应用程序集群（如电子邮件或 RDBMS）的各个 VM 节点上应用，并且对等待时间的敏感性通常高于 NFS。

在任一种情况下，如果到 {{site.data.keyword.CloudDataCent_notm}} 的等待时间可以保持在低水平（对于 iSCSI，小于约 7 毫秒；对于 NFS，为应用程序可以容许的任何值），并且允许应用程序能够以约 1 Gbps 或更低带宽运行，那么 NAS 网络可以通过 HCX 延伸到 {{site.data.keyword.cloud_notm}} 位置。完成此操作后，可以使用 HCX 对 VM 执行迁移/vMotion 操作。

迁移后，可以使用操作系统将 iSCSI 卷镜像到其他本地云存储解决方案，并且可以将 NFS 数据复制到任何云解决方案。注意事项如下：
- 等待时间（iSCSI 的等待时间，或者对于 NFS，为应用程序容许的值）
- 带宽（每个延伸网络约 1 Gbps）
- 下层链路带宽

迁移生命周期结束后，在尝试用于生产之前，测试开发或编译打包应用程序。对于支持等待时间敏感性 L2 延伸网络的 L2C HCX 设备之间的下层隧道流量 (udp 500 / 4500)，可以应用 QoS。

## 网络摆动
{: #hcxclient-migrations-network-swing}

如果目标是将数据中心转移到 {{site.data.keyword.cloud_notm}} 中，那么在除去 HCX 之前要执行的倒数第二步是网络摆动。通过网络摆动，可实现将包含已从源数据中心迁移的 VM 的网络子网迁移到 {{site.data.keyword.cloud_notm}} 中的 NSX 覆盖网络上。

网络摆动涉及以下步骤：
- 验证网络是否已转移完所有工作负载，以及所有非 VM 联网设备是已移至其他网络、功能性迁移到云还是已废弃。
- 验证是否完成了任何 NSX 拓扑或 {{site.data.keyword.cloud_notm}} 支持网络拓扑来支持网络摆动。例如，动态路由协议和防火墙。
- 在 UI 中运行 HCX 取消延伸网络工作流程，并选择相应的路由 NSX 设备来接管取消延伸的网络的缺省网关。
- 运行任何外部路由更改，其中可能包括：为已迁移网络插入更改的路由，除去已迁移网络中源站点的路径，并确保整个 WAN 中已迁移子网的路由仍适用于未迁移的应用程序。
- 应用程序所有者从所有可能的访问点（因特网、内部网和 VPN）对已迁移应用程序进行测试。

假设您希望对已将所有 VM 迁移到云的特定应用程序进行网络摆动。例如：
- 您要在专用网络端使用 Vyatta，以将路径插入到 MPLS 云中，然后通过隧道传输到 MPLS 上的边缘路由设备，以便避免使用 {{site.data.keyword.cloud_notm}} IP 空间。
- 您的帐户已设置为使用 {{site.data.keyword.cloud_notm}} VRF。
- 某些应用程序位于网络负载均衡的虚拟 IP (vIP) 后面。这些 vIP 位于您拥有的子网上，该子网位于 Vyatta 后面的虚拟 F5 上。

对于通过 HCX 摆动到 {{site.data.keyword.cloud_notm}} 的网络，将更具体的路由添加到 MPLS 这种方法虽然对其他网络非常有效，但因为添加了 /32 路径，对于单个 vIP 却不起作用。

解决方案：WAN 提供商通常会过滤掉所添加的 /32 路径。请与 WAN 供应商合作以允许使用这些路径。

下面是注意事项和影响：
- 共享子网、vLAN 和 VXLAN 的应用程序需要一起移动。
- 对于使用内部可路由 IP 的负载均衡器后面的应用程序，如果不能或不宜一起移动，可能需要路由更改。例如，如果在一次摆动中涉及的应用程序太多，那么感知到的风险会太高。
- 需要 VMware 管理员、网络管理员（包括客户和 WAN 供应商）和应用程序所有者的参与，即使规划中对特定系统或网络设备没有影响。

## 相关链接
{: #hcxclient-migrations-related}

* [HCX 组件和术语的词汇表](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [准备安装环境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 客户机部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 内部部署服务网](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [监视参数和组件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
