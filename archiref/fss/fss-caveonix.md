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

# FSS Cloud Caveonix integration
{: #fss-caveonix}

The FSS (Financial Services Sector) Cloud requires Caveonix RiskForesight for continuous compliance monitoring. The FSS Cloud architecture is designed to enable ease of compliance to NIST and other necessary compliance certifications as required of the client that uses the FSS Cloud offering.

## Management cluster
{: #fss-caveonix-management}

[Caveonix RiskForesight](https://www.caveonix.com/) provides a comprehensive cloud workload protection platform for FSS Cloud that delivers a common Risk Management Control Plane (RMCP) for continuous and proactive protection of management and edge workloads.

With the RMCP, you maintain continuous and real-time visibility into workload deployments at scale, incorporating the latest cyberthreats and regulatory compliance needs, evaluating workload-specific cyber and compliance risks, and providing proactive defense by using agentless enforcement at network, security, and compute control planes of deployment.

RiskForesight’s unique Risk Management Control Plane (RMCP) interface slashes or eliminates needless security blind spots and compliance gaps, restoring customers’ risk visibility and confidence in compliant deployments.

## Edge cluster
{: #fss-caveonix-edge}

Caveonix RiskForesight is used to continuously monitor compliance of the edge cluster as it does for the management cluster.

## Workload cluster
{: #fss-caveonix-workload}

Caveonix RiskForesight can optionally monitor compliance of client workloads. Enabling the use of RiskForesight for workload compliance monitoring requires appropriate rules and policies on both the edge security appliance that protects the management plane and the perimeter security appliance that protects the client workloads.

**Next topic**: [FSS Cloud business continuity](/docs/vmwaresolutions?topic=vmware-solutions-fss-budr)

## Related links
{: #fss-caveonix-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
* [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmware-solutions-caveonix_considerations)
