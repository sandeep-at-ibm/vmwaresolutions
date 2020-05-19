---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-05"

keywords: release notes, what's new, version 3.2

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.2
{: #relnotes_v32}

This release includes new features, component updates, usability enhancements, and bug fixes.

## VMware HCX for IBM Cloud availability
{: #relnotes_v32-HCX}

Starting with the 3.2 release, you can order the VMware HCX on {{site.data.keyword.cloud_notm}} service with VMware vCenter Server instances. Previously, you might order the HCX on {{site.data.keyword.cloud_notm}} service only through the VMware vCenter Server with Hybridity Bundle instance. The vCenter Server with Hybridity Bundle instance is not supported for new installations. However, functions of existing vCenter Server with Hybridity Bundle instances are preserved and you can install the HCX on {{site.data.keyword.cloud_notm}} service on these instances.

A 12-month commitment is required when you order the HCX on {{site.data.keyword.cloud_notm}} service. After the 12-month commitment expires, you can install and uninstall the HCX on {{site.data.keyword.cloud_notm}} service and you can add and remove hosts and clusters without restrictions. Your account is then charged monthly and you can cancel at any time.

The 12-month commitment and charging structure do not apply to existing vCenter Server with Hybridity Bundle instances.
{:note}

## VMware vSphere 6.7 Update 2 support
{: #relnotes_v32-vsphere-v67}

You can order VMware vSphere version 6.7 Update 2 with your VMware vCenter Server, VMware vCenter Server with NSX-T, and VMware vSphere on IBM Cloud instances. vSphere Enterprise Plus 6.7u2 replaces the option to order vSphere Enterprise Plus 6.7u1 with new instances. Additionally, Single-node Trial for Migration and App Modernization and Single-node Trial for Data Protection and Disaster Recovery instances are now ordered with vSphere Enterprise Plus 6.7u2.

vSphere Enterprise Plus 6.7u2 is available for Skylake, Cascade Lake, and Broadwell {{site.data.keyword.cloud_notm}} bare metal servers.

If you have an existing instance with vSphere Enterprise Plus 6.7u1, you can add new hosts with either vSphere Enterprise Plus 6.7u1 or vSphere Enterprise Plus 6.7u2. However, adding a 6.7u1 host is unsecure. It is recommended that you update your hosts to the latest ESXi server version as soon as possible.
{:note}

## Cascade Lake support
{: #relnotes_v32-cascade}

Starting with the V3.2 release, the following new bare metal server CPU models are available for deployment with instances and clusters with VMware vSphere 6.7 Update 2. These new models apply to vCenter Server, vCenter Server with NSX-T, and VMware vSphere.

* Dual Intel Xeon Silver 4210 processor / 20 cores total, 2.3 GHz
* Dual Intel Xeon Gold 5218 processor / 32 cores total, 2.3 GHz
* Dual Intel Xeon Gold 6248 processor / 40 cores total, 2.5 GHz

Cascade Lake bare metal servers are available on Multi-Zone Region
{{site.data.keyword.cloud_notm}} data centers.

## Updates for VMware vCenter Server instances
{: #relnotes_v32-vcs}

This release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts:

* VMware NSX for vSphere 6.4.5 (build 13282012)
* vSphere ESXi 6.7 EP 10 (build 6.7.0-13981272)
* vCenter Server Appliance 6.7 Update 2b (6.7.0.-13843469)
* Platform Services Controller 6.7 Update 2b (6.7.0.-13843469)

### Cluster updates
{: #relnotes_v32-vcs-initial-cluster}

* You can now specify the name of your initial cluster to be created at the same time you place your instance order.
* (Updated on 05 November 2019) As a VMware recommended best practice, new clusters are now deployed with a public and private pair of distributed virtual switches. Private-only clusters deploy a new private distributed switch. All networking for the cluster is configured to use these switches.

## Updates for VMware vSphere instances
{: #relnotes_v32-vss}

A public VLAN is no longer required when you order a new vSphere cluster with a private network only.

## Updates for add-on services
{: #relnotes_v32-services}

This release installs the following service versions on newly deployed instances:

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Update 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Update 4

### VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

The vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} service is now available to VMware vCenter Server instances that are deployed in or upgraded to V3.2 or later releases.

This service provides VMware vRealize Log Insight (vRLI) integrated with vRealize Operations Manager (vROps), to help you monitor and proactively manage the health and performance of your virtualized environment, and to perform root cause analysis of an issue by filtering and searching through logs.

You can order vCenter Server instances with vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} included, or add this service to your existing instances later from the Services tab on the instance details page.

You can also bring your enterprise vRealize Operations and vRealize Log Insight licenses to the cloud (per CPU or OSI) or you can rent licenses from IBM Cloud.

## New and updated documentation
{: #relnotes_v32-updated-doc}

* The Activity Tracker documentation is updated.

## User interface updates and enhancements
{: #relnotes_v32-ui}

The user interface is updated and provides the following enhancements:

* The instance name requirements have changed. For more information, see the appropriate topic for the instance type that you are ordering.
* Leading zeros have been added to hostnames to allow for proper sorting.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
