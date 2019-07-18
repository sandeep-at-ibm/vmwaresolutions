---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: Veeam, Veeam install, tech specs Veeam

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud 概述
{: #veeam_considerations}

Veeam on {{site.data.keyword.cloud}} 服务可与 VMware 系统管理程序无缝集成，以帮助企业实现高可用性。此服务可为应用程序和数据提供恢复点和时间目标。在完成配置后的 15 分钟内就会提供恢复点和时间目标。通过使用此服务，您可在 Veeam 控制台中直接控制基础架构的所有虚拟机 (VM) 的备份和复原。

此服务仅可用于在 V1.8 或更高版本中部署的实例。当前安装的 Veeam 版本为 9.5u4。
{:note}

## Veeam on IBM Cloud 的技术规范
{: #veeam_considerations-specs}

Veeam on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### VSI
{: #veeam_considerations-specs-vsi}

* 一个 VSI，带 Veeam Backup and Replication 9.5 操作系统附加组件和 Veeam Availability Suite 9.5
* Windows Server 2016 Standard Edition（64 位）
* 4 个 2.0 GHz 核心
* 8 个 vCPU，32 GB RAM
* 1 Gbps 专用网络上行链路
* 100 GB 磁盘 (SAN)

### 用于备份的存储器
{: #veeam_considerations-specs-storage}

* 耐久性 iSCSI 存储器（2,000、4,000、8,000 或 12,000 GB）
* 存储器性能（0.25、2 或 4 IOPS/GB）

作为 Veeam 服务安装和配置的一部分，将创建以下存储库：
* 对于 Veeam 配置备份文件：名为 `IC4V 缺省配置备份存储库`的存储库。存储 Veeam 备份的文件夹的路径为 `<Drive>:\ConfigBackup\`。
* 对于横向扩展：名为 `IC4V 横向扩展存储库`的存储库。有关更多信息，请参阅[添加横向扩展存储库](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icos_ordering#icos_ordering-scale-repo)。
* 对于虚拟机 (VM) 备份：名为 ``IC4V 缺省 VM 备份存储库``的存储库。存储 VM 备份的文件夹的路径为 ``<Drive>:\VMBackup\`。此存储库作为扩展数据块添加到 ``IC4V 横向扩展存储库`。

### 联网
{: #veeam_considerations-specs-networking}

一个主专用 IP 地址。

### 许可证和费用
{: #veeam_considerations-specs-licenses}

* Veeam Availability Suite 9.5（10、25、50、100 或 200 VM 许可证）

## 安装 Veeam on IBM Cloud 时的注意事项
{: #veeam_considerations-install}

用于存储的存储库和 Veeam 服务器位于原始 pod 和数据中心内。因此，远程集群的备份操作性能可能会下降。

## 除去 Veeam on IBM Cloud 时的注意事项
{: #veeam_considerations-remove}

除去 Veeam on {{site.data.keyword.cloud_notm}} 服务将停止所有备份并删除所有先前的备份。管理 VM 的备份将停止，并且删除先前备份的操作不可撤销。如果管理 VM 损坏，将无法对其进行复原。

## 相关链接
{: #veeam_considerations-related}

* [订购 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Veeam on {{site.data.keyword.cloud_notm}} 的受管服务](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam Web 站点](https://www.veeam.com/){:external}
* [Veeam 帮助中心](https://www.veeam.com/documentation-guides-datasheets.html){:external}
