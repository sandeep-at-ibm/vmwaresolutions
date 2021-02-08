---

copyright:

  years:  2021

lastupdated: "2021-01-28"

keywords: release notes, what's new, version 4.0

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V4.0
{: #relnotes_v40}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Regulated workloads enhancements
{: #relnotes_v40-regulated-workloads}

You can now order regulated workloads directly from the VMware® Solutions main page. The regulated workloads include a secure-by-default architecture that follows IBM's unique policy controls framework, provides continuous compliance monitoring, and offers the highest level of data encryption (FIPS 140-2 Level 4). For regulated workloads, only VMware vSphere® 7.0 Update 1a is supported.

For more information, see [Regulated workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-overview).

## Updates for VMware Solutions Dedicated
{: #relnotes_v40-dedicated}

This release applies the following updates when you order VMware Solutions Dedicated instances.

### VMware vSphere 7.0 Update 1a support
{: #relnotes_v40-dedicated-vsphere-v70}

You can order vSphere 7.0 Update 1a with your VMware vCenter Server® with NSX-T instances and VMware vSphere with NSX-T clusters. vSphere 7.0u1a introduces the following support and enhancements:

* Smaller instance footprint with support for converged management and workload cluster. vSphere 6.7 and NSX-T require eight hosts when using vSAN™ storage and five hosts when using NFS storage. vSphere 7.0u1a enables a footprint of four hosts when using vSAN storage and three hosts when using NFS storage.
* Full support for the HTML5 vSphere web client
* Support for Intel® Cascade Lake EVC level
* The enhanced VMware vSphere Lifecycle Manager (LCM)
* Enhancements to VMware vSphere Distributed Resource Scheduler (DRS) and VMware vSphere vMotion
* Security enhancements that include multi–factor authentication (MFA) and vSphere Trust Authority (vTA)

vSphere 7.0u1a is the exclusive basis for {{site.data.keyword.cloud}} for VMware Regulated Workloads and is available for Cascade Lake and SAP-certified bare metal servers only.

vSphere 7.0u1a currently does not support 25 Gb uplink speed or High performance with Intel Optane for vSAN storage. Support for these features is planned for a future release. Additionally, vSphere 7.0u1a does not support single-node instances.
{:note}

### vSAN storage for vSphere 7.0 Update 1a - not for production use
{: #relnotes_v40-vsan-tech-preview}

For VMware vSphere 7.0 Update 1a, VMware vSAN storage is offered as a beta feature.

IBM and its Business Partners are working to complete full certification and to finalize the vSAN listing in the VMware Compatibility Guide for all new firmware and drivers necessary to support vSphere 7.0u1a.

Final certification is planned for 26 February 2021. However, this date is subject to change. Until certification is complete, {{site.data.keyword.cloud_notm}} provides best-effort support on any issue.

Until the certification is complete, you might see the following warning messages:

* A warning message displays on the VMware Solutions console for vSAN storage with vSphere 7.0u1a. After certification is complete, workloads can run on vSAN clusters and no further action is required from your part.
* A warning message displays when you log in to the vCenter Server through the vSphere Web Client. When the certification is complete, you must download the latest version of the vSAN HCL DB file and update vCenter to remove the warning. For more information, see [Updating the vSAN HCL database manually (2145116)](https://kb.vmware.com/s/article/2145116){:external}.

### Your existing instances and vSphere 7.0 Update 1a
{: #relnotes_v40-dedicated-vsphere-v70-no-support}

For vCenter Server instances with vSphere 6.5 or vSphere 6.7, in-place upgrade to vSphere 7.0 is not currently supported due to changes in VMware license keys and changes in the vCenter Server architecture and topology.
{:note}

Carefully review the VMware product lifecycle matrix for ESXi and NSX as part of your planning. For more information, see [Product LifeCycle Matrix](https://lifecycle.vmware.com/){:external}.

{{site.data.keyword.cloud_notm}} plans to publish guidance for upgrading your existing instance to vSphere 7.0 in a future VMware Solutions release. However, an upgrade cannot be supported for all hardware combinations, will not accomplish a migration from NSX-V to NSX-T, and will enable only limited VMware Solutions capabilities at the vSphere 7.0 level.

Instead, {{site.data.keyword.cloud_notm}} recommends that you deploy a new vSphere 7.0 instance and migrate your current network topology and workload to the new instance. For more information about assistance with your network and workload migration, see [VMware HCX updates](#relnotes_v40-services-HCX).

Migrating your workload to a new instance is especially recommended if you want to perform a hardware refresh, if you want to migrate from NSX–V to NSX–T, or if you want to migrate your existing NSX–T topology with separate management and workload clusters to a converged topology.

### Support for VMware stretched vSAN clusters for vSphere 7.0 Update 1a and NSX-T 3.1
{: #relnotes_v40-dedicated-stretched-v70}

VMware vSphere Enterprise Plus 7.0 Update 1a and VMware NSX-T 3.1 are included when you order a VMware vCenter Server stretched cluster across a multizone region. The stretched cluster is deployed as a single converged cluster capable of hosting both management and workload clusters. The combination of converged cluster and support for a 3-host RAID-1 configuration enables you to deploy an instance with a minimum of eight hosts when you use NFS storage for your witness cluster, or nine hosts when you use vSAN storage for your witness cluster.

Additional features for stretched clusters are planned for future releases, including support for regulated workloads, edge services clusters, additional workload clusters, and optional add-on services.
{:note}

### Updates for VMware NSX
{: #relnotes_v40-dedicated-vmware-nsx-updates}

Review the following information about vCenter Server with NSX-T instances for this release:

* New instances of vCenter Server with NSX-T are provisioned with NSX-T 3.1.
* Day 2 operations continue to be supported for vCenter Server with NSX-T 2.5.1 instances. For restrictions about Red Hat® OpenShift® for VMware on vCenter Server with NSX-T instances, see [Updates for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-relnotes_v40#relnotes_v40-services).
* If you want to upgrade your existing vCenter Server with NSX-T instance, {{site.data.keyword.cloud_notm}} recommends that you upgrade directly to NSX-T 3.1 bypassing NSX-T 3.0.x.

### Updates to data centers
{: #relnotes_v40-dedicated-dc}

* The new data centers **Toronto 04** and **Toronto 05** are available for deployment of vCenter Server instances and vSphere clusters.
* The new region **Toronto** is available for deployment of VMware Mission Critical Workloads.
* The data center **Oslo 01** is no longer available for new deployments.

## Single-node offerings - deprecated
{: #relnotes_v40-single-node-deprecated}

The Single-node for Migration and App Modernization and Single-node for Data Protection and Disaster Recovery offerings are no longer provided for new deployments. Full support remains for existing single-node instances.
{:deprecated}

## Updates for add-on services
{: #relnotes_v40-services}

This release provides the following service versions on newly deployed instances:

* Caveonix RiskForesight™ v2.4
* HyTrust® CloudControl™ v6.2.1 for vCenter Server with NSX-T
* Juniper® vSRX and Juniper vSRX Gateway Appliance 3.0 (20.1R2)

  For more information about vSRX Gateway Appliance 3.0, see [Overview of the available virtual SRX models, vSRX, and vSRX 3.0](https://kb.juniper.net/InfoCenter/index?page=content&id=KB33572){:external}.
* Red Hat OpenShift v4.6
  * New installations of Red Hat OpenShift on vCenter Server require VMware vSphere 7.0 Update 1a with NSX-T 3.1. For NSX-T 2.5.1 deployments, you must upgrade to vSphere 7.0 Update 1a with NSX-T 3.1.
  * During deployment and day 2 operations, you are prompted for the cluster. You can install the service to the management cluster or any workload cluster.
* Veeam® v10a
* vRealize Operations™ v8.2 and Log Insight™ v8.2

### Add-on services that support VMware vSphere 7.0 Update 1a
{: #relnotes_v40-services-vsphere-v70}

The following add-on services support VMware vSphere 7.0 Update 1a:

* Caveonix RiskForesight
* VMware HCX™
* HyTrust CloudControl
* Juniper vSRX
* Red Hat OpenShift
* Veeam
* vRealize Operations

### Red Hat OpenShift on vSphere 6.7 with NSX-V or NSX-T and on vSphere 6.5 with NSX-V - deprecated
{: #relnotes_v40-services-rhos-vsphere67-deprecated}

Red Hat OpenShift is no longer supported for new deployments or for ordering post deployment with NSX-V or NSX-T on vSphere 6.7 or NSX-V on vSphere 6.5.
{:deprecated}

### Juniper vSRX enhancements
{: #relnotes_v40-services-vsrx-security-enhance}

For vCenter Server instances, Juniper vSRX management and edge services cluster installations provide the following enhancements:

* Useful address book entries
* Security enhancements based on CIS guidelines
* vSRX logging to vRealize Log Insight™ if the vRealize Operations add-on service is already installed

For more information, see [Juniper vSRX security and ease of use features](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-managing#juniper-managing-security-enhance).

### VMware HCX updates
{: #relnotes_v40-services-HCX}

HCX is no longer supported for new deployments on vSphere 6.7 with NSX-T or for ordering post deployment on existing vSphere 6.7 instances with NSX-T.
{:note}

Review the following information about the VMware HCX service for this release:

* VMware HCX is now offered on vSphere 7.0 Update 1a for vCenter Server with NSX-T 3.1 instances. HCX is not supported on vSphere 6.7 for vCenter Server with NSX-T 3.1 instances.
* The 12-month commitment for HCX is removed.
* The private interconnect option is removed. The network connection options are either public or private.
* You can choose the target cluster for service mesh (NSX-T only).
* The HCX service is removed if the service mesh target cluster is removed on NSX-T.
* If the management cluster or HCX service mesh target cluster is private only, the only connection type would be private connection. If the connection type is private, a proxy is required.

### vSAN storage requirements for VMware vRealize Operations
{: #relnotes_v40-services-vsan-storagereqs-vrops}

If you install VMware vRealize Operations (vROps) and select vSAN storage, you must have an estimated 750 GB of vSAN storage to successfully install vROps. This storage requirement does not apply to NFS.

For more information, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

### Updates for Caveonix RiskForesight
{: #relnotes_v40-services-caveonix}

Starting with the v4.0 release, RiskForesight v2.4 applies the following updates:

* Updates the regulated workload presets to order 50 licenses, rather than 10.
* Connects to NSX through FQDN, rather than to its IP address.

When you order RiskForesight, you can now select 10 - 25,000 VMs to license, in increments of 10. The RiskForesight license is valid for five years.

### DNS entries removal
{: #relnotes_v40-services-remove-dns-entries}

For several add-on services, if you installed the service before the {{site.data.keyword.vmwaresolutions_short}} v4.0 release and you then delete the service, you must remove the DNS entries manually. For more information, see [Manually removing the DNS entries](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-remove-DNS-entries).

### Updates for KMIP for VMware
{: #relnotes_v40-services-kmip}

Previously, KMIP™ for VMware provided a multi-tenant service that enables VMware vCenter Server to use IBM Key Protect for {{site.data.keyword.cloud_notm}} (Key Protect) and {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services (HPCS) as its key manager.

Starting with the V4.0 release, newly created KMIP for VMware instances that are connected to HPCS now operate as single-tenant services. These services run within the HPCS service and benefit from the features of IBM Secure Service Containers on IBM LinuxONE servers. You can connect only a single KMIP for VMware instance to each HPCS instance.

KMIP for VMware continues to provide a multi-tenant service when you connect to Key Protect. For more information, see [KMIP for VMware design](/docs/vmwaresolutions?topic=vmwaresolutions-kmip-design).

In addition, two new endpoints are now available in the **Osaka** location for KMIP for VMware.

## Updates to REST APIs
{: #relnotes_v40-api}

* REST API support for the VMware HCX service is now available.
* Various other updates are made to the [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) and the [VMware Solutions Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared) documentation.

## New and updated documentation
{: #relnotes_v40-updated-doc}

A new topic, [Managing security and compliance](/docs/vmwaresolutions?topic=vmwaresolutions-manage-scc), is now available. The topic provides information about monitoring security and compliance posture with VMware Solutions by using Caveonix RiskForesight.

## User interface updates and enhancements
{: #relnotes_v40-ui}

The user interface is updated and provides the following enhancements:

* The following enhancements are made to the landing page of {{site.data.keyword.vmwaresolutions_short}} console to better assist you in learning and selecting the appropriate offering and services according to your needs:
   * The previous **Start provisioning** section is renamed to **IaaS platforms**.
   * A new **Regulated workloads** section is added.
   * The previous **Services** section is renamed to **Add-on services**.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
