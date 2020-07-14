---

copyright:

  years:  2020

lastupdated: "2020-07-10"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Encryption
{: #fss-encryption}

There are no native key management tools in vSphere thus the ISV must bring a tool of their choosing to provide the necessary key management functions. The ISV can use the IBM Hyper Protect Crypto Services (HPCS) with the Key Management Interoperability Protocol (KMIP) adapter or HyTrust DataControl on the IBM Cloud for VMware Regulated Workloads or their own on-premises key management services.

## Hyper Protect Crypto Services
{: #fss-encryption-hpcs}

VMware vSphere encryption applies to all types of VMware storage, including vSAN storage. With vSphere encryption solution, vCenter Server and your ESXi hosts connect to a key management server to get the required encryption keys. These keys are used to protect individual virtual machine (VM) disks, according to your VM storage policies.

As vSphere encryption operates at the virtual machine disk level, it can prevent data exposure; if loss of physical disk drives or loss of VM disks occurs. Many backup and replication technologies cannot back up or replicate effectively because the provided data is encrypted. It is also notable, that vSphere encryption is not compatible with vSphere replication, cross-vCenter vMotion, VMware HCX, Zerto, or IBM Spectrum Protect Plus. However, when properly configured, Veeam Backup and Replication is compatible with vSphere encryption.

HPCS is used as the key management service that supports Keep Your Own Key (KYOK). HPCS is accessible through the Enterprise PKCS#11 (EP11) API, but VMware vSphere encryption supports only a Key Management System (KMS) that uses the KMIP standard. Therefore, the solution needs the KMIP adapter for VMware service to act as an adapter between the two.

HyTrust DataControl (HTDC) can replace the use of vSphere encryption but requires the installation of agents into each VM for which encryption is required. The KMIP adapter is not required with HTDC.

![vSphere encryption with Hyper Protect Crypto Services](../../images/fss-hpcs-mgmt.svg){: caption="Figure 1. vSphere encryption with Hyper Protect Crypto Services" caption-side="bottom"}

IBM HPCS is a single-tenant key management service, backed by a FIPS140-2 level 4 certified Hardware Security Module (HSM). With IBM HPCS, customers can move their most mission critical workloads to the IBM Cloud with the assurance of using the highest level of security to prevent unauthorized access to their sensitive data.

At a high level the IBM HPCS consists of the following components:

- Crypto unit - a singular unit that represents a piece of hardware, the HSM, and the corresponding software stack, both are dedicated to a single tenant.
- Service instance - a cluster of crypto units, which operates as a single logical entity to provide redundancy and scalability. It is recommended to have at least two instances to provide high availability.

Customers maintain complete control over their keys and data in the cloud and no one, including IBM Cloud admins, has access to the customer data. Additionally, no single person has access to the full key and if required multiple crypto unit administrators can be deployed.

The KMIP for VMware instance is authorized to Hyper Protect Crypto Services instance by using an IBM Cloud Identity and Access Management (IAM) service ID that has been granted access to the instance. The service ID must have a minimum of platform Viewer access and service Manager access to customer's key manager instance. KMIP for VMware uses the customer root key (CRK) of customer's choice in the key manager instance, and stores all KEKs generated on behalf of VMware, in wrapped form, in the key manager instance.

To access KMIP for VMware over the private network, IBM Cloud service endpoints are used. During the setup, VMware vCenter and ESXi establish a trust with the deployed KMIP instance. VMware vCenter and ESXi authenticate with customer's KMIP for VMware instance by using certificates in VMware vCenter when the connection core a key management server (KMS) is created. The public certificate is installed into KMIP for VMware to identify the vCenter client or clients that are allowed to connect. Each client is authorized to all keys stored in that KMIP for VMware instance.

The customer is responsible for deploying and managing both Hyper Protect Crypto Services and KMIP for VMware instance for their IBM Cloud for VMware Regulated Workloads instance. The cloud administrator creates the KMS cluster configuration in the vCenter.

## HPCS keys
{: #fss-encryption-keys}

To protect the financial institution and the ISV's data, it is recommended they have separate HPCS instances and root keys. The two-key approach balances both the stake holders rights and responsibilities.

![Dual HPCS overview](../../images/fss-dual-hpcs.svg){: caption="Figure 2. Dual HPCS overview" caption-side="bottom"}

### HPCS - independent software vendor view
{: #fss-encryption-keys-isv}

The ISV uses their root key material into the HPCS provisioned as part of the IBM Cloud for VMware Regulated Workloads deployment. This key integrates with the management platform and would be used with vSphere encryption or vSAN encryption or any other tool that is used to encrypt any of the platform components.

### HPCS - financial institution view
{: #fss-encryption-keys-bank}

The Financial institution will manage their own independent HPCS instance and introduce their own root key material. This key is critical to the security of the bank data and they would generate "descendant" keys for use by an individual ISV they engage with.

The keys that are provided by the bank are used to protect any data from the bank.

## HPCS flows
{: #fss-encryption-flows}

Review the following information for the step-by-step process to order and initialize KMIP:
* [VMware Solutions KMIP considerations](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations)
* [Provisioning documentation for HPCS](/docs/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm)

**Next topic**: [Operations management](/docs/vmwaresolutions?topic=vmwaresolutions-fss-operations)

## Related links
{: #fss-encryption-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
