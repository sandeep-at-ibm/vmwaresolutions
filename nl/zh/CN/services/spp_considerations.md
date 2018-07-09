---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# IBM Spectrum Protect Plus on IBM Cloud 概述

IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} 服务为虚拟环境下的数据保护、数据复用和数据恢复提供高效、可扩展的解决方案。可以将此服务作为独立解决方案实施，也可以与 IBM Spectrum Protect Plus 环境集成，以便卸载用于长期存储和数据监管的副本。

**可用性**：此服务仅可用于运行 vSphere 6.5 以及部署在（或升级到）V2.2 或更高发行版的实例。

**注：**
* 如果为部署在 V2.4 或更高发行版中的实例安装服务，那么会安装 IBM Spectrum Protect Plus V10.1.1 补丁 1。此服务会自动为管理虚拟机 (VM) 提供恢复支持。
* 如果为部署在 V2.3 中的实例安装服务，那么会安装 IBM Spectrum Protect Plus V10.1.1。该服务会自动为管理 VM 提供备份。
* 如果为部署在 V2.2 中的实例安装服务，那么会安装 IBM Spectrum Protect Plus V10.1.0。此服务仅为工作负载 VM 提供数据保护。


## IBM Spectrum Protect Plus on IBM Cloud 的组件

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### vCenter 资源

* 一个虚拟机 (VM)，用于运行 IBM Spectrum Protect Plus 服务器
* 4 个 2.0 GHz 核心
* 32 GB RAM
* 370 GB 磁盘

### 用于备份的存储器

用于备份的可定制存储器具有以下选项：
* 文件存储器数：1、2、3 或 4 个
* 每个耐久性文件存储器：500、1000、2000、4000、8000 或 12000 GB
* 存储器性能：0.25、2 或 4 IOPS/GB

### 用于管理的存储器

一个耐久性文件存储器（500 GB，2 IOPS/GB），用于托管 IBM Spectrum Protect Plus 虚拟机并在为该服务订购的备份存储器所在的子网上运行。

### 联网

一个可移植专用 IP 地址。

### 许可证和费用

可在 {{site.data.keyword.vmwaresolutions_short}} 控制台中针对 10 个到最多 1000 个 VM（以 10 为单位递增）对 IBM Spectrum Protect Plus 进行许可。还可以自带许可证 (BYOL) 并在安装过程中上传许可证文件。

## 安装 IBM Spectrum Protect Plus on IBM Cloud 时的注意事项

安装 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：

* 确保实例的缺省集群中的 CPU 和内存足够用于 IBM Spectrum Protect Plus 虚拟机。
* 确保根据 ESXi 服务器版本，ESXi 服务器上的可用 NFS 安装足够。

  部署在（或升级到）V2.2 或更高发行版的 Cloud Foundation 实例和 vCenter Server 实例在 VMware 中有 `NFS.MaxVolumes` 参数设置。此参数定义 ESXi 服务器上的最大 NFS 安装数，并可设置为最大值 256（特定于 ESXi 服务器版本）。有关更多信息，请参阅[增大定义 ESXi/ESX 主机上 NFS 最大挂载量的默认值](https://kb.vmware.com/s/article/2239)。

  在实例的缺省集群中的每个 ESXi 服务器上，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务最多可以使用五个 NFS 卷。此外，该服务将创建瞬态 NFS 安装以用于备份和复原。因此，必须将 NFS 安装数设置为最小值 64，以确保可以成功安装并运行此服务。

## 除去 IBM Spectrum Protect Plus on IBM Cloud 时的注意事项

除去 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：
* 确保除去所有备份作业配置，并确保不存在任何活动的备份或复原操作。
* 除去此服务时，将从 IBM Spectrum Protect Plus VM 中除去用于备份存储库的存储器，并取消存储器订单，这会永久删除备份存储库数据。
* 除去此服务时，还会除去为此服务订购的备份存储器。因此，在除去服务期间，所有备份都会变得不可访问。

## 相关链接

* [IBM Spectrum Protect Plus on IBM Cloud 预防性服务规划](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [订购 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [IBM Spectrum Protect Plus 文档](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
