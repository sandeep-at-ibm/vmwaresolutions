---

copyright:

  years:  2020, 2021

lastupdated: "2021-01-15"

keywords: release notes, what's new, version 3.9

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.9
{: #relnotes_v39}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Updates for VMware Solutions Shared
{: #relnotes_v39-shared}

This release applies the following upgrades when you order VMware Solutions Shared instances.

### Support for Dallas 12 and Dallas 13 IBM Cloud data centers
{: #relnotes_v39-shared-dc}

The Dallas 12 and Dallas 13 {{site.data.keyword.cloud}} data centers are now available for deployment on VMware Solutions Shared instances. For more information, see [Requirements and planning for VMware Solutions Shared
](/docs/vmwaresolutions?topic=vmwaresolutions-shared_planning).

### Integration with IBM Cloud Monitoring
{: #relnotes_v39-shared-monitor}

You can now use {{site.data.keyword.cloud_notm}} Monitoring to view and customize dashboards to visualize performance, volume of usage, and to define alerts to monitor your environment. For more information, see [Visualizing your virtual data center instance environment with IBM Cloud Monitoring](/docs/vmwaresolutions?topic=vmwaresolutions-shared-monitor).

## Updates for VMware Solutions Dedicated
{: #relnotes_v39-dedicated}

This release applies the following updates when you order VMware Solutions Dedicated instances.

### Removed support for VMware vSphere 6.5u3
{: #relnotes_v39-dedicated-vsphere-6.5}

VMware vSphere® 6.5u3 is no longer supported for new VMware vCenter Server® instances. Full support remains for existing instances, including support to add new hosts and clusters.

VMware vSphere 6.5u3 is no longer supported for new VMware vSphere clusters. Full support remains for existing clusters, including support to add new hosts.

### VMware NSX updates
{: #relnotes_v39-dedicated-vmware-nsx-updates}

Review the following information about vCenter Server with NSX-T instances for this release:

* New instances of vCenter Server with NSX-T are provisioned with NSX-T 3.0.1.1.
* Day 2 operations continue to be supported for vCenter Server with NSX-T 2.5.1 instances. For restrictions about Red Hat OpenShift for VMware on vCenter Server with NSX-T instances, see [Updates for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-relnotes_v39#relnotes_v39-services).
* If you want to upgrade your existing vCenter Server with NSX-T instance, you must upgrade to NSX-T 3.0.2.

### New Cascade Lake server support
{: #relnotes_v39-dedicated-CascadeLake-servers}

Starting with the v3.9 release, the following {{site.data.keyword.cloud_notm}} bare metal servers are available for deployment for vCenter Server instances and vSphere clusters with vSphere 6.7:

* Dual Intel Xeon Platinum 8260 (Cascade) / 48 Cores, 2.40 GHz / 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB
* Quad Intel Xeon Platinum 8260 (Cascade) / 96 Cores, 2.40 GHz / 384 GB, 768 GB, 1.5 TB, 3 TB

### Support for Osaka IBM Cloud data centers
{: #relnotes_v39-dedicated-osaka}

The following {{site.data.keyword.cloud_notm}} data centers are available for deployment on vCenter Server, VMware vSphere, and {{site.data.keyword.cloud_notm}} for VMware® Mission Critical Workloads instances: **Osaka 21**, **Osaka 22**, and **Osaka 23**.

### Updates for the edge services cluster
{: #relnotes_v39-dedicated-edge-services-cluster}

The CPU model for new deployments of vCenter Server instance edge services clusters is Dual Intel Xeon Silver 4210 (Cascade).

### Increased local disk count
{: #relnotes_v39-dedicated-local-disks}

For new vCenter Server instances and new clusters added to vCenter Server instances, the local disks option for storage now supports 10 and 12 disks. For more information, see [Local disks for NSX-V SAP-certified HANA only](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-local-disks).

## Updates for add-on services
{: #relnotes_v39-services}

This release provides the following service versions on newly deployed instances:

* BIG-IP® VE v15.1.0.5
* HyTrust® CloudControl™ v6.2 for vCenter Server with NSX-T

  During the pre-configuration of HyTrust CloudControl v6.2, global PIP is enabled.
* Juniper® vSRX and Juniper vSRX Gateway Appliance 3.0 (20.1R1.11)

  For information about vSRX 3.0, see [Overview of the available virtual SRX models, vSRX and vSRX 3.0](https://kb.juniper.net/InfoCenter/index?page=content&id=KB33572){:external}.
* Red Hat® OpenShift® for VMware® v4.4.23

  You can now install the Red Hat OpenShift for VMware service on vCenter Server with NSX-T instances. For NSX-T, you must have a new vCenter Server instance with NSX-T that is provisioned with NSX-T 3.0.1.1 or you must upgrade from NSX-T 2.5.1 to NSX-T 3.0.2.

  For information about how the target cluster is selected if you have NSX-V or NSX-T, see [Selection of the target cluster for installation](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview#ocp_overview-select-target-cluster).

### HyTrust CloudControl for vCenter Server with NSX-V - deprecated
{: #relnotes_v39-services-htcc-nsx-v-deprecated}

New installations of HyTrust CloudControl are no longer supported for new or existing deployments of vCenter Server with NSX-V instances. You can still view or delete existing HyTrust CloudControl installations on your existing instances.
{:deprecated}

## Updates to REST APIs
{: #relnotes_v39-api}

Various updates are made to the [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) and the [VMware Solutions Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared) documentation.

## User interface updates and enhancements
{: #relnotes_v39-ui}

The user interface is updated and provides the following enhancements:

* A new **Uplink speed** option is available in the **Network interface** section when you order vCenter Server instances, order new vSphere clusters, and add clusters for vCenter Server instances.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
