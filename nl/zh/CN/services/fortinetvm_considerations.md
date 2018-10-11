---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# FortiGate Virtual Appliance on IBM Cloud 概述

FortiGate Virtual Appliance on {{site.data.keyword.cloud}} 服务用于将 FortiGate Virtual Appliance 成对部署到环境中，这可帮助通过在虚拟基础架构中实施关键安全控制来降低风险。

可以根据需要安装此服务的多个实例。可以使用 FortiOS Web Client 或通过 SSH 连接的命令行界面来管理此服务。

**可用性**：此服务仅可用于在 V2.0 或更高发行版中部署的实例。

## FortiGate Virtual Appliance on IBM Cloud 的技术规范

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### 虚拟机

* 所有选项都包含虚拟机的高可用性 (HA) 对
* 每个虚拟机 2、4 或 8 个 vCPU，具体取决于部署大小和预订类型
* 每个虚拟机 4、6 或 12 GB RAM，具体取决于部署大小和预订类型

### 高可用性

部署了两个虚拟机，并且这两个虚拟机已准备就绪，可进行 HA 或虚拟路由器冗余协议 (VRRP) 配置。

### 联网

通过专用管理网络提供了对 FortiGate® 控制台的访问权。

### 许可证和费用

每个虚拟机的许可费用将应用于每个计费周期，具体取决于所选的部署大小和每月预订许可模型。

**重要信息**：无法在安装服务后更改许可级别。要更改许可级别，必须除去现有服务，然后使用其他许可选项来重新安装该服务。

## 安装 FortiGate Virtual Appliance on IBM Cloud 时的注意事项

安装 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：
* FortiGate 虚拟机 (VM) 将仅部署到缺省集群中。
* 此外，还为这两个 FortiGate VM 保留了 100% 的 CPU 和 RAM，因为这两个 VM 位于网络通信的数据平面中，并且资源仍然可用对这两个 VM 而言至关重要。

  要计算单个 FortiGate VM 的 CPU 和 RAM 保留量，请使用以下公式：
   * `CPU 保留量 = ESXi 服务器的 CPU 速度 * vCPU 数`
   * `RAM 保留量 = RAM 大小`
* 将 FortiGate Virtual Appliance 的 HA 对部署到实例时，SNAT 和防火墙规则会在“管理 NSX Edge 服务网关 (ESG)”上定义，同时会定义 FortiGate Virtual Appliance 上的静态路由，以允许实例到公用网络的出站 HTTPS 通信，从而激活许可证并获取最新的安全策略和内容。
* 服务安装后即无法更改许可级别。要更改许可级别，必须除去现有服务，然后通过选择其他许可选项来重新安装该服务。
* 必须满足以下需求，以避免 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 上发生故障：
   * 至少有两个活动 ESXi 服务器可用，以使用可使这两个 VM 位于不同服务器上的反关联性规则来部署这两个 FortiGate VM。
   * 这两个活动 ESXi 服务器有足够的资源可用，以便每个 ESXi 服务器上可以托管一个 FortiGate VM，并具有 100% 的 CPU 和 RAM 保留量。
   * VMware vSphere HA 有足够的资源来托管具有 100% 的 CPU 和 RAM 的两个 FortiGate VM。

  由于这些需求，您必须谨慎规划 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 所需的空间。如果需要，在订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 之前，请向实例添加 1 到 2 个 ESXi 服务器和/或减少用于故障转移的 vSphere HA CPU 保留量。

## FortiGate Virtual Appliance on IBM Cloud 订购示例

您订购了具有 2 个 ESXi 服务器的 VMware vCenter Server **小型**实例，配置如下：16 个核心 (2.10 GHz)，每个核心 128 GB RAM。对于 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}，您为部署大小和任何预订许可模型选择了**大型**（8 个 vCPU/ 12 GB RAM）。

在本例中，在每个服务器上，单个 FortiGate VM 需要：
* 2.1 GHz * 8 个 vCPU = 16.8 GHz CPU，以及
* 12 GB RAM

对于两个 FortiGate VM，共需要 33.6 GHz 的 CPU 和 24 GB RAM。

每个 ESXi 服务器的容量都为 16 个核心 * 2.1 GHz = 33.6 GHz，因此如果这两个服务器都处于活动状态，并且每个服务器上至少有 16.8 GHz 的 CPU 和 12 GB RAM 可用，那么可满足前两个需求。

但是，缺省情况下，vSphere HA 会将 50% 的 CPU 和 RAM 保留用于在最初部署有 2 个 ESXi 服务器的 vCenter Server 实例上进行故障转移，因此我们只有：

`2 * 16 个核心 * 2.1 GHz * 50% = 33.6 GHz 可用`

由于 ESXi 服务器上存在其他工作负载（例如，VMware vCenter Server、VMware NSX Controller 或 VMware NSX Edge），因此使用这些资源无法满足第三个需求。这是因为对于两个 FortiGate VM，我们需要 33.6 GHz 的 CPU 和 24 GB RAM。

在这种情况下，FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 安装可能会失败，除非至少向环境中添加一个 ESXi 服务器，并且相应地更新 vShpere HA 故障转移保留量，以确保有足够资源可用于这两个 FortiGate VM。

如果需要更多资源来运行 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务，可以在安装该服务之前添加更多 ESXi 服务器。

## 除去 FortiGate Virtual Appliance on IBM Cloud 时的注意事项

除去 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务之前，请确保正确除去了现有 FortiGate Virtual Appliance 的配置。具体来说，网络流量必须围绕 FortiGate Virtual Appliance 而不是通过 FortiGate Virtual Appliance 来路由。否则，可能会影响环境中的现有数据流量。

### 相关链接

* [订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_ordering.html)
* [管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [Fortinet Web 站点](https://www.fortinet.com/){:new_window}
* [Fortinet 文档库](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
