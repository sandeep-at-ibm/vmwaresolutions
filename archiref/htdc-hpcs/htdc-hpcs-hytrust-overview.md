---

copyright:

  years:  2019, 2020

lastupdated: "2020-12-10"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust Workload Security Platform overview
{: #htdc-hpcs-hytrust-overview}

The HyTrust® Workload Security Platform consists of the following products:

* HyTrust KeyControl™ - HyTrust KeyControl (HTKC) serves as a Key Management Server for VMware vSphere and vSAN encrypted clients, or other products that support KMIP. HTKC manages the encryption keys for virtual machines (VMs) and encrypted data stores and can scale to support thousands of encrypted workloads in large deployments. The following key features are included:
    * VMware certified Key Management Server (KMS) for:
      * vSphere 6.5, 6.7, and 7.0
      * vSAN 6.6, 6.7, and 7.0
      * vSphere Trust Authority 7.0
    * Highly Availability (HA) active- active deployments and clustering.
    * Initial implementation of a 2-Node KeyControl cluster, but can be extended to up to four KeyControl Nodes in a cluster.
    * FIPS 140-2 Level 1 validated. FIPS 140-2 Level 3 compliance by using HSM support.
    * Pre-integration with Intel TXT/TPM for hardware host attestation.
    * Upgradeable to HyTrust DataControl for complete, multi-cloud workload encryption.
* HyTrust DataControl - HyTrust DataControl (HTDC) is an encryption and key management solution. The following key features are included:
    * Includes HTKC.
    * FIPS 140-2 Level 1 certified or FIPS 140-2 Level 3 support with HSM.
    * KMIP support.
    * Dashboard and log based forensic analytics.
    * Role-based access control (RBAC) for administrative controls over policy and key access.
    * Cross-cloud key management.
    * Pre-integration with HyTrust CloudControl™ (HTCC) and HyTrust BoundaryControl to provide automated data geo-fencing for workloads.
    * File/folder level encryption on selected operating systems.
    * Pre-integration with Intel TXT/TPM for hardware host attestation.
* HyTrust CloudControl - HyTrust CloudControl provides a number of security and policy enhancements to VMware vSphere.​ HTCC is deployed as a transparent proxy. It mediates the actions that are taken by VMware administrators by approving actions that are allowed, disapproving actions that are blocked, and requesting additional approval if enabled. The following key features are included:
    * Policy-based protection for the hypervisor, VMs, and data.
    * Continuous monitoring of hypervisor and VMs for security and compliance.
    * One-click security and compliance remediation on vulnerable VMs.
    * Visibility of the security state, configurations, administrator actions, and compliance for VMs.
    * HyTrust BoundaryControl prevent VMs from being moved from a designated host or onto a host that does not have acceptable security policy by enforcing data policy based on software tags or by using Intel TXT.
* HyTrust CloudAdvisor - Data discovery and classification across VMs and backups.

This reference architecture uses HyTrust DataControl.

**Next topic:** [IBM Hyper Protect Crypto Services overview](/docs/vmwaresolutions?topic=vmwaresolutions-htdc-hpcs-hpcs-overview)

## Related links
{: #htdc-hpcs-hytrust-overview-related}

* [HyTrust CloudControl overview](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [HyTrust DataControl overview](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)
* [HyTrust KeyControl overview](/docs/vmwaresolutions?topic=vmwaresolutions-htkc_considerations)
