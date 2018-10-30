---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# HyTrust KeyControl on IBM Cloud 概述

HyTrust KeyControl on {{site.data.keyword.cloud}} 服务简化了已加密工作负载的管理工作。此服务自动化和简化加密密钥的生命周期，包括密钥存储、密钥分发、密钥轮换和密钥撤销。企业使用符合 FIPS 140-2 的加密，可轻松管理大批加密密钥。 

**可用性**：此服务仅可用于运行 vSphere 6.5 以及部署在（或升级到）V2.5 和更高发行版的实例。

## HyTrust KeyControl on IBM Cloud 的技术规范

HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### HyTrust KeyControl 设备

* CPU：2 个 vCPU
* RAM：8 GB
* 磁盘：在融合集群中的 vSAN 上常驻 20 GB VMDK
* 网络：位于为管理指定的支持 VLAN 的专用可移植网络上

### 高可用性

缺省情况下，两个 KeyControl 设备以主动/主动集群配置方式进行部署。

（可选）可以指定以独立非集群配置来部署两个 KeyControl 设备。

### 许可证和费用

对于每个实例安装，将分别订购一个 HyTrust KeyControl 许可证。

## 除去 HyTrust KeyControl on IBM Cloud 时的注意事项

除去 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服务之前，请确保使用 KeyControl 对所有客户机解耦。除去该服务后，可能会删除密钥，并且可能会将您锁定在 VM 之外。

### 相关链接

* [订购 HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](htkc_ordering.html)
* [管理 HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](managinghtkc.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [HyTrust Web 站点](https://www.hytrust.com/)
