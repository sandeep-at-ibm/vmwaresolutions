---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: Veeam, Veeam install, tech specs Veeam

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud overview
{: #veeam_considerations}

The Veeam on {{site.data.keyword.cloud}} service seamlessly integrates directly with your VMware hypervisors to help your enterprise achieve high availability. This service provides recovery points and time objectives for your applications and data. The recovery points and time objectives can be provided in less than 15 minutes after configuration is completed. By using this service, you control both the backup and restore of all virtual machines (VMs) for your infrastructure directly from the Veeam console.

This service is available only to instances that are deployed in V1.8 or later. The current Veeam version that is installed is 9.5u4.
{:note}

## Technical specifications for Veeam on IBM Cloud
{: #veeam_considerations-specs}

The following components are ordered and included in the Veeam on {{site.data.keyword.cloud_notm}} service:

### VSIs
{: #veeam_considerations-specs-vsi}

* Single VSI with Veeam Backup and Replication 9.5 OS Add-on and Veeam Availability Suite 9.5
* Windows Server 2016 Standard Edition (64-bit)
* 4 x 2.0 GHz Cores
* 8 vCPU, 32 GB RAM
* 1 Gbps private network uplink
* 100 GB disk (SAN)

### Storage for backups
{: #veeam_considerations-specs-storage}

* Endurance iSCSI storage (2,000, 4,000, 8,000, or 12,000 GB)
* Storage performance (0.25, 2, or 4 IOPS/GB)

As part of the Veeam service installation and configuration, the following repositories are created:
* For the Veeam configuration backup files: a repository named `IC4V Default Config Backup Repository`. The path to the folder where the Veeam backups are stored is `<Drive>:\ConfigBackup\`.
* For scale-out, a repository named `IC4V Scale-Out Repository`. For more information, see [Adding a scale-out repository](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icos_ordering#icos_ordering-scale-repo).
* For the Virtual Machine (VM) backups: a repository named `IC4V Default VM Backup Repository`. The path to the folder where the VM backups are stored is `<Drive>:\VMBackup\`. This repository is added as an extent to `IC4V Scale-Out repository`.

### Networking
{: #veeam_considerations-specs-networking}

One primary private IP address.

### Licenses and fees
{: #veeam_considerations-specs-licenses}

* Veeam Availability Suite 9.5 (10, 25, 50, 100, or 200 VM license)

## Considerations when you install Veeam on IBM Cloud
{: #veeam_considerations-install}

The storage repository and the Veeam server are in the original pod and data center. Therefore, the performance of the backup operations for remote clusters might deteriorate.

## Considerations when you remove Veeam on IBM Cloud
{: #veeam_considerations-remove}

Removal of the Veeam on {{site.data.keyword.cloud_notm}} service stops all backups and deletes all the previous backups. The backup of the management VMs stops and the deletion of previous backups is irreversible. If the management VMs are corrupted, they can't be restored.

## Related links
{: #veeam_considerations-related}

* [Ordering Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Managing Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Managed Services for Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam website](https://www.veeam.com/){:external}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:external}
