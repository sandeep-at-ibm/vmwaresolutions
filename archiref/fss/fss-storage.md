---

copyright:

  years:  2020

lastupdated: "2020-03-30"

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FSS Cloud storage
{: #fss-storage}

The FSS (Financial Services Sector) Cloud employs multiple storage types.

## Management cluster
{: #fss-storage-management}

The management cluster storage is typically NFS. Security requirements might mandate that shared storage is not permissible and in such cases the use of vSAN is necessary. Shifting storage to vSAN mandates deploying a minimum of four ESXi hosts to the management cluster. Where the customer is willing to accept additional operational risk, local datastores are usable however this inhibits vSphere DRS functions.

## Edge cluster
{: #fss-storage-edge}

The edge services cluster uses only local datastores. Local datastores are suited to support the vSRX nodes since they do not require any vSphere DRS functions. The resiliency of the vSRX HA cluster is a function of the clustering mechanism that is used by the vSRX and is not reliant on the underlying hosts.

## Workload cluster
{: #fss-storage-workload}

The workload clusters require the use of vSAN. vSAN is the only storage option on IBM Cloud that keeps all workload data within the account and delivers resiliency to the applications deployed to the workload clusters. All workload clusters are formed by using a minimum of four ESXi hosts to meet vSAN requirements.

**Next topic**: [FSS Cloud underlay networking](/docs/vmwaresolutions?topic=vmware-solutions-fss-underlay-network)

## Related links
{: #fss-storage-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
