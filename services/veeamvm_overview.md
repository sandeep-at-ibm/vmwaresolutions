---

copyright:

  years:  2020, 2021

lastupdated: "2021-01-28"

keywords: Veeam, Veeam 10, Veeam 10a, Veeam install, tech specs Veeam, Veeam overview

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Veeam v10a overview
{: #veeamvm_overview}

The Veeam® service seamlessly integrates directly with your VMware® hypervisors to help your enterprise achieve high availability. This service provides recovery points and time objectives for your applications and data. The recovery points and time objectives can be provided in less than 15 minutes after configuration is completed. By using this service, you control both the backup and restore of all virtual machines (VMs) for your infrastructure directly from the Veeam console.
{: shortdesc}

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

The current Veeam service that is installed is the new Veeam Availability Suite™ v10a known as Veeam v10a.
{:note}

## Technical specifications for Veeam v10a
{: #veeamvm_overview-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

You can choose one of the following deployment types with Veeam v10a:
* Windows® Server virtual machine (VM) on the management cluster
* Single Public Windows VSI

The following components are ordered and included in the Veeam v10a service:

### VMs for Veeam v10a
{: #veeamvm_overview-specs-vms}

The following are included if you deploy Veeam v10a as a Windows Server VM on the management cluster:

* Virtual machine (VM) with Veeam Backup and Replication 10a OS Add-on and Veeam Availability Suite 10a
* Windows Server 2019 Standard Edition (64-bit)
* 8 vCPU, 32 GB RAM
* 100 GB disk (SAN)

### VSIs for Veeam v10a
{: #veeamvm_overview-specs-vsi}

The following components are included if you deploy Veeam v10a as a single public Windows VSI:

* Single VSI with Veeam Backup and Replication 10a OS Add-on and Veeam Availability Suite 10a
* Windows Server 2019 Standard Edition (64-bit)
* 4 x 2.0 GHz Cores
* 8 vCPU, 32 GB RAM
* 1 Gbps private network uplink
* 100 GB disk (SAN)

### Storage for backups for Veeam v10a
{: #veeamvm_overview-specs-storage}

* Endurance iSCSI storage:
  * 2,000 GB
  * 4,000 GB
  * 8,000 GB
  * 12,000 GB
* Storage performance (0.25, 2, or 4 IOPS/GB)

As part of the Veeam service installation and configuration, the following repositories are created:
* For the Veeam configuration backup files: a repository named `IC4V Default Config Backup Repository`. The path to the folder where the Veeam backups are stored is `<Drive>:\ConfigBackup\`.
* For scale-out, a repository named `IC4V Scale-Out Repository`. For more information, see [Adding a scale-out repository](/docs/vmwaresolutions?topic=vmwaresolutions-icos_ordering#icos_ordering-scale-repo).
* For the virtual machine (VM) backups: a repository named `IC4V Default VM Backup Repository`. The path to the folder where the VM backups are stored is `<Drive>:\VMBackup\`. This repository is added as an extent to `IC4V Scale-Out repository.

### Networking for Veeam v10a
{: #veeamvm_overview-specs-networking}

One primary private IP address.

### Licenses and fees for Veeam v10a
{: #veeamvm_overview-specs-licenses}

For Veeam Availability Suite 10a, you can order 10 - 500 VM licenses in increments of 10.

You must provide a Microsoft® Windows Server 2019 Standard edition license if you choose the option of installing Veeam as a VM.
{:important}

## Considerations when you install Veeam v10a
{: #veeamvm_overview-install}

There are various tasks that you might complete with Veeam v10a, such as ordering a new vCenter Server instance with Veeam and ordering or deleting a Veeam stand-alone license. For more information, see [Tasks you can complete with Veeam v10a](/docs/vmwaresolutions?topic=vmwaresolutions-managingveeam#managingveeam-fivetasks_v10).

Veeam license installation and deletion are different starting with Veeam v10a. For more information, see [Considerations for installing and deleting Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-managingveeam#managingveeam-install-delete-consid).

### Considerations when you delete Veeam v10a
{: #veeamvm_overview-remove}

Deleting the Veeam service stops all backups and deletes all the previous backups. The backup of the management VMs or VSIs stops and the deletion of previous backups is irreversible. If the management VMs or VSIs are corrupted, they can’t be restored.
{:important}

Review the following considerations before you delete the service:
* Deleting the Veeam v10a service does not cancel the Veeam license. You must delete the Veeam license from the Veeam licenses table on the Resources page in the {{site.data.keyword.vmwaresolutions_short}} console.
* When you delete the Veeam v10a service, the {{site.data.keyword.vmwaresolutions_short}} automation deletes only the single Veeam VM or VSI that was deployed and the dedicated private subnet that was ordered for it. Therefore, if you scaled out the Veeam VM or VSI into multiple ones, those additional VMs or VSIs are not deleted.
* The iSCSI storage is deleted, so any data within that storage is lost.

## Related links
{: #veeamvm_overview-related}

* [Ordering Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering)
* [Managing Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-managingveeam)
* [Ordering Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering_licenses)
* [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses)
* [Ordering and configuring IBM Cloud Object Storage with Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-icos_ordering)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Veeam backup and replication](https://www.ibm.com/cloud/architecture/architectures/virtualization_backup_veeam){:external}
* [Veeam website](https://www.veeam.com/){:external}
* [Veeam Help Center (Technical Documentation)](https://www.veeam.com/documentation-guides-datasheets.html){:external}
