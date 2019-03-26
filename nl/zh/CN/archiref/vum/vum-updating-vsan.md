---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# 更新 vSAN 集群
{: #vum-updating-vsan}

vSAN 会生成系统基线和基线组以与 VUM 配合使用，并且您可以使用这些建议的基线通过 vSAN 来更新 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 实例中 vSphere ESXi 主机的软件、补丁和扩展。vSAN 6.6.1 和更高版本会为 vSAN 集群生成自动构建建议。vSAN 将《VMware 兼容性指南》和 vSAN 发行版目录中的信息与有关已安装的 vSphere ESXi 发行版的信息结合使用。

这些建议的更新提供了最佳可用发行版，从而使您的硬件始终保持受支持的状态。
* **vSAN 系统基线** - 通过 VUM 的 vSAN 系统基线提供 vSAN 构建建议。vSAN 会为每个 vSAN 集群生成一个基线组，这些基线会列在“基线和组”选项卡的“基线”窗格中。VUM 会自动扫描每个 vSAN 集群，以根据基线组来检查合规性。但是，要升级 vSAN 集群，必须通过 VUM 手动修复系统基线，这样才能在单个主机或整个集群上对 vSAN 系统基线进行修复。
* **vSAN 发行版目录** - vSAN 发行版目录维护有关可用发行版、发行版的首选顺序以及每个发行版所需的关键补丁的信息。vSAN 需要因特网连接才能访问发行版目录。您无需在客户体验改善计划 (CEIP) 中注册，就可通过 vSAN 来访问发行版目录。
* 使用 **vSAN 构建建议** - VUM 会根据《VMware 兼容性指南》的“硬件兼容性列表”(HCL) 中的信息来检查已安装的 vSphere ESXi 发行版。它会根据当前的 vSAN 发行版目录来确定每个 vSAN 集群的正确升级路径。vSAN 还会在其系统基线中包含建议发行版的必需驱动程序和补丁更新。vSAN 构建建议可确保每个 vSAN 集群保持当前硬件兼容性状态或更佳状态。如果 vSAN 集群中的硬件未包含在 HCL 中，那么 vSAN 会建议升级到最新发行版。

vSAN 集群升级将按以下顺序执行任务：
* **启用 vSAN 联机运行状况工作流程** - 此工作流程启用 VUM 中的 vSAN 基准，以便可以复查和修复更新。它只需要初始执行，以通过 VUM 启用 vSAN
* **先决条件** - 了解先决条件、过程和限制
* **升级 vCenter Server Appliance** - 有关更多信息，请参阅 [VCSA 更新和 SSO 链接的 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)。
* **升级 vSphere ESXi 主机** - 有关更多信息，请参阅[创建基线并连接到库存对象](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines)。
* **升级 vSAN 磁盘格式** - 请参阅“升级 vSAN 磁盘格式”。升级磁盘格式是可选操作，但为了获得最佳结果，请升级对象以使用最新版本。通过磁盘上格式，环境可使用完整的 vSAN 功能集。

## 启用 vSAN 联机运行状况工作流程
{: #vum-updating-vsan-enable-vsan-workflow}

使用以下部分中的任务使 vSAN 基线在 VUM 中可用。vSAN 6.6.1 和更高版本提供了无缝的自动更新过程，可确保 vSAN 集群通过最佳可用发行版保持最新，从而使 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 实例保持受支持的状态，同时提供：
* **vSAN 版本建议** - 使用《VMware 兼容性指南》、vSAN 发行版目录以及底层硬件配置感知中的信息自动生成。此外，还会在其系统基线中包含建议发行版的必需驱动程序和补丁更新。
* **vSAN 构建建议** - 确保集群保持当前硬件兼容性状态或更佳状态。

确保 VCSA 为 vCenter 6.5 补丁 2 或更高版本，然后再继续，因为这样会修复一些代理使用问题。有关更多信息，请参阅 [VCSA 更新和 SSO 链接的 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)。

要查看 VUM 中的 vSAN 更新，请执行 vSAN 联机运行状况工作流程。因此，vSAN 联机运行状况需要连接到 `vcsa.vmware.com` 和 `vmware.com` 站点以执行这些联机运行状况检查，从而启用 vSAN 联机运行状况工作流程，我们需要执行以下操作：
* 配置 VCSA 以使用代理。
* 配置 vSAN 以使用代理。
* 启用客户体验改善计划 (CEIP)。
* 执行测试上传并验证上传是否有效。

第一步是将 my.vmware.com 凭证添加到 vSAN 构建建议引擎。成功登录后，vSAN 将为每个 vSAN 集群生成建议更新基线组。vSAN 系统基线会列在“基线和组”选项卡的“基线”窗格中。

### 配置 VCSA 以使用代理
{: #vum-updating-vsan-config-vcsa-proxy}

1.	通过跳板机 Web 浏览器连接到 VCSA 管理界面 `https://<vCenter ip>:5480`。
2.	通过使用 IC4VS 控制台中的凭证，以 root 用户身份登录到 VCSA 管理界面。
3.	在 vCenter Server Appliance 管理界面中，单击**联网**，然后单击**管理**。
4.	要配置代理服务器，请在“代理设置”窗格中，单击**编辑**。
5.	选择**使用代理服务器**，输入代理服务器设置，然后单击**确定**。

有报告称，只会为 HTTP 设置代理信息，而不会为 HTTPS 设置代理信息。为了配置也适用于 HTTPS 流量的代理信息，必须先启用 HTTPS。通过 SSH 登录到 VCSA 后，使用 proxy.get 命令来查看配置并确认是否未设置 HTTPS 参数。

如果未设置 HTTPS 参数，请使用以下命令：
  `proxy.set --protocol https --server ``<proxy ip>`` --port 3128`

### 配置 vSAN 以使用代理
{: #vum-updating-vsan-config-vsan-proxy}

1. 浏览至**主页** > **主机和集群**，选择“导航”窗格中的 **vSAN 集群**，选择**配置**选项卡并浏览至 **vSAN**，然后选择**常规**。滚动到**因特网连接**部分，然后单击**编辑**。
2. 输入代理的 IP 地址和端口号，然后单击**确定**。

### 启用客户体验改善计划 (CEIP)
{: #vum-updating-vsan-enable-ceip}

这是可选步骤。使用 vSphere Web Client，浏览至**主页** > **管理** > **客户体验改善计划**，然后单击**加入**。

### 完成测试上传并验证上传是否有效
{: #vum-updating-vsan-complete-upload}

1. 使用 vSphere Web Client，浏览至**主页** > **主机和集群**。选择所需的集群，然后选择**监视**选项卡和 **vSAN** 页面，然后单击**运行状况**。单击**启用联机运行状况**。
2. 单击**重新测试**并等待此过程完成。
3. “运行状况”中会显示名为_联机运行状况连接_的新检查，并且**启用联机运行状况**会更改为**重新测试联机运行状况**。
4. 单击**重新测试联机运行状况**来启动第一次上传，然后通过在“最近的任务”窗格中查看状态来等待此过程完成。“测试名称”会更改为“联机运行状况（上次检查时间：刚才）”。
5. 完成后，在“运行状况”窗口中滚动至“vSAN 构建建议”并将其展开，然后单击 **vSAN 构建建议引擎运行状况**。
6. 单击**登录到 my.vmware.com**，并输入凭证。此过程完成后，**测试结果**将更改为**已通过**状态。
7. 按 **Update Manager** 选项卡，vSAN 集群已添加到“基线”。

## 先决条件
{: #vum-updating-vsan-prereq}

启动 vSAN 升级过程之前，请确保满足以下需求：
* 查看 VMware 知识库文章，并查看当前 vSAN 版本与所需目标 vSAN 版本之间的任何已知兼容性问题
* **vSphere 环境是最新的**：
  - VCSA 的补丁级别必须等于或高于 vSphere ESXi 主机。如果需要，请更新 VCSA
  - 所有主机都必须运行的是相同的 ESXi 构建。如果 vSphere ESXi 主机版本不匹配，请进行更新
* **所有 vSAN 磁盘都应该运行正常**：
  - 没有磁盘处于故障或缺失状态。这可以通过 vSphere Web Client 中的 **vSAN 磁盘管理**视图进行确定。单击**主页** > **主机和集群**，选择 **vSAN 集群**，单击 **vSAN** 选项卡，然后单击**物理磁盘**。滚动浏览所有磁盘并查看 vSAN 运行状态。
  - 没有不可访问的 vSAN 对象。这可以通过 **vSAN 运行状况服务**来进行验证，方法是单击**主页** > **主机和集群**，然后选择 **vSAN 集群**。单击**监视**选项卡，单击 **vSAN**，然后单击**运行状况**。复查测试结果。
  - 在升级过程启动时，没有任何活动的再同步，检查方法是单击**主页** > **主机和集群**，选择 **vSAN 集群**，单击 **vSAN** 选项卡，然后单击**再同步组件**。_再同步组件计数应为 0_。由于数据需要在主机重新启动后同步，因此在升级过程中应该会有一些再同步活动。
* **vSphere ESXi 主机准备** - 在 vSAN 集群中将主机移至维护模式后，有三个选项可供选择：
  - **无数据迁移** - 如果选择此选项，那么 vSAN 不会从此主机转移任何数据。如果关闭主机的电源或从集群中除去主机，那么某些虚拟机 (VM) 可能会变得不可访问。
  - **确保可用性** - 如果选择此选项，那么 vSAN 允许您比“完全数据迁移”更快地将主机移至维护模式，并允许访问环境中的 VM。
  - **完全数据迁移**
* **退出维护模式并再同步** - vSphere ESXi 主机升级并退出维护模式时，将执行再同步。您可以通过 Web 客户机来查看此操作。请确保此操作完成后，再移至下一个主机。由于已更新的主机现在可再次向 vSAN 数据存储提供数据，因此将执行再同步。请务必等待此再同步操作完成，以确保不会发生数据丢失。
* **启动 vSAN 集群升级后**：
  - 请勿尝试通过向集群引入新版本并迁移工作负载来升级集群。
  - 如果引入新主机，请确保它们具有相同的初始版本，并将其与集群的其余主机一起升级。
  - 如果要在升级期间添加或替换磁盘，请确保这些磁盘格式设置为相应的原有磁盘上格式版本（如果适用）。
  - 因此，某些 vSAN 行为更改可通过磁盘上格式进行控制，重要的是不要将新的磁盘上格式版本引入混合版本的集群。

## 升级 vCenter Server Appliance
{: #vum-updating-vsan-upgrade-vcsa}

有关更多信息，请参阅 [VCSA 更新和 SSO 链接的 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)。

##	升级 vSphere ESXi 主机
{: #vum-updating-vsan-upgrade-hosts}

有关更多信息，请参阅[创建基线并连接到库存对象](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines)。

##	升级 vSAN 磁盘格式
{: #vum-updating-vsan-upgrade-vsan}

Ruby vSphere Console (RVC) 是面向 vSphere 的基于 Ruby 的命令行界面，可用于管理 VMware vSphere ESXi 和 vCenter。vSphere 库存以树结构呈现，允许您浏览 vCenter 对象并对其运行命令。

许多基本管理任务的执行效率要比通过 vSphere Client 单击相应任务高得多。RVC 在 VCSA 中完全实现，并通过与设备的 SSH 连接进行归咎。
1. 通过 SSH 连接到 VCSA，并使用 root 用户和 ICVS 控制台上提供的密码登录。
2. 在提示符处输入 `rvc Administrator@vsphere.local@localhost`，然后按 **Enter** 键。
3. 输入在 ICVS 控制台上提供的管理员密码。您现在将位于虚拟文件系统的根目录中，请输入 ls，然后按 **Enter** 键，您会看到：
  `0 /
  1 localhost/``

5. 输入 `cd 1` 并按 Enter 键，然后输入 `ls` 并按 **Enter** 键。您会看到：
  `0 / datacenter1 (datacenter)`

6. 输入 `cd 0` 并按 Enter 键，然后输入 `ls` 并按 **Enter** 键。您会看到：

  `0 storage/
  1 computers [host]/
  2 networks [network]/
  3 datastores [datastore]/
  4 vms [vm]/`

7. 输入 `cd 1` 并按 **Enter** 键，然后输入 `ls` 并按 **Enter** 键。您会看到集群：
  `0 cluster1 (cluster)``

8. 针对此集群使用 VSAN 命令。要检查磁盘状态，请输入 `vsan.disks_stats 0` 并按 **Enter** 键。

9. 确保所有磁盘的“运行状态”均为“正常”。然后，通过输入 `vsan.ondisk_upgrade 0` 并按 **Enter** 键来启动升级。

10. 此任务可能需要很长时间，具体取决于 vSAN 的大小。完成后，请输入 `vsan.objstatusreport 0` 并按 **Enter** 键来验证对象版本是否已升级为新的磁盘上格式。

11. 现在，vSAN 集群升级已完成。请输入 `exit` 并按 **Enter** 键以退出 RVC。

## 相关链接
{: #vum-updating-vsan-related}

* [VMware HCX on IBM Cloud 解决方案体系结构](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud 数字技术互动](https://ibm-dte.mybluemix.net/ibm-vmware)（演示）
