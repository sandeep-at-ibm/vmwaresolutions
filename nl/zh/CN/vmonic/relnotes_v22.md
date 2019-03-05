---

copyright:

  years:  2016, 2019

lastupdated: "2018-10-19"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.2 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 和 Meltdown 修复

{{site.data.keyword.vmwaresolutions_short}} 发布了来自 VMware 的补丁，以响应称为 Spectre 和 Meltdown 的漏洞（CVE-2017-5753、CVE-2017-5715 和 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

有关更多信息，请参阅[解决 Spectre 和 Meltdown 漏洞](/docs/services/vmwaresolutions/vmonic/trbl_fix_spectre.html)。

## IBM CloudDriver 虚拟机升级

在 V2.2 升级过程中，会通过 CentOS Linux R7.4.1708 重新部署 IBM CloudDriver 虚拟机。此外，所有新供应的实例在 IBM CloudDriver 上都会包含 CentOS Linux R7.4.1708。

**重要信息：**

* 如果使用的是引用 IBM CloudDriver 虚拟机的备份解决方案，那么在升级到 V2.2 后，请确保备份解决方案引用的是新 IBM CloudDriver 虚拟机。
* 升级到 V2.2 之前，请确保将旧 Veeam VSI 替换为 Veeam on {{site.data.keyword.cloud_notm}} 服务。在 V2.2 和未来发行版中不再支持旧 Veeam，因此与旧 Veeam 关联的管理组件备份不可用于复原。

有关使用 Veeam on {{site.data.keyword.cloud_notm}} 服务的更多信息，请参阅以下主题：
* [Veeam on {{site.data.keyword.cloud_notm}} 的组件和注意事项](/docs/services/vmwaresolutions/services/veeam_considerations.html)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managingveeam.html)

## 对 VMware Federal on IBM Cloud 的支持

VMware Federal on {{site.data.keyword.cloud_notm}} 提供了在 {{site.data.keyword.CloudDataCent_notm}} 上的 WDC03 Federal 中订购基本 vCenter Server 实例的选项。除了支持一部分 vCenter Server 实例产品之外，VMware Federal on {{site.data.keyword.cloud_notm}} 还为美国联邦政府机构提供了用于确保已部署 VMware vCenter Server 实例安全的选项。选择用于确保已部署实例安全的选项会除去存储的有关实例的敏感信息，并除去用于持续访问实例以实现管理功能（例如，添加和除去主机与集群）的开放式管理连接。选择安全选项后，所有管理功能均不可用，但完全实例删除操作除外。

有关确保 VMware Federal 实例安全之前的重要注意事项，请参阅[确保 VMware Federal 实例安全](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html)。

（更新日期：2018 年 4 月 2 日）现在，可以通过添加或除去 ESXi 服务器，扩展或收缩 VMware Federal 实例的容量。此选项仅可用于尚未受到保护的 VMware Federal 实例。

有关更多信息，请参阅以下主题：

* [VMware Federal on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/vcenter/vc_fed_overview.html)
* [添加、查看和删除 VMware Federal 实例的集群](/docs/services/vmwaresolutions/vcenter/fed_addviewdeleteclusters.html)
* [扩展和收缩 VMware Federal 实例的容量](/docs/services/vmwaresolutions/vcenter/vc_fed_addingremovingservers.html)

## ESXi 服务器上的高级配置设置

对于 V2.2 或更高发行版，订购的新实例有一组新的高级配置设置用于 ESXi 服务器。
对于从前发行版升级到 V2.2 或更高发行版的实例，某些设置需要重新引导 ESXi 服务器。因此仅会自动应用一部分配置设置。

建议将其余配置设置更改为新值，以实现在所有实例上的一致性，并为存储扩展提供充分支持。对于所有 {{site.data.keyword.cloud_notm}} for VMware Solutions 未来发行版，IBM 计划仅测试这些新设置。

