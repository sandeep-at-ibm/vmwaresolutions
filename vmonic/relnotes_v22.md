---

copyright:

  years:  2016, 2021

lastupdated: "2021-09-20"

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Release notes for V2.2
{: #relnotes_v22}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Spectre and Meltdown remediation
{: #relnotes_v22-spectre}

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715 and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## IBM CloudDriver virtual machine upgrade
{: #relnotes_v22-cloud-driver}

During the V2.2 upgrade process, the IBM CloudDriver virtual machine is redeployed with CentOS Linux release 7.4.1708. In addition, all new provisioned instances include CentOS Linux release 7.4.1708 on the IBM CloudDriver.

**Important:**

* If you are using a backup solution that references the IBM CloudDriver virtual machine, after you upgrade to V2.2, ensure that the backup solution is referencing the new IBM CloudDriver virtual machine.
* Before you upgrade to V2.2, ensure that you replace the old Veeam VSI with the Veeam on {{site.data.keyword.cloud_notm}} service. The old Veeam is no longer supported in V2.2 and later. Therefore, the management component backups that are associated with the old Veeam are not available for a restore.

## Advanced configuration settings on ESXi servers
{: #relnotes_v22-config-esxi}

For V2.2 or later releases, new instances are ordered with a new set of advanced configuration settings for ESXi servers.
For instances that are upgraded from a previous release to V2.2 or later releases, some settings require rebooting the ESXi servers. Therefore, only a subset of configuration settings is applied automatically.

It is recommended that you change the remaining configuration settings to the new values for consistency across all instances and to allow adequate support for storage expansion. IBM plans to test only with these new settings for all {{site.data.keyword.cloud_notm}} for VMware Solutions future releases.

## Support for up to 51 ESXi servers for an initial cluster and up to 59 ESXi servers for more clusters
{: #relnotes_v22-esxi-cluster}

For V2.2 and later releases, you can now increase the number of ESXi servers to a maximum of 51 for an initial cluster and up to 59 for extra clusters.

For instances deployed in V2.1 or earlier releases, you must enable necessary vSAN support to increase the cluster size beyond 32.
{: important}

## More network configuration options for vCenter Server and Cloud Foundation instances
{: #relnotes_v22-network-config}

For vCenter Server and Cloud Foundation instance orders, you can now reuse existing public and private VLANs for your network configuration. When existing VLANs are not available, you can order one new public and two new private VLANs.

For important considerations before you select existing VLANs, see the *Network interface settings* sections in [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance).

## Updates for VMware vCenter Server instances
{: #relnotes_v22-vcs}

### NSX component and port group configuration setting updates
{: #relnotes_v22-nsx}

The current release applies the VMware NSX for vSphere 6.3.5 component update.

For VMware vCenter Server instances that are deployed in V2.2 or later releases, the NSX and port group configuration settings are updated.

### New option for DNS configuration
{: #relnotes_v22-dns}

You can now select the deployment of a single Microsoft Windows Server Virtual Server Instance (VSI) for Microsoft Active Directory (AD) or two high availability Microsoft Windows virtual machines in the management cluster. For releases before V2.2, the single Microsoft Windows VSI for Microsoft AD was automatically deployed by default. The new option to select two Microsoft Windows virtual machines provides more privacy and the option to back up and restore the virtual machines that use the Veeam service.

You must provide two Microsoft Windows Server 2012 R2 licenses if you configure your instance to use the two Microsoft Windows virtual machines. Use the Microsoft Windows Server 2012 R2 Standard edition license or the Microsoft Windows Server 2012 R2 Datacenter edition license. You have 30 days to activate the virtual machines.
{: note}

### Increased number of clusters per instance
{: #relnotes_v22-clusters-per-inst}

You can now add up to 10 clusters to VMware vCenter Server instances that are deployed in or upgraded to V2.2. and later releases.

## Updates for VMware vSphere clusters
{: #relnotes_v22-vss}

### Component license bundles available to Business Partner customers
{: #relnotes_v22-license-bundles}

As a Business Partner user, you can now select from four component license bundles when you order a new vSphere cluster. Choose from Standard with Management, Advanced, Advanced with Networking, or Advanced with Networking and Management. You can also include more VMware components to your order. However, the option to Bring Your Own License is not available.

## Updates for NetApp ONTAP Select instances
{: #relnotes_v22-netapp}

The current release applies the update of NetApp ONTAP Select 9.3.

### Increased number of SATA drives for high capacity IBM Cloud bare metal servers
{: #relnotes_v22-sata-drives}

Thirty Four SATA drives are now available for NetApp ONTAP Select high capacity bare metal servers.

## Updates for add-on services
{: #relnotes_v22-services}

### Increased bandwidth option for F5 on IBM Cloud
{: #relnotes_v22-bandwidth}

You can now select a maximum bandwidth of 10 Gbps when you install the F5 on {{site.data.keyword.cloud_notm}} service for Cloud Foundation and vCenter Server instances.

### KMIP for VMware on IBM Cloud
{: #relnotes_v22-kmip}

You can now order a Cloud Foundation or vCenter Server instance with the KMIP for VMware on {{site.data.keyword.cloud_notm}} service included or add the service to an existing Cloud Foundation or vCenter Server instance after initial deployment.

This service provides a 24x7 highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and delete the encryption keys. In addition, this service provides management capability to maintain the associations between the client credentials and those encryption keys.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v22-spp}

The IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service is now available to instances that are deployed in (or upgraded to) V2.2 or later releases.

This service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement it as a stand-alone solution or you can integrate it with your IBM Spectrum Protect&trade; Plus environment to offload copies for long-term storage and data governance.

The IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service provides data protection for the workload VMs only.

### Managed Services
{: #relnotes_v22-managed-services}

Managed services for Veeam on {{site.data.keyword.cloud_notm}} and for Zerto on {{site.data.keyword.cloud_notm}} are now available to VMware vCenter Server and VMware Cloud Foundation instances. Request these managed services if you do not want to manage the complexity of your own solution and environment.

The Veeam on {{site.data.keyword.cloud_notm}} service seamlessly integrates with your VMware hypervisors to help your enterprise achieve high availability (HA). A fully managed backup environment can be deployed by using both Veeam backup software and IBM Resiliency Backup as a Service.

The Zerto on {{site.data.keyword.cloud_notm}} service provides replication and disaster recovery capabilities, which can be integrated into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud_notm}}. A fully managed disaster recovery (DR) environment can be deployed by using both Zerto DR software and IBM Resiliency Services.

You can request managed services for your instances from the **Getting Started** page, either by placing a new instance order, or by adding the service to an existing instance.

## New and updated documentation
{: #relnotes_v22-new-docs}

* A comparison table with the supported functions for Cloud Foundation instances, vCenter Server instances, and VMware vSphere clusters, is now available in the documentation. You can see, at a glance, the differences between the functions that each type of instance provides.

* The VLANs and software Bill of Materials (BOM) is now provided in the documentation for Cloud Foundation, vCenter Server, and VMware vSphere clusters.

## User interface updates and enhancements
{: #relnotes_v22-ui}

Improvements are made throughout the user interface:

* When you order an instance, all hardware options are now filtered by location and the unavailable options are displayed in the disabled state.
* The bare metal server configuration is now automatically populated when you order a vSphere cluster based on existing configurations. You can update the configuration according to your requirements.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
