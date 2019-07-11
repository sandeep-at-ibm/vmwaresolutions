---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vCenter Server NSX-T order instance, order vCenter Server NSX-T, order NSX-T

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购 vCenter Server with NSX-T 实例
{: #vc_nsx-t_orderinginstance}

要部署灵活且可定制的 VMware 虚拟化平台，以最适合您的工作负载需求，请订购 VMware vCenter Server with NSX-T 实例。

## vCenter Server with NSX-T 的需求
{: #vc_nsx-t_orderinginstance-req}

确保已完成以下任务：
* 已在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。有关更多信息，请参阅[管理用户帐户和设置](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。
* 已查看[针对 vCenter Server 实例的需求和规划](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)中的信息。
* 已复查实例和域名格式。域名和子域标签用于生成实例的用户名和服务器名称。

表 1. 实例和域名的值格式

|名称|值格式|
  |:------------|:------------ |
  |域名| `<root_domain>` |  
  |vCenter Server 登录用户名|`<user_id>@<root_domain>`（Microsoft Active Directory 用户）或 `administrator@vsphere.local`|
  |vCenter Server（具有嵌入式 PSC）FQDN|`vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`。最大长度为 50 个字符。|
  |Single Sign-On (SSO) 站点名称| `<subdomain_label>` |
  |标准 ESXi 服务器名称| `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中 `<n>` 是 ESXi 服务器的序列。最大长度为 50 个字符。|

不要修改在实例订购或部署期间设置的任何值。这样做可能会使您的实例不可用。例如，如果公用网络关闭，如果服务器和虚拟服务器实例 (VSI) 在供应期间移至 Vyatta 后，或者如果 IBM CloudBuilder VSI 停止或被删除。
{:important}

## 系统设置
{: #vc_nsx-t_orderinginstance-sys-settings}

订购 vCenter Server 实例时，必须指定以下系统设置。

### 实例名称
{: #vc_nsx-t_orderinginstance-inst-name}

实例名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 实例名称必须以字母字符开头并以字母数字字符结尾。
* 实例名称的最大长度为 10 个字符。
* 实例名称在您的帐户中必须唯一。

### VMware vSphere 许可证
{: ##vc_nsx-t_orderinginstance-vsphere-license}

缺省情况下，会选择 vSphere Enterprise Plus 6.7u1 许可证。

### 主实例或辅助实例
{: #vc_nsx-t_orderinginstance-primary-secondary}

选择是订购新的主实例还是为现有主实例订购辅助实例。

## 许可证设置
{: #vc_nsx-t_orderinginstance-licensing-settings}

为实例中的以下 VMware 组件指定许可选项：
* vCenter Server 6.5
* vSphere Enterprise Plus 6.7
* NSX-T 2.4（Base、Advanced 或 Enterprise 版）

对于业务合作伙伴用户，会包含 vCenter Server 许可证 (Standard Edition)、vSphere 许可证 (Enterprise Plus Edition) 和 NSX 许可证，这些许可证以您的名义购买。但是，您必须指定 NSX 许可证的版本。

对于非业务合作伙伴用户，可以通过选择**购买时包含**对这些组件使用 IBM 提供的 VMware 许可证，或者可以通过选择**我将提供**并输入您自己的许可证密钥以自带许可证 (BYOL)。

### 许可说明
{: #vc_nsx-t_orderinginstance-licensing-notes}

* 需要至少具有 8 个 CPU 的许可证，即用于 4 个服务器，每个服务器 2 个 CPU。每个 VMware 组件的许可证选项会应用于基本实例以及日后添加到该实例的任何 ESXi 服务器。因此，请确保您的许可证在基础架构中支持未来的容量扩展。
* 用户界面上指示了最低许可证版本。如果支持不同的组件版本，那么可以选择所需的版本。您负责确保提供的许可证密钥对于选择的每个 VMware 组件都正确。
* 对于 vSphere，在订购时会发生许可费用，但随后会将该许可费用计入您的帐户。
* 可以在完成实例部署后，使用 VMware vSphere Web Client 来更改已提供的任何许可证。
* 对于您提供了许可证的 VMware 组件，将由 VMware 而不是 IBM 支持人员来提供后续支持。


## 裸机服务器设置
{: #vc_nsx-t_orderinginstance-bare-metal-settings}

裸机设置基于您选择的数据中心以及裸机服务器配置。

### 数据中心位置
{: #vc_nsx-t_orderinginstance-dc-location}

选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。

### Skylake
{: #vc_nsx-t_orderinginstance-skylake}

选择 **Skylake** 时，可以根据需要为裸机服务器选择 CPU 和 RAM 组合。

表 2. Skylake {{site.data.keyword.baremetal_short}} 的选项

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|

### Broadwell
{: #vc_nsx-t_orderinginstance-broadwell}

选择 **Broadwell** 时，可以根据需要为裸机服务器选择 CPU 和 RAM 组合。

表 3. Broadwell {{site.data.keyword.baremetal_short}} 的选项

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|四核 Intel Xeon E7-4820 V4 / 共 40 个核心，2.0 GHz|128 GB、256 GB、512 GB、1 TB、2 TB、3 TB|
|四核 Intel Xeon E7-4850 V4 / 共 64 个核心，2.1 GHz|128 GB、256 GB、512 GB、1 TB、2 TB、3 TB|

### 裸机服务器的数量
{: #vc_nsx-t_orderinginstance-bare-metal-number}

* 订购的所有服务器的配置都相同。
* 如果计划使用 vSAN 存储器，那么可以订购 4 到 20 个服务器。
* 如果计划使用 NFS 存储器，那么可以订购 2 到 20 个服务器。但是，对于生产工作负载，建议至少使用 3 个服务器。有关更多信息，请参阅[双节点 vCenter Server 实例具有高可用性吗？](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)。

## 存储设置
{: #vc_nsx-t_orderinginstance-storage-settings}

存储设置基于您选择的裸机服务器配置和存储类型。

对于已部署的实例，可以将 NFS 存储共享添加到现有 NFS 或 vSAN 集群。有关更多信息，请参阅[扩展和收缩 vCenter Server 实例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances)中的*向 vCenter Server 实例添加 NFS 存储器*部分。
{:note}

### vSAN 存储器
{: #vc_nsx-t_orderinginstance-vsan-storage}

vSAN 仅可用于 **Skylake** 和 **Broadwell** 裸机配置。请指定以下 vSAN 选项：
* **vSAN 容量磁盘的磁盘类型和大小**：选择与所需容量磁盘相应的选项。
* **vSAN 容量磁盘数**：指定要添加的容量磁盘数。
* 如果要添加的容量磁盘数超过 10 个的限制，请选中**高性能 Intel Optane** 框。此选项用于提供两个额外的容量磁盘托架，总共可容纳 12 个容量磁盘；此选项对于需要更短等待时间和更高 IOPS 吞吐量的工作负载而言非常有用。

  **高性能 Intel Optane** 选项仅可用于 Skylake CPU 型号。
{:note}

* 查看 **vSAN 高速缓存磁盘的磁盘类型**和 **vSAN 高速缓存磁盘数**值。这些值依赖于是否选中了**高性能 Intel Optane** 框。
* **vSAN 许可证**：通过选择**购买时包含**对 vSAN 组件使用 IBM 提供的 VMware 许可证，或者通过选择**我将提供**并输入您自己的许可证密钥以自带许可证 (BYOL)。

### NFS 存储器
{: #vc_nsx-t_orderinginstance-nfs-storage}

选择 **NFS 存储器**时，可以为实例添加文件级别的共享存储器，其中所有共享使用相同的设置，也可以对每个文件共享指定不同的配置设置。请指定以下 NFS 选项：

文件共享数必须在范围 1 到 32 之间。
{:note}

* **分别配置共享**：选择此项以对每个文件共享指定不同的配置设置。
* **共享数**：对每个文件共享使用相同的配置设置时，指定要添加的 NFS 共享存储器的文件共享数。
* **性能**：选择基于工作负载需求的 IOPS（每秒输入/输出操作数）/GB。
* **大小 (GB)**：选择满足共享存储器需求的容量。
* **添加共享存储器**：选择此项以添加使用不同配置设置的单个文件共享。

表 4. NFS 性能级别选项

|选项|详细信息|
  |:------------- |:------------- |
  |0.25 IOPS/GB |此选项旨在用于不常用的工作负载。示例应用包括：保险库文件数据、托管具有旧数据的大型数据库或虚拟内存系统的虚拟磁盘映像（作为备份）。|
  |2 IOPS/GB|此选项旨在用于大多数通用工作负载。示例应用包括：托管小型数据库、备份 Web 应用程序或系统管理程序的虚拟机磁盘映像。|
  |4 IOPS/GB|此选项旨在用于同时活动数据百分比高的更高强度工作负载。示例应用包括：事务性数据库。|
  |10 IOPS/GB|此选项旨在用于要求最苛刻的工作负载类型（如分析）。示例应用包括：高事务数据库和其他性能敏感型数据库。此性能级别限制为每个文件共享的最大容量为 4 TB。|

## 网络接口设置
{: #vc_nsx-t_orderinginstance-network-interface-settings}

订购 vCenter Server 实例时，必须指定以下网络接口设置。

### 主机名前缀
{: #vc_nsx-t_orderinginstance-host-name-prefix}

主机名前缀必须满足以下需求：
*  只允许使用字母数字字符和短划线 (-) 字符。
*  主机名前缀必须以字母数字字符开头和结尾。
*  主机名前缀的最大长度为 10 个字符。

### 子域标签
{: #vc_nsx-t_orderinginstance-subdomain-label}

子域标签必须满足以下需求：
*  只允许使用字母数字字符和短划线 (-) 字符。
*  子域标签必须以字母字符开头并以字母数字字符结尾。
*  子域标签的最大长度为 10 个字符。

### 域名
{: #vc_nsx-t_orderinginstance-domain-name}

根域名必须满足以下需求：
* 域名必须包含两个或更多用句点 (.) 分隔的字符串。
* 第一个字符串必须以字母字符开头并以字母数字字符结尾。
* 除了最后一个字符串外，其他所有字符串都只能包含字母数字和短划线 (-) 字符。
* 最后一个字符串只能包含字母字符。
* 最后一个字符串的长度必须在 2 到 24 个字符范围内。

主机和 VM 的标准域名 (FQDN) 的最大长度为 50 个字符。域名必须符合此最大长度。
{:note}

### 公用或专用网络
{: #vc_nsx-t_orderinginstance-public-private-network}

网络接口卡 (NIC) 启用设置基于您选择的是**公用和专用网络**还是**仅专用网络**。

### VLAN
{: #vc_nsx-t_orderinginstance-vlans}

网络设置基于您选择的是**订购新 VLAN** 还是**选择现有 VLAN**。

订购实例时，需要包含一个公用 VLAN 和两个专用 VLAN。两个专用 VLAN 用于中继到每个裸机服务器中。

#### 订购新的 VLAN
{: #vc_nsx-t_orderinginstance-new-vlans}

选择此项可订购一个新的公用 VLAN 和两个新的专用 VLAN。

#### 选择现有 VLAN
{: #vc_nsx-t_orderinginstance-existing-vlans}

根据选择的 {{site.data.keyword.CloudDataCent_notm}}，可能会有现有公用和专用 VLAN 可用。

选择复用现有公用和专用 VLAN 时，请指定 VLAN 和子网：
* **公用 VLAN** 用于公用网络访问。
* **专用 VLAN** 用于连接 {{site.data.keyword.cloud_notm}} 中的各数据中心和服务。
* **辅助专用 VLAN** 用于 VMware 功能部件，例如 vSAN。
* **主子网**分配给物理主机以用于公用网络访问。
* **主专用子网**分配给物理主机以用于管理流量。

确保所选 VLAN 上的防火墙配置不会阻止管理数据流量。此外，还确保您选择的所有 VLAN 都在同一 pod 中。在混合 pod VLAN 上无法供应 ESXi 服务器。
{:important}

### DNS 配置
{: #vc_nsx-t_orderinginstance-dns-config}

为实例选择域名系统 (DNS) 配置：

* **一个用于 Active Directory/DNS 的公共 Windows VSI**：一个用于 Microsoft Active Directory (AD) 的 Microsoft Windows Server VSI，充当在其中注册主机和 VM 的实例的 DNS，已部署并且可进行查找。对于 V1.9 和更高版本的实例，缺省情况下已部署此选项。
* **管理集群上两个高可用性专用 Windows Server VM**：部署了两个 Microsoft Windows 虚拟机，以帮助增强安全性和稳健性。

如果将实例配置为使用两个 Microsoft Windows VM，那么必须提供两个 Microsoft Windows Server 2016 标准版本许可证。
{:important}

每个许可证只能分配给一个物理服务器，并且最多包含两个物理处理器。一个 Standard Edition 许可证支持每个双处理器服务器运行两个虚拟化的 Microsoft Windows VM。因此，需要两个许可证，因为两个 Microsoft Windows VM 会部署在两个不同的主机中。

您有 30 天的时间来激活 VM。

有关订购 Windows Server 2016 许可证的更多信息，请参阅 [Windows Server 2016 入门](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:new_window}。

## 订单摘要
{: #vc_nsx-t_orderinginstance-order-summary}

根据选择的配置，估算成本会立即生成并显示在**订单摘要**右侧窗格中。单击**定价详细信息**以生成 {{site.data.keyword.vmwaresolutions_short}} 资源成本汇总的 PDF 文档。

您还可以通过单击**添加到估算**来将供应的资源添加到 {{site.data.keyword.cloud_notm}} 估算工具**。如果要与您可能考虑购买的其他 {{site.data.keyword.cloud_notm}} 资源一起估算所选 {{site.data.keyword.vmwaresolutions_short}} 资源的成本，那么这非常有用。

## 订购 vCenter Server with NSX-T 实例的过程
{: #vc_nsx-t_orderinginstance-procedure}

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格中的 **VMware**，然后单击**虚拟数据中心**部分中的 **vCenter Server**。
2. 在 **VMware vCenter Server on IBM Cloud** 页面上，单击 **vCenter Server** 卡，然后单击**创建**。
3. 在 **vCenter Server** 页面上，输入实例名称。
4. 选择实例类型：
   * 单击**主实例**以在环境中部署单个实例，或者在多站点拓扑中部署第一个实例。
   * 单击**辅助实例**以将该实例与环境中的现有（主）实例连接以获取高可用性，并完成以下步骤：
     1. 选择要与辅助实例连接的主实例。
     2. 对于主实例 V2.8 或更高版本，请输入主实例的 vCenter Server 管理员密码。
     3. 对于主实例 V2.5、2.6 或 2.7，请输入主实例的 PSC 管理员密码。
     4. 对于主实例 V2.4 或更低版本，请验证主实例的 PSC 管理员密码的预填充值是否正确。
6. 完成实例组件的许可证设置。
   *  要使用 IBM 提供的许可证，请选择**购买时包含**，并根据需要选择许可证版本。
   *  要使用您自己的许可证，请选择**我将提供**并输入许可证密钥。
7. 完成裸机服务器设置。
    1. 选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
    2. 选择裸机服务器配置，然后指定 CPU 型号和 RAM 大小。
    3. 指定 {{site.data.keyword.baremetal_short}} 数。如果计划将 vSAN 用作存储解决方案，那么至少需要 4 个 {{site.data.keyword.baremetal_short}}。  
8. 填写存储配置。
  * 如果选择 **vSAN 存储器**，请指定容量和高速缓存磁盘的磁盘类型、磁盘数和 vSAN 许可证版本。如果需要更多存储器，请选中**高性能 Intel Optane** 框。
  * 如果选择 **NFS 存储器**，并且要向所有文件共享添加和配置相同设置，请指定**共享数**、**性能**和**大小 (GB)**。
  * 如果选择 **NFS 存储器**，并且要单独添加和配置文件共享，请选择**单独配置共享**。接着，单击**添加共享存储器**标签旁边的 **+** 图标，然后为每个文件共享选择**性能**和**大小 (GB)**。必须至少选择一个文件共享。
9. 完成网络接口设置。
   1. 输入要供应的实例的主机名前缀、子域标签和根域名。对于辅助实例，系统会自动填写域名。
   2. 选择网络设置**公用和专用网络**或**仅专用网络**。
   3. 选择 VLAN 设置：
      * 如果要订购新的公用和专用 VLAN，请单击**订购新的 VLAN**。
      * 如果要复用可用的现有公用和专用 VLAN，请单击**选择现有 VLAN**，然后指定 VLAN 和子网。
   4. 指定 DNS 配置。

11. 在**订单摘要**窗格上，验证实例配置，然后再下订单。
   1. 复查实例的设置。
   2. 复查实例的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在订购实例之前确认您同意这些条款。
   4. 单击**供应**。

## 订购 vCenter Server with NSX-T 实例后的结果
{: #vc_nsx-t_orderinginstance-results}

* 实例部署会自动启动，并且您将收到确认，指示正在处理订单。通过查看实例详细信息的**部署历史记录**部分，可以检查部署状态，包括可能需要注意的任何问题。
* 成功部署实例后，[vCenter Server with NSX-T 实例的技术规范](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_overview#vc_nsx-t_overview-specs)中描述的组件已安装在 VMware 虚拟平台上。缺省情况下，订购的 ESXi 服务器将分组为 **cluster1**。
* 实例准备就绪可供使用后，该实例的状态会更改为**可供使用**，并且您将收到通过电子邮件发送的通知。
* 订购辅助实例时，在完成辅助实例订单后，可能会重新启动主实例（链接到辅助实例）的 VMware vSphere Web Client。

## 后续步骤
{: #vc_nsx-t_orderinginstance-next}

查看和管理订购的 vCenter Server with NSX-T 实例。有关查看实例的更多信息，请参阅[查看 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)。

您只能在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理在 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 组件，而不能在 {{site.data.keyword.slportal}} 中或在该控制台外部通过其他任何方法对这些组件进行管理。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步。
{:important}

**注意**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部管理任何 {{site.data.keyword.vmwaresolutions_short}} 组件（在订购实例时安装到 {{site.data.keyword.cloud_notm}} 帐户中）可能会使环境变得不稳定。这些管理活动包括：
*  添加、修改、返回或除去组件
*  通过添加或除去 ESXi 服务器来扩展或收缩实例容量
*  关闭组件电源
*  重新启动服务

   这些活动的例外情况包括在 {{site.data.keyword.slportal}} 中管理共享存储器文件共享。此类活动包括：订购、删除（如果已安装，可能会影响数据存储）、授权和安装共享存储器文件共享。

## 相关链接
{: #vc_nsx-t_orderinginstance-related}

* [注册 {{site.data.keyword.cloud_notm}} 帐户](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts)
* [查看 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server 实例的多站点配置](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)
* [添加、查看和删除 vCenter Server with NSX-T 实例的集群](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [扩展和收缩 vCenter Server with NSX-T 实例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
* [删除 vCenter Server with NSX-T 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
