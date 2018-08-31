---

copyright:

  years:  2016, 2018

lastupdated: "2017-11-20"

---

# V2.0 发行说明

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的更多提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## FortiGate Virtual Appliance on IBM Cloud

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务现在可用于 V2.0 和更高版本 VMware Cloud Foundation 实例和 VMware vCenter Server 实例。此服务用于将 FortiGate Virtual Appliance 的高可用性 (HA) 对部署到环境中，这可帮助通过在虚拟基础架构中实施关键安全控制来降低风险。

您可以在订购实例时订购包含 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务的实例，也可以日后在实例详细信息页面上的**服务**选项卡中向现有实例添加此服务。根据您的需求，可为此服务选择三种部署大小和许可选项中的一个选项。成功安装此服务后，可以在 FortiGate 控制台中管理和配置 FortiGate Virtual Appliance 的防火墙规则。

有关更多信息，请参阅以下主题：
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的组件和注意事项](../services/fortinetvm_considerations.html)
* [管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html)

## F5 on IBM Cloud 和 FortiGate Virtual Appliance on IBM Cloud 的多服务安装

现在，可以为 Cloud Foundation 实例或 vCenter Server 实例安装 F5 on {{site.data.keyword.cloud_notm}} 服务和 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务的多个实例。订购实例期间选择 F5 服务或 FortiGate 服务时，必须指定服务实例的名称，使其区别于日后可能安装的其他服务实例。

完成实例部署后，可以通过在实例详细信息页面的**添加服务**选项卡上安装 F5 或 FortiGate 服务，以添加该服务的更多实例。一次只能添加一个服务实例，并且必须对要为服务添加的所有实例重复此过程。

有关更多信息，请参阅以下主题：
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)

## 对 FortiGate Security Appliance on IBM Cloud 的更新

在此发行版中，Fortinet on {{site.data.keyword.cloud_notm}} 服务已重命名为 FortiGate Security Appliance {{site.data.keyword.cloud_notm}}，并且此服务的 FortiGate Security Appliance (FSA) 对在部署到实例时，缺省情况下已配置为安全：
* 如果将 FSA 对作为新 Cloud Foundation 实例或 vCenter Server 实例的一部分进行部署，那么这对 FSA 会配置为仅允许从实例到公用网络的必需出站通信，而拒绝其他所有通信。
* 如果将 FSA 对作为现有 Cloud Foundation 实例或 vCenter Server 实例的一部分进行部署，那么这对 FSA 会配置为使用显式规则以允许从实例到公用网络的所有必需出站管理通信，此外这对 FSA 还会配置为使用其他规则以允许其他所有通信，从而确保现有应用程序流量不会中断。

在所有情况下，您都必须谨慎管理 FSA 配置，以仅允许必要的通信，而拒绝其他所有通信。

## 标准域名格式一致性

现在，对于所有实例，标准域名 (FQDN) 都以一致的方式表示。下订单时，可以输入您自己的子域前缀和主机名前缀。这将确保遵循 FQDN 格式的业界约定，例如：`host-name-prefix<n>.subdomain-prefix.domain-name`。

有关更多信息，请参阅以下主题：
* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)
* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)
* [订购新的 vSphere 集群](../vsphere/vs_orderinginstances.html)

## 订购实例期间估算工作负载和存储量

* 在订购 VMware vSphere on {{site.data.keyword.cloud_notm}} 期间，会向您提供可在订购的实例上运行的虚拟机估算数量。
* 在订购 Cloud Foundation 和 vCenter Server 期间，会向您提供所订购实例的可用存储容量估算值。

有关更多信息，请参阅以下主题：
* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)
* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)
* [订购新的 vSphere 集群](../vsphere/vs_orderinginstances.html)

## 对 VMware Cloud Foundation 实例的更新

当前发行版会对新部署应用以下组件更新和改进：

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware SDDC Manager 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5，补丁发行版 ESXi650-201710401-BG：更新 esx-base、esx-tboot、vsan 和 vsanhealth VIB (2151061)。有关补丁的详细信息，请参阅 [VMware vCenter Server Appliance Photon OS 安全补丁](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}。

**注**：现有实例（源自 V1.9 和更低发行版）无法升级到此列表中的组件版本。

有关组件的更多信息，请参阅 [Cloud Foundation 概述](../sddc/sd_cloudfoundationoverview.html)。

### Cloud Foundation 实例的集群支持

现在，可以使用集群来管理在 V2.0 和更高发行版中部署的 Cloud Foundation 实例中的 ESXi 服务器，以更好地管理资源，并实现高可用性。缺省情况下，订购实例时配置的 ESXi 服务器会分组为 **SDDC-Cluster**。

可以在实例详细信息页面的**基础架构**选项卡上，查看集群详细信息或向实例最多添加共五个集群。展开或收缩实例的容量时，可以选择要向其添加 ESXi 服务器或要从中除去 ESXi 服务器的集群。有关更多信息，请参阅[添加和查看 Cloud Foundation 实例的集群](../sddc/sd_addingviewingclusters.html)。

### 支持定制 vSAN 存储器用于 Cloud Foundation 实例

现在，在订购实例过程中，可以通过选择 vSAN 存储驱动器的数量和大小来定制 vSAN 存储器配置。

有关更多信息，请参阅以下主题：
* [Cloud Foundation 概述](../sddc/sd_cloudfoundationoverview.html)
* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)

### Cloud Foundation 实例的 VMware vSAN 许可证版本选项：Advanced 或 Enterprise

现在，可以在 Cloud Foundation 实例订购期间选择所需的 vSAN 许可证版本。可以在订购期间购买许可证，也可以自带许可证 (BYOL)。有关更多信息，请参阅[订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)。

