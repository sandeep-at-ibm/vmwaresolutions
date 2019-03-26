---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud 概述
{: #addingzertodr}

Zerto on {{site.data.keyword.cloud}} 服务用于将复制和灾难恢复功能集成到部署产品中，以保护和恢复 {{site.data.keyword.cloud_notm}} 上 VMware 虚拟环境中的数据。

此服务仅可用于在 V1.2 或更高版本中部署的实例。安装的当前 Zerto 版本为 6.5 Update 3。
{:note}

## Zerto on IBM Cloud 技术规范
{: #addingzertodr-specs}

Zerto on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件。

Zerto Virtual Replication Appliance (VRA) 组件将仅部署到缺省集群中。
{:note}

### VSI
{: #addingzertodr-specs-vsi}

* 一个虚拟服务实例 (VSI) - Zerto Virtual Manager
* 2 个 2.0 GHz 核心
* 4 GB RAM
* Windows Server 2016 Standard Edition（64 位）

### 存储
{: #addingzertodr-specs-storage}

100 GB (SAN) 磁盘

### 联网
{: #addingzertodr-specs-network}

* 一个主专用 IP 地址
* 1 Gbps 专用网络上行链路

### 许可证和费用
{: #addingzertodr-specs-licenses}

Zerto Replication V6.5 update 3 许可证

## 相关链接
{: #addingzertodr-related}

* [关于 {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-prod_overview)
* [订购 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [管理 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [请求 Zerto on {{site.data.keyword.cloud_notm}} 的受管服务](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com Web 站点](https://www.zerto.com){:new_window}
* [Zerto 技术文档](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
