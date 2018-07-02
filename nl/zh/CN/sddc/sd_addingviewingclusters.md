---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# 添加、查看和删除 Cloud Foundation 实例的集群

订购实例时配置的 ESXi 服务器会分组到缺省集群下。缺省集群名称为：
* 对于在 V2.1 或更高发行版中部署的实例：**MGMT-Cluster-`<subdomain_label>`**
* 对于在 V2.0 或更低发行版中部署的实例：**SDDC-Cluster**

可以向 VMware Cloud Foundation 实例添加您自己的集群以扩展计算和存储容量。在集群中，可以管理 ESXi 服务器以获得更佳的资源分配和高可用性。不再需要添加的集群时，可以从实例中将其删除。

**可用性**：
* 添加集群功能仅可用于部署在（或已升级到）V2.0 和更高发行版中的实例。
* 删除集群功能仅可用于部署在（或已升级到）V2.3 和更高发行版中的实例。  

## 向 Cloud Foundation 实例添加集群

最多可以向一个 Cloud Foundation 实例添加五个集群。

### 系统设置

向 Cloud Foundation 实例添加集群时，必须指定以下设置。

#### 集群名称

集群名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 集群名称必须以字母数字字符开头和结尾。
* 集群名称的最大长度为 30 个字符。
* 集群名称在 Cloud Foundation 实例中必须唯一。

#### 数据中心位置

缺省情况下，集群的 {{site.data.keyword.CloudDataCent}} 位置设置为 Cloud Foundation 实例的 {{site.data.keyword.CloudDataCent_notm}}。可以将集群部署到与所部署实例不同的 {{site.data.keyword.CloudDataCent_notm}}，但必须确保这两个 {{site.data.keyword.CloudDataCents_notm}} 之间的网络等待时间少于 150 毫秒。要检查网络等待时间，可以使用 [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} 等工具。

可供使用的数据中心取决于您为部署选择的裸机服务器配置。如果选择的是**定制**配置，那么所选数据中心包含更多 pod 时，还可以将集群部署到其他 {{site.data.keyword.cloud}} 基础架构 pod。这在部署了初始实例的缺省 {{site.data.keyword.cloud_notm}} 基础架构 pod 达到其最大容量时非常有用。

**注**：**小型**和**大型**裸机服务器标准化配置使用缺省 pod，该 pod 不能更改。

如果将集群部署到其他数据中心或 pod，那么将订购三个额外的 VLAN 以用于订购的 {{site.data.keyword.baremetal_short}}。

### 裸机服务器设置

可以选择**定制**或**预配置**。

#### 定制

对于**定制**设置，您有许多 **CPU 型号**和 **RAM** 选项。可用选项可能有所不同，具体取决于初始部署实例的版本。

表 1. 定制 {{site.data.keyword.baremetal_short}} 的选项

|CPU 选项|RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon E5-2620 V4 / 共 16 个核心，2.1 GHz|128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz|128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz|128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|128 GB、192 GB、384 GB、768 GB、1.5 TB|

#### 预配置

对于**预配置**设置，可以根据需求选择**裸机服务器配置**：
* 小型（双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz / 128 GB RAM / 12 个磁盘）
* 大型（双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz / 512 GB RAM / 12 个磁盘）

### vSAN 存储器设置

对于**预配置**裸机服务器配置，无法更改 vSAN 存储设置：
* 对于**小型**配置，会订购两个 1.9 TB SSD SED 磁盘驱动器。
* 对于**大型**配置，会订购四个 3.8 TB SSD SED 磁盘驱动器。

对于**定制**裸机服务器配置，可以通过指定 vSAN 容量磁盘数、磁盘类型和大小来定制 vSAN 存储器，以满足您的存储需求。

### 许可证设置

可以为集群中的 VMware 组件（包括 VMware vSphere 和 VMware vSAN）指定许可选项：
* 对于业务合作伙伴用户，会包含 vSphere 许可证 (Enterprise Plus Edition) 和 vSAN 许可证，该许可证以您的名义购买。但是，您必须指定 vSAN 许可证的版本。
* 对于非业务合作伙伴用户，可以通过选择**购买时包含**对组件使用 IBM 提供的 VMware 许可证，或者可以通过选择**我将提供**并输入您自己的许可证密钥以自带许可证 (BYOL)。

## 向 Cloud Foundation 实例添加集群的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**部署的实例**。
2. 在 **Cloud Foundation 实例**表中，单击要添加集群的实例。

   **注**：确保实例处于**可供使用**状态。否则，无法向实例添加集群。

3. 单击左侧导航窗格上的**基础架构**，然后单击**集群**表右上角的**添加**。
4. 在**添加集群**页面上，输入集群名称。
5. 如果希望托管集群的 {{site.data.keyword.CloudDataCent_notm}} 与托管实例的不同，请在**裸机服务器**下选中**选择其他位置**复选框，然后选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
6. 完成裸机配置：
   * 如果选择的是**定制**，请选择 **CPU 型号**和 **RAM** 大小。
   * 如果选择的是**预配置**，请选择**裸机服务器配置**。
