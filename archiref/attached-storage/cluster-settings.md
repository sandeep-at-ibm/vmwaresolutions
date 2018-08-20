---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# Cluster settings

Before the addition of attached storage, the vCenter Server solution did not enable advanced features such as vSphere Distributed Resource Scheduler (DRS) and vSphere High Availability (HA). With the addition of the NFS attached storage device, these features are enabled on the cluster with the settings that are listed in the following sections.

## vSphere Distributed Resource Scheduler

There are two main features that are enabled when turning on vSphere DRS on a cluster: Load Balancing and Power Management.

### Load Balancing

With load balancing, the distribution and usage of CPU and memory resources for all hosts and virtual machines (VMs) in the cluster are continuously monitored. DRS compares these metrics to an ideal resource utilization given the attributes of the cluster’s resource pools and VMs, the current demand, and the imbalance target. It then performs (or recommends) VM migrations accordingly.

When a VM is first powered on in the cluster, DRS attempts to maintain proper load balancing by either placing the VM on an appropriate host or making a recommendation. The placement or recommendation settings are set in the DRS Automation section of the cluster settings.

In this design, the DRS Automation level is set to fully automated so when VMs are powered on they are automatically placed onto hosts with sufficient capacity. The VMs are also automatically migrated from one host to another to load balance the cluster. Additionally, the migration threshold of the DRS cluster is set at the midpoint between conservative and aggressive such that priority 1, priority 2, and priority 3 recommendations are applied. This means that vCenter Server  provides at least good improvements to the cluster’s load balance.

The following table shows the settings for the vSphere DRS cluster in the VMware vSphere Web Client.

Table 1. DRS Automation settings for the vSphere DRS cluster

| Setting             | Value  |
|:------------------- |:------ |
| Turn ON vSphere DRS | Selected |
| Automation Level | Fully Automated |
| Migration Threshold | Apply priority 1, priority 2, and priority 3 recommendations |
| Enable individual machine automation levels | Selected, set to 15 ms |

For more information about configuring these settings in the vSphere Web Client, see [Set a Custom Automation Level for a Virtual Machine in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-C21C0609-923B-46FB-920C-887F00DBCAB9.html).

In addition to the automation level and migration threshold of the cluster, this design enables VMs automation so that you can set overrides to individual VMs. This allows more granular control of VMs and enables you to further prioritize the load balancing of VMs.

### Power management

When the VMware Distributed Power Management feature is enabled, DRS compares cluster- and host-level capacity to the demands of the cluster’s VMs, including recent historical demand. It places (or recommends placing) hosts in standby power mode if sufficient excess capacity is found or powering on hosts if capacity is needed. Depending on the resulting host power state recommendations, VMs might need to be migrated to and from the hosts as well.
In this design, power management is disabled since there is no operational or financial benefit to powering on and off hosts in the cluster.

## vSphere High Availability

vSphere provides high availability for VMs by pooling them and the hosts they reside on into a cluster. Hosts in the cluster are monitored and in the event of a failure, the VMs on a failed host are restarted on alternate hosts.
In this design, vSphere High Availability is enabled with host monitoring and VM monitoring on the cluster.

### Host monitoring

Host monitoring allows hosts in the cluster to exchange network heartbeats and allows vSphere HA to take action when it detects failures. This feature is enabled in this design.

### Virtual machine monitoring

The VM monitoring feature uses the heartbeat information that VMware Tools captures as a proxy for guest operating system availability. This allows vSphere HA automatically to reset or restart individual VMs that have lost their ability to heartbeat. This design enables both VM and application monitoring.

#### Failure conditions and VM response

The failure conditions define how the VMs fail and the response given to each failure. In this design, the VM restart priority is set to medium; it is highly recommended to review this value and adjust settings accordingly so the restart priority matches the importance of the workload. Additionally, the response for host isolation is set to “Power off and restart VMs” so that VMs are not effected by an isolated host in the cluster. The rest of the values for this setting are set to default.

The following table shows the settings for the vSphere HA cluster in the VMware vSphere Web Client.

Table 2. Failure Conditions and VM Response settings for the vSphere HA cluster

| Setting             | Value  |
|:------------------- |:------ |
| VM restart priority | Medium |
| Response for Host Isolation | Power off and restart VMs |
| Response for Datastore with Permanent Device Loss (PDL) | Disabled |
| Response for Datastore with All Paths Down (APD) | Disabled |
| Response for APD recovery after APD timeout | Disabled |
| VM monitoring sensitivity | Custom |
| Failure interval | 50 s |
| Minimum uptime | 90 s |
| Maximum per-VM resets | 10 |
| Maximum resets time window | Within 1 hrs |

For more information about configuring these settings in the vSphere Web Client, see [Configure Virtual Machine Responses](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.avail.doc/GUID-3DAED2B1-55B8-4877-BD0F-BC57C10A516C.html).

#### Admission control

vCenter Server uses admission control to ensure that sufficient resources are available in a cluster to provide failover protection and to ensure that VM resource reservations are respected. In this design, the failover capacity is reserved by specifying a percentage of the cluster resources. The defined failover capacity is set to 25% CPU and 25% memory.

#### Datastore for Heartbeating

vSphere HA uses datastore heartbeating to distinguish between hosts that have failed and hosts that reside on a network partition. Datastore heartbeating allows vSphere HA to monitor hosts when a management network partition occurs and to continue to respond to failures that occur. In this design, the heartbeat datastore selection policy is set to “Automatically select datastores accessible from the host”.

### Related links

* [Solution overview](../solution/solution_overview.html)
