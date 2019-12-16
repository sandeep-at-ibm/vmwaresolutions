---

copyright:

  years:  2019

lastupdated: "2019-12-12"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud for VMware Mission Critical Workloads architecture overview
{: #mcv-archi-overview}

The Joint Innovation Lab (JIL) project is a collaboration between {{site.data.keyword.IBM}} and VMware to develop and promote new offerings, functionality, and capabilities for the long-term growth of the VMware platform within the IBM ecosystem of products and services.

The {{site.data.keyword.vmwaresolutions_short}} team is chartered with building automated platform deployments for VMware infrastructures on {{site.data.keyword.cloud_notm}}. This JIL project for {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads creates automation around components and functions of the Mission Critical Workloads offering.

At a high level, the Mission Critical Workloads architecture is a fully managed solution relying on numerous VMware and {{site.data.keyword.cloud_notm}} components in a high availability infrastructure deployment. The solution set is capable of offering customers an aggregate SLA of up to 99.99% availability at the virtual machine level.
As part of the {{site.data.keyword.vmwaresolutions_short}} portfolio, the automation of the Mission Critical Workloads offering is designed to support the Mission Critical Workloads Reference Architecture as described and deployed by IBM Global Technical Services (GTS). This project and document supplement the Mission Critical Workloads reference architecture and does not replace it.

The Mission Critical Workloads offering is based on the fully automated provisioning of a VMware SDDC comprised of:

* Multiple clusters with redundant vSphere infrastructure spread across three {{site.data.keyword.CloudDataCents_notm}}. Because the design relies on vSAN stretched clusters and extremely low-latency, deployment is restricted to {{site.data.keyword.cloud_notm}} Multi-Zone-Region (MZR) Data Centers.
* vCenter HA including integrated Platform Services Controllers (PSCs).
* vSAN stretched cluster support for customer workloads.
* NSX-V with a pre–configured Management Edge.
* High availability of storage and compute resources allowing for complete loss of one of the three {{site.data.keyword.CloudDataCents_notm}} without disruption to customer workloads.
* {{site.data.keyword.vmwaresolutions_short}} automation to add and remove workload capacity.

## Automation
{: #mcv-archi-overview-auto}

The most significant part of the {{site.data.keyword.vmwaresolutions_short}} MCV offering is the automated deployment of the instance.

The only action you take is selecting the configuration of the Mission Critical Workloads instance, all other operations are provided by the automation.

Automation refers to ordering and setup of the instance. Automation does not include ongoing operation.
{:note}

The automation begins with fully ordering of infrastructure, networking components, software licenses supplied by IBM (not including Bring Your Own License), and add-on services.

After the ordered infrastructure is provisioned in the {{site.data.keyword.CloudDataCents_notm}}, the automation flow begins.

The following steps outline the process:

1. Access the {{site.data.keyword.cloud_notm}} ordering portal.
2. Select the MZR and specify the desired configuration of the Mission Critical Workloads instance.
3. Review the price estimate and terms of service, then select to provision the instance.

The {{site.data.keyword.vmwaresolutions_short}} automation then completes the following:

1. Orders {{site.data.keyword.baremetal_short}}, {{site.data.keyword.cloud_notm}} networking components (such as VLANs and subnets), storage, software licenses, and support systems.
2. Deploys vCenter.
3. Deploys vSAN and NSX.
4. Configures vSAN stretched clusters and vCenter HA according to the chosen configuration.
5. Registers the Mission Critical Workloads instance in your {{site.data.keyword.vmwaresolutions_short}} portal for ongoing Day 2 operations.

## Consumability
{: #mcv-archi-overview-consume}

Mission Critical Workloads are offered in the standard {{site.data.keyword.vmwaresolutions_short}} ordering flow, similar to the standard VCenter Server offering. A new {{site.data.keyword.cloud_notm}} user experience is available to support the Mission Critical Workloads order flow due to the overall complexity of the process.

## Ordering and management
{: #mcv-archi-overview-order}

Mission Critical Workloads instances are intended to be primarily ordered and managed by IBM GTS or by specific customer personnel as part of a GTS managed Services Engagement.

Support is provided by GTS and the {{site.data.keyword.vmwaresolutions_short}} Devops team.

Initial provision and configuration are provided by {{site.data.keyword.vmwaresolutions_short}} automation, along with the ability to scale-up and scale-down capacity.

Day 2 operation and management activities are not part of the automation process and are the responsibility of GTS or customer personnel. Day 2 operation and management activities include:

* Monitoring
* Management and operation
* Disaster recovery
* Failure operations
* Manual recovery
* Backup and restore
* Network failure recovery

Although this offering is intended to be ordered and used in conjunction with a GTS support contract, it can be ordered by anyone by using the {{site.data.keyword.vmwaresolutions_short}} portal.

## Related links
{: #mcv-archi-overview-related}

* [{{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads architecture](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv-archi-design)
* [Bill of Materials](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv-archi-bom)
* [Component and feature details](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv-archi-comp)
