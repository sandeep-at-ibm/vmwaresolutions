---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Considerations for KMIP for VMware on IBM Cloud

The KMIP for VMware on {{site.data.keyword.cloud}} service provides a 24x7 highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and destroy the encryption keys, and it also provides management capability to maintain the associations between the client credentials and those encryption keys.

**Availability**: This service is available only to instances deployed in V2.2 or later releases.

You can order an instance with the KMIP for VMware on {{site.data.keyword.cloud_notm}} service included. For more information, see:
* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)

You can also add the KMIP for VMware on {{site.data.keyword.cloud_notm}} service to your existing instances after initial deployment. For more information, see:
* [Ordering and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)

## Considerations when installing KMIP for VMware on IBM Cloud

KMIP for VMware on {{site.data.keyword.cloud_notm}} uses the IBM Key Protect for IBM Cloud service to create, encrypt, and decrypt encryption keys. Therefore, before installing the service, ensure that you have ordered a usable Key Protect service. Meanwhile, an {{site.data.keyword.cloud_notm}} service ID has been created by following the steps in [Creating a service ID](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id) to access the Key Protect service instance that you created.

Ensure that you grant the following access levels for the service ID:
* At the platform access level: Viewer authority to your IBM Key Protect instance.
* At the service access level: Writer authority to your IBM Key Protect instance.

The API key for the created service ID is required when ordering the service.

The service assumes that you have already created at least one customer root key (CRK) from the Key Protect user interface by following the steps in [Creating root keys](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys), or by using the RESTful API in [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect).

You cannot order the service without CRKs. It is highly recommended that you use the method to create a CRK using existing key material, and backup the key material that you are creating. By doing so, you ensure that you can recover your keys in case of a total failure of the data center where IBM Key Protect is applied to store your CRKs.

## Considerations when using KMIP for VMware on IBM Cloud

* To use an ordered KMIP for VMware on {{site.data.keyword.cloud_notm}} service as a Key Management Server (KMS) that is registered to VMware vCenter Server, you must ensure that configurations are in place so that the network connectivity from the vCenter Server to the endpoint of the ordered KMIP for VMware on {{site.data.keyword.cloud_notm}} service is functional.
* To use the service for VMware vSAN encryption, you must ensure that the network connectivity between the hosts on the target vSAN and the endpoint of the ordered KMIP for VMware on {{site.data.keyword.cloud_notm}} service is functional.
* {{site.data.keyword.cloud_notm}} maintains a highly available KMIP for VMware on {{site.data.keyword.cloud_notm}} service endpoint in each region where the service is available. You select the region for the service when you deploy the service. For vCenter Server, you must configure a KMS cluster with connections to the endpoint in your selected region. See the following table for the endpoint in each region. These endpoints use self-signed certificates that are maintained by the {{site.data.keyword.vmwaresolutions_short}} team. The thumbprint for the certificates is `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`.

Table 1: KMIP for VMware on IBM Cloud service endpoint regions

| Region         | Endpoint               |
|:---------------|:-----------------------|
| Sydney         |  `130.198.73.134:5696` |
| United Kingdom |  `158.175.93.122:5696` |
| US South       |  `169.60.185.42:5696`  |

## Considerations when removing KMIP for VMware on IBM Cloud

The VMware public certificate that your provided during ordering or using the service is used as the client certificate to communicate with the service instance. When the service is removed, all the encryption keys created by this service instance for the associated VMware public certificate are removed together.

Therefore, before you remove the service, you must ensure that no virtual machines or vSANs are being encrypted by using the keys created by the KMIP service.

## Related links

* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [FAQ](../vmonic/faq.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
