---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# VMware 和 Skate Advisor 概念车简介
{: #vcscar-intro}

以下参考体系结构是一种“概念车”，即用于重点说明并显示解决实际问题的技术的机制。“概念车”绝不代表如今现成可用的服务。

该参考体系结构还提供了以下信息：

-   为各个项目干系人提供通用语言。
-   提供技术实施的一致性以解决问题。
-   支持根据成熟的参考体系结构来验证解决方案。
-   鼓励遵循通用标准、规范和模式。

## 关于 ACME Skate Advisor
{: #vcscar-intro-about}

我们希望以实际方式演示 Watson 人工智能与机器学习之间的互动，并借此更深入地探索滑板文化。我们将以独特的方式说明可用的服务和云基础架构，以展示该领域的技术能力和进步成果。“概念车”的实现是对名为 Skate Advisor 的演示性 Acme Skateboards 应用程序的扩展。Skate Advisor 是一种工具，支持用户与 Watson 驱动的引擎进行滑板技巧对话。下面引用的内容是一个样本对话：

-   “Watson，显示‘卡斯坡’技巧组合”
-   “Watson，显示练习技巧的常见地点”
-   “Watson，显示‘卡斯坡’技巧的视频”

Acme Skate Advisor 利用 Watson Discovery 服务来摄入文章、视频、博客和其他基于因特网的内容，从而创建一个广博的技巧数据库，供该应用程序查询。

Skate Advisor 应用程序还在应用程序现代化平台上实现，该平台通过 {{site.data.keyword.cloud_notm}} for VMware Services 平台上托管的 {{site.data.keyword.icpfull_notm}} 提供基于容器的服务。

Acme Skate Advisor 应用程序同时利用 Watson 平台和应用程序现代化平台。

## 用例
{: #vcscar-intro-use-cases}

### 应用程序现代化演示
{: #vcscar-intro-app-mod-demo}

演示已部署到应用程序现代化平台的应用程序。该平台包含在 {{site.data.keyword.cloud_notm}} 上部署的用于 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 产品的 {{site.data.keyword.icpfull_notm}}、CAM 和 NSX 组件。

### 使用 Watson Assistant 实现 Watson 语音识别
{: #vcscar-intro-speech}

Acme Skate Advisor 通过 Watson 平台随附的语音转文字和文字的语音合成服务与用户通信。

### Watson Discovery 服务的使用和训练
{: #vcscar-intro-watson-disc}

Acme Skate Advisor 使用 Watson Discovery服务跟踪应用了分类语言的技巧数据库以及通过联机服务发现的技巧。

### Watson 服务的使用
{: #vcscar-intro-watson-services}

以下 Watson 服务用于创建 Acme Skate Advisor：
-   Watson Text to Speech。
-   Watson Speech to Text。
-   Watson Advisor。
-   Watson Discovery 服务。
-   Watson Knowledge Studio。

## IBM Cloud 上的应用程序现代化
{: #vcscar-intro-app-mod}

应用程序现代化这一术语描述的是将现有应用程序转变为使用云上新的开发和交付方法的过程。如今，客户寻求的是创新、高效的方法，以帮助他们根据业务和应用程序的复杂性进行这一转变。

业务压力要求加快产品上市速度。您的现有产业不仅包括应用程序，还包括数据、流程、业务逻辑和用户界面，所有这些都需要调整以随时适应新的业务需求。

以下列表描述了应用程序现代化的优点：
- 提高开发者工作效率
- 提高运营效率
- 降低构建新功能的成本
- 在短时间内交付扩展容量

据 IBM 所知，70% 的私有云是在应用程序环境现代化需求的推动下采用的。然而，大多数组织是分阶段逐渐实现应用程序现代化，这就需要一个混合及多云的环境，其中：

- 通常在大型机或 UNIX 系统上运行的复杂和单一庞大的遗留应用程序仍为内部部署。
- 用于记录系统 (SoR) 的 x86 环境、安全敏感的应用程序以及受监管的工作负载会被放置在虚拟化基础架构或私有云上。
- SAP 或高性能计算等应用程序会使用裸机资源。
- 可移至公共云的安全敏感的工作负载和一些受监管的工作负载将移至专用环境。
- Web、移动、IoT、AI 或视频等全接触系统 (SoE) 将移至公共云。

例如，通用模式是将前端 SoE 应用程序部署为容器，并将数据库和遗留中间件部署在私有云的 VM 上。

由于 IT 基础架构和业务需求是独一无二的，因此现代化的方法必须提供以下优先级：

* 加速实现业务价值
* 尽可能缩短交付时间
* 降低风险
* 保护现有投资。

IBM 提供的正是这种应用程序现代化方法，您可对该方法加以定制来满足您的独特业务和技术需求。

以下文档从不同角度展示了 {{site.data.keyword.cloud_notm}} 应用程序现代化之旅中使用的技术：

* [vCenter Server 和 {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro) - 部署以下平台的参考体系结构。
   - **VMware vCenter Server on IBM Cloud** - vCenter Server 是 {{site.data.keyword.vmwaresolutions_short}} 中的一个产品，这是在 {{site.data.keyword.cloud_notm}} 上自动供应的基于 VMware 的平台。
   - **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} 是一种用于开发和管理容器化应用程序的应用程序平台。{{site.data.keyword.icpfull_notm}} 是一个集成环境，包括容器编排器 Kubernetes、专用映像存储库、管理控制台、监视框架和图形用户界面。该用户界面提供了一个集中位置来部署、管理、监视和扩展应用程序。
   - **IBM Cloud Automation Manager** - CAM 是一种企业就绪型基础架构即代码平台，它提供了一个窗格，通过使用存储库中存储和进行版本控制的模板，供应基于 VM 的工作负载以及基于 Kubernetes 的工作负载。
* [vCenter Server 和 {{site.data.keyword.containerlong_notm}} 服务](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - 部署以下平台的参考体系结构。
   - **VMware vCenter Server on IBM Cloud** - vCenter Server 是 {{site.data.keyword.vmwaresolutions_short}} 中的一个产品，这是在 {{site.data.keyword.cloud_notm}} 上自动供应的基于 VMware 的平台。
   - **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} 是 {{site.data.keyword.cloud_notm}} 上的一种受管服务，使用 Kubernetes 作为编排引擎，在单租户集群中自动部署、扩展和操作应用程序容器。
* [vCenter Server 联网](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) - 重点关注用于 vCenter Server、{{site.data.keyword.icpfull_notm}} 和 {{site.data.keyword.containerlong_notm}} 之间集成的网络技术（例如 NSX-V 和 Calico）以及 NSX-T 的技术预览。
* _VMware 和 Skate Advisor 概念车指南_ - 此参考体系结构是一种“概念车”，即用于重点说明并显示解决实际问题的技术的机制。我们希望以实际方式演示 Watson AI 与机器学习之间的互动。通过滑板文化，我们以独特的方式展示云服务。“概念车”的实现是对名为 Skate Advisor 的 Acme Skateboards 应用程序的扩展。Skate Advisor 是一种工具，支持用户与 Watson 驱动的引擎进行滑板技巧对话。
* [VMware：Stock Trader 现代化之旅](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - 此参考用例描述了一个经典的 WebSphere Application Server 应用程序，该应用程序使用 {{site.data.keyword.cloud_notm}} Private、IBM Middleware 内容、{{site.data.keyword.containerlong_notm}} 和 vCenter Server on {{site.data.keyword.cloud_notm}} 进行现代化。我们虽然同在一个云旅程中，但处于该旅程的不同阶段。通过应用程序架构设计师 Jane 和云基础架构设计师 Todd 实施的递增步骤，我们将对名为 Stock Trader 的现有应用程序进行现代化。查看示例可帮助您完成旅程中的每个步骤，每个步骤无论大小都将为您的业务实现价值。我们专注于以下四个主题：应用程序、DevOps、集成和管理。所有主题协同工作，一起帮助您实现目标。如果只将一个主题现代化而忽略其他主题，可能会导致各种问题。

## 相关链接
{: #vcscar-intro-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
