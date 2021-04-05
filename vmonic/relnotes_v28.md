---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-08"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V2.8
{: #relnotes_v28}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Single-node Trial for Migration and App Modernization instances
{: #relnotes_v28-single-node-trial}

The Single-node Trial for Migration and App Modernization is a quick way to test drive {{site.data.keyword.cloud_notm}} to migrate VMware workloads into the {{site.data.keyword.cloud_notm}} and then modernize workloads that use containers. This trial is a version of {{site.data.keyword.icpfull_notm}} Hosted on VMware vCenter Server on {{site.data.keyword.cloud_notm}} that provides the Kubernetes management platform for containers and the single-tenant VMware platform that can be managed by using the same familiar tools as on-premises environments.

## Adding and removing Network file system storage
{: #relnotes_v28-nfs}

Starting with the V2.8 release, you can now add network file system (NFS) storage shares to an existing NFS or vSAN vCenter Server cluster, as well as remove NFS file shares from an existing vCenter Server cluster.

The following options for customized shared file-level storage are now available:

* NFS share sizes that start at 20 GB up to 12 TB at single GB increments
* 0.25 IOPS/GB

## SAP-certified Broadwell E5-2690 and E7-8890 server support
{: #relnotes_v28-broadwell-e5-e7}

The following {{site.data.keyword.cloud_notm}} bare metal server CPU models are available for deployment for VMware vCenter Server on {{site.data.keyword.cloud_notm}} and VMware vSphere on {{site.data.keyword.cloud_notm}} instances and clusters:

* Dual Intel Xeon E5-2690 v4 processor / 28 cores total, 2.60 GHz / 512 GB RAM
* Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.20 GHz / 1024 GB RAM
* Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.20 GHz / 2048 GB RAM
* Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.20 GHz / 4096 GB RAM

## Broadwell E7-4820 and E7-4850 server support
{: #relnotes_v28-broadwell-e7}

The following {{site.data.keyword.cloud_notm}} bare metal server CPU models are available for deployment for vCenter Server, vCenter Server with Hybridity Bundle, Cloud Foundation, and vSphere on {{site.data.keyword.cloud_notm}} instances and clusters:

* Quad Intel Xeon E7-4820 v4 / 40 cores total, 2.0 GHz
* Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.1 GHz

## Embedded Platform Services Controller
{: #relnotes_v28-psc}

Starting with the V2.8 release, vCenter Server is deployed with an embedded PSC (Platform Services Controller). vCenter Server, the vCenter Server components, and the PSC are deployed on a single virtual machine. This change applies to all newly deployed vCenter Server, vCenter Server with Hybridity, and NetApp instances.

For instances that are upgraded from an earlier release to V2.8, the PSC is not embedded in vCenter Server. If you want to use embedded PSC, you must convert from external to embedded PSC yourself.

In a multi-site configuration where the primary instance is an upgraded instance for which the PSC was manually converted from external to embed, any newly deployed V2.8 secondary instances have embedded PSC.

## Updates for VMware vCenter Server instances
{: #relnotes_v28-vcs}

This release applies the following upgrades and improvements:

* vSphere ESXi 6.5 Update EP11 (build 6.5.0-10719125)
* vCenter Server 6.5 U2d (build 6.5.0-10964411)
* Platform Services Controller 6.5 U2d (build 6.5.0-10964411)

## Updates for VMware Cloud Foundation instances
{: #relnotes_v28-cf}

This release applies the following upgrades and improvements:

* vSphere ESXi 6.5 Update EP11 (build 6.5.0-10719125)
* vCenter Server 6.5 U2c (build 6.5.0-9451637)
* Platform Services Controller 6.5 U2c (build 6.5.0-9451637)

## Updates for add-on services
{: #relnotes_v28-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v28-spp}

The current release installs IBM Spectrum Protect™ Plus V10.1.2 on all newly deployed instances.

### KMIP for VMware on IBM Cloud
{: #relnotes_v28-kmip}

Previously, you might order a Cloud Foundation or vCenter Server instance with the KMIP for VMware on {{site.data.keyword.cloud_notm}} service that is included or add the service to an existing Cloud Foundation or vCenter Server instance after initial deployment.

Starting with the V2.8 release, the service is available as a stand-alone service without being associated to a VMware instance. Each instance of the service can serve one or more Cloud Foundation instances, vCenter Server instances, or vSphere clusters.

## Reference architecture documentation
{: #relnotes_v28-ref}

(Updated on 08 February 2019) The following technical documents are new or updated in the *Reference* section of the user documentation:

* {{site.data.keyword.vmwaresolutions_short}} architecture (with NSX-V and NSX-T)
* Caveonix RiskForesight reference architecture
* VMware HCX on {{site.data.keyword.cloud_notm}} for VMware Solutions

## User interface updates and enhancements
{: #relnotes_v28-ui}

The user interface is updated and provides the following enhancements:

* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
