---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware 实例的部署后注意事项

{{site.data.keyword.vmwaresolutions_full}}、VMware vCenter Server 和 VMware Cloud Foundation 产品不是受管服务。您负责所有软件组件的配置、安全性、管理和监视。借助对解决方案的完整管理访问权，您拥有强大的能力和灵活性，这需要在各种领域具备丰富的技术、管理和运作专业知识。在 {{site.data.keyword.cloud_notm}} 中管理 VMware 实例需要的规划和专业知识与规划内部部署实例时相同。软件定义的技术（例如，VMware NSX 和 VMware vSAN）大大简化了实例管理的某些方面，但这可能需要具备新的技能和工具，才能妥善进行管理和操作。将 {{site.data.keyword.cloud_notm}} 自动化 VMware 部署的能力、速度和可靠性与相应的操作规划和测试相结合，可确保快速成功地实现混合云。

请查看以下注意事项，以了解您在部署实例前后须承担的管理和操作责任。

以下列表并非详尽无遗。有关更多信息，请参阅 [IBM 管理的服务](/docs/services/vmwaresolutions/services/managing_imi.html)。
{:note}

## IBM Cloud 帐户访问权

要管理对 {{site.data.keyword.cloud_notm}} 帐户的访问权，请允许您团队的其他成员在 {{site.data.keyword.vmwaresolutions_short}} 控制台中访问实例。有关更多信息，请参阅[邀请用户访问服务和资源](/docs/services/vmwaresolutions/vmonic/iamuserinvite.html)。

## 限制

请熟悉实例的以下限制：

- [更改 vCenter 工件产生的影响](/docs/services/vmwaresolutions/vcenter/vcenter_chg_impact.html)
- [联网注意事项和限制](/docs/services/vmwaresolutions/vcenter/vc_networkingonvcenterserver.html)
- [常见问题](/docs/services/vmwaresolutions/vmonic/faq.html)

## 网络设计和连接

完成以下步骤以管理对 {{site.data.keyword.cloud_notm}} 网络和 VMware 管理组件的访问权，并规划 {{site.data.keyword.cloud_notm}} 网络拓扑。