有关更多信息，请参阅以下主题中的 _ESXi 服务器的高级配置设置_：
* [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter/vc_bom.html#advanced-configuration-settings-for-esxi-servers)
* [Cloud Foundation 材料清单](/docs/services/vmwaresolutions/sddc/sd_bom.html#advanced-configuration-settings-for-esxi-servers)

## 针对初始集群最多支持 51 个 ESXi 服务器，针对其他集群最多支持 59 个 ESXi 服务器

对于 V2.2 和更高发行版，现在可以将 ESXi 服务器数增加到最大 51 个（对于初始集群）和最大 59 个（对于其他集群）。

对于 V2.1 或更低发行版中部署的实例，必须启用必要的 vSAN 支持才能将集群大小增加到 32 以上。有关增加 ESXi 服务器数的步骤的更多信息，请参阅[关于 ESXi 服务器的常见问题](/docs/services/vmwaresolutions/vmonic/faq_esxi.html#how-many-esxi-servers-can-i-add-to-a-cluster-)中的_可以向集群添加多少个 ESXi 服务器？_。
{:important}

## vCenter Server 和 Cloud Foundation 实例的更多网络配置选项

对于 vCenter Server 和 Cloud Foundation 实例订单，现在可以将现有公用和专用 VLAN 复用于网络配置。现有 VLAN 不可用时，您可以订购一个新的公用 VLAN 和两个新的专用 VLAN。

有关选择现有 VLAN 之前的重要注意事项，请参阅以下内容中的*网络接口设置*部分：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [订购 Cloud Foundation 实例](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)

## 对 VMware vCenter Server 实例的更新

### NSX 组件和端口组配置设置更新

当前发行版会应用 VMware NSX for vSphere 6.3.5 组件更新。有关组件的更多信息，请参阅 [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter/vc_bom.html)。

对于 V2.2 或更高发行版中部署的 VMware vCenter Server 实例，NSX 和端口组配置设置已更改。有关更多信息，请参阅 [vCenter Server 软件材料清单](/docs/services/vmwaresolutions/vcenter/vc_bom.html#nsx-and-port-group-configuration-settings)中的 *NSX 和端口组配置设置*部分。

### DNS 配置的新选项

现在，可以选择在管理集群中部署一个用于 Microsoft Active Directory (AD) 的 Microsoft Windows Server 虚拟服务器实例 (VSI) 或两个高可用性 Microsoft Windows 虚拟机。对于 V2.2 之前的发行版，缺省情况下会自动部署一个用于 Microsoft AD 的 Microsoft Windows VSI。用于选择两个 Microsoft Windows 虚拟机的新选项提供了更多隐私性，并提供了使用 Veeam 服务来备份和复原虚拟机的选项。

如果将实例配置为使用 2 个 Microsoft Windows 虚拟机，那么必须提供 2 个 Microsoft Windows Server 2012 R2 许可证。使用 Microsoft Windows Server 2012 R2 Standard Edition 许可证和/或 Microsoft Windows Server 2012 R2 Datacenter Edition 许可证。您有 30 天的时间来激活虚拟机。
{:note}

有关更多信息，请参阅[订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html#system-settings)中的*系统设置*部分。

### 增加每个实例的集群数

现在，对于部署在或已升级到 V2.2 和更高发行版中的 VMware vCenter Server 实例，最多可以添加 10 个集群。有关更多信息，请参阅[添加和查看 vCenter Server 实例的集群](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)。

## 对 VMware vSphere 集群的更新

### 可用于业务合作伙伴客户的组件许可捆绑软件

现在，业务合作伙伴用户在订购新的 vSphere 集群时，可以从四个组件许可捆绑软件中进行选择。这四个选项为：“管理”、“高级”、“高级（带联网）”或“高级（带联网和管理）”。您还可以在订单中包含其他 VMware 组件。但是，自带许可证选项不可用。

有关更多信息，请参阅[订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)中的*许可设置*部分。

## 对 NetApp ONTAP Select 实例的更新

当前发行版会应用 NetApp ONTAP Select 9.3 的更新。

### 增加了用于高容量 IBM Cloud 裸机服务器的 SATA 驱动器数

现在，有 34 个 SATA 驱动器可用于 NetApp ONTAP Select 高容量 {{site.data.keyword.baremetal_short}}。有关更多信息，请参阅 [NetApp ONTAP Select 实例的技术规范](/docs/services/vmwaresolutions/netapp/np_netappoverview.html#technical-specifications-for-netapp-ontap-select-instances)。

## 对附加组件服务的更新

### 增大了 F5 on IBM Cloud 的带宽选项

现在，为 Cloud Foundation 和 vCenter Server 实例安装 F5 on {{site.data.keyword.cloud_notm}} 服务时，可以选择的最大带宽为 10 Gbps。有关更多信息，请参阅 [F5 on {{site.data.keyword.cloud_notm}} 的注意事项](/docs/services/vmwaresolutions/services/f5_considerations.html)。

### KMIP for VMware on IBM Cloud

现在，可以订购包含 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的 Cloud Foundation 或 vCenter Server 实例，也可以在初始部署后向现有 Cloud Foundation 或 vCenter Server 实例添加此服务。

此服务用于提供全天候高可用性服务，以管理 {{site.data.keyword.cloud_notm}} 中 VMware 使用的加密密钥。此服务提供了运行时功能，以支持客户创建、检索、激活、撤销和删除加密密钥。此外，此服务还提供了管理功能，以维护客户机凭证与这些加密密钥之间的关联。

有关更多信息，请参阅 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 的注意事项](/docs/services/vmwaresolutions/services/kmip_considerations.html)。

### IBM Spectrum Protect Plus on IBM Cloud

IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服务现在可用于部署在（或已升级到）V2.2 或更高发行版中的实例。

此服务用于在虚拟环境下为数据保护、数据复用和数据恢复提供高效的可扩展解决方案。可以将此服务作为独立解决方案实施，也可以与 IBM Spectrum Protect&trade; Plus 环境集成，以便卸载用于长期存储和数据监管的副本。

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务仅为工作负载 VM 提供数据保护。

有关更多信息，请参阅[管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managingspp.html)。

### 受管服务

Veeam on {{site.data.keyword.cloud_notm}} 和 Zerto on {{site.data.keyword.cloud_notm}} 的受管服务现在可用于 VMware vCenter Server 和 VMware Cloud Foundation 实例。如果您不想管理自己解决方案和环境的复杂性，那么请求这些受管服务。

Veeam on {{site.data.keyword.cloud_notm}} 服务可与 VMware 系统管理程序无缝集成，以帮助企业实现高可用性 (HA)。可以使用 Veeam 备份软件和 IBM Resiliency Backup as a Service 来部署完全受管的备份环境。

Zerto on {{site.data.keyword.cloud_notm}} 服务用于提供复制和灾难恢复功能，这些功能可以集成到部署产品中，以保护和恢复 {{site.data.keyword.cloud_notm}} 上 VMware 虚拟环境中的数据。可以使用 Zerto 灾难恢复 (DR) 软件和 IBM Resiliency Services 来部署完全受管的 DR 环境。

可以在**开始**页面中，通过订购新实例或向现有实例添加服务，为实例请求受管服务。

有关更多信息，请参阅以下主题：
* [请求 Veeam on {{site.data.keyword.cloud_notm}} 的服务](/docs/services/vmwaresolutions/services/managing_veeam_services.html)
* [请求 Zerto on {{site.data.keyword.cloud_notm}} 的服务](/docs/services/vmwaresolutions/services/managing_zerto_services.html)

## 新增和更新的文档

* 现在，文档中提供了 Cloud Foundation 和 vCenter Server 实例受支持功能的比较表以及 VMware vSphere 集群的信息。您可以快速查看每种实例类型提供的功能之间的差异。有关更多信息，请参阅[产品比较图表](/docs/services/vmwaresolutions/vmonic/inst_comp_chart.html)。

* 现在，Cloud Foundation、vCenter Server 和 VMware vSphere 集群的文档中提供了 VLAN 和软件材料清单 (BOM)。

  有关更多信息，请参阅以下主题：

  * [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter/vc_bom.html)
  * [Cloud Foundation 材料清单](/docs/services/vmwaresolutions/sddc/sd_bom.html)
  * [VMware vSphere 材料清单](/docs/services/vmwaresolutions/vsphere/vs_bom.html)

## 用户界面更新和增强功能

对整个用户界面进行了改进：

* 现在，订购实例时，所有硬件选项按位置进行过滤，不可用选项会显示为“已禁用”状态。
* 现在，根据现有配置订购 vSphere 集群时，会自动填充 **{{site.data.keyword.baremetal_short}}** 配置。您可以根据需求更新该配置。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
