---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server multi-site, multi-site configuration, multi-site deployment vCenter Server

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Multi-site configuration for vCenter Server on IBM Cloud instances
{: #vc_multisite}

{{site.data.keyword.vmwaresolutions_full}} allows instances to be deployed across different locations and have them up and running in a short time.

Multi-site configuration for vCenter Server instances is supported only for V2.0 and later instances.
{:note}

## Multi-site deployment components
{: #vc_multisite-deployment-components}

A multi-site deployment consists of the following components.

* **Primary instance**: The primary VMware vCenter Server instance has the following configuration:
  *  Microsoft Active Directory (AD) and DNS (Domain Name System) root domain
  *  vCenter Server subdomain
  *  SSO (Single Sign-On) domain
  *  SSO site name
* **Secondary instance or instances**: One or more secondary vCenter Server instances, linked to the primary instance, with the following configuration:
   *  SSO site name
   *  DNS subdomain that is linked to the root domain on the primary instance
   *  DNS and AD replication set-up between the AD virtual machines on the primary and secondary instances
   *  For primary instances that are deployed in V2.8 or later: vCenter Server Appliance (vCSA) with embedded Platform Services Controller (PSC) is deployed and configured
   *  VMware vCenter on the secondary instances is set up with Enhanced Linked Mode to the vCenter on the primary instance

## vCenter Server multi-site deployment
{: #vc_multisite-deployment}

The multi-site configuration feature uses a hub and spoke topology with a primary site and a maximum of seven secondary sites. A single layer of sites is supported, that is, you cannot configure subsequent sites that are linked to other secondary sites. You can have a total of 128 ESXi servers in a multi-site configuration across all instances.

If your configuration requires a multi-site deployment with more than 128 ESXi servers, contact IBM Support for assistance. For more information, see [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).
{:note}

The following graphic depicts the overall view of the vCenter Server multi-site deployment.

![vCenter Server multi-site deployment](../images/multisite-hub-spoke.svg "vCenter Server multi-site deployment"){: caption="Figure 1. vCenter Server multi-site deployment" caption-side="bottom"}

The model contains the following layers:

* **Primary instance**: In a multi-site configuration, to deploy the first instance, you define that instance as primary during the instance order process.
* **Secondary instances**: In a multi-site configuration, you define the instances that are attached to the primary instance as secondary instances during the order process.

You can assign only one secondary instance to a primary instance at a time. You cannot assign multiple secondary instances to a primary instance at the same time. To do that, you must go through the order process again and select the previously defined primary instance as a primary instance for the secondary instance. You must repeat the process for all secondary instances that you want to create.

You can have a maximum of 8 (1 primary and 7 secondary) instances that are deployed in a multi-site configuration.

Deleting vCenter Server instances that are part of a multi-site configuration requires special planning. For more information, see [Deleting vCenter Server instances in a multi-site configuration](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance_multi).
{:note}

## Related links
{: #vc_multisite-related}

* [Assign Primary Role to NSX Manager](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:external}
* [Configuring Secondary NSX Managers](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:external}
* [Microsoft Active Directory Trusts supported with VMware vCenter Single Sign-On](https://kb.vmware.com/s/article/2064250){:external}
