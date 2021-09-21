---

copyright:

  years:  2021

lastupdated: "2021-09-21"

keywords: release notes, what's new, version 4.2

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:term: .term}

# Release notes for V4.2
{: #relnotes_v42}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Updates for VMware Solutions Shared
{: #relnotes_v42-shared}

This release applies the following updates when you order {{site.data.keyword.cloud}} for VMware® Solutions Shared instances.

### Veeam Backup and Replication V11
{: #relnotes_v42-shared-veeam}

Starting with the 4.2 release, VMware Solutions Shared instances provide Veeam Backup and Replication V11 for the Veeam Cloud Connect Replication ready-to-use service.

For more information about the compatibility requirements between Veeam service providers and tenants, see [Product versions in Veeam Cloud Connect infrastructure](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_versions.html?ver=110){:external}.

### Network High Availability through data center groups
{: #relnotes_v42-shared-net-ha}

VMware Solutions Shared now provides Network High Availability, a VMware vCloud Director feature that allows a vCloud Director network to be anchored in two data centers. This feature enables the network to be resilient and to withstand an outage in any of the two data centers. For more information, see [Using Network High Availability](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-network-ha).

## Updates for VMware Solutions Dedicated
{: #relnotes_v42-dedicated}

This release applies the following updates when you order VMware® Solutions Dedicated instances.

### Updates for VMware vCenter Server instances
{: #relnotes_v42-dedicated-vcs}

This release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts. For more information, see [Software BOM for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom#vc_bom-software).

* VMware vSphere® ESXi
  * 7.0 Update 1d (build 17551050)
  * 6.7 P05 (build 17700523)
  * 6.5 P06 (build 17477841)

* VMware vCenter Server® Appliance
  * 7.0 Update 2b (build 17958471)
  * 6.7 Update 3n (build 18010531)

* VMware NSX-T™ 3.1.0.0.0 (build 17107167)
* VMware NSX-V 6.4.10 (build 17626462)
* VMware vSAN™ 7.0 Update 1d (build 17551050) or 6.7 P05
* VMware vSAN Witness 7.0 Update 1d (build 17551050)[^vsanwitness]

[^vsanwitness]: vCenter Server multizone instances only

### NSX-T for vCenter Server instances with vSphere 6.7 - deprecated
{: #relnotes_v42-nsx-t-vsphere67}

NSX-T is no longer supported for new deployments of vCenter Server instances with vSphere 6.7. NSX-T is available only for vSphere 7. You can still view and manage your existing instances with vSphere 6.7 and NSX-T.
{:deprecated}

### Uplink speed updates - 25 Gb
{: #relnotes_v42-dedicated-uplink-speed}

Enhanced support is now provided for 25 Gb uplink speed for vCenter Server multizone instances.
* When you order new vCenter Server multizone instances, 25 Gb is supported for the witness cluster, the consolidated or management cluster, and the workload cluster.
* When you add clusters to vCenter Server multizone instances, 25 Gb is supported for the workload cluster.

### NFS storage limitation for VMware multizone instances
{: #relnotes_v42-nfs-limitation}

The initial NFS storage that you order is used mainly for management. Its size must be at least 1,000 GB and the performance at least 2 IOPS/GB. Do not delete this storage. If you require extra storage, you can add it post-deployment. The size and performance of the NFS storage added post-deployment can have any of the available values.
{:important}

### Updates to NFS host orders
{: #relnotes_v42-nfs-host-orders}

For locations where appropriate 1U servers are available, when you order hosts for clusters that use NFS storage, 1U servers are ordered silently rather than 2U servers. Clusters that use vSAN storage will continue to order 2U servers.

## Updates for VMware Regulated Workloads
{: #relnotes_v42-vrw}

This release applies the following updates when you order VMware Regulated Workloads instances.

### Uplink speed updates - 25 Gb
{: #relnotes_v42-vrw-uplink-speed}

Enhanced support is now provided for 25 Gb uplink speed for VMware Regulated Workloads instances, both single-zone and multizone.
* When you order new VMware Regulated Workloads instances, 25 Gb is supported for the management cluster and the workload cluster.
* When you add clusters to VMware Regulated Workloads instances, 25 Gb is supported for the workload cluster.

## Updates for add-on services
{: #relnotes_v42-services}

This release provides the following service versions on newly deployed instances.

* Caveonix RiskForesight™ 3.0
* F5® BIG-IP® 15.1.3
* HyTrust® CloudControl™ 6.3.1
* HyTrust DataControl® 5.3[^htdc]
* Juniper® vSRX 3.0 (20.4R1.12)

[^htdc]: vSphere 6.7 for NSX-T and vSphere 6.7 and 6.5 for NSX-V

### HyTrust KeyControl - deprecated
{: #relnotes_v42-services-htkc-deprecated}

New installations of HyTrust KeyControl™ are no longer supported for new or existing deployments of vCenter Server instances. You can still use or delete existing HyTrust KeyControl installations on your existing instances.
{:deprecated}

### Veeam on vSphere 6.5 - deprecated
{: #relnotes_v42-services-veeam-vsphere65-deprecated}

New installations of Veeam® are no longer supported for new or existing deployments of vCenter Server instances with VMware vSphere® 6.5. You can still use or delete existing Veeam installations on your existing vSphere 6.5 instances.
{:deprecated}

### F5 BIG-IP
{: #relnotes_v42-services-f5-bigip}

Starting with the 4.2 release, F5 BIG-IP is supported on vSphere 7 and NSX-T. This support is available on a management cluster.

### FortiGate Virtual Appliance
{: #relnotes_v42-services-fortigate}

Review the following information about FortiGate® Virtual Appliance for this release:

* FortiGate Virtual Appliance is supported on VMware vSphere® 7 and VMware NSX-T. This support is available on a management cluster and edge services cluster for single-zone instances only. Multizone support is not available.
* For VMware Regulated Workloads instances and Security and Compliance Readiness Bundle instances, you can install FortiGate Virtual Appliance only on the edge services cluster.
* The VM16 edition of FortiGate Virtual Appliance is available for all types of clusters. However, it is recommended that the 16 CPU license is used for high-bandwidth edge deployments only. For more information about any VM16 restrictions and Fortinet® sizing, see [FortiGate-VM on VMware ESXi data sheet](https://www.fortinet.com/content/dam/fortinet/assets/data-sheets/FortiGate_VM_ESXi.pdf){:external}.
* You can order multiple FortiGate Virtual Appliances on the management cluster. However, you can have only one pair on each edge services cluster.
* You cannot install FortiGate Virtual Appliance and Juniper vSRX on the same edge services cluster.
* After FortiGate Virtual Appliance v6.2.1, you are able to resize the RAM of FortiGate Virtual Appliance regardless of the licensing and pricing you currently have. You can make this change only if the CPU does not change. For more information, see [FortiGate-VM virtual licenses and resources](https://docs.fortinet.com/document/fortigate/6.2.0/vmware-esxi-cookbook/367417/fortigate-vm-virtual-licenses-and-resources){:external}.

For more information, see [FortiGate Virtual Appliance overview](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations).

### Juniper vSRX
{: #relnotes_v42-services-juniper}

Review the following information about Juniper vSRX for this release:

* Juniper vSRX is supported on vCenter Server multizone instances. For more information, see [Ordering services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices).
* You cannot install Juniper vSRX and FortiGate Virtual Appliance on the same edge services cluster.

### KMIP for VMware on IBM Cloud
{: #relnotes_v42-services-kmip}

Two new endpoints are now available in the **Toronto** location for the KMIP™ for VMware service. For more information, see [Ordering KMIP for VMware instances](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_ordering).

## Updates to REST APIs
{: #relnotes_v42-api}

* REST API support is now available for the F5 BIG-IP and FortiGate Virtual Appliance services.
* REST API support is now available for adding edge services clusters to vCenter Server instances.
* Various other updates are made to the [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) and the [VMware Solutions Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared) documentation.

## New and updated documentation
{: #relnotes_v42-updated-doc}

The following documentation is updated.

* [Upgrading vCenter Server vSphere software from VMware vSphere 6.5 or 6.7 to 7.0](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vsphere_70_upgrade#vc_vsphere_70_upgrade-procedure-esxi-upgrade) now includes important considerations and a section for updating licenses.
* FAQ is updated to clarify [how service license charges are being calculated](/docs/vmwaresolutions?topic=vmwaresolutions-faq_byol#faq_byol-service-charges).

## User interface updates and enhancements
{: #relnotes_v42-ui}

The user interface is updated and provides the following enhancements:

* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
