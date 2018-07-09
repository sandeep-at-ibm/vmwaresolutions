---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# HyTrust DataControl on IBM Cloud 概述

HyTrust DataControl on {{site.data.keyword.cloud}} 服务通过集成密钥管理提供高强度加密功能，以确保工作负载在整个生命周期中的安全。此服务可以提供操作系统级别和数据级别的加密，这意味着可以对工作负载中的任何目录、文件夹或文件进行加密和解密。

**可用性**：此服务仅可用于运行 vSphere 6.5 以及部署在（或升级到）V2.3 或更高发行版的实例。

## HyTrust DataControl on IBM Cloud 的组件

HyTrust DataControl (HTDC) 设备的高可用性 (HA) 对会以主动/主动方式部署在缺省集群上。HTDC 设备已获得许可，可为工作负载提供 HyTrust KeyControl 功能。

每对 HTDC 设备都会部署在为管理虚拟机 (VM)（例如 NSX Manager、vCenter Server Appliance 和 Platform Services Controller）指定的相同可移植子网上。这些设备通过 {{site.data.keyword.cloud_notm}} 后端客户路由器 (BCR) 进行路由，并分配有与管理 VM 子网关联的网关。此外，设备会放置在缺省集群的缺省存储器上。

## 除去 HyTrust DataControl on IBM Cloud 时的注意事项

除去 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服务之前，请确保已对 DataControl 中的所有磁盘进行加密或备份。除去该服务后，可能会删除密钥，并且可能会锁定 VM。

## 相关链接

* [订购 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [管理 HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [HyTrust Web 站点](https://www.hytrust.com/)
