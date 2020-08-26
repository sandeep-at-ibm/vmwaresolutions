---

copyright:

  years:  2020

lastupdated: "2020-08-24"

keywords: release notes, what's new, version 3.8

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.8
{: #relnotes_v38}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Updates for VMware Solutions Shared
{: #relnotes_v38-shared}

(Updated on August 25, 2020) VMware® Solutions provides an upgrade to the Shared infrastructure to the latest version of VMware vCloud Director (vCD) v10.1.1. The v10.1.1 update is available to Dallas and Frankfurt {{site.data.keyword.cloud}} data centers.

The Flash portal is no longer available with the v10.1.1 update.
{:note}

### Storage policy updates
{: #relnotes_v38-shared-storage}

* For existing storage policies in your virtual data center, the default storage policy is now the new *standard* storage policy. Previously, the default storage policy was *4 IOPS/GB*. This default storage policy is automatic for new VMware Solutions Shared instances.

* This release introduces *Standard* storage policies and *Encrypted* storage policies. These new storage policies are available for new VMware Solutions Shared instances and added to existing VMware Solutions Shared instances with the VMware vCloud Director (vCD) v10.1.1 upgrade.

For more information about storage policies, see the *Storage* section in [Technical specifications for VMware Solutions Shared
](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview#shared_overview-specs-storage).

#### Standard storage policies
{: #relnotes_v38-shared-storage-standard}

A standard storage policy is now available for both decrypted and encrypted policies. The standard storage policy has no maximum throughput, but the number of IOPS/GB is not guaranteed.

#### Encrypted storage policies
{: #relnotes_v38-shared-storage-encryption}

VMware vCloud Director v10.1.1 provides the capability to create encryption enabled storage policies to all organization virtual data centers. Administrators can encrypt virtual machines (VMs) and disks by associating the VM or disk with a storage policy that has the VM encryption capability.

### Off-site copy mode availability for Veeam Availability Suite
{: #relnotes_v38-shared-off-site}

Veeam Availability Suite off-site copy mode is now automatically enabled for new and existing VMware Solutions Shared instances. For more information, see the *Veeam Availability Suite* section in [Managing Veeam for VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_veeam) instances.

## Updates for VMware Solutions Dedicated
{: #relnotes_v38-dedicated}

This release applies the following updates when you order VMware Solutions Dedicated instances.

### VMware vSphere 6.7u3 support
{: #relnotes_v38-dedicated-vsphere-v67}

You can order VMware vSphere® 6.7u3 with your VMware vCenter Server® instances and VMware vSphere® clusters. vSphere Enterprise Plus 6.7u3 replaces the option to order vSphere Enterprise Plus 6.7u2 with new instances. Additionally, Single-node Trial for Migration and App Modernization and Single-node Trial for Data Protection and Disaster Recovery instances are now ordered with vSphere Enterprise Plus 6.7u3.

vSphere Enterprise Plus 6.7u3 is available for Skylake, Cascade Lake, and Cascade Lake SAP {{site.data.keyword.cloud_notm}} bare metal servers.

If you have an existing instance with vSphere Enterprise Plus 6.7u2, you can add new ESXi servers with either vSphere Enterprise Plus 6.7u2 or vSphere Enterprise Plus 6.7u3.
{:note}

### vSphere ESXi 6.7u2 for vSAN storage
{: #relnotes_v38-dedicated-esxi-vsan}

For vSAN storage, even though vSphere 6.7u3 is selected on the user interface, vSphere ESXi 6.7u2 will be installed. This distinction applies to:
* Newly deployed vCenter Server instances.
* New clusters that are added to new and existing vCenter Server instances.
* New ESXi servers that are added to new and existing vCenter Server instances.

For NFS storage, vSphere ESXi 6.7u3 will be installed.

### VMware NSX-T 3.0.1 support
{: #relnotes_v38-dedicated-nsx-t}

New VMware vCenter Server® with NSX-T instances are now deployed with NSX-T v3.0.1 instead of v2.5.1. Day 2 operations continue to be supported for vCenter Server with NSX-T v2.5.1 instances.

### Updates for IBM Cloud for VMware Mission Critical Workloads
{: #relnotes_v38-mcv}

Starting with v3.8, all newly deployed {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads instances are provisioned with NSX-T.

## Updates for add-on services
{: #relnotes_v38-services}

This release provides the following service versions on newly deployed instances:

* BIG-IP® VE v15.1.0.4
* HyTrust® CloudControl™ v6.1.1 for vCenter Server with NSX-T
* Juniper® vSRX and Juniper vSRX Gateway Appliance v19.4R2.6
* Red Hat® OpenShift® for VMware v4.4.13

### Promotions for VMware Solutions add-on services
{: #relnotes_v38-services-promo-codes}

Starting with v3.8, {{site.data.keyword.vmwaresolutions_short}} offers promotions for some VMware services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges.

You can use one promotion (promo) code for one or more services for:
* Ordering a new VMware vCenter Server
* Adding a service to an existing vCenter Server
* Ordering a stand-alone service (license), such as Caveonix or Veeam®

For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

### Resource requirements for add-on services
{: #relnotes_v38-services-resource-reqs-services}

In this release, capacity checks are performed to ensure that resource requirements are met for services installation. Capacity checks are performed for the following services during instance deployment:
* Caveonix RiskForesight™
* F5 BIG-IP
* FortiGate® Virtual Appliance
* HyTrust CloudControl
* Zerto

For more information, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

### Selecting the target cluster for Red Hat OpenShift for VMware
{: #relnotes_v38-services-select-target-cluster}

Starting with v3.8, the target cluster for installing Red Hat OpenShift varies:
* During deployment, you aren't prompted for the cluster. The service is automatically installed to the management cluster.
* During day 2 operations, you are prompted for the cluster. You can install the service to a management cluster or a workload cluster.

For more information, see [Selection of the target cluster for installation](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview#ocp_overview-select-target-cluster).

### Deleting services from a cluster before deleting the cluster
{: #relnotes_v38-services-delete-cluster}

Starting with v3.8, if you remove a non-management cluster that has services installed on it, the services are also deleted as part of the process.

Previously, when you removed a non-management cluster, for example, an edge services cluster, any services installed on that cluster were not removed. You had to first delete the services from the cluster and then delete the cluster itself.

This change affects the Juniper vSRX and Red Hat OpenShift for VMware services.

## Updates to REST APIs
{: #relnotes_v38-api}

Various updates are made to the [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) and the [VMware Solutions Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared) documentation.

## New and updated documentation
{: #relnotes_v38-updated-doc}

A new topic, [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements), is now available.

The topic describes how capacity checking works for various services and what resources are required to install certain services, such as Caveonix RiskForesight, Juniper vSRX, and Veeam. The information replaces the documentation that was provided in the overviews of the individual services.

## User interface updates and enhancements
{: #relnotes_v38-ui}

The user interface is updated and provides the following enhancements:

* A checklist is added at the beginning of the ordering pages to help you prepare your environment when you place an order for the first time. This feature does not apply to the following instances and services:
   * Single-node Trial for Migration and App Modernization instances
   * Single-node Trial for Data Protection and Disaster Recovery instances
   * KMIP™ for VMware instances
   * On-premises VMware HCX instances
   * Caveonix RiskForesight licenses
   * Veeam licenses

  For more information, see [Setting up your environment for your first order](/docs/vmwaresolutions?topic=vmwaresolutions-completing_checklist).
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
