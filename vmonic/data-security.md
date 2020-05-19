---

copyright:
  years: 2020
lastupdated: "2020-04-08"

keywords: data encryption in IBM Cloud for VMware Solutions, data storage for IBM Cloud for VMware Solutions, bring your own keys for IBM Cloud for VMware Solutions, BYOK for IBM Cloud for VMware Solutions, key management for IBM Cloud for VMware Solutions, key encryption for IBM Cloud for VMware Solutions, personal data in IBM Cloud for VMware Solutions, data deletion for IBM Cloud for VMware Solutions, data in IBM Cloud for VMware Solutions, data security in IBM Cloud for VMware Solutions, IBM Cloud for VMware Solutions

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}

# Securing your data in IBM Cloud for VMware Solutions
{: #mng-data}

To ensure that you can securely manage your personal data when you use {{site.data.keyword.vmwaresolutions_full}}, it's important to know what data is stored and encrypted and how you can delete any stored data. 
{: shortdesc}

## How your data is stored and encrypted in IBM Cloud for VMware Solutions
{: #data-storage}

When a user onboards to VMware Solutions and orders instances, we store and manage user data of configuration and metadata that is associated with the user and ordered instances. That user data includes:

* For both VMware Solutions Shared and Dedicated:
   * IBMid (email)
   * Instance configuration information
   * Instance access information such as login credentials to vCloud Director, vCenter Server, and NSX Manager.
* For VMware Solutions Dedicated:
   * {{site.data.keyword.cloud_notm}} classic infrastructure credential (username and API key)

This configuration data and metadata is stored and managed by IBM. It is encrypted at REST and in transit. Additionally, sensitive data such as API key and access information are encrypted with customer–specific encryption keys.

With VMware Solutions Dedicated, you can bring your own data to {{site.data.keyword.cloud_notm}} bare metal servers and {{site.data.keyword.cloud_notm}} File and Block storage that is managed by your VMware instance. All of this data is managed by you and not managed by IBM, and you have the option of encrypting it using various solutions. These solutions include:
* KMIP for VMware service along with {{site.data.keyword.cloud_notm}} Key Protect or {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services to enable vSAN or vSphere encryption for your workloads
* HyTrust DataControl encryption of your virtual machines, with optional integration with {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services
* HyTrust KeyControl as a key server that enables vSAN or vSphere encryption for your workloads
* Other self–managed VMware–compatible encryption technologies

If you use VMware Solutions Shared, your workload data exists in an IBM–managed Cloud infrastructure account. VMware vSphere encryption is automatically enabled by IBM for your virtual machines by using IBM–managed keys that are backed by {{site.data.keyword.cloud_notm}}'s KMIP for VMware and Hyper Protect Crypto Services. You can optionally implement your own encryption solutions within your VMware workloads.

## Protecting your sensitive data in IBM Cloud for VMware Solutions
{: #data-encryption}

### About customer-managed keys
{: #about-encryption}

VMware Solutions uses envelope encryption to offer customer–managed keys for Dedicated VMware offerings. For VMware Solutions Shared, envelope encryption is used but with IBM–managed rather than customer–managed keys.

Envelope encryption within VMware Solutions uses either the [KMIP for VMware service](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) to provide key management for VMware vSphere encryption or vSAN encryption, or [HyTrust Data Control](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations) policy–based virtual machine encryption. In both cases, these offerings use {{site.data.keyword.cloud_notm}} Key Protect or {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services for key wrapping and unwrapping. Key Protect offers Bring Your Own Key (BYOK) capability by using FIPS 140–2 level 3 certified hardware security modules (HSMs). Hyper Protect Crypto Services offers Keep Your Own Key (KYOK) capability by using FIPS 140–2 level 4 certified HSMs.

### Enabling customer-managed keys for IBM Cloud for VMware Solutions
{: #using-byok}

See the [KMIP for VMware implementation guide](/docs/vmwaresolutions?topic=vmwaresolutions-kmip-implementation) for using IBM Cloud key management with VMware vSphere or vSAN encryption.

See the [HyTrust Data Control and HPCS deployment guide](/docs/vmwaresolutions?topic=vmwaresolutions-htdc-hpcs-deployment) for using HyTrust Data Control together with Hyper Protect Crypto Services to secure your VMware virtual machines.

### Working with customer-managed keys for IBM Cloud for VMware Solutions
{: #working-with-keys}

For guidance on special considerations for VMware key management, key revocation, and key rotation, see [KMIP for VMware considerations](/docs/vmwaresolutions?topic=vmwaresolutions-kmip-design#kmip-design-considerations) and [KMIP for VMware management guide](/docs/vmwaresolutions?topic=vmwaresolutions-kmip-implementation#kmip-implementation-key-rotation).

## Deleting your data in IBM Cloud for VMware Solutions
{: #data-delete}

### Deleting IBM Cloud for VMware Solutions instances
{: #service-delete}

When a customer deletes a VMware Solutions Dedicated instance, all associated customer workload data will be deleted. The underneath IaaS resources will also be deleted at the end of the corresponding billing cycle. 

When a customer deletes a VMware Solutions Shared instance, all associated customer data will be deleted immediately.

Along with the instance deletion, the instance's configuration and metadata are also marked as inactive. You can request complete deletion of the metadata through a "secure wipe" ticket.  

### Restoring deleted data for IBM Cloud for VMware Solutions
{: #data-restore}

You are responsible to make provision for backup and recovery of all data you bring to VMware Solutions. {{site.data.keyword.cloud_notm}} does not back up your workload data and cannot restore it after deletion.
