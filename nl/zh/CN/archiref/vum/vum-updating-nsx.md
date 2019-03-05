---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# 更新 NSX

以下信息是 NSX 更新过程的示例。有关针对要升级到的 NSX 版本的相应更新过程，请参阅 VMware 指南。

如果您需要升级 NSX 和 vSphere，那么 VMware 建议先完成 NSX 升级，再完成 vSphere 升级，因为 NSX VIB 会特定于主机上安装的 ESXi 的版本。但是，如果手动执行以下工作流程，那么建议使用 VUM（如本文档中所述），一次处理一个主机：

1. **升级 ESXi** - ESXi 升级完成后，主机会退出维护模式，但是，要到下一步完成后，才能将连接到逻辑交换机的 VM 移至主机。
2. **升级 NSX VIB** - VIB 已升级并且主机已退出维护模式后，可以将连接到逻辑交换机的 VM 移至主机。

通过使用从 _my.vmware.com_ 下载的更新来更新 NSX Manager，从而可更新 NSX。为此，您需要帐户来下载更新。如果您是将 {{site.data.keyword.cloud}} 预订许可用于 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 实例，那么无法使用 **my.vmware.com** 帐户下载更新。因此，您需要[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic/trbl_support.html)。

开始升级之前，请查看 NSX 说明以了解升级问题和解决方法。使用发行说明验证 vCenter 是否满足 NSX 的新系统需求。

如果已安装 VMware 业务合作伙伴提供的其他任何软件，请参阅业务合作伙伴文档以了解兼容性和升级详细信息。如果已部署 vCenter Server 主实例和辅助实例，并具有跨 vCenter NSX 环境，请参阅发行说明以了解正确的升级过程。

在跨 vCenter NSX 环境中，会首先更新主 NSX Manager 设备，然后更新所有辅助 NSX Manager 设备。**不支持降级**，因此在继续升级之前，请先备份 NSX Manager；所有 NSX Edge 配置、逻辑路由器和 Edge 服务网关都会作为 NSX Manager 备份的一部分进行备份。

NSX Manager 成功升级后，无法对 NSX 降级。建议您在商定的维护时段内执行任何维护活动，因此，请遵循您的企业指南进行操作。建议在一个中断时段内升级所有 NSX 组件，以最大程度地缩短停机时间，减少功能问题。NSX 升级过程可能需要一些时间，因此了解 NSX 部署升级顺序很重要：
* NSX
Manager
* NSX Controller 集群
* NSX 主机集群
* 在 NSX Manager 升级后，可以随时升级 Edge 服务网关
* 访客自省（如果使用），请遵循发行说明中的相关指示信息

工作流程如下：
1. 登录到跳板机，然后打开浏览器。
2. 使用您的 _my.vmware.com_ 凭证，浏览至下载部分，然后搜索 _NSX for vSphere_。
3. 选择所需的版本。
4. 在下载页面上，选择**升级捆绑软件 - 立即下载**。
5. 下载到合适的文件夹。
6. **升级 NSX Manager**：
  - 通过使用 IC4VS 控制台中记录的 IP 地址和凭证，登录到 NSX Manager 虚拟设备，然后单击主页上的“升级”按钮。
  - 登录到 NSX Manager。
  - 在**设备管理**下，单击**备份和复原**。
  - 单击“备份”并输入相应的文件名。VMware 建议您在复原 NSX Manager 数据之前重新安装 NSX Manager 设备。虽然对现有 NSX Manager 设备的复原操作可能会正常工作，但此操作并未受到正式支持。最佳做法是记下 NSX Manager 设备的 IP 设置，以便可以使用这些设置来指定新部署的 NSX Manager 设备的 IP 信息和备份位置信息。
  - 单击右上角的**上传捆绑软件**，并上传从 _my.vmware.com_ 下载的文件。
  - 阅读升级信息，并选择是否要启用 SSH 并参与“VMware 客户体验改进计划”。
  - 单击**升级**。
  - 上传完成后，会将您重定向到 NSX Manager 登录页面。请重新登录，并验证当前软件版本的显示是否正确。
7. **升级 NSX Controller 集群**：
  - 打开 vSphere Web Client 并登录到 VCSA。
  - 浏览至**主页** > **联网和安全性** > **安装**，选择**管理**选项卡，然后单击“控制器集群状态”列中的**升级可用**。
  - 环境中的控制器会升级并重新引导（每次处理一个控制器）。启动升级后，系统会下载升级文件，升级每个控制器，重新启动每个控制器，然后更新每个控制器的升级状态。
8. **升级 NSX 主机集群**：
  - 升级 NSX Manager 和 NSX Controller 后，主机集群将更新 vSphere ESXi 主机上的 NSX VIB。
  - 在 vSphere Web Client 中，浏览至**主页** > **联网和安全性** > **安装**，然后选择**主机准备**选项卡。对于要升级的每个集群，单击**升级可用**。安装状态会显示为“正在安装”。
  - 集群安装状态会显示_未就绪_。单击**未就绪**以显示更多信息，然后单击**全部解决**以尝试完成 VIB 安装。主机会置于维护模式并根据需要重新引导以完成升级。“安装状态”列会显示“正在安装”。升级完成后，“安装状态”列会显示绿色复选标记和升级的 NSX 版本。
9. **Edge 服务网关**：
  - 在升级过程中，将随现有 Edge 虚拟设备一起部署一个新的 Edge 虚拟设备。新 Edge 准备就绪时，旧 Edge 的 vNIC 会断开连接，并且新 Edge 的 vNIC 处于连接状态。然后，新 Edge 会发送免费 ARP (GARP) 包来更新已连接交换机的 ARP 高速缓存。部署 HA 后，将执行两次升级过程。此过程可能会暂时影响包转发。
  - 在 vSphere Web Client 中，选择**联网和安全性** > **NSX Edge**。对于每个 NSX Edge 实例，从**操作**菜单中选择**升级版本**。
  - NSX Edge 成功升级后，“状态”为“已部署”，并且“版本”列会显示新的 NSX 版本。如果 Edge 升级失败，并且未回滚到旧版本，请单击**重新部署 NSX Edge** 图标，然后重试升级。

### 相关链接

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解决方案体系结构](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 数字技术互动](https://ibm-dte.mybluemix.net/ibm-vmware)（演示）
