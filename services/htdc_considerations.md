---

copyright:

  years:  2016, 2020

lastupdated: "2020-08-10"

keywords: HyTrust DataControl, HTDC, tech specs HTDC

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl overview
{: #htdc_considerations}

The HyTrust DataControl service offers strong encryption with integrated key management to secure workloads throughout their lifecycle. The service provides encryption at both the operating system level and at the data level. This enables any directory, folder, or file within a workload to be encrypted and decrypted.
{: shortdesc}

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service's licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

The current HyTrust DataControl version that is installed is 5.1.1.
{:note}

## Technical specifications for HyTrust DataControl
{: #htdc_considerations-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

The following components are ordered and included in the HyTrust DataControl service:

### HyTrust DataControl appliance
{: #htdc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* Disk: 20 GB VMDK resident on vSAN in converged cluster
* Network: Placed on VLAN-backed private portable network specified for management

### High availability
{: #htdc_considerations-ha
}
Two DataControl appliances are deployed in an active-active configuration.

### Licenses and fees
{: #htdc_considerations-licenses}

Per-host license: A HyTrust DataControl license is ordered for each host in the environment.

## Considerations when you delete HyTrust DataControl
{: #htdc_considerations-remove}

Before you delete the HyTrust DataControl service, decouple all clients from using DataControl. After you delete the service, the keys might be deleted and you might be locked out of your virtual machines.

## Related links
{: #htdc_considerations-related}

* [Ordering HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_ordering)
* [Managing HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-managinghtdc)
* [Contacting {{site.data.keyword.IBM}} Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [HyTrust website](https://www.hytrust.com/){:external}
