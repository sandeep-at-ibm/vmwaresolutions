---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# vCenter Server 联网简介

本文档展示了 {{site.data.keyword.cloud}} 的应用程序现代化之旅，侧重于支持将集成的多个云用于应用程序现代化的以下平台中的网络方面：

- **VMware vCenter Server on IBM Cloud** - {{site.data.keyword.vmwaresolutions_short}} 中的一个产品，是在 {{site.data.keyword.cloud_notm}} 上自动供应的基于 VMware 的平台。
- **IBM Cloud Private** - 一种用于开发和管理容器化应用程序的应用程序平台，这些应用程序部署到虚拟化的基础架构平台（例如 VCS）或内部部署 vSphere 环境。
- **IBM Kubernetes Service** - {{site.data.keyword.cloud_notm}} 上的受管服务，使用 Kubernetes 作为编排引擎，在单租户集群中自动部署、扩展和操作应用程序容器。

应用程序现代化的最大困难是迁移、联网和安全性。VCS、VMware Hybrid Cloud Extension (HCX)、VMware NSX、IKS 和 ICP 可帮助应对其中一些困难。以下网络体系结构描述了一种方法，该方法以 Acme Skateboards 为例，说明如何连接分布在云和内部部署环境中的组件。

[NSX-T 预览](vcsnsxt-techpreview.html)是一种技术预览，用于描述在未来的参考体系结构中使用 VMware NSX Transformers (NSX-T)。NSX-T 旨在解决具有异构端点和技术堆栈的应用程序框架和体系结构。除了 vSphere 外，这些环境还可以包含其他系统管理程序、KVM、容器和裸机。NSX-T 支持 IT 和开发团队选择最适合其应用程序的技术。除了联网团队外，NSX-T 还旨在供开发组织用于管理、操作和使用。

## IBM Cloud 上的应用程序现代化

应用程序现代化这一术语描述的是将现有应用程序转变为使用云上新的开发和交付方法的过程。如今，客户寻求的是创新、高效的方法，以帮助他们根据业务和应用程序的复杂性进行这一转变。

业务压力要求加快产品上市速度。您的现有产业不仅包括应用程序，还包括数据、流程、业务逻辑和用户界面，所有这些都需要调整以随时适应新的业务需求。

应用程序现代化的优点如下：

- 提高开发者工作效率
- 提高运营效率
- 降低构建新功能的成本
- 在短时间内交付扩展容量

据 IBM 所知，70% 的私有云是在应用程序环境现代化需求的推动下采用的，然而大多数组织是利用分阶段方法来逐渐实现应用程序现代化，这使得混合云和多云环境成为必要，其中：

- 通常在大型机或 UNIX 系统上运行的复杂和单一庞大的旧应用程序仍为内部部署。
- 用于记录系统 (SoR) 的 x86 环境、安全敏感的应用程序或受监管的工作负载会被放置在虚拟化基础架构或私有云上。
- SAP 或高性能计算等应用程序会消耗裸机资源。
- 可移至公共云的安全敏感的工作负载和一些受监管工作负载将移至专用环境。
- Web、移动、IoT、AI 或视频等全接触系统 (SoE) 将移至公共云。

例如，通用模式是将前端 SoE 应用程序部署为容器，并将数据库和旧中间件部署在私有云的 VM 上。

由于您的 IT 基础架构和业务需求是独一无二的，因此您需要一种现代化的方法，以加快业务价值实现，尽可能缩短交付时间，降低风险并保护现有投资。IBM 提供的正是这种应用程序现代化方法，您可对该方法加以定制来满足您的独特业务和技术需求。

本文档从不同角度展示了 {{site.data.keyword.cloud_notm}} 应用程序现代化之旅中使用的技术：

* [vCenter Server 和 {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - 此指南是部署以下平台的参考体系结构：
   - **VMware vCenter Server on IBM Cloud** - {{site.data.keyword.vmwaresolutions_short}} 中的一个产品，是在 {{site.data.keyword.cloud_notm}} 上自动供应的基于 VMware 的平台。
   - **IBM Cloud Private** - ICP 是用于开发和管理容器化应用程序的应用程序平台。这是一个集成环境，包括容器编排器 Kubernetes 以及专用映像存储库、管理控制台、监视框架和图形用户界面，该界面提供了一个集中位置来部署、管理、监视和扩展应用程序。
   - **IBM Cloud Automation Manager** - CAM 是一种企业就绪型基础架构即代码平台，它提供了一个窗格，通过仅使用存储库中存储和进行版本控制的模板，供应基于 VM 的工作负载以及基于 Kubernetes 的工作负载。
* [vCenter Server 和 IBM Kubernetes Service](../vcsiks/vcsiks-intro.html) - 此指南是部署以下平台的参考体系结构：
   - **VMware vCenter Server on IBM Cloud** - {{site.data.keyword.vmwaresolutions_short}} 中的一个产品，是在 {{site.data.keyword.cloud_notm}} 上自动供应的基于 VMware 的平台。
   - **IBM Cloud Kubernetes Service** - {{site.data.keyword.cloud_notm}} 上的受管服务，使用 Kubernetes 作为编排引擎，在单租户集群中自动部署、扩展和操作应用程序容器。
* _vCenter Server 联网_ - 当前指南重点关注用于 VCS、ICP 和 IKS 之间集成的网络技术（例如 NSX-V 和 Calico）以及 NSX-T 的技术预览。
* [VMware 和 Skate Advisor 概念车](../vcscar/vcscar-intro.html) - 此参考体系结构是一种“概念车”，即，用于重点说明并显示解决实际问题的技术的机制。我们希望以实际方式演示 Watson AI 与机器学习之间的互动。首先，通过滑板文化，我们以独特的方式展示云服务。“概念车”的实现是对名为 Skate Advisor 的 Acme Skateboards 应用程序的扩展。Skate Advisor 是一种工具，支持用户与 Watson 驱动的引擎进行滑板技巧对话。
* [VMware：Stock Trader 现代化之旅](../vcscontent/vcscontent-modjourney.html) - 我们的参考用例描述了一个经典的 WebSphere Application Server 应用程序，该应用程序在使用 {{site.data.keyword.cloud_notm}} Private、IBM Middleware 内容、{{site.data.keyword.cloud_notm}} Kubernetes Service 和 vCenter Server on {{site.data.keyword.cloud_notm}} 进行现代化。我们虽然同在一个云旅程中，但处于该旅程的不同阶段。通过应用程序架构设计师 Jane 和云基础架构设计师 Todd 实施的递增步骤，我们将对名为 Stock Trader 的现有应用程序进行现代化。其中所示的示例可帮助您完成旅程中的每个步骤，每个步骤无论大小都将为您的业务实现价值。我们专注于以下四个主题：应用程序、DevOps、集成和管理。所有主题协同工作一起帮助您实现目标。事实上，如果只对一个主题实行现代化而忽略其他可能会导致问题。

### 相关链接

* [VCS Hybridity Bundle 概述](../vcs/vcs-hybridity-intro.html)
