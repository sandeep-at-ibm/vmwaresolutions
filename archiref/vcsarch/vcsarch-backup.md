---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-04"

---

# Backup

As part of this solution, Veeam backup software is optionally deployed on an {{site.data.keyword.cloud}} virtual server instance (VSI) using {{site.data.keyword.cloud_notm}} Endurance storage outside the VMware cluster. The software backs up the management components in this solution. Specifically, Veeam automatically backs up the vCenter Server Appliance and the Platform Services Controller. These backups occur daily with 14 restore points. You can modify the backup schedule.


## NSX backup

Proper backup of all NSX components is crucial to restore the system to its working state if a failure occurs. It isn't sufficient to back up the NSX virtual machines (VMs). You must employ the NSX backup function within the NSX manager for a proper backup. This requires you specify an FTP or SFTP server for the repository of NSX backup data.

The NSX Manager backup contains all of the NSX configuration, including controllers, logical switching and routing entities, security, firewall rules, and everything else you configure within the NSX Manager user interface (UI) or API. You must backup the vCenter database and related elements, such as the virtual switches, separately. Backup the NSX configuration along with a vCenter backup. The NSX manager backup is the responsibility of the user.

## Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
