---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-30"

---

# V2.5 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的更多提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 和 Meltdown 修复

{{site.data.keyword.vmwaresolutions_short}} 发布了来自 VMware 的补丁，以响应称为 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 和 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

有关更多信息，请参阅[解决 Spectre 和 Meltdown 漏洞](../vmonic/trbl_fix_spectre.html)。

## NSX 组件更新

此发行版安装了 VMware NSX for vSphere 6.4.1，以用于 VMware vCenter Server on {{site.data.keyword.cloud_notm}}、VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle、NetApp ONTAP Select 和 VMware Federal on {{site.data.keyword.cloud_notm}} 的新部署。

## 除去了缺省备份配置

{{site.data.keyword.vmwaresolutions_short}} 为备份提供了两个集成的附加组件服务：IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 和 Veeam on {{site.data.keyword.cloud_notm}}。通过这些服务，您可以计划并提供对管理基础架构和工作负载的恢复。此外，IBM Resiliency Services 还提供了用于 Veeam 备份的受管服务。

从 V2.5 发行版开始，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 和 Veeam on {{site.data.keyword.cloud_notm}} 服务在部署时，不再预先配置任何 VM 的备份。此更改可确保您能够正确配置备份作业的所有方面，包括安排计划、设置保留期、使用去重功能、监视和警报以及管理加密密钥。此外，IBM CloudDriver VM 不再配置为 NSX 备份的持久文件服务器。

您负责所有软件组件的配置、管理和监视，包括管理基础架构和工作负载的备份和可用性。有关更多信息，请参阅[备份组件](../archiref/solution/solution_backingup.html#backing-up-components)。

**注：**此更改不会影响已安装 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}} 服务且在 V2.5 之前部署的实例。

## IBM CloudDriver 弹性

对于已部署到或升级到 V2.5 或更高发行版的实例，不再将 IBM CloudDriver 组件配置为 vSphere 集群中的虚拟机 (VM)，而是根据需要使用最新的 {{site.data.keyword.cloud_notm}} for VMware 代码将其部署为 {{site.data.keyword.cloud_notm}} 基础架构虚拟服务器实例 (VSI)，以用于诸如部署更多节点、集群或服务之类的操作。此外，还将 IBM CloudDriver 更改为使用 {{site.data.keyword.cloud_notm}} 专用网络与 {{site.data.keyword.cloud_notm}} 管理平面进行通信。此更改除去了允许 IBM CloudDriver 与公用网络进行出站通信的管理 NSX Edge 服务网关 (ESG) 防火墙和网络地址转换 (NAT) 规则。

某些附加组件服务（例如，F5 on {{site.data.keyword.cloud_notm}}、FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 和 Zerto on {{site.data.keyword.cloud_notm}}）仍需要公用网络访问，因此管理 NSX ESG 仍保持部署在所有实例中。

## 支持 IAM 的用户和访问权管理

从 V2.5 发行版开始，{{site.data.keyword.vmwaresolutions_short}} 与 IBM Identity and Access Management (IAM) 集成，以提供统一的方法来管理 {{site.data.keyword.cloud_notm}} 帐户中的用户帐户和用户访问权。因此，可以实现以下操作：
* 现在，您可以向 {{site.data.keyword.cloud_notm}} 帐户添加多个用户来进行协作，还可以通过为用户分配不同的平台访问角色，来管理用户对帐户中所供应服务和资源的访问权。  
* 部署在 V2.5 和更高发行版中的实例会自动链接到订购实例时使用的用户帐户。
* 对于部署在 V2.4 和前发行版中的实例，可以将其迁移到指定的 {{site.data.keyword.cloud_notm}} 帐户，然后同样使用 IAM 来管理这些实例。

有关更多信息，请参阅以下主题：
* [邀请用户访问服务和资源](../vmonic/iamuserinvite.html)
* [使用 IAM 管理用户访问权](../vmonic/iam.html)

## 更改了 VMware vCenter Server 和 VMware Cloud Foundation 实例的用户帐户和组

