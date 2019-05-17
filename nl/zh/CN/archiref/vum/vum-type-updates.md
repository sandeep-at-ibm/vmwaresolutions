---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# VMware 软件更新的类型
{: #vum-type-updates}

VMware 使用以下术语来描述软件更新。

表 1. VMware 软件更新术语和定义

|术语|定义
|
|:------- |:----------- |
|公告|	由一个或多个 VIB 构成的分组。公告在元数据中进行定义。|
|库|	由联机发布的 VIB 和关联元数据构成的逻辑分组|
|主机升级映像|	一种 ESXi 映像，可以在 Update Manager 存储库中导入并用于将 ESXi 5.5 或 ESXi 6.0 主机升级到 ESXi 6.5。|
|扩展| 	一种公告，定义用于将可选组件添加到 ESXi 主机的一组 VIB。扩展通常由第三方提供，该第三方还负责提供扩展的补丁或更新。|
|元数据|	用于定义依赖性信息、文本描述、系统需求和公告的额外数据。|
|脱机捆绑软件压缩文件|	一个归档文件，用于将 VIB 和相应元数据封装在一个自包含的包中，这对于脱机修补很有用。不能使用第三方脱机捆绑软件，也不能使用基于从 ESXi 5.5 或 ESXi 6.0 到 ESXi 6.5 的主机升级的定制 VIB 集生成的脱机捆绑软件。|
|补丁|	一种公告，用于将一个或多个 VIB 分组在一起以解决特定问题或增强功能。|
|累积|	为便于下载和部署而分组在一起的补丁集合。|
|VA 升级|	虚拟设备的更新，供应商将其视为升级。|
|VIB|	VIB 是单个软件包。|

## 相关链接
{: #vum-type-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解决方案体系结构](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 数字技术互动](https://ibm-dte.mybluemix.net/vmware)（演示）
