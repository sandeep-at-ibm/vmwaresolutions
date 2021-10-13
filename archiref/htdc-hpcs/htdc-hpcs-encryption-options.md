---

copyright:

  years:  2019, 2021

lastupdated: "2021-08-17"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server encryption options
{: #htdc-hpcs-encryption-options}

Enterprises that require encrypted data at rest on their vCenter Server instance have the following options:

* {{site.data.keyword.cloud}} Endurance native encryption - this option uses IBM-managed keys, so is not suitable for clients that require either Bring Your Own Key (BYOK) or Keep Your Own Key (KYOK). The encryption scope is the complete NFS volume.
* vSAN encryption - This option requires the use of a key management server such as the following, the encryption scope are the vSAN™ disks:
   * IBM KeyProtect™ (IBM KP) service for customers who require BYOK, along with the KMIP™ for VMware® service.
   * IBM Hyper Protect Crypto Services (IBM HPCS), for customers who require KYOK, with the KMIP for VMware service.
   * HyTrust® KeyControl™ (HTKC) on {{site.data.keyword.cloud_notm}}.
   * A manually installed solution such as IBM Security Key Lifecycle Manager (SKLM). This solution can also use {{site.data.keyword.cloud_notm}} HSMs.
* vSphere encryption - This option requires the use of a key management server. However, the encryption scope is the virtual machine (VM) disks.
* HyTrust DataControl® encryption - This option uses the HTKC key management server and Policy Agent, both components of HyTrust DataControl (HTDC). This option can now also use IBM HPCS to deliver KYOK. The encryption scope includes Microsoft® Windows® or Linux® VM disks, files, or file systems.

The use of IBM KP or IBM HPCS allows:
* Bring Your Own Key (BYOK) - Bring your keys to the cloud and manage them using the IBM KP multi-tenant key management service.
* Keep Your Own Key (KYOK) - Keep your keys protected with the IBM HPCS single-tenant key management service. It has built-in customer-controlled FIPS 140-2 Level 4 Hardware Security Modules (HSM), which provide control and authority over encryption keys.

This reference architecture is based on the HTDC and IBM HPCS option, and the following table compares this option against vSAN and vSphere encryption.

| Item | HTDC | vSphere Encryption | vSAN Encryption | Notes |
| ---- | ---- | ------------------ | --------------- | ----- |
| Compatible with replication products - Zerto, HCX, and vSphere Replication | Yes | Yes | Yes| |
| Encryption scope | VM | Hypervisor only | Data store only | The higher up the stack encryption occurs, the higher the security level and fewer attack vectors. |
| Workload boot and clone protection | Yes | No | No | Ensures cloned workloads. VMs don't work unless authorized. |
| Encrypted backups with Veeam | Yes | Yes | Yes | |
| Encryption granularity | Per VM | Per VM | Per vSAN cluster | More granularity provides more secure deployment options. |
| vSAN deduplication and compression | No | No | Yes | Deduplication reduces storage requirements. |
| Encrypt and rekey without downtime | Yes | No | No | Frequent rekeying is fundamental to security compliance. HyTrust can perform rekeying automatically, while VMs continue to run. |
| Secure workload mobility | vSphere, vSAN, bare metal, or any hypervisor | Within vSphere only | Within the vSAN cluster only | With HyTrust, policies follow the workload across any platform. |
| Secure workload mobility public cloud | AWS, Azure, IBM | No | No | Operational simplicity - one solution for encryption across all platforms, less chance of mistakes. |
| Transparency | Fully transparent | Limited | Limited | vSphere and vSAN provide limited visibility into clones and snapshots. |
| Geo-Fencing (GDPR) | Yes | No | No | HyTrust BoundaryControl integration |
| NIST/PCI compliant live rekey | Yes | No | No | Allows NIST-compliant rekeying without downtime. |
{: caption="Table 1. Encryption features comparison" caption-side="top"}

**Next topic:** [IBM Hyper Protect Crypto Services overview](/docs/vmwaresolutions?topic=vmwaresolutions-htdc-hpcs-hpcs-overview)

## Related links
{: #htdc-hpcs-encryption-options-related}

* [HyTrust DataControl](https://www.hytrust.com/products/datacontrol-workload-encryption/){: external}
* [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](https://www.ibm.com/cloud/hyper-protect-crypto){: external}
