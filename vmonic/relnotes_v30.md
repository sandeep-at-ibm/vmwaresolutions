---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

keywords: release notes, what's new, version 3.0

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.0
{: #relnotes_v30}

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## End of Support for VMware Cloud Foundation on IBM Cloud
{: #relnotes_v30-vcf-eos}

In an effort to consolidate our offerings for a better customer experience, the {{site.data.keyword.vmwaresolutions_short}} platform will no longer offer  VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} effective May 13, 2019.

Moving forward, all customers will be directed to VMware vCenter Server on {{site.data.keyword.cloud_notm}}, our flagship VMware Software-Defined Data Center solution on {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

Existing customers who use VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} will be assisted to convert to VMware vCenter Server on {{site.data.keyword.cloud_notm}} by the end-of-support date of May 13, 2019.

After May 13, management abilities for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} will be frozen from the {{site.data.keyword.vmwaresolutions_short}} console until they have been converted to VMware vCenter Server on {{site.data.keyword.cloud_notm}}. Customers who chose not to have their VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} instance migrated or converted to VMware vCenter Server on {{site.data.keyword.cloud_notm}} can access their instances from the {{site.data.keyword.cloud_notm}} infrastructure console.

## Removed support for Broadwell 2-CPU servers
{: #relnotes_v30-broadwell}

Starting with the V3.0 release, Broadwell 2-CPU servers are no longer available for deployment for new vCenter Server, vCenter Server with Hybridity Bundle, vCenter Server with NSX-T, and vSphere on {{site.data.keyword.cloud_notm}} instances and clusters. You can still add servers to existing clusters.

## Network file system operation enhancements
{: #relnotes_v30-nfs}

Starting with the V3.0 release you can simultaneously add or remove NFS storage and ESXi servers to clusters that are in the **Ready to Use** state. For example, you can add or remove an ESXi server in a cluster and add or remove NFS storage in another cluster. This applies to all vCenter Server and vCenter Server with NSX-T instances.

## Updates for VMware vCenter Server instances
{: #relnotes_v30-vcs}

This release applies the following upgrades and improvements:

* vSphere ESXi 6.7 Update 1 (build 6.7.0-13004448)
* vSphere ESXi 6.5 Update 2 (build 6.5.0-13004031)
* vCenter Server Appliance 6.7 Update 1b (build 6.7.0-11727113)
* Platform Services Controller 6.7 Update 1b (build 6.7.0-11727113) 

For more information, see [vCenter Server Bill of Materials](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

The Windows software that is ordered for Microsoft Active Directory (AD) and DNS (Domain Name System) services is upgraded to Windows Server 2016 for both configuration options: the VSIs (Virtual Server Instances) and the two highly-available Windows VMs. For more information about selecting your VMware components, see [Software BOM for vCenter Server instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software).

### vSAN storage enhancements
{: #relnotes_v30-vcs-vsan}

* When using vSAN storage, the number of Bare Metal Servers that you can order can now be greater than four. This applies to all vCenter Server, vCenter Server with Hybridity, and vCenter Server with NSX-T instances.
* Starting with the V3.0 release, an M.2 solid-state drive is ordered with your vSAN storage instance. You can order up to 10 capacity disks or a total of 12 capacity disks if you select the **High Performance with Intel Optaine** option.

For more information, see the *Storage settings* section in:
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [Ordering vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [Ordering vCenter Server with NSX-T instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## Updates for add-on services
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

In the current release, HyTrust CloudControl 5.5 is installed on all newly deployed instances. For more information about the new features in HyTrust CloudControl 5.5, see [What's New in HyTrust CloudControl Version 5.5](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

The current release installs HyTrust DataControl 4.3 on all newly deployed instances. For more information about the new features in HyTrust DataControl 4.3, see [What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

The current release installs HyTrust KeyControl 4.3 on all newly deployed instances. For more information about the new features in HyTrust KeyControl 4.3, see [What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

The current release installs {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2, together with {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, on all newly deployed instances.

For more information about the new features in {{site.data.keyword.cloud_notm}} Private v3.1.2, see [What's new in {{site.data.keyword.cloud_notm}} Private v3.1.2](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}.
For more information about the new features in {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, see [What's new in {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

Two new endpoints are now available in London and US East for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service. For more information, see [KMIP for VMware on {{site.data.keyword.cloud_notm}} service configuration](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config).

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

The current release installs IBM Spectrum Protect™ Plus V10.1.3 on all newly deployed instances. For more information about the new features in IBM Spectrum Protect Plus V10.1.3, see [IBM Spectrum Protect Plus updates](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

You are now able to add Zerto on {{site.data.keyword.cloud_notm}} on instances that are private-only. If you choose to install Zerto on private-only instances, you must set up your own proxy server and also configure the Call Home feature for Zerto. For more information, see [Ordering Zerto on {{site.data.keyword.cloud_notm}} for instances that are private network only](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only).

## New and updated documentation

* Documentation is now available to assist you in upgrading {{site.data.keyword.vmwaresolutions_short}} components to VMware vSphere 6.7. This upgrade is required if you want to continue to benefit from {{site.data.keyword.vmwaresolutions_short}} automation. For more information, see [Upgrading vCenter Server vSphere software from VMware vSphere 6.5 to 6.7](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade).
* Reference documentation is now available to provide you with user IDs that {{site.data.keyword.vmwaresolutions_short}} maintains for use by {{site.data.keyword.cloud_notm}} automation. Possible messages that display in your instance history logs are also available for your review. For more information, see [IBM user IDs](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) and [Instance history messages](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages).
* The **Reboot/Control** permission has been added to the table describing required permissions for the IBM Cloud infrastructure account. For more information, see [Permissions for the {{site.data.keyword.cloud_notm}} infrastructure account](/docs/services/vmwaresolutions/services?topic=vmware-solutions-cloud-infra-acct-req#cloud-infra-acct-req-permissions).
* New reference documentation is available for the following APIs. For more information, see [API reference](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}.
  * List all history messages for a specified VMware vCenter Server instance
  * Add shared storages to a specified cluster
  * Delete NFS storages from a specified cluster

## User interface updates and enhancements
{: #relnotes_v30-ui}

The user interface is updated and provides the following enhancements:

* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