- 使用 [{{site.data.keyword.cloud_notm}} VPN](https://www.softlayer.com/vpn-access) 或 [{{site.data.keyword.cloud_notm}}“直接链路”连接](https://www.ibm.com/cloud/direct-link)来访问实例管理端点。
- 设计从实例内部建立公用网络连接的策略。您的选项包括：样本客户 VMware NSX Edge 服务网关 (ESG)、网关设备（例如，Vyatta 和 FortiGate）以及在 {{site.data.keyword.cloud_notm}} 网络或在通过 DirectLink 访问的您自己的网络上部署的代理服务器。
- 规划是在具有 [{{site.data.keyword.cloud_notm}} 可移植 IP 地址](/docs/infrastructure/subnets/getting-started.html)的 {{site.data.keyword.cloud_notm}} VLAN 上部署工作负载，还是[使用您自己的 IP 地址在 NSX 逻辑交换机 (VXLAN) 上](/docs/services/vmwaresolutions/archiref/nsx/nsx_overview.html)部署工作负载。请注意，使用 NSX 软件定义的联网 (SDN) 可为您在 {{site.data.keyword.cloud_notm}} 中管理并确保工作负载网络安全提供最大的灵活性。
- 使用 NSX ESG、[IBM Cloud Vyatta](https://console.cloud.ibm.com/catalog/infrastructure/virtual-router-appliance) 和 DirectLink 对等连接来规划与工作负载的连接（网络地址转换、虚拟专用网和路由）。
- 如果要实现跨 vCenter NSX，请确保在部署任何本地工作负载之前，本地分段标识范围不重叠。

## 安全性规划和强化

您负责保护、加密和监视自己的 VMware 实例和工作负载，以满足企业、行业和法规标准。完成以下步骤以确保适当的安全性。

- 更改 {{site.data.keyword.vmwaresolutions_short}} 控制台中显示的所有密码，并使用您自己的密码管理系统。请注意，IBM 保留持续自动化和支持所需的独特用户标识。
- 复查所有组件上的密码策略，例如复杂性和到期时间段。
- 复查所有组件上的加密设置。
- 规划并实施相应的物理或虚拟防火墙解决方案，例如 NSX 分布式防火墙 (DFW)、NSX ESG、[Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_considerations.html) 和 [IBM Cloud Vyatta](https://console.cloud.ibm.com/catalog/infrastructure/virtual-router-appliance)。
- 规划并实施相应的应用程序负载均衡和安全性解决方案，例如 [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/f5_considerations.html)。
- 规划并实施相应的安全信息和事件管理 (SIEM) 解决方案，例如 [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence)。
- 规划并实施相应的漏洞扫描。
- 使用 [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html) 等解决方案为实例规划并实施相应的变更管理、核准、审计和访问控制。

## 定制

完成以下步骤以根据您的需求定制基本 VMware 实例安装。

- 使用您自己的认证中心 (CA) 为组件（例如，vCenter、VMware Platform Services Controller (PSC) 和 NSX Manager）生成证书。
- 配置部署的服务。例如：
  - 对于 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}，请配置 AD 集成、访问控制、简单电子邮件传输协议 (SMTP) 设置和合规性策略。
  - 对于 Zerto on {{site.data.keyword.cloud_notm}}，由于不支持网络地址转换程序 (NAT) 遍历，因此请规划 Zerto Virtual Replication Appliance (VRA) 通信的 IP 寻址和路由。请考虑使用隧道或重新部署 VRA，以便执行相应的寻址和路由。
  - 对于 Veeam on {{site.data.keyword.cloud_notm}} 和 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 等备份服务，请配置备份作业，（可选）配置其他存储器，以及配置监视警报。
  - 对于 F5 on {{site.data.keyword.cloud_notm}} 和 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 等联网和安全服务，请根据网络拓扑和其他需求来配置网络接口、证书、高可用性 (HA) 配置和规则。

## Active Directory

完成以下步骤以确保配置和管理正确的单点登录 (SSO)。

- 配置 Active Directory (AD) 服务器更新和重新引导安排。
- 如果已选择用于将 AD 服务器部署到 vSphere 集群中的选项，请为服务器提供 Microsoft Windows 许可和激活，以确保合规性和可用性。
- 在实例与内部部署 AD 服务器之间建立相互信任。
- 将 NSX VPN（如果适用）与 AD SSO 相集成。
- 将 ESXi 主机与 AD SSO 相集成。

## 维护规划

完成以下步骤以确保正确规划软件维护。

- 通过代理[设置 VMware Update Manager (VUM)](/docs/services/vmwaresolutions/archiref/vum/vum-intro.html) 以获取 VMware 更新。
- 如果适用，请通过代理设置 vSAN，以维护 vSAN 硬件兼容性列表 (HCL) 数据库。
- 针对 VUM 不支持的 VMware 组件，规划常规维护。例如，VMware vCenter、PSC 和 NSX。
- 复查 vSphere Enhanced vMotion Compatibility (EVC) 配置。如果当前版本的 vSphere 不支持 EVC 用于您的硬件级别，那么说明您的集群可能未配置为启用 EVC。
- 针对 Veeam on {{site.data.keyword.cloud_notm}}、Zerto on {{site.data.keyword.cloud_notm}} 和 F5 on {{site.data.keyword.cloud_notm}} 等附加组件服务，规划定期维护。

## 监视

确保规划并实施以下解决方案来监视实例和实例组件。

- 日志记录服务器，包括所有实例组件的日志转发或收集，以及充分的日志保留时间。
- 警报基础架构，包括根据需要配置 SMTP 服务器和短消息服务 (SMS) 网关。
- 主动监视主机、驱动器、管理软件和网络。
- vSAN 监视（如果适用）。
- 容量监视和规划。您可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台中针对实例[添加和除去集群](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)以及[添加和除去主机](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservers.html)。
- 监视备份基础架构和备份作业。

## 业务连续性和可用性

您的 VMware 实例是在 {{site.data.keyword.cloud_notm}} 中的裸机服务器上运行。完成以下步骤以确保您针对高可用性和业务连续性进行了充分的规划。

- 根据您的需求，复查 vSphere HA 和 vSphere 分布式资源调度程序 (DRS) 配置。
- 根据您的需求，复查网络和 Storage I/O Control 配置。
- 根据您的需求，配置虚拟机启动顺序。
- 根据需要配置资源池以用于管理和工作负载。
- 规划、实施和监视用于[实例管理组件](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html)和工作负载的备份解决方案。
- 规划实例管理的高可用性，包括可以使用多个实例、多个集群、vCenter HA 和 PSC HA。
- 使用 [Zerto Disaster Recovery](/docs/services/vmwaresolutions/services/addingzertodr.html)、[Veeam Backup and Replication](/docs/services/vmwaresolutions/services/veeam_considerations.html) 和 [IBM Spectrum Protect Plus](/docs/services/vmwaresolutions/services/spp_considerations.html) 等解决方案为工作负载规划业务连续性。

## 存储规划

除了容量规划之外，请完成以下操作，以确保存储器配置满足性能和可用性需求。

- 存储器性能取决于各种因素，包括 RAID 配置和磁盘条带分割；网络配置；块大小；为网络连接存储器配置的 IOPS（每秒输入/输出操作数）；VM 硬件配置和存储器连接方法；集群和复制方法；以及使用加密、去重和压缩等存储策略。规划用于测试和调整配置以满足存储性能需求的时间。
- 复查 vSAN 存储策略
  - 相比 RAID-5，RAID-1 提供的性能更高，可能发生连续故障的时段更短，例如重建时间更短。但是，RAID-5 的存储开销更少。
  - RAID-6 提供双重故障保护，但至少需要六台主机，而 RAID-5 只需要四台主机。
- 要向 vSAN 集群添加更多存储器，必须向集群添加新的主机或改为添加 {{site.data.keyword.cloud_notm}} 耐久性 NFS 存储器。目前不支持向现有主机添加磁盘。
- 如果将其他 {{site.data.keyword.cloud_notm}} 耐久性 NFS 存储器安装到集群中，请确保遵循相应的体系结构指南，并使用 `SDDC-DPortGroup-NFS` 端口组地址来配置存储器的主机路径。必须将这些地址（而不是主机本身）授权给存储器。有关更多信息，请参阅[连接的存储器基础架构管理](/docs/services/vmwaresolutions/archiref/attached-storage/storage-infra-mgmt.html#vsphere-host-static-routing)。

此外，请参阅 developerWorks 诀窍，其中举例说明了如何使用 IBM Spectrum Protect Plus [向 VMware 集群添加更多耐久性存储器](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)。

### 相关链接

* [解决方案概述](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
* [设计概述](/docs/services/vmwaresolutions/archiref/solution/design_overview.html)
* [缩放容量](/docs/services/vmwaresolutions/archiref/solution/solution_scaling.html)
