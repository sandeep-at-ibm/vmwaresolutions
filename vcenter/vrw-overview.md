---

copyright:

  years:  2020, 2021

lastupdated: "2021-06-03"

keywords: regulated workloads, workloads instance, regulated instance

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware Regulated Workloads overview
{: #vrw-overview}

The VMware® Regulated Workloads offering includes a secure-by-default architecture that follows the IBM unique policy controls framework. It also includes continuous compliance monitoring and the highest level of data encryption FIPS 140-2 Level 4.

Review the following specifications before you begin.
* The VMware Regulated Workloads offering is available for both single-zone and multizone region topologies.
* VMware Regulated Workloads are based on VMware NSX-T™ and VMware vSphere® 7.
* [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services), [KMIP for VMware](https://cloud.ibm.com/infrastructure/vmware-solutions/console/servicestandalonenew/KMIPAdapter), and [Direct Link Dedicated](https://cloud.ibm.com/interconnectivity/direct-link) are required for the VMware Regulated Workloads. Ensure that you order these services before you start your VMware Regulated Workloads order.
* If you are planning to bring your own licenses (BYOLs) for the VMware components, ensure that you have the complete list of BYOL licenses that are required.
* Some of the services require configuration setup. Review each service and ensure that you configure its settings properly, as indicated.
* The **Private network only** option is available for all clusters. The **Public and private network** option is available only for the edge services cluster.

## Options not available for VMware Regulated Workloads
{: #vrw-overview-before-not-avail-options}

The following options or settings are not available for VMware Regulated Workloads:
* VMware Subscription Purchasing Program
* Local disks
* High performance with Intel® Optane
* vSAN™ deduplication and compression
* Selection of existing VLANs. Only the option to order new VLANs is available.
* Single public Windows® VSI for Active Directory™ DNS configuration. Only the option to order two highly available dedicated Windows server virtual machines (VMs) on the management cluster is available.

## Related links
{: #vrw-overview-related}

* [VMware Regulated Workloads reference architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-archi-overview)
* [Requirements and planning for VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-planning)
* [Ordering VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-orderinginstance)
* [Viewing and deleting VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-view-delete-instance)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
