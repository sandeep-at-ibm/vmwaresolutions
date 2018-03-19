---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

# vCenter Server Bill of Materials

The following table details the Bill of Materials (BOM) information for vCenter Server instances.

Table 1. Bill of Materials for vCenter Server instances

| Manufacturer | Component                       | Version      |
|:-------------|:--------------------------------|:-------------|
| VMware       | vSphere ESXi                    | 6.5 Patch 02 |
| VMware       | vCenter Server Appliance        | 6.5 Update 1e |
| VMware       | Platform Services Controller    | 6.5 Update 1e |
| VMware       | vSAN                            | 6.6.1        |
| VMware       | NSX for vSphere                 | 6.3.5        |
| IBM          | CloudDriver                     | 2.2          |
| Microsoft    | Windows Server Standard edition | 2012R2       |

**Note**: VMware vSAN is an optional component.

## Advanced configuration settings for ESXi servers

Review the following table for an overview of the advanced configuration settings that are applied to ESXi servers depending on whether the vCenter Server instance is deployed in V2.2 or later, or upgraded to V2.2 or later from a previous V2.1 or earlier release.

The settings apply to new instances and new clusters in new instances V2.2 or later. The settings do not apply to new clusters in existing instances from V2.1 or earlier or existing instances upgraded to V2.2 or later.

Table 2. ESXi servers advanced configuration settings for vCenter Server instances and clusters

| Configuration setting | If newly deployed in V2.2 or later  | If upgraded from V2.1 or earlier |   
|:------------- |:------------- |:------------- |
| TCP/IP Heap Size | **TcpipHeapSize** = 32 | Not set |
| TCP/IP Heap Maximum | **TcpipHeapMax** = 1536 | Not set |  
| Maximum of Volumes | **MaxVolumes** = 256 | Both **/NFS/MaxVolumes** and **/NFS41/MaxVolumes** = 256 |  
| Heartbeat Maximum Failures | **HeartbeatMaxFailures** = 10 | Not set |  
| Heartbeat Frequency | **HeartbeatFrequency** = 12 | Not set |  
| Heartbeat Timeout | **HeartbeatTimeout** = 5 | Not set |
| Maximum Queue Depth | **MaxQueueDepth** = 64 | Not set |
| Queue Full Sample Size | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Queue Full Threshold | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |

**Notes**:
* The **MaxVolumes** setting is required for the IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service because the service might use more than the default number of NFS mounts on the ESXi server.
* A value of **Not set** for a configuration setting indicates that the new setting is not automatically applied, because it requires rebooting the ESXi servers, which might be disruptive.

  It is recommended that you change the **Not set** configuration settings to the new values for consistency across all instances and to allow adequate support for storage expansion. IBM plans to test only with these new settings for all {{site.data.keyword.vmwaresolutions_full}} V2.2 and later releases.

  For more information, see [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

## NSX and port group configuration settings

Review the following table for an overview of the NSX and port group configuration settings for vCenter Server instances, and the differences between releases.

The settings apply to new instances and new clusters in new instances V2.2 or later. The settings do not apply to new clusters in existing instances from V2.1 or earlier or existing instances upgraded to V2.2 or later.

Table 3. NSX and port group configuration settings for vCenter Server instances

| Configuration setting | V2.1 or earlier  | V2.2 or later |   
|:------------- |:------------- |:------------- |
| NSX VXLAN cluster teaming policy | Fail Over | Load Balance - SRCID |
| Segment ID pool for primary instance | 6000-8000 | 6000-7999 |  
| Segment ID pool for subsequence secondary instance or instances | 6000-8000 | Previous end range in the multisite + 2000 |  
| Port group SDDC-DPortGroup-VSAN (if applicable) | **Active uplinks** set to **uplink1** and **Standby uplinks** set to **uplink2** | **Active uplinks** set to **uplink2** and **Standby uplinks** set to **uplink1** |  
| Port group SDDC-DPortGroup-Mgmt | **Port binding** set to **Ephermeral - no binding** and **Load balancing** set to **Route based on originating virtual port** | **Port binding** set to **Static binding** and **Load balancing** set to **Route based on physical NIC load** |  
| Port group SDDC-DPortGroup-External | **Port binding** set to **Ephemeral - no binding** | **Port binding** set to **Static binding** |

## Related links

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [vCenter Server overview](vc_vcenterserveroverview.html)
* [Planning vCenter Server instances](vc_planning.html)
