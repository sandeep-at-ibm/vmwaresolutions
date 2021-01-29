---

copyright:

  years:  2016, 2021

lastupdated: "2021-01-28"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto overview
{: #addingzertodr}

The Zerto service integrates replication and disaster recovery capabilities into the deployment offerings to protect and recover data in your VMware® virtual environment on {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.vmwaresolutions_short}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

The Zerto service is not supported for VMware vCenter Server® with NSX-T instances. For vCenter Server with NSX-V instances, the installed version is 7.5 Update 3.
{:note}

## Before you begin
{: #addingzertodr-req}

* Ensure that your {{site.data.keyword.cloud_notm}} account is a billable account, and that it is linked to the {{site.data.keyword.cloud_notm}} infrastructure account where your instance is deployed. For more information, see [Billing for Zerto replication](/docs/vmwaresolutions?topic=vmwaresolutions-zerto_ordering#zerto_ordering-billing).
* This service is available only to instances that are deployed in V1.2 or later.

## Technical specifications for Zerto
{: #addingzertodr-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

The following components are ordered and included in the Zerto service.

Zerto Virtual Replication Appliance (VRA) components are deployed only into the default cluster.
{:note}

### Virtual Service Instances
{: #addingzertodr-specs-vsi}

* One Virtual Service Instance (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz cores
* 4 GB RAM
* Windows® Server 2019 Standard Edition (64-bit)

### Storage
{: #addingzertodr-specs-storage}

100 GB (SAN) disk

### Networking
{: #addingzertodr-specs-network}

* VSI
  * One primary private IP address
  * 1 Gbps private network uplink
* Virtual replication appliances (VRAs)
  * One private portable subnet for VRA deployment

### Licenses and fees
{: #addingzertodr-specs-licenses}

Zerto Replication 7.5 Update 3 license

## Related links
{: #addingzertodr-related}

* [Ordering Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-zerto_ordering)
* [Managing Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-managingzertodr)
* [Managed Disaster Recovery Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_zerto_services)
* [zerto.com website](https://www.zerto.com){: external}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){: external}
