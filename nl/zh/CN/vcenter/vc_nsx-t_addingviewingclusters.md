---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: vCenter Server NSX-T add cluster, view cluster vCenter Server NSX-T, delete cluster vCenter Server NSX-T

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 添加、查看和删除 vCenter Server with NSX-T 实例的集群
{: #vc_nsx-t_addingviewingcluster}

可以向 VMware vCenter Server with NSX-T 实例添加您自己的集群以扩展计算和存储容量。在集群中，可以管理 ESXi 服务器以获得更佳的资源分配和高可用性。不再需要添加的集群时，请从实例中将其删除。

## 向 vCenter Server 实例添加集群
{: #vc_nsx-t_addingviewingclusters-adding}

### 添加集群之前
{: #vc_nsx-t_addingviewingclusters-before-add}

* 尽可能使用 {{site.data.keyword.vmwaresolutions_full}} 控制台添加集群，因为在 VMware vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。因此，将集群添加到 vCenter Server 仅适用于内部部署集群，或者无法或不会在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理的集群。
* 集群数、主机数和虚拟机 (VM) 数将决定可以添加的最大集群数限制。您必须遵守适用于部署的 VMware 大小调整准则和限制。有关最大限制的更多信息，请参阅 [VMware 配置最大值](https://configmax.vmware.com/home){:external}。

### 系统设置
{: #vc_nsx-t_addingviewingclusters-adding-sys-settings}

为 vCenter Server with NSX-T 实例添加集群时，必须指定以下设置。

#### 集群名称
{: #vc_nsx-t_addingviewingclusters-adding-cluster-name}

集群名称必须满足以下需求：
* 只允许使用小写字母、数字和短划线 (-) 字符。
* 集群名称必须以小写字母字符开头。
* 集群名称必须以小写字母或数字字符结尾。
* 集群名称的最大长度为 30 个字符。
* 集群名称在 vCenter Server with NSX-T 实例中必须唯一。

#### 数据中心位置
{: #vc_nsx-t_addingviewingclusters-adding-dc-location}

缺省情况下，集群的 {{site.data.keyword.CloudDataCent}} 位置设置为 vCenter Server 实例的 {{site.data.keyword.CloudDataCent_notm}}。可以将集群部署到与所部署实例不同的 {{site.data.keyword.CloudDataCent_notm}}，但必须确保这两个 {{site.data.keyword.CloudDataCents_notm}} 之间的网络等待时间少于 150 毫秒。要检查网络等待时间，可以使用 [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass) 等工具。

如果将集群部署到其他 {{site.data.keyword.CloudDataCent_notm}} 或 {{site.data.keyword.cloud_notm}} 基础架构 pod，那么可订购三个额外的 VLAN 以用于订购的 {{site.data.keyword.baremetal_short}}。

### 裸机服务器设置
{: #vc_nsx-t_addingviewingclusters-bare-metal-settings}

您可以选择 **Skylake**、**Cascade** 或 **Broadwell**。

#### Skylake
{: #vc_nsx-t_addingviewingclusters-adding-skylake}

对于 **Skylake** 设置，您有各种 **CPU 型号**和 **RAM** 选项。可用选项可能有所不同，具体取决于初始部署实例的版本。

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|
{: caption="表 1. Skylake {{site.data.keyword.baremetal_short}} 的选项" caption-side="top"}

#### Cascade
{: #vc_nsx-t_addingviewingclusters-adding-cascade}

对于 **Cascade** 设置，您有各种 **CPU 型号**和 **RAM** 选项。

Cascade {{site.data.keyword.baremetal_short}} 仅可用于 VMware vSphere Enterprise Plus 6.7 U2 实例。
{:note}

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon Gold 4210 处理器 / 共 20 个核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5218 处理器 / 共 32 个核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6248 处理器 / 共 40 个核心，2.5 GHz|64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB|
{: caption="表 2. Cascade {{site.data.keyword.baremetal_short}} 的选项" caption-side="top"}

#### Broadwell
{: #vc_nsx-t_addingviewingclusters-adding-broadwell}

对于 **Broadwell** 设置，您有多个 **CPU 型号**和 **RAM** 选项。可用选项可能有所不同，具体取决于初始部署实例的版本。

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|四核 Intel Xeon E7-4820 V4 / 共 40 个核心，1.9 GHz|128 GB、256 GB、512 GB、1 TB、2 TB、3 TB|
|四核 Intel Xeon E7-4850 V4 / 共 64 个核心，2.2 GHz|128 GB、256 GB、512 GB、1 TB、2 TB、3 TB|
{: caption="表 3. Broadwell {{site.data.keyword.baremetal_short}} 的选项" caption-side="top"}

#### 裸机服务器的数量
{: #vc_nsx-t_addingviewingclusters-adding-bare-metal-number}

* 订购的所有服务器的配置都相同。
* 对于 vSAN 存储器，可以订购 4 到 59 个服务器。
* 对于 NFS 存储器，可以订购 2 到 59 个服务器。但是，对于生产工作负载，建议至少使用 3 个服务器。有关更多信息，请参阅[双节点 vCenter Server 实例具有高可用性吗？](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)。

### 存储设置
{: #vc_nsx-t_addingviewingclusters-adding-storage-settings}

存储设置基于您选择的裸机服务器配置和存储类型。

#### vSAN 存储器
{: #vc_nsx-t_addingviewingclusters-adding-vsan-storage}

请指定以下 vSAN 选项：
* **vSAN 容量磁盘的磁盘类型和大小**：选择与所需容量磁盘相应的选项。
* **vSAN 容量磁盘数**：指定要添加的容量磁盘数。
* 如果要添加的容量磁盘数超过 10 个的限制，请选中**高性能 Intel Optane** 框。此选项用于提供两个额外的容量磁盘托架，总共可容纳 12 个容量磁盘；此选项对于需要更短等待时间和更高 IOPS 吞吐量的工作负载而言非常有用。

  **高性能 Intel Optane** 选项仅可用于 Skylake 和 Cascade CPU 型号。
{:note}

* 查看 **vSAN 高速缓存磁盘的磁盘类型**和 **vSAN 高速缓存磁盘数**值。这些值依赖于是否选中了**高性能 Intel Optane** 框。
* **vSAN 许可证**：通过选择**购买时包含**对 vSAN 组件使用 IBM 提供的 VMware 许可证，或者通过选择**我将提供**并输入您自己的许可证密钥以自带许可证 (BYOL)。

如果初始集群为 vSAN 集群，那么其他任何 vSAN 集群都会使用与初始 vSAN 集群相同的 vSAN 许可证，并具有与初始 vSAN 集群相同的配置。如果实例中的任何集群选择了要部署 vSAN（初始或其他集群），也是如此。第一次系统会提示您提供 vSAN 许可证（BYOL 或购买的许可证）和版本。下次您为新集群选择 vSAN 时，将复用最初选择的许可证。

#### NFS 存储器
{: #vc_nsx-t_addingviewingclusters-adding-nfs-storage}

选择 **NFS 存储器**时，可以为实例添加文件级别的共享存储器，其中所有共享使用相同的设置，也可以对每个文件共享指定不同的配置设置。请指定以下 NFS 选项：

文件共享数必须在范围 1 到 32 之间。
{:note}

* **分别配置共享**：选择此项以对每个文件共享指定不同的配置设置。
* **共享数**：要对每个文件共享使用相同的配置设置时，请指定要添加的 NFS 共享存储器的文件共享数。
* **大小**：选择满足共享存储器需求的容量。
* **性能**：选择基于工作负载需求的 IOPS（每秒输入/输出操作数）/GB。
* **添加 NFS**：选择此项以添加使用不同配置设置的单个文件共享。

性能级别详细信息：

|选项|详细信息|
|:------------- |:------------- |
|0.25 IOPS/GB |此选项旨在用于不常用的工作负载。示例应用包括：保险库文件数据、托管具有旧数据的大型数据库或虚拟内存系统的虚拟磁盘映像（作为备份）。|
|2 IOPS/GB|此选项旨在用于大多数通用工作负载。示例应用包括：托管小型数据库、备份 Web 应用程序或系统管理程序的虚拟机 (VM) 磁盘映像。|
|4 IOPS/GB|此选项旨在用于同时活动数据百分比高的更高强度工作负载。示例应用包括：事务性数据库。|
|10 IOPS/GB|此选项旨在用于要求最苛刻的工作负载类型（如分析）。示例应用包括：高事务数据库和其他性能敏感型数据库。此性能级别限制为每个文件共享的最大容量为 4 TB。|
{: caption="表 4. NFS 性能级别选项" caption-side="top"}

### 许可证设置
{: #vc_nsx-t_addingviewingclusters-adding-licensing-settings}

为集群中的 VMware vSphere 组件指定许可选项：
* 对于业务合作伙伴用户，会包含 vSphere 许可证 (Enterprise Plus Edition)，该许可证以您的名义购买。
* 对于非业务合作伙伴用户，可以通过选择**购买时包含**对此组件使用 IBM 提供的 VMware 许可证，或者可以通过选择**我将提供**并输入您自己的许可证密钥以自带许可证 (BYOL)。

### 网络接口设置
{: #vc_nsx-t_addingviewingclusters-adding-network-interface-settings}

网络接口卡 (NIC) 启用设置基于您选择的是**公用和专用网络**还是**仅专用网络**。

### 订单摘要
{: #vc_nsx-t_addingviewingclusters-adding-order-summary}

根据为集群选择的配置，估算成本会立即生成并显示在**订单摘要**右侧窗格中。单击**定价详细信息**以生成 {{site.data.keyword.vmwaresolutions_short}} 资源成本汇总的 PDF 文档。

您还可以通过单击**添加到估算**来将供应的资源添加到 {{site.data.keyword.cloud_notm}} 估算工具**。如果要与您可能考虑购买的其他 {{site.data.keyword.cloud_notm}} 资源一起估算所选 {{site.data.keyword.vmwaresolutions_short}} 资源的成本，那么这非常有用。

## 向 vCenter Server with NSX-T 实例添加集群的过程
{: #vc_nsx-t_addingviewingclusters-adding-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要添加集群的实例。

   确保实例处于**可供使用**状态。否则，无法向实例添加集群。
   {:note}
3. 单击左侧导航窗格上的**基础架构**，然后单击**集群**表右上角的**添加**。
4. 在**添加集群**页面上，输入集群名称。
5. 如果希望托管集群的 {{site.data.keyword.CloudDataCent_notm}} 与托管实例的不同，请在**裸机服务器**下选中**选择其他位置**复选框，然后选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
6. 填写裸机配置。指定 **CPU 型号**、**RAM** 量和 **{{site.data.keyword.baremetal_short}} 数**。
7. 填写存储配置。
  * 如果选择 **vSAN 存储器**，请指定容量和高速缓存磁盘的磁盘类型、磁盘数和 vSAN 许可证版本。如果需要更多存储器，请选中**高性能 Intel Optane** 框。
  * 如果选择 **NFS 存储器**，并且要向所有文件共享添加和配置相同设置，请指定**共享数**、**性能**和**大小 (GB)**。
  * 如果选择 **NFS 存储器**，并且要单独添加和配置文件共享，请选择**单独配置共享**。接着，单击**添加共享存储器**标签旁边的 **+** 图标，然后为每个文件共享选择**性能**和**大小 (GB)**。必须至少选择一个文件共享。
8. 完成网络接口设置。
8. 指定 vSphere 许可证密钥的提供方式：
  * 对于业务合作伙伴用户，会包含 vSphere 许可证 (Enterprise Plus Edition)，该许可证以您的名义购买。
  * 对于非业务合作伙伴的用户，可以选择下列其中一个选项：
      * 如果希望以您自己的名义购买新许可证，请为组件选择**购买时包含**。
      * 如果要对组件使用您自己的 VMware 许可证，请选择**我将提供**并输入您的许可证密钥。
9. 选择网络设置**公用和专用网络**或**仅专用网络**。
10. 在**订单摘要**窗格上，验证集群配置，然后再添加集群。
   1. 复查集群的设置。
   2. 复查集群的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在添加集群之前确认您同意这些条款。
   4. 单击**供应**。

### 向 vCenter Server with NSX-T 实例添加集群后的结果
{: #vc_nsx-t_addingviewingclusters-adding-results}

1. 集群部署会自动启动，并且集群的状态会更改为**正在初始化**。可以通过在实例的**摘要**页面中查看部署历史记录，以检查部署的状态。
2. 集群准备就绪可供使用后，其状态会更改为**可供使用**。将对新添加的集群启用 vSphere 高可用性 (HA) 和 vSphere 分布式资源调度程序 (DRS)。

不能更改集群名称。更改集群名称可能会导致集群中添加或除去 ESXi 服务器的操作失败。
{:important}

## 查看 vCenter Server with NSX-T 实例中集群的过程
{: #vc_nsx-t_addingviewingclusters-viewing-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击实例以查看其中的集群。
3. 在左侧导航窗格上，单击**基础架构**。在**集群**表中，查看有关集群的摘要：
  * **名称**：集群的名称。
  * **ESXi 服务器数**：集群中的 ESXi 服务器数。
  * **CPU**：集群中 ESXi 服务器的 CPU 规范。
  * **定制 vSAN 磁盘数**：集群中的 vSAN 磁盘数，包括磁盘类型和容量。
  * **内存**：集群中 ESXi 服务器的内存总大小。
  * **数据中心位置**：托管集群的 {{site.data.keyword.CloudDataCent_notm}}。
  * **pod**：在其中部署集群的 pod。
  * **状态**：集群的状态。状态可以是下列其中一个值：
    <dl class="dl">
        <dt class="dt dlterm">正在初始化</dt>
        <dd class="dd">正在创建并配置集群。</dd>
        <dt class="dt dlterm">正在修改</dt>
        <dd class="dd">正在修改集群。</dd>
        <dt class="dt dlterm">可供使用</dt>
        <dd class="dd">集群准备就绪，可供使用。</dd>
        <dt class="dt dlterm">正在删除</dt>
        <dd class="dd">正在删除集群。</dd>
        <dt class="dt dlterm">已删除</dt>
        <dd class="dd">集群已删除。</dd>
    </dl>
  * **操作**：单击**删除**图标以删除集群。
4. 单击集群名称以查看 ESXi 服务器、存储和网络接口详细信息：

|项|描述|  
|:------------- |:------------- |
|名称|ESXi 服务器名称的格式为 `<data_center>-<host_prefix><n>.<subdomain_label>.<root_domain>`，其中 `n` 是 ESXi 服务器的序列。|
|版本|ESXi 服务器的版本。|
|凭证|用于访问 ESXi 服务器的用户名和密码。|
|专用 IP|ESXi 服务器的专用 IP 地址。|
|状态|ESXi 服务器的状态，可以是下列某个值：<br> **已添加** ESXi 服务器已添加并随时可供使用。<br> **正在添加** 正在添加 ESXi 服务器。<br> **正在删除** 正在删除 ESXi 服务器。|
{: caption="表 5. ESXi 服务器详细信息" caption-side="top"}

查看存储器详细信息：

|项|描述|  
|:------------- |:------------- |
|名称|数据存储名称。|
|大小|存储的容量。|
|IOPS/GB|存储的性能级别。|
|NFS 协议|存储的 NFS 版本。|
{: caption="表 6. 存储器详细信息" caption-side="top"}

查看网络接口详细信息：

|项|描述|  
|:------------- |:------------- |
|VLAN 编号| 唯一的 VLAN 编号。|
|描述|VLAN 的描述。|
|位置| 数据中心位置。|
|主路由|VLAN 的主路由。|
{: caption="表 7. 网络接口 - VLAN 详细信息" caption-side="top"}

单击**查看资源**以访问 VLAN 详细信息。

查看子网详细信息：

|项|描述|  
|:------------- |:------------- |
|名称|子网名称。单击名称以访问子网详细信息。|
|类型| 子网的类型：主子网或可移植子网。|
|描述|子网的描述。|
{: caption="表 8. 网络接口 - 子网详细信息" caption-side="top"}

查看 IP 详细信息：

|项|描述|  
|:------------- |:------------- |
|IP 数|IP 地址。|
|状态|IP 地址的状态。|
|描述|IP 地址的描述。|
{: caption="表 9. 网络接口 - IP 详细信息" caption-side="top"}

## 从 vCenter Server with NSX-T 实例中删除集群
{: #vc_nsx-t_addingviewingclusters-deleting}

当不再需要集群时，您可能希望将其从实例中删除。

### 删除之前
{: #vc_nsx-t_addingviewingclusters-deleting-prereq}

* 尽可能使用 {{site.data.keyword.vmwaresolutions_full}} 控制台删除集群，因为在 VMware vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。因此，从 vCenter Server 中删除集群仅适用于内部部署集群，或者无法或不会在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理的集群。
* 一次可以删除一个集群。要删除多个集群，必须按顺序依次执行。请等待前一个集群删除后，再删除下一个集群。
* 删除集群之前，请确保集群中的所有节点都已打开电源且正常运行。
* 删除集群时，集群中的所有 VM 也会一起删除且无法恢复。如果要保留这些 VM，请将其迁移到其他集群。
* 无法删除缺省集群。

### 从 vCenter Server with NSX-T 实例中删除集群的过程
{: #vc_nsx-t_addingviewingclusters-deleting-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要从中删除集群的实例。

   确保实例处于**可供使用**状态。否则，无法从实例中删除集群。
   {:note}

3. 在左侧导航窗格上，单击**基础架构**。在**集群**表中，找到要删除的集群，然后单击**操作**列中的**删除**图标。
4. 确认已完成将 VM 迁移到其他集群的操作（如果需要），并确认要删除该集群。

## 相关链接
{: #vc_nsx-t_addingviewingclusters-related}

* [查看 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [扩展和收缩 vCenter Server with NSX-T 实例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
