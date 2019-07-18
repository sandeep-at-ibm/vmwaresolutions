---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: IBM Spectrum Protect Plus, SPP, tech specs SPP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Spectrum Protect Plus on IBM Cloud 概述
{: #spp_considerations}

{{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务为虚拟环境的数据保护、数据复用和数据恢复提供高效、可扩展的解决方案。可以将此服务作为独立解决方案实施，也可以与 IBM Spectrum Protect 环境集成，以便卸载用于长期存储和数据监管的副本。

此服务仅可用于运行 vSphere 6.5 以及部署在或已升级到 V2.2 或更高版本的实例。当前安装的 {{site.data.keyword.IBM}} Spectrum Protect Plus 版本为 V10.1.3。
{:note}

## IBM Spectrum Protect Plus on IBM Cloud 的技术规范
{: #spp_considerations-specs}

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### vCenter 资源
{: #spp_considerations-vcenter}

* 运行 IBM Spectrum Protect Plus 服务器的服务器 VM
   * Linux 3.10.0-693.11.1.el7.x86_64 操作系统
   * 4 个 2.0 GHz 核心
   * 32 GB RAM
   * 370 GB 磁盘
* 运行 IBM Spectrum Protect Plus vSnap 服务器和 VADP 代理的辅助 VM
   * Linux 3.10.0-693.11.1.el7.x86_64 操作系统
   * 根据所选存储器大小和 [IBM Spectrum Protect Plus 蓝图](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints){:external}中的大小调整指南而配置的 CPU 和 RAM
   * 150 GB 磁盘

### 用于备份的存储器
{: #spp_considerations-backup-storage}

用于备份的可定制存储器具有以下选项：
* 文件存储器数：1 - 10 个
* 每个耐久性文件存储器：500、1000、2000、4000、8000 或 12000 GB
* 存储器性能：0.25、2 或 4 IOPS/GB

请参阅 [IBM Spectrum Protect Plus 蓝图和大小调整工具](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints){:external}以进行规划和大小调整。

### 用于管理的存储器
{: #spp_considerations-mgmt-storage}

一个 1000 GB、2 IOPS/GB 耐久性文件存储器，用于托管 IBM Spectrum Protect Plus 虚拟机并在备份存储器所在的子网上运行。

### 联网
{: #spp_considerations-network}

两个可移植专用 IP 地址。

### 许可证和费用
{: #spp_considerations-license}

* IBM Spectrum Protect Plus（10 个到最多 1000 个 VM 许可证，以 10 为单位递增）
* 通过 {{site.data.keyword.vmwaresolutions_short}} 控制台提供的 IBM Spectrum Protect Plus 许可证（VM 数，以 10 为单位递增）或作为 BYOL 提供

## 安装 IBM Spectrum Protect Plus on IBM Cloud 时的注意事项
{: #spp_considerations-install}

安装 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：

* 确保实例的缺省集群中的 CPU 和内存足够用于 IBM Spectrum Protect Plus 虚拟机。
* 确保根据 ESXi 服务器版本，ESXi 服务器上的可用 NFS 安装足够。

  部署在（或升级到）V2.2 或更高发行版的实例在 VMware 中有 `NFS.MaxVolumes` 参数设置。此参数定义 ESXi 服务器上的最大 NFS 安装数，并可设置为最大值 256（特定于 ESXi 服务器版本）。有关更多信息，请参阅[增大定义 ESXi/ESX 主机上 NFS 最大挂载量的默认值](https://kb.vmware.com/s/article/2239){:external}。

  在实例的缺省集群中的每个 ESXi 服务器上，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务最多可以使用 11 个 NFS 卷。此外，该服务将创建瞬态 NFS 安装以用于备份和复原。因此，必须将 NFS 安装数设置为最小值 64，以确保可以成功安装并运行此服务。

## 除去 IBM Spectrum Protect Plus on IBM Cloud 时的注意事项
{: #spp_considerations-remove}

除去 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：
* 确保除去所有备份作业配置以及活动的备份或复原操作。
* 除去此服务时，将从 IBM Spectrum Protect Plus VM 中除去用于备份存储库的存储器，并取消存储器订单，这会永久删除备份存储库数据。
* 除去此服务时，还会除去为此服务订购的备份存储器。在除去服务期间，所有备份都会变得不可访问。

## 相关链接
{: #spp_considerations-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 预防性服务规划](https://www-01.ibm.com/support/docview.wss?uid=swg22012650){:external}
* [管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)
* [订购 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [IBM Spectrum Protect Plus 文档](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:external}
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
