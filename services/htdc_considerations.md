---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-13"

keywords: HyTrust DataControl, HTDC, tech specs HTDC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl on IBM Cloud overview
{: #htdc_considerations}

The HyTrust DataControl on {{site.data.keyword.cloud}} service offers strong encryption with integrated key management to secure workloads throughout their lifecycle. The service provides encryption at both the operating system level and at the data level. This enables any directory, folder, or file within a workload to be encrypted and decrypted.

This service is available only to instances that are running vSphere 6.5 and are deployed in or upgraded to V2.3 or later. The current HyTrust DataControl version that is installed is 4.3.2.
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

## Considerations when you install HyTrust DataControl on IBM Cloud
{: #htdc_considerations-install}

* Before the service is installed in your environment, a check is performed against the available capacity of the default cluster in the environment to ensure that the service components can fit.
* If the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email.
* To install the service, you must increase the capacity in your default cluster by either adding more hosts or by freeing up RAM, CPU, or disk space, and then add the service again in the console. After that, you can remove the existing service in the **Capacity Validation Failed** state by clicking the delete icon next to it.

## Considerations when you remove HyTrust DataControl on IBM Cloud
{: #htdc_considerations-remove}

Before you remove the HyTrust DataControl on {{site.data.keyword.cloud_notm}} service, decouple all clients from using DataControl. After you remove the service, the keys might be deleted and you might be locked out of your VMs.

## Related links
{: #htdc_considerations-related}

* [Ordering HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Managing HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust website](https://www.hytrust.com/){:external}
