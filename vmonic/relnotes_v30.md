---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

keywords: release notes, what's new, version 3.0

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}


# Release notes for V3.0
{: #relnotes_v30}

This release includes new features, component updates, usability enhancements, and bug fixes.

## End of Support for VMware Cloud Foundation on IBM Cloud
{: #relnotes_v30-vcf-eos}

In an effort to consolidate our offerings for a better customer experience, the {{site.data.keyword.vmwaresolutions_short}} platform will no longer offer VMware Cloud Foundation effective May 13, 2020.

Moving forward, all customers will be directed to VMware vCenter Server on {{site.data.keyword.cloud_notm}}, our flagship VMware Software-Defined Data Center solution on {{site.data.keyword.cloud_notm}} bare metal servers.

Existing customers who use VMware Cloud Foundation will be assisted to convert to VMware vCenter Server by the end-of-support date of May 13, 2020.

After May 13 2020, management functions for VMware Cloud Foundation instances will no longer be available from the {{site.data.keyword.vmwaresolutions_short}} console until the instances have been converted to VMware vCenter Server. Customers who choose not to have their VMware Cloud Foundation instances migrated or converted to VMware vCenter Server can access their instances from the {{site.data.keyword.cloud_notm}} infrastructure console.

## Removed support for Broadwell 2-CPU servers
{: #relnotes_v30-broadwell}

Starting with the V3.0 release, Broadwell 2-CPU servers are no longer available for deployment for new vCenter Server, vCenter Server with Hybridity Bundle, vCenter Server with NSX-T, and vSphere on {{site.data.keyword.cloud_notm}} instances and clusters. You can still add servers to existing clusters.

## Network file system operation enhancements
{: #relnotes_v30-nfs}

Starting with the V3.0 release you can simultaneously add or remove NFS storage and ESXi servers to clusters that are in the **Ready to use** state. For example, you can add or remove an ESXi server in a cluster and add or remove NFS storage in another cluster. This applies to all vCenter Server and vCenter Server with NSX-T instances.

## Updates for VMware vCenter Server instances
{: #relnotes_v30-vcs}

This release applies the following upgrades and improvements:

* vSphere ESXi 6.7 Update 1 (build 6.7.0-13004448)
* vSphere ESXi 6.5 Update 2 (build 6.5.0-13004031)
* vCenter Server Appliance 6.7 Update 1b (build 6.7.0-11727113)
* Platform Services Controller 6.7 Update 1b (build 6.7.0-11727113)

The Windows software that is ordered for Microsoft Active Directory (AD) and DNS (Domain Name System) services is upgraded to Windows Server 2016 for both configuration options: the VSIs (Virtual Server Instances) and the two highly-available Windows VMs.

The AD domain functional level remains at 2008 to allow for backward compatibility with any potential secondary instances. If compatibility with earlier (2008) secondary instances is not a consideration in your environment, you can upgrade the domain functional level to a higher version.

### vSAN storage enhancements
{: #relnotes_v30-vcs-vsan}

* When using vSAN storage, the number of {{site.data.keyword.cloud_notm}} bare metal servers that you can order can now be greater than four. This applies to all vCenter Server, vCenter Server with Hybridity, and vCenter Server with NSX-T instances.
* Starting with the V3.0 release, an M.2 solid-state drive is ordered with your vSAN storage instance. You can order up to 10 capacity disks or a total of 12 capacity disks if you select the **High Performance with Intel Optane** option.

## Updates for add-on services
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

In the current release, HyTrust CloudControl 5.5 is installed on all newly deployed instances.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

The current release installs HyTrust DataControl 4.3 on all newly deployed instances.

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

The current release installs HyTrust KeyControl 4.3 on all newly deployed instances.

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

The current release installs {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2, together with {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, on all newly deployed instances.

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

Two new endpoints are now available in London and US East for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

The current release installs IBM Spectrum Protect™ Plus V10.1.3 on all newly deployed instances.

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

You are now able to add Zerto on {{site.data.keyword.cloud_notm}} on instances that are private-only. If you choose to install Zerto on private-only instances, you must set up your own proxy server and also configure the Call Home feature for Zerto.

## New and updated documentation

* Documentation is now available to assist you in upgrading {{site.data.keyword.vmwaresolutions_short}} components to VMware vSphere 6.7. This upgrade is required if you want to continue to benefit from {{site.data.keyword.vmwaresolutions_short}} automation.
* Reference documentation is now available to provide you with user IDs that {{site.data.keyword.vmwaresolutions_short}} maintains for use by {{site.data.keyword.cloud_notm}} automation. Possible messages that display in your instance history logs are also available for your review.
* The **Reboot/Control** permission has been added to the table describing required permissions for the IBM Cloud infrastructure account.
* New reference documentation is available for the following APIs.
  * List all history messages for a specified VMware vCenter Server instance
  * Add shared storages to a specified cluster
  * Delete NFS storages from a specified cluster

## User interface updates and enhancements
{: #relnotes_v30-ui}

The user interface is updated and provides the following enhancements:

* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
