---

copyright:

  years:  2016, 2019

lastupdated: "2019-12-03"

subcollection: vmware-solutions


---

# IBM Cloud networking and infrastructure
{: #vcscar-arch-overview-infrastructure}

## Virtual Routing and Forwarding
{: #vcscar-arch-overview-infrastructure-vrf}

{{site.data.keyword.cloud}} accounts can be configured as a Virtual Routing and Forwarding (VRF) account. A VRF account enables automatic global routing between subnet IP blocks. All accounts with Direct-Link connections must be converted to, or created as, a VRF account.

## Direct Link
{: #vcscar-arch-overview-infrastructure-direct-link}

{{site.data.keyword.cloud_notm}} Direct Link Connect offers private access to your {{site.data.keyword.cloud_notm}} infrastructure and to any other clouds linked to your Network Service Provider, through your local {{site.data.keyword.CloudDataCent_notm}}. This option is perfect for creating multi-cloud connectivity in a single environment.

We connect customers to the {{site.data.keyword.cloud_notm}} Private network, by using a shared bandwidth topology. As with all Direct-Link products, you can add global routing, which enables private network traffic to all {{site.data.keyword.cloud_notm}}
locations.

## Virtual private networks
{: #vcscar-arch-overview-infrastructure-virt-private-net}

### strongSwan VPN
{: #vcscar-arch-overview-infrastructure-strongswan}

The strongSwan IPSec VPN service provides a secure end-to-end communication channel over the internet that is based on the industry-standard Internet Protocol Security (IPSec) protocol suite.

### Hybridity (HCX)
{: #vcscar-arch-overview-infrastructure-hcx}

The VMware vCenter Server Hybridity Bundle service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

## Physical structure
{: #vcscar-arch-overview-infrastructure-phys-structure}

The physical infrastructure required to deploy an {{site.data.keyword.icpfull_notm}} production instance onto a VMware vCenter Server cluster, requires the following minimum specification.

| | NFS Deployment | vSAN Deployment |
|:---------- |:---------- |:---------- |
| Number of Servers | 3 | 4 |
| CPU | 28 Cores 2.2 GHz | 28 Cores 2.2 GHz |
| Memory | 384 GB | 384 GB |
| Storage | 2000 GB 2IOPS/GB Management, 2000 GB 4IOPS/GB Workload, 4000 GB 4IOPS/GB {{site.data.keyword.icpfull_notm}} | Min 960-GB SSD x 2 |
{: caption="Table 1. vCenter Server specification for {{site.data.keyword.icpfull_notm}}" caption-side="bottom"}

In addition to the {{site.data.keyword.cloud_notm}} Private hardware requirements, you must create persistent volumes in the {{site.data.keyword.icpfull_notm}} environment to store Cloud Automation Manager (CAM) database and log data. While CAM supports all of the persistent volume types that {{site.data.keyword.icpfull_notm}} supports, the two recommended storage configurations for CAM are NFS and GlusterFS.

## Virtual structure
{: #vcscar-arch-overview-infrastructure-virt-structure}

![Structure of vCenter Server and {{site.data.keyword.icpfull_notm}} deployment](../../images/vcscar-icp.svg "Structure of vCenter Server and {{site.data.keyword.icpfull_notm}} deployment"){: caption="Figure 1. Structure of vCenter Server and {{site.data.keyword.icpfull_notm}} deployment" caption-side="bottom"}

Within the vCenter Server instance, the {{site.data.keyword.icpfull_notm}} instance is deployed with a dedicated NSX Edge Services Gateway (ESG) and Distributed Logical Router (DLR).
The {{site.data.keyword.icpfull_notm}} installation is loaded into the VXLAN subnet that is defined in the previous components.

The ESG is configured with a source NAT rule (SNAT) to allow outbound traffic, which enables internet connectivity to download the {{site.data.keyword.icpfull_notm}} prerequisites and to connect to GitHub and Docker. Alternatively, you can use a web-proxy for internet connectivity. The ESG is also configured to provide access to DNS and NTP services.

The ESG is also configured with a destination NAT rule (DNAT) to the {{site.data.keyword.icpfull_notm}} Master/Proxy virtual IP addresses from the {{site.data.keyword.cloud_notm}} 10.x network to the VXLAN environment.

**Next topic:** [Common services components for VMware and Skate Advisor Concept Car](/docs/services/vmwaresolutions?topic=vmware-solutions-vcscar-commonservices)
