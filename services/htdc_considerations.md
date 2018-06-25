---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# HyTrust DataControl on IBM Cloud overview

The HyTrust DataControl on {{site.data.keyword.cloud}} service offers strong encryption with integrated key management to secure workloads throughout their lifecycle. The service can provide encryption at both the operating system level and at the data level, which means that any directory, folder, or file within a workload can be encrypted and decrypted.

**Availability:** This service is available only to instances that are running vSphere 6.5 and that are deployed in (or upgraded to) V2.3 or later releases.

## Components of HyTrust DataControl on IBM Cloud

A highly available (HA) pair of HyTrust DataControl (HTDC) appliances is deployed on the default cluster in active-active mode. The HTDC appliances are licensed to provide HyTrust KeyControl functionality to your workloads.

Each pair of HTDC appliances is deployed on the same portable subnet that is specified for the management virtual machines (VMs), such as NSX Manager, vCenter Server Appliances, and Platform Services Controller. The appliances route via the {{site.data.keyword.cloud_notm}} backend customer routers (BCRs) and are assigned the gateway that is associated with the management VMs subnet. Additionally, the appliances are placed on the default storage of the default cluster.

## Considerations when removing HyTrust DataControl on IBM Cloud

Before you remove the HyTrust DataControl on {{site.data.keyword.cloud_notm}} service, ensure that you encrypted or backed up all disks from DataControl. After you remove the service, the keys might be deleted and you could be locked out of your VMs.

## Related links

* [Ordering HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Managing HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust website](https://www.hytrust.com/)
