---

copyright:

  years:  2020

lastupdated: "2020-04-15"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FSS Cloud vSphere components
{: #fss-vsphere-platform}

The FSS (Financial Services Sector) Cloud is built with vSphere technology, this includes the ESXi hypervisors and a vCenter appliance.

## Management cluster
{: #fss-vsphere-platform-management}

The single vCenter with embedded PSC (platform services controller) appliance provides management of the entire FSS Cloud virtualized compute infrastructure and management of any vSAN(s) operating in the management or workload clusters.

The vCenter appliance provides the necessary interfaces to the virtualization administrators, which include a robust RESTful API. Resilience of the vCenter appliance is delivered by using vSphere native DRS functions such as vMotion. More management components are deployed to the management cluster but only the vCenter appliance is responsible for direct operation of the platform.

## Edge cluster
{: #fss-vsphere-platform-edge}

No vSphere management components are deployed to the edge cluster.

## Workload cluster
{: #fss-vsphere-platform-workload}

No vSphere management components are deployed to the workload cluster.

**Next topic**: [FSS Cloud operations management](/docs/vmwaresolutions?topic=vmwaresolutions-fss-operations)

## Related links
{: #fss-vsphere-platform-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
