---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# IBM Cloud networking and infrastructure

## Virtual Routing and Forwarding (VRF)
{{site.data.keyword.cloud}} accounts can also be configured as a VRF account. This
provides similar functions to VLAN spanning, enabling automatic
routing between subnet IP blocks. All accounts with Direct-Link
connections must be converted to, or created as, a VRF account.

## Direct Link
{{site.data.keyword.cloud_notm}} Direct Link Connect offers private access to your {{site.data.keyword.cloud_notm}}
infrastructure and to any other clouds linked to your Network Service
Provider, through your local {{site.data.keyword.CloudDataCent_notm}}. This option is
perfect for creating multi-cloud connectivity in a single environment.
We connect customers to the {{site.data.keyword.cloud_notm}} Private network, by using a shared
bandwidth topology. As with all Direct-Link products, you can add global
routing, which enables private network traffic to all {{site.data.keyword.cloud_notm}}
locations.

## Virtual private networks

### strongSwan VPN
The strongSwan IPSec VPN service provides a secure end-to-end
communication channel over the Internet that is based on the
industry-standard Internet Protocol Security (IPSec) protocol suite.

### Hybridity (HCX)
The VCS Hybridity Bundle on {{site.data.keyword.cloud_notm}} service can seamlessly extend the
networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows
virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without
any conversion or change.

## Physical structure

The physical infrastructure required to deploy a VCS cluster, requires
the following minimum specification.

Table 1. VCS specifications

  | NFS Deployment | VSAN Deployment
---|---|---
Number of Servers | 3 | 4
CPU | 28 Cores 2.2GHZ | 28 Cores 2.2GHZ
Memory | 384 GB | 384 GB
Storage|Mgmt: 2 TB 2 IOPS, Workload: 2 TB 4 IOPS|Min SSD: 960 GB(x2)   

The IKS deployment options vary based on your worker node requirements.

Table 2. IKS specifications

  | virtual machine | Bare Metal
--|---|--
Number of Servers | 3 | 3
CPU | 2 – 56 Core | 4 – 28 Core
Memory | 4 GB - 242 GB | 32 GB - 512 GB
Storage  | 100 GB  |  SATA: 2 TB / SSD: 960 GB

## Virtual structure

Figure 1. Physical structure of IKS and ICP deployments

![Physical Structure of IKS and ICP Deployment
Diagram](vcsiks-phy-ics-iks-deployment.svg)

Within the VCS instance, the customer VMSs are deployed to dedicated NSX
Edge Services Gateways (ESG) and Distributed Logical Routers (DLR).

The ESG is configured with a SNAT to allow outbound traffic, enabling
Internet connectivity to download the ICP prerequisites and connectivity
to GitHub and Docker or a web-proxy can be used to provide the Internet
connectivity. The ESG is configured to access DNS and NTP services via
the private network. Integration to the IKS instance is available via
{{site.data.keyword.cloud_notm}} networking between the VCS instance and IKS.

## VCS components

Figure 2. VCS platform components
![VCS Environment Diagram](vcsiks-vcs-env.svg)

### Platform Service Controller
The VCS deployment uses a single, external platform services controller
(PSC) installed on a portable subnet in the private VLAN associated with
management virtual machines. Its default gateway is set to the backend
customer router (BCR).

### vCenter Server
Like the PSC, the vCenter Server is deployed as an appliance.
Additionally, the vCenter is installed on a portable subnet in the
private VLAN associated with management virtual machines. Its default
gateway is set to the BCR.

### NSX Manager
The NSX Manager is deployed on the initial VCS cluster. Additionally,
the NSX Manager is assigned an IP address from the private portable
address block that is designated for management components.

### NSX Controllers
The {{site.data.keyword.cloud_notm}} automation deploys three NSX Controllers within the
initial cluster. The controllers are assigned IP addresses from the
private portable subnet that is designated for management components.

### NSX ESGs / DLRs
NSX Edge Services Gateway (ESG) pairs are deployed. In all cases, one
gateway pair is used for outbound traffic from automation components
residing on the private network. In the case of VMware vCenter Server on
{{site.data.keyword.cloud_notm}} (VCS) and ICP, a second gateway, which is known as the
icp–managed edge, is deployed and configured with an uplink to the
public network and an interface that is assigned to the private network.
Any required NSX component such as Distributed Logical
Router (DLR), logical switches, and firewalls can be configured by the
administrator. For more information about the NSX Edges that are
deployed as part of the solution, see [vCenter Server networking guide](../vcsnsxt/vcsnsxt-intro.html).

The following tables summarize the ICP ESG / DLR specifications.

Table 3. ICP ESG specifications

Attribute  |  Specification
--|--
Edge Service Gateway | Virtual appliance
Edge size	Large | Number of vCPUs	2
Memory	| 1 GB
Disk	| 1000 GB on local datastore

Table 4. ICP DLR specifications

Attribute  |  Specification
--|--|
Distributed Logical Router |	Virtual appliance
Edge size	Compact | Number of vCPUs	1
Memory	| 512 MB
Disk	| 1000 GB on local datastore

## IKS components

Figure 3. IKS components
![IKS components diagram](vcsiks-iks-components.svg)

### Kubernetes master

The Kubernetes master is tasked with managing all compute, network, and
storage resources in the cluster. The Kubernetes master ensures that
your containerized apps and services are equally deployed to the worker
nodes in the cluster.

###	Worker node
Each worker node is a physical machine (bare metal) or a virtual machine
that runs on physical hardware in the cloud environment. When you
provision a worker node, you determine the resources that are available
to the containers that are hosted on that worker node. Out of the box,
your worker nodes are set up with an IBM-managed Docker Engine, separate
compute resources, networking, and a volume service. The built-in
security features provide isolation, resource management capabilities,
and worker node security compliance.

### Related links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
