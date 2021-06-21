---

copyright:

  years:  2021

lastupdated: "2021-04-13"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on bare metal server introduction
{: #veeam-bms-archi-intro}

The Veeam on bare metal server for {{site.data.keyword.vmwaresolutions_short}} service can be used as a dedicated and all-in-one backup solution for VMware Solutions Dedicated instances, such as vCenter Server or VMware Regulated Workloads.

The Veeam on bare metal server solution is built on standard {{site.data.keyword.cloud_notm}} bare metal servers. The servers have both a dedicated compute and a local dedicated storage. This solution provides a backup infrastructure that is physically isolated from other {{site.data.keyword.cloud_notm}} Storage services.

The solution uses Direct Attached Storage (DAS), that is, local SATA disks with RAID 6 attached to the bare metal server, as the Storage Repository for backups. For scaling up, customers can add more proxy servers to the solution to add backup capacity and performance. They can also use {{site.data.keyword.cloud_notm}} Object Storage together with Veeam's scale-out backup repository functions for redundancy (copying backups) or long-term retention (offload backups).

**Next topic:** [Veeam on bare metal server overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeam-bms-archi-overview)

## Related links
{: #veeam-bms-archi-overview-intro}

* [Veeam Backup & Replication](https://www.veeam.com/vm-backup-recovery-replication-software.html?ad=menu-products){:external}
* [Veeam Help Center technical documentation](https://www.veeam.com/documentation-guides-datasheets.html?ad=menu-resources){:external}
