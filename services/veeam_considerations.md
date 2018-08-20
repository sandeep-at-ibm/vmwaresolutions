---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Veeam on IBM Cloud overview

The Veeam on {{site.data.keyword.cloud}} service seamlessly integrates directly with your VMware hypervisors to help your enterprise achieve high availability. This service can provide recovery points and time objectives for your applications and data. The recovery points and time objectives can be provided in less than 15 minutes after configuration is completed. By using this service, you can control both the backup and restore of all virtual machines (VMs) for your infrastructure directly from the Veeam console.

**Availability**: This service is available only to instances deployed in V1.8 or later releases.

## Technical specifications for Veeam on IBM Cloud

The following components are ordered and included in the Veeam on {{site.data.keyword.cloud_notm}} service:

### VSIs

* Single VSI with Veeam Backup and Replication 9.5 OS Add-on
* Windows Server 2016 Standard Edition (64-bit)
* 4 x 2.0 GHz Cores
* 8 GB RAM
* 1 Gbps private network uplink
* 100 GB disk (SAN)

### Storage for backups

* Endurance iSCSI storage (2000, 4000, 8000, or 12000 GB)
* Storage performance (0.25, 2, or 4 IOPS/GB)

### Networking

One primary private IP address.

### Licenses and fees

Veeam Backup and Replication 9.5 Enterprise Plus (10, 25, 50, 100, or 200 VM license).

### Management

Management backups configured by default with up to five VMs and 2000 GB of storage.

## Considerations when installing Veeam on IBM Cloud

The storage repository and the Veeam server are in the original pod and data center. Therefore, the performance of the backup operations for remote clusters might deteriorate.

## Considerations when removing Veeam on IBM Cloud

Before you remove the Veeam on {{site.data.keyword.cloud_notm}} service, note that removal of this service stops all backups (including the backup of the management VMs) and deletes all the previous backups (the deletion is irreversible). If the management VMs are corrupted subsequently, they cannot be restored.

### Related links

* [Ordering Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Managing Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Requesting managed services for Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam website](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
