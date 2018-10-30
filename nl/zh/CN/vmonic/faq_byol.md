---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# 关于许可和 BYOL 的常见问题

查找有关许可的常见问题的答案，包括 {{site.data.keyword.vmwaresolutions_full}} 的自带许可证 (BYOL) 功能。

## 什么是 BYOL？

自带许可证 (BYOL) 是向 V1.8 和更高发行版中 VMware Cloud Foundation 实例以及 V2.0 和更高发行版中 vCenter Server 和 vSphere 集群提供的一项功能。利用 BYOL，在订购实例时，您可以将自己的 VMware 许可证用于以下一个或多个 VMware 软件组件：
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

如果选择将自己的许可证用于 VMware 组件，并且为其提供有效的许可证密钥，那么不会向 IBM 订购此组件的许可证，并且您的 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) 帐户每月也不会发生此组件的许可费用。

**注**：BYOL 功能不可用于业务合作伙伴用户。

## 在何处管理通过 VMware vSphere on IBM Cloud 订购的许可证和组件？

下了订单以为 VMware vSphere on {{site.data.keyword.cloud_notm}} 创建新集群后，会交付 VMware 许可证、ESXi 服务器和其他联网组件，并可在 {{site.data.keyword.slportal}} 中对这些内容进行管理。

部署后，请转至 {{site.data.keyword.vmwaresolutions_short}} 控制台以使用保存的配置来扩展新集群。有关扩展的更多信息，请参阅[扩展现有 vSphere 集群](../vsphere/vs_scalingexistingclusters.html)。

## BYOL 需要哪些许可证版本和 CPU 数量？

以下需求适用于 BYOL 的许可证版本。

### vCenter Server 实例的 BYOL 需求

表 1. vCenter Server 实例的许可证版本和 CPU 最低需求

  |VMware 组件|需要的许可证版本|需要的最少 CPU 数
  |:-------------  |:-------------  |:-------|
  |vCenter Server|Standard|不适用|
  |vSphere|Enterprise Plus|8 个 CPU|
  |vSAN|Advanced 或 Enterprise|8 个 CPU|
  |NSX|Standard、Advanced 或 Enterprise|8 个 CPU|

### Cloud Foundation 实例的 BYOL 需求

表 2. Cloud Foundation 实例的许可证版本和 CPU 最低需求

  |VMware 组件|需要的许可证版本|需要的最少 CPU 数
  |:-------------  |:-------------  |:-------|
  |vCenter Server|Standard|不适用|
  |vSphere|Enterprise Plus|8 个 CPU|
  |vSAN|Advanced 或 Enterprise|8 个 CPU|
  |NSX|Enterprise|8 个 CPU|

## 如果我提供的许可证密钥不正确，会发生什么情况？

系统将验证您提供的所有许可证密钥，以确保它们对于相应的 VMware 组件是正确的，并且满足 VMware 组件的最低版本和 CPU 需求。如果任何许可证密钥的验证失败，那么您将收到通知，并且无法继续处理该实例订单。

## 我能提供超过 8 个 CPU 的许可证密钥吗？

可以。对于每个 VMware 组件，需要每个 CPU 一个许可证。目前，所有 vCenter Server 和 Cloud Foundation 服务器都有两个 CPU。因此，每个服务器都需要两个许可证。建议您提供可以支持基本实例以及未来要添加到该实例的任何扩展节点的许可证密钥。

## 使用 BYOL 功能时，可以提供 SDDC Manager 许可证吗？

不行。我们与 VMware 的协议要求我们必须接受客户的实际许可证密钥。虽然 Cloud Foundation 部署包含 SDDC Manager 许可证，但我们不接受 SDDC Manager 许可证密钥文件，也不会针对 BYOL 验证这些文件。因此，IBM 会对所有实例收取 SDDC Manager 许可证费用。SDDC Manager 许可证的费用在 Cloud Foundation 实例的总体许可证费用中所占比例不大。

## 可以将 BYOL 功能用于某些 VMware 组件，而为其他组件购买每月许可证吗？

可以。您可以使用 BYOL 功能或购买许可证来用于四个 VMware 组件的任意组合。订购 vCenter Server 或 Cloud Foundation 实例时，{{site.data.keyword.vmwaresolutions_short}} 控制台支持您直接选择许可选项。初始订购实例时的许可选项会在该实例的生命周期内应用。

## 对于特定 VMware 组件，可以将 BYOL 功能用于某些许可证，而向 IBM 购买其他许可证吗？

可以。如果为特定 VMware 组件选择了 BYOL，那么在创建新集群时，可以选择是输入新的 BYOL 密钥、继续使用现有 BYOL 密钥，还是购买 IBM 为该集群提供的许可。目前，仅 VMware vSphere Enterprise 和 VMware vSAN 可用于针对每个集群进行许可。

## 可以在创建新集群时使用 BYOL 吗？

