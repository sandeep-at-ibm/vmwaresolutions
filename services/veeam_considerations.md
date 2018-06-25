---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Veeam on IBM Cloud overview

The Veeam on {{site.data.keyword.cloud}} service seamlessly integrates directly with your VMware hypervisors to help your enterprise achieve high availability. This service can provide recovery points and time objectives for your applications and data. The recovery points and time objectives can be provided in less than 15 minutes after configuration is completed. By using this service, you can directly control both the backup and restore of all virtual machines for your infrastructure from the Veeam console.

**Availability**: This service is available only to instances deployed in V1.8 or later releases.

## Components of Veeam on IBM Cloud

The following components are ordered and included in the Veeam on {{site.data.keyword.cloud_notm}} service:
* One Windows Server 2016 VSI with a primary private IP address and 1 GbE interface
* {{site.data.keyword.cloud_notm}} Endurance block storage of the size and performance that you select when you order the service

## Considerations when installing Veeam on IBM Cloud

* The service backs up the following management components:
  - VMware vCenter Server
  - Platform Services Controller (PSC)
  - IBM CloudDriver
  - **Cloud Foundation instances only**: VMware SDDC Manager
  - **vCenter Server instances with HA AD/DNS only**: High-availability pair of AD/DNS servers

* The configurations of the ESXi servers are not backed up by the Veeam on {{site.data.keyword.cloud_notm}} service.

* By default, the configurations of the NSX Controller and the NSX Edge are backed up daily by using the NSX Manager with up to 14 points of restoration. For a full restore of the NSX configurations, you must create an {{site.data.keyword.cloud_notm}} Support ticket, because the backups of the NSX configurations are saved on the storage that is internal to {{site.data.keyword.vmwaresolutions_full}}. For more information on managing the NSX configuration backups by using NSX Manager, see the [VMware technical instructions](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html).
* The repository for the storage and the Veeam server are in the original pod and data center. Because of that, the performance of the backup operations for remote clusters might deteriorate.

## Considerations when removing Veeam on IBM Cloud

Before you remove the Veeam on {{site.data.keyword.cloud_notm}} service, note that removal of this service will stop all backups (including the backup of the management VMs) and will delete all the previous backups (the deletion is irreversible). If the management VMs are corrupted subsequently, they cannot be restored.

## Related links

* [Ordering Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Managing Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Requesting managed services for Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam website](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
