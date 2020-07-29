---

copyright:

  years:  2020

lastupdated: "2020-07-28"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust integration
{: #fss-hytrust}

IBM Cloud for VMware® Regulated Workloads requires HyTrust CloudControl (HTCC) for identity and access management. HTCC enables fine grained role-based access control with capability of forensic auditing for all actions that are taken by any privileged user.

## Management cluster
{: #fss-hytrust-management}

Identity and access management for administrators of the IBM Cloud for VMware Regulated Workloads infrastructure is handled by HTCC and Microsoft® Active Directory servers. CloudControl uses the AD to authenticate the administrator but handles the authorization of privileged users internally.

### HyTrust CloudControl
{: #fss-hytrust-management-cloudcontrol}

HyTrust CloudControl (HTCC) enables unified security policies for access to the management stack, unified visibility to security configuration and context, and continuous compliance by using templates to enforce segregation of duties. It also provides a robust audit trail that includes a full record of all actions that are attempted by security, network, and compute platform administrators. HTCC also simplifies compliance with administrative controls requirements in HIPAA, PCI, FedRAMP, CJIS, and other regulations.

![HyTrust CloudControl transparent proxy](../../images/fss-transparent-proxy.svg "HyTrust CloudControl transparent proxy"){: caption="Figure 1. HyTrust CloudControl transparent proxy" caption-side="bottom"}

#### HyTrust CloudControl architecture
{: #fss-hytrust-management-cloudcontrol-architecture}

HTCC is composed of many internal functional components:

- Transparent proxy – provides the proxy functions for requests to vCenter and ESXi. This same mechanism is used for vSphere Client, vSphere Web Client, and even SSH to ESXi hosts.
- Policy engine – enforces security policies that are created by the security administrators.
- Authentication engine – uniform authentication policy, which integrates with Active Directory or LDAP, and it applies multi-factor authentication policy.
- Inventory engine – keeps a synchronized inventory of vCenter objects and determines the trust level for ESXi hosts.
- Compliance engine – performs configuration assessments and remediation.
- Logging – Logs every action, regardless of whether it was performed or denied by policy, and, if configured, forwards to syslog server or SIEM tool. Forwarding of logging to vRealize Log Insight is required.

![IBM Cloud for VMware Regulated Workloads HyTrust integration](../../images/fss-htcc.svg "IBM Cloud for VMware Regulated Workloads HyTrust integration"){: caption="Figure 2. IBM Cloud for VMware Regulated Workloads HyTrust integration" caption-side="bottom"}

All access is through HyTrust CloudControl and no direct access to the ESXi hosts is enabled. The network is designed to allow only the necessary connections from the vCenter Server. Lockdown mode is enabled. Allowlisting of IP addresses permitted network access to the ESXi hosts is configured in the integrated host firewall. The rules on the gateway further enforce limited traffic flows from the vCenter Server to the subnets upon which the ESXi hosts are deployed. The cloud account administrator (through IBM Cloud IAM) should not authorize VPN connections to the subnets upon which the ESXi hosts are deployed except for the connections that are essential to support DR recovery operations.

## Edge cluster
{: #fss-hytrust-edge}

The ESXi host access is strictly limited. No direct access to an ESXi host is permissible. The gateway appliance uses only local accounts and is configured to forward all logs to vRealize Log Insight. These logs can contain authentication failure and success events for full visibility into the activities taken that might impact security or compliance status. HyTrust does not play a role in authentication or authorization for access to the gateway appliance. The host level firewall is also configured with allowlisted IPs to permit required network traffic.

## Workload cluster
{: #fss-hytrust-workload}

The ESXi host access is strictly limited. No direct access to an ESXi host is permissible. HTCC provides the same level of access control and auditing for administrators who are assigned to manage the dedicated workload infrastructure, such as the SDN (NSX-T). The fine-grained RBAC capability of HTCC limits their scope of action to the workload region. The host level firewall is also configured with allowlisted IPs to permit required network traffic.

**Next topic**: [Active Directory](/docs/vmwaresolutions?topic=vmwaresolutions-fss-iam-active-directory)

## Related links
{: #fss-hytrust-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)
* [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto)
