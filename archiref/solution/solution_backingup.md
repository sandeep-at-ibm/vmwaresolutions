---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-20"

---

# Backing up components

As part of the solution, you can optionally deploy the following add-on services to back up the management components that you ordered through the solution:
* IBM Spectrum Protect Plus on IBM Cloud
* Veeam on IBM Cloud

These add-on services are deployed together with IBM Cloud Endurance storage. The services can help you back up your workloads as well as the management components. The management components include the vCenter Server Appliance, PSC, IBM CloudDriver, and if present, the SDDC Manager VM (virtual machine). You can customize the backup policy and schedule.

## NSX Backup

Proper backup of all NSX components is crucial to restoring the system to its working state in the event of a failure. The design automates NSX backup through the NSX manager backup function instead of backing up the VMs. The design uses the IBM CloudDriver server as the FTP or SFTP server for the repository of the NSX backup data.

The NSX Manager backup contains all NSX configuration, including controllers, logical switching and routing entities, security, firewall rules, and everything else that you configure through the NSX Manager UI or API. The following requirements apply for the NSX Manager backup:
* You must back up the vCenter database and related elements such as the virtual switches separately.
* You must back up the NSX configuration in conjunction with a vCenter backup.

The NSX manager is configured to deposit its backups on the IBM CloudDriver VM. An SFTP server is configured on IBM CloudDriver to allow the NSX Manager to deposit its backups. The IBM CloudDriver itself is backed up externally to the cluster by the Veeam backup service.
