---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-02"

---

# 添加、查看和删除 vCenter Server with Hybridity Bundle 实例的集群

缺省情况下，订购实例时配置的 ESXi 服务器会分组为 **cluster1**。

可以向 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 实例添加集群以扩展计算和存储容量。在集群中，可以管理 ESXi 服务器以获得更佳的资源分配和高可用性。不再需要添加的集群时，可以从实例中将其删除。

## 向 vCenter Server with Hybridity Bundle 实例添加集群

最多可以向 vCenter Server with Hybridity Bundle 实例添加 10 个集群。

### 系统设置

为 vCenter Server with Hybridity Bundle 实例添加集群时，必须指定以下设置。

#### 集群名称

集群名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 集群名称必须以字母数字字符开头和结尾。
* 集群名称的最大长度为 30 个字符。
* 集群名称在 vCenter Server with Hybridity Bundle 实例中必须唯一。

#### 数据中心位置

缺省情况下，集群的 {{site.data.keyword.CloudDataCent_notm}} 位置设置为 vCenter Server 实例的 {{site.data.keyword.CloudDataCent_notm}}。可以将集群部署到与所部署实例不同的 {{site.data.keyword.CloudDataCent_notm}}，但必须确保这两个 {{site.data.keyword.CloudDataCents_notm}} 之间的网络等待时间少于 150 毫秒。要检查网络等待时间，可以使用 [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} 等工具。

如果将集群部署到其他 {{site.data.keyword.CloudDataCent_notm}} 或 {{site.data.keyword.cloud_notm}} 基础架构 pod，那么可订购三个额外的 VLAN 以用于订购的 {{site.data.keyword.baremetal_short}}。

### 裸机服务器设置

#### 定制

指定用于裸机服务器的 CPU 型号和 RAM。可用选项可能有所不同，具体取决于初始部署实例的版本。

表 2. 定制裸机服务器的选项

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon E5-2620 V4 / 共 16 个核心，2.1 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|96 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|

#### 裸机服务器的数量

一个集群至少需要 2 个 {{site.data.keyword.baremetal_short}}。

可以为一个集群最多添加 59 个 {{site.data.keyword.baremetal_short}}，并且一次可以添加 1 到 59 个 ESXi 服务器。

部署后，最多可以再创建四个集群。对于 VMware vSAN 存储器，初始集群和部署后集群都需要 4 个服务器。

### vSAN 存储器设置

vCenter Server with Hybridity Bundle 实例订单中包含 VMware vSAN 6.6。您必须将许可证版本指定为 **Advanced** 或 **Enterprise**。

* **vSAN 容量磁盘的磁盘类型和大小**：选择满足共享存储器需求的容量。
* **vSAN 容量磁盘数**：选择要添加的 vSAN 共享存储器的磁盘数。磁盘数量必须为 2、4、6 或 8 个。
* 选择 VMware vSAN 6.6 许可证版本（Advanced 或 Enterprise）。

### 许可证设置

用于以下各项的 IBM 提供的 VMware 许可证：
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition（Advanced 或 Enterprise）6.4

### 订单摘要

根据为集群选择的配置，估算成本会立即生成并显示在**订单摘要**右侧窗格中。

## 向 vCenter Server with Hybridity Bundle 实例添加集群的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击实例以查看其中的集群。

   **注**：确保实例处于**可供使用**状态。否则，无法向实例添加集群。

3. 单击左侧导航窗格上的**基础架构**，然后单击**集群**表右上角的**添加**。
4. 在**添加集群**页面上，输入集群名称。
5. 如果希望托管集群的 {{site.data.keyword.CloudDataCent_notm}} 与托管实例的不同，请在**裸机服务器**下选中**选择其他位置**复选框，然后选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
6. 针对裸机配置，选择 **CPU 型号**、**RAM** 量和**裸机服务器数**。
7.  选择 **vSAN 存储器**，然后为存储配置选择 **vSAN 容量磁盘数**以及 **vSAN 容量磁盘的磁盘类型和大小**。
8. 为 VMware vSAN 选择许可证版本，以进行许可证配置。
9. 在**订单摘要**窗格上，验证集群配置，然后再添加集群。
   1. 复查集群的设置。
   2. 复查集群的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在添加集群之前确认您同意这些条款。
   4. 单击**供应**。

### 向 vCenter Server with Hybridity Bundle 实例添加集群后的结果

1. 集群部署会自动启动，并且集群的状态会更改为**正在初始化**。可以通过在实例的**摘要**页面上查看部署历史记录，以检查部署的状态。
2. 集群准备就绪可供使用后，其状态会更改为**可供使用**。将对新添加的集群启用 vSphere 高可用性 (HA) 和 vSphere 分布式资源调度程序 (DRS)。

**重要信息**：不能更改集群名称。更改集群名称可能会导致集群中添加或除去 ESXi 服务器的操作失败。

## 查看 vCenter Server with Hybridity Bundle 实例中的集群

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
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
4. 单击集群名称以查看 ESXi 服务器及其存储的详细信息：

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

## 从 vCenter Server with Hybridity Bundle 实例中删除集群

当不再需要集群时，您可能希望将其从实例中删除。

### 删除之前

* 一次可以删除一个集群。要删除多个集群，必须按顺序依次执行；请等待前一个集群删除后，再尝试删除下一个集群。
* 删除集群之前，请确保集群中的所有节点都已打开电源且正常运行。
* 删除集群时，集群中的所有 VM（虚拟机）也会一起删除且无法恢复。如果要保留这些 VM，请将其迁移到其他集群。
* 无法删除缺省集群。

## 从 vCenter Server with Hybridity Bundle 实例中删除集群的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击要从中删除集群的实例。

   **注**：确保实例处于**可供使用**状态。否则，无法从实例中除去集群。

3. 在左侧导航窗格上，单击**基础架构**。在**集群**表中，找到要删除的集群，然后单击**操作**列中的**删除**图标。

### 相关链接

* [查看 vCenter Server with Hybridity Bundle 实例](vc_hybrid_viewinginstances.html)
* [扩展和收缩 vCenter Server with Hybridity Bundle 实例的容量](vc_hybrid_addingremovingservers.html)
