---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-18"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 添加、查看和删除 vCenter Server with Hybridity Bundle 实例的集群
{: #vc_hybrid_addingviewingclusters}

缺省情况下，订购实例时配置的 ESXi 服务器会分组为 **cluster1**。

可以向 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 实例添加集群以扩展计算和存储容量。在集群中，管理 ESXi 服务器以获得更佳的资源分配和高可用性。不再需要添加的集群时，请从实例中将其删除。

## 向 vCenter Server with Hybridity Bundle 实例添加集群
{: #vc_hybrid_addingviewingclusters-adding}

可添加到实例的集群数取决于实例版本：
* 对于部署在（或已升级到）V2.5 和更高版本中的实例，集群数、主机数和 VM 数将决定可以添加的最大集群数限制。您必须遵守适用于部署的 VMware 大小调整准则和限制。
* 对于部署在（或已升级到）V2.3 和更高版本中的实例，最多可以添加 10 个集群。

有关最大限制的更多信息，请参阅 [VMware 配置最大值](https://configmax.vmware.com/home){:new_window}。

### 系统设置
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

为 vCenter Server with Hybridity Bundle 实例添加集群时，必须指定以下设置。

#### 集群名称
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

集群名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 集群名称必须以字母数字字符开头和结尾。
* 集群名称的最大长度为 30 个字符。
* 集群名称在 vCenter Server with Hybridity Bundle 实例中必须唯一。

#### 数据中心位置
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

缺省情况下，集群的 {{site.data.keyword.CloudDataCent_notm}} 位置设置为 vCenter Server 实例的 {{site.data.keyword.CloudDataCent_notm}}。可以将集群部署到与所部署实例不同的 {{site.data.keyword.CloudDataCent_notm}}，但必须确保这两个 {{site.data.keyword.CloudDataCents_notm}} 之间的网络等待时间少于 150 毫秒。要检查网络等待时间，请使用 [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} 等工具。

如果将集群部署到其他 {{site.data.keyword.CloudDataCent_notm}} 或 {{site.data.keyword.cloud_notm}} 基础架构 pod，应再订购三个 VLAN 用于已订购的 {{site.data.keyword.baremetal_short}}。

### 裸机服务器设置
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

可以选择 **Skylake** 或 **Broadwell**。选项可能有所不同，具体取决于初始部署实例的版本。

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

选择 **Skylake** 时，可以根据需要选择 CPU 和 RAM 组合。

表 1. Skylake 裸机服务器的选项

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

选择 **Broadwell** 时，可以根据需要选择 CPU 和 RAM 组合。

表 2. Broadwell 裸机服务器的选项

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon E5-2620 V4 / 共 16 个核心，2.1 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|四核 Intel Xeon E7-4820 V4 / 共 40 个核心，1.9 GHz|128 GB、256 GB、512 GB、1 TB、2 TB、3 TB|
|四核 Intel Xeon E7-4850 V4 / 共 64 个核心，2.2 GHz|128 GB、256 GB、512 GB、1 TB、2 TB、3 TB|

#### 裸机服务器的数量
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

一个集群至少需要两个 {{site.data.keyword.baremetal_short}}。

可以为一个集群最多添加 59 个 {{site.data.keyword.baremetal_short}}，并且一次可以添加 1 到 59 个 ESXi 服务器。

部署后，最多可以再创建四个集群。对于 VMware vSAN 存储器，初始集群和部署后集群都需要 4 个服务器。

### vSAN 存储器设置
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

vCenter Server with Hybridity Bundle 实例订单中包含 VMware vSAN 6.6。请指定以下 vSAN 选项：
* **vSAN 容量磁盘的磁盘类型和大小**：选择与所需容量磁盘相应的选项。
* **vSAN 容量磁盘数**：指定要添加的容量磁盘数。
* 如果要添加的容量磁盘数超过 8 个的限制，请选中**高性能 Intel Optane** 框。此选项用于提供两个额外的容量磁盘托架，总共可容纳 10 个容量磁盘；此选项对于需要更短等待时间和更高 IOPS 吞吐量的工作负载而言非常有用。

  **高性能 Intel Optane** 选项仅可用于 Skylake CPU 型号双 Intel Xeon Gold 5120 和双 Intel Xeon Gold 6140。
  {:note}

* 查看 **vSAN 高速缓存磁盘的磁盘类型**和 **vSAN 高速缓存磁盘数**值。这些值依赖于是否选中了**高性能 Intel Optane** 框。
* **vSAN 许可证**：选择 VMware vSAN 6.6 许可证版本（Advanced 或 Enterprise）。

### 许可证设置
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

用于以下 VMware 组件的 IBM 提供的许可证：
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4（Advanced Edition 或 Enterprise Edition）

### 网络接口设置
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

网络接口卡 (NIC) 设置基于您选择的是**公用和专用网络**还是**仅专用网络**。以下附加组件服务需要公共 NIC，并且这些服务在选择了专用选项时不可用：

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### 订单摘要
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

根据为集群选择的配置，估算成本会立即生成并显示在**订单摘要**右侧窗格中。

## 向 vCenter Server with Hybridity Bundle 实例添加集群的过程
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击实例以查看其中的集群。

   确保实例状态为**可供使用**。否则，无法向实例添加集群。
   {:note}

3. 单击左侧导航窗格上的**基础架构**，然后单击**集群**表右上角的**添加**。
4. 在**添加集群**页面上，输入集群名称。
5. 托管集群的 {{site.data.keyword.CloudDataCent_notm}} 可以与托管实例的不同。为此，请在**裸机服务器**下选中**选择其他位置**复选框，然后选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
6. 针对裸机配置，选择 **CPU 型号**、**RAM** 量和**裸机服务器数**。
7.  选择 **vSAN 存储器**，并指定容量和高速缓存磁盘的磁盘类型以及磁盘数。如果需要更多存储器，请选中**高性能 Intel Optane** 框。
8. 为 VMware vSAN 选择许可证版本，以进行许可证配置。
9. 选择网络设置**公用和专用网络**或**仅专用网络**。
10. 在**订单摘要**窗格上，验证集群配置，然后再添加集群。
   1. 复查集群的设置。
   2. 复查集群的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在添加集群之前确认您同意这些条款。
   4. 单击**供应**。

### 向 vCenter Server with Hybridity Bundle 实例添加集群后的结果
{: #vc_hybrid_addingviewingclusters-adding-results}

1. 集群部署会自动启动，并且集群的状态会更改为**正在初始化**。可以通过在实例的**摘要**页面上查看部署历史记录，以检查部署的状态。
2. 集群准备就绪可供使用后，其状态会更改为**可供使用**。将对新添加的集群启用 vSphere 高可用性 (HA) 和 vSphere 分布式资源调度程序 (DRS)。

不能更改集群名称。更改集群名称可能会导致集群中添加或除去 ESXi 服务器的操作失败。
{:important}

## 查看 vCenter Server with Hybridity Bundle 实例中集群的过程
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

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
4. 单击集群名称以查看 ESXi 服务器、存储和网络接口详细信息：

  * ESXi 服务器详细信息：
     * **名称**：ESXi 服务器名称的格式为 `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中：

       `host_prefix` 是主机名前缀，

       `n` 是服务器的序列，

       `subdomain_label` 是子域标签，

       `root_domain` 是根域名。

     * **版本**：ESXi 服务器的版本。
     * **凭证**：用于访问 ESXi 服务器的用户名和密码。
     * **专用 IP**：ESXi 服务器的专用 IP 地址。
     * **状态**：ESXi 服务器的状态，可以是下列其中一个值：
        <dl class="dl">
        <dt class="dt dlterm">已添加</dt>
        <dd class="dd">ESXi 服务器已添加并准备就绪可供使用。</dd>
        <dt class="dt dlterm">正在添加</dt>
        <dd class="dd">正在添加 ESXi 服务器。</dd>
        <dt class="dt dlterm">正在删除</dt>
        <dd class="dd">正在删除 ESXi 服务器。</dd>
        </dl>
  * 存储详细信息：
    * **名称**：数据存储名称。
    * **大小**：存储器的容量。
    * **IOPS/GB**：存储器的性能级别。
    * **NFS 协议**：存储器的 NFS 版本。
  * 网络接口 - VLAN 详细信息：
    * **VLAN 编号**：唯一的 VLAN 编号。
    * **描述**：VLAN 的描述。
    * **位置**：数据中心位置。
    * **主路径**：VLAN 的主路径。
    单击**查看资源**以访问 VLAN 详细信息。
  * 网络接口 - 子网详细信息：
    * **名称**：子网名称。单击名称以访问子网详细信息。
    * **类型**：子网的类型：主子网或可移植子网。
    * **描述**：子网的描述。
  * 网络接口 - IP 详细信息：
    * **IP**：IP 地址。
    * **状态**：IP 地址的状态。
    * **描述**：IP 地址的描述。

## 从 vCenter Server with Hybridity Bundle 实例中删除集群
{: #vc_hybrid_addingviewingclusters-deleting}

当不再需要集群时，您可能希望将其从实例中删除。

### 删除之前
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* 一次可以删除一个集群。要删除多个集群，必须按顺序依次执行；请等待前一个集群删除后，再删除下一个集群。
* 删除集群之前，请确保集群中的所有节点都已打开电源且正常运行。
* 删除集群时，集群中的所有 VM（虚拟机）也会一起删除且无法恢复。如果要保留这些 VM，请将其迁移到其他集群。
* 无法删除缺省集群。

## 从 vCenter Server with Hybridity Bundle 实例中删除集群的过程
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要从中删除集群的实例。

   确保实例处于**可供使用**状态。否则，无法从实例中除去集群。
   {:note}

3. 在左侧导航窗格上，单击**基础架构**。在**集群**表中，找到要删除的集群，然后单击**操作**列中的**删除**图标。

## 相关链接
{: #vc_hybrid_addingviewingclusters-related}

* [查看 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [扩展和收缩 vCenter Server with Hybridity Bundle 实例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
