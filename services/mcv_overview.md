---

copyright:

  years:  2019, 2020

lastupdated: "2020-09-28"

keywords: VMware Mission Critical, request Mission Critical, tech specs Mission Critical, Mission Critical Workloads

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}

# IBM Cloud for VMware Mission Critical Workloads overview
{: #mcv_overview}

{{site.data.keyword.cloud}} for VMware® Mission Critical Workloads delivers a multizone cloud architecture to help enterprises prevent downtime for cloud applications and to automate failovers within a cloud region.

You can deploy VMware’s stretched vSAN clusters in an automated and self-managed infrastructure that gives you the flexibility to control and manage all aspects of your solution set. This option is available in on-demand ordering within the current vCenter Server workflow.

In addition, you can deploy a fully managed solution that is delivered by IBM Services. {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads delivers greater availability, resiliency, and support than many enterprises currently maintain on premises. This option is available as a coordinated engagement with IBM Services teams.

The fully managed capability provides near-continuous availability of virtual machines up to an aggregate 99.99 percent SLA, without the need for modification. This design consists of a full stack of VMware software-defined virtualization technology and associated tools to enable the consumption of services. The stack includes performance and capacity management (vRealize Suite), Active Directory, resiliency, integration with IBM Netcool and IBM Bluecare, and integration with the IBM Services Platform with Watson.

Mission critical applications are traditional applications that require near continuous availability. These applications are essential to the survival of the business and cannot be impacted. By using this capability, you can deploy in {{site.data.keyword.cloud_notm}} a more robust high availability solution than you can implement in a traditional data center.

## Technical specifications for IBM Cloud for VMware Mission Critical Workloads
{: #mcv_overview-specs}

The {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads architecture is an end to end reference architecture that provides automated failover for customer workloads. It uses an {{site.data.keyword.cloud_notm}} [multizone region](#x9774820){: term} with an IBM-managed service that covers the following components:

* Compute architecture (VMware vSphere®)
* Network architecture (NSX-T)
* Storage architecture (VMware vSAN)
* Integration with IBM Services Platform with Watson to enable the consumption of services
* Tools for monitoring, troubleshooting, performance, and capacity management, such as:
  * vRealize Suite pattern (Operations, Log Insight and Network Insight)
  * Active Directory pattern
  * Integration with IBM Netcool and IBM Bluecare for auto-ticketing, alerting, and event enrichment
  * Resiliency patterns (backup and recovery)

{{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads is available in the following regions:
* America - US South (Dallas) and US East (Washington, DC)
* Europe - Frankfurt and London
* Asia-Pacific - Sydney, Tokyo, and Osaka

### Base infrastructure architecture specifications
{: #mcv_overview-base-specs}

The base infrastructure has the following specifications:
* Each site has its own dedicated edge and management cluster.
* The resource cluster is a vSphere + vSAN stretched cluster.
* The witness site contains two ESXi hosts that provide quorum for both vSAN and vCenter.
* Single vCenter and NSX Manager architecture.
* vCenter Server Appliance with embedded Platform Services Controller (PSC) that uses vCenter High Availability (HA) over an L3 network architecture.
* NSX Manager recovery is using a Hot Standby method that syncs up backup files.

### Tools and technology architecture specifications
{: #mcv_overview-tooling-specs}

The tools and technology architecture has the following specifications:
* vRealize Operations, vRealize Log Insight, and vRealize Network Insight to provide operations and management capabilities specific to the VMware products that are used, for example NSX, vSAN, and vSphere
* IBM Software Defined Environment Automation Tool Health Check for validating deployments against best practices and security policies
* Optional Disaster Recovery (DR) to an out of Region {{site.data.keyword.cloud_notm}} site
* FortiGate Security Appliance or similar to secure any internet access and to facilitate active-active network integration with the on-premises network

### vSphere + vSAN stretched cluster architecture specifications
{: #mcv_overview-stretched-cluster-specs}

The vSphere + vSAN stretched cluster architecture has the following specifications:
* The cluster provides storage and compute capabilities, which span two sites for enhanced availability.
* Write requests from virtual machines (VMs) are synchronously written to both sites, which incur site to site network latency.
* Read requests from VMs are fulfilled locally to the physical location of where the VM is located, thus avoiding extra latency.
* The witness site and witness host act as the split brain or quorum.
* vSAN Native Encryption (for at rest encryption) can be used in combination with this architecture.

### Network architecture specifications
{: #mcv_overview-network-specs}

The network architecture has the following specifications:
* Edge/DLR/VXLANs in combination with BGP metric-based routing to facilitate an active-active site design with automated failover.
* Each site has the concept of their own set of Edges, DLRs, and VXLANs.
* Under normal circumstances, any VMs connected to DLR-A, for example VM-A, are in {{site.data.keyword.cloud_notm}} availability zone #1 and traffic is both ingress and egress locally.
* During a vMotion activity for VM-A, traffic still ingresses and egresses through the {{site.data.keyword.cloud_notm}} availability zone #1.
* During a site or edge failure, traffic routes out of the remaining available site.

## Related links
{: #mcv_overview-related}

* [Ordering a stretched cluster across multizone region](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_ordering)
* [Requesting managed IBM Cloud for VMware Mission Critical Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_ordering-managed)
* [Managed VMware services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_imi)
* [Managed Disaster Recovery services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_zerto_services)
