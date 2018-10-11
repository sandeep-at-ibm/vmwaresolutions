---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# V2.6 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Spectre 和 Meltdown 修复

{{site.data.keyword.vmwaresolutions_short}} 发布了来自 VMware 的补丁，以响应与 Spectre 和 Meltdown 相关的漏洞（CVE-2017-5753、CVE-2017-5715 和 CVE-2017-5754）。

* CVEID：[CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID：[CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID：[CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

有关更多信息，请参阅[解决 Spectre 和 Meltdown 漏洞](../vmonic/trbl_fix_spectre.html)。

## 高性能 Intel Optane 选项

此发行版提供了用于在订购新实例或在初始部署后添加新的 vSAN 集群时，为 vSAN 存储器添加高性能高速缓存的选项。

此选项支持将存储容量磁盘的数量从 8 个增加到最多 10 个。

“高性能 Intel Optane”选项仅可用于使用双 Intel Xeon Gold 5120 和双 Intel Xeon Gold 6140 处理器的定制配置。

有关更多信息，请参阅实例或集群类型的相应订购主题。

## 启用公用或专用网络

现在，您可以部署 vCenter Server 和 vCenter Server with Hybridity Bundle 实例以及 VMware vSphere 集群，并启用公用和专用网络接口卡 (NIC)，或者启用仅专用 NIC。此外，在向 vCenter Server 和 vCenter Server with Hybridity Bundle 实例添加新集群时，此选项也可用。

某些附加组件服务需要公共 NIC，但这些服务在您选择启用仅专用网络时不可用。

有关更多信息，请参阅以下主题中的_网络接口设置_部分：

* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html#network-interface-settings)
* [订购 vCenter Server with Hybridity Bundle 实例](../vcenter/vc_hybrid_orderinginstance.html#network-interface-settings)
* [订购新的 vSphere 集群](../vsphere/vs_orderinginstances.html#network-interface-settings)

## 删除 ESXi 服务器

如果您满足实例的最低需求，那么现在可以从 vCenter Server、vCenter Server with Hybridity Bundle 或 Cloud Foundation 实例中删除任何 ESXi 服务器。

有关 ESXi 服务器需求的更多信息，请参阅以下主题：

* [扩展和收缩 vCenter Server 实例的容量](../vcenter/vc_addingremovingservers.html)
* [扩展和收缩 vCenter Server with Hybridity Bundle 实例的容量](../vcenter/vc_hybrid_addingremovingservers.html)
* [扩展和收缩 Cloud Foundation 实例的容量](../sddc/sd_addingremovingservers.html)

## 对 VMware vCenter Server 实例的更新

本发行版应用了以下升级和改进：

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## 对 VMware vCenter Server with Hybridity Bundle 的更新

### 从 vCenter Server 实例中除去 Hybridity Bundle

现在，您可以从 vCenter Server 实例中除去 Hybridity Bundle 许可证。为此，您需要将 VMware NSX 和 VMware vSAN 租赁许可证密钥替换为自带许可证 (BYOL) 密钥，并开具支持凭单以取消租用许可证的费用。

有关更多信息，请参阅[从 vCenter Server 实例中除去 Hybridity Bundle](../vcenter/vc_hybrid_deletingbundle.html)。

### vCenter Server with Hybridity Bundle 可用性

现在，业务合作伙伴可以订购 vCenter Server with Hybridity Bundle 实例。业务合作伙伴无法将现有 vCenter Server 实例升级到 vCenter Server with Hybridity Bundle，也无法从 vCenter Server with Hybridity Bundle 实例中除去 Hybridity Bundle。

有关更多信息，请参阅以下主题：

* [vCenter Server with Hybridity Bundle 概述](../vcenter/vc_hybrid_overview.html)
* [订购 vCenter Server with Hybridity Bundle 实例](../vcenter/vc_hybrid_orderinginstance.html)

## 对 VMware Cloud Foundation 实例的更新

本发行版应用了以下升级和改进：

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## 对附加组件服务的更新

### HyTrust KeyControl on IBM Cloud

现在，HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服务可用于运行 vSphere 6.5 以及部署在或已升级到 V2.5 和更高发行版中的 VMware Cloud Foundation 实例和 VMware vCenter Server 实例。此服务通过自动化和简化加密密钥的生命周期来简化已加密工作负载的管理工作。该服务可以使用符合 FIPS 140-2 的加密来轻松管理大批加密密钥。通过使用此服务，可以管理所有虚拟机和已加密数据存储的加密密钥，并可对其进行扩展，以支持大型部署中的数千个已加密工作负载。

您可以在订购实例时订购包含此服务的实例，也可以日后向现有实例添加此服务。

有关更多信息，请参阅以下主题：
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 的组件和注意事项](../services/htkc_considerations.html)
* [管理 HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/managinghtkc.html)

### HyTrust CloudControl on IBM Cloud

当前发行版在所有新部署的实例上安装 HyTrust CloudControl 5.4。有关 HyTrust CloudControl 5.4 中新增功能的更多信息，请参阅 [HyTrust CloudControl V5.4 联机文档集](https://docs.hytrust.com/CloudControl/5.4.0/Online/index.html)。

### HyTrust DataControl on IBM Cloud

当前发行版在所有新部署的实例上安装 HyTrust DataControl 4.2。有关 HyTrust DataControl 4.2 中新增功能的更多信息，请参阅 [HyTrust DataControl 4.x 中的新增内容](https://docs.hytrust.com/DataControl/4.2/Admin_Guide-4.2/Content/Books/aaCommon/New-Changed-4x.htm)。

### vSphere ESXi V6.5 update 2c 的 Veeam on IBM Cloud 支持

从 V2.6 开始，将使用 vSphere ESXi V6.5 Update 2c 供应新实例和新主机。如果在使用 Veeam Backup and Replication，那么 Veeam 建议您将 Veeam on {{site.data.keyword.cloud_notm}} 实例更新到 V9.5u3a 或更高版本，以确保与 vSphere ESXi 6.5 Update 2c 的最佳兼容性。

建议安装了 Veeam on {{site.data.keyword.cloud_notm}} 的现有 Cloud Foundation 实例也更新为 V9.5u3a 或更高版本。

有关 Veeam on {{site.data.keyword.cloud_notm}} 的更多信息，请参阅 [Veeam on {{site.data.keyword.cloud_notm}} 概述](../services/veeam_considerations.html)。

### VMware HCX on IBM Cloud

当前发行版在所有新部署的实例上安装 VMware HCX 3.5.1 R106。有关 HCX 3.5.1 R106 中新增功能的更多信息，请参阅 [VMware NSX Hybrid Connect 文档](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/index.html)。

## 新增和更新的文档

### 参考体系结构文档
{{site.data.keyword.vmwaresolutions_short}} 体系结构文档已更新，包含了解管理和运行 VMware 实例的责任的重要注意事项。

有关更多信息，请参阅 [VMware 实例的部署后注意事项](../archiref/solution/solution_considerations.md)。

## 用户界面更新和增强功能

用户界面已更新，并提供了以下增强功能：

* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
