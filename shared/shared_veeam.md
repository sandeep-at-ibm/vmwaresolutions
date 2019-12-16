---

copyright:

  years:  2019

lastupdated: "2019-12-11"

keywords: veeam, veeam install, tech specs veeam

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam for VMware Solutions Shared
{: #shared_veeam_considerations}

The Veeam service is available and ready-to-use in all vCloud Director virtual data center instances. It seamlessly integrates as a managed solution to help your enterprise achieve high availability. This service provides recovery points for your applications and data. By using this service, you control both the backup and restore of all virtual machines (VMs) for your infrastructure directly from the Veeam console.
{: shortdesc}

## Managing Veeam
{: #shared_veeam-managing}

Veeam is available at the VMware vCloud Director organization level and has visibility to back up VMs from any virtual data center in the organization.

You can access the Veeam self-service portal on the Virtual Data Center details page when the instance is in the **Ready to Use** state. For information about accessing the details page, see [Procedure to view the Virtual Data Center details](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing#shared_managing-procedure-view-vdc-details).

### Procedure to access Veeam from the Virtual Data Center instance
{: #shared_veeam-proc-access}

1. On the Virtual Data Center details page, under **Recommended Services**, click **Veeam Portal**.
2. Log in to the Veeam Portal by using the vCloud Director **admin** credentials that you use to log in to the vCloud Director Management Console. To obtain the vCloud Director credentials, use the **Get Location Password** link.

Any vCloud Director user with the **Organization Administrator** role can log in to the **Veeam Portal**.

When creating backup jobs in the **Veeam Portal**, you can choose vApp and VM instances from any virtual data center in the organization.

Alternatively, click the **admin** drop down in the vCloud Director Management Console to log in to the Veeam Portal.
{:note}

## Licenses and fees
{: #shared_veeam_fees}

Veeam usage incurs the following On-demand charges. You can view the charges on the **{{site.data.keyword.cloud}} billing and usage** view along with the usage and charges from all other {{site.data.keyword.cloud_notm}} services.

In the **{{site.data.keyword.cloud_notm}} Usage** view, locate the **VMware Solutions** service type. Locate the **Organization** plan to find the Veeam usage across all virtual data centers in that organization. The virtual data center usage is located in a separate plan, depending on the type of virtual data center (**On-Demand** or **Reserved**).

| Metric                                   | Frequency   | Description |
|:-----------------------------------------|:------------|:------------|
| Veeam_Instances_License | Monthly | Veeam license charge for every VM under backup. The monthly charge is for the highest number of VMs under backup at any time period in the month. |
| Veeam_Backup_Block_Storage_GB_Hour | Hourly | Charge per GB of block storage used for all backups. |
| Veeam_Backup_Object_Storage_GB_Hour | Hourly | Charge per GB of object storage used for all backups. |
{: caption="Table 1. Licenses and fees" caption-side="top"}

There are no additional Veeam usage charges for VMware Solutions Shared.
{:note}

Initially, all backups go to the block storage that is closest to their VM workloads. Backups that are older than 14 days are automatically moved to longer term Cloud Object Storage in the region, which are at a lower price point. The restore speed for these older than 14 days backups might be impacted.

You can change the default 14 days time period by opening a VMware Solutions service ticket.

## Considerations when you remove vCloud Director virtual data centers
{: #shared_veeam_considerations-remove}

If you remove all vCloud Director virtual data centers in your account, backup operations will be stopped. All previous backups will also be deleted and cannot be recovered.

## Limitations
{: #shared_veeam_limitations}

- For Veeam **application aware image processing** and **guest file system indexing** options to work for Windows VMs, the latest VMware Tools must be installed on the VMs. Linux VMs are not supported.
- If you are using **application aware image processing** for MS SQL or Oracle DB backups, note that the options **application aware** and **Item** restore are not supported. The restore operation needs to complete a full VM restore, which requires a downtime window for any consumers of the database.

## Related links
{: #shared_veeam_considerations-related}

* [Ordering Shared On-demand](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_ordering_ondemand)
* [Ordering Shared Reserved](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_ordering_reserved)
* [Managing Shared resources](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [VMware Solutions Shared operations](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_vcd-ops-guide)
* [FAQ](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
* [Veeam website](https://www.veeam.com/){:external}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:external}
