---

copyright:

  years:  2019

lastupdated: "2019-12-19"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server encryption options
{: #htdc-hpcs-encryption-options}

Enterprises that require encrypted data at rest on their vCenter Server instance have the following options:

* IBM Cloud Endurance native encryption - this option uses IBM-managed keys, so is not suitable for clients that require either Bring Your Own Key (BYOK) or Keep Your Own Key (KYOK). The encryption scope is the complete NFS volume.
* vSAN encryption - This option requires the use of a key management server such as the following, the encryption scope are the vSAN disks:
  * IBM KeyProtect (IBM KP) service for customers who require BYOK, along with the KMIP for VMware service.
  * IBM Hyper Protect Crypto Services (IBM HPCS), for customers who require KYOK, with the KMIP for VMware service.
  * HyTrust Key Control (HTKC) on IBM Cloud.
  * A manually installed solution such as IBM Security Key Lifecycle Manager (SKLM). This solution can also use IBM Cloud HSMs.
* vSphere encryption - This option requires the use of a key management server. However, the encryption scope is the virtual machine disks.
* HyTrust DataControl encryption - This option uses the HTKC key management server and Policy Agent, both components of HyTrust DataControl (HTDC). This option can now also use IBM HPCS to deliver KYOK. The encryption scope includes Windows or Linux virtual machine disks, files, or file systems.

The use of IBM KP or IBM HPCS allows:
* Bring Your Own Key (BYOK) - Allows the customer to bring their keys to the cloud and manage them using a multi-tenant key management service, IBM KP.
* Keep Your Own Key (KYOK) - The customer keeps their keys protected with a single-tenant key management service, IBM HPCS, with built-in customer-controlled FIPS 140-2 Level 4 Hardware Security Modules (HSM), which provides control and authority over encryption keys.

This reference architecture is based on the HTDC and IBM HPCS option, and the following table compares this option against vSAN and vSphere encryption.

| Item | HTDC | vSphere Encryption | vSAN Encryption | Notes |
| ---- | ---- | ------------------ | --------------- | ----- |
| Encryption travels with VM  | Yes | No. VM migrations to other data stores are in clear text. | Limited, not across vCenters | Critical for VMs that are mobile, especially across physical locations or public cloud providers. You don't know and can't trust the networks in-between. |
| Encryption scope | VM | Data Store only | Hypervisor only | The higher up the stack encryption occurs, the higher the security level/fewer attack vectors. |
| Workload boot/ clone protection | Yes | No | No | Ensures cloned workloads. VMs don't work unless authorized. |
| Encrypted backups | Yes | No | No | Automatic encryption for backed up VMs (via VMware or other backup providers). |
| Encryption Granularity | per VM | Per vSAN cluster | Per VM | More granularity provides more secure deployment options. |
| Dedupe/compression | Single-Encryption Key | Flash storage only |  | De-duplication reduces storage requirements but hybrid storage is less expensive. |
| Encrypt/rekey without downtime | Yes | No | No | Frequent rekeying is fundamental to security compliance. HyTrust can perform rekeying  automatically, while VMs continue to run. |
| Secure workload mobility On-premises | vSphere/VSAN/Bare Metal/Any Hypervisor | Within the vSAN cluster only | Within vSphere only | With HyTrust, policies follow the workload across any platform. |
| Secure workload mobility public cloud | AWS, Azure, IBM | No | No | Operational simplicity: one solution for encryption across all platforms, less chance of mistakes. |
| Transparency | Fully transparent | Limited | Limited | vSphere and VSAN provide limited visibility into clones and snapshots. |
| Geo-Fencing (GDPR) | Yes | No | No | HyTrust BoundaryControl integration |
| NIST/PCI compliant live rekey | Yes | No | No | Allows NIST-compliant rekeying without downtime. |
| Encrypted workload migration | Yes | Clear text VM migrations between data stores | Only within the same vCenter Server |  |
{: caption="Table 1. Encryption features comparison" caption-side="bottom"}

**Next topic:** [HyTrust overview](/docs/services/vmwaresolutions?topic=vmware-solutions-htdc-hpcs-hytrust-overview)

## Related links
{: #htdc-hpcs-encryption-options-related}

* [HyTrust DataControl](https://www.hytrust.com/products/datacontrol-workload-encryption/){:external}
* [IBM Cloud Hyper Protect Crypto Services](https://www.ibm.com/cloud/hyper-protect-crypto){:external}
