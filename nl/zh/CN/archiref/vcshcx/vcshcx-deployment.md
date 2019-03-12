---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# 云和客户机部署
{: #vcshcx-deployment}

如本文档开头所述，最小的 HCX 安装包含单个云和客户机端部署。HCX 客户机端可以安装在 HCX 支持的任何版本的 vSphere 上，前提是客户机端与云端之间存在网络连接。

## 需求
{: #vcshcx-deployment-req}

- HCX Manager - CPU 计数 4 个，内存 12 G，磁盘 60 G
- CGW - CPU 计数 8 个，内存 3 G，磁盘 2 G
- L2C - CPU 计数 8 个，内存 3 G，磁盘 2 G
- WAN Opt - CPU 计数 8 个，内存 14 G，磁盘 100 G

## 云
{: #vcshcx-deployment-cloud}

云端 HCX 部署由 {{site.data.keyword.vmwaresolutions_full}} 自动化进行处理。缺省配置使用公共端口组来配置任何系列组件端点连接。云端上的系列组件通过其配置有公共 IP 地址的端点接口进行部署，因为这些组件是安全加固设备。可以将这些组件部署在防火墙后面。不支持客户机端和云端通过现有 VPN 隧道相互连接。如果要使用专用网络进行 HCX 端点连接，那么可以为专用网络系列部署订购 HCX 云端，以便通过专用链路（例如，MPLS）使用。

## 客户机
{: #vcshcx-deployment-client}

客户机端 HCX 是用户部署的，需要具有对源 vCenter 的管理员级别许可权。本文撰写之时，HCX 客户机端管理器 OVA 大约为 1.7 GB。使用 {{site.data.keyword.vmwaresolutions_short}} 控制台订购 HCX 时，会提供一个 URL，其中包含用于下载客户机端 HCX 版本的链接，该版本与部署在云端的 HCX 版本相匹配。此链接在云端管理器 HCX 用户界面 (UI) 中提供。

此外，还提供一次性使用注册密钥。使用以下步骤来配置使用注册。

1. 从云端 HCX UI 中提供的链接下载 HCX 客户机（企业）OVA。
    1. 使用 IBM 提供的 HCX 注册 UI 登录到云端 HCX UI。
    2. 使用云 vCenter 标识和密码登录到 UI。
    3. 在**管理**选项卡上，选择**请求下载链接**以下载客户机端 OVA。使用部署了 OVA 的源 vCenter 的本地“跳转框”来完成此步骤。
2. 登录到 vSphere C++ 客户机（或具有正常运行的客户机集成插入件的 Web 客户机），然后使用 vCenter 导入向导来导入 OVA。
    1. 确保配置了 HCX Manager 的网络有权访问源 vCenter 和因特网。  
    2. 系统提示时输入注册密钥。（如果您已设置客户机工具插入件，请使用 Web 客户机。）  
3. 注销并重新登录到 vCenter Web 客户机。**HCX** 菜单选择图标会显示在主屏幕菜单下。
4. 对于自签名证书，请选择 HCX 菜单项以访问 HX 插入件 UI。选择**管理**选项卡。
    1. 选择从 URL 导入证书，并键入 HCX 的 {{site.data.keyword.vmwaresolutions_short}} 控制台提供的 HCX 云端注册 URL。
    2. 在**仪表板**选项卡的**站点配对**窗格中，选择**新建站点配对**。
    3. 遵循提示并提供 HCX 云端注册 URL 以及云端 vCenter 管理员标识和密码。
    4. 继续遵循站点注册向导中的提示来配置系列组件，包括云网关、第 2 层集中器和 WAN Optimizer。  

对于客户机端，使用**任务**菜单来监视系列组件的部署。对于云端部署，请使用 vCenter Web UI 中针对特定 vCenter Server 实例的**任务**菜单。

如果任一端发生部署失败，那么将退出并删除系列组件部署。确定故障原因后，单击客户机端 HCX vCenter Web UI 中的**互连**选项卡，然后在屏幕顶部选择**安装 HCX 组件**。

成功部署系列组件并等待几分钟后，在**互连**选项卡中，CGW 和 L2C 组件的隧道状态将为**正常运行**状态。

## 相关链接
{: #vcshcx-deployment-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
