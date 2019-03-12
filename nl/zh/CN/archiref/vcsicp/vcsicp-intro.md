---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# VMware vCenter Server on IBM Cloud 和 IBM Cloud Private 简介
{: #vcsicp-intro}

本文档展示了 {{site.data.keyword.cloud}} 的应用程序现代化之旅，侧重于支持将集成的多个云用于应用程序现代化的云管理组件：

- **vCenter Server on {{site.data.keyword.cloud_notm}}** - vCenter Server 是 {{site.data.keyword.vmwaresolutions_short}} 中的一个产品，也是在 {{site.data.keyword.cloud_notm}} 上自动供应的基于 VMware 的平台。
- **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} 是用于开发和管理容器化应用程序的应用程序平台，这些应用程序部署到虚拟化的基础架构平台（例如 VMware）。
- **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} 是 {{site.data.keyword.cloud_notm}} 上的一种受管服务，使用 Kubernetes 作为编排引擎，在单租户集群中自动部署、扩展和操作应用程序容器。
- **IBM Multi-Cluster Manager** - MCM 在各种云和集群中提供用户可视性、以应用程序为中心的管理（策略、部署、运行状况和操作）以及基于策略的合规性。通过 MCM，您可以控制 Kubernetes 集群。
- **{{site.data.keyword.cloud_notm}} Automation Manager** - CAM 是在 {{site.data.keyword.icpfull_notm}} 上运行的多云自助服务管理平台，支持开发者和管理者满足其业务需求。

## IBM Cloud 上的应用程序现代化
{: #vcsicp-intro-app-mod}

应用程序现代化这一术语描述的是将现有应用程序转变为使用云上的新方法的过程。如今，客户寻求的是创新、高效的方法，以帮助他们根据业务和应用程序的复杂性进行这一转变。

业务压力要求加快产品上市速度。您的现有产业不仅包括应用程序，还包括数据、流程、业务逻辑和用户界面，所有这些都需要调整以随时适应新的业务需求。

应用程序现代化的优点如下：

- 提高开发者的工作效率。
- 提高运营效率。
- 降低构建新功能的成本。
- 在短时间内交付扩展容量。

据 IBM 所知，70% 的私有云是在应用程序环境现代化需求的推动下采用的。然而，大多数组织是分阶段逐渐实现应用程序现代化，这就需要一个混合及多云的环境，其中：

- 通常在大型机或 UNIX 系统上运行的复杂和单一庞大的旧应用程序仍为内部部署。
- 用于记录系统 (SoR) 的 x86 环境、安全敏感的应用程序以及受监管的工作负载会被放置在虚拟化基础架构或私有云上。
- SAP 或高性能计算等应用程序会消耗裸机资源。
- 可移至公共云的安全敏感的工作负载和一些受监管的工作负载将移至专用环境。
- Web、移动、IoT、AI 或视频等全接触系统 (SoE) 将移至公共云。

例如，通用模式是将前端 SOE 应用程序部署为容器，并将数据库和旧中间件部署在私有云的 VM 上。

由于您的 IT 基础架构和业务需求是独一无二的，因此您需要一种现代化的方法，以帮助加快业务价值交付，降低风险并保护现有投资。IBM 正好提供了此类方法，您可加以定制来满足与应用程序现代化相关的独特业务和技术需求。

有五个文档展示了 {{site.data.keyword.cloud_notm}} 应用程序现代化之旅中使用的技术的不同方面，本文档是其中之一：

* _vCenter Server 和 {{site.data.keyword.icpfull_notm}}_ - 当前指南，这是部署以下平台的参考体系结构：
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - {{site.data.keyword.vmwaresolutions_short}} 中的一个产品，也是在 {{site.data.keyword.cloud_notm}} 上自动供应的基于 VMware 的平台。
  - **{{site.data.keyword.icpfull_notm}}** - 一种用于开发和管理容器化应用程序的应用程序平台。{{site.data.keyword.icpfull_notm}} 是一个集成环境，包含容器编排器 Kubernetes、专用映像存储库、管理控制台、监视框架和图形用户界面，该界面提供了一个集中位置来部署、管理、监视和扩展应用程序。
  - **{{site.data.keyword.cloud_notm}} Automation Manager** - 一种企业就绪型基础架构即代码 (IaC) 平台，它提供了一个窗格，通过使用存储库中存储和进行版本控制的模板，供应基于 VM 的工作负载以及基于 Kubernetes 的工作负载。
* [vCenter Server 和 {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - 部署以下平台的参考体系结构：
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - {{site.data.keyword.vmwaresolutions_short}} 中的一个产品，也是在 {{site.data.keyword.cloud_notm}} 上自动供应的基于 VMware 的平台。
  - **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.cloud_notm}} 上的一种受管服务，使用 Kubernetes 作为编排引擎，在单租户集群中自动部署、扩展和操作应用程序容器。
* [vCenter Server 联网](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) - 此指南重点关注 vCenter Server、{{site.data.keyword.icpfull_notm}} 和 {{site.data.keyword.containerlong_notm}} 内使用的网络技术，例如 NSX-V、NSX-T 和 Calico。
* [VMware 和 Skate Advisor 概念车](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro) - 此参考体系结构是一种“概念车”，即用于重点说明并显示解决实际问题的技术的机制。我们希望以实际方式演示 Watson AI 与机器学习之间的互动。通过滑板文化，我们以独特的方式展示云服务。“概念车”的实现是对名为 Skate Advisor 的 Acme Skateboards 应用程序的扩展。Skate Advisor 是一种工具，支持用户与 Watson 驱动的引擎进行滑板技巧对话。
* [VMware：Stock Trader 现代化之旅](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - 我们的参考用例描述了一个经典的 WebSphere Application Server 应用程序，该应用程序使用 {{site.data.keyword.icpfull_notm}}、IBM Middleware 内容、{{site.data.keyword.containerlong_notm}} 和 vCenter Server 进行现代化。我们虽然同在一个云旅程中，但处于该旅程的不同阶段。通过应用程序架构设计师 Jane 和云基础架构设计师 Todd 实施的递增步骤，我们将对名为 Stock Trader 的现有应用程序进行现代化。其中所示的示例可帮助您完成旅程中的每个步骤，每个步骤无论大小都将为您的业务实现价值。我们专注于以下四个主题：应用程序、DevOps、集成和管理。所有主题协同工作，一起帮助您实现目标。如果只将一个主题现代化而忽略其他主题，可能会导致各种问题。

## 相关链接
{: #vcsicp-intro-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
