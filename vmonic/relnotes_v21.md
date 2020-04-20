---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}


# Release notes for V2.1
{: #relnotes_v21}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Spectre and Meltdown remediation
{: #relnotes_v21-spectre}

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715 and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware HCX on IBM Cloud
{: #relnotes_v21-hcx}

The HCX on {{site.data.keyword.cloud_notm}} service is now available to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.1 or later releases. This service can seamlessly extend the networks of your on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows bidirectional migration of virtual machines (VMs) between your on-premises data centers and {{site.data.keyword.cloud_notm}} without any change. By establishing a layer 2 bridge, HCX uses WAN optimization, deduplication, compression, and encryption to more quickly and securely migrate data over a Direct Link or VPN tunnel. The bulk migration of VMs is backwards compatible with VMware vSphere 5.1 or greater. If you use vSphere 6.0 or greater on-premises, you can vMotion live (powered-on) VMs from on-premises to an {{site.data.keyword.cloud_notm}} data center. You are not required to have VMware NSX installed in your data center when using HCX.

You can order Cloud Foundation or vCenter Server instances with the HCX on {{site.data.keyword.cloud_notm}} service included when you order your instance, or add this service to your existing instances later from the **Services** tab on the instance details page.

You can also order an on-premises HCX instance for licensing and activation of your on-premises HCX installation.

## More flexible Bring Your Own License model for VMware Cloud Foundation and vCenter Server
{: #relnotes_v21-byol}

Bring Your Own License (BYOL) or purchase IBM-provided subscription licensing when you create a new cluster is now available to V2.1 and later VMware Cloud Foundation instances and VMware vCenter Server instances. These options allow you to use your existing component key or to rent the license from IBM. Before V2.1, you could not purchase IBM-provided licensing for a specific VMware component if you BYOL. Currently, only VMware vSphere and VMware vSAN are available for licensing per cluster.

Additionally, when you add nodes to a cluster that is licensed with your key, the console prompts you to provide a new license key if the number of nodes exceeds the key capacity.

## Zerto on IBM Cloud service component updates
{: #relnotes_v21-zerto}

For Zerto on {{site.data.keyword.cloud_notm}} service that is deployed in V2.1 and later Cloud Foundation instances and vCenter Server instances, Zerto Virtual Replication 5.5u2 is provisioned. Zerto virtual replication appliances (VRAs) are now deployed to the management data store (either vSAN or Endurance) rather than to the local data store for performance reasons. If you have existing VRAs, consider migrating their storage to the management data store for better performance.

## Updates for VMware vCenter Server instances
{: #relnotes_v21-vcs}

### Network MTU configuration settings
{: #relnotes_v21-mtu}

For V2.1 or later releases, new vCenter Server instances are ordered with the setting Public Distributed Virtual Switch (DVS) as MTU 1500 (default).

### Automatic application of VMware ESXi patches and updates to hosts
{: #relnotes_v21-esxi-patches}

In V2.0 and earlier VMware vCenter Server instances, patches were not automatically applied to ESXi hosts that were added to a cluster.

In V2.1 and later instances, the automation applies patches to new ESXi hosts so that the patch level matches the patch level at the time that the initial instance was provisioned. You are responsible for manually applying any future patches and updates.
When VMware patches and updates become available in future releases, the automation scans the ESXi hosts of your existing instances and email you a reminder to apply the most recent patches and updates manually.

### Price estimates for VMware NSX license upgrades
{: #relnotes_v21-nsx-license}

You can now see a price estimate before you submit an order to upgrade to the VMware NSX Advanced or Enterprise edition. The pricing is based on the number of ESXi hosts in the vCenter Server instance. This purchase changes only the NSX license key and upgrades your VMware NSX Base edition to the Advanced or Enterprise edition. The purchase does not upgrade the NSX software version.

### Maximum servers per cluster increases from 32
{: #relnotes_v21-max-clusters}

For the default cluster in an instance, you can deploy or expand up to 51 servers. For all subsequent clusters in an instance, you can deploy or expand up to 59 servers.

This capability is available only to instances that are deployed in V2.1 and later. Instances that are upgraded to V2.1 from pre-V2.1 releases do not have this option.
{:note}

### User customized IBM Cloud bare metal server configuration options
{: #relnotes_v21-bare-metal}

User customized {{site.data.keyword.cloud_notm}} bare metal server configuration now offers the Dual Intel Xeon Gold 6140 with 36 cores total, 2.3 GHz.

### Individual NFS file share configurations
{: #relnotes_v21-nfs}

You can now configure NFS file shares on an individual basis. Select the file size and performance level for each individual file share or select the same file size and performance level for all of the file shares that you order.

## User interface updates and enhancements
{: #relnotes_v21-ui}

Improvements are made throughout the user interface:

* The **Order Instance** option is no longer available from the left navigation pane. Click **Getting Started** to complete the steps to order an instance.
* The **Subdomain Prefix** field from the **Basics** page when you order an instance is renamed to **Subdomain Label**.
* In addition to viewing your cost estimate on the **Summary** page when you order a primary or secondary vCenter Server or Cloud Foundation instance, you can now calculate a cost estimate on any page as you provide the details for your instance order.
* Breadcrumb navigation is added to the **Resources** page as an alternative method of navigation, thus reducing the number of steps that are required to reach parent pages.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.

## New and updated documentation
{: #relnotes_v21-new-docs}

A new IBM Developer recipe is available with step-by-step instructions on how to attach dedicated storage to existing {{site.data.keyword.vmwaresolutions_full}} deployments that use NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}.
