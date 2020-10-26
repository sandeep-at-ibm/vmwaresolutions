---

copyright:

  years:  2016, 2020

lastupdated: "2020-09-25"

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

The HCX service extends the networks of on-premises data centers into {{site.data.keyword.cloud}}, and it helps you migrate virtual machines (VMs) to and from the {{site.data.keyword.cloud_notm}} without any conversion or change. HCX creates an abstraction layer that enables application mobility and infrastructure hybridity through securely stretched networks. You can modernize your VMware® environment from vSphere 5.1 to the most recent vSphere version without needing to refactor or modify your existing application, as HCX enables this seamless transformation. With HCX, you can bring your IP subnet ranges into {{site.data.keyword.cloud_notm}} ensuring the IP consistency through a hybrid deployment and by providing high-level security with end-to-end Suite B encryptions.
{: shortdesc}

VMware HCX requires you to use either NSX Advanced or Enterprise through {{site.data.keyword.cloud_notm}} or an equivalent version that uses BYOL (Bring Your Own License). A 12-month commitment is required when you order the VMware HCX service. You are charged for 12 consecutive months after the initial deployment of HCX. Any additional nodes are included within the initial provisioning expiration date. After the 12-month commitment expires, you can install and uninstall the HCX service and you can add and remove hosts and clusters without restrictions. Your account is then charged monthly and you can cancel at any time.

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

The 12-month commitment expiration date is available on the HCX details page. For more information about viewing service details, see [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

VMware requires you to be on one of their supported versions in order for you to open a support request for HCX. For more information, see [VMware HCX release notes](https://docs.vmware.com/en/VMware-HCX/services/rn/VMware-HCX-Release-Notes.html){:external}.

A vCenter Server instance with HCX is limited to three simultaneous connections from on-premises sites.

HCX is supported on the following platforms:
* vSphere 5.1 (command line only for vCenter Server 5.1 using the REST API)
* vSphere 5.5 (web client UI supported on vCenter Server 5.5u3 and later)
* vSphere 6.0
* vSphere 6.5 (vDS must be at a 6.0 level)
* vSphere 6.7

## HCX and multi-site service mesh
{: #hcx_considerations-hcx-services-mesh}

HCX uses multi-site service mesh to provide its services. Multi-site service mesh provides the following features:
* Increased flexibility in the configuration and scalability of HCX.
* Numerous usability improvements, such as deployment diagrams and diagnostic tools.
* Compute and Network profiles that are shareable across multiple sites that are connected to the HCX cloud instance.

The {{site.data.keyword.vmwaresolutions_short}} automation configures the Compute profile and Network profiles on the cloud side HCX instance when it is installed, so the instance is ready for pairings with on-premises data centers.

For more information, see [About the HCX multi-site service mesh](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-59FC4E76-5DE4-444C-ADDD-50A3D31AA677.html){:external}.

## Technical specifications for HCX
{: #hcx_considerations-specs}

The following components are ordered and included in the HCX service.

On-premises HCX instances include only licensing and activation.
{:note}

### An active/passive pair of VMware NSX Edge Services Gateways for HCX management
{: #hcx_considerations-nsx}

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

## Considerations when you install HCX
{: #hcx_considerations-install}

Review the following considerations before you attempt to install HCX.

### Requirements on the number of ESXi servers
{: #hcx_considerations-esxi-servers}

The HCX service cannot be installed into an instance for which the default cluster has more than 51 ESXi servers. HCX requires eight IP addresses in the vMotion subnet from the default cluster. Because of this requirement, if the number of ESXi servers exceeds 51, no IP addresses in the vMotion subnet are available for HCX.

### Requirements on firewall rules
{: #hcx_considerations-firewall}

Before you install the HCX service, you must add a firewall rule to any existing firewalls to allow all outbound HTTPS traffic so that the HCX Manager virtual appliance (HCX Manager) can register itself. After the HCX Manager installation is completed, you can remove the firewall rule. In addition, you must configure firewall rules to allow HCX to function properly. For more information, see [VMware HCX port access requirements](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-port-req#hcx-archi-port-req).

## Considerations when you delete HCX
{: #hcx_considerations-delete}

A 12-month commitment is required when you order the HCX service. You cannot delete the service until your 12-month period expires. The 12-month commitment expiration date is available on the HCX details page. For more information about viewing service details, see [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure). The 12-month commitment and charging structure do not apply to existing vCenter Server with Hybridity Bundle instances.
{:note}

Review the following considerations before you delete the HCX service:
* Ensure that the service mesh and extended networks between the on-premises source site and the {{site.data.keyword.cloud_notm}} target sites are deleted. To remove the service mesh and extended networks, use the HCX user interface in the on-premises VMware vSphere® Web Client.

* Ensure that the site pairings between the on-premises source site and the {{site.data.keyword.cloud_notm}} target sites are removed. To remove the site pairings, use the HCX user interface in the on-premises VMware vSphere Web Client.
* The deletion of HCX is automated. The following procedures are completed for the successful deletion of this service:
   * The HCX license that is ordered for the cloud-side HCX Manager is deactivated.
   * HCX Manager is deleted.
   * The vMotion IP addresses that were reserved for HCX are released.
   * The HCX-related resource pools are removed.
   * The HCX management edge appliances are deleted.

Only the virtual machines (VMs) that were deployed during the initial installation of the HCX instances are deleted. Any node that is deployed after the installation is not cleaned up.
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
