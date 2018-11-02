---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# VMware and Skate Advisor Concept Car introduction

This Reference Architecture is a “concept car”, that is, a mechanism to
highlight and show technologies solving real world problems. The
“concept car” is exactly that and in this it in no way represents a
readily available service today. This reference architecture also:

-   Provides common language for the various stakeholders.
-   Provides consistency of technology implementation to solve problems.
-   Supports the validation of solutions against a proven reference
architecture.
-   Encourage adherence to common standards,
specifications, and patterns.

## About the ACME Skate Advisor

We wanted to demonstrate an interaction between Watson artificial
intelligence and machine learning in a real way and through it explore
deeper the culture of skateboarding. Through this we wanted to
demonstrate the available services and cloud infrastructure in a unique
way, demonstrating the technical capability and advancements in this
area. The implementation of the “concept car” is an extension to the
demonstrative Acme Skateboard application called Skate Advisor. Skate
Advisor is a tool, which allows users to have skateboarding trick
conversations with a Watson driven engine. A sample conversation is as
follows:

-   “Watson, show me combinations of the trick Casper”
-   “Watson, show me common locations to perform a trick”
-   “Watson, show me a video of the trick Casper”

Acme Skate Advisor takes advantage of the Watson Discovery Service to
ingest articles, videos, blogs, and other Internet-based content to
create a learned database of tricks, which can be queried by the
application.

The Skate Advisor application is also implemented on the application
modernization platform, which provides container-based services through
ICP hosted on {{site.data.keyword.cloud}} for VMware Services platform.

The Acme Skate Advisor application takes advantage of both the Watson
platform and the application modernization platform.

## Use cases

### Application modernization demonstration

Demonstrate an application that has been deployed to the application
modernization platform, which includes ICP, CAM and NSX components
deployed on the {{site.data.keyword.cloud_notm}} for VMware Services vCenter Server (VCS)
offering.

### Watson speech recognition With Watson Assistant

The Acme Skate Advisor communicates with users via a speech-to-text and
text-to-speech service that is provided with the Watson platform.

### Watson Discovery Service usage and training

The Acme Skate Advisor utilizes the Watson Discovery Services to keep
track of a database of Tricks for which a classification language has
been applied and the tricks discovered from online services.

### Watson services utilized

The following Watson Services were utilized to create the Acme Skate
Advisor:
-   Watson Text to Speech.
-   Watson Speech to Text.
-   Watson Advisor.
-   Watson Discovery Service.
-   Watson Knowledge Studio.

## Application modernization on IBM Cloud

Application modernization is a term describing the process of
transitioning existing applications to leverage new development and
delivery approaches on the cloud. Customers today are seeking
innovative, efficient approaches that help them make this transition
based on business and application complexity.

Business pressures demand faster time to market. Your existing estate
includes not only applications, but data, processes, business logic, and
user interfaces, all of which need to adapt to keep up with new business
demands.

The benefits of application modernization include the following:

- Improves developer productivity
- Increases operational efficiency
- Reduces cost to build new capabilities
- Expands capacity that is delivered in a short time

IBM understands that 70% of private cloud adoption is being driven by
the need to modernize application environments, however, most
organizations are approaching application modernization in a staged
approach, which necessitates a hybrid and multi-cloud landscape, where:

- Complex and monolithic legacy applications that typically run on
mainframes or UNIX systems remain on-premises.
- x86 environments used for Systems of Record (SoR), or applications
that are security sensitive or regulated workloads are placed on
virtualized infrastructure or a private cloud.
- Applications such as SAP or high-performance computing consume bare
metal resources.
- Security sensitive and some regulated workloads, which can move to the
public cloud are moving to dedicated environments.
- Systems of Engagement (SoE) such as web, mobile, IoT, AI, or Video are
moving to public clouds.

For example, a common pattern is to have front end SoE applications that are deployed as containers with databases and legacy middleware that is deployed on
VMs on a private cloud.

Because your IT infrastructure and business needs are unique, you need
an approach to modernization that accelerates business value, minimizes
delivery time, reduces your risks, and preserves your existing
investments. IBM provides just such an approach to application
modernization that is customizable to address your unique business and
technology needs.

This document is one of five documents that provide different views on the technologies that are used in the application modernization journey to {{site.data.keyword.cloud_notm}}:

* [vCenter Server and {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - This guide is a reference architecture for deploying the following platforms:
   - **VMware vCenter Server on IBM Cloud** - VCS is an offering from {{site.data.keyword.vmwaresolutions_short}} that is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Private** – ICP is an application platform for developing and managing containerized applications. It is an integrated environment that includes the container orchestrator Kubernetes, as well as a private image repository, a management console, monitoring frameworks and a graphical user interface, which provides a centralized location from where you can deploy, manage, monitor, and scale your applications.
   - **IBM Cloud Automation Manager** – CAM is an enterprise-ready infrastructure as code platform that provides a single pane of glass to provision VM-based workloads alongside Kubernetes based workloads by simply using templates that are stored and versioned in a repository.

* [vCenter Server and IBM Kubernetes service](../vcsiks/vcsiks-intro.html) - This guide is a reference architecture for deploying the following platforms:
   - **VMware vCenter Server on IBM Cloud** - VCS is an offering from {{site.data.keyword.vmwaresolutions_short}} that is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Kubernetes Service** – IKS is a managed service on {{site.data.keyword.cloud_notm}} that leverages Kubernetes as the orchestration engine for automating deployment, scaling, and operations of application containers across a single-tenant cluster.

* [vCenter Server networking](../vcsnsxt/vcsnxt-intro.html) - This guide focuses on the network technologies that are used for integration between VCS, ICP, and IKS such as NSX-V and Calico along with a technology preview of NSX-T.

* _VMware and Skate Advisor Concept Car guide_ - This reference architecture is a “concept car”, that is, a mechanism to highlight and show technologies solving real world problems. We wanted to demonstrate an interaction between Watson AI and machine learning in a real way. Above all, through the culture of skateboarding, we demonstrate cloud services in a unique way. The implementation of the “concept car” is an extension to the Acme Skateboard application called Skate Advisor. Skate Advisor is a tool, which allows users to have skateboarding trick conversations with a Watson driven engine.

* [VMware: The modernization journey of Stock Trader](../vcscontent/vcscontent-intro.html) - Our reference use case describes a classic WebSphere Application Server application being modernized using {{site.data.keyword.cloud_notm}} Private, IBM Middleware content, {{site.data.keyword.cloud_notm}} Kubernetes Service, and vCenter Server on {{site.data.keyword.cloud_notm}}. We are all on a cloud journey, and we are all at different points on that journey. Through incremental steps by the application architect, Jane, and the cloud infrastructure architect, Todd, we modernize an existing application called Stock Trader. It shows examples that help you take each step in your journey, and the value realized to your business, regardless of how large or small each step is. We focus on four themes: applications, DevOps, integration, and management. Each work together to help you achieve your goals, and in fact, modernizing one without the others results in problems all around.

### Related links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
