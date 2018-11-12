---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# vCenter Server and IBM Kubernetes service introduction

This document provides a view on the application modernization journey to {{site.data.keyword.cloud}}, focusing on the network aspects of the following platforms to allow an integrated multi-cloud to be leveraged for application modernization:

This document provides a view of the application modernization journey to {{site.data.keyword.cloud_notm}}, focusing on the cloud management components to allow an integrated multi-cloud to be leveraged for application modernization:

- **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - VCS is an offering from {{site.data.keyword.vmwaresolutions_full}} and is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
- **{{site.data.keyword.cloud_notm}} Private** - ICP is an application platform for developing and managing containerized applications, which are designed to be deployed on to virtualized infrastructure platforms, such as VMware.
- **IBM Kubernetes Services** - IKS is a managed service on {{site.data.keyword.cloud_notm}} that leverages Kubernetes as the orchestration engine for automating deployment, scaling, and operations of application containers across a single tenant cluster
- **IBM Multi-Cluster Manager** – MCM provides user visibility, application-centric management (policy, deployments, health, operations), and policy-based compliance across clouds and clusters. With MCM, you have control of your Kubernetes clusters.
- **{{site.data.keyword.cloud_notm}} Automation Manager** – CAM is a multi cloud, self-service management platform running on ICP that empowers developers and administrators to meet business demands.

## Application modernization on IBM Cloud
Application modernization is a term that describes the process of transitioning existing applications to leverage new approaches on the cloud. Customers today are seeking innovative, efficient approaches that help them make this transition based on business and application complexity.

Business pressures demand faster time to market. Your existing estate includes not only applications, but data, processes, business logic, and user interfaces, all of which need to adapt to keep up with new business demands.

The benefits of application modernization include the following:
- Improved developer productivity.
- Increased operational efficiency.
- Reduced cost to build new capabilities.
- Expanded capacity delivered in a short time.

IBM understands that 70% of private cloud adoption is being driven by the need to modernize application environments, however, most organizations are approaching application modernization in a staged approach, which necessitates a hybrid and multi cloud landscape, where:
- Complex and monolithic legacy applications that typically run on mainframes or UNIX systems remain on-premises.
- x86 environments used for systems of record (SoR), or applications that are security sensitive or regulated workloads are placed on virtualized infrastructure or a private cloud.
- Applications such as SAP or high-performance computing consume bare metal resources.
- Security sensitive and some regulated workloads, which can move to the public cloud are moving to dedicated environments.
- Systems of engagement (SoE) such as; web, mobile, IoT, AI, or Video are moving to public clouds.

For example, a common pattern is to have front end SOE applications that are deployed as containers with databases and legacy middleware that is deployed on VMs on a private cloud.

Because your IT infrastructure and business needs are unique, you need an approach to modernization that helps accelerate business value delivery, reduces your risks, and preserves your existing investments. IBM provides just such an approach that can be customized to address your unique business and technology needs related to application modernization.

This document is one of five documents that provides different views on the technologies that are used in the application modernization journey to {{site.data.keyword.cloud_notm}}:

* [vCenter Server and {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - This guide is a reference architecture for deploying the following platforms:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - an offering from {{site.data.keyword.vmwaresolutions_full}} and is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}} Private** – an application platform for developing and managing containerized applications. It is an integrated environment that includes the container orchestrator Kubernetes, as well as a private image repository, a management console, monitoring frameworks and a graphical user interface, which provides a centralized location from where you can deploy, manage, monitor, and scale your applications.
  - **{{site.data.keyword.cloud_notm}} Automation Manager** – an enterprise-ready Infrastructure as Code (IaC) platform that provides a single pane of glass to provision VM-based workloads alongside Kubernetes based workloads by simply using templates that are stored and versioned in a repository.
* [vCenter Server and {{site.data.keyword.cloud_notm}} Private](../vcsiks/vcsiks-intro.html) - This guide is a reference architecture for deploying the following platforms:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - an offering from {{site.data.keyword.vmwaresolutions_full}} and is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}} Kubernetes Service** – managed service on {{site.data.keyword.cloud_notm}} that leverages Kubernetes as the orchestration engine for automating deployment, scaling, and operations of application containers across a single-tenant cluster.
* [vCenter Server networking](../vcsnsxt/vcsnsxt-intro.html) - This guide focuses on the network technologies that are used within VCS, ICP and IKS such as NSX-V, NSX-T and Calico.
* [VMware and Skate Advisor Concept Car](../vcscar/vcscar-intro.html) - This reference architecture is a “concept car”, that is, a mechanism to highlight and show technologies solving real world problems. We wanted to demonstrate an interaction between Watson AI and machine learning in a real way. Above all, through the culture of skateboarding, we demonstrate cloud services in a unique way. The implementation of the “concept car” is an extension to the Acme Skateboard application called Skate Advisor. Skate Advisor is a tool, which allows users to have skateboarding trick conversations with a Watson driven engine.
* [VMware: The modernization journey of Stock Trader](../vcscontent/vcscontent-modjourney.html) - Our reference use case describes a classic WebSphere Application Server application being modernized using {{site.data.keyword.cloud_notm}} Private, IBM Middleware content, {{site.data.keyword.cloud_notm}} Kubernetes Service, and vCenter Server on {{site.data.keyword.cloud_notm}}. We are all on a cloud journey, and we are all at different points on that journey. Through incremental steps by the application architect, Jane, and the cloud infrastructure architect, Todd, we modernize an existing application called Stock Trader. It shows examples that help you take each step in your journey, and the value realized to your business, regardless of how large or small each step is. We focus on four themes: applications, DevOps, integration, and management. Each work together to help you achieve your goals, and in fact, modernizing one without the others results in problems all around.

### Related links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
