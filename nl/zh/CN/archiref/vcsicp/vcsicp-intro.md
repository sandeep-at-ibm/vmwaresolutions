---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

# vCenter Server 和 IBM Cloud Private 简介

本文档展示了 IBM Cloud 的应用程序现代化之旅，侧重于支持将集成的多个云用于应用程序现代化的云管理组件：

- **VMware vCenter Server on IBM Cloud** - VCS 是 IBM Cloud for VMware Solutions 中的一个产品，也是在 IBM Cloud 上自动供应的基于 VMware 的平台。

- **IBM Cloud Private** - ICP 是用于开发和管理容器化应用程序的应用程序平台，这些应用程序旨在部署到虚拟化的基础架构平台（例如 VMware）。

- **IBM Kubernetes Services** - IKS 是 IBM Cloud 上的一款受管服务产品，利用 Kubernetes 作为编排引擎，在单租户集群中自动部署、扩展和操作应用程序容器。

- **IBM Multi-Cluster Manager** - MCM 在各种云和集群中提供用户可视性、以应用程序为中心的管理（策略、部署、运行状况和操作）以及基于策略的合规性。通过 MCM，您可以控制 Kubernetes 集群。

- **IBM Cloud Automation Manager** - CAM 是在 ICP 上运行的多云自助服务管理平台，支持开发者和管理员满足其业务需求。

## IBM Cloud 上的应用程序现代化
应用程序现代化这一术语描述的是将现有应用程序转变为利用云上的新方法的过程。如今，客户寻求的是创新、高效的方法，以帮助他们根据业务和应用程序的复杂性进行这一转变。

业务压力要求加快产品上市速度。您的现有产业不仅包括应用程序，还包括数据、流程、业务逻辑和用户界面，所有这些都需要调整以随时适应新的业务需求。

应用程序现代化的优点如下：
- 提高开发者的工作效率。
- 提高运营效率。
- 降低构建新功能的成本。
- 在短时间内交付扩展容量。

据 IBM 所知，70% 的私有云是在应用程序环境现代化需求的推动下采用的，然而大多数组织是利用分阶段方法来逐渐实现应用程序现代化，这使得混合云和多云环境成为必要，其中：
- 通常在大型机或 UNIX 系统上运行的复杂和单一庞大的旧应用程序仍为内部部署。
- 用于记录系统 (SoR) 的 x86 环境或属于安全敏感性或受监管工作负载的应用程序被放置在虚拟化基础架构或私有云上。
- SAP 或高性能计算等应用程序会消耗裸机资源。
- 可移至公共云的安全敏感性工作负载和一些受监管工作负载将移至专用环境。
- Web、移动、IoT、AI 或视频等全接触系统 (SoE) 将移至公共云。

例如，通用模式是将前端 SOE 应用程序部署为容器，并将数据库和旧中间件部署在私有云的 VM 上。

由于您的 IT 基础架构和业务需求是独一无二的，因此您需要一种现代化的方法，以帮助加快业务价值交付，降低风险并保护现有投资。IBM 正好提供了此类方法，您可加以定制来满足与应用程序现代化相关的独特业务和技术需求。

有五个文档展示了 IBM Cloud 应用程序现代化之旅中使用的技术的不同方面，本文档是其中之一：

参考体系结构指南：VCS - ICP 和 CAM - 当前部分。

用于部署以下平台的参考体系结构：
  - **VMware vCenter Server on IBM Cloud** - IBM Cloud for VMware Solutions 中的一个产品，也是在 IBM Cloud 上自动供应的基于 VMware 的平台。
  - **IBM Cloud Private** - 一种用于开发和管理容器化应用程序的应用程序平台。这是一个集成环境，包括容器编排器 Kubernetes 以及专用映像存储库、管理控制台、监视框架和图形用户界面，该界面提供了一个集中位置来部署、管理、监视和扩展应用程序。
  - **IBM Cloud Automation Manager**- 一种企业就绪型基础架构即代码 (IaC) 平台，它提供了一个窗格，通过仅使用存储库中存储和进行版本控制的模板，供应基于 VM 的工作负载以及基于 Kubernetes 的工作负载。

[参考体系结构指南：VCS - IKS](../vcsiks/vcsiks-intro.html)

  用于部署以下平台的参考体系结构：
  - **VMware vCenter Server on IBM Cloud** - IBM Cloud for VMware Solutions 中的一个产品，也是在 IBM Cloud 上自动供应的基于 VMware 的平台。
  - **IBM Kubernetes Service** - IBM Cloud 上的受管服务，利用 Kubernetes 作为编排引擎，在单租户集群中自动部署、扩展和操作应用程序容器。

[参考体系结构指南：VCS - 联网](../vcsnsxt/vcsnsxt-intro.html)

本文档重点关注 VCS、ICP 和 IKS 内使用的网络技术，例如 NSX-V、NSX-T 和 Calico。

[参考体系结构指南：Watson 和 Sk8boarding 概念车](../vcscar/vcscar-intro.html)

本文档使用“概念车”方法来演示 Watson AI 与机器学习之间的交互。

本文档重点介绍了以下技术：
  - **Pepper** - 一个界面，包含与云环境集成以执行应用程序和搜索操作的功能。
  - **VMware vCenter Server on IBM Cloud** - 用于托管应用程序的元素，例如数据库工作负载。
  - **IBM Cloud Kubernetes Service** - 用于托管应用程序的容器化元素。
  - **IBM Cloud Private** - 用于提供平台和服务级别编排，包括在各个 VM 和容器平台上托管和扩展应用程序的功能。此组件还支持启用面向该平台的 Watson 开发者服务，从而允许访问 AI 功能。

[参考体系结构指南：VCS - 内容](../vcscontent/vcscontent-intro.html)

本文档重点介绍 IBM Cloud Automation Manager 中可用的以下内容类型：
- 内部目录内容，例如“预装”的 Helm 图表、Terraform 模板和 Chef 诀窍。
- 服务内容，例如区块链和 Watson 服务。

### 相关链接

  * [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
