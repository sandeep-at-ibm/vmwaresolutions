---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-02"

---

# 订购 vCenter Server with Hybridity Bundle 实例

要部署灵活且可定制的 VMware 虚拟化平台，以最适合您的工作负载需求，请订购 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 实例。vCenter Server with Hybridity Bundle 实例订单中包含 VMware Hybrid Cloud Extension (HCX) 许可，并授权您使用 VMware HCX on {{site.data.keyword.cloud_notm}} 服务。您还可以添加服务，例如用于灾难恢复的 [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html)。

## 需求

确保已完成以下任务：
*  已在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。有关更多信息，请参阅[管理用户帐户和设置](../vmonic/useraccount.html)。
*  已查看[针对 vCenter Server with Hybridity Bundle 的需求和规划](vc_hybrid_planning.html)中的信息。
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

订购 vCenter Server with Hybridity Bundle 实例时，必须指定以下系统设置。

### 实例名称

实例名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 实例名称必须以字母数字字符开头和结尾。
* 实例名称的最大长度为 10 个字符。
* 实例名称在您的帐户中必须唯一。

### 主实例或辅助实例

选择是订购新的主实例还是为现有主实例订购辅助实例。

## 许可证设置

vCenter Server with Hybridity Bundle 实例订单中包含以下许可证。您必须将 NSX 许可证版本指定为 **Advanced** 或 **Enterprise**。

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition（Advanced 或 Enterprise）6.4
* VMware vSAN 6.6 许可证版本（Advanced 或 Enterprise）。

**注意：**
* vCenter Server with Hybridity Bundle 实例不支持自带许可证。
* 用户界面上指示了最低许可证版本。如果支持不同的组件版本，那么可以选择所需的版本。

## 裸机服务器设置

裸机设置基于 {{site.data.keyword.CloudDataCent_notm}} 和定制配置。

对于 vSAN 配置，初始集群和部署后集群都需要 4 个 ESXi 服务器。所有 ESXi 服务器共享相同的配置。部署后，可以再添加四个集群。

### 数据中心位置

选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。

### 定制

为定制的裸机服务器指定 CPU 型号和 RAM 量。

表 2. 定制 {{site.data.keyword.baremetal_short}} 的选项

| CPU 模型选项   |RAM 选项|
|:------------- |:------------- |
|双 Intel Xeon E5-2620 V4 / 共 16 个核心，2.1 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz|64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB|
|双 Intel Xeon Silver 4110 处理器 / 共 16 个核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
|双 Intel Xeon Gold 6140 处理器 / 共 36 个核心，2.3 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB|
### 裸机服务器的数量

缺省情况下已选择 4 个 ESXi 服务器，对此无法进行更改。

## 存储设置

vCenter Server with Hybridity Bundle 实例订单中包含 VMware vSAN 6.6。订购该实例时，必须指定以下存储设置：

* **vSAN 容量磁盘的磁盘类型和大小**：选择满足共享存储器需求的容量。
* **vSAN 容量磁盘数**：选择要添加的 vSAN 共享存储器的磁盘数。磁盘数量必须为 2、4、6 或 8 个。

## 网络接口设置

订购 vCenter Server with Hybridity Bundle 实例时，必须指定以下网络接口设置。

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

**注**：主机和 VM（虚拟机）的 FQDN（标准域名）的最大长度为 50 个字符。域名必须符合此最大长度。

### 订购新的 VLAN

选择**订购新的 VLAN** 可订购一个新的公用 VLAN 和两个新的专用 VLAN。

订购实例时，需要包含一个公用 VLAN 和两个专用 VLAN。两个专用 VLAN 用于中继到每个裸机服务器中。

### 选择现有 VLAN

根据选择的 {{site.data.keyword.CloudDataCent_notm}}，可能会有现有公用和专用 VLAN 可用。

订购实例时，需要包含一个公用 VLAN 和两个专用 VLAN。两个专用 VLAN 用于中继到每个裸机服务器中。

选择**选择现有 VLAN** 可复用现有公用 VLAN 和专用 VLAN，并可从可用的 VLAN 和子网中进行选择。

**重要信息：**
* 确保所选 VLAN 上的防火墙配置不会阻止管理数据流量。
* 确保选择的所有 VLAN 都在同一 pod 中，因为 ESXi 服务器不能在混合 pod VLAN 上进行供应。

### DNS 配置

为实例选择域名系统 (DNS) 配置：

* **一个用于 Active Directory/DNS 的公共 Windows VSI**：一个用于 Microsoft Active Directory (AD) 的 Microsoft Windows Server VSI，充当在其中注册主机和 VM 的实例的 DNS，已部署并且可进行查找。
* **管理集群上两个高可用性专用 Windows Server VM**：部署了两个 Microsoft Windows 虚拟机，以帮助增强安全性和稳健性。

**重要信息**：如果将实例配置为使用两个 Microsoft Windows VM，那么必须提供两个 Microsoft Windows Server 2012 R2 许可证。使用 Microsoft Windows Server 2012 R2 Standard Edition 许可证和/或 Microsoft Windows Server 2012 R2 Datacenter Edition 许可证。

每个许可证只能分配给一个物理服务器，并且最多包含两个物理处理器。一个 Standard Edition 许可证支持每个双处理器服务器运行两个虚拟化的 Microsoft Windows VM。因此，需要两个许可证，因为两个 Microsoft Windows VM 会部署在两个不同的主机中。

