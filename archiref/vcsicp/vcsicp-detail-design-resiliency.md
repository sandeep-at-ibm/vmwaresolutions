---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Backup, disaster recovery, and scalability

## Backup and DR

###	VCS backup

As part of {{site.data.keyword.vmwaresolutions_full}}, Veeam backup software is optionally deployed on an {{site.data.keyword.cloud_notm}} virtual server instance (VSI) using {{site.data.keyword.cloud_notm}} Endurance Storage outside the VMware cluster. The purpose of this software is to back up the management components in this solution.

### NSX backup

Proper backup of all NSX components is crucial to restore the system to its working state if failure occurs. It is not sufficient to back up the NSX VMs, the NSX backup function within the NSX Manager must be employed for a proper backup. This requires that an FTP or SFTP server be specified for the repository of NSX backup data.
The NSX Manager backup contains all of the NSX configuration, including controllers, logical switching and routing entities, security, firewall rules, and everything else that you configure within the NSX Manager UI or API. The vCenter database and related elements like the virtual switches need to be backed up separately. The NSX configuration should be backed up along with a vCenter backup.

###	Backup and DR for IBM Cloud Private

Backups for an ICP deployment are crucial to restore the system to its working state if failure occurs. On top of a traditional VM backup, there is a sticking point, every ICP master node runs etcd, and etcd documentation clearly states not to use traditional VM backup to restore it.

{{site.data.keyword.cloud_notm}} Private at the platform level, you need to back up these components:

-	**Etcd** — is used to store Kubernetes resources as well as Calico state information.
-	**Docker Registry** — private image registry that is used to store container image files in an image repository.
-	**MongoDB** — database that is used by the metering service, Helm repository server, Helm API server, LDAP configuration, Tenant (namespace), and team/user/usergroup role configurations.
-	**MariaDB** — database that is used by OIDC.
-	**Elasticsearch** — stores the system and application logs.
-	**Prometheus** — stores data for monitoring.
-	**Persistent storage** — used for management services that leverage ICP or Kubernetes Persistent Volume and storage provider. You can use the backup or restore technology that is provided by the storage provider. A similar process can be extended into your user’s application as well.

###	Backup and DR for CAM
Backup for a CAM deployment is crucial to restore the system to its working state if failure occurs. The CAM backup requires the customer to back up the following components:
-	**Mongo Database** – Main CAM database.
-	**Maria Database** - Used by CAM Blueprint Designer.
-	**NFS/GlusterFS** - CAM data resides in four persistent volumes.

### Backup and DR for IKS
Backups of the etcd database are provided to the customer as part of the managed service, any application data must be backed by yourself.

## Scalability

### VCS scalability

After the deployment of the initial hosts, the user has the ability to scale out the compute capacity from within the {{site.data.keyword.cloud_notm}} for VMware portal.

This scale out of the environment follows one of three paths:
- Addition of new sites managed by separate vCenter Servers.
- Addition of new clusters.
- Addition of new hosts to an existing cluster.

####	Multi site deployments
VMware on {{site.data.keyword.cloud_notm}} can leverage IBM Cloud’s world–wide data center presence and integrated network backbone to allow for various cross–geography use cases to be deployed and functioning within a fraction of the time it would take to build such an infrastructure from scratch.

####	Scale out with new cluster
The user also has the option to scale out the compute capacity by creating a new cluster from within the console, ordering the hosts, and the new hosts are automatically added to the new cluster. This option will create a separate cluster in the environment and give users the ability to physically and logically segregate management workloads from application workloads, the ability to segregate workloads based on other characteristics (for example, Microsoft SQL database cluster), and the ability to deploy applications in highly available topologies.

####	Scale out existing cluster
The user can scale out an existing cluster by ordering hosts from within the console and the new hosts are automatically added to the cluster. Note that users might need to adjust the HA reservation policy for the cluster based on their reservation requirements.

### ICP scalability
Based on the available compute capacity at the on-premises or cloud locations, the user has the ability to scale out the node architecture from the boot node initially deployed.

The scale out of the environment follows:
- Expand the ICP worker nodes.
- Expand and utilize the IKS offering.

####	ICP expansion
ICP worker virtual machine nodes are scaled to expand the compute/application:
  - Customer provisions a new virtual machine, in the same VXLAN that ICP is deployed.
  - Customers can scale worker nodes, by provisioning new virtual machines, then logging in to the boot node and running a command to bring the new nodes into the cluster.
  - Utilize CAM to automate the provisioning of the VM and running the commands to add to the ICP Cluster.


###  IKS expansion
Users can provision an IKS environment via the {{site.data.keyword.cloud_notm}} Portal to extend/utilize a container environment.

Application deployments into IKS can be done via:
- IKS connection/services are developed in CAM and published to ICP catalog.
- Multi-Cloud Manager future enhancement to manage IKS instances
- Helm Command Line.
- Use Multizone clusters to increase high availability.

### Related links
* [Adding or removing cluster nodes](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Adding worker nodes by resizing an existing worker pool](../../../../containers/cs_clusters.html#resize_pool)
* [How to back up and restore {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [ICP backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
