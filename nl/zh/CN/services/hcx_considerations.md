---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud 规范和注意事项

HCX on {{site.data.keyword.cloud}} 服务可将内部部署数据中心的网络无缝扩展到 {{site.data.keyword.cloud_notm}}，这允许虚拟机 (VM) 在不进行任何转换或更改的情况下，迁移到 {{site.data.keyword.cloud_notm}} 或从中迁移出来。

此服务仅可用于在 V2.3 和更高发行版中部署的 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 实例。
{:note}

可以将现有 vCenter Server 实例升级到 vCenter Server with Hybridity Bundle 实例。有关升级实例和部署 HCX on {{site.data.keyword.cloud_notm}} 服务的更多信息，请参阅[升级到 vCenter Server with Hybridity Bundle 实例的过程](/docs/services/vmwaresolutions/vcenter/vc_applyingupdates.html#procedure-to-upgrade-to-the-vcenter-server-with-hybridity-bundle-instance)。

具有 HCX on {{site.data.keyword.cloud_notm}} 的 vCenter Server 实例限制为可同时从内部部署站点建立三个连接。
{:note}

## HCX on IBM Cloud 的技术规范

HCX on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

内部部署 HCX 实例仅包括许可和激活。
{:note}

### VMware NSX Edge 服务网关 (ESG) 的主动/被动对，以用于 HCX 管理

* CPU：6 个 vCPU
* RAM：8 GB
* 磁盘：3 GB VMDK

### HCX Management Appliance - 虚拟机

* CPU：4 个 vCPU
* RAM：12 GB
* 磁盘：60 GB VMDK

配置期间根据需要部署了更多 HCX 设备，以用于 L2 连接、WAN 优化和网关连接。

### 联网

* 一个具有 16 个 IP 地址的公用可移植子网
* 两个具有 64 个 IP 地址的专用可移植子网
* 专用可移植 vMotion 子网中的 8 个 IP 地址

## 安装 HCX on IBM Cloud 时的注意事项

尝试安装 HCX on {{site.data.keyword.cloud_notm}} 之前，请查看以下注意事项。

### 对 ESXi 服务器数的需求

无法将 HCX on {{site.data.keyword.cloud_notm}} 服务安装到其缺省集群的 ESXi 服务器数超过 51 个的实例中。因为 HCX on {{site.data.keyword.cloud_notm}} 需要缺省集群中 vMotion 子网中的 8 个 IP 地址，如果 ESXi 服务器数超过 51 个，那么 vMotion 子网中没有 IP 地址可用于 HCX on {{site.data.keyword.cloud_notm}}。

### 有关防火墙规则的需求

安装 HCX on {{site.data.keyword.cloud_notm}} 服务之前，必须向任何现有防火墙添加防火墙规则以允许所有出站 HTTPS 流量，以便 HCX Manager 虚拟设备 (HCX Manager) 可以注册自身。在 HCX Manager 安装完成后，可以除去该防火墙规则。此外，必须配置防火墙规则以允许 HCX 正常运行。有关更多信息，请参阅 [HCX on {{site.data.keyword.cloud_notm}} 体系结构](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)中的*附录 A - 端口访问需求*。

## 除去 HCX on IBM Cloud 时的注意事项

除去 HCX on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：
* 确保除去了内部部署源站点与 {{site.data.keyword.cloud_notm}} 目标站点之间的互连和扩展网络。要除去互连和扩展网络，请使用内部部署 VMware vSphere Web Client 中的 HCX 用户界面。
* 确保除去了内部部署源站点与 {{site.data.keyword.cloud_notm}} 目标站点之间的站点配对。要除去站点配对，请使用内部部署 VMware vSphere Web Client 中的 HCX 用户界面。
* 除去 HCX on {{site.data.keyword.cloud_notm}} 会自动执行。将完成以下过程，以成功除去此服务：
   * 停用为云端 HCX Manager 订购的 HCX 许可证。
   * 删除 HCX Manager。
   * 释放保留用于 HCX 的 vMotion IP 地址。
   * 如果为空，那么除去与 HCX 相关的资源池。
   * 如果为空，那么除去与 HCX 相关的文件夹。
   * 删除 HCX 管理 Edge 设备。

### 相关链接

* [订购 HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/hcx_ordering.html)
* [管理 HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managinghcx.html)
* [HCX 术语的词汇表](/docs/services/vmwaresolutions/services/hcx_glossary.html)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension 概述](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension 文档](https://cloud.vmware.com/vmware-hcx/resources)
