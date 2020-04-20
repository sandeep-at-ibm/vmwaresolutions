---

copyright:

  years:  2020

lastupdated: "2020-02-24"

keywords: release notes, what's new, version 3.5

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.5
{: #relnotes_v35}

This release includes new features, component updates, usability enhancements, and bug fixes.

## VMware Solutions Shared
{: #relnotes_v35-shared}

(Updated on 26 Feb 2020) {{site.data.keyword.vmwaresolutions_short}} Shared, a managed public Infrastructure as a Service (IaaS) solution, offers either a standardized or customizable deployment option of VMware vCloud Director Virtual Data Center environments. Use Virtual Data Center instances to quickly and seamlessly migrate or deploy VMware workloads to the cloud on top of IBM hosted VMware infrastructure. The Veeam Availability Suite and Veeam Cloud Connect Replication services are available and ready-to-use in all Virtual Data Center instances. Charges are incurred only if you choose to use the service.

For more information, see [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmware-solutions-shared_overview).

## VMware Solutions Dedicated
{: #relnotes_v35-dedicated}

To consolidate the {{site.data.keyword.vmwaresolutions_short}} offerings for a better customer experience, the VMware vCenter Server (both NSX-V and NSX-T) instances and VMware vSphere clusters are now grouped under a new card on the console, called {{site.data.keyword.vmwaresolutions_short}} Dedicated.

On the {{site.data.keyword.vmwaresolutions_short}} console, in the **Start Provisioning** section, you can click the **VMware Solutions Dedicated** to start your instance order.

For more information, see:
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Ordering VMware vSphere clusters](/docs/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances)

## Improved design for vCenter Server with NSX-T
{: #relnotes_v35-nsx-t-design}

The new NSX-T architecture is significantly improved from earlier {{site.data.keyword.vmwaresolutions_short}} versions. It employs a non-converged cluster design with three or more bare metal servers in the Management cluster and two or more bare metal servers in the Workload cluster. Only VMware vSphere 6.7 is supported for NSX-T instances.

Currently, no support is provided for:
* Private-only clusters
* License upgrades
* Broadwell CPU generation servers
* Local disks
* Add-on services

For more information, see the specific NSX-T details in [VMware vCenter Server overview](/docs/vmwaresolutions?topic=vmware-solutions-vc_vcenterserveroverview).

## VMware vSphere 6.5u1 - Deprecated
{: #relnotes_v35-vss-65u1dep}

vSphere 6.5u1 has been deprecated.
{:deprecated}

When you order new instances or add new clusters, you can choose either vSphere 6.7u2 or vSphere 6.5u3. Support for existing customers who are using vSphere 6.5u1 is still provided.

If you are using vSphere 6.5u1 for your instance, any new clusters are added with vSphere 6.5u2. If you are using vSphere 6.5u1 for your clusters, any new ESXi servers are added with vSphere 6.5u2.

## Juniper vSRX
{: #relnotes_v35-juniper-vsrx}

Juniper vSRX is a virtual security appliance that provides security and networking services at the perimeter or edge in virtualized private or public cloud environments. Within a VMware infrastructure, vSRX runs as a pair of virtual machines (VMs) within the vSphere environment.

For more information, see [Juniper vSRX overview](/docs/vmwaresolutions?topic=vmware-solutions-vsrx_overview).

## Updates for VMware vCenter Server instances
{: #relnotes_v35-vcs}

This release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts.

### Cascade Lake updates
{: #relnotes_v35-cascade-lake}

* The Cascade Lake bare metal server model Quad Intel Xeon Gold 6248 is now available for deployment.
* Cascade Lake servers are now available in the **LON02 - London** availability zone in the Europe region.

### New models for SAP-certified servers
{: #relnotes_v35-sap-cert}

The following SAP-certified bare metal server models are now available for deployment:

* Dual Intel Xeon Gold 5218 (Cascade, BI.S4.NW192)
* Dual Intel Xeon Gold 5218 (Cascade, BI.S4.NW384)
* Dual Intel Xeon Gold 6248 (Cascade, BI.S4.NW768)
* Dual Intel Xeon Platinum 8280M (Cascade, BI.S4.NW1500)
* Dual Intel Xeon Platinum 8280M (Cascade, BI.S4.NW3000)

### Cluster deployment considerations
{: #relnotes_v35-vcs-clusters}

The allocation of distributed switches for vCenter Server with NSX-V instances is changed in this release. This behavior varies if you have existing instances and clusters. Review the following considerations for switch creation when you create a new cluster:

* If there are one or more existing clusters in the same pod that uses distributed switches named ``SDDC-DSwitch-Private`` and ``SDDC-DSwitch-Public``, your new cluster uses the same switches as the existing cluster.
* If there are one or more existing clusters in the same pod that uses distributed switches that have been named by using the same name as the pod (rather than named by using the same name as the cluster), your new cluster uses the same switches as the existing cluster.
* If there are no existing clusters in the same pod, or all clusters in that pod have distributed switches that have been named by using the same name as the cluster rather than the pod, then your new cluster is configured with the new switch whose name is based only on the pod.

For vCenter Server with NSX-T instances, clusters in the same pod reuse NSX-T segments and ESXi TEP IP pools. New clusters in new pods create new segments and IP pools.

### vSAN compression and deduplication
{: #relnotes_v35-vsan-compress-dedup}

This release provides the option to disable vSAN compression and deduplication. This option is available only when you order a new instance or add a cluster.

For more information, see:
* [Enable vSAN compression and deduplication for new instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-vsan-storage-enable-comp)
* [Enable vSAN compression and deduplication for new clusters](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters-adding-vsan-storage-enable-comp)

## Updates for add-on services
{: #relnotes_v35-services}

This release installs the following service versions on newly deployed instances:

* BIG-IP VE v15.1
* Caveonix RiskForesight 2.2.2
* FortiGate Virtual Appliance 6.2.3

### FortiGate Security Appliance - Deprecated
{: #relnotes_v35-fortigate-security}

Automated deployment of the FortiGate Security Appliance service by using the {{site.data.keyword.vmwaresolutions_short}} console has been deprecated. Use the {{site.data.keyword.cloud_notm}} catalog to order and configure the FortiGate Security Appliance service. For more information about ordering the service through the {{site.data.keyword.cloud_notm}} catalog, see [FortiGate Security Appliance](https://cloud.ibm.com/catalog/infrastructure/fortigate-security-appliance-group).
{:deprecated}

### Gateway Appliances
{: #relnotes_v35-gateway-appliance}

A direct link to order Gateway appliances is now available on the **Security and Compliance** card in the **Services** section of the {{site.data.keyword.vmwaresolutions_short}} console. For more information about gateway appliance devices, see [Gateway appliances](https://www.ibm.com/cloud/network-appliances).

## New and updated documentation
{: #relnotes_v35-updated-doc}

* (Updated on 6 Mar 2020) The [Financial Services Sector Cloud reference architecture](/docs/vmwaresolutions?topic=vmware-solutions-fss-overview) is now available in the *Reference* section of the user documentation.
* Documentation is now provided about the products and versions that are supported in the current release of {{site.data.keyword.vmwaresolutions_short}}. For more information, see [Product compatibility guide](/docs/vmwaresolutions?topic=vmware-solutions-vmware-comp-guide).
* Various updates are made for the [{{site.data.keyword.vmwaresolutions_short}} API](https://cloud.ibm.com/apidocs/vmware-solutions) and the {{site.data.keyword.vmwaresolutions_short}} Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared).

## User interface updates and enhancements
{: #relnotes_v35-ui}

The user interface is updated and provides the following enhancements:
* On the ordering pages of instances and services, the following two tabs are added:
   * The **Create** tab: you can order an instance or a service on this tab.
   * The **About** tab: you can find the introduction of the instance or service on this tab, such as the technical specifications.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
