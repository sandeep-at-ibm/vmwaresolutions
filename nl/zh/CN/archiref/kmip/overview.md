---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware 概述
{: #kmip-overview}

此解决方案体系结构描述了用于保护 VMware on {{site.data.keyword.cloud_notm}} 实例的 KMIP on VMware 体系结构。许多存储加密选项可用于保护 VMware 工作负载。KMIP for VMware 与 VMware 本机 vSphere 加密和 vSAN 加密一起使用，可简化存储加密管理，并提供 {{site.data.keyword.cloud_notm}} Key Protect 客户管理的密钥的安全性和灵活性。

此解决方案被视为 {{site.data.keyword.cloud_notm}} 上的 vCenter Server 和 VMware Cloud Foundation 解决方案产品的额外组件和扩展。因此，本文档未涵盖 {{site.data.keyword.cloud_notm}} 上这些基础解决方案的现有配置。要了解有关基础解决方案体系结构的更多信息，请参阅 [VMware on {{site.data.keyword.cloud_notm}} 解决方案体系结构](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)。

## 主要优点
{: #kmip-overview-benefits}

虽然许多存储加密解决方案可用于 VMware 工作负载，但 KMIP for VMware 具有以下优点：

* 与 VMware vSAN 加密和 vSphere 加密集成，这两种加密都是在系统管理程序层实现的，而不是在存储器或虚拟机层实现。通过此方法，可以轻松管理和透明了解存储解决方案及应用程序。
* 完全受管的密钥管理服务器在许多 {{site.data.keyword.cloud_notm}} 多专区区域 (MZR) 中可用。
* 通过将 VMware 集群与 {{site.data.keyword.cloud_notm}} Key Protect 集成，为您提供了完全由客户管理的密钥，您可以随时撤销这些密钥。

## 相关链接
{: #kmip-overview-related}

* [解决方案设计](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [实现和管理](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-implementation)
