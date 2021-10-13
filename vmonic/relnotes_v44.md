---

copyright:

  years:  2021

lastupdated: "2021-10-13"

keywords: release notes, what's new, version 4.4

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for V4.4
{: #relnotes_v44}

This release includes new features, component updates, usability enhancements, and bug fixes.

## End of Support for instance deployments with vSphere 6.5
{: #relnotes_v44-eos-vsphere-65}

{{site.data.keyword.cloud}} support for ordering all update levels of VMware® vSphere® 6.5 ended on 10 October 2021.

Beginning on this date, you can no longer order new VMware vCenter Server® instances with vSphere 6.5 and your existing vCenter Server instances with vSphere 6.5 become read–only in the VMware Solutions console and through the public REST API.

Until you upgrade to vSphere 6.7 or later, you cannot perform operations such as:
* Adding and deleting clusters.
* Adding and removing ESXi servers.
* Adding and removing storage.
* Adding and deleting services.

You can still view and delete your existing instances with vSphere 6.5.

{{site.data.keyword.cloud_notm}} will continue to support your infrastructure on our cloud and will continue to support the vSphere 6.5 software until the [VMware announced end of support date](https://lifecycle.vmware.com/#/){: external} of 15 October 2022.

vSphere 6.5 is superseded by vSphere 6.7 and vSphere 7.0. If you have active workloads on vSphere 6.5, consider upgrading or migrating to vSphere 6.7 or vSphere 7.0 today. The documentation provides instructions and considerations for upgrading to [vSphere 6.7](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vsphere_upgrade) and [vSphere 7.0](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vsphere_70_upgrade).

{{site.data.keyword.cloud_notm}} recommends you move to vSphere 7.0, the latest VMware vSphere version, which is the focus of feature investment for both VMware® and {{site.data.keyword.cloud_notm}}. Furthermore, {{site.data.keyword.cloud_notm}} recommends that you migrate rather than upgrade to vSphere 7.0. Migration ensures that you are aligned with current and supported hardware, other {{site.data.keyword.cloud_notm}} features, and the recommended vSphere 7 NSX–T topology, including the use of VDS switches.

Before you upgrade, IBM recommends that you assess your environments for infrastructure and workload dependencies to ensure that they are supported for the current version.

vSphere 6.7 introduces support for embedded Platform Services Controller (PSC), improved support for the HTML5 client including vSAN management, support for Intel® Skylake EVC level, support for virtual TPM, improved support for VMware Update Manager (VUM), and vSAN support for Windows® Failover Clustering.

vSphere 7.0 introduces full support for the HTML5 client, support for Intel Cascade Lake EVC level, the enhanced vSphere Lifecycle Manager (LCM), enhancements to DRS and vMotion, security enhancements including multi–factor authentication (MFA), vSphere Trust Authority (vTA), and in–flight encryption for vSAN. vSphere 7.0 is also the exclusive basis for VMware Regulated Workloads.

For more information about end of life procedures for {{site.data.keyword.cloud_notm}} infrastructure services and Third–Party software products, see [Lifecycle policy for IBM Cloud products](https://www.ibm.com/cloud/cloud-prod-life). If you have any questions or need assistance, email clouddigitalsales@us.ibm.com or open a support ticket in the VMware Solutions console.

## Removed support for Broadwell servers
{: #relnotes_v44-broadwell-eos}

The following Broadwell servers are no longer available when you add ESXi servers for vCenter Server instances and VMware Regulated Workloads:
* Dual Intel Xeon® E5-2620 v4
* Dual Intel Xeon E5-2650 v4
* Dual Intel Xeon E5-2690 v4
* Dual Intel Xeon E5-2690 v4 (Broadwell, BI.S2.NW512)
* Quad Intel Xeon E7-8890 v4 (Broadwell, BI.S2.H4400)
* Quad Intel Xeon E7-8890 v4 (Broadwell, BI.S2.H4200)
* Quad Intel Xeon E7-8890 v4 (Broadwell, BI.S2.H4100)

## Updates for VMware Solutions Dedicated
{: #relnotes_v44-dedicated}

This release applies the following updates when you order VMware Solutions Dedicated instances.

### Updates for VMware vCenter Server instances
{: #relnotes_v44-vcs}

This release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts. For more information, see [Software BOM for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom#vc_bom-software).

* VMware vCenter Server® Appliance
   * 7.0 Update 2d (build 18455184)
   * 6.7 Update 3o (build 18485166)
* VMware NSX-T™ 3.1.1.0.0 (build 17483185)

### Updates for VMware NSX-T
{: #relnotes_v44-vcs-nsx}

Starting with the 4.4 release, new instances with NSX-T are provisioned with VMware NSX-T 3.1.1.

## Updates for add-on services
{: #relnotes_v44-services}

This release provides the following service versions on newly deployed instances.

* F5® BIG-IP® v16.1
* FortiGate® Virtual Appliance v7.0.1
* HyTrust® CloudControl™ v6.4.1
* Red Hat® OpenShift® v4.7.24
* Zerto v9.0u1

### FortiGate Virtual Appliance for multizone instances on VMware Regulated Workloads
{: #relnotes_v44-services-fortigate-multizone-edge}

Starting with this release, for VMware Regulated Workloads, you can deploy FortiGate Virtual Appliance on edge services clusters for multizone instances. You can deploy FortiGate Virtual Appliance when you first order the instance or as part of day 2 operations.

For more information, see [FortiGate Virtual Appliance overview](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations).

### Veeam deployment type displayed on services detail page
{: #relnotes_v44-services-veeam-deploy-type}

Starting with this release, the deployment type for Veeam is displayed on the service details page. The possible deployment types are VM, VSI, or Bare metal.

### Zerto licenses availability
{: #relnotes_v44-services-zerto-license}

You can now order Zerto license without associating it to any vCenter Server instance. When you submit your order, IBM Support requests a license key from Zerto that is then delivered to the email address that is associated with your order. For more information, see [Ordering Zerto licenses](/docs/vmwaresolutions?topic=vmwaresolutions-zerto_ordering_licenses).

You can use the {{site.data.keyword.vmwaresolutions_short}} console to view license details and delete the license. For more information, see [Managing Zerto licenses](/docs/vmwaresolutions?topic=vmwaresolutions-zerto_managing_licenses).

## Updates to REST APIs
{: #relnotes_v44-api}

As a result of End of Support for instance deployments with vSphere 6.5, REST APIs for the following tasks for instances with vSphere 6.5 are no longer provided:
* Adding and deleting clusters.
* Adding and removing ESXi servers.
* Adding and removing storage.
* Adding and deleting services.

## User interface updates and enhancements
{: #relnotes_v44-ui}

Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
