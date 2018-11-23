---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# 关于更改 vCenter Server 工件的注意事项

更改保留用于 {{site.data.keyword.vmwaresolutions_full}} 的用户、资源或子网可能会影响管理操作。

**重要信息**：不要在 VMware vSphere Web Client 上的**用户和组**页面中编辑 **ic4v-vCenter** 组的全局许可权。此类更改包括：更改用户名、删除用户或更改其密码。

## automation 标识

**automation** 标识是由 {{site.data.keyword.vmwaresolutions_short}} 控制台中提供的自动化操作使用的用户帐户。

不能更改用于控制台中自动化操作的用户和密码，否则依赖于这些凭证的控制台操作可能会失败。

## 特定于服务的用户帐户

每个服务在 vCenter Server 中都会创建一个内部用户帐户。此帐户是必需的，有了此帐户，与服务关联的管理操作才能连接到 vCenter Server 以对该服务执行操作。

**重要信息**：为了防止发生中断和连接问题，如果更改此用户帐户的用户标识、密码或密码到期时间设置，请确保同时更新关联服务中的相应信息。

此帐户的用户标识的格式为 `<service_name>-<truncated service_uuid>@test.local` 或 `<service_name>-<truncated service_uuid>@example-domain.local`。例如，Veeam on {{site.data.keyword.cloud_notm}} 服务用于连接到 vCenter Server 以执行安排的备份的用户标识为 `Veeam-<Veeam_uuid>@test.local`。

**注**：`<service_name>` 和 `<service_uuid>` 一起被截断为 20 个字符。

## vCenter Server 实例（V1.9 和更高版本）的 VMware 资源

对于 V1.9 和更高版本中部署的实例，如果 vCenter Server 实例处于**可供使用**状态，那么可以在 VMware vSphere Web Client 中修改 VMware 虚拟数据中心、集群、交换机、端口组和客户数据存储名称。但是，不能更改管理数据存储的缺省值：**vsanDatastore**（对于 vSAN 实例）和 **management-share**（对于网络文件系统 (NFS) 实例）。

## vCenter Server 实例（V1.8 和更低版本）的 VMware 资源

下表列出了 SSO 管理员在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改 VMware vCenter Server 资源时，可能会影响的操作。如果用于恢复的解决方案可用，那么还会提供该解决方案。

下表适用于在 V1.8 和更低版本上部署的实例，以及在 V1.8 和更低版本上部署且已升级到 V1.9 或更高版本的实例。

表 1. 通过更改 VMware 资源影响的操作

|尝试的更改|影响的操作|严重性|恢复方法|
|:------------- |:------------- |:--------------|:--------------|
|更改 VMware 虚拟数据中心名称。|添加 VMware 虚拟数据中心可能会失败，因为新 ESXi 服务器无法连接更改后的虚拟数据中心。|重要|将 VMware 虚拟数据中心名称更改回原始名称。|
|更改任何端口组名称。|添加 ESXi 服务器可能会失败。|重要|将端口组名称更改回原始名称。|
|更改集群名称。|添加 ESXi 服务器可能会失败。|重要|将集群名称更改回原始名称。
|更改公共或专用分布式虚拟交换机 (DVS) 名称。|添加 ESXi 服务器可能会失败。|重要|将公共或专用分布式虚拟交换机 (DVS) 名称更改回原始名称。
|更改使用 vSAN 的实例中的 vSAN 数据存储名称。|添加 ESXi 服务器可能会失败。<br><br>升级实例可能会失败。|重要|将 vSAN 数据存储名称更改回原始名称 **vsanDatastore**。
|更改使用 NFS 的实例中的管理 NFS 数据存储名称。|添加 ESXi 服务器可能会失败。<br><br>升级实例可能会失败。|重要|将 NFS 管理数据存储名称更改回原始名称 **management-share**，然后在 ESXi 服务器上将 NFS 数据存储重新安装为只读。

下表列出了禁用对各种资源的 SSH 或 shell 访问时可能会受影响的操作。

表 2. 受 SSH 和 shell 访问影响的操作（本地）

|尝试的更改|影响的操作|严重性|恢复方法|
|:------------- |:------------- |:--------------|:--------------|
|禁用对 vCenter Server 或 PSC 的 SSH 或 shell 访问。|对主实例和辅助实例进行配对可能会失败。|重要|不适用|
|禁用对 ESXi 的 SSH 或 shell 访问。|在实例中添加和除去主机、服务和网络存储器可能会失败。|重要|不适用|

如果选择禁用 SSH 或 shell 访问，那么应该在执行指示的操作之前，临时重新启用 SSH 或 shell 访问。

## vCenter Server 实例的管理子网

以下信息讨论了 {{site.data.keyword.vmwaresolutions_short}} 订购的子网，并提供了一些选项，供您订购额外子网以供自己使用。

**注意**：不要将这些组件用于其他用途，否则环境的稳定性将受到严重影响。

每次订购 {{site.data.keyword.cloud_notm}} 裸机服务器时，缺省情况下都会订购以下 IP 地址范围：
*  32 个 IP 地址的主公共范围
*  64 个 IP 地址的主专用范围

此外，还会为 {{site.data.keyword.vmwaresolutions_short}} 保留以下管理子网：
*  第一个 VLAN 上包含 64 个 IP 地址的两个可移植专用子网：一个用于管理，另一个用于 VTEPS
*  第二个 VLAN 上包含 64 个 IP 地址的两个可移植专用子网：一个用于 VMotion，另一个用于 vSAN
*  公用 VLAN 上包含 16 个 IP 地址的公用可移植子网

如果需要使用更多子网，可以通过下列其中一种方式来获取要使用的 IP 地址：
*  **选项 1（建议）**：使用 VMware NSX 虚拟网络覆盖。订购时提供了样本 VXLAN 模板。此 VXLAN 可用作构建软件定义的联网 (SDN) 的起点。有关更多信息，请参阅[配置网络以使用客户管理的 NSX Edge](vc_esg_config.html)。
*  **选项 2**：订购您自己的可移植公用子网或专用子网以获取 IP 地址。要使订购的子网区别于管理子网，可以向订购的所有子网添加注释。
