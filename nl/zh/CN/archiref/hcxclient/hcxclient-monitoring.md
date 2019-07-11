---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 监视参数和组件
{: #hcxclient-monitoring}

## 使用 WAN Optimizer 进行监视
{: #hcxclient-monitoring-using-wan}

作为 HCX 的一部分部署的 Silver Peak WAN 优化设备未配置其管理界面。该 Web 用户界面 (UI) 是一个很有用的工具，可在设置流量吞吐量基线以及对网络迁移带宽使用量调速时使用。

仅 HCX CGW 网关 WAN 隧道流量会流过 WAN Optimizer 设备。因此，它无法监视 L2 延伸流量。
{:note}

### 配置 UI
{: #hcxclient-monitoring-config-ui}

除了配置 Web UI 的 IP 地址外，不要对 WAN Optimizer 设备进行其他配置更改，除非 {{site.data.keyword.IBM}} 或 VMware 支持人员指示这样做。

要配置 WAN Opt Web UI，请执行以下操作：

1. 在 vCenter 客户机中找到 WAN Opt 虚拟机 (VM) 设备。
2. 将控制台打开到使用 vCenter 客户机的 VM。
3. 在控制台中，单击 **F4** 以配置管理界面。
4. 选择以配置静态 IP。
5. 使用管理 {{site.data.keyword.cloud}} 分配的可移植 IP 范围的 IP 地址和缺省网关。
6. 单击下一个屏幕上的**应用**以保存。
7. 在 vCenter 控制台中，单击 WAN Opt VM 的编辑设置。
8. 选择**打开电源时已连接**和**对于网络适配器 1 为已连接**。
9. 单击**确定**以保存。
10. 在 vCenter 中找到“CGW - <xxx> - WANOPT”。
11. 编辑 VM 上的设置。
12. 单击复选框以连接网络适配器 1。
13. 单击**确定**。
14. 转至 `https://<configured_WAN_OPT_IP>`。
15. 使用 `admin` 缺省用户和 `admin` 密码登录。

现在，可以使用 WAN Opt Web UI 来监视吞吐量速率、压缩比率以及设置带宽限制。

### 迁移带宽调速
{: #hcxclient-monitoring-mig-bandwidth}

迁移 VM 之前，请对使用的网络链路执行评估。请与包含 vSphere 源实例的网络的联网工程师合作，或者复查每周和每月的流量使用情况。如果该流量通过对业务关键的链路进行遍历，尤其是该链路小于 1 Gbps 时，请限制用于迁移的可用带宽。使用带宽限制最严格的一端，这通常是客户机端。

在 HCX 客户机 UI 中部署系列组件时执行此操作，但部署后需要转至 WAN Opt UI。

如果在 HCX Web UI 中重新部署 HCX CGW，那么更改将丢失。这仅针对迁移流量设置带宽限制。L2 延伸流量不受此设置的影响。
{:note}

1. 登录到 WAN Opt Web UI。
2. 在**配置**选项卡中，从菜单中选择**整形器**。
3. 在**最大带宽**框中，设置 WAN Opt 设备可用的最大带宽（以 Kbps 为单位）。不要超过 WAN 链路的最大带宽。要将值设置为以 Mbps 为单位，请乘以 1，000。 要将值设置为以 Gbps 为单位，请乘以 1,000,000。 缺省值为 10 Gbps (10,000,000 Kbps)。
4. 单击**应用**。

对于 L2 延伸带宽调速，可以对传输 L2C 设备之间隧道流量的 UDP 500 和 4500 应用 QoS。

## 监视 HCX 组件
{: #hcxclient-monitoring-hcx-comp}

通过以下方式监视 HCX 组件，例如 HCX Manager、云网关、WAN opt 和第 2 层集中器：

- 配置 HCX Manager 以向 Syslog 服务器发送日志。使用 HCX Manager 设备管理实用程序来运行 `https://<hcxhostname or
IP>:9443` 命令。
- 针对每个 L2 延伸网络，设置对网络摆动之前迁移的 VM 的 ping。
- 使用 VMware vRealize Operations Manager 或其他 VMware VM 监视工具来监视 HCX 组件 VM 运行状况。

## 带宽使用量
{: #hcxclient-monitoring-band-use}

使用以下方法可监视带宽使用量和等待时间。

- vMotion 流量最好使用 WAN Opt Web UI 来完成。WAN Opt 可显著降低通过 WAN 传输的流量，并通过发送冗余包来减少丢包。据观察，LAN 与 WAN 带宽使用量的典型比率约为 3:1 (350 Mbps LAN = 90-120 Mbps WAN)。
- 基于复制（批量）迁移 HCX 中的 VM 会导致 VM 通过密集配置进行迁移。虽然这并不是希望出现的情况，但在移动未使用的磁盘数据时，WAN Opt UI 显示的 LAN 与 WAN 使用量比率较高。与之相反的是，据观察，迁移非可压缩数据（例如，数据库数据和数字介质）时，WAN 的使用量达到峰值，更接近 LAN 使用量。

观察结果：
- 在 HCX 内 VM 的 vMotion 迁移不会生成比单个 ESXi 主机的 vMotion 联网更大的吞吐量。
- 由于批量迁移可以同时动态执行多个迁移，因此带宽使用量高于 vMotion 迁移。在使用 ESX 主机的 1 Gbps vMotion 链路的客户端观察到的比率为：8 个复制 = 1 个 vMotion 的带宽使用量。
- 移动磁盘中未使用的空间会导致显示较高的 LAN 使用量，并且 LAN 与 WAN 使用量比率较高，因而 WAN 使用量较低。请注意，1 Gbps 似乎是限制。实际上，在此特定情况下，vMotion 网络只能达到 1 Gbps，这是瓶颈。
- 对多 TB Oracle 数据库执行 vMotion 迁移。对于 1 Gbps 的 WAN 链路，vMotion 网络的限制为 1 Gbps。

## 第 2 层延伸流量
{: #hcxclient-monitoring-stretched-layer-2-traffic}

HCX 系列组件第 2 层集中器对于遍历该集中器的所有 L2 网络流量，设置了约 4 Gbps 的带宽限制。单独延伸的网络的带宽限制为约 1 Gbps 或更低，具体取决于流量类型。可以在单个 L2C 对上具有多个 L2 延伸网络（理论上允许每个 L2C 对最多有 4096 个网络）。虽然 L2C 设计为检测并保护同一 L2C 对内的小流量流不被大流量淹没，但确定是否发生这种情况，并启动更多 L2C 来提高总体带宽能力，会非常有利。

如果在客户站点与 {{site.data.keyword.cloud}} 之间存在多个路径（例如，直接链路和因特网），那么部署多个 L2C 也可能非常有利。在多个 L2C 对上，不能使单个网络成为冗余或增加单个网络的带宽。

使用 L2C VM 的“监视”选项卡来监视所有接口上的流量。如果总数据率接近 8 Gbps（4 Gbps 输入/输出），请考虑添加另一个 L2 对，并重新分配延伸网络以进行重新均衡。

## 相关链接
{: #hcxclient-monitoring-related}

* [HCX 组件和术语的词汇表](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [准备安装环境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 客户机部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 内部部署服务网](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合云迁移](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
