---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# 部分分布式
{: #caveonix-partially}

自动部署完成后，可以通过在初始虚拟机 (VM) 中增加 RAM 和磁盘，并添加三个横向扩展 VM 来手动横向扩展。可以运行 Riskforesight 配置脚本来启用和配置所有四个 VM 上的应用程序组件。

此部署模型预计将最多提供 500 个资产，包含最多 30 天的数据索引。

从 {{site.data.keyword.cloud}} 专用可移植子网中选择下一个可用 IP 地址。在 ADDNS 中配置 FQDN 名称。

VM 的大小调整如下所示：

表 1. 基本参数

|参数|值|
|---|---|
|类型|基本|
|VM 数量|1|
|vCPU|16|
|RAM|64 GB|
|磁盘|1000 GB|
|操作系统|CentOS 7|
|已安装的应用程序组件|UI、应用程序、插件、中央收集器、索引数据存储、消息传递数据存储、关系数据存储和远程收集器|

横向扩展 VM 详细信息如下所示：

表 2. 横向扩展参数

|参数|值|
|---|---|
|类型|横向扩展|
|VM 数量|3|
|vCPU|8|
|RAM|16 GB|
|磁盘|4 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|数据节点（横向扩展）|

下表中显示了远程收集器 VM 详细信息。

表 3. 远程收集器参数

|参数|值|
|---|---|
|VM 数量|根据需要|
|vCPU|8|
|RAM|8 GB|
|磁盘|1 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|远程收集器|

## 相关链接
{: #caveonix-partially-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
