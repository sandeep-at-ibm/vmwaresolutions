---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# HCX 组件和术语的词汇表
{: #vcshcx-components}

HCX 由一个云端（目标）和一个或多个客户机（源）组成。必须为每个 vCenter 部署一个 HCX 实例，即使部署了 HCX 的 vCenter 在客户机或云端的同一 SSO 域中链接也是如此。HCX 支持的配置为一对一、一对多、多对一和多对多。

## 云端和客户机端
{: #vcshcx-components-cloud-client-side}

HCX 具有云端（目标）和客户机端（源）的概念。
- 云端 - vCenter Server on 	{{site.data.keyword.cloud}} with Hybridity Bundle。HCX 的云端在 HCX 客户机与云的关系中是从属实例，由客户机端进行控制。
- 客户机端 - 满足安装和运行先决条件的任何 vSphere 实例。HCX 的客户机端是主实例，通过其 vCenter Web 客户机用户界面 (UI) 插入件来控制云端从属实例。

## HCX Manager
{: #vcshcx-components-hcx-manager}

- 云端 HCX Manager 是 {{site.data.keyword.vmwaresolutions_short}} 自动化在云端部署的 HCX 安装中的第一部分。最初，这是特定于云端的单个部署的 OVA 映像文件，同时部署有 NSX Edge 负载均衡器（专门为 HCX 角色配置的防火墙）。HCX Manager 配置为侦听入局客户机端注册、管理和控制流量。
- 客户机端 HCX Manager 是特定于客户机端的 OVA 映像文件，提供用于管理和运行 HCX 的 UI 功能。客户机端 HCX Manager 负责向云端 HCX Manager 进行注册，并在客户机与云端之间创建管理平面。此外，它还负责在客户机端部署系列组件，并指示云端执行相同的操作。

## 系列组件
{: #vcshcx-components-fleet}

HCX 系列组件负责在客户机和云端之间创建数据和控制平面。系列作为虚拟机 (VM) 部署为镜像对，由以下组件组成：

- 云网关 (CGW) - 云网关是一个可选组件，负责创建支持 vMotion 和复制（批量迁移）流量的加密隧道。每个链接的 HCX 站点仅存在一个对。
- 第 2 层集中器 (L2C) - 第 2 层集中器是一个可选组件，负责为数据和控制平面创建对应于第 2 层延伸流量的加密隧道。每个 L2C 对可以处理多达 4096 个延伸网络。可根据需要部署更多 L2C 对。带宽能力限制为约 4 Gbps，因此如果外部带宽容量大于 4 Gbps，那么使用更多 L2C 对可提高底层网络的利用率。
- WAN Optimizer - HCX 包含可选择部署的 Silver Peak™ WAN 优化设备。它会部署为 VM 设备。部署后，CGW 隧道流量会重定向，以遍历 WAN Optimizer 对。由于 WAN Optimizer 可显著降低 WAN 上的流量（据观察，通常比率为 3:1 到 6:1），同时提高了连接可靠性，因此建议始终对 CGW 部署 WAN Optimizer。部署 WAN Optimizer 的额外好处是，可限制 VM 迁移流量使用的 WAN 带宽。缺省情况下，未配置 WAN Optimizer 管理界面。
- 代理 ESX 主机 - 每当将 CGW 配置为连接到云端 HCX 站点时，都会在任何集群外部的 vCenter 中显示代理 ESXi 主机。此 ESXi 主机的管理和 vMotion IP 地址与对应的 CGW 设备相同。这支持客户机和云端的 vSphere 环境像执行本地 vMotion 一样正常运行。此方法的优点如下：
    - 任一端的管理 IP 范围可能重叠，但功能不会丢失。
    - 云端无法查看客户机端的 vSphere，因此安全性更高。

## HCX 用户门户网站
{: #vcshcx-components-hcx-user-portals}

- 客户机 Web UI - HCX 客户机 Web 门户网站是 HCX 的主 UI。在安装客户机端 HCX Manager 后，它显示为 vCenter Web UI 的插入件。它可控制远程云 HCX 注册（站点配对）、系列组件部署、网络延伸以及将 VM 迁入云中和从云中迁出 VM。

- 云端 UI - 通过为 HCX 客户机注册提供的公共注册 URL，可以访问云端 HCX UI。缺省情况下，云端 UI 会使用云端 vSphere SSO 登录 (`administrator@vsphere.local`)。此 UI 通常用于升级安装和修改某些网络配置。还可用于在 HCX 中构建虚拟网络。

- 客户机/云 HCX Manager 设备管理 UI - 通过 VM 专用 IP 地址（可在 vCenter 中查看）访问云端或客户机端的设备管理 UI。`https://<hcxmanager_IP>:9443`。标识（通常为“admin”）和密码通过 {{site.data.keyword.vmwaresolutions_short}} 门户网站提供。管理 UI 用于启动和停止 HCX Manager 服务，配置日志监视，进行基本联网配置，手动升级，支持在 Web UI 未运行时收集日志，以及注册 vSphere 组件（vCenter、PSC 和 NSX Manager）和管理证书。

## 相关链接
{: #vcshcx-components-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
