---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# 现代化之旅

此参考用例描述了一个经典的 WebSphere Application Server 应用程序如何使用 {{site.data.keyword.cloud}} Private、IBM Middleware 内容、{{site.data.keyword.containerlong_notm}} 和 vCenter Server on {{site.data.keyword.cloud_notm}} 进行现代化。

## 现代化的不仅仅是应用程序

我们虽然同在一个云旅程中，但处于该旅程的不同阶段。此用例关注的是现有应用程序 Stock Trader 如何通过应用程序架构设计师 Jane 和云基础架构设计师 Todd 计划的递增步骤来实现现代化。此用例显示的示例可帮助您完成旅程中的每个步骤，每个步骤无论大小都将为您的业务实现价值。

在此旅程中，我们关注最多的是对 Stock Trader 应用程序进行现代化。要将业务完全现代化为云本机业务，必须讨论应用程序、DevOps、集成和管理主题。所有主题协同工作，一起帮助您实现目标。如果只将一个主题现代化而忽略其他主题，可能会导致各种问题。

## 实现现代化的原因

### 应用程序现代化

目标是获得可扩展并响应快速变化的需求的云本机应用程序。

* 您需要现代化现有应用程序，创建新的云本机应用程序，以充分体现客户的想象力。
* 您需要应用程序能够扩展、触及全球范围、根据需求进行调整、做出更改、进行增强并能迅速启动。

### DevOps 现代化

在应用程序现代化过程中，还需要对该应用程序的交付方式以及整个交付管道进行现代化，使得开发者创建的新云本机文化可以缩放到应用程序的交付方式中。

* 在应用程序现代化过程中，您还需要对开发和运作（以及安全性）文化进行现代化。
* 您需要 DevOps 团队能够扩展、触及全球范围、根据需求进行调整、做出更改、进行增强并能迅速启动。

###  集成现代化

在现代化旅程中，团队需要集成现有资产、新的云服务、数据以及通过对这些数据执行的分析而获得的新洞察。

* 在此旅程中，您需要使用现有资产，以便能够扩展、触及全球范围、根据需求进行调整、做出更改、进行增强并能迅速启动。
* 您需要在此旅程的每个步骤中使用新的云服务进行扩充。
* 您需要集成数据以及通过对数据应用分析而获得的洞察。

### 管理

在应用程序现代化过程中，管理实践现代化是另一个并行的旅程。如何管理和维护现代化应用程序的工具、文化和核心行为与以前大为不同。

* 您需要使用内置的编排、日志记录和监视功能来管理微服务和容器化中间件。
* 您需要管理全球范围内各个位置的多云混合平台，以便能够扩展、触及全球范围、根据需求进行调整、做出更改、进行增强并能迅速启动。
* 您需要对如何管理多个云以及在这些云上运行的应用程序和中间件进行自动化。

## Todd 和 Jane 简介

在 Stock Trader 旅程中，我们重点关注两个人物：Todd 和 Jane。Todd 是 ACME 公司的运营负责人，负责管理基础架构、安全性、云环境以及确保在这些环境中运行的工作负载符合各种法规的策略。

Jane 是 Stock Trader 解决方案的开发负责人，现在负责对 Stock Trader 现代化，这意味着在其开发团队中致力于更改开发工具、文化和平台，从而使现有的整体 Stock Trader 解决方案现代化，成为一个运行良好云本机解决方案。

## Stock Trader 简介

Todd 和 Jane 构建了一个在 WebSphere 中运行的应用程序，名为 Stock Trader。虽然此应用程序只有基本的用户界面，但却十分可靠，投资组合经理可使用此应用程序来管理投资组合，包括买入和卖出股票以及查看内部忠诚度级别。

Stock Trader 在 WebSphere 中运行，通过几个 .war 文件进行构建，并使用在其数据中心内运行的传统 Db2 数据库，该数据中心已经可靠使用多年。由于基础架构团队、开发团队和数据团队之间有着依赖关系，因此增强此应用程序需要很长时间。

不过，虽然 Stock Trader 很不错，但公司里所有人都希望能更好用。产品经理希望将社交媒体添加到他们的忠诚度计划中。Jane 对此非常高兴，因为她可以将应用程序重构为微服务，这样他们就能够持续交付增强的功能，同时减少依赖关系。Todd 很欣赏云效率的构想，但仍需要监管以保持企业策略的合规性。

## 旅程中的各个步骤

Todd 和 Jane 根据经验得知，理想的解决方案现代化之旅应从路线图开始。虽然计划可以改变，但从长远角度考虑，并定义务实的方法来实现目标始终是不错的方法。每个步骤都必须为公司带来价值，并且这些步骤的重要程度并不至于对其客户造成费用高昂的中断。

对于 Todd 和 Jane 来说，他们在 Stock Trader 旅程中的各步骤如下：
1. 将 Stock Trader VM 提升到 {{site.data.keyword.cloud_notm}}。通过此步骤，Todd 可以减少在本地数据中心内管理他自己的硬件和 VMware 内容的需求。

2. 将 WebSphere Application Server 中的 Stock Trader 转换为容器中的 Stock Trader。此步骤可提高弹性，因为在 Kubernetes 中运行容器可提供编排功能和其他云行为。这确实需要 Todd 在其 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 环境中准备 {{site.data.keyword.cloud_notm}} Private 实例，然后与 Jane 和 Transformation Advisor 一起合作以对 Stock Trader 进行容器化。

3. 重构中间件并将中间件添加到 {{site.data.keyword.cloud_notm}} Private 中。此步骤将他们的现有中间件引入云环境，并优化云行为。这也简化了许可过程，并准备解决方案，使其完全可移植，以便在其他 Kubernetes 环境中使用。

4. 使用 Watson 和其他公共云服务进行扩充。此步骤通过引入 AI 服务以及与全球范围内的云数据中心进行通信的能力，可使 Stock Trader 体验实现以指数方式增值。

5. 通过 {{site.data.keyword.cloud_notm}} Kubernetes Service 实现真正的混合。通过此步骤，Todd 可以将仍连接到同一云区域的受管 Kubernetes 服务作为他自己的 {{site.data.keyword.cloud_notm}} Private 实例。此外，还能使 Jane 的开发团队将开发和测试集群（可以对其进行试验，同时仍访问相同的数据源）作为其核心 {{site.data.keyword.cloud_notm}} Private 集群。

6. 将 DevOps 现代化。在此旅程中，Jane 改进了她交付 Stock Trader 的方式。

7. 将管理现代化。Todd 和 Jane 致力于改进 Stock Trader 及其运行所在平台的管理方式，甚至可跨多个集群和云环境进行管理。

### 相关链接

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
