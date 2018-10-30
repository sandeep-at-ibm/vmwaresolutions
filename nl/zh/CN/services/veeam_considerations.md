---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Veeam on IBM Cloud 概述

Veeam on {{site.data.keyword.cloud}} 服务可与 VMware 系统管理程序无缝集成，以帮助企业实现高可用性。此服务可为应用程序和数据提供恢复点和时间目标。在完成配置后的 15 分钟内就会提供恢复点和时间目标。通过使用此服务，您可在 Veeam 控制台中直接控制基础架构的所有虚拟机 (VM) 的备份和复原。

**可用性**：此服务仅可用于在 V1.8 或更高发行版中部署的实例。

## Veeam on IBM Cloud 的技术规范

Veeam on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### VSI

* 一个 VSI，带 Veeam Backup and Replication 9.5 操作系统附加组件
* Windows Server 2016 Standard Edition（64 位）
* 4 个 2.0 GHz 核心
* 8 GB RAM
* 1 Gbps 专用网络上行链路
* 100 GB 磁盘 (SAN)

### 用于备份的存储器

* 耐久性 iSCSI 存储器（2000、4000、8000 或 12000 GB）
* 存储器性能（0.25、2 或 4 IOPS/GB）

### 联网

一个主专用 IP 地址。

### 许可证和费用

Veeam Backup and Replication 9.5 Enterprise Plus（10、25、50、100 或 200 个 VM 许可证）。

### 管理

缺省情况下，配置的管理备份为最多 5 个 VM 和 2000 GB 存储器。

## 安装 Veeam on IBM Cloud 时的注意事项

用于存储的存储库和 Veeam 服务器位于原始 pod 和数据中心内。因此，远程集群的备份操作性能可能会下降。

## 除去 Veeam on IBM Cloud 时的注意事项

除去 Veeam on {{site.data.keyword.cloud_notm}} 服务将停止所有备份并删除所有先前的备份。管理 VM 的备份将停止，并且删除先前备份的操作不可撤销。如果管理 VM 损坏，将无法对其进行复原。

### 相关链接

* [订购 Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [请求 Veeam on {{site.data.keyword.cloud_notm}} 的受管服务](managing_veeam_services.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [Veeam Web 站点](https://www.veeam.com/){:new_window}
* [Veeam 帮助中心](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
