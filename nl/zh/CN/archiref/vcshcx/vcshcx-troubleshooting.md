---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

# HCX 故障诊断
{: #vcshcx-troubleshooting}

查看以下信息以了解常见 HCX 问题和解决办法。

## HCX 客户机用户界面问题
{: #vcshcx-troubleshooting-hcx-client-issues}

### HCX 用户界面令牌超时
{: #vcshcx-troubleshooting-hcx-ui-issues}

通常，如果 vCenter 用户界面 (UI) 已经保持打开一段时间，那么可能会在 HCX UI 中遇到超时。这是因为 HCX Manager 服务器的登录令牌已超时。请从 vSphere Web UI 注销，然后重新登录以刷新该令牌。

### 在 HCX 客户机 UI 的仪表板屏幕上，所有度量值均显示为“NaN”
{: #vcshcx-troubleshooting-nan-display}

此问题与当前登录的 vCenter 帐户的许可权相关。请确保在 HCX 云端设备管理器 UI 中设置“企业管理员”组。

## 迁移问题
{: #vcshcx-troubleshooting-mig-issues}

当前版本的 HCX 中的迁移问题通常分为三个类别：许可、云网关联网连接和目标硬件兼容性。

### 许可
{: #vcshcx-troubleshooting-licensing}

如果由于许可问题而导致迁移失败，那么当前版本的 HCX 会在 vCenter UI 中客户机 Web UI 的错误消息中明确显示此信息。

### 网络 (WAN) 连接
{: #vcshcx-troubleshooting-wan-connect}

如果 WAN 连接存在问题，请务必检查 HCX UI 中的**互连 -> HCX 组件**屏幕以了解隧道状态。系列组件通常无需重置或重新引导。如果 WAN 连接已复原，那么这些组件会自动重新连接。

如果有适用于 HCX Manager（客户机和云）的修订和更新，并且这些更新还会修补与系列组件相关的问题，那么必须对云网关以及部署的任何 L2C 进行重新部署。通过 SSH 客户机（如 ccli）连接到 HCX Manager，可以进一步执行隧道状态调试。  

1. 使用管理员帐户和提供的密码通过 SSH 登录到 HCX Manager。
2. 运行 `su –` 命令，并输入 `root` 用户的密码（与管理员密码相同）以切换为 root 用户。
3. 将目录切换到 `/opt/vmware/bin`，然后运行 `./ccli` 命令。如果由于环境不是针对 root 用户设置的而失败，请运行 `./ccliSetup.pl` 命令。
4. 在 `ccli` 中运行 `list` 命令，以列出向 HCX Manager 注册的系列组件。
5. 通过输入为系列组件列出的标识，选择 `ccli` 的系列标识。例如，`go 8`。
6. 运行 `debug remoteaccess enable` 命令，以使用 SSH 连接到所需的系列组件。
7. 退出 `ccli`，然后使用 SSH 连接到启用了 SSH 的系列组件的 IP 地址。
9. 继续进行故障诊断。
10. 返回到 `ccli` 并禁用组件的 `ssh` 服务。
11. 如果需要，请使用 `hc` ccli 命令对组件执行运行状况检查。

## 目标硬件兼容性问题
{: #vcshcx-troubleshooting-hw-compatibility}

客户机源端的硬件版本和 vSphere 发行版高于云时，vMotion 迁移可能会发生问题。由于基于复制的迁移是将数据复制到目标端新构建的虚拟机 (VM)，因此将迁移类型更改为“批量迁移”应该在大多数情况下会允许迁移成功。

## 延伸的 L2 集中器问题
{: #vcshcx-troubleshooting-stretched-l2}

L2 集中器 (L2C) 运行时，发生的问题极少。与 CGW 类似，如果 L2C 失去连接，那么在网络连接复原后，L2C 会自动重新连接。使用 ccli shell 来检查运行状况和操作。启用了 SSH 并且连接 L2C 后，运行 `ip tunnel` 和 `ip link |grep t_` 命令可查看隧道的状态。

## 相关链接
{: #vcshcx-troubleshooting-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
