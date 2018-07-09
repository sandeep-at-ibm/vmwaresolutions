---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# 订购 VMware Federal 实例

要部署灵活且可定制的 VMware 虚拟化平台，以最适合您的工作负载需求，请订购 VMware Federal 实例来支持将打开的管理连接断开连接并确保已部署实例的安全。

**注**：目前仅 vCenter Server 实例支持 VMware Federal on {{site.data.keyword.cloud}}。

## 需求

确保已完成以下任务：
* 已在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。有关更多信息，请参阅[管理用户帐户和设置](../vmonic/useraccount.html)。
* 已查看[针对 VMware Federal 实例的需求和规划](vc_fed_planning.html)中的信息。
* 已复查实例和域名格式。域名和子域标签用于生成实例的用户名和服务器名称。

表 1. 实例和域名的值格式

|名称|值格式|
  |:------------- |:------------- |
  |域名| `<root_domain>` |  
  |vCenter Server 登录用户名| `<user_id>@<root_domain>`（Microsoft Active Directory 用户）或 `administrator@vsphere.local`|
  |vCenter Server FQDN|`vcenter.<subdomain_label>.<root_domain>`. 最大长度为 50 个字符。|
  |Single Sign-On (SSO) 站点名称| `<subdomain_label>` |
  |标准 ESXi 服务器名称| `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中 `<n>` 是 ESXi 服务器的序列。最大长度为 50 个字符。|  
  |PSC FQDN|`psc-<subdomain_label>.<subdomain_label>.<root_domain>`. 最大长度为 50 个字符。|

**重要信息**：不要修改在订购和实例部署期间设置的任何值。这样做可能会导致实例变得不可用。例如，公用网络可能会关闭，在供应期间服务器和虚拟服务器实例 (VSI) 可能会移至 Vyatta 后，或者 IBM CloudBuilder VSI 可能会停止或被删除。

## 系统设置

订购 VMware Federal 实例时，必须指定以下系统设置。

### 实例名称

实例名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 实例名称必须以字母数字字符开头和结尾。
* 实例名称的最大长度为 10 个字符。
* 实例名称在您的帐户中必须唯一。

### 主实例或辅助实例

订购新的主实例。目前不支持部署辅助实例来实现高可用性。

## 许可证设置

用于以下各项的 IBM 提供的 VMware 许可证：

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition（Base、Advanced 或 Enterprise）6.3
* （对于 vSAN 集群）VMware vSAN Advanced 或 Enterprise 6.6

**注意：**

* 用户界面上指示了最低许可证版本。如果支持不同的组件版本，那么可以选择所需的版本。您负责确保提供的许可证密钥对于选择的每个 VMware 组件都正确。
* 对于 vSphere，在订购时将发生许可费用，但随后会将该许可费用计入您的帐户。

## 裸机服务器设置

裸机设置基于您的定制配置。目前不支持用于选择预配置的配置的选项。

### 数据中心位置

选择要托管实例的 IBM Cloud Data Center。

### 定制

指定用于裸机服务器的 CPU 型号和 RAM。

表 2. 定制 {{site.data.keyword.baremetal_short}} 的选项

|CPU 选项|RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon E5-2620 V4 / 共 16 个核心，2.1 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|

### 裸机服务器的数量

可以配置的 ESXi 服务器数的范围为 2 到 20 个。

所有 ESXi 服务器共享相同的配置。部署后，可以再添加四个集群。对于 vSAN 存储设置，初始集群和部署后集群都需要 4 个 ESXi 服务器。有关最少 ESXi 服务器数的更多信息，请参阅[双节点 vCenter Server 实例具有高可用性吗？](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## 存储设置

存储设置基于您选择的裸机服务器配置和存储类型。

### vSAN 存储器

对于 vSAN，指定以下存储选项：

* **vSAN 容量磁盘的磁盘类型和大小**：选择满足共享存储器需求的容量。
* **vSAN 容量磁盘数**：选择要添加的 vSAN 共享存储器的磁盘数。磁盘数量必须为 2、4、6 或 8 个。
* 选择 VMware vSAN 6.6 许可证版本（Advanced 或 Enterprise）。

### NFS 存储器

选择 **NFS 存储器**时，可以为实例添加文件级别的共享存储器，其中所有共享使用相同的设置，也可以对每个文件共享指定不同的配置设置。请指定以下 NFS 选项：

**注：**文件共享数必须在范围 1 到 32 之间。

* **分别配置共享**：选择此项以对每个文件共享指定不同的配置设置。
* **共享数**：对每个文件共享使用相同的配置设置时，指定要添加的 NFS 共享存储器的文件共享数。
* **大小**：选择满足共享存储器需求的容量。
* **性能**：选择基于工作负载需求的 IOPS（每秒输入/输出操作数）/GB。
* **添加 NFS**：选择此项以添加使用不同配置设置的单个文件共享。

表 3. NFS 性能级别选项

|选项|详细信息|
  |:------------- |:------------- |
  |2 IOPS/GB|此选项旨在用于大多数通用工作负载。示例应用包括：托管小型数据库、备份 Web 应用程序或系统管理程序的虚拟机磁盘映像。|
  |4 IOPS/GB|此选项旨在用于同时活动数据百分比高的更高强度工作负载。示例应用包括：事务性数据库。|
  |10 IOPS/GB|此选项旨在用于要求最苛刻的工作负载类型（如分析）。示例应用包括：高事务数据库和其他性能敏感型数据库。此性能级别限制为每个文件共享的最大容量为 4 TB。|

## 网络接口设置

### 主机名前缀

主机名前缀必须满足以下需求：
*  只允许使用字母数字字符和短划线 (-) 字符。
*  主机名前缀必须以字母数字字符开头和结尾。
*  主机名前缀的最大长度为 10 个字符。

### 子域标签

子域标签必须满足以下需求：
*  只允许使用字母数字字符和短划线 (-) 字符。
*  子域标签必须以字母数字字符开头和结尾。
*  子域标签的最大长度为 10 个字符。
*  子域标签在您的帐户中必须唯一。

### 域名

根域名必须满足以下需求：
* 域名必须包含两个或更多用句点 (.) 分隔的字符串。
* 第一个字符串必须以字母字符开头并以字母数字字符结尾。
* 除了最后一个字符串外，其他所有字符串都只能包含字母数字和短划线 (-) 字符。
* 最后一个字符串只能包含字母字符。
* 最后一个字符串的长度必须在 2 到 24 个字符范围内。

**注**：主机和 VM 的标准域名 (FQDN) 的最大长度为 50 个字符。域名必须符合此最大长度。

### DNS 配置

为实例选择域名系统 (DNS) 配置：

* **一个用于 Active Directory/DNS 的公共 Windows VSI**：一个用于 Microsoft Active Directory (AD) 的 Microsoft Windows Server VSI，充当在其中注册主机和虚拟机的实例的 DNS，已部署并且可进行查找。
* **管理集群上两个高可用性专用 Windows Server VM**：对于 V2.3 和未来发行版，会部署两个 Microsoft Windows 虚拟机，以帮助增强安全性和稳健性。

**重要信息**：如果将实例配置为使用两个 Microsoft Windows 虚拟机，那么必须提供两个 Microsoft Windows Server 2012 R2 许可证。使用 Microsoft Windows Server 2012 R2 Standard Edition 许可证和/或 Microsoft Windows Server 2012 R2 Datacenter Edition 许可证。

目前，每个许可证只能分配给一个物理服务器，并且最多包含两个物理处理器。一个 Standard Edition 许可证支持每个双处理器服务器运行两个虚拟化的 Microsoft Windows 虚拟机。因此，需要两个许可证，因为两个 Microsoft Windows 虚拟机会部署在两个不同的主机中。

您有 30 天的时间来激活虚拟机。

有关订购 Windows 许可的更多信息，请参阅 [Windows Server 2012 R2 文档](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2)。

## 订单摘要

根据为实例选择的配置，估算成本会立即生成并显示在右侧窗格的**订单摘要**部分中。单击右侧窗格底部的**定价详细信息**可生成提供估算详细信息的 PDF 文档。

## 过程

1. 在 IBM Cloud“目录”中，单击左侧导航窗格中的 **VMware**，然后单击**虚拟数据中心**部分中的 **vCenter Server**。
2. 在 **VMware vCenter Server on IBM Cloud** 页面上，单击 **vCenter Server** 卡，然后单击**创建**。
3. 在 **vCenter Server** 页面上，输入实例名称。
4. 单击**主实例**以在环境中部署单个实例。
5. 指定 VMware NSX 许可证版本。
6. 完成裸机服务器配置：
  1. 选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
  2. 选择**定制** CPU 型号和 **RAM** 量。
7. 填写存储配置。
  * 选择 **vSAN 存储器**时，指定 **vSAN 容量磁盘的磁盘类型和大小**、**vSAN 容量磁盘数**以及要如何提供 **vSAN 许可证**。
  * 选择 **NFS 存储器**并且想要向所有文件共享添加和配置相同设置时，请指定**共享数**、**大小**和**性能**。
  * 选择 **NFS 存储器**并想要单独添加和配置文件共享时，请选择**单独配置共享**，然后单击**添加 NFS** 标签旁边的 **+** 图标，然后为每个单独的文件共享选择**大小**和**性能**。必须至少选择一个文件共享。
8. 完成网络接口配置。
   1. 输入主机名前缀、子域标签和根域名。
   2. 选择 DNS 配置。
9. 在**订单摘要**窗格上，验证实例配置，然后再下订单。
   1. 复查实例的设置。
   2. 单击订单适用条款的链接，并在订购实例之前确认您同意这些条款。
   3. 通过单击**计算成本**下的成本链接来复查实例的估算成本。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   4. 单击**供应**。

## 结果

实例部署会自动启动。您将收到说明订单正在处理的确认，并且您可以通过查看实例详细信息来检查部署的状态。

成功部署实例后，[VMware Federal on {{site.data.keyword.cloud_notm}} 的 vCenter Server 实例组件](../vcenter/vc_fed_overview.html#vcenter-server-instance-components-for-vmware-federal-on-ibm-cloud)中描述的组件已安装在 VMware 虚拟平台上。缺省情况下，订购的 ESXi 服务器将分组为 **cluster1**。

实例准备就绪可供使用后，该实例的状态会更改为**可供使用**，并且您将收到通过电子邮件发送的通知。

<!--When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.-->

## 后续步骤

查看、管理订购的 VMware Federal 实例或确保其安全。

**重要信息**：您只能在 {{site.data.keyword.vmwaresolutions_full}} 控制台中管理 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 组件，而不能在 {{site.data.keyword.slportal}} 中或在控制台外部通过其他任何方法来进行管理。
如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步。

**注意**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部管理任何 {{site.data.keyword.vmwaresolutions_short}} 组件（在订购实例时安装到 {{site.data.keyword.cloud_notm}} 帐户中）可能会使环境变得不稳定。这些管理活动包括：
*  添加、修改、返回或除去组件
*  通过除去 ESXi 服务器来扩展或收缩实例容量
*  关闭组件电源

   这些活动的例外情况包括在 {{site.data.keyword.slportal}} 中管理共享存储器文件共享。此类活动包括：订购、删除（如果已安装，可能会影响数据存储）、授权和安装共享存储器文件共享。

## 相关链接

* [注册 {{site.data.keyword.cloud_notm}} 帐户](../vmonic/signing_softlayer_account.html)
* [查看 VMware Federal 实例](vc_fed_viewinginstance.html)
* [扩展和收缩 VMware Federal 实例的容量](vc_fed_addingremovingservers.html)
* [添加、查看和删除 VMware Federal 实例的集群](fed_addviewdeleteclusters.html)
* [确保 VMware Federal 实例安全](vc_fed_securinginstance.html)
* [删除 VMware Federal 实例](vc_fed_deletinginstance.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
