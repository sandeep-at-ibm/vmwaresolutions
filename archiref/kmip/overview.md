---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware overview
{: #kmip-overview}

This solution architecture describes the KMIP on VMware architecture for protecting your VMware instances. Many storage encryption options are available to protect your VMware workload. KMIP for VMware works together with VMware native vSphere encryption and vSAN encryption to provide simplified storage encryption management together with the security and flexibility of {{site.data.keyword.cloud_notm}} Key Protect or {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services customer-managed keys.

This solution is considered to be an extra component and extension of the vCenter Server offering on {{site.data.keyword.cloud_notm}}. As a result, this document doesn't cover the existing configuration of these foundation solutions on {{site.data.keyword.cloud_notm}}. To understand more about the foundation solution architecture, see [Overview of {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview).

## Key benefits
{: #kmip-overview-benefits}

While many storage encryption solutions are available for your VMware workload, KMIP for VMware offers the following benefits:

* Integration with VMware vSAN encryption and vSphere encryption, both of which are implemented in the hypervisor layer rather than the storage or virtual machine layer. This approach allows easy management and transparency to your storage solution and application.
* Fully managed key management server available in many {{site.data.keyword.cloud_notm}} multi-zone regions (MZRs).
* Integrating your VMware cluster with {{site.data.keyword.cloud_notm}} Key Protect or {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services provides you with fully customer-managed keys that you can revoke at any time.

**Next topic:** [KMIP for VMware design](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip-design)

## Related links
{: #kmip-overview-related}

* [Solution design](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip-design)
* [Implementation and management](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip-implementation)
