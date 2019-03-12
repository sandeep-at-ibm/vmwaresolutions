---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 一体化部署
{: #caveonix-allinone}

自动部署和配置一个虚拟机 (VM)，用于托管所有 RiskForesight 应用程序组件。此部署模型适用于小型部署，即最多 100 个资产，包含 7 到 30 天的索引。下表中显示了“一体化”VM 详细信息：

表 1. 一体化参数

|参数|值|
|---|---|
|类型|基本|
|VM 数量|1|
|vCPU|16|
|RAM|32 GB|
|磁盘|80 GB|
|操作系统|CentOS 7|
|已安装的应用程序组件|	UI、应用程序、插件、中央收集器、索引数据存储、消息传递数据存储、关系数据存储和远程收集器|

下表中显示了其他远程收集器 VM 详细信息。

表 2. 远程收集器

|参数|值|
|---|---|
|VM 数量|根据需要|
|vCPU|8|
|RAM|8 GB|
|磁盘|1 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|远程收集器|

## 相关链接
{: #caveonix-allinone-related}

*   [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
