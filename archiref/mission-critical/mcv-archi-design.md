---

copyright:

  years:  2019, 2021

lastupdated: "2021-08-24"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:term: .term}

# VMware multizone architecture design
{: #mcv-archi-design}

## Topology
{: #mcv-archi-design-topology}

The VMware® multizone instance architecture relies on a highly available storage, compute, and networking solution in {{site.data.keyword.cloud_notm}}. In addition, a number of VMware and IBM® components are required to provide management and tooling capabilities.

## IBM Cloud multizone regions
{: #mcv-archi-design-mzr}

The multizone instance architecture depends on {{site.data.keyword.cloud_notm}} [multizone regions](#x9774820){: term} (MZRs). An MZR is an {{site.data.keyword.cloud_notm}} data center designation, which consists of triplets of geographically close sites with high bandwidth and low latency between them.

These configurations are the only site configurations for the multizone instance offering that are enforced at order time.

| Region        | {{site.data.keyword.cloud_notm}} data centers |
|:------------- |:------------- |
| NA South | Dallas 10, Dallas 12, Dallas 13 |
| NA East | Washington DC 04, Washington DC 06, Washington DC 07 |
| Europe | London 04, London 05, London 06 |
| Europe | Frankfurt 02, Frankfurt 04, Frankfurt 05 |
| Asia-Pacific | Tokyo 02, Tokyo 04, Tokyo 05 |
| Asia-Pacific | Sydney 01, Sydney 04, Sydney 05 |
{: caption="Table 1. Available MZRs in {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Distribution across multizone regions
{: #mcv-archi-design-distibution}

When you order a Multizone Instance, you select one of the three {{site.data.keyword.cloud_notm}} data centers in the MZR as the witness site. This site hosts all components that require representatives to maintain quorum for high availability. The other two {{site.data.keyword.cloud_notm}} data centers in the MZR host the management and resource components of the multizone instance. They are hosted in a cluster that is known as the consolidated cluster (consolidated management and workload components).

The designation of witness and consolidated cluster data centers in the MZR is fixed for each multizone instance. You can select any data center to use as either a witness or for management and resources. There is nothing unique about a data center that makes it suitable or preferable for either purpose.

Separate instances can also be deployed in the same or different MZR with their own independent choice of witness and management workload sites.

### Witness site
{: #mcv-archi-design-distibution-witness}

The witness site that is selected for the first cluster contains the witness component for vCenter HA, an NSX Manager, and the vSAN witness for the stretched cluster.

You select the witness site during the deployment process. The witness site can be either vSAN or NFS Endurance based. This choice cannot be modified after deployment. If the witness is vSAN based, it remains separate from and does not participate in the stretched cluster configuration that is deployed onto the management and resource sites.

It is not recommended for you to deploy your customer workloads in the witness site.
{: note}

### Consolidated Cluster sites
{: #mcv-archi-design-distibution-mgmt}

The two remaining sites in the MZR that were not selected as the witness site are assigned as the management and resource sites. Two management clusters are deployed, one into each of these sites for management components such as vCenter Server. A single stretch cluster for customer workload is deployed spanning the two sites.

The consolidated cluster is vSAN based only. Additional workload clusters can be either vSAN or NFS based.

For the consolidated cluster, the two sites are intended to serve as identical replicas of each other and are provisioned and maintained in a homogeneous configuration. The following configurations across the two sites are identical:

* Number of hosts
* Processor type
* RAM
* Disk configuration
* Network configuration
* VMware software stack

Day 2 scale-up and scale-down operations to add and remove hosts to the management and stretch clusters are automatically selected to take place simultaneously in each of the two resource sites. This automatic maintenance of consistency across the management and stretch clusters is enforced and cannot be overridden.

The following configuration with separate management and edge services clusters is an IBM Global Technology Services (GTS) Large style VMware multizone configuration. The edge services clusters must be deployed separately as day 2 operations.

![A typical large VMware multizone instance deployment](../../images/mcv-lg-config.svg "A typical large VMware multizone instance deployment"){: caption="Figure 1. A typical large VMware multizone instance deployment" caption-side="bottom"}

### Differences between management and resource usage of the two sites
{: #mcv-archi-design-distibution-mgmt-diff}

The two sites that contain the management and resource layers of the VMware multizone instance are designated as Site A and Site B.

vCenter functions in an active-passive availability model with a witness appliance. The NSX control plane functions in an active–active availability model with a quorum of managers.

Your workloads are deployed onto active–active storage that is mirrored between the workload sites. You must plan for sufficient host capacity to run the entire workload in one site. VMware admission control should be used to ensure that neither side is over-committed and that complete loss of a site can be accommodated by moving all workloads to the remaining site. More planning is also required to design a workload network topology, such as that used by the IBM GTS Mission Critical Workloads architecture that is highly available.

#### Site A
{: #mcv-archi-design-site-a}

The consolidated cluster Site A has the following components:
* vCenter Server active appliance
* NSX Manager
* Active Directory server
* Customer workload

#### Site B
{: #mcv-archi-design-site-b}

The consolidated cluster Site B has the following components:
* vCenter Server passive appliance
* NSX Manager
* Active Directory server
* Customer workload

**Next topic:** [VMware multizone BOM](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-bom)

## Related links
{: #mcv-archi-design-related}

* [VMware multizone introduction](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-overview)
* [VMware multizone components](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-comp)
