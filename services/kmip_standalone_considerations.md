---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-02"

keywords: KMIP for VMware, KMIP stand-alone, tech specs KMIP

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware overview
{: #kmip_standalone_considerations}

The KMIP for VMware service provides a 24x7 highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and destroy the encryption keys. It also provides management capability to maintain the associations between the client credentials and the encryption keys.
{: shortdesc}

The KMIP for VMware service is available as a stand-alone service without being associated to a VMware instance. Each instance of the service can serve one or more vCenter Server instances or vSphere clusters.

## Technical specifications for KMIP for VMware
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

The following specifications are included with the KMIP for VMware service:

* A VMware-compatible Key Management Interoperability Protocol (KMIP)
* Two managed services: [Key Protect](https://cloud.ibm.com/catalog/services/key-protect) and [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* Available in multiple geographic regions worldwide
* Two KMIP network service endpoints provided in each region for high availability

## Considerations when you install KMIP for VMware instances
{: #kmip_standalone_considerations-install}

Review the following considerations before you install a KMIP for VMware instance:

* KMIP for VMware uses the IBM Key Protect service or the Hyper Protect Crypto Services (HPCS) service to create, encrypt, and decrypt encryption keys. Therefore, before you install KMIP for VMware, ensure that:
   * You ordered a usable Key Protect or HPCS service instance in the {{site.data.keyword.cloud_notm}} region where your KMIP for VMware instance is to be hosted:
      * For more information about creating an instance of Key Protect, see [Provisioning the service](/docs/key-protect?topic=key-protect-provision).
      * For more information about creating an instance of HPCS, see [Provisioning the service](/docs/hs-crypto?topic=hs-crypto-provision#provision). In addition to provisioning the HPCS service, you must also [initialize your crypto instance](/docs/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm) so that HPCS can provide key related functions.
   * An {{site.data.keyword.cloud_notm}} service ID was created by following the steps in [Creating a service ID](/docs/iam?topic=iam-serviceids). This service ID is used to access the Key Protect or HPCS service instance that you created.
   * You granted the following access levels for the service ID:
      * At the platform access level: Viewer authority to your Key Protect or HPCS service instance
      * At the service access level: Manager authority to your Key Protect or HPCS service instance
   * You have an API key for the created service ID. The key is required when you order the service.
   * You created at least one customer root key (CRK) by using the GUI or API of Key Protect or HPCS:
      * For more information about creating root keys with the Key Protect GUI or API, see [Creating root keys](/docs/key-protect?topic=key-protect-create-root-keys#create-root-keys) or [IBM Key Protect API](https://cloud.ibm.com/apidocs/key-protect){:external}.
      * For more information about creating root keys with the HPCS GUI or API, see [Creating root keys](/docs/hs-crypto/get-started?topic=hs-crypto-create-root-keys) or [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto){:external}.

     **Important:** You cannot order the service without CRKs. It is highly recommended that you use the method to create a CRK by using existing key material, and back up the key material that you are creating. By doing so, you ensure that you can recover your keys if a failure of the data center where Key Protect or HPCS is applied to store your CRKs.
* Ensure that your {{site.data.keyword.cloud_notm}} infrastructure account is enabled for Virtual Routing and Forwarding (VRF) and for connectivity to Service Endpoints. For more information, see:
   * [Virtual Routing and Forwarding on {{site.data.keyword.cloud_notm}}](/docs/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Enabling service endpoints](/docs/account?topic=account-vrf-service-endpoint#service-endpoint)
* Because only private connection is supported, you do not need to configure any firewall or SNAT rules in vCenter Server for the network connectivity from the vCenter Server to the endpoint of the KMIP for VMware instance.

For more information, see [KMIP for VMware solution architecture](/docs/vmwaresolutions?topic=vmware-solutions-kmip-overview).

**Notes:**

* Before the service is installed in your environment, a check is runs against the available capacity of the default cluster in the environment to ensure that the service components can fit.
* If the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email.
* To install the service, you must increase the capacity in your default cluster by either adding more hosts or by freeing up RAM, CPU, or disk space, and then add the service again in the console. After that, you can remove the existing service in the **Capacity Validation Failed** state by clicking the delete icon next to it.

## Considerations when you delete KMIP for VMware instances
{: #kmip_standalone_considerations-delete}

All data protected by the KMIP for VMware service, including encrypted backups, cannot be decrypted after you remove the service.

## Related links
{: #kmip_standalone_considerations-related}

* [Ordering KMIP for VMware instances](/docs/vmwaresolutions?topic=vmware-solutions-kmip_standalone_ordering)
* [Adding, viewing, and deleting certificates for KMIP for VMware instances](/docs/vmwaresolutions?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [Viewing KMIP for VMware instances](/docs/vmwaresolutions?topic=vmware-solutions-kmip_standalone_viewing)
* [Deleting KMIP for VMware instances](/docs/vmwaresolutions?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker events](/docs/vmwaresolutions?topic=vmware-solutions-at-events)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmware-solutions-trbl_support)