可以。创建新集群时，可以通过现有 BYOL 许可证使用 BYOL，也可以输入新的 BYOL。在创建新集群时，您还可以购买 IBM 提供的预订许可证。目前，仅 VMware vSphere Enterprise 和 VMware vSAN 可用于针对每个集群进行许可。

## 如何管理 BYOL 许可证？

可以在完成实例部署后，使用 VMware vSphere Web Client 来管理 BYOL 许可证。

## 日后向实例添加更多 ESXi 服务器时，该实例会验证 BYOL 许可证的容量是否足够吗？

会的。向已部署的实例添加更多 ESXi 服务器时，会自动根据指定的 ESXi 服务器数来检查 BYOL 许可证的容量。如果容量不足，那么不会添加 ESXi 服务器，并且您将收到控制台通知。

## 如何确定在使用 BYOL 的集群上有多少许可容量可用？

要查找许可证密钥中可用的 CPU 数，请完成下列步骤：
1. 转至**已部署的实例**页面。
2. 找到并单击该实例。
3. 在**基础架构**选项卡中，单击要检查许可容量的集群。可用的 CPU 数会列在**用户提供的许可证**表中。

## 如果选择 BYOL 许可选项，IBM 会提供支持吗？

如有任何实例配置问题，您可以继续联系 IBM 支持人员。但是，如果确定报告的问题是针对 BYOL VMware 组件的，那么会将您定向到 VMware 支持。

## 如果我使用的是 BYOL，为什么 vSphere 许可费用会在价格估算列表上显示？会因此向我收费吗？

供应 {{site.data.keyword.baremetal_short}} 时，已安装 VMware vSphere，并且已包含 vSphere 许可证。如果为 vSphere 选择了 BYOL，那么在实例部署时会自动启动相应流程来除去包含的 vSphere 许可证。然后，会将相应许可证费用计入您的 {{site.data.keyword.cloud_notm}} 帐户。您不必在此过程中执行任何操作。

## 我仍可以对 BYOL 使用现有的手动过程吗？

引入 BYOL 功能后，建议不要继续使用手动过程。如果要使用 BYOL，请在订购实例时提供您自己的许可证。

## 其他 VMware 产品（如 VMware vRealize Automation、VMware vRealize Operations 或 VMware vRealize Log Insight）支持 BYOL 吗？

不支持，因为这些 VMware 产品不是实例部署的一部分。除了初始部署以外可能还安装了这些 VMware 产品，这就需要客户机或其代理程序来执行安装和许可。

## 可以通过 vCenter Server with Hybridity Bundle 订购 NFS 存储器吗？

对于新部署的实例，仅支持 vSAN 全闪存存储器。vCenter Server with Hybridity Bundle 包含 vSAN Advanced 或 vSAN Enterprise 许可。

如果您的 vCenter Server 实例具有 NFS 存储器，那么可以将现有实例升级到 vCenter Server with Hybridity Bundle。虽然在升级期间会订购 vSAN Advanced 许可，但您无需供应全闪存 vSAN 集群。

## 可以将 BYOL 用于 vCenter Server with Hybridity Bundle 吗？

不能提供自己的 VMware 许可 (BYOL) 用于 {{site.data.keyword.cloud_notm}}。vCenter Server with Hybridity Bundle 要求所有 VMware 许可证均由 IBM 提供。

## vCenter Server with Hybridity Bundle 许可和 vCenter Server 许可有何不同？

vCenter Server 中提供的各个 VMware 许可证按 CPU 定价。与 IBM 提供的所有按 CPU 定价的 VMware 许可证一样，在每个 CPU 的核心数超过 16 个的所有服务器上，将提价 1.3 倍，例如对于双 Intel Xeon Gold 6140。

vCenter Server with Hybridity Bundle 是一组按核心（而不按 CPU）许可的规定 VMware 许可证和版本。因此，这些实例的许可价格不会更改。

## 哪些 IBM 提供的 VMware 许可证组件和版本可用于 vCenter Server with Hybridity Bundle？

vCenter Server with Hybridity Bundle 的新实例包括 VMware vSphere Enterprise Plus、VMware vCenter Standard、VMware NSX Advanced 或 Enterprise、VMware vSAN Advanced 或 Enterprise 以及 VMware Hybrid Cloud Extension (HCX)。

如果您的 vCenter Server 实例具有 NSX Base Edition，那么在订购 vCenter Server with Hybridity Bundle 时，会自动将其升级到 NSX Advanced。

## 可以将 vCenter Server with Hybridity Bundle 中包含的 NSX Advanced Edition 升级到 NSX Enterprise Edition 吗？

虽然 vCenter Server with Hybridity Bundle 包含 NSX Advanced，但在订购 vCenter Server with Hybridity Bundle 后，可以升级到 NSX Enterprise Edition。要进行升级，请使用 {{site.data.keyword.vmwaresolutions_short}} 控制台中实例详细信息页面选项卡上的**更新和补丁**选项卡。

### 相关链接

* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)
* [Cloud Foundation 实例](../sddc/sd_cloudfoundationoverview.html)
* [访问控制台](loginmethod.html)
* [联系 IBM 支持人员](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
