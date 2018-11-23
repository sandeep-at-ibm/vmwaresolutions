---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-09"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 从 vCenter Server 实例中除去 Hybridity Bundle

要从 vCenter Server 实例中除去 Hybridity Bundle 许可证，必须在 VMware vSphere Web Client 中将 VMware NSX 和 VMware vSAN 租用许可证密钥替换为自带许可证 (BYOL) 密钥。此外，您必须开具支持凭单以取消租用许可证的费用。

对许可证降级可能会导致 vCenter Server 实例发生故障。您可以选择自行承担许可证降级风险，但请首先考虑降级时不可用的功能。有关更多信息，请参阅 [VMware 组件版本的比较图表](../archiref/solution/appendix.html)。
{:important}

## 从多站点环境中除去 Hybridity Bundle 之前的重要注意事项

在从多站点环境中除去 Hybridity Bundle 之前，请查看以下注意事项：

* 除去租用许可证之前，必须对所有多站点部署应用 BYOL 许可证。
* 必须合并 VMware NSX 许可证并具有足够的容量在所有多站点部署中使用。
* 必须创建单个支持凭单，以从所有多站点部署中除去 Hybridity Bundle。

从多站点环境除去 Hybridity Bundle 时，将应用 BYOL 许可证。对于多站点配置中的所有站点，NSX 许可证会自动还原为所有站点中最低的许可证版本。您必须确保许可证版本在多站点配置中的所有站点之间保持一致。
{:note}

## 除去 Hybridity Bundle 之前

除去 Hybridity Bundle 之前，请先验证以下需求：

* 您具有启用了 Hybridity Bundle 的 V2.4 或更高版本的 vCenter Server 实例。
* 您没有在 vCenter Server 实例上安装 VMware HCX on {{site.data.keyword.cloud_notm}} 服务。
* 您有权以管理员身份访问 VMware vSphere Web Client。
* 如果尚未将可用的 BYOL 密钥应用于 VMware NSX 和每个 VMware vSAN 集群，请进行应用。
* （可选）如果尚未将可用的 BYOL 密钥应用于 VMware vCenter Server 和 VMware vSphere Enterprise Plus 许可证，请进行应用。

## 除去 Hybridity Bundle 的过程

1. 以**管理员**身份登录到要除去 HHybridity Bundle 的 VMware vSphere Web Client。
2. 单击**主页 > 管理 > 许可 > 许可证**。
3. 单击**资产**选项卡。
4. 要安装 VMware NSX BYOL，请完成以下步骤：
   1. 单击**解决方案**选项卡。
   2. 选择 NSX for vSphere，然后单击**所有操作 > 分配许可证**。
   3. 单击**添加**图标，然后输入许可证密钥。单击**下一步**。
   4. 输入许可证的名称，然后单击**下一步**。单击**完成**以添加许可证。
   5. 选择新的许可证密钥。
   6. 记下已应用的许可证和所替换许可证的完整许可证密钥。

   您必须使许可证详细信息可供此过程稍后使用。
   {:important}
   7. 单击**确定**以分配许可证。
5. 要安装 VMware vSAN BYOL，请完成以下步骤：
   1. 单击**集群**选项卡。
   2. 对与 vCenter Server 实例关联的每个 vSAN 集群，完成以下步骤：
    1. 选择 vSAN 集群，然后单击**所有操作 > 分配许可证**。
    2. 单击**添加**图标，然后输入许可证密钥。单击**下一步**。
    3. 输入许可证的名称，然后单击**下一步**。单击**完成**以添加许可证。
    4. 选择新的许可证密钥。
    5. 记下集群名称以及已应用的许可证和所替换许可证的完整许可证密钥。

您必须使许可证详细信息可供此过程稍后使用。
   {:important}
    6. 单击**确定**以分配许可证。
6. （可选）要安装 VMware vCenter Server BYOL，请完成以下步骤：
   1. 单击 **vCenter Server 系统**选项卡。
   2. 选择 vCenter Server，然后单击**所有操作 > 分配许可证**。
   3. 单击**添加**图标，然后输入许可证密钥。单击**下一步**。
   4. 输入许可证的名称，然后单击**下一步**。单击**完成**以添加许可证。
   5. 选择新的许可证密钥。
   6. 记下已应用的许可证和所替换许可证的完整许可证密钥。

   您必须使许可证详细信息可供此过程稍后使用。
   {:important}

   7. 单击**确定**以分配许可证。
7. （可选）要安装 VMware vSphere Enterprise Plus BYOL，请完成以下步骤：
  1. 单击**主机**选项卡。
  2. 请对与 vCenter Server 实例关联的每个集群分别完成以下步骤，或者如果要将同一许可证应用于与 vCenter Server 关联的所有集群，请同时对所有集群完成以下步骤：
    1. 选择与集群关联的所有主机，然后单击**所有操作 > 分配许可证**。
    2. 单击**添加**图标，然后输入许可证密钥。单击**下一步**。
    3. 输入许可证的名称，然后单击**下一步**。单击**完成**以添加许可证。
    4. 选择新的许可证密钥。
    5. 记下集群名称以及已应用的许可证和所替换许可证的完整许可证密钥。

    您必须使许可证详细信息可供此过程稍后使用。
   如果所有集群上的许可证密钥不同，请确保记下与每个许可证密钥关联的集群名称。
    {:important}

    6. 单击**确定**以分配许可证。
8. 除去租用许可证。
   1. 单击**许可证**选项卡。
   2. 选择在步骤 4 到 7 中所替换的许可证。
   3. 单击**除去许可证**图标。
9. 开具支持凭单并提供以下信息，以取消租用许可证的费用：
  * vCenter Server 实例的名称。
  * 与 vCenter Server 实例关联的标识。
  * 在此过程中安装的 BYOL 许可证密钥的列表。（如果适用）为 vSphere 和 vSAN 集群提供带许可证密钥的实例和集群名称。
  * 在此过程中除去的租用许可证密钥的列表。（如果适用）为 vSphere 和 vSAN 集群提供带许可证密钥的实例和集群名称。

  IBM 支持团队和运营团队会访问您的 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) 帐户的 vCenter 管理层，以验证租用许可证是否已除去。如果确定租用许可证已除去，即会取消 Hybridity Bundle 租用许可证费用。
  {:note}

### 相关链接

* [订购 vCenter Server with Hybridity Bundle 实例](vc_hybrid_orderinginstance.html)
* [查看 vCenter Server with Hybridity Bundle 实例](vc_hybrid_viewinginstances.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
