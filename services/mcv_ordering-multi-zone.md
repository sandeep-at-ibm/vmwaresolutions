---

copyright:

  years:  2019

lastupdated: "2019-12-05"

keywords: VMware Mission Critical, request Mission Critical, tech specs Mission Critical, Mission Critical Workloads

subcollection: vmware-solutions


---

# Ordering multi-zone stretched clusters
{: #mcv_ordering}

To deploy a multi-zone stretched cluster consisting of compute, network, and storage elements that are deployed across three availability zones in an {{site.data.keyword.cloud}} multi-zone region (MZR), order {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads multi-zone stretched clusters.

## Requirements
{: #mcv_ordering-req}

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/services/vmwaresolutions?topic=vmware-solutions-useraccount).
* You reviewed the information in [Requirements and planning for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_planning).
* You reviewed the instance and domain name format. The domain name and subdomain label are used to generate the user name and server names of the instance.

| Name        | Value Format      |
|:------------|:------------ |
| Domain name | `<root_domain>` |  
| vCenter Server login user name | `<user_id>@<root_domain>` (Microsoft Active Directory user) or `administrator@vsphere.local` |
| vCenter Server (with embedded PSC) FQDN | `<instance_name>-vc.<root_domain>`. The maximum length is 50 characters. |
| Single Sign-On (SSO) site name | `<subdomain_label>` |
| Fully qualified ESXi server name | `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `n` is the sequence of the ESXi server. The maximum length is 50 characters. |
{: caption="Table 1. Value format for instance and domain names" caption-side="top"}

Don't modify any values that are set during instance order or deployment. Doing so can make your instance unusable. For example, if public networking shuts down, if servers and Virtual Server Instances (VSIs) move behind a Vyatta mid-provision, or if the IBM CloudBuilder VSI stops or is deleted.
{:important}

## System settings
{: #mcv_ordering-sys-settings}

You must specify the following system settings when you order a vCenter Server instance.

### Saved configuration
{: #mcv_ordering-sys-config}

Select a predefined configuration to populate the form or create a new configuration that you can also save to use later.

For a predefined configuration, click **Topology diagram** to see an example of the configuration.

You have the option to edit a saved configuration and then save the changes made to the configuration or enter a new name to save the updates as a new configuration.

### Instance name
{: #mcv_ordering-sys-inst-name}

The instance name must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The instance name must start with a lowercase alphabetic character.
* The instance name must end with a lowercase alphabetic or numeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

## Location settings
{: #mcv_ordering-location}

Location settings are based on your selection of the {{site.data.keyword.cloud_notm}} multi-zone region (MZR), witness location, and management and resource location.

### Multi-Zone Region
{: #mcv_ordering-location-mzr}

The multi-zone region is a group of three or more {{site.data.keyword.CloudDataCents_notm}} within close proximity of each other, ensuring high availability and resiliency.

### Witness Location
{: #mcv_ordering-location-witness}

From the multi-zone region, select the availability zone of the witness site. The remaining management and vSAN stretched resource clusters are placed in the remaining availability zones. The witness site in a vSAN stretched cluster acts as the arbitrator to determine placement in the event of a loss of connectivity or failure of an availability zone.  This witness is considered the third fault domain in the stretched cluster architecture.

### Management and Resource Location
{: #mcv_ordering-location-mgmt-resource}

The remaining availability zones are where the resource and management cluster components are placed.

## Licensing settings
{: #mcv_ordering-licensing-settings}

Specify the licensing options for the following VMware components in the instance:
* VMware vSAN Enterprise
* NSX Service Providers 6.4 (Advanced or Enterprise edition)

A deployment of VMware vSAN stretched clusters on {{site.data.keyword.cloud_notm}} requires a vSAN Enterprise Edition license.
{:note}

You can use the IBM-provided VMware licenses for these components by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license keys.

### Licensing notes for Bring Your Own License
{: #mcv_ordering-licensing-notes}

* A license with a minimum of eight CPUs is required, which is for four servers with two CPUs per server. The license choice for each VMware component applies to the base instance and to any ESXi servers that you add to the instance later. Ensure that your license supports future capacity expansion in your infrastructure.
* The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want. You are responsible to ensure that the license key provided is correct for each VMware component selected.
* For vSphere, a license charge is incurred at the time of order, but the license charge is then credited to your account.
* You can change any licenses that you provided by using the VMware vSphere Web Client after the instance deployment is completed.
* Support for the VMware components that you provide licenses is provided by VMware, not by IBM Support.

## Availability zone settings
{: mcv_ordering-availability-zones}

The deployment of a multi-zone stretched cluster consists of compute, network, and storage elements deployed across the following three availability zones in an {{site.data.keyword.cloud_notm}} multi-zone region.

<dl>
  <dt>Witness cluster</dt>
  <dd>An availability zone that maintains the vSAN witness appliance and any other site specific components as needed.</dd>
  <dt>Management cluster</dt>
  <dd>An availability zone that provides vSphere management such as vCenter, NSX manager, NSX-based networking components, vRealize management tools, additional tooling such as backup, disaster recovery or other required management elements.</dd>
  <dt>vSAN stretched cluster</dt>
  <dd>An availability zone that has customer defined workloads that require high availability and availability zone resilience.</dd>
</dl>

The availability zone cluster settings are based on your host and storage selections.

### Host settings
{: #mcv_ordering-availability-zones-host}

For the host settings, you have options for the CPU Model, RAM, and number of hosts.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Gold 4210 Processor / 20 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 Processor / 32 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 Processor / 40 cores total, 2.5 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Host CPU and RAM options" caption-side="top"}

### Storage settings
{: #mcv_ordering-availability-zones-storage}

Storage settings are based on your selection of vSAN or NFS storage.

#### vSAN storage
{: #mcv_ordering-availability-zones-storage-vsan}

Specify the following vSAN options:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity over the limit of 10 disks, select the **High-Performance with Intel Optane** box. This option provides two extra capacity disk bays for a total of 12 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

#### NFS storage
{: #mcv_ordering-availability-zones-storage-nfs}

When you select **NFS Storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. Specify the following NFS options:

The number of file shares must be in the range of 1 to 32.
 {:note}

* **Configure shares individually**: Select to specify different configuration settings for each file share.
* **Number of Shares**: When you use the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size (GB)**: Select the capacity that meets your shared storage needs.
* **Performance**: Select the IOPS (input/output operations per second) per GB based on your workload requirements.
* **Add Shared Storage**: Select to add individual file shares that use different configuration settings.

Choose performance level options according to your needs.

| Option        | Details       |
|:------------- |:------------- |
| 0.25 IOPS/GB | This option is designed for workloads that are not used often. Example applications include: vaulted data, hosting large databases with legacy data, or virtual disk images of virtual memory system as backup. |
| 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
| 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
| 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |
{: caption="Table 3. NFS performance level options" caption-side="top"}

## Network interface settings
{: #mcv_ordering-network-interface-settings}

Specify the following network interface settings for your .

### DNS configuration
{: #mcv_ordering-dns-config}

Select the Domain Name System (DNS) configuration for your instance:

* **Single Public Windows VSI for Active Directory/DNS**: A single Microsoft Windows Server VSI for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and VMs are registered, is deployed and can be looked up. This option has been deployed by default for V1.9 and later instances.
* **Two highly available dedicated Windows Server VMs on the management cluster**: Two Microsoft Windows VMs are deployed, helping enhance security and robustness.

You must provide two Microsoft Windows Server 2016 Standard edition licenses if you configure your instance to use the two Microsoft Windows VMs.
{:important}

Each license can be assigned only to one single physical server and covers up to two physical processors. One Standard edition license can run two virtualized Microsoft Windows VMs per 2-processor server. Therefore, two licenses are required since two Microsoft Windows VMs are deployed in two different hosts.

You have 30 days to activate the VMs.

For more information on ordering Windows Server 2016 licenses, see [Get started with Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:external}.

### Hostname prefix
{: #mcv_ordering-host-name-prefix}

The host name prefix must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The host name prefix must start with a lowercase alphabetic character.
* The host name prefix must end with a lowercase alphabetic or numeric character.
* The maximum length of the host name prefix is 10 characters.

### Subdomain label
{: #mcv_ordering-subdomain-label}

The subdomain label must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The subdomain label must start with a lowercase alphabetic character.
* The subdomain label must end with a lowercase alphabetic or numeric character.
* The maximum length of the subdomain label is 10 characters.
* The subdomain label must be unique within all instances in your multi-site configuration.

### Domain name
{: #mcv_ordering-domain-name}

The root domain name must meet the following requirements:
* The domain name must consist of two or more strings that are separated by period (.)
* The first string must start with a lowercase alphabetic character.
* The first string must end with a lowercase alphabetic or numeric character.
* All strings, except for the last one, can contain only lowercase alphabetic, numeric, and dash (-) characters.
* The last string can contain only lowercase alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

The maximum length of the Fully Qualified Domain Name (FQDN) for hosts and VMs is 50 characters. Domain names must accommodate for this maximum length.
{:note}

## Procedure to order a Multi-Zone Stretched Cluster
{: #mcv_ordering-proc-multi}

You can order a Multi-Zone Stretched Cluster by using one of the following methods:

* From the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from left navigation pane, and then click the **VMware vCenter Server** card in the **Start Provisioning** section. Click the **vCenter Server** card, click **Continue**, and then click **Multi Zone Stretched Clusters** on the **vCenter Server** page.

* From the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane, scroll to the **Services** section, and then click **IBM Cloud for VMware Mission Critical Workloads** on the **Business Continuity and Migration** card. Click **Order Stretched Cluster**.

Proceed with the following steps to order a Multi-Zone Stretched Cluster:

1. Select to create a new configuration or select a saved configuration.
   * If you make edits to a saved configuration and want to save them to the saved configuration, click **Save**.
   * If you want to create a new configuration with the changes you made to the saved configuration, enter a different name and click **Save**.
2. Enter the instance name.
3. Complete the location settings.
    1. Select the **Multi Zone Location**.
    2. Click the arrow on the **Witness Location** tile and select the availability zone for the witness site. The remaining availability zones are used for the **Management and Resource Location**.
4. Complete the license settings for the instance components.
   *  To use IBM-provided licenses, select **Include with purchase** and select the license edition, if necessary.
   *  To use your own license, select **I will provide** and enter the license key.
5. Complete the settings for the witness, management, and vSAN stretched clusters.
    1. Specify the CPU model and the RAM size.
    2. Specify the number of hosts.
    3. Specify the storage settings.
       * If you select **vSAN Storage**, specify the disk types for the capacity and cache disks and the number of disks. If you want more storage, check the **High-Performance Intel Optane** box.
       * If you select **NFS Storage** and want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Size (GB)**, and **Performance**.
       * If you select **NFS Storage** and want to add and configure file shares individually, select **Configure shares individually**. Then, click the **+** icon next to the **Add Shared Storage** label and select the **Performance** and **Size (GB)** for each file share. You must select at least one file share.
6. Complete the network interface settings.
   1. Specify the DNS configuration.
   2. Enter the host name prefix, the subdomain label, and the domain name. The price calculation begins after all fields are complete.
7. On the **Order Summary** pane, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click **Save Configuration**.
   4. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you order the instance.
   5. Click **Provision**.

## Related links
{: #mcv_ordering-related}

* [IBM Cloud for VMware Mission Critical Workloads overview](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv_overview)
* [Managed VMware Services](/docs/services/vmwaresolutions?topic=vmware-solutions-managing_imi)
* [Managed Backup Services](/docs/services/vmwaresolutions?topic=vmware-solutions-managing_veeam_services)
* [Managed Disaster Recovery Services](/docs/services/vmwaresolutions?topic=vmware-solutions-managing_zerto_services)
