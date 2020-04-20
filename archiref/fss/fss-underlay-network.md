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

# FSS Cloud underlay networking
{: #fss-underlay-network}

The FSS (Financial Services Sector) Cloud requires isolated networking between the workload clusters and the management and edge services clusters.

## Management cluster
{: #fss-underlay-network-management}

The management cluster requires only a single VLAN with two subnets. The VLAN supports all management functions including management of all ESXi hosts operating in any cluster of the FSS Cloud. The two subnets that are contained within the VLAN are to isolate the ESXi or bare metal host management network and the management software stack that includes the vCenter. By using two subnets, the ESXi or bare metal hosts are isolated, such that the only traffic to and from the systems is through vCenter Server or other dedicated services. Likewise, unsolicited traffic from the ESXi or bare metal hosts is prevented from reaching the management systems. The use of the vSRX running on the edge services cluster controls the traffic flow between these two subnets and from the subnets to any other area outside of the management region.

## Edge cluster
{: #fss-underlay-network-edge}

The edge services cluster adds two transit network VLANs to the solution. These VLANs connect the vSRX to both the BCR for private traffic and FCR for public (internet) traffic flows. When a private-only deployment is wanted, the public transit VLAN is not ordered. The management VLAN is trunked to the edge services cluster. The network design is executed in this manner to enable the vSRX to control traffic flows within the management zone and between the management zone and the IBM Cloud private and public networks.

## Workload cluster
{: #fss-underlay-network-workload}

The workload cluster network design is closely aligned to that of a traditional vCenter Server deployment. VLANs and subnets are provisioned to support vMotion, vSAN, VTEPS for the SDN network, and workload cluster host management functions.

Expanding the workload region might require more VLANs and subnets to support the additional hosts added to the existing cluster or any new clusters.

The edge services cluster does not provide protection to any VLANs or subnets in the workload region except for the management VLAN that originates from the management region.

The use of a gateway device to control traffic flows within the workload region and between the workload region and the IBM Cloud public and private networks is recommended.

**Next topic**: [FSS Cloud clusters](/docs/vmwaresolutions?topic=vmware-solutions-fss-compute-clusters)

## Related links
{: #fss-underlay-network-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
