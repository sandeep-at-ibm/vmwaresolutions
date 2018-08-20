---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust DataControl on IBM Cloud overview

The HyTrust DataControl on {{site.data.keyword.cloud}} service offers strong encryption with integrated key management to secure workloads throughout their lifecycle. The service can provide encryption at both the operating system level and at the data level, which means that any directory, folder, or file within a workload can be encrypted and decrypted.

**Availability:** This service is available only to instances that are running vSphere 6.5 and that are deployed in (or upgraded to) V2.3 or later releases.

## Technical specifications for HyTrust DataControl on IBM Cloud

The following components are ordered and included in the HyTrust DataControl on {{site.data.keyword.cloud_notm}} service:

### HyTrust DataControl appliance
* CPU: 2 vCPU
* RAM: 8 GB
* Disk: 20 GB VMDK resident on vSAN in converged cluster
* Network: Placed on VLAN-backed private portable network specified for management

### High availability
Two DataControl appliances are deployed in an active-active configuration.

### Licenses and fees

Per-host license: A HyTrust DataControl license is ordered for each host in the environment.

## Considerations when removing HyTrust DataControl on IBM Cloud

Before you remove the HyTrust DataControl on {{site.data.keyword.cloud_notm}} service, ensure that you encrypted or backed up all disks from DataControl. After you remove the service, the keys might be deleted and you could be locked out of your VMs.

### Related links

* [Ordering HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Managing HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust website](https://www.hytrust.com/)
