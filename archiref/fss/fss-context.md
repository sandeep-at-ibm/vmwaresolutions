---

copyright:

  years:  2020

lastupdated: "2020-07-10"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# System context
{: #fss-context}

Although the IBM Cloud for VMware Regulated Workloads is a self-contained design, there are external dependencies that are necessary. IBM Cloud for VMware Regulated Workloads is designed without the use of IBM Cloud shared offerings such as VSIs and shared storage offerings.

![IBM Cloud for VMware Regulated Workloads context](../../images/fss-context.svg "IBM Cloud for VMware Regulated Workloads context"){: caption="Figure 1. IBM Cloud for VMware Regulated Workloads context" caption-side="bottom"}

Connections between the on-premises environment, CSP (Cloud Service Provider), CHP (Cloud Hosting Provider), and IBM Cloud traverse the internet and are required to use IBM Cloud Direct Link, IPsec, or other secure protocol.

* IBM Cloud Account Administrator - Manages the clients IBM Cloud account through the IBM Cloud portal. The IBM Cloud administrator is the only administrator who can add or remove hosts or services from the cloud account.
* IBM Cloud for VMware Regulated Workloads Administrator - Manages the virtualized environment that is the IBM Cloud for VMware Regulated Workloads instances. The IBM Cloud for VMware Regulated Workloads Administrator manages all compute, storage, and network resources that are used by the client applications. For simplicity, the administrator who is shown is a collection of multiple administration roles. Separation of duties might require dedicated virtualization, network, and security administrator roles.
* User - uses the resources available in the IBM Cloud for VMware Regulated Workloads instances to run their applications. The user has no access to the management plane.
* IBM Cloud data centers - supply the needed racks, cooling, and power to support the vSphere hosts used to build out the regions of the IBM Cloud for VMware Regulated Workloads.
* IBM Cloud network services - enable the connection of the IBM Cloud for VMware Regulated Workloads to the internet (disabled by default), through the frontside network, and through private connection to client over the backside network through IBM Cloud network offerings such as DirectLink.
* Edge cluster - provides compute, storage, and network services to support the gateway appliance. The edge cluster is only present where a virtual appliance is deployed as the perimeter gateway.
* Edge gateway appliance - physical or virtual device that protects the management plane and supports secure network communication between the IBM Cloud for VMware Regulated Workloads Management region and the client.
* Management cluster - provides compute, storage, and network services to support management functions.
* Management services - enable administrators to monitor, operate, and maintain the infrastructure to ensure it is compliant, secure, and available to support client applications.
* Workload clusters - provides compute, storage, and network services to support client applications and operations.
* Applications - applications are VMs that deliver services to the user that support business operations.
* On-premises facilities - customers' existing facilities.
* CSP (Cloud Service Provider) - deliver ancillary services to the user. Examples might include credit card transaction processing or ACH services.
* CHP (Cloud Hosting Provider) - can provide hosting services to support disaster recovery or specialized application hosting.

**Next topic**: [Zero-trust model](/docs/vmwaresolutions?topic=vmwaresolutions-fss-separation-of-duties)

## Related links
{: #fss-context-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance){:external}
