---

copyright:

  years:  2021

lastupdated: "2021-10-01"

keywords: release notes, what's new, version 4.3

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for V4.3
{: #relnotes_v43}

This release includes new features, component updates, usability enhancements, and bug fixes.

## VMware vSphere 7.0 Update 2a support
{: #relnotes_v43-vsphere-v70}

VMware® vSphere® 7.0 Update 2a is now available for newly deployed instances. For existing vSphere 7.0u1 instances and clusters, you can either add a 7.0u1 or 7.0u2 host or cluster.

## New disk type for VMware vSAN
{: #relnotes_v43-vsan}

For the VMware vSAN™ component, the 7.68 TB SSD SED capacity disk is now available for {{site.data.keyword.cloud}} bare metal servers for newly deployed instances and when you add hosts and clusters to existing instances. The 7.68 TB SSD SED disk type is supported for only VMware vSphere 7.0 or 6.7 instances with 25 Gb uplink speed.

For more information, see [vSAN storage](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-vsan-storage).

## Updates for VMware Solutions Shared
{: #relnotes_v43-shared}

This release applies the following updates when you order VMware Solutions Shared instances.

### Windows pricing metrics
{: #relnotes_v43-shared-windows}

(Updated on 1 October 2021) The Microsoft® Windows® pricing metric is now hourly. For more information, see [VMware Solutions Shared pricing](/docs/vmwaresolutions?topic=vmwaresolutions-shared_pricing).

## Updates for VMware Solutions Dedicated
{: #relnotes_v43-dedicated}

This release applies the following updates when you order VMware Solutions Dedicated instances.

### Updates for VMware vCenter Server instances
{: #relnotes_v43-dedicated-vcs-bom}

This release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts. For more information, see [Software BOM for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom#vc_bom-software).

* VMware vSphere ESXi™
   * 7.0 Update 2a (build 17867351)
   * 6.7 P05 (build 17700523)
   * 6.5 P06 (build 17477841)
* VMware vCenter Server® Appliance
   * 7.0 Update 2b (build 17958471/17958471)
   * 6.7 Update 3n (build 18010531/18010599)
* VMware NSX-T™ 3.1.0.0.0 (build 17107167)
* VMware NSX-V 6.4.10 (build 17626462)
* VMware vSAN 7.0 Update 2 (build 17630552) or 6.7 P05

### vCenter Server multizone instances - deprecated
{: #relnotes_v43-vcs-multizone-deprecated}

New deployments of vCenter Server multizone instances are no longer supported.
{: deprecated}

You can still complete the following operations for existing multizone instances:
* [Adding clusters](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_addviewdeleteclusters) and [Deleting clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vc_deletingclusters)
* [Adding ESXi servers](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_addingremovingservers) and [Removing ESXi servers](/docs/vmwaresolutions?topic=vmwaresolutions-vc_removingservers)
* [Adding storage](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_addingnfs-storage) and [Deleting storage](/docs/vmwaresolutions?topic=vmwaresolutions-vc_removingnfs)
* [Deleting services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_deletingservices)

## Updates for VMware Regulated Workloads
{: #relnotes_v43-vrw}

This release applies the following updates when you order VMware Regulated Workloads instances.

### Support for consolidated cluster
{: #relnotes_v43-vrw-consldt}

Rather than requiring that the VMware Regulated Workloads solution deploys a separate management cluster and separate clusters for workloads, now you can start with a smaller footprint by selecting the **Customize a consolidated cluster** option, which deploys a consolidated management and workload cluster.

The **Customize a consolidated cluster** option is available in single-zone deployments (non-stretched) and brings down the entry price point by enabling workloads to run alongside VMware management components in the same cluster. The minimum number of hosts required to start is reduced from 10 to 6. This option is helpful for proof of concepts (POCs) and for clients who want to start small and grow over time.

If you do not want workloads to run on the primary cluster, you can select **Management optimized cluster** and order a 2-CPU Intel Cascade Lake chipset with 20 cores total and 192 GB of RAM per bare metal server. Under **Additional cluster for workloads**, you must select the checkbox to include a separate secondary cluster for workloads and then customize the bare metal hardware based on your workload capacity requirements. 

The VMware HCX™ service is available only if you also include a workload cluster in your instance.
{: note}

### Support for save configuration
{: #relnotes_v43-vrw-saveconfig}

A new **Save configuration** button is added to the **Summary** pane of the ordering page for VMware Regulated Workloads. Use this option to save your instance settings as a configuration template without placing an order. You can manage the configuration templates by further editing or deleting them as well.

## Updates for Security and Compliance Readiness Bundle
{: #relnotes_v43-scb}

A new **Save configuration** button is added to the **Summary** pane of the ordering page for Security and Compliance Readiness Bundle instances. Use this option to save your instance settings as a configuration template without placing an order. You can manage the configuration templates by further editing or deleting them as well.

## Updates for add-on services
{: #relnotes_v43-services}

This release provides the following service versions on newly deployed instances.

* Caveonix RiskForesight™ v3.0.1
* FortiGate® Virtual Appliance v6.4.6
* Juniper® vSRX v20.4 (R2)
* Red Hat® OpenShift® v4.7

### FortiGate Virtual Appliance
{: #relnotes_v43-services-fortigate}

For this release, FortiGate Virtual Appliance add the following features:
* 25 Gb uplink speed on vSphere 7 and NSX-T
* High-performance deployment size of Fortigate-VM32

The uplink speed and deployment size require Cascade Lake 5218 or higher.

For more information, see:
* [Uplink speeds, deployment sizes, and CPU models](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations#fortinetvm_considerations-installvalues)
* [Considerations when you install FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations#fortinetvm_considerations-install)

### Juniper vSRX
{: #relnotes_v43-services-Juniper-vSRX}

For this release, you can install Juniper vSRX on 25 Gb uplink speed consolidated and edge services clusters on vSphere 7 with NSX-T. On 25 Gb uplink speed clusters, only the Content Security Bundle license is available.

For more information, see [Ordering Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-ordering).

## Updates to REST APIs
{: #relnotes_v43-api}

* REST API support for vCenter Server multizone instances is no longer provided as a result of feature deprecation in this release.
* Various other updates are made to the [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) and the [VMware Solutions Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared) documentation.

## User interface updates and enhancements
{: #relnotes_v43-ui}

Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
