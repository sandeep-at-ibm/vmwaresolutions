---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# 简介
{: #opsprocs-intro}

许多 IT 组织会在运行手册中记录其操作过程。运行手册是一组标准化的文档、参考和过程，用于说明常见的重复执行的 IT 任务。IT 员工通过参考运行手册，能以最佳方式完成自己的工作。运行手册通过标准化提高了组织效率，可更有效地帮助员工上手。通常有两种类型的运行手册：

1. 常规文档，用于捕获过程、指南和任务。此类文档通常是一般性文档，指的是供应商提供的现有文档。
2. 为企业编写的专用文档。此类文档特定于系统、应用程序或应用程序套件，其中的内容未由供应商文档涵盖。在记录专用文档时，建议采用以下结构：

 * 概述 - 对服务的概述，包含多个部分，用于描述：
    * 服务是什么？为什么企业需要该服务？
    * 服务的主要联系人是谁？
    * 如何使用服务报告问题？
 * 构建 - 此部分主要关注服务的开发团队和主要软件组件以及服务的构造方式。包含有关软件产品、OVA 位置、分发介质或源代码位置的信息，以及打包或分发发行版所需的步骤。此外，还包含有关新开发者入门所需的任何指示信息。
 * 部署 - 此部分主要关注操作团队以及如何部署软件。包含硬件和虚拟化基础架构的详细信息以及如何构建虚拟机 (VM) 的详细信息，包括：vCPU、RAM 和磁盘需求、操作系统版本和配置，以及要安装的中间件或包。
 * 过程 - 常见任务的分步骤指导信息，例如添加、更改和删除操作，常见问题及其解决方案、故障诊断建议等。
 * 故障诊断 - 来自监视系统的常见警报的列表，包括针对这些警报的分步骤任务，以及有关对服务进行故障诊断的通用指导信息。
 * 灾难恢复计划和过程 - 有关如何在主位置发生灾难时，在其他位置恢复服务的详细信息。
 * 服务级别协议 - 商定的服务参数，例如操作级别协议、关键点指标、可用性目标、恢复点目标和恢复时间目标。

大多数 IT 组织都有多个运行手册作为其参考手册。此系列文档旨在用作使用 vCenter 服务器实例的组织的常规运行手册。虽然每个运行手册的内容都特定于组织的需求，但创建运行手册的方法是相当标准的，分为两个阶段：

1. 第一个阶段是决定需要记录哪些过程，并在列出这些过程时，为每个过程提供足够的详细信息。
2. 第二个阶段是持续进行的，包括维护、更新和更正这些过程，添加新过程以及使不再需要的过程引退。

{{site.data.keyword.vmwaresolutions_full}} 支持您利用内部部署中团队的现有技能、工具集和运行手册来管理 {{site.data.keyword.cloud_notm}} 中的实例。但是，我们已创建以下常规文档来捕获常见过程、指南和任务：

* 配置任务 - 这些任务是系统管理员需要执行的常见活动，用于对环境进行定制，以满足企业需求和响应服务请求，例如添加新 VM 和增加容量。这些任务分组为以下结构：
 * 通用指南
 * VM 过程
 * vCenter 过程
 * vSphere ESXi 主机过程
 * 存储器过程
 * 网络过程
* 警报 - vSphere 包含事件和警报子系统，用于跟踪 vSphere 环境中发生的事件，并在 vCenter 中提供这些信息。此部分描述了此子系统以及如何在企业中启用和使用警报。
* 主动日常检查 - 借助这些检查，系统管理员可使环境保持正常运行。通过日常执行这些检查，应该可以防止与容量和性能相关的许多常见问题影响工作负载。
* 故障诊断 - 即使执行主动日常检查，也会发生影响工作负载的问题，因此，需要尽快解决底层问题。这些故障诊断指南和一些常见故障诊断场景可帮助系统管理员快速识别并解决这些问题。
* 合规性 - 合规性指南提供了有关根据监管合规性机制或行业最佳实践来保持环境合规性的一些洞察。本指南的重点是指导如何强化 VMware 安全性，这其中记录了 VMware 环境最佳实践的多个列表。

上述许多任务是在 Operations Management on {{site.data.keyword.cloud_notm}} 中自动执行的，因此对于不在此工具中执行的任务，系统管理员手动执行过程要轻松得多。您必须在 Operations Management on {{site.data.keyword.cloud_notm}} 中监视 VMware 环境的核心组件，实现此操作的步骤如下所示：

## Operations Management on IBM Cloud
{: #opsprocs-intro-ops-mgmt}

您可能已实施了企业工具，可利用该工具来监视和管理 vCenter Server 实例。表 1 描述了 vCenter Server 环境的核心组件，为什么需要监视这些组件，以及如何使用 Operations Management on {{site.data.keyword.cloud_notm}} 来监视这些组件。有关更多信息，请参阅参考体系结构文档。

表 1. vCenter Server 环境核心组件

|组件|原因|监视工具|
|---|---|---|
|vCenter|vCenter 是用于管理 vSphere 主机并管理虚拟化构造（例如，集群）的基础架构管理组件。vSAN 通过 vCenter 进行监视。vSphere 联网（例如，分布式交换机和端口组）也通过 vCenter 进行监视。| vRealize Operations Manager (vROps) 和 VMware SDDC Health Management Pack。vRealize Log Insights (vRLI) 从 vCenter 中收集日志数据，vSphere 的内容包将特定理解添加到日志，并转而向 vROps 发送警报。|
|vSphere 主机|vSphere 主机向计算 VM 提供虚拟化的 CPU、RAM 和网络。|vROps 通过 vCenter 进行监视。vRLI 用于收集日志数据。|
|vSAN|vSAN 通过合并主机中的存储器以供 VM 使用来提供数据存储。影响容量和性能的问题还会影响在这些 VM 上运行的应用程序。|vROps 和 Management Pack for vSAN 提供了其他仪表板来帮助监视 vSAN。vCenter vSAN 运行状况检查通过 vROps 进行收集。vRLI 用于从 vCenter 中收集日志数据。|
|NSX|NSX 提供计算 VM 利用的虚拟化网络组件，网络中的任何故障都可能会影响在这些 VM 上运行的应用程序。|vROps 和 vROps Management Pack for VMware NSX 提供了对网络拓扑的透视。vRLI 从 NSX 组件（例如，控制器、ESG 和逻辑交换机）中收集日志数据。vRealize Network Insight (vRNI) 提供对网络问题的深入故障诊断。|

Operations Management on {{site.data.keyword.cloud_notm}} 除了监视外，还提供了有关配置、合规性以及本文档中详细描述的许多主动任务的帮助。


## 相关链接
{: #opsprocs-intro-links}

* [vSphere 监控](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [VMware 安全强化指南](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [关于更改 vCenter Server 工件的注意事项](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
