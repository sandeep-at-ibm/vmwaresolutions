---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud overview

The KMIP for VMware on {{site.data.keyword.cloud}} service provides a 24x7 highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and destroy the encryption keys. It also provides management capability to maintain the associations between the client credentials and the encryption keys.

This service is available only to instances deployed in V2.2 or later.
{:note}

## Technical specifications for KMIP for VMware on IBM Cloud

The following specifications are included with the KMIP for VMware on {{site.data.keyword.cloud_notm}} service:

* A VMware-compatible Key Management Interoperability Protocol (KMIP)
* A managed service
* Available in multiple geographic regions worldwide
* A highly available KMIP service endpoint in each region

## Considerations when you install KMIP for VMware on IBM Cloud

KMIP for VMware on {{site.data.keyword.cloud_notm}} uses the IBM Key Protect for {{site.data.keyword.cloud_notm}} service to create, encrypt, and decrypt encryption keys. Therefore, before you install KMIP for VMware on {{site.data.keyword.cloud_notm}}, ensure that:
* You ordered a usable Key Protect service.
* An {{site.data.keyword.cloud_notm}} service ID was created by following the steps in [Creating a service ID](../../../iam/serviceid.html). This service ID is used to access the Key Protect service instance that you created.
* You granted the following access levels for the service ID:
   * At the platform access level: Viewer authority to your IBM Key Protect instance.
   * At the service access level: Writer authority to your IBM Key Protect instance.
* You have an API key for the created service ID. The key is required when you order the service.
* You created at least one customer root key (CRK) from the Key Protect user interface by following the steps in [Creating root keys](../../keymgmt/keyprotect_create_root.html), or by using the REST API in [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect).

   **Important:** You cannot order the service without CRKs. It is highly recommended that you use the method to create a CRK using existing key material, and back up the key material that you are creating. By doing so, you ensure that you can recover your keys if a failure of the data center where IBM Key Protect is applied to store your CRKs.

## Considerations when you use KMIP for VMware on IBM Cloud

* To use an ordered KMIP for VMware on {{site.data.keyword.cloud_notm}} service as a Key Management Server (KMS) that is registered to VMware vCenter Server, ensure that the network connectivity from the vCenter Server to the endpoint of the ordered KMIP for VMware on {{site.data.keyword.cloud_notm}} service is functional.
* To use the service for VMware vSAN encryption, ensure that the network connectivity between the hosts on the target vSAN and the endpoint of the ordered KMIP for VMware on {{site.data.keyword.cloud_notm}} service is functional.

## Considerations when you remove KMIP for VMware on IBM Cloud

The VMware public certificate that you're provided during ordering or when you use the service is used as the client certificate to communicate with the service instance. When the service is removed, all the encryption keys that are created by this service instance for the associated VMware public certificate are also removed.

Therefore, before you remove the service, ensure that no virtual machines or vSANs are being encrypted by using the keys that are created by the KMIP service.

### Related links

* [Ordering KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_ordering.html)
* [{{site.data.keyword.cloudaccesstrailshort}} events](../vmonic/at-events.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](../../keymgmt/index.html)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [FAQ](../vmonic/faq.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