7. 完成存储配置：
   * 如果对裸机配置选择的是**定制**，请指定 **vSAN 容量磁盘数**以及 **vSAN 容量磁盘的磁盘类型和大小**。
   * 如果对裸机配置选择的是**预配置**，请注意，无法更改**小型**和**大型**裸机服务器配置的存储设置。
8. 指定许可证密钥的提供方式：
   * 对于业务合作伙伴用户，会包含 vSphere 许可证 (Enterprise Plus Edition) 和 vSAN 许可证，该许可证以您的名义购买。但是，您必须指定 vSAN 许可证的版本。
   * 对于非业务合作伙伴用户，可以选择以下某个选项：
       * 如果希望以您自己的名义购买新许可证，请为组件选择**购买时包含**。对于 VMware vSAN，还要选择许可证版本。
       * 如果要对组件使用您自己的 VMware 许可证，请选择**我将提供**并输入组件的许可证密钥。
9. 在**订单摘要**窗格上，验证集群配置，然后再添加集群。
   1. 复查集群的设置。
   2. 复查集群的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在添加集群之前确认您同意这些条款。
   4. 单击**供应**。

### 向 Cloud Foundation 实例添加集群后的结果

1. 集群部署会自动启动，并且集群的状态会更改为**正在初始化**。可以通过在实例摘要页面上查看部署历史记录，以检查部署的状态。
2. 集群准备就绪可供使用后，其状态会更改为**可供使用**。将对新添加的集群启用 vSphere 高可用性 (HA) 和 vSphere 分布式资源调度程序 (DRS)。

**重要信息**：不能更改集群名称。更改集群名称可能会导致集群中添加或除去 ESXi 服务器的操作失败。

## 查看 Cloud Foundation 实例中的集群

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**部署的实例**。
2. 在 **Cloud Foundation 实例**表中，单击实例以查看其中的集群。
3. 在左侧导航窗格上，单击**基础架构**。在**集群**表中，查看有关集群的摘要：
   * **名称**：集群的名称。
   * **ESXi 服务器数**：集群中的 ESXi 服务器数。
   * **CPU**：集群中 ESXi 服务器的 CPU 规范。
   * **定制 vSAN 磁盘数**：集群中的 vSAN 磁盘数，包括磁盘类型和容量。
   * **内存**：集群中 ESXi 服务器的内存总大小。
   * **数据中心位置**：托管集群的数据中心。
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
4. 单击集群名称以查看 ESXi 服务器及其信息的列表：

   * **名称**：ESXi 服务器名称的格式为 `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中：

      `host_prefix` 是主机名前缀，
      `n` 是 ESXi 服务器的序列，
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
   * vSAN 许可证和 vSphere 许可证的详细信息。仅当在集群订购期间选择使用您自己的 VMware 许可证 (BYOL) 时，vSphere 许可证详细信息才可用：
       * **许可证类型**：vSAN 许可证或 vSphere 许可证。
       * **订购类型**：许可证由用户提供 (BYOL)，或以用户名义购买。
       * **许可证版本**：许可证的版本。
       * **许可证密钥**：许可证密钥。
       * **总容量 (CPU)**：许可证提供的 CPU 总容量或 CPU 数。
       * **可用容量 (CPU)**：许可证中当前可用的容量。

## 从 Cloud Foundation 实例中删除集群

当不再需要集群时，您可能希望将其从实例中删除。

### 删除之前

* 使用此过程从部署在 V2.3 或更高发行版中的实例中删除集群。
* 对于在 V2.2 或更低版本实例中部署的集群，必须将实例升级到 V2.3，才能删除已添加到实例的集群。
* 一次可以删除一个集群。要删除多个集群，必须按顺序依次执行；请等待前一个集群删除后，再尝试删除下一个集群。
* 删除集群之前，请确保集群中的所有节点都已打开电源且正常运行。
* 删除集群时，集群中的所有 VM（虚拟机）也会一起删除且无法恢复。如果要保留这些 VM，请将其迁移到其他集群。
* 无法删除缺省集群。

## 从 Cloud Foundation 实例中删除集群的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**部署的实例**。
2. 在 **Cloud Foundation 实例**表中，单击要从中删除集群的实例。

   **注**：确保实例处于**可供使用**状态。否则，无法从实例中删除集群。

3. 在左侧导航窗格上，单击**基础架构**。在**集群**表中，找到要删除的集群，然后单击**删除**图标。
4. 确认已完成将 VM 迁移到其他集群（如果适用），并确认要删除该集群。

## 相关链接

* [查看 Cloud Foundation 实例](sd_viewinginstances.html)
* [扩展和收缩 Cloud Foundation 实例的容量](sd_addingremovingservers.html)
