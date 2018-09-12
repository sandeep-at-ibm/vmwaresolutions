---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# 连接的存储器基础架构管理

基础架构管理是指用于管理 vSphere ESXi 基础架构的 VMware 组件。

有关组件的更多信息，请参阅[虚拟基础架构设计](../solution/design_virtualinfrastructure.html)中的“图 2. NSX Manager 网络概述”。

## 虚拟联网设计

在此设计中使用的网络虚拟化使用与专用网络相关联且在 [{{site.data.keyword.vmwaresolutions_full}} 体系结构](../solution/solution_overview.html)中指定的现有 vSphere 分布式交换机 (vDS)。

## vSphere 分布式交换机

如前所述，在 vCenter Server 解决方案中创建另一个 VLAN 并用于将 NFS 安装点连接到现有集群中的 ESXi 主机。因为 vCenter Server 解决方案已将 vSphere 分布式交换机 (vDS) 与专用网络相关联，因此创建另一个端口组并使用附加 VLAN 编号进行标记（因为此附加 VLAN 非本机）。

下表描述新端口组的缺省设置。

**重要信息：**请勿更改这些缺省设置。

表 1. NFS 端口组摘要

|端口组名称| SDDC-DPG-NFS |
|:--------------- |:------------ |
|端口绑定|静态
|
|VLAN 类型|专用 VLAN B |
|负载均衡|基于发起虚拟端口进行路由|
|活动的上行链路| Uplink1 和 uplink2 |

除了针对 NFS 存储流量创建 vDS 端口组，将在部署中的每个 vSphere ESXi 主机上创建一个 VMkernel 端口并分配给 SDDC-DPG-NFS 端口组。还会为 VMkernel 端口分配一个来自与连接的存储器 VLAN 相关联的专用可移植子网的 IP 地址，也就是，专用 VLAN B 及其 MTU 设置为 9000 以支持巨型帧。

图 1. 专用 vDS 端口组和上行链路

![专用 vDS 端口组和上行链路](private_vds_portgroups_and_uplinks.svg "专用 vDS 端口组和上行链路")

### vSphere 主机静态路由选择

虽然使用新端口组配置 vDS 并将 VMkernel 端口分配给端口组，解决方案在部署中的每个 vSphere ESXi 主机上创建一个静态路由，从而使所有 NFS 流量遍历 VLAN 和 NFS 的子网。在 `/etc/rc.local.d/local.sh` 中创建静态路由，因此跨主机重新启动持久存在。

### 相关链接

* [解决方案概述](../solution/solution_overview.html)
