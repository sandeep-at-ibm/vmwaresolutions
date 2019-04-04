---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware implementation and management
{: #kmip-implementation}

## Connecting the key management server
{: #kmip-implementation-connecting-kms}

To enable vSphere encryption or vSAN encryption by using KMIP for VMware on {{site.data.keyword.cloud_notm}}, you need to complete the following tasks:

1. [Enabling your account for using Service Endpoints using IBM Cloud CLI](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps).
2. Create a key manager instance, using either [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-tutorial) or [IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started). If you are using Hyper Protect Crypto Services, [initialize your crypto instance](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm) so that Hyper Protect Crypto Services can provide key related functions.
3. Create a customer root key (CRK) within your key manager instance.
4. Create an Identity and Access Management (IAM) [service ID and API key](/docs/iam?topic=iam-serviceidapikeys#serviceidapikeys) for use with KMIP for VMware. Grant this service ID platform viewer access and service write access to your key manager instance.
5. Create a [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering#kmip_standalone_ordering) instance from the {{site.data.keyword.cloud_notm}} catalog.
6. Within VMware vCenter, create a key management server (KMS) cluster with two servers, one for each KMIP for VMware endpoint in your chosen region.
7. Select one of VMware&rsquo;s methods to generate or install a KMS client certificate in vCenter.
8. Export the public version of the certificate and configure it as an allowed client certificate in your KMIP for VMware instance.

## Enabling encryption
{: #kmip-implementation-enable-encrypt}

To use vSAN encryption, edit the vSAN general settings in your vCenter cluster and select the encryption check box.

The vSAN health check might issue periodic warnings that it is unable to connect to the KMS cluster from one or more of your vSphere hosts. These warnings occur because the vSAN health check connection times out too quickly. You can ignore these warnings. For more information, see [vSAN KMS Health Check intermittently fails with SSL Handshake Timeout error](https://kb.vmware.com/s/article/67115){:new_window}.
{:note}

To use vSphere encryption, edit your virtual machine storage policies to require disk encryption.

## Key rotation
{: #kmip-implementation-key-rotation}

Rotate your [Key Protect](/docs/services/key-protect?topic=key-protect-rotate-keys#rotate-keys) or [Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-rotating-keys#rotating-keys) customer root key (CRK) by using the {{site.data.keyword.cloud_notm}} console or API.

For VMware vSAN encryption, rotate your VMware key&ndash;encrypting keys (KEKs) and optionally data&ndash;encrypting keys (DEKs) from the vSAN general settings in your vCenter cluster.

For VMware vSphere encryption, rotate your VMware KEKs and DEKs (optionally) by using the **Set-VMEncryptionKey** PowerShell command.

## Key revocation
{: #kmip-implementation-key-revocation}

You can revoke all keys in use by KMIP for VMware by deleting your chosen CRK from your key manager.

When keys are revoked, all data that is protected by these keys and by your KMIP for VMware instance is cryptographically shredded by this method. VMware preserves some keys while an ESXi host is powered on, so you need to restart your vSphere cluster to ensure that all encrypted data is no longer in use.
{:important}

KMIP for VMware stores individual wrapped KEKs in your Key Protect or Hyper Protect Crypto Services instance by using names that are associated with the key IDs that are known to VMware. You can delete individual keys to revoke the encryption of individual disks or drives.

VMware does not delete keys from the KMS when a VM having encrypted disks is removed from inventory. This is to allow recovery of that VM from backup or if it is restored to inventory. If you wish to reclaim these keys and cryptographically invalidate all backups, you need to delete the keys from your key manager instance after deleting your VMs.
{:note}

## Related links
{: #kmip-implementation-related}

* [Solution overview](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview#kmip-overview)
* [Solution design](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design#kmip-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
* [IBM Cloud Hyper Protect Crypto Services](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-tutorial)
