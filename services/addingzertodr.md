---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-15"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto overview
{: #addingzertodr}

The Zerto service integrates replication and disaster recovery capabilities into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud_notm}}.

The current Zerto version that is installed is 7.0 Update 2.
{:note}

## Before you begin
{: #addingzertodr-req}

* Ensure that your {{site.data.keyword.cloud_notm}} account is a billable account, and that it is linked to the {{site.data.keyword.cloud_notm}} infrastructure account where your instance is deployed. For more information, see [Billing for Zerto replication](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).
* This service is available only to instances that are deployed in V1.2 or later.

## Technical specifications for Zerto
{: #addingzertodr-specs}

The following components are ordered and included in the Zerto service.

Zerto Virtual Replication Appliance (VRA) components are deployed only into the default cluster.
{:note}

### Virtual Service Instances
{: #addingzertodr-specs-vsi}

* One Virtual Service Instance (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz cores
* 4 GB RAM
* Windows Server 2016 Standard Edition (64-bit)

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

Zerto Replication V6.5 update 3 license

## Related links
{: #addingzertodr-related}

* [Ordering Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Managing Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Managed Disaster Recovery Services](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com website](https://www.zerto.com){: external}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){: external}
