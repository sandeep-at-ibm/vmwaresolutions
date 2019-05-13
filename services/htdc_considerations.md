---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl on IBM Cloud overview
{: #htdc_considerations}

The HyTrust DataControl on {{site.data.keyword.cloud}} service offers strong encryption with integrated key management to secure workloads throughout their lifecycle. The service provides encryption at both the operating system level and at the data level. This enables any directory, folder, or file within a workload to be encrypted and decrypted.

This service is available only to instances that are running vSphere 6.5 and are deployed in or upgraded to V2.3 or later. The current HyTrust DataControl version that is installed is 4.3.
{:note}

## Technical specifications for HyTrust DataControl on IBM Cloud
{: #htdc_considerations-specs}

The following components are ordered and included in the HyTrust DataControl on {{site.data.keyword.cloud_notm}} service:

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

## Considerations when you remove HyTrust DataControl on IBM Cloud
{: #htdc_considerations-remove}

Before you remove the HyTrust DataControl on {{site.data.keyword.cloud_notm}} service, decouple all clients from using DataControl. After you remove the service, the keys might be deleted and you might be locked out of your VMs.

## Related links
{: #htdc_considerations-related}

* [Ordering HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Managing HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust website](https://www.hytrust.com/)
