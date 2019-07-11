---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: vSphere upgrade, NSX upgrade, PSC upgrade

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 将 vCenter Server vSphere 软件从 VMware vSphere 6.5 升级到 6.7
{: #vc_vsphere_upgrade}

vCenter Server on {{site.data.keyword.cloud}} 产品是用于 VMware vSphere SDDC 堆栈的完全自动化部署解决方案，包括 vSphere、NSX 和可选的 vSAN 产品。虽然 vCenter Server 会自动执行部署、扩展和收缩基于 VMware SDDC 的基础架构中最困难的部分，但它并不是受管服务。由于 vCenter Server 有策略来支持在 N-1 范围内自动控制 VMware SDDC 软件版本，因此要继续受益于 {{site.data.keyword.vmwaresolutions_short}} 自动化，必须升级 vCenter Server 的现有实例。

不在自动化支持所需级别范围内的 vCenter Server 版本仍将根据 VMware 支持策略的要求受到支持，但无法再通过 {{site.data.keyword.vmwaresolutions_short}} 自动化运作。您必须在 vCenter Server 实例的生命周期内，对 VMware 软件定期进行修补和升级。这包括根据需要将 VMware SDDC 软件升级到 {{site.data.keyword.vmwaresolutions_short}} 自动化支持的版本。

以下过程提供了将基于 vCenter Server VMware vSphere 6.5 的实例转换为基于 vCenter Server VMware vSphere 6.7 的实例所需的步骤。这些步骤提供了初始升级到最新 6.7 级别的 vSphere、NSX 和 vSAN 的过程。在此升级之后，您可能需要使用正常 vSphere 功能来升级虚拟机 (VM) 硬件级别和工具。

vCenter Server 设计为支持“滚动”升级。即，如果完成以下过程，那么当前正在运行的 VM 工作负载会继续运行，不会发生中断。企业必须参与其变更管理策略，以就升级进行安排和沟通，并制定应急计划。但是，在某些管理功能（如 vCenter 和 NSX Manager）的升级过程中，可能会有一定影响，例如临时中断管理功能、配置更改以及关闭 VM 电源和打开 VM 电源。
{:note}

## 开始之前
{: #vc_vsphere_upgrade-prereq}

执行升级的估计时间未知。可能需要多个维护时段才能对环境完全升级。在升级过程中，VMware 支持运行 SDDC 软件的高级别和低级别版本。但是，某些功能（如 vMotion）在此过程中可能会受限。

开始升级之前，请先满足以下需求：  
* 您负责在 vCenter Server 环境中升级任何扩展或插入件。在规划升级之前，请查看以下文档：
  * [VMware vCenter Server 6.7 Update 1b Release Notes](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:new_window}
  * [About VMware ESXi Upgrade](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:new_window}
* 在 vCenter Server 实例中设置 vSphere Update Manager (VUM)，以从 VMware vSphere 下载最新更新。有关更多信息，请参阅 [VMware Update Manager 简介](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro)。
* 向 {{site.data.keyword.vmwaresolutions_short}} 团队开具支持凭单，以通知他们将执行升级。该凭单会保持待处理状态，直到实例在 {{site.data.keyword.vmwaresolutions_short}} 控制台中以升级后的级别注册。
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，确认要升级的 vCenter Server 实例是作为主实例还是辅助实例链接到其他 vCenter Server 实例。在特定站点升级过程中，所有链接的实例都必须首先升级其 Platform Services Controller (PSC)。
* 对于基于 vSAN 的实例，确认以下内容：
  * 确保 vSAN 运行状况工具已启用，并且未报告任何严重错误。如果存在严重错误，请联系 IBM 支持团队并提供升级支持凭单标识。
  * 如果在升级期间 ESXi 主机未能恢复正常运行，请确保每个节点上都有空间来处理 vSAN 对象的重建冗余。在升级之前，您可能需要减少磁盘使用量或添加额外的 ESXi 主机。  
  * 验证总体 vSAN 卷的利用率是否已超过 70%。在升级之前，您可能需要减少磁盘使用量或添加额外的 ESXi 主机。
* 如果 vCenter Server 实例是从 {{site.data.keyword.vmwaresolutions_short}} V2.5 或更高版本开始的，那么必须联系 IBM 支持人员来获取 PSC 和 vCenter 的 **root** 用户标识密码，因为只有具有 **customerroot** 访问权的服务帐户才可在门户网站上显示。如果显示了 PSC 和 vCenter 的 **root** 用户标识及其密码，那么此步骤不是必需的。
* 确认您是否具有 https://my.vmware.com 用户标识，以为其下载必需的升级二进制文件。如果没有，请联系 IBM 支持人员并提供升级支持凭单标识。
* 确认 VUM 是否配置为访问 https://www.vmware.com 来下载补丁。如果由于安全策略而无法对 VUM 进行配置，那么必须手动下载最新的补丁集，然后将其上传到 VUM。有关更多信息，请参阅 [VMware Update Manager 简介](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro)。

### 准备跳板机
{: #vc_vsphere_upgrade-prereq-jumpbox}

由于 {{site.data.keyword.cloud_notm}} 客户机访问 VPN 限制为 512 Kbps，因此建议您供应 {{site.data.keyword.cloud_notm}} Windows 2012-2016 Server 虚拟服务器实例 (VSI)，或在同一 {{site.data.keyword.CloudDataCent_notm}} 中的单独 vSphere vCenter Server 环境中设置类似的 Windows VM。这将用作要升级的 vCenter Server 实例中的跳板机，并支持从 https://my.vmware.com 快速下载二进制文件。虽然可以将此 VM 放置在要升级的 vCenter Server 实例上，但建议不要这样做。

要订购 VSI 跳板机，请完成以下步骤。

如果环境中已有 VSI 跳板机，请跳过第一步。
{:note}

1. 在 [IBM Cloud 基础架构客户门户网站](https://control.softlayer.com/)中订购每小时或每月 VSI。订购以下属性：
  * Windows 2012 或 2016 Server Standard
  * 2 个 CPU
  * 16 GB 内存
  * 100 G 磁盘
  * 1 Gbps 公共和专用上行链路
2. 供应 VSI 时，请在控制面板中配置 {{site.data.keyword.cloud_notm}} 访问控制表 (ACL)，以允许专用链路的所有流入和流出流量，但仅允许公共链路的流出流量。必须使用 {{site.data.keyword.cloud_notm}} 客户机访问 VPN 将远程桌面协议 (RDP) 会话连接到 Windows VSI。
3. 通过 RDP 连接到 Windows VSI。在专用网络适配器上修改其域名系统 (DNS) 设置，以仅指向要升级的 vCenter Server 实例中的 Windows AD 服务器。
4. 下载并安装 Google Chrome 浏览器。可以使用 Mozilla Firefox，但在使用 vCenter 用户界面中的 VUM 屏幕时，会发生高速缓存问题。
5. 下载首选的 SSH 终端软件。例如，Putty。
6. 使用 Google Chrome 来访问要升级的 vCenter Server 实例。使用 **administrator@vsphere.local** 并确保可以查看用户界面。  
7. 检查 vSphere 环境中是否存在先前部分中讨论的错误和问题。
8. 使用 SSH 终端软件，通过门户网站或支持人员为 **root** 用户提供的密码来访问 PSC 和 vCenter。
9. （可选）使用 SL 控制面板中说明的 **root** 用户标识和密码来访问每个 ESXi 主机，以验证 **root** 用户密码。

#### 下载二进制文件
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

使用 Windows VSI 跳板机并登录到您的 https://my.vmware.com 帐户，以下载下列二进制文件：

* VMware vSphere 6.7u1 系统管理程序 (ESXi ISO) 映像（包括 VMware Tools）
* vCenter 6.7u1b 设备 ISO。不是更新捆绑软件。
* NSX for vSphere 6.4.4 升级捆绑软件

对于 Intel Optane 驱动器，下载以下文件以在利用 VMware Update Manager 的升级后修补过程中使用。

在 https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742 上，找到用于 Intel® Optane™ SSDDC P4800X 系列 SSDPED1K750GA（750 GB，HHHL）的 Intel NVMe 驱动程序的 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 文件。

#### 备份组件

开始升级之前，请备份每个组件。

* 有关备份 vCenter Server 和 PSC 的信息，请参阅 [vCenter Server 6.x 中备份和复原选项概述 (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window}。
* 有关备份 vCenter Server 和 PSC 的其他注意事项和信息，请参阅 [vCenter 基于文件的备份](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter)。
* 有关备份 NSX 的信息，请参阅 [Backing Up NSX Manager Data](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}。

建议使用基于文件的备份。VMware VSphere 6.7 中不支持基于映像的备份（使用 vSphere Data Protection）。
{:note}

## 将 IBM vCenter Server vSphere 软件从 6.5 升级到 6.7 的过程
{: #vc_vsphere_upgrade-procedure}

如果在升级过程中任何时候遇到问题，请使用在过程开始时开具的 {{site.data.keyword.vmwaresolutions_short}} 升级凭单来联系 IBM 支持人员。IBM 支持人员会根据需要，向 VMware 支持人员开具凭单。

**重要信息**：

* 您必须使用此途径来确保 {{site.data.keyword.vmwaresolutions_short}} 为 VMware 支持人员提供其所需的有关 vCenter Server 设计和设置的所有信息以及 {{site.data.keyword.cloud_notm}} 信息。遵循此过程来确保与 VMware 支持人员共享准确的信息，从而加快支持体验。IBM 支持人员向 VMware 支持人员提供必要的信息后，您可以根据需要直接与 VMware 支持人员进行交互。

* 确保记录此升级过程中创建的所有新密码和凭证。IBM 支持人员在升级过程结束时需要这些凭证以更新其内部数据库。

### 升级 VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx}

升级 VMware NSX 可能需要一些时间，因为升级过程会更新 ESXi 主机上的 vSphere 安装捆绑软件，并且需要重新引导每个主机。请相应地规划维护时段。

#### 升级 VMware NSX 之前
{: #vc_vsphere_upgrade-procedure-nsx-before}

* 如果在环境中安装了 Zerto for {{site.data.keyword.cloud_notm}}，请使用 Zerto 用户界面来关闭每个主机上的 zVRA VM。在 Zerto 用户界面的“策略”部分中，选中 Zerto 站点设置中的**允许 Zerto 在修复过程中始终使主机进入维护模式**。否则，Zerto 会启动 zVRA，并通过不允许要升级的 ESXi 主机进入维护模式而阻止升级继续。
* 对于未安装 VMware Tools 的 VM，请在 NSX ESXi 主机模块安装之前，手动关闭这些 VM 或强制关闭其电源。这些 VM 会使目标 ESXi 主机无法进入维护模式。

#### 升级 VMware NSX 的过程
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

有关以下过程的相关详细信息，请参阅 [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}。

1. 请阅读 NSX 6.4.4 的发行说明，以确保与特定环境配置的兼容性。有关更多信息，请参阅 [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}。
2. 首先升级 NSX Manager。如果有多个 NSX 环境使用交叉 vCenter 链接方式，请在 NSX 用户界面的**升级协调程序**中升级组件之前，先升级所有 NSX Manager。
3. 使用 vCenter 用户界面的 NSX 用户界面中的**升级协调程序**来升级 NSX 组件。
4. 在解决了可能的问题之后，继续在 vCenter 用户界面中复查并监视 NSX 升级用户界面，以确保升级继续执行，直到所有组件均已升级为止。

### 升级 Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc}

如果您有 vCenter Server 链接的实例，那么必须升级 vCenter Server 主站点和辅助站点中的所有 PSC 实例。由于链接的 vCenter Server 实例会创建轴辐式 PSC 复制拓扑，其中主 vCenter Server 实例作为主数据中心，因此建议您首先升级主 vCenter Server 实例 PSC，然后再升级每个辅助站点 PSC。

#### 升级 Platform Services Controller 之前
{: #vc_vsphere_upgrade-procedure-psc-before}

* 使 vCenter 和 PSC root 用户密码可用于以下过程。使用 {{site.data.keyword.vmwaresolutions_short}} 控制台来确定 vCenter Server 实例版本是否已从 V2.4 或更低版本升级到 V2.7 或更高版本。
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台上，将针对 PSC 和 vCenter 显示同一个 root 用户密码。但是，这只是 vCenter 密码。您必须[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)以获取 root 用户的 PSC 密码。
* 为了避免冲突，请使用 vCenter 和 PSC 当前正在使用的同一子网高段中的 IP 地址。对于新的设备部署，必须使用临时 IP 地址。

#### 升级 Platform Services Controller 的过程
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. 登录到 PSC `https://<psc-fqdn>:5480` 和 vCenter 设备管理用户界面，以确认 root 用户密码是否已到期。如果密码到期日期为 **1970**，说明密码已到期，因此您必须在 PSC 设备管理用户界面中启用 SSH 和 bash shell。
    1. 使用 root 用户标识和密码通过 SSH 登录到 PSC。尽管密码已到期，也仍然允许您登录。
    2. 使用 shell **passwd** 命令为 PSC 和 vCenter 设置新的 root 用户密码。
    3. 保存 {{site.data.keyword.vmwaresolutions_short}} 控制台上显示的密码或由 IBM 支持人员提供给您的密码。稍后升级设备时，将复用这些密码。
2. 使用内置的 Windows ISO 安装功能在跳板机中安装 vCenter 6.7u1b ISO。
3. 遵循 VMware 指示信息以首先升级所有 PSC。有关更多信息，请参阅 [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html)。

其中，声明的需求 **You must run the GUI upgrade from a Windows, Linux, or Mac machine that is in the same network as the appliance that you want to upgrade**（必须从与要升级的设备位于同一个网络的 Windows、Linux 或 Mac 计算机运行 GUI 升级）适用于您帐户中 {{site.data.keyword.cloud_notm}} 内的任何子网。
{:note}

建议使用 vCenter 作为升级的源和目标。

### 升级 vCenter
{: #vc_vsphere_upgrade-procedure-vcenter}

对于 vCenter Server 链接的实例，虽然建议升级 vCenter Server 主站点和辅助站点中的所有 vCenter 实例，但这并不是必需的。

#### 升级 vCenter 之前
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* 使 vCenter 和 PSC root 用户密码可用于以下过程。使用 {{site.data.keyword.vmwaresolutions_short}} 控制台来确定 vCenter Server 实例版本是否已从 V2.4 或更低版本升级到 V2.7 或更高版本。
* 为了避免冲突，请使用 vCenter 和 PSC 当前正在使用的同一子网高段中的 IP 地址。对于新的设备部署，必须使用临时 IP 地址。

#### 升级 vCenter 的过程
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. 登录到 PSC ``https://<psc-fqdn>:5480`` 和 vCenter 设备管理用户界面，以确认 root 用户密码是否已到期。如果密码到期日期为 **1970**，说明密码已到期，因此您必须在 PSC 设备管理用户界面中启用 SSH 和 bash shell。
    1. 使用 root 用户标识和密码通过 SSH 登录到 PSC。尽管密码已到期，也仍然允许您登录。
    2. 使用 shell **passwd** 命令为 PSC 和 vCenter 设置新的 root 用户密码。
    3. 保存 {{site.data.keyword.vmwaresolutions_short}} 控制台上显示的密码或由 IBM 支持人员提供给您的密码。稍后升级设备时，将复用这些密码。
2. 使用内置的 Windows ISO 安装功能在跳板机中安装 vCenter 6.7u1b ISO。
3. 遵循 VMware 指示信息以升级 vCenter。有关更多信息，请参阅 [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html)。VMware 指示信息类似于 PSC 的升级过程。但是，对于升级过程，请指向 vCenter FQDN/IP，而不是指向 PSC。

**注**：
* 其中，声明的需求 **You must run the GUI upgrade from a Windows, Linux, or Mac machine that is in the same network as the appliance that you want to upgrade**（必须从与要升级的设备位于同一个网络的 Windows、Linux 或 Mac 计算机运行 GUI 升级）适用于您帐户中 {{site.data.keyword.cloud_notm}} 内的任何子网。

* 建议使用 vCenter 作为升级的源和目标。

#### 将 PSC 功能合并到 vCenter 中

1. 成功完成 PSC 和 vCenter 升级后，登录到基于 vCenter FLEX 的用户界面，然后在**系统配置**部分中，检查与 vCenter 和 PSC 相关的所有服务的运行状况。  
2. 备份 PSC。建议使用基于文件的备份。有关更多信息，请参阅 [vSphere 6.7 中基于文件的备份](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:new_window}。
3. 导航至 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge`` 目录。
4. 将 ``converge.json`` 文件复制到跳板 VM 上的本地驱动器。
  * 如果这是第一个要合并的 PSC，那么必须从 ``json`` 文件中除去 **replication** 部分。
  * 如果这是后续链接的 PSC，那么必须在 ``json`` 文件的 **replication** 部分中填写请求的属性。
5. 导航至 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission`` 目录。
6. 将 ``decommission_psc.json`` 文件复制到跳板 VM 上的本地驱动器。
7. 编辑 ``converge.json`` 和 ``decommission_psc.json`` 文件。有关要编辑的字段的指示信息位于这些 ``json`` 文件中。建议在 **managing_esxi_or_vc** 部分中使用包含 PSC 的 ESXi 主机，而不要使用 vCenter。
8. 在命令窗口中，导航至 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` 目录。
9. 运行 ``vcsa-util.exe``，命令中包含 **converge** 开关和先前编辑的 ``converge.json`` 文件的路径。例如，``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``。
   1. 输入 **Y** 以确认 PSC 已备份，然后继续。
   2. 过程完成后，输入 **Y** 以确认重新引导 vCenter。

   如果聚合过程失败，且显示 ``ERROR converge Failed to get vecs users and permissions`` 消息，请参阅 [Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:new_window}，以获取解决此错误的步骤。
   {:note}

10. 重新引导 vCenter 后，通过登录到 vCenter 用户界面来验证运行是否正常。
11. 在命令窗口中，导航至 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` 目录。
12. 运行 ``vcsa-util.exe``，命令中包含 **decommission** 开关和先前编辑的 ``decommission_psc.json`` 文件的路径。例如，``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``。
13.	命令成功完成后，登录到 vCenter Flex 用户界面，验证 vCenter 设备是否是在非链接环境中列出的唯一设备，并且验证是否所有服务都在正常运行。
14. 删除原先的 PSC、vCenter 和不使用的已合并 PSC VM。
15. 将 vCenter 用户界面中的 vCenter Server 重命名为 **<instancename>_vc_separate**。例如，如果 vCenter Server 实例名称为 **production**，那么在 vCenter 用户界面中的名称为 **production_vc_separate**。此操作是必需的，这样自动化才可恢复其对此 vCenter Server 实例的功能。  

### 升级 ESXi 主机
{: #vc_vsphere_upgrade-procedure-esxi}

vCenter 中的 VMware Update Manager 功能用于将 ESXi 主机升级并修补到 6.7u1 级别。与本文档的 NSX 升级部分类似，任何无法通过 vMotion 迁移到其他主机的 VM 必须正常关闭而不发生问题，否则可能会导致升级过程停止。
{:note}

#### 将 ESXi ISO 上传到 VUM
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. 确保将 VUM 配置为从 https://www.vmware.com 下载补丁。有关更多信息，请参阅 [VMware Update Manager 简介](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction)。
2. 使用 Flex 或 HTML 来打开 vCenter 用户界面，并导航至 **VUM 管理视图**。
3. 在 **VUM 管理视图**中，选择 **ESXi 映像**选项卡，然后选择**导入 ESXi 映像**。
4. 浏览以查找从 VMware 下载的 **ESXi 6.7u1iso** 映像，然后将其导入到 VUM 存储库。

#### 升级 ESXi 主机的过程
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. 在 vCenter 用户界面中，导航至包含要升级的 ESXi 主机的集群。
2. 单击导航面板中的**更新**选项卡。转至主机更新并单击**连接**。
3. 选择已上传到 VUM 的基线（适用于 ESXi 升级的 ISO 映像）并单击**修复**。
4. 接受“最终用户许可协议”并单击**确定**。
5. 查看要修复的主机并确认预先修复检查结果。

   必须将任何连接到 VM 的 CD 或 DVD 分离，否则将不允许包含该 VM 的主机进入维护模式。
   {:note}

6. 预先修复检查成功后，单击**修复**。使用修复实体任务监视升级过程。
7. 升级完成后，查看主机的摘要部分以确认是否显示了 ``VMware ESXi, 6.7.0``。

如果升级过程立即失败并显示**主机无法进入维护模式**错误消息，请关闭 Zerto ZVA，然后重试。在每个服务器退出修复后，ZVRA VM 会自动启动。有关在升级过程中继续 Zerto 复制的信息，请参阅 [How to Place a Host with an Associated VRA into Maintenance Mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:new_window}。
{:note}

#### 向 VUM 存储库添加 Intel NVME 驱动程序补丁
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

如二进制文件下载部分中所述，必须将 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 文件的内容导入到存储库。然后，在后续部分中会将其作为非关键 ESXi 主机扩展来应用。

1. 将 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 文件解压缩到跳板 VM 上的本地驱动器。
2. 使用 Flex 或 HTML 来打开 vCenter 用户界面，并导航至 **VUM 管理视图**。
3. 在 **VUM 管理视图**中，选择**补丁存储库**选项卡，然后选择**导入补丁**。
4. 浏览以查找 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 目录的解压缩内容，然后选择 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip`` 文件。该文件会立即导入到 VUM 存储库。

在补丁存储库中找到作为**重要**主机扩展的该映像。

#### 修补 ESXi 主机
{: #vc_vsphere_upgrade-procedure-esxi-patch}

升级后，建议您应用所有关键和非关键的 ESXi 主机补丁。

1. 在 vCenter 用户界面中，选择包含要应用补丁的主机的集群。
2. 单击导航面板中的**更新**选项卡，并选择**主机更新**选项卡。选择**关键主机补丁（预定义）**。重复此过程以升级 ESXi 主机。
3. 单击导航面板中的**更新**选项卡，并选择**主机更新**选项卡。选择**非关键主机补丁（预定义）**。重复此过程以升级 ESXi 主机。

在此过程中，您可能需要再次关闭 Zerto zVRA VM。
{:note}

### 升级其他项
{: #vc_vsphere_upgrade-procedure-addtl}

#### 升级 vSAN 磁盘上格式版本
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

将 vSAN 磁盘上格式版本升级到 V7。

1. 在 vCenter 用户界面中导航至包含要升级的 vSAN 的集群。
2. 在集群对象中，选择**配置 > vSAN > 常规**。
3. 单击**预检查升级**，以检查升级兼容性和可能的问题。等待检查返回**升级准备就绪...**。
4. 单击**升级**。由于升级一次处理一个磁盘组，因此可能需要一些时间才能完成，具体取决于集群的大小。（可选）在此过程中，可选择**减少冗余**。虽然选择此项可以显著缩短升级所用的时间，但如果在升级过程中发生磁盘故障，可能会导致数据丢失。

#### 升级虚拟分布式交换机
{: #vc_vsphere_upgrade-procedure-addtl-vds}

将虚拟分布式交换机 (VDS) 升级到 V6.6.0 还会升级网络 I/O 控制，并添加增强的链路聚集控制协议 (LACP) 支持。

1.	如果已部署 HCX，那么必须先取消部署 HCX 的 Cloud Gateway 部分，然后再升级它所在的 VDS。请确保在重新部署 Cloud Gateway 之前，HCX 已更新为最新版本。
2.	在 vCenter 用户界面中，导航至**网络**选项卡。
3.	右键单击要升级的分布式交换机（**SDDC-Dswitch-Private** 或 **SDDC-Dswitch-Public**），然后选择 **升级分布式交换机**。

#### 升级 vCenter 用户界面扩展和插件
{: #vc_vsphere_upgrade-procedure-addtl-extension}

您负责在 vCenter Server 环境中升级任何扩展或插入件。在 vCenter 用户界面中，单击**主页 > 管理 > 解决方案**以查看状态，并启用或禁用 vCenter 扩展和插件。

#### 升级 VMware Tools
{: #vc_vsphere_upgrade-procedure-addtl-tools}

使用 vCenter 用户界面来执行 VMware 访客工具升级。在已迁移到 vCenter Server 环境的某些较旧 VM 上，可能需要某些 VMware 工具。  

#### 升级虚拟机硬件级别
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

与 VMware 访客工具类似，vCenter Server 环境升级可能会导致较旧的 VM 在其当前硬件级别处于不受支持的状态。使用 vCenter 用户界面根据需要查找和更新这些 VM。  

#### 将“增强 vMotion 兼容性”方式设置为 Intel Skylake
{: #vc_vsphere_upgrade-procedure-addtl-evc}

您可以使用 Intel Skylake 生成设置主机，以便集群在升级后进入 Skylake“增强 vMotion 兼容性 (EVC)”方式。使用以下步骤以更新 EVC 方式：

1. 从包含主机的集群，单击**配置**。
2. 从 **VMware EVC** 单击**编辑**，将 EVC 方式更改为 **Intel Skylake 生成**。

有关更多信息，请参阅[增强 vMotion 兼容性 (EVC) 处理器支持 (1003212)](https://kb.vmware.com/s/article/1003212){:new_window}。

#### 重新配置 NSX Manager 和 HCX Manager 以指向 PSC

1. 从 Web 浏览器，导航至 NSX Manager 设备用户界面，网址为 ``https://<nsx-manager-ip>`` 或 ``https://<nsx-manager-hostname>``。使用凭证登录。
2. 从主页单击**管理 vCenter 注册**。
3. 编辑**查找服务 URL** 以指向 vCenter IP。使用嵌入式 **PSC doesn’t exist anymore** PSC 单机。

## 升级 vCenter Server vSphere 软件后的结果
{: #vc_vsphere_upgrade-results}

升级完成后运行 vSAN 运行状况检查可能会导致出现 IBM Cloud 提供的 RAID 和网络控制器的固件更新相关警告。确定需要固件更新的主机后，请向 IBM 支持人员开具凭单，以将固件更新为建议的版本。

1. 在 vCenter 用户界面中，选择包含要检查其运行状况的 vSAN 的集群。
2. 选择**监视**选项卡，然后选择 **vSAN** 选项卡。
3. 选择**运行状况**并记下显示的任何警告。
4. 如果显示**硬件兼容性**警告，请展开警告并单击**控制器固件是 VMware 认证的固件**消息（如果处于警告状态）。
5. 记下其中列有固件更新建议的主机。
6. 向 IBM 支持人员开具凭单，从而安排使各个主机停止服务以允许进行固件更新的时间。

升级完成后，请向 IBM 支持人员更新支持凭单。提供在此升级过程中创建的新密码。例如，在支持凭单中提供密码以部署设备管理服务 -PSC 和 vCenter。然后，IBM 支持人员会更新 {{site.data.keyword.vmwaresolutions_short}} 控制台和内部数据库以恢复 6.7 级别的 {{site.data.keyword.vmwaresolutions_short}} 自动化。这包括添加和除去服务、主机、集群和辅助 vCenter Server 实例。

## 相关链接
{: #vc_vsphere_upgrade-related}

* [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}
* [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
