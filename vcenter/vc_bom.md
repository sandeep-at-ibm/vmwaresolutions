---

copyright:

  years:  2016, 2020

lastupdated: "2020-08-20"

keywords: vCenter Server BOM, bill of materials vCenter Server, BOM

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server Bill of Materials
{: #vc_bom}

Review the Bill of Materials (BOM) information for VMware vCenter Server instances.

## VLANs BOM for vCenter Server instances
{: #vc_bom-vlans}

The following table details the BOM information for the vCenter Server VLANs.

| VLAN       | Type       | Details       |
|:---------- |:---------- |:------------- |
| VLAN1     | Public, Primary | Assigned to physical ESXi servers for public network access. The servers are assigned a public IP address but this IP address is not configured on the servers, so they are not directly accessible on the public network. Instead, the public VLAN is intended to provide public internet access for other components, such as NSX Edge Services Gateways (ESGs). |
| VLAN2     | Private A, Primary | Assigned by {{site.data.keyword.cloud}} to physical ESXi servers. Used by the management interface for VMware vSphere management traffic.<br><br>Assigned to VMs (virtual machines) that function as management components.<br><br>For NSX-T, assigned to VMware NSX VTEP (VXLAN Tunnel Endpoint) |
| VLAN3     | Private B, Portable | Assigned to VMware vSAN, if used.<br><br>Assigned to VMware NFS, if used.<br><br>Assigned to VMware vSphere vMotion.<br><br>For NSX-T, assigned to VMware NSX VTEP (VXLAN Tunnel Endpoint).|
{: caption="Table 1. BOM for the VLANs in vCenter Server instances" caption-side="top"}

## Software BOM for vCenter Server instances
{: #vc_bom-software}

The following table details the BOM information for vCenter Server software components.

| Manufacturer | Component                       | Version       |
|:------------ |:------------------------------- |:------------- |
| VMware       | vSphere ESXi                    | 6.7 EP 15 (build 6.7.0-16316930) or <br/>ESXi 6.5 P04 (build 6.5.0-15256549) |
| VMware       | vSphere 6.7                     | Distributed vSwitch 6.6.0 |
| VMware       | vSphere 6.5                     | Distributed vSwitch 6.5.0 |
| VMware       | vCenter Server Appliance        | 6.7 Update 3g (6.7.0-16046470) or <br/>6.5 Update 3i (build 6.5.0-15808842) |
| VMware       | vSAN[^vsan]                     | 6.7 EP 10 or<br> 6.6.1 Patch 04 |
| VMware       | NSX for vSphere[^nsxv]          | 6.4.6 (build 14819921) |
| VMware       | NSX-T for vSphere[^nsxt]        | 3.0.1 (build 16404476) |
| Microsoft    | Windows Server Standard edition | 2019 |
| Microsoft    | Active Directory domain functional level | 2016 (WinThreshold)[^domain] |
{: caption="Table 2. BOM for the software components in vCenter Server instances" caption-side="top"}

[^vsan]: VMware vSAN is an optional component. The vSphere ESXi 6.5 P04 (build 6.5.0-15256549) update is applicable only to 6.5u3 hosts and not to 6.5u2 hosts. The vSphere ESXi 6.7 EP10 (build 6.7.0-13981272) update is applicable to 6.7u2 hosts.

[^nsxv]: vCenter Server with NSX-V only

[^nsxt]: vCenter Server with NSX-T only

[^domain]: The domain functional level 2016 is set to allow for compatibility with an earlier version. For more information, see [Domain controllers](/docs/vmwaresolutions?topic=vmwaresolutions-adds-infra-domain#adds-infra-domain-controllers).

## Advanced configuration settings for ESXi servers
{: #vc_bom-esxi-server-advance-config}

Review the following table for an overview of the advanced configuration settings that are applied to ESXi servers. These settings depend on whether the vCenter Server instance is deployed in V2.2 or later, or upgraded to V2.2 or later from V2.1 or earlier.

The settings apply to new instances and new clusters in new instances V2.2 or later. The settings don't apply to new clusters in existing instances from V2.1 or earlier or existing instances that are upgraded to V2.2 or later.

| Configuration setting | If newly deployed in V2.2 or later  | If upgraded from V2.1 or earlier |
|:------------- |:------------- |:------------- |
| Maximum of Volumes | **MaxVolumes** = 256 | Both **/NFS/MaxVolumes** and **/NFS41/MaxVolumes** = 256 |
| Heartbeat Maximum Failures | **HeartbeatMaxFailures** = 10 | Not set |
| Heartbeat Frequency | **HeartbeatFrequency** = 12 | Not set |
| Heartbeat Timeout | **HeartbeatTimeout** = 5 | Not set |
| Maximum Queue Depth | **MaxQueueDepth** = 64 | Not set |
| Queue Full Sample Size | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Queue Full Threshold | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |
| TCP/IP Heap Size | **TcpipHeapSize** = 32 | Not set |
| TCP/IP Heap Maximum | **TcpipHeapMax** = 1536 | Not set |
{: caption="Table 3. ESXi servers advanced configuration settings for vCenter Server instances and clusters before and after V2.2" caption-side="top"}

### Notes
{: #vc_bom-notes}

* The **MaxVolumes** setting is required for the IBM Spectrum Protect&trade; Plus service because the service might use more than the default number of NFS mounts on the ESXi server.
* A value of **Not set** for a configuration setting indicates that the new setting is not automatically applied because it requires rebooting the ESXi servers, which might be disruptive.

  It is recommended that you change the **Not set** configuration settings to the new values for consistency across all instances and to allow adequate support for storage expansion. IBM plans to test only with these new settings for all {{site.data.keyword.vmwaresolutions_short}} V2.2 and later releases.

  For more information, see [Increasing the default value that defines the maximum number of NFS mounts on an ESXi host](https://kb.vmware.com/s/article/2239){:external}.

Review the following table for an overview of the advanced configuration settings that are applied to ESXi servers. For V3.6 or later releases, new instances are ordered with a new set of advanced configuration settings for ESXi servers.

| Configuration setting | If newly deployed in V3.6 or later  | If upgraded from V3.5 or earlier |
|:------------- |:------------- |:------------- |
| Block guest sourced BPDU frames | **Net.BlockGuestBPDU** = 1 | **Net.BlockGuestBPDU** = 0 |
| Duration, in seconds, to lock out a user's account after it exceeds the maximum allowed failed login attempts. | **Security.AccountUnlockTime** = 1800 | **Security.AccountUnlockTime** = 900 |
| Maximum allowed failed login attempts before a user's account is locked out. Zero disables account locking. | **Security.AccountLockFailures** = 6 | **Security.AccountLockFailures** = 5 |
{: caption="Table 4. ESXi servers advanced configuration settings for vCenter Server instances and clusters before and after V3.6" caption-side="top"}

Starting in V3.6, ESXi servers join Active Directory domain for authentication. Also, the ESXi shell service is stopped instead of running.

## NSX and port group configuration settings
{: #vc_bom-nsx-port-group-config}

Review the following table for an overview of the VMware NSX and port group configuration settings for vCenter Server instances, and the differences between releases.

The settings apply to new instances and new clusters in new instances V2.2 or later. The settings do not apply to new clusters in existing instances from V2.1 or earlier or existing instances that are upgraded to V2.2 or later.

| Configuration setting | V2.1 or earlier  | V2.2 or later |   
|:------------- |:------------- |:------------- |
| NSX VXLAN cluster teaming policy | Fail Over | Load Balance - SRCID |
| NSX VXLAN cluster VTEP | 1 | 2 |
| Segment ID pool for primary instance | 6000-8000 | 6000-7999 |  
| Segment ID pool for subsequent secondary instance or instances | 6000-8000 | Previous end range in the multi-site configuration + 1 to the previous end range in the multi-site configuration + 2000 |  
| Port group SDDC-DPortGroup-VSAN (if applicable) | **Active uplinks** set to **uplink1** and **Standby uplinks** set to **uplink2** | **Active uplinks** set to **uplink2** and **Standby uplinks** set to **uplink1** |  
| Port group SDDC-DPortGroup-Mgmt | **Port binding** set to **Ephemeral - no binding** and **Load balancing** set to **Route based on originating virtual port** | **Port binding** set to **Static binding** and **Load balancing** set to **Route based on physical NIC load** |  
| Port group SDDC-DPortGroup-External | **Port binding** set to **Ephemeral - no binding** | **Port binding** set to **Static binding** |
{: caption="Table 5. NSX and port group configuration settings for vCenter Server instances" caption-side="top"}

Starting in V3.6, security policies for promiscuous mode, MAC address changes, and forged transmits are now accepted on distributed port groups.

## Network MTU configuration settings
{: #vc_bom-network-mtu-config}

The vSphere cluster uses two vSphere Distributed Switches (vDS), one for public network connectivity and the other one for private network connectivity.

The private network connections are configured to use Jumbo Frames MTU (Maximum Transmission Unit) with the size of 9000, which improves performance for large data transfers such as storage and VMware vMotion. This value is the maximum MTU allowed within VMware and by {{site.data.keyword.cloud_notm}}.

In V2.1 or later, the public network connections use a standard Ethernet MTU of 1500. This setting of 1500 must be maintained; any changes might cause packet fragmentation over the internet.

Review the following table for an overview of the Network MTU configuration settings that are applied to the public and private Distributed Virtual Switch (DVS).

| vDS | V2.1 or later  | V2.0 or earlier (or upgraded from V2.0 or earlier) |
|:-------------- |:-------------- |:------------- |
| Public switch  | 1500 (default) | 9000 (Jumbo Frames) |
| Private switch | 9000 (Jumbo Frames) | 9000 (Jumbo Frames) |
{: caption="Table 6. MTU configuration settings for vCenter Server instances and clusters depending on the instance version" caption-side="top"}

The settings apply to new instances and new clusters from instances that are deployed in V2.1 or later. The settings also apply to new clusters in cross {{site.data.keyword.cloud_notm}} data centers from instances that were upgraded to V2.1 or later.

The settings do not apply to new clusters in the same {{site.data.keyword.cloud_notm}} data center, for existing instances from V2.0 or earlier or existing instances upgraded to V2.1 or later.

For instances that were deployed in V2.0 or earlier, it is recommended that you update the public switch MTU setting to 1500.

### Updating the public switch MTU setting
{: #vc_bom-procedure-update-public-switch-mtu-setting}

To update the MTU setting for the public switch, complete the following steps in the VMware vSphere Web Client:
1. Right-click the vDS and click **Edit Settings**.
2. On the **Properties** tab, select the **Advanced** option.
3. Ensure that the **Maximum MTU** value is set to 1500.

   When the MTU size in a vDS is changed, the attached uplinks (physical NICs) are brought down and up again. As a result, a brief outage occurs for the VMs that are using the uplink. Therefore, it is recommended to plan the MTU setting update during scheduled downtime.
   {:note}

## Distributed switch allocation
{: #vc_bom-network-dswitch-allocation}

The allocation of distributed switches varies if you have existing instances and clusters. Review the following considerations for switch creation when you create a cluster:

* If there are one or more existing clusters in the same pod that uses distributed switches named ``SDDC-DSwitch-Private`` and ``SDDC-DSwitch-Public``, your new cluster uses the same switches as the existing cluster.
* If one or more existing clusters are in the same pod, and the pod uses distributed switches that are named by using the same name as the pod (rather than named by using the same name as the cluster), your new cluster uses the same switches as the existing cluster.
* If there are no existing clusters in the same pod, or all clusters in that pod have distributed switches that are named by using the same name as the cluster rather than the pod, then your new cluster is configured with the new switch whose name is based only on the pod.

## Enhanced VMware vMotion Compatibility (EVC) mode settings
{: #vc_bom-evc-mode-settings}

Review the following table for an overview of the EVC mode settings for vCenter Server instances and the differences between vSphere versions.

| Bare metal server CPU model | vSphere 6.5  | vSphere 6.7 |
|:------------- |:------------- |:------------- |
| Skylake | EVC is set to Intel **Broadwell** Generation | EVC is set to Intel **Skylake** Generation. |
| Cascade Lake[^vsphere] | For the management cluster, EVC is not set. For all other clusters, EVC is set to Intel **Broadwell** Generation. | For the management cluster, EVC is not set. For all other clusters, EVC is set to Intel **Skylake** Generation. |
{: caption="Table 7. EVC mode settings for vCenter Server instances and clusters" caption-side="top"}

[^vsphere]: For instances with vSphere 6.5, Cascade Lake supports 6.5u3 only.

## Related links
{: #vc_bom-related}

* [Build numbers and versions of VMware ESXi and ESX (2143832)](https://kb.vmware.com/s/article/2143832){:external}
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838){:external}
* [Enabling Jumbo Frames on virtual distributed switches](https://kb.vmware.com/s/article/1038827){:external}
* [{{site.data.keyword.vmwaresolutions_short}} Protection data sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040){:external}
* [vCenter Server overview](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)
* [Planning vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning)