### Cloud Foundation 实例的新标准化 IBM 裸机服务器配置

现在提供了以下裸机服务器配置设置：
* 小型（双 Intel Xeon E5-2650 V4 / 共 24 个核心，2.2 GHz / 128 GB RAM / 12 个磁盘）
* 大型（双 Intel Xeon E5-2690 V4 / 共 28 个核心，2.6 GHz / 512 GB RAM / 12 个磁盘）

**注**：机箱的空间可容纳 12 个磁盘，但并非所有插槽都已装满。**小型**配置提供两个 1.9 TB Micron 5100 MAX 驱动器，**大型**配置提供四个 3.8 TB Micron 5100 PRO 驱动器。

有关更多信息，请参阅以下主题：
* [Cloud Foundation 概述](../sddc/sd_cloudfoundationoverview.html)
* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)

## 对 VMware vCenter Server 实例的更新

当前发行版会对新部署应用以下组件更新：

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

**注**：vCenter Server 定制订单（包含或不包含 VMware vSAN 组件）始终包含可容纳 12 个磁盘的机箱服务器，在价格估算 PDF 中对于非 vSAN 订单案例会反映为 {{site.data.keyword.baremetal_short}} 的成本略高。

有关组件的更多信息，请参阅 [vCenter Server 概述](../vcenter/vc_vcenterserveroverview.html)。

### vCenter Server 实例的多站点配置支持

现在，除了部署连接到主实例的辅助实例外，还可以部署单个 vCenter Server 实例。多站点配置模型使用轴辐式拓扑，其中包含一个主站点和最多七个辅助站点。

有关更多信息，请参阅 [vCenter Server 实例的多站点配置](../vcenter/vc_multisite.html)。

### 支持定制 vSAN 存储器用于 vCenter Server 实例

vSAN 存储器现在可用于 vCenter Server 实例，包括主实例和辅助实例。仅当选择用户定制的配置时，此存储器才可用。现在，可以在 vCenter Server 实例订购期间选择所需的 vSAN 许可证版本（Advanced 或 Enterprise）。可以在订购期间购买许可证，也可以自带许可证 (BYOL)。

有关更多信息，请参阅[订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)。

### 自带许可证 (BYOL) 用于 VMware vCenter Server 实例

BYOL 现在可用于 vCenter Server 实例。订购 vCenter Server 实例时，BYOL 支持使用一个或多个您自己的 vCenter Server、vSphere、vSAN 和 NSX VMware 许可证。

有关更多信息，请参阅以下主题：
* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)
* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)
* [订购新的 vSphere 集群](../vsphere/vs_orderinginstances.html)

## 对 VMware vSphere on IBM Cloud 的更新

### 裸机服务器的新磁盘类型

对于 VMware vSAN 组件，以下磁盘类型现在可用于 {{site.data.keyword.baremetal_short}}：
* 960 GB SSD SED
* 1.9 TB SSD SED
* 3.8 TB SSD SED

**注：**
* 3.8 TB SSD SED 驱动器在 {{site.data.keyword.CloudDataCent_notm}} 中一般可用后就会受到支持。
* 订单（包含或不包含 VMware vSAN 组件）始终包含可容纳 12 个磁盘的机箱服务器，在价格估算 PDF 中对于非 vSAN 订单案例会反映为 {{site.data.keyword.baremetal_short}} 的成本略高。

有关更多信息，请参阅[订购新的 vSphere 集群](../vsphere/vs_orderinginstances.html)。

## 对 NetApp ONTAP Select on IBM Cloud 的更新

### 新的裸机服务器选项

现在提供了以下裸机服务器配置选项：
* **高性能（中型）**- 高级许可证 / 双 Intel Xeon E5-2650 V4（共 24 个核心，2.2 GHz）/ 128 GB RAM / 每节点 22 个 1.9 TB SSD 驱动器容量 / 4 节点集群的有效容量 - 59 TB
* **高性能（大型）**- 高级许可证 / 双 Intel Xeon E5-2650 V4（共 24 个核心，2.2 GHz）/ 128 GB RAM / 每节点 22 个 3.8 TB SSD 驱动器容量 / 4 节点集群的有效容量 - 118 TB
* **高容量** - 标准许可证 / 双 Intel Xeon E5-2650 V4（共 24 个核心，2.2 GHz）/ 64 GB RAM / 每节点 10 个 4 TB SATA 驱动器容量 / 4 节点集群的有效容量 - 60 TB

**注**：3.8 TB SSD 驱动器在 {{site.data.keyword.CloudDataCent_notm}} 中一般可用后就会受到支持。

有关更多信息，请参阅以下主题：
* [NetApp ONTAP Select 概述](../netapp/np_netappoverview.html)
* [订购 NetApp ONTAP Select 实例](../netapp/np_orderinginstances.html)

## 新增和更新的文档

VMware Cloud Foundation 用户可以将逐步指示信息与 {{site.data.keyword.cloud_notm}} 上 VMware 的 NSX 平台一起使用，以允许虚拟机相互通信和使用因特网。有关更多信息，请参阅[针对 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} (VCF) 上的工作负载 VM 设置 NSX](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}。

## 用户界面更新和增强功能

* 可以添加到集群的最大 ESXi 服务器数现在已更新为 32 个服务器。最大集群数仍然为 5 个。
* 在**部署的实例**页面上，实例摘要表中的 **ESXi 服务器**列已替换为**版本**列，在此列中可以找到实例部署或更新到的发行版版本。
* 实例详细信息页面上现在提供了用于 Cloud Foundation 实例的 SDDC Manager 的版本。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择适当的设置。
