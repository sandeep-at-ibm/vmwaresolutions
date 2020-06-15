---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-10"

keywords: Veeam 9.5, Veeam 9 overview, Veeam 9.5 deprecated

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Veeam v9.5 overview
{: #veeam_considerations}

Veeam v9.5 is deprecated. However, you can continue to use Veeam v9.5. This topic provides information about Veeam v9.5u4b.
{:deprecated}

The Veeam service seamlessly integrates directly with your VMware hypervisors to help your enterprise achieve high availability. This service provides recovery points and time objectives for your applications and data. The recovery points and time objectives can be provided in less than 15 minutes after configuration is completed. By using this service, you control both the backup and restore of all virtual machines (VMs) for your infrastructure directly from the Veeam console.
{: shortdesc}

## Technical specifications for Veeam v9.5u4b
{: #veeam_considerations-specs}

The following components are in the Veeam v9.5u4b service:

The current Veeam version that is installed is v10. The documentation about Veeam v9.5u4b is included for customers using that version.
{:note}

### VSIs for Veeam v9.5u4b
{: #veeam_considerations-specs-vsi}

* Single VSI with Veeam Backup and Replication 9.5 OS Add-on and Veeam Availability Suite 9.5
* Windows Server 2016 Standard Edition (64-bit)
* 4 x 2.0 GHz Cores
* 8 vCPU, 32 GB RAM
* 1 Gbps private network uplink
* 100 GB disk (SAN)

### Storage for backups for Veeam v9.5u4b
{: #veeam_considerations-specs-storage}

* Endurance iSCSI storage:
  * 2,000 GB
  * 4,000 GB
  * 8,000 GB
  * 12,000 GB
* Storage performance (0.25, 2, or 4 IOPS/GB)

As part of the Veeam service installation and configuration, the following repositories are created:
* For the Veeam configuration backup files: a repository named `IC4V Default Config Backup Repository`. The path to the folder where the Veeam backups are stored is `<Drive>:\ConfigBackup\`.
* For scale-out, a repository named `IC4V Scale-Out Repository`. For more information, see [Adding a scale-out repository](/docs/vmwaresolutions?topic=vmwaresolutions-icos_ordering#icos_ordering-scale-repo).
* For the Virtual Machine (VM) backups: a repository named `IC4V Default VM Backup Repository`. The path to the folder where the VM backups are stored is `<Drive>:\VMBackup\`. This repository is added as an extent to `IC4V Scale-Out repository.

### Networking for Veeam v9.5u4b
{: #veeam_considerations-specs-networking}

One primary private IP address.

### Licenses and fees for Veeam v9.5u4b
{: #veeam_considerations-specs-licenses}

Veeam Availability Suite 9.5 (10, 25, 50, 100, or 200 VM license)

## Considerations when you delete Veeam v9.5u4b
{: #veeam_considerations-remove}

Deleting the Veeam service stops all backups and deletes all the previous backups. The backup of the management VMs stops and the deletion of previous backups is irreversible. If the management VMs are corrupted, they can't be restored.

## Related links
{: #veeam_considerations-related}

* [Veeam v10 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Ordering Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering)
* [Managing Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-managingveeam)
* [Ordering Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering_licenses)
* [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses)
* [Ordering and configuring IBM Cloud Object Storage with Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-icos_ordering)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Veeam backup and replication](https://www.ibm.com/cloud/architecture/architectures/virtualization_backup_veeam){:external}
* [Veeam website](https://www.veeam.com/){:external}
* [Veeam Help Center (Technical Documentation)](https://www.veeam.com/documentation-guides-datasheets.html){:external}
