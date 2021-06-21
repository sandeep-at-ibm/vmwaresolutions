---

copyright:

  years:  2021

lastupdated: "2021-06-16"

keywords: data encryption in VMware Solutions, data storage for VMware Solutions, bring your own keys for VMware Solutions, BYOK for VMware Solutions, key management for VMware Solutions, key encryption for VMware Solutions, personal data in VMware Solutions, data deletion for VMware Solutions, data in VMware Solutions, data security in VMware Solutions

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}

# Securing your data in VMware Solutions
{: #data-security-mng-data}

To ensure that you can securely manage your personal data when you use {{site.data.keyword.cloud}} for VMware® Solutions, it's important to know what data is stored and encrypted and how you can delete any stored data. 
{: shortdesc}

## How your data stored and encrypted in VMware Solutions
{: #data-security-data-storage}

When a user onboards to VMware Solutions and orders instances, we store and manage user data of configuration and metadata that is associated with the user and ordered instances. That user data includes the following items.

* For both VMware Solutions Shared and Dedicated, the user data includes the following items:
   * IBMid (email)
   * Instance configuration information
   * Instance access information such as login credentials to vCloud Director, VMware vCenter Server®, and VMware NSX® Manager.
* For VMware Solutions Dedicated, the user data includes the following items:
   * {{site.data.keyword.cloud_notm}} classic infrastructure credentials (username and API key)

This configuration data and metadata is stored and managed by IBM. It is encrypted at REST and in transit. Additionally, sensitive data such as API key and access information are encrypted with customer–specific encryption keys.

With VMware Solutions Dedicated, you can bring your own data to {{site.data.keyword.cloud_notm}} bare metal servers and {{site.data.keyword.cloud_notm}} File and Block storage that is managed by your VMware instance. All of this data is managed by you and not managed by IBM, and you have the option of encrypting it using various solutions.

These solutions include the following options:
* KMIP™ for VMware service along with {{site.data.keyword.cloud_notm}} Key Protect or {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services to enable vSAN™ or VMware vSphere® encryption for your workloads
* HyTrust DataControl® encryption of your virtual machines (VMs), with optional integration with {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services
* HyTrust KeyControl™ as a key server that enables vSAN or vSphere encryption for your workloads
* Other self–managed VMware–compatible encryption technologies

If you use VMware Solutions Shared, your workload data exists in an IBM–managed cloud infrastructure account. You are provided with the default vSphere encryption option for your VMs, which uses IBM–managed keys that are backed by the {{site.data.keyword.cloud_notm}} KMIP for VMware and Hyper Protect Crypto Services. You can optionally implement your own encryption solutions within your VMware workloads.

## How your data stored and encrypted in the VMware Solutions Shared Veeam Availability Suite service
{: #data-security-data-veeamshared}

When you onboard to VMware Solutions Shared and order instances, you can get extra services, such as Veeam Availability Suite™, which is relevant to data storage and encryption.

The Veeam Availability Suite backup storage uses a unique scale-out backup repository (SOBR) object for each customer. The SOBR is programmatically configured for each customer, with a dedicated location on each disk and a generated backup file encryption password. The SOBR includes an extent that is backed by IBM block storage in each of the physical data centers within the specific region. For example, if the virtual data center is in **Dallas 10**, the SOBR has extents in **Dallas 10**, **Dallas 12**, and **Dallas 13**. The SOBR includes a customer-specific Cloud Object Storage bucket for more cost-effective long-term storage and as a second copy. Depending on the regions and compliance requirements of each geography, the Cloud Object Storage buckets remain in the same country, which is sometimes the same physical site.

When you decide to use the Veeam self-service portal to create backup jobs, identify which vApp and VM instances from any virtual data center in the organization participate in the backup job. Those backups are stored in the organizations SOBR.

You can manage (restore or delete) backups in the Veeam self-service portal. All backups are deleted if a virtual organization is deleted.

## Protecting your sensitive data in VMware Solutions
{: #data-security-data-encryption}

### IBM Cloud Support access
{: #data-security-ibm-access}

{{site.data.keyword.cloud_notm}} Support has access to your VMware virtualization environment.
* For VMware Solutions Shared, {{site.data.keyword.cloud_notm}} manages the virtualization environment and this access cannot be revoked.
* For VMware Solutions Dedicated, IBM maintains this access to enable automated day 2 operations such as capacity expansion, and to enable support for problem resolution. For more information, see the following topics.
   * [Policy for accessing clients instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_compl_info#vc_compl_info-policy-for-access-client-inst)
   * [Consent to accessing client environments](/docs/vmwaresolutions?topic=vmwaresolutions-vc_compl_info#vc_compl_info-consent-to-access-client-environment)

In VMware Solutions Dedicated, you can take steps to limit {{site.data.keyword.cloud_notm}} access to your instance. These steps can include the following actions:
* You must create a functional {{site.data.keyword.cloud_notm}} account to own the API key that you provide to VMware Solutions for provisioning. Ensure that you monitor the mailbox of this account for notices.
* You can regenerate this API key to revoke automation and support access to your API key. When you need to restore {{site.data.keyword.cloud_notm}} access, for example, to deploy a new host, you must reenter the API key in the VMware Solutions Settings page.
* {{site.data.keyword.cloud_notm}} retains a set of [user IDs](/docs/vmwaresolutions?topic=vmwaresolutions-audit_user_ids) in your instance. You can disable or revoke these user IDs. When you need to restore {{site.data.keyword.cloud_notm}} access, for example, to deploy a new host, you must re-enable these accounts. If you changed the password for these accounts, you must open a support ticket to provide the updated password to {{site.data.keyword.cloud_notm}}.

### About customer-managed keys
{: #data-security-about-encryption}

For VMware Solutions Dedicated, envelope encryption is used to offer customer–managed keys. For VMware Solutions Shared, envelope encryption is used but with IBM–managed rather than customer–managed keys.

Envelope encryption within VMware Solutions uses either the [KMIP for VMware service](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) to provide key management for VMware vSphere® encryption or vSAN encryption, or [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations) policy–based VM encryption.

In both cases, these offerings use {{site.data.keyword.cloud_notm}} Key Protect or {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services for key wrapping and unwrapping. Key Protect offers Bring Your Own Key (BYOK) capability by using FIPS 140–2 level 3 certified hardware security modules (HSMs). Hyper Protect Crypto Services offers Keep Your Own Key (KYOK) capability by using FIPS 140–2 level 4 certified HSMs.

### Enabling customer-managed keys for VMware Solutions
{: #data-security-using-byok}

You can use {{site.data.keyword.cloud_notm}} key management with VMware vSphere or vSAN encryption. For more information, see the [KMIP for VMware implementation guide](/docs/vmwaresolutions?topic=vmwaresolutions-kmip-implementation).

You can use HyTrust DataControl together with Hyper Protect Crypto Services to secure your VMs. For more information, see the [HyTrust DataControl and HPCS deployment guide](/docs/vmwaresolutions?topic=vmwaresolutions-htdc-hpcs-deployment).

### Working with customer-managed keys for VMware Solutions
{: #data-security-working-with-keys}

For more information about considerations for VMware key management, key revocation, and key rotation, see:
* [KMIP for VMware considerations](/docs/vmwaresolutions?topic=vmwaresolutions-kmip-design#kmip-design-considerations)
* [KMIP for VMware management guide](/docs/vmwaresolutions?topic=vmwaresolutions-kmip-implementation#kmip-implementation-key-rotation)

## Deleting your data in VMware Solutions
{: #data-security-data-delete}

### Deleting VMware Solutions instances
{: #data-security-service-delete}

When a customer deletes a VMware Solutions Dedicated instance, all associated customer workload data is deleted. The underneath IaaS resources are also deleted at the end of the corresponding billing cycle. 

When a customer deletes a VMware Solutions Shared instance, all associated customer data is deleted immediately.

Along with the instance deletion, the instance's configuration and metadata are also marked as "inactive". You can request complete deletion of the metadata through a "secure wipe" ticket.  

### Restoring deleted data for VMware Solutions
{: #data-security-data-restore}

You are responsible to make provision for backup and recovery of all data you bring to VMware Solutions. {{site.data.keyword.cloud_notm}} does not back up your workload data and cannot restore it after deletion.

## Related links
{: #data-security-related}

* [Managing access for VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-iam)
* [Auditing events for VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-at-events)
* [Managing security and compliance with VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-manage-scc)
