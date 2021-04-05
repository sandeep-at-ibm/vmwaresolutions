---

copyright:

  years:  2016, 2021

lastupdated: "2021-03-24"

keywords: HyTrust KeyControl, HTKC, tech specs HTKC

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust KeyControl overview
{: #htkc_considerations}

The HyTrust® KeyControl™ service simplifies the management of encrypted workloads. This service automates and simplifies the lifecycle of encryption keys, including key storage, key distribution, key rotation, and key revocation. Using FIPS 140-2 compliant encryption, enterprises can easily manage encryption keys at scale.
{: shortdesc}

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

The HyTrust KeyControl service is not supported for VMware vCenter Server® with NSX-T instances. For vCenter Server with NSX-V instances, the installed version is 5.0.1.
{:note}

## Technical specifications for HyTrust KeyControl
{: #htkc_considerations-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

The following components are ordered and included in the HyTrust KeyControl service:

### HyTrust KeyControl appliance
{: #htkc_considerations-appliance}

* CPU - 2 vCPU
* RAM - 8 GB
* Disk - 20 GB VMDK resident on vSAN in the consolidated cluster
* Network - Placed on a VLAN-backed private portable network specified for management

### High availability
{: #htkc_considerations-ha}

By default, two KeyControl appliances are deployed in an active-active clustered configuration.

Optionally, you can specify to deploy two KeyControl appliances in a stand-alone unclustered configuration.

### Licenses and fees
{: #htkc_considerations-licenses}

A HyTrust KeyControl license is ordered for each instance installation.

## Considerations when you delete HyTrust KeyControl
{: #htkc_considerations-remove}

Review the following considerations before you delete the service:

* Before you delete the HyTrust KeyControl service, ensure that you decouple all clients from using KeyContol. After you delete the service, the keys might be deleted and you might be locked out of your VMs.

* If you installed the HyTrust KeyControl service before VMware Solutions v4.0 and you then delete that service, you must manually remove the DNS entries. For more information, see [Manually removing the DNS entries](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-remove-DNS-entries).

## Related links
{: #htkc_considerations-related}

* [Ordering HyTrust KeyControl](/docs/vmwaresolutions?topic=vmwaresolutions-htkc_ordering)
* [Managing HyTrust KeyControl](/docs/vmwaresolutions?topic=vmwaresolutions-managinghtkc)
* [Contacting {{site.data.keyword.IBM}} Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [HyTrust website](https://www.hytrust.com/){:external}
