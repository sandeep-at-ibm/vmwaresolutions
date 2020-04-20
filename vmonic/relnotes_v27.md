---

copyright:

  years:  2016, 2018

lastupdated: "2018-12-14"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V2.7
{: #relnotes_v27}

This release includes new features, component updates, usability enhancements, and bug fixes.

## SAP-certified 6140 server support
{: #relnotes_v27-sap}

Starting with the V2.7 release, the following new {{site.data.keyword.cloud_notm}} bare metal server CPU models are available for deployment for VMware vCenter Server on {{site.data.keyword.cloud_notm}} and VMware vSphere on {{site.data.keyword.cloud_notm}} instances and clusters:
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 192 GB RAM
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.2 GHz / 384 GB RAM
* Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 768 GB RAM

## Updates for add-on services
{: #relnotes_v27-services}

### IBM Cloud Private Hosted
{: #relnotes_v27-icp}

The {{site.data.keyword.cloud_notm}} Private Hosted service is now available to VMware vCenter Server with Hybridity Bundle instances, in addition to VMware vCenter Server instances that are deployed in (or upgraded to) V2.5 and later releases. You can now order a vCenter Server instance or a vCenter Server with Hybridity Bundle instance with the service included. You can also add the service to an existing vCenter Server instance or a vCenter Server with Hybridity Bundle instance after initial deployment.

### Mission Critical VMware on IBM Cloud
{: #relnotes_v27-mcv}

The Mission Critical VMware on {{site.data.keyword.cloud_notm}} service is now available to instances that are deployed in, or upgraded to, V2.7 or later releases.

Mission Critical VMware on {{site.data.keyword.cloud_notm}} delivers a multi-zone cloud architecture to help enterprises prevent downtime for cloud applications and to automate failovers within a cloud region. With this cloud architecture, you can achieve a higher availability and failover success rate than most VMware clients can achieve with on-premises environments or competing cloud platforms.

### F5 on IBM Cloud
{: #relnotes_v27-f5}

Now when you order the F5 on {{site.data.keyword.cloud_notm}} service, you can select whether you want F5 to apply license over public network or over private network with a proxy server.

### FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v27-fva}

In 3Q 2018, Fortinet changed their subscription bundles.

For FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service that is deployed in V2.7 and later Cloud Foundation instances and vCenter Server instances, FortiOS 6.0.3 is provisioned.

When you order FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, you can select whether you want FortiGuard to apply license and security updates over public network or over private network with a proxy server.

### Zerto on IBM Cloud service component updates
{: #relnotes_v27-zerto}

For the Zerto on {{site.data.keyword.cloud_notm}} service that is deployed in V2.7 and later Cloud Foundation instances and vCenter Server instances, Zerto Virtual Replication 6.0 update 3 is provisioned.

### KMIP for VMware on IBM Cloud integration with IBM Cloud Activity Tracker
{: #relnotes_v27-kmip-icat}

In addition to VMware instance events, events for KMIP for VMware on {{site.data.keyword.cloud_notm}}, such as key creation, key deletion, and key access, are now integrated with your {{site.data.keyword.cloud_notm}} Activity Tracker instance.

### KMIP for VMware on IBM Cloud - Deprecated
{: #relnotes_v27-kmip-deprecated}

(Updated on 14 December 2018) The current version of KMIP for VMware on {{site.data.keyword.cloud_notm}} is being deprecated.
{:deprecated}

## New and updated documentation
{: #relnotes_v27-new-docs}

### Reference architecture documentation
{: #relnotes_v27-ref-archi}

The following technical documents are now available in the *Reference* section of the user documentation:

* [NSX Edge Services Gateway solution architecture](/docs/vmwaresolutions?topic=vmware-solutions-nsx_overview)
* [VMware Update Manager guide](/docs/vmwaresolutions?topic=vmware-solutions-vum-intro)

## User interface updates and enhancements
{: #relnotes_v27-ui}

The user interface is updated and provides the following enhancements:

* The **Customized** tab is now split into the **Skylake** and **Broadwell** tabs based on the server type to help you in server selection. This tab is where you specify CPU model and RAM for bare metal server settings when you order instances.
* The **Preconfigured** options for bare metal server configuration are not available anymore.
* The **Type** column is now included in the **vCenter Server Instances** table on the **Resources** page to identify vCenter Server, vCenter Server with Hybridity Bundle, and vCenter Limited Test Drive instances.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
