---

copyright:

  years:  2019

lastupdated: "2019-10-24"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Deployment architecture for Horizon 7
{: #horizon-deploy-arch}

## Horizon 7 pod and building block architecture
{: #horizon-deploy-arch-build-block}

A typical VMware Horizon 7 architecture design uses a pod strategy. A pod is a unit of organization that is determined by Horizon 7 scalability limits. Each pod has a separate management UI and the typical design is to minimize the number of pods.

Customers usually include multiple building blocks in a Horizon 7 pod on-premises. A building block is a logical construct and should not be sized for more than the maximum number of desktops tested. See the VMware Knowledge Base article VMware Horizon 7 sizing limits and recommendations (2150348).

A building block consists of:
* Physical servers
* One vCenter Server and vSphere infrastructure
* Horizon 7 Connection Servers
* Shared storage
* Virtual desktops or RDS hosts for users

![Horizon 7 pod](../../images/horizon-cloud-pod.svg){: caption="Figure 1. Horizon 7 pod" caption-side="bottom"}

When you deploy Horizon 7, a two-cluster approach is recommended. This approach provides a small management cluster for running the server workloads that are used to support the Horizon environment and a larger workload cluster for the VDI or Published Apps workload. The management cluster consists of a three-node cluster that uses NFS storage, and the workload cluster will consider of at least four-nodes utilizing VMware VSAN.

## Sizing Horizon 7
{: #horizon-deploy-arch-sizing}

Planning a deployment of Horizon 7 is like planning an on-premises deployment. You will need to size your Horizon 7 deployment based on your requirements to determine the number of hosts you will need. Hosts are needed for the following purposes:
* Your Virtual Desktop or RDS workloads
* Your Horizon 7 infrastructure components such as connection servers, Unified Access Gateways, and App Volumes managers.
* SDDC infrastructure components on {{site.data.keyword.cloud_notm}}. These components are deployed and managed automatically for you by {{site.data.keyword.cloud_notm}}, but you will need capacity in your SDDC for running them.

The methodology for sizing Horizon 7 is the same as on-premises. {{site.data.keyword.cloud_notm}} provides the ability to customize the hosts deployed through the vCenter Server service, including various processor and RAM options. {{site.data.keyword.cloud_notm}} also provides multiple storage options including VMware VSAN and NFS-based IP storage.

### Minimum SDDC size
{: #horizon-deploy-arch-min-sddc}

The minimum number of hosts that are required for the workload cluster is four nodes. This is the minimum size that is required to utilize VMware VSAN in {{site.data.keyword.cloud_notm}}. The management cluster will need at least three nodes.

### Host sizing and storage recommendations
{: #horizon-deploy-arch-host-sizing}

{{site.data.keyword.cloud_notm}} provides multiple host options based on the Intel Skylake and Broadwell processor architectures with the vCenter Server service. VMware recommends using the Skylake-enabled hosts. Currently, Skylake-enabled hosts on {{site.data.keyword.cloud_notm}} offer three processor options.

The three options are:
* Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz per core
* Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz per core
* Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz per core

The Dual Intel Xeon Gold 6140 option is recommended for VMware Horizon desktop workloads as it provides the most cores and the highest clock rate. This will allow for a greater density of desktops per host. The Management Cluster does not require the Xeon Gold 6140 option, and this workload can utilize the Dual Intel Xeon Silver 4110 processors.

{{site.data.keyword.cloud_notm}} provides multiple options for host RAM. These options range from 64 GB per host to 1.5 TB per host. The total amount of RAM that is required for the management cluster is determined by the memory required to run the vSphere and NSX management components and the Horizon management components.

To support 1,000 users in {{site.data.keyword.cloud_notm}}, 102 GB of RAM is required for the management components.  

The RAM requirements for the management components for the Horizon environment are:
* vCenter Server with embedded PSC: 24 GB
* NSX Manager: 16 GB
* NSX Controllers (x3): 4 GB
* NSX Edges (x4): .5 GB per Edge
* Horizon Connection Servers (x3): 10 GB per server
* App Volumes Managers (x3): 4 GB per server
* Unified Access Gateways (x3 per 1000 users): 2 GB per UAG

Expanding the environment beyond 1000 users would require more Unified Access Gateways, and the RAM required for management components should be increased. This does not include the RAM required for SQL Server, Active Directory domain controllers, or other servers that would be supporting the environment such as file servers.

The amount of RAM required for workload cluster is the number of desktops multiplied by the amount of RAM per desktop. This amount, when added to the management server requirements, will provide the total RAM needed to run the environment.

The vCenter Server offering has two storage types – one based on an All-Flash VSAN and one based on NFS storage. VMware vSAN is preferred for all VDI workloads to provide the best performance. vSAN provides several options during configuration, including the number and size of the capacity tier drives and the ability to utilize Intel Optane for the VSAN cache tier. The Management Cluster should utilize NFS storage for the management VMs. Each datastore should be configured by using the NFS storage option and have 1 TB of capacity with at least 2 IOPS per GB. Environments that are planning to place large file servers might require more IOPS to provide a good user experience in the environment.

For assistance with sizing the cluster environment, use the [vSAN ReadyNode™ Sizer](https://vsansizer.vmware.com/){:external}.

## Network configuration for Horizon 7 deployment on IBM Cloud
{: #horizon-deploy-arch-net-config}

When configuring a new {{site.data.keyword.cloud_notm}} SDDC, multiple networking options are presented. Customers have a choice of using VMware NSX-V or NSX-T when selecting the type of SDDC that they would like to deploy. They can also select the type of networks during deployment including public and private VLANs or private VLANs only. They can provision new VLANs or utilize existing VLANs that have already been created in their cloud.

VMware recommends using the Public and Private Network option. If the Private Network Only option is selected, the NSX Edge Services Gateways will not be configured, and access to some {{site.data.keyword.cloud_notm}} networking services will not be available.

The recommended network architecture consists of a double DMZ and a separation between Horizon management components and the RDSH and VDI virtual machines.

![Network diagram](../../images/horizon-network.svg){: caption="Figure 2. Network diagram. Subnets are for illustrative purposes" caption-side="bottom"}

Because the Horizon Connection Server must communicate with the vCenter Server, traffic must be allowed between these virtual machines.

When direct external access is required, configure a public IP address with Network Address Translation towards the Unified Access Gateway virtual IP of the load balancer.

For external management or access to external or on-premises resources, a VPN connection, Direct-Link Cloud Connect, or Direct-Link Cloud Exchange must be created to the {{site.data.keyword.cloud_notm}} environment.

### Active Directory and DNS services
{: #horizon-deploy-arch-ad-dns}

{{site.data.keyword.cloud_notm}} deploys an Active Directory and DNS Service that will be used by the deployed infrastructure. When deploying the environment, there are two options for this infrastructure.  

These options are:
* Single Windows Server VSI – a single Windows Server running as a domain controller and DNS server. This server runs as a virtual server instance in {{site.data.keyword.cloud_notm}} and includes licensing.
* Highly Available dedicated Windows Server VMs – Two Windows Server virtual machines are deployed into the new SDDC during deployment. The two VMs do not include licensing, and they will need to bring their own server licensing.

These options enable customers to stand up an entire environment without having to have connectivity to the datacenter in place. After the connectivity is in place, the {{site.data.keyword.cloud_notm}} environment can be connected to the enterprise Active Directory via a trust.

When deploying Horizon 7, the highly available option is recommended over the single Windows Server VSI.  Horizon 7 relies heavily on Active Directory, and this option ensures that the service will be available. Since the VMs are running in the management infrastructure, they can also be connected back to on-premises Active Directory environments through trust relationships more easily.

## Architecting Horizon 7 Cloud Pod Architecture (CPA) for IBM Cloud
{: #horizon-deploy-arch-cpa}

Cloud Pod Architecture (CPA) is a standard Horizon 7 feature that allows you to connect your Horizon 7 deployment across multiple pods and sites for federated management. It can be used to scale up your deployment to build hybrid cloud and to provide redundancy for Business Continuity and Disaster Recovery. CPA introduces the concept of a global entitlement (GE) that spans the federation of multiple Horizon pods and sites. Any users or user groups belonging to the global entitlement are entitled to access virtual desktops and RDS published apps on multiple Horizon 7 pods that are part of the CPA.

CPA is not a stretched deployment. Each Horizon 7 pod is distinct and all Connection Servers belonging to each of the individual pods are required to be located in a single location and run on the same broadcast domain from a network perspective.
{:important}

![Basic two site - two pods CPA implementation](../../images/horizon-inter-pod.svg){: caption="Figure 3. Overview of a basic two sites - two pods CPA implementation)" caption-side="bottom"}

For the full documentation on how to set up and configure CPA, see "Administering View Cloud Pod Architecture" in the [VMware Horizon 7 documentation](https://docs.vmware.com/en/VMware-Horizon-7/index.html){:external} and [VMware Workspace ONE and VMware Horizon Reference Architecture](https://techzone.vmware.com/resource/workspace-one-and-horizon-reference-architecture){:external}.

### Using CPA to build Hybrid Cloud and Scale for Horizon 7
{: #horizon-deploy-arch-cpa-hybrid}

You can deploy Horizon 7 in a hybrid cloud environment when you use CPA to interconnect Horizon 7 on-premises and Horizon 7 pods on {{site.data.keyword.cloud_notm}}. You can easily entitle your users to Virtual Desktop and RDS published apps on-premises and/or on {{site.data.keyword.cloud_notm}}. You can configure it such that they can connect to whichever site is closest to them geographically as they roam.

You can also stretch CPA across Horizon 7 pods in two or more {site.data.keyword.CloudDataCents_notm}} with the same flexibility to entitle your users to one or multiple pods as wanted.

The use of CPA is optional. You can choose to deploy Horizon 7 exclusively in a single {site.data.keyword.CloudDataCent_notm}} without linking it to any other data center.

**Next topic:** [Configuring IBM Cloud for Horizon 7 deployment](/docs/services/vmwaresolutions?topic=vmware-solutions-horizon-deploy-config)
