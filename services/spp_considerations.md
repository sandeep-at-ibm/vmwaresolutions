---

copyright:

  years:  2016, 2021

lastupdated: "2021-01-28

keywords: IBM Spectrum Protect Plus, SPP, tech specs SPP

subcollection: vmwaresolutions

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Spectrum Protect Plus overview
{: #spp_considerations}

The IBM Spectrum® Protect Plus service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement the service as a stand-alone solution or you can integrate it with your IBM Spectrum Protect environment to offload copies for long-term storage and data governance.
{: shortdesc}

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

For VMware vCenter Server® with NSX-V instances, the installed version is 10.1.5. Currently, automated installation of IBM Spectrum Protect Plus is not available for vCenter Server with NSX-T instances.
{:note}

## Technical specifications for IBM Spectrum Protect Plus
{: #spp_considerations-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

The following components are ordered and included in the IBM Spectrum Protect Plus service:

### vCenter resources
{: #spp_considerations-vcenter}

* Server VM running IBM Spectrum Protect Plus server
   * Linux 4.19.65-1c.el7.x86_64 operating system
   * 8 x 2.0 GHz cores
   * 48 GB RAM
   * 528 GB disk
* Secondary VM running IBM Spectrum Protect Plus vSnap server and VADP proxy
   * Linux 4.19.65-1c.el7.x86_64 operating system
   * CPU and RAM configured based on the selected storage size and the sizing guidance in [IBM Spectrum Protect Plus Blueprints](https://www.ibm.com/support/pages/node/1119489){:external}
   * 278 GB disk

### Storage for backups
{: #spp_considerations-backup-storage}

Customizable storage for backups with the following options:
* Number of file storage: 1 - 10
* Each endurance file storage: 500, 1000, 2000, 4000, 8000, or 12000 GB
* Storage performance: 0.25, 2, or 4 IOPS/GB

For planning and sizing information, see [IBM Spectrum Protect Plus Blueprints and Sizing Spreadsheet](https://www.ibm.com/support/pages/node/1119489){:external}.

### Storage for management
{: #spp_considerations-mgmt-storage}

One 1000 GB, 2 IOPS/GB endurance file storage that hosts the IBM Spectrum Protect Plus virtual machine and running on the same subnet as the backup storage.

### Networking
{: #spp_considerations-network}

Two portable private IP addresses.

### Licenses and fees
{: #spp_considerations-license}

* IBM Spectrum Protect Plus (10 to a maximum of 1000 VM licenses in increments of 10)
* IBM Spectrum Protect Plus license offered through the {{site.data.keyword.vmwaresolutions_short}} console (number of VMs in packages of 10) or as BYOL

## Considerations when you install IBM Spectrum Protect Plus
{: #spp_considerations-install}

Review the following considerations before you install the IBM Spectrum Protect Plus service.

* Ensure that the CPU and memory in the default cluster of your instance is sufficient for the IBM Spectrum Protect Plus virtual machine.
* Ensure that the NFS mounts available on the VMware ESXi™ servers are sufficient based on the version of the ESXi servers.

  Instances that are deployed in (or upgraded) to V2.2 or later releases have an `NFS.MaxVolumes` parameter setting in VMware. This parameter defines the maximum number of NFS mounts on an ESXi server and can be set to a maximum of 256 that is specific to the version of the ESXi server. For more information, see [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239){:external}.

  The IBM Spectrum Protect Plus service can use up to 11 of the NFS volumes on each ESXi server in the default cluster of your instance. In addition, the service creates transient NFS mounts for backup and restore purposes. Therefore, you must set the number of NFS mounts to a minimum of 64 to ensure that the service can be installed and function successfully.

## Considerations when you delete IBM Spectrum Protect Plus
{: #spp_considerations-remove}

Review the following considerations before you delete the IBM Spectrum Protect Plus service:
* Ensure that all the backup job configurations are removed along with active backup or restore operations.
* When you delete the service, the storage for the backup repository is deleted from the IBM Spectrum Protect Plus VM and the storage order is canceled, which deletes the backup repository data permanently.
* When you delete the service, the backup storage that is ordered for the service is deleted too. All the backups become inaccessible during service deletion.

## Related links
{: #spp_considerations-related}

* [IBM Spectrum Protect Plus Preventive Service Planning](https://www-01.ibm.com/support/docview.wss?uid=swg22012650)
* [Managing IBM Spectrum Protect Plus](/docs/vmwaresolutions?topic=vmwaresolutions-managingspp)
* [Ordering IBM Spectrum Protect Plus](/docs/vmwaresolutions?topic=vmwaresolutions-spp_ordering)
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Opening a case for IBM Spectrum Protect Plus](https://www.ibm.com/mysupport/s/article/How-to-Open-a-Case)