**ic4v-vCenter** 用户组已在 Microsoft Active Directory 服务器上创建，并添加到 vCenter Server 上的全局许可权以及 NSX Manager 的用户组。该组包含用于 vCenter Server 实例的 **automation** 用户帐户，以及用于 vCenter Server 和 Cloud Foundation 实例的特定于服务的用户帐户。

不要在 VMware vSphere Web Client 上的**用户和组**页面中编辑 **ic4v-vCenter** 组的全局许可权。这样做可能会影响管理操作。

对于 Cloud Foundation 实例，请使用 **customerroot** 主机用户标识来代替 **root** 主机用户标识。对于 vCenter Server 实例，请继续使用 **root** 主机用户标识。

有关用户帐户的更多信息，请参阅以下主题：

* [关于更改 vCenter Server 工件的注意事项](../vcenter/vcenter_chg_impact.html)
* [关于更改 Cloud Foundation 工件的注意事项](../sddc/cf_chg_impact.html)

## 对附加组件服务的更新

### IBM Cloud Private Hosted（于 2018 年 8 月 30 日更新）

{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} 服务现在可用于在 V2.5 或更高发行版中部署或升级到这些版本的 vCenter Server 实例。

{{site.data.keyword.cloud_notm}} Private Hosted 会将微服务和容器的强大功能引入到 {{site.data.keyword.cloud_notm}} 上的 VMware 环境中。使用此服务，可以将内部部署中您所熟悉的相同 VMware 和 {{site.data.keyword.cloud_notm}} Private 操作模型和工具扩展到 {{site.data.keyword.cloud_notm}} 中。

在订购 vCenter Server 实例后，您可以请求此服务。有关更多信息，请参阅[请求 {{site.data.keyword.cloud_notm}} Private Hosted](../services/managing_icp.html)。

### IBM Spectrum Protect Plus on IBM Cloud

从 V2.5 发行版开始，会基于最佳实践将 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务部署为两个单独的 VM：一个 VM 运行 IBM Spectrum Protect Plus 服务器；另一个 VM 运行 vSnap 服务器和 VADP 代理。

现在，您最多可订购 10 个备份数据存储，且可使用的最大备份存储器大小为 120 TB。vSnap 和 VADP VM 的大小取决于所选的备份存储器大小，并根据 [IBM Spectrum Protect Plus 蓝图](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)中的信息进行调整。

### KMIP for VMware on IBM Cloud

现在，德国有可用于 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的新端点。

有关更多信息，请参阅 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务配置](../services/kmip_ordering.html#kmip-for-vmware-on-ibm-cloud-service-configuration)。

## 新增和更新的文档

### 连接的存储器文档

现在，用户文档的*参考*部分中提供了“vCenter Server on IBM Cloud 的连接存储器”技术文档。此参考体系结构文档仅提供英语版本。有关更多信息，请参阅 [vCenter Server on IBM Cloud 的连接存储器](../archiref/attached-storage/storage-benefits.html)。

### 技术规范

现在，用户文档中提供了所有实例类型和服务类型的技术规范，这些规范还可通过用户界面中的链接获取。有关更多信息，请参阅实例和服务的相应概述主题。

### 服务文档

改进了服务信息，以便根据在其中提供服务支持的发行版号轻松识别服务支持。

有关更多信息，请参阅以下主题：

* [可用于 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html#available-services-for-vcenter-server-instances)
* [vCenter Server with Hybridity Bundle 实例的可用服务](../vcenter/vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances)
* [可用于 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html#available-services-for-cloud-foundation-instances)

## 用户界面更新和增强功能

用户界面已更新，并提供了以下增强功能：

* 如果您有链接到 {{site.data.keyword.cloud_notm}} 帐户的 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) 帐户，那么现在可以单击**设置**页面上新添加的**检索**按钮，以自动获取 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) 帐户的用户名和 API 密钥。
* 在实例详细信息页面的左侧导航窗格中添加了新的**部署历史记录**选项卡，供您检查实例的部署历史记录。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择适当的设置。
