---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust CloudControl on IBM Cloud 概述

HyTrust CloudControl on {{site.data.keyword.cloud}} 服务根据安全标准强制实施和控制合规性，并提供详细的基于角色的访问控制 (RBAC)、核准和审计功能。与 HyTrust DataControl 组合使用时，该服务可确保虚拟机和工作负载数据不会离开 {{site.data.keyword.CloudDataCent_notm}} 内的特定区域、集群或 ESXi 服务器。

**可用性**：此服务仅可用于运行 vSphere 6.5 以及部署在（或升级到）V2.3 或更高发行版的实例。

## HyTrust CloudControl on IBM Cloud 的技术规范

HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### HyTrust CloudControl 设备

* CPU：4 个 vCPU
* RAM：16 GB
* 磁盘：在融合集群中的 vSAN 上常驻 70 GB VMDK
* 网络：位于为管理指定的支持 VLAN 的专用可移植网络上

### 高可用性

两个 CloudControl 设备以主动/被动配置方式进行部署。

### 许可证和费用

按主机订购许可证：为环境中的每个主机订购了一个 HyTrust CloudControl 许可证。

## 除去 HHyTrust CloudControl on IBM Cloud 时的注意事项

除去 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服务之前，请确保禁用 **root 用户密码保险库**（如果已配置），并且从 HyTrust CloudControl 中删除所有受保护的主机。

### 相关链接

* [订购 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [管理 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [HyTrust Web 站点](https://www.hytrust.com/)
