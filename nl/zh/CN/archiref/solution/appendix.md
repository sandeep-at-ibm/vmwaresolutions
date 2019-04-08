---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# VMware 组件版本的比较图表
{: #solution-appendix}

## VMware NSX 版本比较
{: #solution-appendix-nsx-editions}

在此设计中，有多个组件需要许可证。以下信息说明了环境正常运行所需的最低许可证。

表 1. 许可证需求

组件|用途|许可证
----------|---------|-------------
**vSphere**|计算虚拟化|vSphere 6.7 Enterprise Plus
**vCenter Server**
   |基础架构管理|vCenter Server 6.7 Standard
**NSX**|网络虚拟化|NSX Base for Service Providers 6.4
**vSAN**|存储虚拟化|vSAN 6.6 Advanced

NSX Base for Service Providers 版本仅可通过 VMware vCloud Air Network (vCAN) 供服务提供者使用。此版本中的功能可以在下表中找到。
{:note}

表 2. VMware NSX 版本比较图表

|NSX 功能| Base | Advanced | Enterprise |
|-----------------------------------------------|------|----------|------------|
|分布式交换和路由| •    | •        | •          |
|NSX Edge 防火墙| •    | •        | •          |
|NAT| •    | •        | •          |
|NSX Edge 负载均衡| •    | •        | •          |
|VPN (IPsec)| •    | •        | •          |
|VPN (SSL)| •    | •        | •          |
|API 驱动的自动化| •    | •        | •          |
|与 vRealize 和 OpenStack 集成\*| •    | •        | •          |
|使用 vRealize 自动执行安全策略|      | •        | •          |
|通过 SW L2 桥接到物理环境|      | •        | •          |
|使用 ECMP 进行动态路由（主动/主动）|      | •        | •          |
|分布式防火墙|      | •        | •          |
|与 Active Directory 集成|      | •        | •          |
|服务器活动监视|      | •        | •          |
|服务插入（第三方集成）|      | •        | •          |
|分布式负载均衡|      |          | •          |
|跨 vCenter NSX|      |          | •          |
|多站点 NSX 优化|      |          | •          |
|远程网关|      |          | •          |
|与硬件 VTEP 集成|      |          | •          |
\*仅限 L2、L3 和 NSX Edge 集成。不使用安全组

## VMware vSAN 版本比较
{: #solution-appendix-vsan-editions}

下表列出了解决方案支持的 VMware vSAN 的 **Advanced** 和 **Enterprise** 版本的可用功能。

表 3. VMware vSAN 版本比较图表

|vSAN 功能| Advanced | Enterprise |
|-------------------------------------------------|----------|------------|
|基于存储策略的管理| •        | •          |
|读/写闪存| •        | •          |
|分布式 RAID| •        | •          |
|虚拟分布式交换机| •        | •          |
|机架感知| •        | •          |
|vSphere 复制| •        | •          |
|软件校验和| •        | •          |
|全闪存硬件| •        | •          |
|iSCSI 目标服务| •        | •          |
|IOPS 限制| •        | •          |
|去重和压缩| •        | •          |
|RAID-5/6 擦除编码| •        | •          |
|静态数据加密|          | •          |
|具有本地故障保护功能的延伸集群|          | •          |

## 相关链接
{: #solution-appendix-related}

* [解决方案概述](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [设计概述](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [备份组件](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
