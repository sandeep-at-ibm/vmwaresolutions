---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-29"

---

# Viewing the VMware Federal instance default cluster

View the default cluster details for the VMware Federal instances that you ordered.

## VMware Federal instance default cluster summary

The following summary details are available for the VMware Federal instance default cluster in your environment.

Table 1. VMware Federal cluster summary descriptions

| Item        | Description       |  
|:------------- |:------------- |
| Name | The name of the cluster. |
| ESXi Servers | The number of ESXi servers in the cluster. |  
| CPU | The CPU specification of the ESXi servers in the cluster. |  
| Customized vSAN Disks | The number of vSAN disks in the cluster, including the disk type and capacity. |
| Memory | The total memory size of the ESXi servers in the cluster. |  
| Data Center Location | The {{site.data.keyword.CloudDataCent_notm}} where the cluster is hosted. |  
| Pod | The pod where the cluster is deployed. |
| Status | The status of the cluster.|

Table 2. VMware Federal cluster status descriptions

| Status        | Description       |
|:------------- |:------------- |
| Initializing | The cluster is being created and configured. |
| Modifying | The cluster is being modified. |
| Ready to use | The cluster is ready to use. |

## VMware Federal instance default cluster details

You can open the default cluster, grouped as **cluster1** when you ordered the instance, to view the ESXi server, NFS storage, and vSAN license details for the cluster.

Additionally, open the default cluster to manage the ESXi servers for better resource allocation and high availability. For more information, see [Expanding and contracting capacity for VMware Federal instances](vc_fed_addingremovingservers.html).

Table 3. ESXi server summary descriptions

| Item        | Description       |  
|:------------- |:------------- |
| Name | The name of the ESXi server in the following format:<br><br>`<host_prefix><n>.<subdomain_label>.<root_domain>`<br><br>where:<br><br>`host_prefix` is the host name prefix, `n` is the sequence of the server, `subdomain_label` is the subdomain label, and `root_domain` is the root domain name |
| Version | The version of the ESXi server. |  
| Credentials | The user name and password to access the ESXi server. |  
| Private IP | The private IP address of the ESXi server. |  
| Status | The status of the ESXi server.|

Table 4. ESXi server status descriptions

| Status        | Description       |
|:------------- |:------------- |
| Added | The ESXi server is added and is ready for use. |
| Adding | The ESXi server is being added. |
| Deleting | The ESXi server is being deleted. |

Table 5. Storage summary descriptions

**Note:** This table displays only for NFS shared storage clusters.

| Item        | Description       |  
|:------------- |:------------- |
| Name | The data store name. |
| Size | The capacity of the storage. |  
| IOPS/GB | The performance level of the storage. |  
| NFS Protocol | The NFS version of the storage. |  

Table 6. License summary descriptions

**Note:** This table displays only for vSAN clusters.

| Item        | Description       |  
|:------------- |:------------- |
| License | The component for the license. |
| Order Type | Specifies user provided or purchased license.<br><br>**Note:** User provided licenses are not available for VMware Federal instances. |  
| License Edition | The version and edition of the license. |  
| License Key | The license key for a user provided license. <br><br>**Note:** User provided licenses are not available for VMware Federal instances. |
| Total Capacity (CPU) | The total amount of storage capacity. |
| Free Capacity (CPU) | The available amount of storage capacity. |

## Procedure

1. Click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance name.
3. Click the **Infrastructure** tab and review the summary of the default cluster.
4. In the **CLUSTERS** table, click **cluster1** and review the cluster details.

**Important**: You cannot change the cluster name. Changing the cluster name might cause the add or remove ESXi servers operations in the cluster to fail.

## Related links

* [Viewing VMware Federal instances](vc_fed_viewinginstance.html)
* [Expanding and contracting capacity for VMware Federal instances](vc_fed_addingremovingservers.html)
