---

copyright:

  years:  2019

lastupdated: "2019-04-09"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V2.9
{: #relnotes_v29}

This release includes new features, component updates, usability enhancements, and bug fixes.

## VMware vCenter Server on IBM Cloud with NSX-T
{: #relnotes_v29-vcs-nsx-t}

This release introduces the VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T™ offering as a proof of concept or sandbox testing offering. vCenter Server with NSX-T is a privately hosted cloud that you can use to test drive the VMware next generation networking platform, NSX-T.

## End of Support for VMware Cloud Foundation on IBM Cloud
{: #relnotes_v29-vcf-eos}

To consolidate the current offerings for better customer experience, {{site.data.keyword.cloud_notm}} will no longer support VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} effective May 13 2020.  
 
Moving forward, all customers are directed to VMware vCenter Server on {{site.data.keyword.cloud_notm}}, which offers more flexibility around storage and licensing options. 
 
Existing customers who use VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} will be assisted to migrate to VMware vCenter Server on {{site.data.keyword.cloud_notm}} by the end-of-support date of May 13, 2020.

After May 13 2020, management functions for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} instances will be removed from the {{site.data.keyword.vmwaresolutions_short}} console. Instances that have not been migrated to VMware vCenter Server on {{site.data.keyword.cloud_notm}} can be accessed by using the IBM Cloud infrastructure console.

Customers will be contacted by {{site.data.keyword.cloud_notm}} Support before March 25, 2020 to begin migration from VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}.
 
Customers can view their existing VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} instance on the [{{site.data.keyword.vmwaresolutions_short}} console](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted).

## VMware vSphere 6.7 Update 1 support
{: #relnotes_v29-vsphere}

You can now order VMware vSphere version 6.7 Update 1 with your VMware vCenter Server, VMware vCenter Server with Hybridity Bundle, and VMware vSphere on {{site.data.keyword.cloud_notm}} instances.

Additionally, Single-node Trial for Migration and App Modernization instances are now ordered with vSphere Enterprise Plus 6.7u1.

vSphere Enterprise Plus 6.7u1 is available for Broadwell and Skylake {{site.data.keyword.cloud_notm}} bare metal servers only.

## Support for application programming interfaces
{: #relnotes_v29-api}

Application programming interfaces (APIs) are now available for deploying instances, deleting instances, and adding and removing ESXi servers and clusters.

The REST API documentation is available in the *Reference* section of the user documentation.

## Updates for VMware vCenter Server instances
{: #relnotes_v29-vcs}

This release applies the following upgrades and improvements:

* vSphere ESXi 6.7 Update 1 (build 6.7.0-11675023)
* vSphere ESXi 6.5 Update 2 (build 6.5.0-11925212)
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1 (build 6.7.0-10244745)
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4 (build 11197766)
* NSX-T for vSphere 2.4

### Updates to data centers
{: #relnotes_v29-dc}

The following new data centers are available for deployment: **FRA-05 - Frankfurt** and **LON-05 - London**.

### ESXi server enhancements
{: #relnotes_v29-vcs-esxi}

* The Secure Shell (SSH) Protocol is now disabled for ESXi servers before instance delivery. If you want to enable SSH, see [Enable SSH from the vSphere Web Client](https://vdc-repo.vmware.com/vmwb-repository/dcr-public/4fcf776d-9ec6-448d-83de-bc730ef047ea/e6a46e41-5c99-4a7d-beed-790cf7e146cd/doc/GUID-C3A44A30-EEA5-4359-A248-D13927A94CCE.html).
* Starting with the V2.9 release, the following ESXi server operations are available:

   * Add new ESXi servers to an existing cluster while the servers are in maintenance mode. Virtual machines are not migrated to the new servers until you remove them from maintenance mode.
   * Simultaneously add or remove ESXi servers across multiple clusters in your instance.

### Network File System storage size
{: #relnotes_v29-vcs-nfs}

For vCenter Server instance orders, you can now add up to 24 TB of Network File System (NFS) shared storage for the performance levels of 0.25, 2, and 4 IOPS/GB.

The 10 IOPS/GB performance level is still limited to a maximum capacity of 4 TB per file share.
{:note}

## Updates for add-on services
{: #relnotes_v29-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v29-services-caveonix}

The Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service is now available to VMware vCenter Server instances that are deployed in or upgraded to V2.9 or later releases. This service can help to manage cyber and compliance risk with proactive monitoring and automated defense controls to protect against threats and to meet industry or government regulations.

You can order vCenter Server instances with the Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service included. Additionally, you can add this service to your existing vCenter Server instances later from the **Services** tab on the instance details page.

You can also order a stand-alone Caveonix RiskForesight license without associating it with any VMware instance for licensing and activation of your on-premises workloads.

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

In the current release, F5-BigIP VE V14.1.0.2 is installed on all newly deployed instances.

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

In the current release, HyTrust CloudControl 5.4.2 is installed on all newly deployed instances.

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

Two new endpoints are now available in Sydney for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service.

(Updated on 9 April 2019) Previously, KMIP for VMware on {{site.data.keyword.cloud_notm}} used IBM Key Protect for {{site.data.keyword.cloud_notm}} to create, encrypt, and decrypt encryption keys. Starting with the V2.9 release, KMIP for VMware on {{site.data.keyword.cloud_notm}} can also use {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services. These services are a complete set of encryption and key management services that manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}.

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

In the current release, Veeam Backup and Replication 9.5 Update 4 is installed on all newly deployed instances.

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

In the current release, Zerto Virtual Replication 6.5 update 3 is installed on all newly deployed instances.

## User interface updates and enhancements
{: #relnotes_v29-ui}

The user interface is updated and provides the following enhancements:

* On the **Infrastructure** page, a new **Network Interface** table provides VLAN, subnet, and IP address details for your cluster.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
