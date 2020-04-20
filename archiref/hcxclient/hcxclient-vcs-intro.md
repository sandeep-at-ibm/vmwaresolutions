---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-30"

subcollection: vmware-solutions


---

# VMware HCX introduction
{: #hcxclient-vcs-intro}

The VMware HCX service enables creating a seamless connection between {{site.data.keyword.vmwaresolutions_short}} and an on-premises VMware virtualized datacenter.

The {{site.data.keyword.vmwaresolutions_short}} includes fully automated, rapid deployments of VMware vCenter Server (VCS) in the {{site.data.keyword.cloud_notm}}. These offerings complement the on-premises infrastructure and allow existing and future workloads to run in the {{site.data.keyword.cloud_notm}} without conversion by using the same tools, skills, and processes they use on-premises. For more information, see the [Virtualization for extending virtualized private cloud](https://www.ibm.com/cloud/architecture/architectures/virtualizationArchitecture).

The VMware HCX service takes this hybridity to the next step, blending instances of vCenter Server with existing on-premises virtualized datacenters by enabling the creation of seamless network extensions and bidirectional migration of workloads.

The VMware HCX components that are deployed as virtual machines in the {{site.data.keyword.cloud_notm}} VMware target site enable the establishment of a connection with the VMware HCX components installed in the peer on-premises source site.

![VMware vCenter Server – Hybrid Cloud Services](../../images/cloudfoundation_hybrid_cloud_services.svg "VMware vCenter Server – Hybrid Cloud Services"){: caption="Figure 1. VMware vCenter Server – Hybrid Cloud Services" caption-side="bottom"}

This connection creates a loosely coupled inter-connectivity between on-premises and {{site.data.keyword.cloud_notm}} and enables capabilities such as:
* Simple inter-connectivity – logical network connections are established easily over any physical connection such as public internet, private VPN, or direct link.
* Layer 2 extension – on-premises networks are extended into the cloud. These networks include on-premises subnets and IP addressing.
* Encryption – network traffic is securely encrypted between the two sides.
* Optimized network – selects the best connection and efficiently floods the connection so that network traffic is moved as fast as possible.
* Data de-duplication – as much as 50% reduction in network traffic can be achieved Intelligent routing – when a workload is moved, proximity routing can change the network path (that is, gateway) so that network traffic uses the target site gateway and does not “hairpin” back to the originating site.
* Zero downtime migration – a running system can be moved to and back from the cloud by using vMotion.
* Scheduled migration – any number of virtual machines can be replicated to the destination site and then activated on that site at a designated time, which replaces the systems that are running on the originating site.
* Migration of security policies – if NSX is used on-premises, any security policies or firewalls are
moved along with the workload.

**Next topic:** [Preparing the installation environment](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-planning-prep-install)

## Related links
{: #hcxclient-vcs-intro-related}

* [Glossary of HCX components and terms](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-components)
* [HCX Client deployment](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX on-premises Service Mesh](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud migrations](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-migrations)
* [Monitoring parameters and components](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-monitoring)
* [HCX troubleshooting](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-troubleshooting)