您有 30 天的时间来激活 VM。

有关订购 Windows 许可的更多信息，请参阅 [Windows Server 2012 R2 文档](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2)。

## 服务设置

订购 vCenter Server with Hybridity Bundle 实例时，还可以订购其他服务。有关服务的更多信息，请参阅 [vCenter Server with Hybridity Bundle 实例的可用服务](vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances)。

## 订单摘要

根据为实例和附加组件服务选择的配置，估算成本会立即生成并显示在右侧窗格的**订单摘要**部分中。单击右侧窗格底部的**定价详细信息**可生成提供估算详细信息的 PDF 文档。

## 过程

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格中的 **VMware**，然后单击**虚拟数据中心**部分中的 **vCenter Server**。
2. 在 **VMware vCenter Server on IBM Cloud** 页面上，单击 **vCenter Server with Hybridity Bundle** 卡，然后单击**创建**。
3. 在 **vCenter Server** 页面上，输入实例名称。
4. 选择实例类型：
   * 单击**主实例**以在环境中部署单个实例，或者在多站点拓扑中部署第一个实例。
   * 单击**辅助实例**以将该实例与环境中的现有（主）实例连接以获取高可用性，并完成以下步骤：
     1. 选择要与辅助实例连接的主实例。
     2. 输入主实例的 PSC 管理员密码。
5. 选择 NSX 许可证版本和 vSAN 许可证版本。
6. 完成裸机服务器设置。
  1. 选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
  2. 选择**定制** CPU 型号和 **RAM** 量。

  **注**：缺省情况下，**裸机服务器数**设置为 4，且无法更改。

7. 填写存储配置。
  1. 选择 **vSAN 容量磁盘的磁盘类型和大小**。
  2. 选择 **vSAN 容量磁盘数**。
8. 完成网络接口配置。
  1. 输入主机名前缀、子域标签和根域名。
  2. 选择 VLAN 配置。
     *  如果要订购新的公用和专用 VLAN，请单击**订购新的 VLAN**。
     *  如果要复用可用的现有公用和专用 VLAN，请单击**选择现有 VLAN**，然后选择公用 VLAN、主子网、专用 VLAN、专用主子网和辅助专用 VLAN。
  3. 选择 DNS 配置。
9. 通过单击相应的服务卡，选择要部署到实例中的附加组件服务。如果服务需要配置，请完成特定于服务的设置，然后单击相应卡上的**添加服务**。  
有关如何为服务提供设置的信息，请参阅相应的服务订购主题。

8. 在**订单摘要**窗格上，验证实例配置，然后再下订单。
   1. 复查实例的设置。
   2. 复查实例的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在订购实例之前确认您同意这些条款。
   4. 单击**供应**。

## 结果

实例部署会自动启动。您将收到说明订单正在处理的确认，并且您可以通过查看实例详细信息来检查部署的状态。

成功部署实例后，[vCenter Server with Hybridity Bundle 实例的技术规范](vc_hybrid_overview.html#technical-specifications-for-vcenter-server-with-hybridity-bundle-instances)中描述的组件已安装在 VMware 虚拟平台上。缺省情况下，订购的 ESXi 服务器将分组为 **cluster1**。如果订购了更多服务，那么这些服务的部署将在订单完成后启动。

实例准备就绪可供使用后，该实例的状态会更改为**可供使用**，并且您将收到通过电子邮件发送的通知。

订购辅助实例时，在完成辅助实例订单后，可能会重新启动主实例（链接到辅助实例）的 VMware vSphere Web Client。

## 后续步骤

查看和管理订购的 vCenter Server with Hybridity Bundle 实例。

**重要信息**：您只能在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 组件，而不能在 {{site.data.keyword.slportal}} 中或在控制台外部通过其他任何方法来进行管理。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步。

**注意**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部管理任何 {{site.data.keyword.vmwaresolutions_short}} 组件（在订购实例时安装到 {{site.data.keyword.cloud_notm}} 帐户中）可能会使环境变得不稳定。这些管理活动包括：
*  添加、修改、返回或除去组件
*  通过添加或除去 ESXi 服务器来扩展或收缩实例容量
*  关闭组件电源
*  重新启动服务

   这些活动的例外情况包括在 {{site.data.keyword.slportal}} 中管理共享存储器文件共享。此类活动包括：订购、删除（如果已安装，可能会影响数据存储）、授权和安装共享存储器文件共享。

### 相关链接

* [注册 {{site.data.keyword.cloud_notm}} 帐户](../vmonic/signing_softlayer_account.html)
* [查看 vCenter Server with Hybridity Bundle 实例](vc_hybrid_viewinginstances.html)
* [vCenter Server with Hybridity Bundle 实例的多站点配置](vc_hybrid_multisite.html)
* [添加和查看 vCenter Server with Hybridity Bundle 实例的集群](vc_hybrid_addingviewingclusters.html)
* [扩展和收缩 vCenter Server with Hybridity Bundle 实例的容量](vc_hybrid_addingremovingservers.html)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](vc_hybrid_addingremovingservices.html)
* [删除 vCenter Server with Hybridity Bundle 实例](vc_hybrid_deletinginstance.html)
