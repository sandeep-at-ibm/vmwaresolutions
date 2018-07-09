---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# HyTrust CloudControl on IBM Cloud 概述

HyTrust CloudControl on {{site.data.keyword.cloud}} 服务根据安全标准强制实施和控制合规性，并提供详细的基于角色的访问控制 (RBAC)、核准和审计功能。与 HyTrust DataControl 组合使用时，该服务可确保虚拟机和工作负载数据不会离开 {{site.data.keyword.CloudDataCent_notm}} 内的特定区域、集群或 ESXi 服务器。

**可用性**：此服务仅可用于运行 vSphere 6.5 以及部署在（或升级到）V2.3 或更高发行版的实例。

## HyTrust CloudControl on IBM Cloud 的组件

HyTrust CloudControl (HTCC) 设备的高可用性 (HA) 对会以主动/被动方式部署在缺省集群上。

每对 HTCC 设备都会部署在为管理虚拟机 (VM) 指定的相同的专用可移植子网上，例如 NSX Manager、vCenter Server Appliance 和 Platform Services Controller。

该对设备充当 vSphere 主机、vCenter Server Appliance 和实例的 NSX Manager 的代理。因此，用户将通过由管理员分配的已发布 IP (PIP) 地址（而不是由 {{site.data.keyword.cloud}} 分配的实际 IP 地址 (RIP)）来访问 vSphere 主机、vCenter Server Appliance 和 NSX Manager。

HTCC 设备与 Microsoft Active Directory 集成，以强制实施基于角色的访问控制。

## 除去 HHyTrust CloudControl on IBM Cloud 时的注意事项

除去 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服务之前，请确保禁用 **root 用户密码保险库**（如果已配置），并且从 HyTrust CloudControl 中删除所有受保护的主机。

## 相关链接

* [订购 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [管理 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [HyTrust Web 站点](https://www.hytrust.com/)
