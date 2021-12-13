---

copyright:

  years:  2016, 2021

lastupdated: "2021-12-10"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Zerto overview
{: #addingzertodr}

The Zerto service integrates replication and disaster recovery capabilities into the deployment offerings to protect and recover data in your VMware® virtual environment on {{site.data.keyword.cloud}}. Zerto is supported on VMware vCenter Server® instances with:

* VMware NSX-V
* VMware NSX-T™ 3.1 or later with VMware vSphere® 7.0
{: shortdesc}

{{site.data.keyword.vmwaresolutions_short}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices#vc_addingservices-service-promotions).

The current Zerto version that is installed is 9.0u1.
{: note}

## Before you begin
{: #addingzertodr-req}

* Ensure that your {{site.data.keyword.cloud_notm}} account is a billable account, and that it is linked to the {{site.data.keyword.cloud_notm}} infrastructure account where your instance is deployed. For more information, see [Billing for Zerto replication](/docs/vmwaresolutions?topic=vmwaresolutions-zerto_ordering#zerto_ordering-billing).
* This service is available only to instances that are deployed in V1.2 or later.

## Technical specifications for Zerto
{: #addingzertodr-specs}

For more information about resource requirements and capacity checking for some services, see [Resource requirements for services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices#vc_addingservices-resource-requirements).

The following components are ordered and included in the Zerto service.

Zerto Virtual Replication Appliance (VRA) components are deployed only into the default cluster.
{: note}

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

Zerto Replication version 9.0u1 license

## Related links
{: #addingzertodr-related}

* [Ordering Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-zerto_ordering)
* [Managing Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-managingzertodr)
* [Ordering Zerto licenses](/docs/vmwaresolutions?topic=vmwaresolutions-zerto_ordering_licenses)
* [Managing Zerto licenses](/docs/vmwaresolutions?topic=vmwaresolutions-zerto_managing_licenses)
* [Managed Disaster Recovery Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_zerto_services)
* [Zerto](https://www.zerto.com){: external}
* [Zerto product documentation](https://www.zerto.com/myzerto/technical-documentation/){: external}
