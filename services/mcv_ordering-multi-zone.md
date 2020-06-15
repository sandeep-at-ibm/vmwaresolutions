---

copyright:

  years:  2019, 2020

lastupdated: "2020-06-13"

keywords: VMware Mission Critical, request Mission Critical, tech specs Mission Critical, Mission Critical Workloads

subcollection: vmwaresolutions

---

{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Ordering multi-zone stretched clusters
{: #mcv_ordering}

To deploy a multi-zone stretched cluster consisting of compute, network, and storage elements that are deployed across three availability zones in an {{site.data.keyword.cloud}} multi-zone region (MZR), order {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads multi-zone stretched clusters.

## Requirements
{: #mcv_ordering-req}

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount).
* You reviewed the information in [Requirements and planning for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning).
* You reviewed the instance and domain name format. The domain name and subdomain label are used to generate the user name and server names of the instance.

| Name        | Value Format      |
|:------------|:------------ |
| Domain name | `<root_domain>` |  
| vCenter Server login user name | `<user_id>@<root_domain>` (Microsoft Active Directory user) or `administrator@vsphere.local` |
| vCenter Server (with embedded PSC) FQDN | `<instance_name>-vc.<root_domain>`. The maximum length is 50 characters. |
| Single Sign-On (SSO) site name | `<subdomain_label>` |
| Fully qualified ESXi server name | `<host_prefix><n>.<subdomain_label>.<root_domain>`, where `n` is the sequence of the ESXi server. The maximum length is 50 characters. |
{: caption="Table 1. Value format for instance and domain names" caption-side="top"}

Do not modify any values that are set during instance order or deployment. Doing so can make your instance unusable. For example, if public networking shuts down, if servers and Virtual Server Instances (VSIs) move behind a Vyatta mid-provision, or if the IBM CloudBuilder VSI stops or is deleted.
{:important}

## System settings
{: #mcv_ordering-sys-settings}

You must specify the following system settings when you order a vCenter Server instance.

### Instance configurations
{: #mcv_ordering-sys-config}

You can select **New Configuration** to specify settings for an instance and place the order or save the settings as a configuration template without placing an order.

You can also select a sample configuration template to further edit it, or to update it and then save it as a new configuration template.

For a sample configuration, click **Topology diagram** to see an example of the configuration.

### Instance name
{: #mcv_ordering-sys-inst-name}

The instance name is set to **vcs-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify an instance name that meets the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The instance name must start with a lowercase alphabetic character.
* The instance name must end with a lowercase alphabetic or numeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Resource group
{: #mcv_ordering-resource-group}

Use resource groups to organize the resources in your account for access control and billing purposes. The default resource group in your account is selected by default. You can also select another resource group according to your needs. The resource group that you select cannot be changed after the instance is created.

If **No resource group available** is displayed in this field, contact the account owner to be assigned an Editor or Administrator role on a resource group in the account because you currently do not have the permission to add the instance to any resource group in this account. For more information, see [IAM access](/docs/iam?topic=iam-userroles#platformroles).

## Location settings
{: #mcv_ordering-location}

Location settings are based on your selection of the {{site.data.keyword.cloud_notm}} multi-zone region (MZR), witness location, and management and resource location.

### Multi-Zone Region
{: #mcv_ordering-location-mzr}

The multi-zone region is a group of three or more {{site.data.keyword.cloud_notm}} data centers within close proximity of each other, ensuring high availability and resiliency.

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
| Dual Intel Xeon Silver 4210 Processor / 20 cores total, 2.3 GHz |64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 Processor / 32 cores total, 2.3 GHz |64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 Processor / 40 cores total, 2.5 GHz |64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Host CPU and RAM options" caption-side="top"}

### Storage settings
{: #mcv_ordering-availability-zones-storage}

Storage settings are based on your selection of vSAN or NFS storage.

#### vSAN storage
{: #mcv_ordering-availability-zones-storage-vsan}

Specify the following vSAN options:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add more capacity disks, select the **High Performance with Intel Optane** checkbox. This option provides two extra capacity disk bays, which is useful for workloads that require less latency and higher IOPS throughput.

#### NFS storage
{: #mcv_ordering-availability-zones-storage-nfs}

When you select **NFS Storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. Specify the following NFS options:

The number of file shares must be in the range of 1 to 100.
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

Specify the following network interface settings for your multi-zone stretched cluster.

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

## Summary
{: #mcv_ordering-summary}

Based on your selected configuration for the instance, the estimated price is instantly generated and displayed in the **Summary** right pane. Click **Pricing details** to generate a PDF document with the price summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to order Multi-Zone Stretched Clusters
{: #mcv_ordering-proc-multi}
{: help}
{: support}

You can order Multi-Zone Stretched Clusters by using one of the following methods:

* From the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from left navigation pane, and then click the **VMware Solutions - Dedicated** card in the **Start Provisioning** section. On the **VMware Solutions - Dedicated** page, ensure that the **vCenter Server** card is selected and click the **Multi Zone Stretched Clusters** tab.

* From the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane, scroll to the **Services** section, and then click **IBM Cloud for VMware Mission Critical Workloads** on the **Business Continuity and Migration** card. Click **Order Stretched Cluster**.

Proceed with the following steps to order a Multi-Zone Stretched Cluster:

1. For the instance configuration, select to create a new configuration or select a saved configuration.
   * If you want to create a new configuration, select **New Configuration**.
   * If you want to update a saved configuration or create a new configuration based on a saved one, select a saved configuration.
2. Enter the instance name and select a resource group.
3. Complete the location settings.
    1. Select the **Multi-Zone Region**.
    2. Click the arrow on the **Witness Location** card and select the availability zone for the witness site. The remaining availability zones are used for the **Management and Resource Location**.
4. Complete the license settings for the instance components.
   *  To use IBM-provided licenses, select **Include with purchase** and select the license edition, if necessary.
   *  To use your own license, select **I will provide** and enter the license key.
5. Complete the settings for the witness, management, and vSAN stretched clusters.
    1. Specify the CPU model and the RAM size.
    2. Specify the number of hosts.
    3. Specify the storage settings.
       * If you select **vSAN Storage**, specify the disk types for the capacity and cache disks and the number of disks. If you want more storage, select the **High Performance with Intel Optane** checkbox.
       * If you select **NFS Storage** and want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Size (GB)**, and **Performance**.
       * If you select **NFS Storage** and want to add and configure file shares individually, select **Configure shares individually**. Then, click the **+** icon next to the **Add Shared Storage** label and select the **Performance** and **Size (GB)** for each file share. You must select at least one file share.
6. Complete the network interface settings.
   1. Specify the DNS configuration.
   2. Enter the host name prefix, the subdomain label, and the domain name. The price calculation begins after all fields are complete.
7. On the **Summary** pane, review the instance settings and the estimated price.
   * To save the settings as a new configuration template without placing an order, click **Save Configuration**, enter a name for the configuration, and click **Continue**.
   * To save the updates to a saved configuration, click **Save Configuration**, select **Modify current configuration**, and click **Continue**.
   * To save the updates to a new saved configuration, click **Save Configuration**, select **Create new configuration**, enter a new name for the configuration, and click **Continue**.
8. To place the order, ensure that the account to be charged is correct, review and accept the terms, and click **Create**.

## Related links
{: #mcv_ordering-related}

* [IBM Cloud for VMware Mission Critical Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_overview)
* [Managed VMware Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_imi)
* [Managed Disaster Recovery Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_zerto_services)
