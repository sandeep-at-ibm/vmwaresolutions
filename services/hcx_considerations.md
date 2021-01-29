---

copyright:

  years:  2016, 2021

lastupdated: "2021-01-27"

keywords: VMware HCX, HCX, tech specs HCX

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX overview
{: #hcx_considerations}

The HCX™ service extends the networks of on-premises data centers into {{site.data.keyword.cloud}}, and it helps you migrate virtual machines (VMs) to and from the {{site.data.keyword.cloud_notm}} without any conversion or change. HCX creates an abstraction layer that enables application mobility and infrastructure hybridity through securely stretched networks. You can modernize your VMware® environment from VMware vSphere® 5.1 to the most recent vSphere version without needing to refactor or modify your existing application, as HCX enables this seamless transformation. With HCX, you can bring your IP subnet ranges into {{site.data.keyword.cloud_notm}} ensuring the IP consistency through a hybrid deployment and by providing high-level security with end-to-end Suite B encryptions.
{: shortdesc}

VMware HCX requires you to use either VMware NSX® Advanced or Enterprise through {{site.data.keyword.cloud_notm}} or an equivalent version that uses BYOL (Bring Your Own License).

{{site.data.keyword.vmwaresolutions_short}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

VMware requires you to be on one of their supported versions in order for you to open a support request for HCX. For more information, see [VMware HCX release notes](https://docs.vmware.com/en/VMware-HCX/services/rn/VMware-HCX-Release-Notes.html){:external}.

A VMware vCenter Server® instance with HCX is limited to three simultaneous connections from on-premises sites.

For vCenter Server with NSX-T instances, HCX is supported for NSX-T 3.1 and VMware vSphere 7.0 Update 1a.

For vCenter Server with NSX-V instances, HCX is supported for the following vSphere versions:
* vSphere 6.7
* vSphere 6.5 (vDS must be at a 6.0 level)

## Technical specifications for HCX
{: #hcx_considerations-specs}

The following components are ordered and included in the HCX service.

On-premises HCX instances include only licensing and activation.
{:note}

### VMware NSX Edge Services Gateways for HCX management (NSX-V only)
{: #hcx_considerations-nsx}

An active/passive pair of VMware NSX Edge Services Gateways for HCX management is ordered for vCenter Server with NSX-V instances only.
* CPU: 6 vCPU
* RAM: 8 GB
* Disk: 3 GB VMDK

### HCX Management Appliance - virtual machine
{: #hcx_considerations-vm}

* CPU: 4 vCPU
* RAM: 12 GB
* Disk: 60 GB VMDK

More HCX appliances are deployed during configuration as necessary for L2 connectivity, WAN optimization, and gateway connections.

### Networking
{: #hcx_considerations-networking}

* One public portable subnet with 16 IP addresses
* Two private portable subnets with 64 IP addresses
* Eight IP addresses from private portable vMotion subnet

For information about resource requirements and capacity checking, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

### NFS storage
{: #hcx_considerations-nsf-storage}

If the service mesh target cluster is not a vSAN™ cluster, NFS storage (500 GB/ 10 IOPS/GB) is automatically ordered. Note that by default on NSX-V, the service mesh target cluster is the default cluster.

## Considerations when you install HCX
{: #hcx_considerations-install}

Review the following considerations before you attempt to install HCX.

### Requirements on the number of ESXi servers
{: #hcx_considerations-esxi-servers}

The HCX service mesh target cluster cannot have more than 51 ESXi servers. HCX requires eight IP addresses in the vMotion subnet from the service mesh target cluster. Because of this requirement, if the number of ESXi servers exceeds 51, no IP addresses in the vMotion subnet are available for HCX. Note that when HCX is installed on VMware vCenter Server with NSX-V, the service mesh target cluster is always the default cluster.

### Requirements on firewall rules
{: #hcx_considerations-firewall}

Before you install the HCX service, you must add a firewall rule to any existing firewalls to allow all outbound HTTPS traffic so that the HCX Manager virtual appliance (HCX Manager) can register itself. After the HCX Manager installation is completed, you can remove the firewall rule. In addition, you must configure firewall rules to allow HCX to function properly. For more information, see [VMware HCX port access requirements](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-port-req#hcx-archi-port-req).

## Considerations when you delete HCX
{: #hcx_considerations-delete}

Review the following considerations before you delete the HCX service:
* Ensure that the service mesh and extended networks between the on-premises source site and the {{site.data.keyword.cloud_notm}} target sites are deleted. To remove the service mesh and extended networks, use the HCX user interface in the on-premises VMware vSphere Web Client.

* Ensure that the site pairings between the on-premises source site and the {{site.data.keyword.cloud_notm}} target sites are removed. To remove the site pairings, use the HCX user interface in the on-premises VMware vSphere Web Client.

* If you delete a workload cluster and that cluster is the service mesh cluster, the HCX add-on service is automatically deleted.

* The deletion of HCX is automated. The following procedures are completed for the successful deletion of this service:
   * The HCX license that is ordered for the cloud-side HCX Manager is deactivated.
   * HCX Manager is deleted.
   * The vMotion IP addresses that were reserved for HCX are released.
   * The HCX management edge appliances are deleted.

Only the virtual machines that were deployed during the initial installation of the HCX instances are deleted. Any node that is deployed after the installation is not cleaned up.
{:note}

## Related links
{: #hcx_considerations-related}

* [Ordering HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_ordering)
* [Managing HCX](/docs/vmwaresolutions?topic=vmwaresolutions-managinghcx)
* [VMware HCX on {{site.data.keyword.cloud_notm}} guided demo: Learn how to migrate a VM by using HCX](https://www.ibm.com/cloud/garage/dte/producttour/vmware-hcx-ibm-cloud-guided-demo-learn-how-migrate-vm-using-hcx){:external}
* [Glossary of HCX terms](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_glossary)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension documentation](https://cloud.vmware.com/vmware-hcx/resources){:external}
