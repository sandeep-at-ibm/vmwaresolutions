---

copyright:

  years:  2020

lastupdated: "2020-03-30"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FSS Cloud clusters
{: #fss-compute-clusters}

The FSS (Financial Services Sector) Cloud is built upon multiple clusters of bare metal hosts with ESXi as the hypervisor.

## Management cluster
{: #fss-compute-clusters-management}

The management cluster consists of three or four ESXi hosts. Configuring the cluster with four hosts is mandatory when vSAN is selected as the storage platform. These hosts are sized to meet the requirements of the management applications. No workloads are run in the management cluster.

Shared storage is recommended to provide resiliency to the management services VMs. The use of shared storage and vSphere DRS enables rapid recovery of management VMs if an underlying ESXi host is lost.
Local storage is also supported where dictated by security and compliance controls. However, recovery might require manual intervention.

## Edge cluster
{: #fss-compute-clusters-edge}

The edge services cluster requires only two ESXi hosts. vSAN is not an available storage option. NFS is not required since use of local datastore is preferred. The hosts are sized to support the requirements of the virtual router or gateway appliance that is deployed to the individual hosts.

Each host runs a single vSRX node. The vSRX nodes (node0 & node1) are configured as a highly available cluster above the hypervisor layer. No vSphere DRS services are implemented. Affinity rules are set to pin the vSRX nodes to their respective ESXi host.

## Workload cluster
{: #fss-compute-clusters-workload}

The workload cluster uses vSAN for storage and thus a minimum of four bare metal hosts with ESXi as the hypervisor are required. More hosts are added as necessary to support the required compute, memory, and storage needs of the customer applications.

If wanted, more workload clusters can be added to support applications or to provide dedicated resources to satisfy business or compliance requirements.

**Next topic**: [FSS Cloud overlay networking](/docs/vmwaresolutions?topic=vmwaresolutions-fss-overlay-network)

### Related links
{: #fss-compute-clusters-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
