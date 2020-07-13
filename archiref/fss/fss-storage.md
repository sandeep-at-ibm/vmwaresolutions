---

copyright:

  years:  2020

lastupdated: "2020-07-10"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Storage
{: #fss-storage}

The IBM Cloud for VMware Regulated Workloads employs multiple storage types.

## Management cluster
{: #fss-storage-management}

The management cluster storage is vSAN. Security requirements mandate that multi-tenant shared storage is not permissible and in such cases the use of vSAN is necessary. Shifting storage to vSAN mandates deploying a minimum of four ESXi hosts to the management cluster. Where the ISV is willing to accept more operational risk the use of NFS shared storage and Cloud Object Storage is available.

## Edge cluster
{: #fss-storage-edge}

The edge services cluster uses only local data stores. Local data stores are suited to support the vSRX nodes since they do not require any vSphere DRS functions. The resiliency of the vSRX HA cluster is a function of the clustering mechanism that is used by the vSRX and is not reliant on the underlying hosts.

## Workload cluster
{: #fss-storage-workload}

The workload clusters require the use of vSAN. vSAN is the only storage option on IBM Cloud that keeps all workload data within the account and delivers resiliency to the applications deployed to the workload clusters. All workload clusters are formed by using a minimum of four ESXi hosts to meet vSAN requirements.

## Bare metal storage design
{: #fss-storage-bare-metal}

Physical storage design consists of the configuration of the physical disks that are installed in the physical hosts and the configuration of the shared network-attached storage. This includes the operating system (vSphere ESXi) and the disks that are used for storage of the virtual machines (VMs). Storage for VMs consists of local disks that are virtualized by VMware vSAN. Cloud Object Storage is available in Q4.

![Storage options](../../images/fss-storage-connections.svg "Storage Options"){: caption="Figure 1. Storage options" caption-side="bottom"}

### Operating system disks
{: #fss-storage-os-disks}

The vSphere ESXi hypervisor is installed in a persistent location. As a result, the physical hosts boot drive consists of two disks in a RAID–1 configuration to support redundancy for the vSphere ESXi hypervisor.

### vSAN disks
{: #fss-storage-vsan-disks}

This design allows for the option of using either VMware vSAN or shared network-attached storage (an option for the management layer only) as the primary data store for virtual machines. For VMware vSAN, it is configured by using an all–flash configuration. This design allows for several configuration options, including 2U and 4U chassis, various numbers of disks, and various disk sizes.

All configurations use two vSAN disk groups of solid-state disks (SSD):
* Two disks for cache tier (one per disk group)
* Two or more SSDs for capacity tier (one or more per disk group, drive counts must match in each disk group)

All drives that are allocated for vSAN consumption are configured in single-disk RAID-0.

**Next topic**: [Underlay networking](/docs/vmwaresolutions?topic=vmwaresolutions-fss-underlay-network)

## Related links
{: #fss-storage-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
