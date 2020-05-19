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

# FSS Cloud overlay networking
{: #fss-overlay-network}

The FSS (Financial Services Sector) Cloud uses NSX-T as the software defined network overlay provider.

## Management cluster
{: #fss-overlay-network-management}

The management cluster requires only the use of VLANs to support the requirements of the management services. No overlay networking is enabled on the management cluster.

## Edge cluster
{: #fss-overlay-network-edge}

The edge services cluster does not employ any overlay networking. The vSRX running on the edge cluster connects the management network to the private and public transit networks. The vSRX is configured to allow only traffic into or out of the management region that is necessary for proper operation and monitoring of the environment.

## Workload cluster
{: #fss-overlay-network-workload}

The workload cluster network design requires both the overlay network that is delivered with NSX-T and two or more VLANs to support the infrastructure layer functions.

Expanding the workload region might require more VLANs and subnets to support the additional hosts that are added to the existing cluster or any new clusters.

The edge services cluster does not provide protection to any overlay network segments, including any transit networks that move traffic in to and out of the overlay network.

The use of a gateway device to control traffic flows within the workload region and between the workload region and the IBM Cloud public and private networks is recommended.

**Next topic**: [FSS Cloud vSphere components](/docs/vmwaresolutions?topic=vmwaresolutions-fss-vsphere-platform)

## Related links
{: #fss-overlay-network-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
