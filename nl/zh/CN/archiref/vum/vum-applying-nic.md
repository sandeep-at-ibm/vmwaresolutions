---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# 应用本机 NIC 驱动程序

ESXi 6.5 包含许多新的本机驱动程序，用于替换较低版本的 vmklinux 驱动程序。缺省情况下，大多数新的本机驱动程序都会在安装或升级后启用，但其中有三个新的本机驱动程序会缺省禁用，因为它们并不完全支持对应的 vmklinux 驱动程序的功能。

ixgben 是用于替换 vmklinux net-ixgbe 驱动程序的本机驱动程序，但不支持 SR-IOV 和软件 FcOE。在供应 vSphere ESXi 主机时，ICVS 自动化不会启用此驱动程序。建议您启用此驱动程序，以获取它所带来的性能优势。本附录中描述的以下过程说明了如何使用 vSphere 命令行 (vCLI) 来启用和禁用本机驱动程序。

开始此任务之前，请在 [{{site.data.keyword.cloud}} 基础架构门户网站](https://control.softlayer.com/devices)中检索所有物理主机 IPMI IP 地址、登录标识和密码。如果不存在对主机的直接网络访问，那么在回退中或者检查升级进度时需要这些信息。

对于每个主机，请依次执行以下操作：
1. 使用 vSphere Web Client 通过选择**主页** > **主机和集群**，将 vSphere ESXi 主机置于维护模式。在“导航器”窗格中，选择 vSphere ESXi 主机，然后右键单击该主机，并选择**维护模式** > **进入维护模式**。由于主机是自动 DRS 集群的一部分，因此当主机进入维护模式时，会将虚拟机迁移到其他主机。
2. 使用 IC4VS 控制台中的详细信息，通过 SSH 登录到 vSphere ESXi 主机。
3. 运行以下 vCLI 命令以启用 ixgben 本机驱动程序：
  `esxcli system module set --enabled=true --module=ixgben`
4. 运行以下 vCLI 命令以重新启动 vSphere ESXi 主机：
  `system shutdown reboot --reason “Install ixgben driver”`
5. vSphere ESXI 主机重新引导后，使用 SSH 重新登录到该主机，发出以下 vCLI 命令并检查 ixgben 驱动程序的状态是否为“loaded”（第一列）和“enabled”（第二列）：
  `esxcli system module list |grep ixg`
6. 如果驱动程序已启用，那么通过使用 vSphere Web Client，在“导航器”窗格中选择主机，右键单击并选择**维护模式** > **退出维护模式**。选择下一个主机，并启用驱动程序，直到对所有主机执行完这些操作。
7. 如果更改不起作用，那么要还原，请运行以下命令：
  `esxcli system module set --enabled=false --module=ixgben`

8. 如果无法通过网络连接到主机，请使用 {{site.data.keyword.cloud_notm}} 控制窗口在 IPMI 控制台中运行先前的命令。
9. 重新引导 vSphere ESXi 主机后，现在您会观察到缺省 ixgbe 驱动程序已装入并已启用。

如果需要还原，但无法通过 SSH 登录到 vSphere ESXi 主机，那么您需要通过 {{site.data.keyword.cloud_notm}} 控制窗口登录到需要还原的主机的 KVM 控制台。

将 {{site.data.keyword.cloud_notm}} 控制窗口中列出的标识和密码与 IPMI IP 地址一起使用，以登录到 IPMI Web 界面。您需要通过 VPN 连接到主机所在的数据中心。有关更多信息，请参阅 [VPN 入门](/docs/infrastructure/iaas-vpn/getting-started.html)。

1. 转至 vSphere ESXi 主机的“设备详细信息”>“远程管理”页面，然后选择**操作** > **KVM 控制台**。这将打开另一个窗口，供您输入 IPMI 用户和密码。
2. 选择**远程控制** > **iKVM/HTML5**，然后单击 **iKVM/HTML5** 以重新启动。现在，您能够访问 vSphere ESXi 主机的控制台。
3. 如果主机可响应命令，请在控制台中使用 **ALT-F1** 来访问 ESXi 主机控制台。使用主机的凭证进行登录。
4. 如果主机未响应，请使用 IPMI 菜单来关闭主机的电源再打开。
5. 主机重新启动时，请仔细观察 HTML5 控制台。ESXi 重新启动后，您只有几秒钟时间可进入恢复模式。
6. 同时按 **CMD + R** 键以进入恢复模式。
7. 输入“**Y**”进入恢复模式，并使用先前版本引导 ESXi 服务器。
8. 通过控制台监视其进度。引导可能需要 10 到 20 分钟。

### 相关链接

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解决方案体系结构](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 数字技术互动](https://ibm-dte.mybluemix.net/ibm-vmware)（演示）
