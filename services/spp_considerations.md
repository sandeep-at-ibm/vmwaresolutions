---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# IBM Spectrum Protect Plus on IBM Cloud overview

The IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement the service as a stand-alone solution or you can integrate it with your IBM Spectrum Protect Plus environment to offload copies for long-term storage and data governance.

**Availability**: This service is available only to instances that are running vSphere 6.5 and that are deployed in (or upgraded to) V2.2 or later releases.

**Notes:**
* If you install the service for instances that are deployed in V2.4 or later releases, IBM Spectrum Protect Plus V10.1.1 Patch 1 is installed. The service provides recovery support for management virtual machines (VMs) automatically.
* If you install the service for instances that are deployed in V2.3, IBM Spectrum Protect Plus V10.1.1 is installed. The service provides backup for management VMs automatically.
* If you install the service for instances that are deployed in V2.2, IBM Spectrum Protect Plus V10.1.0 is installed. The service provides data protection for the workload VMs only.


## Components of IBM Spectrum Protect Plus on IBM Cloud

The following components are ordered and included in the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service:

### vCenter resources

* A single virtual machine (VM) running the IBM Spectrum Protect Plus server
* 4 x 2.0 GHz cores
* 32 GB RAM
* 370 GB disk

### Storage for backups

Customizable storage for backups with the following options:
* Number of file storage: 1, 2, 3, or 4
* Each endurance file storage: 500, 1000, 2000, 4000, 8000, or 12000 GB
* Storage performance: 0.25, 2, or 4 IOPS/GB

### Storage for management

One endurance file storage (500 GB, 2 IOPS/GB) hosting the IBM Spectrum Protect Plus virtual machine and running on the same subnet as the backup storage ordered for the service.

### Networking

One portable private IP address.

### Licenses and fees

IBM Spectrum Protect Plus can be licensed in the {{site.data.keyword.vmwaresolutions_short}} console for 10 to a maximum of 1000 VMs in increments of 10. You can also Bring Your Own License (BYOL) and upload the license file during the installation process.

## Considerations when installing IBM Spectrum Protect Plus on IBM Cloud

Review the following considerations before you install the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service.

* Ensure that the CPU and memory in the default cluster of your instance is sufficient for the IBM Spectrum Protect Plus virtual machine.
* Ensure that the NFS mounts available on the ESXi servers are sufficient based on the version of the ESXi servers.

  Cloud Foundation instances and vCenter Server instances that are deployed in (or upgraded) to V2.2 or later releases have an `NFS.MaxVolumes` parameter setting in VMware. This parameter defines the maximum number of NFS mounts on an ESXi server and can be set to a maximum of 256 which is specific to the version of the ESXi server. For more information, see [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

  The IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service can consume up to five of the NFS volumes on each ESXi server in the default cluster of your instance. In addition, the service will create transient NFS mounts for backup and restore purposes. Therefore, you must set the number of NFS mounts to a minimum of 64 to ensure that the service can be installed and function successfully.

## Considerations when removing IBM Spectrum Protect Plus on IBM Cloud

Review the following considerations before you remove the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service:
* Ensure that all the backup job configurations are removed and that there are no active backup or restore operations.
* When you remove the service, the storage for the backup repository is removed from the IBM Spectrum Protect Plus VM and the storage order is cancelled, which deletes the backup repository data permanently.
* When you remove the service, the backup storage ordered for the service is removed too. Therefore, all the backups become inaccessible during service removal.

## Related links

* [IBM Spectrum Protect Plus on IBM Cloud Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Managing IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Ordering IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
