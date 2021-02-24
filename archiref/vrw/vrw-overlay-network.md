---

copyright:

  years:  2020, 2021

lastupdated: "2021-02-23"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}

# Overlay networking
{: #vrw-overlay-network}

{{site.data.keyword.cloud_notm}} for VMware® Regulated Workloads uses NSX-T as the software defined network overlay provider.

## Management cluster
{: #vrw-overlay-network-management}

The management cluster uses VLANs only to support the requirements of the management services. No overlay networking is enabled on the management cluster.

## Edge services cluster
{: #vrw-overlay-network-edge}

The optional edge services cluster does not employ any overlay networking and a physical FortiGate appliance is available to serve as the perimeter gateway in its place.

The vSRX running on the edge services cluster connects the management network to the private and public transit networks. The vSRX is configured to allow only traffic in or out of the management region that is necessary for proper operation and monitoring of the environment. The vSRX also isolates all traffic between the clusters' ESXi hosts and the vCenter Server. ESXi hosts within a cluster can communicate with each other and the vCenter Server. ESXi hosts in one cluster (workload or management for example) are unable to communicate with the hosts of any other clusters. The limitation of cross-cluster traffic is enforced by the vSRX and the configuration of the ESXi hosts' own firewalls.

The edge services cluster is the peering point for traffic between the on-premises SaaS provider and {{site.data.keyword.cloud_notm}} for VMware® Regulated Workloads. It also serves as the demarcation for traffic from the SaaS consumer. The SaaS provider uses vSRX as the secure tunnel endpoint for its VPN.

Traffic from the SaaS consumer passes through the vSRX in an encrypted tunnel, which lands on the overlay network virtual edge device.

## Workload cluster
{: #vrw-overlay-network-workload}

![Workload cluster overlay network](../../images/vrw-workload-overlay.svg "Workload cluster overlay network"){: caption="Figure 1. Workload cluster overlay network" caption-side="bottom"}

The workload cluster network design requires both the overlay network that is delivered with NSX-T and two or more VLANs to support the infrastructure layer functions.

Traffic from the SaaS consumer is peered with the overlay network virtual edge. It is the virtual edge that the SaaS consumer uses as the secure tunnel end point to establish an encrypted VPN.

![Workload cross account network](../../images/vrw-bank-to-isv.svg "Workload cross account network"){: caption="Figure 2. Workload cross account network" caption-side="bottom"}

**Next topic**: [Multizone region](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-mzr)

## Related links
{: #vrw-overlay-network-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
