---

copyright:

  years:  2019, 2021

lastupdated: "2021-06-17"

keywords: VMware Mission Critical, request Mission Critical, tech specs Mission Critical, Mission Critical Workloads

subcollection: vmwaresolutions

---

{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}

# Ordering vCenter Server multizone instances
{: #mcv_ordering}

To deploy a cluster that consists of compute, network, and storage elements, which are deployed across three availability zones in an {{site.data.keyword.cloud}} [multizone region](#x9774820){: term}, order a VMware vCenter Server® multizone instance.

## Requirements
{: #mcv_ordering-req}

Ensure that you completed the following tasks:
* If this order is your first instance order, ensure that you completed the tasks in the **Before you begin** section on the ordering page. For more information, see [Setting up your environment for your first order](/docs/vmwaresolutions?topic=vmwaresolutions-completing_checklist).
* You reviewed the information in [Requirements and planning for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning).
* You reviewed the instance and domain name format. The domain name is used to generate the username and server names of the instance.

| Name        | Value Format      |
|:------------|:------------ |
| Domain name | `<root_domain>` |  
| vCenter Server login username | `<user_id>@<root_domain>` (Microsoft® Active Directory™ user) or `administrator@vsphere.local` |
| vCenter Server (with embedded PSC) FQDN | `<instance_name>-vc.<root_domain>`. The maximum length is 50 characters. |
| Single Sign-On (SSO) site name | `<root_domain>` |
| Fully qualified ESXi server name | `<host_prefix><n>.<root_domain>`, where `n` is the sequence of the VMware ESXi™ server. The maximum length is 50 characters. |
{: caption="Table 1. Value format for instance and domain names" caption-side="top"}

Do not modify any values that are set during instance order or deployment. Doing so can make your instance unusable. For example, if public networking shuts down, if servers and Virtual Server Instances (VSIs) move behind a Vyatta mid-provision, or if the IBM CloudBuilder VSI stops or is deleted.
{:important}

## System settings
{: #mcv_ordering-sys-settings}

You must specify the following system settings when you order a VMware vCenter Server instance.

### Instance configurations
{: #mcv_ordering-sys-config}

- You can select New configuration to specify settings for an instance and place the order or save the settings as a configuration template without placing an order.
- You can also select a saved configuration template to further edit it, or to update it and then save it as a new configuration template.

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

If **No resource group available** is displayed in this field, you currently do not have the permission to add the instance to any resource group in this account. Contact the account owner to be assigned an Editor or Administrator role on a resource group in the account. For more information, see [IAM access](/docs/account?topic=account-userroles).
{:note}

### VMware properties
{: #mcv_ordering-vmware-properties}

For vCenter Server multizone instances, only VMware vSphere® Enterprise Plus 7.0 and VMware NSX-T™ are supported.

## Location settings
{: #mcv_ordering-location}

Location settings are based on your selection of the {{site.data.keyword.cloud_notm}} multizone region, witness location, and management and resource location.

### Multizone region
{: #mcv_ordering-location-mzr}

The multizone region is a group of three or more {{site.data.keyword.cloud_notm}} data centers within close proximity of each other, ensuring high availability and resiliency.

### Witness location
{: #mcv_ordering-location-witness}

From the multizone region, select the availability zone of the witness site. The remaining management and vSAN™ stretched resource clusters are placed in the remaining availability zones. The witness site in a vSAN stretched cluster acts as the arbitrator to determine placement if a loss of connectivity or failure of an availability zone. This witness is considered the third fault domain in the stretched cluster architecture.

### Consolidated cluster location
{: #mcv_ordering-location-concolidated-cluster}

The remaining availability zones are where the resource and management cluster components are placed.

## Licensing settings
{: #mcv_ordering-licensing-settings}

Specify the licensing options for the following VMware components in the instance:
* vCenter Server Standard
* vSphere - Enterprise Plus
* VMware vSAN Enterprise
* NSX-T 3.1 (Advanced or Enterprise edition)

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

The deployment of a multizone instance consists of compute, network, and storage elements deployed across the following three availability zones in an {{site.data.keyword.cloud_notm}} multizone region.

<dl>
  <dt>Witness cluster</dt>
  <dd>An availability zone that maintains the vSAN witness appliance and any other site-specific components as needed.</dd>
  <dt>Consolidated cluster</dt>
  <dd>An availability zone that provides vSphere management such as vCenter, NSX Manager, NSX-based networking components, vRealize management tools, and more tools such as backup, disaster recovery, or other required management elements.  
  The cluster configuration is mirrored across two availability zones and has multiple compute, network and storage options for hosting management components. The architecture uses two dedicated management clusters each deployed across two availability zones. This architecture allows for management and maintenance of all components across zones without impacting workloads that are running in the vSAN stretched resource cluster.</dd>
  <dt>Additional workload cluster</dt>
  <dd>Optionally select the **Include a separate, additional workload cluster** checkbox. The workload cluster configuration is also mirrored across the two availability zones as the consolidated cluster. The minimum hosts across each data center is three. A total of six bare metal servers are ordered for the workload cluster. </dd>
  <dt>Edge services cluster</dt>
  <dd>Optionally select the **Edge services cluster** checkbox to order three edge services clusters. One cluster is deployed in each availability zone: one for the witness location and two for the consolidated location. Two bare metal servers are required for the edge services cluster. The default CPU model for the edge services cluster is Dual Intel Xeon Silver 4210 processor / 20 cores total, 2.2 GHz and cannot be changed.</dd>
</dl>

The availability zone cluster settings are based on your host and storage selections.

### Cluster name
{: #mcv_ordering-availability-zones-name}

The cluster name must meet the requirements that are listed in [Cluster name](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-cluster-name).

### Host settings
{: #mcv_ordering-availability-zones-host}

For the host settings, you have options for the CPU model, RAM, and number of hosts.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4210 processor / 20 cores total, 2.2 GHz |128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 processor / 32 cores total, 2.3 GHz |128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 processor / 40 cores total, 2.5 GHz |128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Platinum 8260 processor / 48 cores total, 2.4 GHz |128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Gold 6248 processor / 80 cores total, 2.5 GHz |384 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Platinum 8260 processor / 96 cores total, 2.4 GHz |384 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Host CPU and RAM options" caption-side="top"}

If you are planning to use vSAN storage, you can order 3 - 30 servers. If you are planning to use NFS storage, you can order 2 - 30 servers.

### Storage settings
{: #mcv_ordering-availability-zones-storage}

Storage settings are based on your selection of vSAN or NFS storage for the witness cluster and vSAN settings for the consolidated cluster.

#### vSAN storage
{: #mcv_ordering-availability-zones-storage-vsan}

Specify the following vSAN options:
* **Disk type and size for vSAN capacity disks** - Select an option for the capacity disks that you need.
* **Number of vSAN capacity disks** - Specify the number of capacity disks that you want to add.
* The option to enable deduplication and compression. For more information, see [Enable vSAN deduplication and compression](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-vsan-storage-enable-comp).

#### NFS storage
{: #mcv_ordering-availability-zones-storage-nfs}

When you select **NFS storage** for the witness cluster, you can add file-level shared storage for your instance where all shares use the same settings. Or you can specify different configuration settings for each file share. NFS storage requires a minimum of two hosts.

Specify the following NFS options.

* **Configure shares individually** - Select to specify different configuration settings for each file share.
* **Number of shares** - When you use the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size (GB)** - Select the capacity that meets your shared storage needs.
* **Performance** - Select the IOPS (input/output operations per second) per GB based on your workload requirements.
* **Add shared storage** - Select to add individual file shares that use different configuration settings.

Choose performance level options according to your needs.

| Option        | Details       |
|:------------- |:------------- |
| 0.25 IOPS/GB | This option is designed for workloads that are not used often. Example applications include: vaulted data, hosting large databases with existing data, or virtual disk images of virtual memory system as backup. |
| 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
| 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include transactional databases. |
| 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |
{: caption="Table 3. NFS performance level options" caption-side="top"}

For the NFS storage that you order initially, the size must be at least 1,000 GB and the performance at least 2 IOPS/GB. This storage, which is used mainly for management, should not be deleted. If you require additional storage, you can add it post-deployment. The size and performance of the NFS storage added post-deployment can have any of the available values.
{:important}

## Network interface settings
{: #mcv_ordering-network-interface-settings}

Specify the following network interface settings for your multizone instance.

### DNS configuration
{: #mcv_ordering-dns-config}

Select the Domain Name System (DNS) configuration for your instance:

* **Two public Windows VSIs for Active Directory/DNS** - Two Microsoft Windows® Server VSIs for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and VMs are registered, is deployed and can be looked up. This option is by default for V1.9 and later instances.
* **Four highly available dedicated Windows Server VMs on the management cluster** - Four Microsoft Windows VMs are deployed, helping enhance security and robustness.

You must provide four Microsoft Windows Server 2019 Standard edition licenses if you configure your instance to use the four Microsoft Windows VMs.
{:important}

Each license can be assigned only to one single physical server and covers up to two physical processors. One Standard edition license can run two virtualized Microsoft Windows VMs per 2-processor server. Therefore, two licenses are required since two Microsoft Windows VMs are deployed in two different hosts.

You have 30 days to activate the VMs.

For more information about ordering Windows Server 2019 licenses, see [Get started with Windows Server 2019](https://docs.microsoft.com/en-us/windows-server/get-started-19/get-started-19){:external}.

### Hostname prefix
{: #mcv_ordering-host-name-prefix}

The hostname prefix must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The hostname prefix must start with a lowercase alphabetic character.
* The hostname prefix must end with a lowercase alphabetic or numeric character.
* The maximum length of the hostname prefix is 10 characters.

### Domain name
{: #mcv_ordering-domain-name}

The root domain name must meet the following requirements:
* The domain name must consist of three or more strings that are separated by period (.) with a maximum of 50 characters.
* The first string must start with a lowercase alphabetic character.
* The first string must end with a lowercase alphabetic or numeric character.
* All strings, except for the last one, can contain only lowercase alphabetic, numeric, and dash (-) characters.
* The last string can contain only lowercase alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

The maximum length of the Fully Qualified Domain Name (FQDN) for hosts and VMs is 50 characters. Domain names must accommodate for this maximum length.
{:note}

## Service settings
{: #mcv_ordering-services}

When you order a vCenter Server multizone instance, you can also order add-on services. The following services are supported on vCenter Server multizone instances:

* Caveonix RiskForesight™
* HyTrust® CloudControl™
* Juniper® vSRX
* Veeam®
* vRealize Operations™ and Log Insight™

Veeam and Caveonix RiskForesight are recommended services. HyTrust CloudControl, Juniper vSRX, and vRealize Operations and Log Insight are optional services you can select.

## Summary
{: #mcv_ordering-summary}

Based on your selected configuration for the instance, the estimated price is instantly generated and displayed in the **Summary** right pane. Click **Pricing details** to generate a PDF document with the price summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. The tool is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to order a multizone instance
{: #mcv_ordering-proc-multi}
{: help}
{: support}

You can order a multizone instance by using one of the following methods on the {{site.data.keyword.vmwaresolutions_short}} console:

* In the **IaaS platforms** section, click the **VMware Solutions Dedicated** card. On the **VMware Solutions Dedicated** page, ensure that the **vCenter Server** card is selected and click the **Multizone VMware instance** card.
* Scroll down to the services section and click **IBM Cloud for VMware Mission Critical Workloads** in the **Business continuity and migration** category. Click **Order your stretched cluster across multizone region**.

Proceed with the following steps to order a multizone instance:

1. For the instance configuration, select to create a new configuration or select a saved configuration.
   * If you want to create a new configuration, select **New configuration**.
   * If you want to update a saved configuration or create a new configuration based on a saved one, select a saved configuration.
2. Enter the instance name and select a resource group.
3. Complete the location settings.
    1. Select the multizone region.
    2. Click the arrow on the **Witness location** card and select the availability zone for the witness site. The remaining availability zones are used for the management and resource location.
4. Complete the license settings for the instance components.
   *  To use IBM-provided licenses, select **Include with purchase** and select the license edition, if necessary.
   *  To use your own license, select **I will provide** and enter the license key.
5. Complete the settings for the witness and consolidated cluster.
    1. Enter the cluster name.
    2. Specify the CPU model and the RAM size.
    3. Specify the number of hosts.
    4. Specify the storage settings.
       * If you select **vSAN storage**, specify the disk types for the capacity and cache disks and the number of disks. Optionally, select the **Enable vSAN deduplication and compression** checkbox.
       * If you select **NFS storage** for your witness cluster and want to add and configure the same settings to all file shares, specify the **Number of shares**, **Size (GB)**, and **Performance**.
       * If you select **NFS storage** for your witness cluster and you want to add and configure file shares individually, select **Configure shares individually**. Then, click the **+** icon next to the **Add shared storage** label and select the **Performance** and **Size (GB)** for each file share. You must select at least one file share.
6. Optionally, select the **Include a separate, additional workload cluster** checkbox and complete the settings for the additional workload cluster.
7. Optionally, select the **Edge services cluster** checkbox and complete the settings for the edge services cluster.
   1. Enter the cluster name.
   2. Specify the RAM size and number of hosts.
   3. Select the private NICs enablement.
8. Complete the network interface settings.
   1. Specify the DNS configuration.
   2. Enter the hostname prefix and the domain name. The price calculation begins after all fields are complete.
9. Select the services you want to order for the vCenter Server multizone instance.
   1. Click **Edit** to configure Veeam, which is a recommended service.
   2. Complete the following information and click **Save**:
      * Name
      * Deployment type
      * Storage size
      * Storage performance
      * Number of VMs to license
  3. Click **Edit** to configure Caveonix RiskForesight, which is a recommended service.
  4. Complete the following information and click **Save**:
     * License name
     * License notes
     * Number of VMs to license
  5. Optionally, select HyTrust CloudControl. No service configuration is required.
  6. Optionally, click **Edit** to configure vRealize Operations and Log Insight.
  7. Select whether you will provide the license for vRealize Operations and the license for vRealize Log Insight or you want to include the license with your purchase. Click **Save**.
10. On the **Summary** pane, review the instance settings and the estimated price.
   * To save the settings as a new configuration template without placing an order, click **Save configuration**, enter a name for the configuration, and click **Continue**.
   * To save the updates to a saved configuration, click **Save configuration**, select **Modify current configuration**, and click **Continue**.
   * To save the updates to a new saved configuration, click **Save configuration**, select **Create new configuration**, enter a new name for the configuration, and click **Continue**.
11. To place the order, ensure that the account to be charged is correct, review and accept the terms, and click **Create**.

## Related links
{: #mcv_ordering-related}

* [IBM Cloud for VMware Mission Critical Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_overview)
* [Ordering, viewing, and deleting services for vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_addingremovingservices)
* [Managed VMware Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_imi)
* [Managed Disaster Recovery Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_zerto_services)
