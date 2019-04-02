---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud overview
{: #kmip_standalone_considerations}

The KMIP for VMware on {{site.data.keyword.cloud}} service provides a 24x7 highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and destroy the encryption keys. It also provides management capability to maintain the associations between the client credentials and the encryption keys.

The KMIP for VMware on {{site.data.keyword.cloud_notm}} service is available as a stand-alone service without being associated to a VMware instance. Each instance of the service can serve one or more vCenter Server instances or vSphere clusters.

## Technical specifications for KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

The following specifications are included with the KMIP for VMware on {{site.data.keyword.cloud_notm}} service:

* A VMware-compatible Key Management Interoperability Protocol (KMIP)
* Two managed services: [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/catalog/services/key-protect) and [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](https://console.bluemix.net/catalog/services/hyper-protect-crypto-services)
* Available in multiple geographic regions worldwide
* Two KMIP network service endpoints provided in each region for high availability

## Considerations when installing KMIP for VMware on IBM Cloud instances
{: #kmip_standalone_considerations-install}

Review the following considerations before you install a KMIP for VMware on {{site.data.keyword.cloud_notm}} instance:

* KMIP for VMware on {{site.data.keyword.cloud_notm}} uses the IBM Key Protect for {{site.data.keyword.cloud_notm}} (Key Protect) service or the {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services (HPCS) service to create, encrypt, and decrypt encryption keys. Therefore, before you install KMIP for VMware on {{site.data.keyword.cloud_notm}}, ensure that:
   * You ordered a usable Key Protect or HPCS service instance in the {{site.data.keyword.cloud_notm}} region where your KMIP for VMware on {{site.data.keyword.cloud_notm}} instance is to be hosted:
      * For more information about creating an instance of Key Protect, see [Provisioning the service](/docs/services/key-protect?topic=key-protect-provision).
      * For more information about creating an instance of HPCS, see [Provisioning the service](/docs/services/hs-crypto?topic=hs-crypto-provision#provision). In addition to provisioning the HPCS service, you must also [initialize your crypto instance](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm) so that HPCS can provide key related functions.
   * An {{site.data.keyword.cloud_notm}} service ID was created by following the steps in [Creating a service ID](/docs/iam?topic=iam-serviceids). This service ID is used to access the Key Protect or HPCS service instance that you created.
   * You granted the following access levels for the service ID:
      * At the platform access level: Viewer authority to your Key Protect or HPCS service instance
      * At the service access level: Manager authority to your Key Protect or HPCS service instance
   * You have an API key for the created service ID. The key is required when you order the service.
   * You created at least one customer root key (CRK) by using the GUI or API of Key Protect or HPCS:
      * For more information about creating root keys with the Key Protect GUI or API, see [Creating root keys](/docs/services/keymgmt/keyprotect_create_root.html) or [IBM Key Protect API](https://cloud.ibm.com/apidocs/key-protect).
      * For more information about creating root keys with the HPCS GUI or API, see [Creating root keys](/docs/hs-crypto/get-started?topic=hs-crypto-create-root-keys) or [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hp-crypto).

     **Important:** You cannot order the service without CRKs. It is highly recommended that you use the method to create a CRK using existing key material, and back up the key material that you are creating. By doing so, you ensure that you can recover your keys if a failure of the data center where Key Protect or HPCS is applied to store your CRKs.
* Ensure that your {{site.data.keyword.cloud_notm}} infrastructure account is enabled for Virtual Routing and Forwarding (VRF) and for connectivity to Service Endpoints. For more information, see:
   * [Overview of Virtual Routing and Forwarding (VRF) on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Enabling your account for using Service Endpoints using IBM Cloud CLI](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)
* Because only private connection is supported, you do not need to configure any firewall or SNAT rules in vCenter Server for the network connectivity from the vCenter Server to the endpoint of the KMIP for VMware on {{site.data.keyword.cloud_notm}} instance.

For more information, see [KMIP for VMware on IBM Cloud solution architecture](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview).

## Considerations when deleting KMIP for VMware on IBM Cloud instances
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

All data protected by the KMIP for VMware on IBM Cloud service, including encrypted backups, cannot be decrypted after you remove the service.

## Related links
{: #kmip_standalone_considerations-related}

* [Ordering KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [Adding, viewing, and deleting certificates for KMIP for VMware on IBM Cloud instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [Viewing KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Deleting KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker events](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
