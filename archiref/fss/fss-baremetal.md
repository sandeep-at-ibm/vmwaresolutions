---

copyright:

  years:  2020

lastupdated: "2020-03-04"

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FSS Cloud Bare Metal hosts
{: #fss-baremetal}

The FSS (Financial Services Sector) Cloud is built upon multiple clusters of bare metal hosts with ESXi as the hypervisor.

## Management cluster
{: #fss-baremetal-management}

The management cluster has three or four bare metal hosts. Configuring the cluster with four hosts is mandatory when vSAN is selected as the storage platform. These hosts are sized to meet the requirements of the management applications. No workloads are run in the management cluster.

## Edge cluster
{: #fss-baremetal-edge}

The edge services cluster requires only two bare metal hosts. vSAN is not an available storage option. NFS is not required since use of local datastore is preferred. The hosts are sized to support the requirements of the virtual router or gateway appliance that is deployed to the individual hosts.

## Workload cluster
{: #fss-baremetal-workload}

The workload cluster uses vSAN for storage and thus a minimum of four bare metal hosts with ESXI as the hypervisor are required. More hosts are added as necessary to support the required compute, memory, and storage needs of the customer applications.

If you require dedicated resources for an application or business unit, you can deploy additional workload clusters.

**Next topic**: [FSS Cloud storage](/docs/services/vmwaresolutions?topic=vmware-solutions-fss-storage)

## Related links
{: #fss-baremetal-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
