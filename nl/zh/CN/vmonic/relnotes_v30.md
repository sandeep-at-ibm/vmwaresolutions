---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.0 发行说明
{: #relnotes_v30}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## 对 VMware Cloud Foundation on IBM Cloud 的支持结束 
{: #relnotes_v30-vcf-eos}

为了整合我们的产品以获得更好的客户体验，从 2019 年 5 月 13 日起，{{site.data.keyword.vmwaresolutions_short}} 平台将不再提供 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}。

此后，所有客户将定向到 VMware vCenter Server on {{site.data.keyword.cloud_notm}}，这是 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 上我们的旗舰 VMware 软件定义的数据中心解决方案。


在 2019 年 5 月 13 日结束支持之前，使用 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的现有客户将在支持人员的协助下转换到 VMware vCenter Server on {{site.data.keyword.cloud_notm}}。

在 5 月 13 日之后，{{site.data.keyword.vmwaresolutions_short}} 控制台中将冻结 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的管理功能，直至将其转换到 VMware vCenter Server on {{site.data.keyword.cloud_notm}}。对于选择不将 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 实例迁移或转换到 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的客户，可以在 {{site.data.keyword.cloud_notm}} 基础架构控制台中访问自己的实例。

## 除去了对 Broadwell 2-CPU 服务器的支持
{: #relnotes_v30-broadwell}

从 V3.0 发行版开始，Broadwell 2-CPU 服务器不再可用于部署新的 vCenter Server、vCenter Server with Hybridity Bundle、vCenter Server with NSX-T 和 vSphere on {{site.data.keyword.cloud_notm}} 实例和集群。您仍可以向现有集群添加服务器。

## 网络文件系统操作增强功能
{: #relnotes_v30-nfs}

从 V3.0 发行版开始，您可以在多个处于**可供使用**状态的集群中同时添加或除去 NFS 存储器和 ESXi 服务器。例如，可以在一个集群中添加或除去 ESXi 服务器，在另一个集群中添加或除去 NFS 存储器。这适用于所有 vCenter Server 和 vCenter Server with NSX-T 实例。

## 对 VMware vCenter Server 实例的更新
{: #relnotes_v30-vcs}

本发行版应用了以下升级和改进：

* vSphere ESXi 6.7 Update 1（构建 6.7.0-13004448）
* vSphere ESXi 6.5 Update 2（构建 6.5.0-13004031）
* vCenter Server Appliance 6.7 Update 1b（构建 6.7.0-11727113）
* Platform Services Controller 6.7 Update 1b（构建 6.7.0-11727113）

有关更多信息，请参阅 [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

为 Microsoft Active Directory (AD) 和 DNS（域名系统）服务订购的 Windows 软件会升级到 Windows Server 2016，以支持以下两个配置选项：VSI（虚拟服务器实例）和两个高可用性 Windows VM。有关选择 VMware 组件的更多信息，请参阅 [vCenter Server 实例的软件 BOM](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software)。

### vSAN 存储器增强功能
{: #relnotes_v30-vcs-vsan}

* 现在，使用 vSAN 存储器时，订购的裸机服务器数可以大于四个。这适用于所有 vCenter Server、vCenter Server with Hybridity 和 vCenter Server with NSX-T 实例。
* 从 V3.0 发行版开始，订购 vSAN 存储器实例时会随附订购 M.2 固态驱动器。如果选择**高性能（使用 Intel Optane）**选项，那么可以最多订购 10 个容量磁盘或总共 12 个容量磁盘。

有关更多信息，请参阅以下内容中的*存储设置*部分：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [订购 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [订购 vCenter Server with NSX-T 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## 对附加组件服务的更新
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

在当前发行版中，HyTrust CloudControl 5.5 安装在所有新部署的实例上。有关 HyTrust CloudControl 5.5 中新增功能的更多信息，请参阅 [What's New in CloudControl, Version 5.5](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}。

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

当前发行版在所有新部署的实例上安装 HyTrust DataControl 4.3。有关 HyTrust DataControl 4.3 中新增功能的更多信息，请参阅 [What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}。

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

当前发行版在所有新部署的实例上安装 HyTrust KeyControl 4.3。有关 HyTrust KeyControl 4.3 中新增功能的更多信息，请参阅 [What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}。

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

当前发行版在所有新部署的实例上安装 {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 以及 {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2。

有关 {{site.data.keyword.cloud_notm}} Private V3.1.2 中新增功能的更多信息，请参阅 [ {{site.data.keyword.cloud_notm}} Private V3.1.2 中的新增内容](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}。有关 {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 中新增功能的更多信息，请参阅 [{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 中的新增内容](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}。

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

现在，在伦敦和美国东部有可用于 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的两个新端点。有关更多信息，请参阅 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务配置](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config)。

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

当前发行版在所有新部署的实例上安装 IBM Spectrum Protect™ Plus V10.1.3。有关 IBM Spectrum Protect Plus V10.1.3 中新增功能的更多信息，请参阅 [IBM Spectrum Protect Plus 更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}。

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

现在，您可以在仅专用实例上添加 Zerto on {{site.data.keyword.cloud_notm}}。如果选择在仅专用实例上安装 Zerto，那么必须设置您自己的代理服务器，此外还必须配置 Zerto 的“回拨”功能。有关更多信息，请参阅[为仅适用于专用网络的实例订购 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only)。

## 新增和更新的文档

* 现在，有文档可用于帮助您将 {{site.data.keyword.vmwaresolutions_short}} 组件升级到 VMware vSphere 6.7。如果要继续受益于 {{site.data.keyword.vmwaresolutions_short}} 自动化，此升级是必需的。有关更多信息，请参阅[将 vCenter Server vSphere 软件从 VMware vSphere 6.5 升级到 6.7](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade)。
* 现在，有参考文档可用于为您提供 {{site.data.keyword.vmwaresolutions_short}} 维护供 {{site.data.keyword.cloud_notm}} 自动化使用的用户标识。此外，在实例历史记录日志中显示的可能消息也可供您查看。有关更多信息，请参阅 [IBM 用户标识](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids)和[实例历史记录消息](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages)。
* **重新引导/控制**许可权已添加到描述 IBM Cloud 基础架构帐户所需许可权的表中。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 基础架构帐户许可权](/docs/services/vmwaresolutions/services?topic=vmware-solutions-slaccountrequirement#slaccountrequirement-permissions)。
* 新的参考文档可用于以下 API。有关更多信息，请参阅 [API 参考](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}。
  * 列出指定 VMware vCenter Server 实例的所有历史记录消息
  * 向指定集群添加共享存储器
  * 从指定集群中删除 NFS 存储器

## 用户界面更新和增强功能
{: #relnotes_v30-ui}

用户界面已更新，并提供了以下增强功能：

* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
