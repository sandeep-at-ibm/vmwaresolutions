---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# 关于 NSX Edge 服务网关
{: #nsx_overview}

VMware NSX Edge 服务网关 (ESG) 解决方案是目前 {{site.data.keyword.cloud_notm}} 上提供的 VMware Cloud Foundation on {{site.data.keyword.cloud}} 和 vCenter Server on {{site.data.keyword.cloud_notm}} 产品的扩展。Cloud Foundation 和 vCenter Server 的解决方案体系结构详细说明了设计中解决方案的组件以及每个组件的高级别配置。

有关 Cloud Foundation 和 vCenter Server 设计的更多信息，请参阅[解决方案概述](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)。

## NSX Edge 服务网关概述
{: #nsx_overview-nsx-esg}

NSX Edge 服务网关通过提供通用网关服务（例如，动态主机配置协议 (DHCP)、虚拟专用网 (VPN)、网络地址转换 (NAT)、动态路由选择和负载均衡），将已隔离的存根网络与共享（上行链路）网络相连接。NSX Edge 的常见部署包括非保护区 (DMZ)、VPN 外部网和多租户云环境，其中 NSX Edge 为每个租户、工作负载或管理组件创建虚拟边界。NSX Edge 服务网关内提供了以下功能。

表 1. NSX Edge 服务网关的可用功能

|功能|描述|
|:------- |:----------- |
|NSX Edge 服务路由|在第 2 层广播域之间提供必要的信息转发功能，允许您减少第 2 层广播域，提高网络效率和规模。NSX 将此智能功能扩展到工作负载所在位置以执行东-西路由。这允许虚拟机到虚拟机之间进行更直接的通信，而无需耗费成本或时间来扩展中继段。同时，NSX 还提供了南-北连接，支持租户访问公用网络。|
|防火墙|支持的防火墙规则包括使用所有协议的有状态检查的 IP 和端口范围进行 IP 五元组配置。|
|NAT|为源和目标 IP 地址以及端口转换提供单独的控制。|
|DHCP|提供 IP 池、网关、DNS 服务器和搜索域的配置。|
|站点到站点 VPN|使用标准化的 IPSec 协议设置，与所有主要的 VPN 供应商进行互操作。|
|L2VPN|跨 L3 拓扑延伸 L2 网络。|
|SSL VPN-Plus|通过 SSL VPN-Plus，远程用户能够安全地连接到 NSX Edge 网关后面的专用网络。|
|负载均衡|提供简单和动态可配置的虚拟 IP 地址和服务器组。|
|高可用性|确保网络中有活动 NSX Edge，以防主 NSX Edge 虚拟机不可用。|

## 相关链接
{: #nsx_overview-related}

* [解决方案概述](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
