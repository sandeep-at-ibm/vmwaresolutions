---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购 vCenter Server 实例

要部署灵活且可定制的 VMware 虚拟化平台，以最适合您的工作负载需求，请订购 VMware vCenter Server 实例。在初始订购期间，还可以添加服务，例如用于灾难恢复的 [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html)。

## 需求

确保已完成以下任务：
* 已在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。有关更多信息，请参阅[管理用户帐户和设置](../vmonic/useraccount.html)。
* 已查看[针对 vCenter Server 实例的需求和规划](vc_planning.html)中的信息。
* 已复查实例和域名格式。域名和子域标签用于生成实例的用户名和服务器名称。

表 1. 实例和域名的值格式

|名称|值格式|
  |:------------|:------------ |
  |域名| `<root_domain>` |  
  |vCenter Server 登录用户名| `<user_id>@<root_domain>`（Microsoft Active Directory 用户）或 `administrator@vsphere.local`|
  |vCenter Server FQDN|`vcenter.<subdomain_label>.<root_domain>`. 最大长度为 50 个字符。|
  |Single Sign-On (SSO) 站点名称| `<subdomain_label>` |
  |标准 ESXi 服务器名称| `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中 `<n>` 是 ESXi 服务器的序列。最大长度为 50 个字符。|  
  |PSC FQDN|`psc-<subdomain_label>.<subdomain_label>.<root_domain>`. 最大长度为 50 个字符。|

不要修改在实例订购或部署期间设置的任何值。这样做可能会使您的实例不可用。例如，如果公用网络关闭，如果服务器和虚拟服务器实例 (VSI) 在供应期间移至 Vyatta 后，或者如果 IBM CloudBuilder VSI 停止或被删除。
{:important}

## 系统设置

订购 vCenter Server 实例时，必须指定以下系统设置。

### 实例名称

实例名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 实例名称必须以字母数字字符开头和结尾。
* 实例名称的最大长度为 10 个字符。
* 实例名称在您的帐户中必须唯一。

### 主实例或辅助实例

选择是订购新的主实例还是为现有主实例订购辅助实例。

## 许可证设置

为实例中的以下 VMware 组件指定许可选项：
* vCenter Server 6.5 - Standard Edition
* vSphere 6.5u1 - Enterprise Plus Edition
* NSX Service Providers 6.4（Base Edition、Advanced Edition 或 Enterprise Edition）

对于业务合作伙伴用户，会包含 vCenter Server 许可证 (Standard Edition)、vSphere 许可证 (Enterprise Plus Edition) 和 NSX 许可证，这些许可证以您的名义购买。但是，您必须指定 NSX 许可证的版本。

对于非业务合作伙伴用户，可以通过选择**购买时包含**对这些组件使用 IBM 提供的 VMware 许可证，或者可以通过选择**我将提供**并输入您自己的许可证密钥以自带许可证 (BYOL)。


**注意：**
* 需要至少具有 8 个 CPU 的许可证，即用于 4 个服务器，每个服务器 2 个 CPU。每个 VMware 组件的许可证选项会应用于基本实例以及日后添加到该实例的任何 ESXi 服务器。因此，请确保您的许可证在基础架构中支持未来的容量扩展。
* 用户界面上指示了最低许可证版本。如果支持不同的组件版本，那么可以选择所需的版本。您负责确保提供的许可证密钥对于选择的每个 VMware 组件都正确。
* 对于 vSphere，在订购时会发生许可费用，但随后会将该许可费用计入您的帐户。
* 可以在完成实例部署后，使用 VMware vSphere Web Client 来更改已提供的任何许可证。
* 对于您提供了许可证的 VMware 组件，将由 VMware 而不是 IBM 支持人员来提供后续支持。
{:important}

## 裸机服务器设置

裸机设置基于您选择的数据中心以及裸机服务器配置。

### 数据中心位置

选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。

### Skylake

选择 **Skylake** 时，可以根据需要为裸机服务器选择 CPU 和 RAM 组合。

表 2. Skylake {{site.data.keyword.baremetal_short}} 的选项

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|

### SAP 认证

选择 **SAP 认证**后，无法变更 CPU 或 RAM 设置。

根据需求，选择裸机服务器配置：
  * 双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz / 192 GB RAM
  * 双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz / 384 GB RAM
  * 双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz / 768 GB RAM

### Broadwell

选择 **Broadwell** 时，可以根据需要为裸机服务器选择 CPU 和 RAM 组合。

表 3. Broadwell {{site.data.keyword.baremetal_short}} 的选项

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon E5-2620 V4 / 共 16 个核心，2.1 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|

### 裸机服务器的数量

对于实例中的初始集群，可以配置的 ESXi 服务器数范围为 2 到 20 个。所有 ESXi 服务器共享所设置的配置。 

初始部署后，可以再添加四个集群。如果为 VMware vSAN 选择的是 **Skylake** 或 **Broadwell** 配置，那么初始集群和部署后集群都需要 4 个 ESXi 服务器。有关最少 ESXi 服务器数的更多信息，请参阅[双节点 vCenter Server 实例具有高可用性吗](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)。

## 存储设置

存储设置基于您选择的裸机服务器配置和存储类型。

### vSAN 存储器

vSAN 仅可用于 **Skylake** 和 **Broadwell** 裸机配置。请指定以下 vSAN 选项：
* **vSAN 容量磁盘的磁盘类型和大小**：选择与所需容量磁盘相应的选项。
* **vSAN 容量磁盘数**：指定要添加的容量磁盘数。
* 如果要添加的容量磁盘数超过 8 个的限制，请选中**高性能 Intel Optane** 框。此选项用于提供两个额外的容量磁盘托架，总共可容纳 10 个容量磁盘；此选项对于需要更短等待时间和更高 IOPS 吞吐量的工作负载而言非常有用。**高性能 Intel Optane** 选项仅可用于双 Intel Xeon Gold 5120 和 6140 处理器。

* 查看 **vSAN 高速缓存磁盘的磁盘类型**和 **vSAN 高速缓存磁盘数**值。这些值依赖于是否选中了**高性能 Intel Optane** 框。
* **vSAN 许可证**：通过选择**购买时包含**对 vSAN 组件使用 IBM 提供的 VMware 许可证，或者通过选择**我将提供**并输入您自己的许可证密钥以自带许可证 (BYOL)。

### NFS 存储器

选择 **NFS 存储器**时，可以为实例添加文件级别的共享存储器，其中所有共享使用相同的设置，也可以对每个文件共享指定不同的配置设置。请指定以下 NFS 选项：

文件共享数必须在范围 1 到 32 之间。
{:note}

* **分别配置共享**：选择此项以对每个文件共享指定不同的配置设置。
* **共享数**：对每个文件共享使用相同的配置设置时，指定要添加的 NFS 共享存储器的文件共享数。
* **大小**：选择满足共享存储器需求的容量。
* **性能**：选择基于工作负载需求的 IOPS（每秒输入/输出操作数）/GB。
* **添加 NFS**：选择此项以添加使用不同配置设置的单个文件共享。

表 4. NFS 性能级别选项

|选项|详细信息|
  |:------------- |:------------- |
  |2 IOPS/GB|此选项旨在用于大多数通用工作负载。示例应用包括：托管小型数据库、备份 Web 应用程序或系统管理程序的虚拟机磁盘映像。|
  |4 IOPS/GB|此选项旨在用于同时活动数据百分比高的更高强度工作负载。示例应用包括：事务性数据库。|
  |10 IOPS/GB|此选项旨在用于要求最苛刻的工作负载类型（如分析）。示例应用包括：高事务数据库和其他性能敏感型数据库。此性能级别限制为每个文件共享的最大容量为 4 TB。|

## 网络接口设置

订购 vCenter Server 实例时，必须指定以下网络接口设置。

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

主机和 VM 的标准域名 (FQDN) 的最大长度为 50 个字符。域名必须符合此最大长度。
{:note}

### 公用或专用网络

网络接口卡 (NIC) 启用设置基于您选择的是**公用和专用网络**还是**仅专用网络**。以下附加组件服务需要公共 NIC，并且这些服务在您选择专用选项时不可用：

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### VLAN

网络设置基于您选择的是**订购新 VLAN** 还是**选择现有 VLAN**。

订购实例时，需要包含一个公用 VLAN 和两个专用 VLAN。两个专用 VLAN 用于中继到每个裸机服务器中。

#### 订购新的 VLAN
选择此项可订购一个新的公用 VLAN 和两个新的专用 VLAN。

#### 选择现有 VLAN
根据选择的 {{site.data.keyword.CloudDataCent_notm}}，可能会有现有公用和专用 VLAN 可用。

选择复用现有公用和专用 VLAN 时，请指定 VLAN 和子网：
* **公用 VLAN** 用于公用网络访问。
* **专用 VLAN** 用于连接 {{site.data.keyword.cloud_notm}} 中的各数据中心和服务。
* **辅助专用 VLAN** 用于 VMware 功能部件，例如 vSAN。
* **主子网**分配给物理主机以用于公用网络访问。
* **主专用子网**分配给物理主机以用于管理流量。

* 确保所选 VLAN 上的防火墙配置不会阻止管理数据流量。
* 确保选择的所有 VLAN 都在同一 pod 中。在混合 pod VLAN 上无法供应 ESXi 服务器。
{:important}

### DNS 配置

为实例选择域名系统 (DNS) 配置：

* **一个用于 Active Directory/DNS 的公共 Windows VSI**：一个用于 Microsoft Active Directory (AD) 的 Microsoft Windows Server VSI，充当在其中注册主机和 VM 的实例的 DNS，已部署并且可进行查找。对于 V1.9 和更高版本的实例，缺省情况下已部署此选项。
* **管理集群上两个高可用性专用 Windows Server VM**：部署了两个 Microsoft Windows 虚拟机，以帮助增强安全性和稳健性。

如果将实例配置为使用两个 Microsoft Windows VM，那么必须提供两个 Microsoft Windows Server 2012 R2 许可证。使用 Microsoft Windows Server 2012 R2 Standard Edition 许可证和/或 Microsoft Windows Server 2012 R2 Datacenter Edition 许可证。
{:important}

每个许可证只能分配给一个物理服务器，并且最多包含两个物理处理器。一个 Standard Edition 许可证支持每个双处理器服务器运行两个虚拟化的 Microsoft Windows VM。因此，需要两个许可证，因为两个 Microsoft Windows VM 会部署在两个不同的主机中。

您有 30 天的时间来激活 VM。

有关 Windows 许可的更多信息，请参阅 [Windows Server 2012 R2 文档](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2)。

## 服务设置

订购 vCenter Server 实例时，还可以订购附加组件服务。有关服务的更多信息，请参阅 [vCenter Server 实例的可用服务](vc_addingremovingservices.html#available-services-for-vcenter-server-instances)。

## 订单摘要

根据为实例和附加组件服务选择的配置，估算成本会立即生成并显示在右侧窗格的**订单摘要**部分中。单击右侧窗格底部的**定价详细信息**可生成提供估算详细信息的 PDF 文档。

## 订购 vCenter Server 实例的过程

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格中的 **VMware**，然后单击**虚拟数据中心**部分中的 **vCenter Server**。
2. 在 **VMware vCenter Server on IBM Cloud** 页面上，单击 **vCenter Server** 卡，然后单击**创建**。
3. 在 **vCenter Server** 页面上，输入实例名称。
4. 选择实例类型：
   * 单击**主实例**以在环境中部署单个实例，或者在多站点拓扑中部署第一个实例。
   * 单击**辅助实例**以将该实例与环境中的现有（主）实例连接以获取高可用性，并完成以下步骤：
     1. 选择要与辅助实例连接的主实例。
     2. 对于主实例 V2.5 或更高版本，请输入**主实例 PSC 的管理员密码**的值。
     3. 对于主实例 V2.4 或更低版本，请验证**主实例 PSC 的管理员密码**字段的预填充值是否正确。
5. 完成实例组件的许可证设置。
   *  要使用 IBM 提供的许可证，请选择**购买时包含**，并根据需要选择许可证版本。
   *  要使用您自己的许可证，请选择**我将提供**并输入许可证密钥。
6. 完成裸机服务器设置。
    1. 选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
    2. 选择裸机服务器配置。
       * 选择 **Skylake** 或 **Broadwell** 时，请指定 CPU 型号和 RAM 大小。
       * 选择的是 **SAP 认证**时，请选择 CPU 型号。
    3. 指定 {{site.data.keyword.baremetal_short}} 数。如果计划将 vSAN 用作存储解决方案，那么至少需要 4 个 {{site.data.keyword.baremetal_short}}。  
7. 填写存储配置。
  * 如果选择 **vSAN 存储器**，请指定容量和高速缓存磁盘的磁盘类型、磁盘数和 vSAN 许可证版本。如果需要更多存储器，请选中**高性能 Intel Optane** 框。
  * 如果选择 **NFS 存储器**，并且要向所有文件共享添加和配置相同设置，请指定**共享数**、**大小**和**性能**。
  * 如果选择 **NFS 存储器**，并且要单独添加和配置文件共享，请选择**单独配置共享**。接着，单击**添加 NFS** 标签旁边的 **+** 图标，然后为每个文件共享选择**大小**和**性能**。必须至少选择一个文件共享。
8. 完成网络接口设置。
   1. 输入主机名前缀、子域标签和根域名。对于辅助实例，系统会自动填写域名。
   2. 选择网络设置**公用和专用网络**或**仅专用网络**。
   3. 选择 VLAN 设置：
      * 如果要订购新的公用和专用 VLAN，请单击**订购新的 VLAN**。
      * 如果要复用可用的现有公用和专用 VLAN，请单击**选择现有 VLAN**，然后指定 VLAN 和子网。
   4. 指定 DNS 配置。

9. 通过单击相应的服务卡，选择要部署到实例中的附加组件服务。如果服务需要配置，请完成特定于服务的设置，然后单击相应卡上的**添加服务**。有关如何为服务提供设置的更多信息，请参阅相应的服务订购主题。

10. 在**订单摘要**窗格上，验证实例配置，然后再下订单。
   1. 复查实例的设置。
   2. 复查实例的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在订购实例之前确认您同意这些条款。
   4. 单击**供应**。

## 结果

实例部署会自动启动。您将收到说明订单正在处理的确认，并且您可以通过查看实例详细信息来检查部署的状态。

成功部署实例后，[vCenter Server 实例的技术规范](vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances)中描述的组件已安装在 VMware 虚拟平台上。缺省情况下，订购的 ESXi 服务器将分组为 **cluster1**。如果订购了附加组件服务，那么这些服务的部署将在订单完成后启动。

实例准备就绪可供使用后，该实例的状态会更改为**可供使用**，并且您将收到通过电子邮件发送的通知。

订购辅助实例时，在完成辅助实例订单后，可能会重新启动主实例（链接到辅助实例）的 VMware vSphere Web Client。

## 后续步骤

查看和管理订购的 vCenter Server 实例。

您只能在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理在 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 组件，而不能在 {{site.data.keyword.slportal}} 中或在该控制台外部通过其他任何方法对这些组件进行管理。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步。
{:important}

**注意**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部管理任何 {{site.data.keyword.vmwaresolutions_short}} 组件（在订购实例时安装到 {{site.data.keyword.cloud_notm}} 帐户中）可能会使环境变得不稳定。这些管理活动包括：
*  添加、修改、返回或除去组件
*  通过添加或除去 ESXi 服务器来扩展或收缩实例容量
*  关闭组件电源
*  重新启动服务

   这些活动的例外情况包括在 {{site.data.keyword.slportal}} 中管理共享存储器文件共享。此类活动包括：订购、删除（如果已安装，可能会影响数据存储）、授权和安装共享存储器文件共享。

### 相关链接

* [注册 {{site.data.keyword.cloud_notm}} 帐户](../vmonic/signing_softlayer_account.html)
* [查看 vCenter Server 实例](vc_viewinginstances.html)
* [vCenter Server 实例的多站点配置](vc_multisite.html)
* [添加、查看和删除 vCenter Server 实例的集群](vc_addingviewingclusters.html)
* [扩展和收缩 vCenter Server 实例的容量](vc_addingremovingservers.html)
* [订购、查看和除去 vCenter Server 实例的服务](vc_addingremovingservices.html)
* [删除 vCenter Server 实例](vc_deletinginstance.html)
