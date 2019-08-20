---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# HCX 组件和术语的词汇表
{: #hcxclient-components}

HCX 由一个云端（目标或 VCD 环境）和一个或多个客户机（源）组成。必须为每个 vCenter 部署一个 HCX 实例，即使部署了 HCX 的 vCenter 在客户机或云端的同一 SSO 域中链接也是如此。HCX 支持的配置为一对一、一对多、多对一和多对多。

## 目标端和客户机端
{: #hcxclient-components-cloud-client-side}

HCX 具有云端（目标或 VCD 环境）和客户机端（源）的概念。

- 目标端 - HCX Cloud Manager 预先部署并配置了网络和计算概要文件，可随时用于创建服务网。  
- 客户机端 - 满足安装和运行先决条件的任何 vSphere 实例。HCX 的客户机端是主实例，通过其 vCenter Web 客户机用户界面 (UI) 插入件来控制云端从属实例。

## HCX Manager
{: #hcxclient-components-hcx-manager}

- 云端 - HCX Cloud Manager 配置为侦听入局客户机端注册、管理和控制流量。
- 客户机端 - HCX Enterprise Manager 是特定于客户机端的 OVA 映像文件，提供用于管理和运行 HCX 的 UI 功能。客户机端 HCX Manager 负责向云端 HCX Manager 进行注册，并在客户机与云端之间创建管理平面。此外，它还负责在客户机端部署服务网，并指示云端执行相同的操作。

## 服务网组件
{: #hcxclient-components-fleet}

HCX 服务网组件负责在客户机和云端之间创建数据和控制平面。服务网作为虚拟机 (VM) 部署为镜像对，由以下组件组成：

- 互联设备 (HCX-IX) - 互联设备创建支持 vMotion 和复制（批量迁移）流量的加密隧道。
- WAN Optimizer 设备 (HCX-WAN) - HCX 包含可选择部署的 Silver Peak™ WAN 优化设备。它会部署为 VM 设备。部署后，CGW 隧道流量会重定向，以遍历 WAN Optimizer。由于 WAN Optimizer 可显著降低 WAN 上的流量（据观察，通常比率为 3:1 到 6:1），同时提高了连接可靠性，因此建议始终对 CGW 部署 WAN Optimizer。部署 WAN Optimizer 的额外好处是，可限制 VM 迁移流量使用的 WAN 带宽。缺省情况下，未配置 WAN Optimizer 管理界面。
- 网络扩展 (HX-NE) - 提供第 2 层网络扩展功能，支持在内部部署位置和 vSphere 环境之间迁移，需要为 VM 重新分配 IP 地址。
- 代理 ESXi 主机 - 每当将 HCX-IX 配置为连接到云端 HCX 站点时，都会在任何集群外部的 vCenter 中显示代理 ESXi 主机。此 ESXi 主机的管理和 vMotion IP 地址与对应的 HCX-IX 设备相同。这支持客户机和云端的 vSphere 环境像执行本地 vMotion 一样正常运行。此方法的优点如下：
  - 任一端的管理 IP 范围可能重叠，但功能不会丢失。
  - 云端无法查看客户机端的 vSphere，因此安全性更高。

## HCX 用户门户网站
{: #hcxclient-components-hcx-user-portals}

- 客户机 Web UI - HCX 客户机 Web 门户网站是 HCX 的主 UI。客户机端 HCX Manager 安装后，会显示为 vCenter Web UI 的插入件。它可控制远程云 HCX 注册（站点配对）、系列组件部署、网络延伸以及将 VM 迁入云中和从云中迁出 VM。
- 云端 UI - 通过为 HCX 客户机注册提供的公共注册 URL，可以访问云端 HCX UI。缺省情况下，会使用云端 vCenter Admin 凭证 `administrator@vsphere.local`。此 UI 通常用于升级安装和修改某些网络配置。

## 相关链接
{: #hcxclient-components-related}

* [VMware HCX on IBM Cloud 的端口访问需求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [准备安装环境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 客户机部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 内部部署服务网](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合云迁移](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [监视参数和组件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
