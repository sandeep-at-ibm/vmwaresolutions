---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-09"

subcollection: vmware-solutions


---

# 体系结构概述
{: #vcsicp-arch-overview}

{{site.data.keyword.vmwaresolutions_full}} 产品提供了自动化功能，可将 VMware 技术组件部署到全球范围的 {{site.data.keyword.CloudDataCents_notm}} 中。该体系结构包含一个云区域，并支持扩展到其他地理位置中的更多云区域或扩展到同一数据中心内的其他 {{site.data.keyword.cloud_notm}} pod 中。

您可以将 {{site.data.keyword.cloud_notm}} Private 和 Cloud Automation Manager (CAM) 产品手动部署到内部部署虚拟化平台中，从而支持通过内部部署位置进行云管理。或者，{{site.data.keyword.icpfull_notm}} 和 CAM 可借助自动化功能，作为服务扩展提供给现有或新的 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 部署，从而支持通过 {{site.data.keyword.cloud_notm}} 进行云管理。

{{site.data.keyword.cloud_notm}} Private 是一种用于开发和管理内部部署容器化应用程序的应用程序平台。{{site.data.keyword.cloud_notm}} Private 是用于管理容器的集成环境，包括容器编排器 Kubernetes、专用映像存储库、管理控制台和监视框架。

IBM Multi-Cluster Manager (MCM) 在各种云和集群中提供用户可视性、以应用程序为中心的管理（策略、部署、运行状况和操作）以及基于策略的合规性。通过 MCM，您可以控制 Kubernetes 集群。MCM 可帮助确保集群是安全的、在高效运行，并提供在 {{site.data.keyword.cloud_notm}} Private 上运行的服务管理平台，支持开发者和管理员满足业务需求。

使用 Cloud Automation Manager Service Composer 可以在 {{site.data.keyword.cloud_notm}} Private 目录中显示 Hybrid Cloud Services。

## IBM Cloud 端云管理平台
{: #vcsicp-arch-overview-ibm-cloud-side-platform}

下图是在 {{site.data.keyword.cloud_notm}} 基础架构中部署的 {{site.data.keyword.icpfull_notm}} 和 CAM 的示例，连接到内部部署 vCenter 和 {{site.data.keyword.cloud_notm}} 上部署的 {{site.data.keyword.containerlong_notm}}。用户可以将内部部署虚拟机 (VM) 和 VM 部署到 vCenter Server 实例，并将容器部署到 {{site.data.keyword.icpfull_notm}} 和 {{site.data.keyword.containerlong_notm}} 集群。

![在云上 - 云管理](../../images/vcsicp-oncloud-cloudmgt.svg "在云上 - 云管理")

在该图中，CAM 在逻辑上创建与 vCenter、云提供者、{{site.data.keyword.icpfull_notm}} 和 {{site.data.keyword.containerlong_notm}} 环境的云连接。{{site.data.keyword.icpfull_notm}} 集群必须部署到每个数据中心云环境，其中 MCM 提供将 {{site.data.keyword.icpfull_notm}} 集群连接到单个管理视图的机制。

可以使用 NSX-V 或 NSX-T 组件来部署 {{site.data.keyword.icpfull_notm}}。通过使用 NSX-V 的 {{site.data.keyword.icpfull_notm}}，支持 {{site.data.keyword.icpfull_notm}} VM 在 VXLAN 网络上运行，并使用 Kubernetes Calico 内部联网。

通过使用 NSX-T 的 {{site.data.keyword.icpfull_notm}}，用户可以在中央 UI (NSX T Manager) 中控制和配置联网、子网和策略。请参阅 [vCenter Server 联网指南](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro)，以了解 NSX-V 和 NSX-T 之间的差异。

## 内部部署云管理平台
{: #vcsicp-arch-overview-on-premises-platform}

下图是在内部部署基础架构中部署的 {{site.data.keyword.icpfull_notm}} 和 CAM 的示例，连接到 {{site.data.keyword.cloud_notm}} 上部署的 vCenter 和 {{site.data.keyword.containerlong_notm}}。用户可以内部部署 VM 和容器，将 VM 部署到 vCenter Server 实例中，并将容器部署到 {{site.data.keyword.containerlong_notm}} 集群中。

![本地云管理](../../images/vcsicp-onprem-cloudmgt.svg "本地云管理")

strongSwan VPN 用于与部署的 {{site.data.keyword.containerlong_notm}} 容器建立连接。strongSwan VPM 可能会替换为直接链路连接。

在该图中，CAM 在逻辑上创建与 vCenter、云提供者、{{site.data.keyword.icpfull_notm}} 和 {{site.data.keyword.containerlong_notm}} 环境的云连接。{{site.data.keyword.icpfull_notm}} 集群必须部署到每个数据中心云环境，其中 MCM 提供将 {{site.data.keyword.icpfull_notm}} 集群连接到单个管理视图的机制。

## 相关链接
{: #vcsicp-arch-overview-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
