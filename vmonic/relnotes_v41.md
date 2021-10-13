---

copyright:

  years:  2021

lastupdated: "2021-09-20"

keywords: release notes, what's new, version 4.1

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for V4.1
{: #relnotes_v41}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Updates for VMware Solutions Shared
{: #relnotes_v41-shared}

This release applies the following updates when you order VMware® Solutions Shared instances.

### Support for Zerto
{: #relnotes_v41-shared-zerto}

Starting with the 4.1 release, the Zerto service is available and ready-to-use to provide disaster recovery for critical workloads in your virtual data center instances. Additionally, you can order the Zerto Cloud Connector (ZCC) service after you deploy your virtual data center instance. Use ZCC to replicate your on-premises virtual data centers to {{site.data.keyword.cloud}}.

Charges are incurred only if you choose to use the services.

### Network type options
{: #relnotes_v41-shared-network}

The option to select a private only network or a public and private network is now available when you order VMware® Solutions Shared instances.

## Updates for VMware Solutions Dedicated
{: #relnotes_v41-dedicated}

This release applies the following updates when you order VMware Solutions Dedicated instances.

### Upgrade support for vSphere 7.0 instances
{: #relnotes_v41-dedicated-upgrade-support-vsphere-v70}

For VMware vCenter Server® instances with VMware vSphere® 6.5 or vSphere 6.7, in-place upgrade to vSphere 7.0 is now supported for select configurations. Not all hardware configurations are supported, and the upgrade cannot help you migrate from VMware NSX®-V to NSX-T™ or from a non-converged NSX-T topology to a converged NSX-T topology.

You must contact {{site.data.keyword.vmwaresolutions_short}} Support before and after you upgrade your instance.
{: important}

{{site.data.keyword.cloud_notm}} supports only Cascade Lake bare metal servers for vSphere 7.0 instances. You must ensure that all VMware ESXi™ servers have the proper firmware and drivers to support 7.0.

After you complete an upgrade to vSphere 7.0, you can add clusters and hosts to your upgraded instance. When you add a cluster or host to the upgraded instance, you must keep the original deployment configuration, naming, and network topology.

The following upgrade scenarios are supported:
* Adding NFS storage, hosts, and clusters (NFS or vSAN) on instances upgraded from vSphere 6.5 or 6.7
* Adding hosts and clusters on upgraded NSX-V or non-converged NSX-T instances
* Adding hosts in an upgraded NFS or vSAN™ cluster

{{site.data.keyword.cloud_notm}} recommends that you deploy a new vSphere 7.0 instance and migrate your current network topology and workload to the new instance.
{: note}

### SAP-certified servers support for vSphere 7
{: #relnotes_v41-dedicated-sap-cert-vsphere-7}

The following SAP®-certified bare metal server models are now available for deployment with vSphere 7.0. These models are available for vCenter Server instances and clusters, and for VMware vSphere® clusters.
* Dual Intel® Xeon® Platinum 8280M (Cascade Lake, BI.S4.NW1500)
* Dual Intel Xeon Platinum 8280M (Cascade Lake, BI.S4.NW3000)
* Dual Intel Xeon Platinum 8280M (Cascade Lake)
* Quad Intel Xeon Platinum 8280M (Cascade Lake)

### Uplink speed updates - 25 Gb
{: #relnotes_v41-dedicated-uplink-speed}

Enhanced support is now provided for the 25 Gb uplink speed option for vCenter Server instances and clusters, and VMware vSphere clusters:
* This option is now available for vSphere 7.0.
* More data centers now support this option.

### Updates to data centers
{: #relnotes_v41-dedicated-dc}

(Updated on 20 April 2021) The {{site.data.keyword.cloud_notm}} data centers **Sao Paulo 04** and **Sao Paulo 05** are now available for deployment.

### Updates for IBM Cloud for VMware Mission Critical Workloads
{: #relnotes_v41-dedicated-mission-critical}

Starting with the 4.1 release, the following updates are available for vCenter Server multizone instances:

* You can select to use IBM-provided or your own licenses for vCenter Server Standard and vSphere Enterprise Plus licenses.
* You can specify an initial cluster name for your witness and consolidated clusters.
* You can optionally order an additional workload cluster and an edge services cluster to new vCenter Server multizone instances.
* You can add or remove the additional workload cluster or edge services cluster to existing vCenter Server multizone instances.
* You can add or remove VMware ESXi servers to and from your additional workload cluster.
* You can add or remove services to new or existing vCenter Server multizone instances.

### Known issue for IBM Cloud for VMware Mission Critical Workloads
{: #relnotes_v41-dedicated-mission-critical-warning}

For Mission Critical Workloads, a known issue with vCenter HA failover exists. If eth0 is not active on the passive node before failover is initiated, the passive node is isolated and fails to take over as the active node. vCenter HA might not activate `eth0` when failover is initiated.
{: important}

## VMware Regulated Workloads enhancements
{: #relnotes_v41-vrw}

(Updated on 4 May 2021) The VMware Regulated Workloads offering delivers a new multizone architecture to instances that are deployed in V4.1 and later releases. The multizone architecture can help to prevent downtime for cloud applications and to automate failovers within a cloud region.

## Security and Compliance Readiness Bundle
{: #relnotes_v41-scb}

The Security and Compliance Readiness Bundle is a prescriptive offering that provides many of the security and compliance features of {{site.data.keyword.cloud_notm}} for Financial Services at a lower entry price. The offering is packaged with security and compliance tools and templates for you to use with your preferred regulation standard.

## Updates for add-on services
{: #relnotes_v41-services}

This release provides the following service versions on newly deployed instances.
* BIG-IP® VE v15.1.2
* FortiGate® Virtual Appliance 6.4.4
* HyTrust® CloudControl v6.3
* Veeam® v11

### Updates for Caveonix RiskForesight
{: #relnotes_v41-services-caveonix-updates}

Review the following information about Caveonix RiskForesight™ for this release:

* Caveonix RiskForesight is offered as a per-host license for new deployments of Caveonix on VMware Regulated Workloads and Security and Compliance Readiness Bundle instances. For vCenter Server deployments, Caveonix is still offered as license packs that are priced per virtual machine (VM).
* A Caveonix RiskForesight license is valid for five years.
* Deleting Caveonix RiskForesight deletes the initial Caveonix RiskForesight license that was associated with the service.

### Services support for vCenter Server multizone instances
{: #relnotes_v41-services-multizone-vcs-instances}

Starting with the 4.1 release, the following add-on services are supported on vCenter Server multizone instances:

* Caveonix RiskForesight
* HyTrust CloudControl
* Veeam
* vRealize Operations™ and Log Insight™

### Veeam on bare metal server
{: #relnotes_v41-services-veeam-baremetal}

Starting with the 4.1 release, you can install Veeam v11 on a bare metal server. This new feature is supported only for vSphere 7.0 with NSX-T.

## Updates to REST APIs
{: #relnotes_v41-api}

* The [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) provides support for the additional edge services cluster and workload cluster on multizone instances.
* The [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) provides support for the following services on multizone instances: Caveonix RiskForesight, HyTrust CloudControl, Veeam, and vRealize Operations and Log Insight.
* The `network` option for selecting a private only network or a public and private network is available through the [VMware Solutions Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared).

## User interface updates and enhancements
{: #relnotes_v41-ui}

The user interface is updated and provides the following enhancements:

* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
