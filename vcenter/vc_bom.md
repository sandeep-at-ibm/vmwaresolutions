---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-20"

---

# vCenter Server Bill of Materials

Review the Bill of Materials (BOM) information for VMware vCenter Server instances.

## VLANs BOM for vCenter Server instances

The following table details the BOM information for the vCenter Server VLANs.

Table 1. BOM for the VLANs in vCenter Server instances

| VLAN      | Type      | Details      |
|:----------|:----------|:-------------|
| VLAN1     | Public, Primary | Assigned to physical ESXi servers for public network access. Not used after initial deployment. Available for internet access. |
| VLAN2     | Private A, Primary | Assigned by IBM Cloud to physical ESXi servers. Used by the management interface for VMware vSphere management traffic.<br><br>Assigned to VMs (virtual machines) that function as management components.<br><br>Assigned to VMware NSX VTEP (VXLAN Tunnel Endpoint) |
| VLAN3     | Private B, Portable | Assigned to VMware vSAN, if used.<br><br>Assigned to VMware NFS, if used.<br><br>Assigned to VMware vSphere vMotion. |

## Software BOM for vCenter Server instances

The following table details the BOM information for vCenter Server software components.

Table 2. BOM for the software components in vCenter Server instances

| Manufacturer | Component                       | Version      |
|:-------------|:--------------------------------|:-------------|
| VMware       | vSphere ESXi                    | 6.5 U1g (ESXi 6.5u1 with patch level ESXi650-201803001 applied) |
| VMware       | vCenter Server Appliance        | 6.5 Update 1g |
| VMware       | Platform Services Controller    | 6.5 Update 1g |
| VMware       | vSAN                            | 6.6.1        |
| VMware       | NSX for vSphere                 | 6.3.5       |
| {{site.data.keyword.IBM}} | CloudDriver        | 2.4          |
| Microsoft    | Windows Server Standard edition | 2012R2       |

**Note**: VMware vSAN is an optional component.

## Advanced configuration settings for ESXi servers

Review the following table for an overview of the advanced configuration settings that are applied to ESXi servers depending on whether the vCenter Server instance is deployed in V2.2 or later, or upgraded to V2.2 or later from a previous V2.1 or earlier release.

The settings apply to new instances and new clusters in new instances V2.2 or later. The settings do not apply to new clusters in existing instances from V2.1 or earlier or existing instances upgraded to V2.2 or later.

Table 3. ESXi servers advanced configuration settings for vCenter Server instances and clusters

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

  It is recommended that you change the **Not set** configuration settings to the new values for consistency across all instances and to allow adequate support for storage expansion. IBM plans to test only with these new settings for all {{site.data.keyword.vmwaresolutions_short}} V2.2 and later releases.

  For more information, see [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

## NSX and port group configuration settings

Review the following table for an overview of the VMware NSX and port group configuration settings for vCenter Server instances, and the differences between releases.

The settings apply to new instances and new clusters in new instances V2.2 or later. The settings do not apply to new clusters in existing instances from V2.1 or earlier or existing instances upgraded to V2.2 or later.

Table 4. NSX and port group configuration settings for vCenter Server instances

| Configuration setting | V2.1 or earlier  | V2.2 or later |   
|:------------- |:------------- |:------------- |
| NSX VXLAN cluster teaming policy | Fail Over | Load Balance - SRCID |
| NSX VXLAN cluster VTEP | 1 | 2 |
| Segment ID pool for primary instance | 6000-8000 | 6000-7999 |  
| Segment ID pool for subsequent secondary instance or instances | 6000-8000 | Previous end range in the multi-site configuration + 1 to Previous end range in the multi-site configuration + 2000 |  
| Port group SDDC-DPortGroup-VSAN (if applicable) | **Active uplinks** set to **uplink1** and **Standby uplinks** set to **uplink2** | **Active uplinks** set to **uplink2** and **Standby uplinks** set to **uplink1** |  
| Port group SDDC-DPortGroup-Mgmt | **Port binding** set to **Ephermeral - no binding** and **Load balancing** set to **Route based on originating virtual port** | **Port binding** set to **Static binding** and **Load balancing** set to **Route based on physical NIC load** |  
| Port group SDDC-DPortGroup-External | **Port binding** set to **Ephemeral - no binding** | **Port binding** set to **Static binding** |

## Network MTU configuration settings

The vSphere cluster uses two vSphere Virtual Distributed Switches (VDS), one for public network connectivity and the other one for private network connectivity.

The private network connections are configured to use Jumbo Frames MTU (Maximum Transmission Unit) with the size of 9000, which improves performance for large data transfers such as storage and VMware vMotion. This is the maximum MTU allowed within VMware and by IBM Cloud.

In V2.1 or later, the public network connections use a standard Ethernet MTU of 1500. This setting of 1500 must be maintained; any changes might cause packet fragmentation over the internet.

Review the following table for an overview of the Network MTU configuration settings that are applied to the public and private Distributed Virtual Switch (DVS), depending on whether the vCenter Server instance is deployed in V2.1 or later.

Table 5. MTU configuration settings for vCenter Server instances and clusters depending on the instance version

| VDS | V2.1 or later  | V2.0 or earlier (or upgraded from V2.0 or earlier) |
|:-------------- |:-------------- |:------------- |
| Public Switch  | 1500 (default) | 9000 (Jumbo Frames) |
| Private Switch | 9000 (Jumbo Frames) | 9000 (Jumbo Frames) |

The settings apply to new instances and new clusters from instances deployed in V2.1 or later. The settings also apply to new clusters in cross IBM Cloud Data Centers from instances that were upgraded to V2.1 or later.

The settings do not apply to new clusters in the same IBM Cloud Data Center, for existing instances from V2.0 or earlier or existing instances upgraded to V2.1 or later.

For instances that were deployed in V2.0 or earlier, it is recommended that you update the Public Switch MTU setting to 1500.

### Updating the Public Switch MTU setting

To update the MTU setting for the Public Switch, complete the following steps in the VMware vSphere Web Client:
1. Right-click the VDS and click **Edit Settings**.
2. On the **Properties tab**, select the **Advanced** option.
3. Ensure that the **Maximum MTU** value is set to 1500.

   **Note**: When changing the MTU size in a vDS, the attached uplinks (physical NICs) are brought down and up again. As a result, a brief outage occurs for the VMs that are using the uplink. Therefore, it is recommended to plan the MTU setting update during scheduled downtime.

## Related links

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Enabling Jumbo Frames on virtual distributed switches](https://kb.vmware.com/s/article/1038827)
* [VMware vCenter Server on IBM Cloud Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040)
* [vCenter Server overview](vc_vcenterserveroverview.html)
* [Planning vCenter Server instances](vc_planning.html)
