---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-26"

keywords: vCenter Server NSX-T order instance, order vCenter Server NSX-T, order NSX-T

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering vCenter Server with NSX-T instances
{: #vc_nsx-t_orderinginstance}

To deploy a flexible and customizable VMware virtualized platform that best fits your workload needs, order a VMware vCenter Server with NSX-T instance.

## Requirements for vCenter Server with NSX-T
{: #vc_nsx-t_orderinginstance-req}

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/services/vmwaresolutions?topic=vmware-solutions-useraccount).
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
{: #vc_nsx-t_orderinginstance-sys-settings}

You must specify the following system settings when you order a vCenter Server with NSX-T instance.

### Instance name
{: #vc_nsx-t_orderinginstance-inst-name}

The instance name must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The instance name must start with a lowercase alphabetic character.
* The instance name must end with a lowercase alphabetic or numeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Initial cluster name
{: #vc_nsx-t_orderinginstance-cluster-name}

The initial cluster name must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The cluster name must start with a lowercase alphabetic character.
* The cluster name must end with a lowercase alphabetic or numeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server with NSX-T instance.

### VMware vSphere version
{: ##vc_nsx-t_orderinginstance-vsphere-license}

The vSphere Enterprise Plus 6.7u2 license is selected by default.

### Primary or secondary
{: #vc_nsx-t_orderinginstance-primary-secondary}

Select whether to order a new primary instance or a secondary instance for an existing primary instance.

## Licensing settings
{: #vc_nsx-t_orderinginstance-licensing-settings}

Specify the licensing options for the following VMware components in the instance:
* vCenter Server 6.5
* vSphere Enterprise Plus 6.7
* NSX-T 2.4 (Base, Advanced, or Enterprise edition)

For Business Partner users, the vCenter Server license (Standard edition), the vSphere license (Enterprise Plus edition), and the NSX license are included and purchased on your behalf. However, you must specify the edition for the NSX license.

For non-Business Partner users, you can use the IBM-provided VMware licenses for these components by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license keys.

### Licensing notes
{: #vc_nsx-t_orderinginstance-licensing-notes}

* The minimum number of licenses for BYOL that are required depends on the number of CPUs per server and the number of servers in the order. The license choice for each VMware component applies to the base instance and to any ESXi servers that you add to the instance later. Ensure that your license supports future capacity expansion in your infrastructure.
* The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want. You are responsible to ensure that the license key provided is correct for each VMware component selected.
* For vSphere, a license charge is incurred at the time of order, but the license charge is then credited to your account.
* You can change any licenses that you provided by using the VMware vSphere Web Client after the instance deployment is completed.
* Support for the VMware components that you provide licenses is provided by VMware, not by IBM Support.

## Bare Metal Server settings
{: #vc_nsx-t_orderinginstance-bare-metal-settings}

Bare Metal settings are based on your data center selection and bare metal server configuration.

### Data center location
{: #vc_nsx-t_orderinginstance-dc-location}

Select the {{site.data.keyword.CloudDataCent_notm}} where the instance is to be hosted.

### Skylake
{: #vc_nsx-t_orderinginstance-skylake}

When you select **Skylake**, you can choose the CPU and RAM combination for the Bare Metal Server according to your needs.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 Processor / 16 cores total, 2.1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 28 cores total, 2.2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 36 cores total, 2.3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Options for Skylake {{site.data.keyword.baremetal_short}}" caption-side="top"}

### Cascade Lake
{: #vc_nsx-t_orderinginstance-cascade}

For the **Cascade Lake** setting, you have options for the **CPU Model** and **RAM**.

Cascade Lake {{site.data.keyword.baremetal_short}} are available only for VMware vSphere Enterprise Plus 6.7 U2 instances.
{:note}

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Dual Intel Xeon Gold 4210 Processor / 20 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 Processor / 32 cores total, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 Processor / 40 cores total, 2.5 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
{: caption="Table 3. Options for Cascade Lake {{site.data.keyword.baremetal_short}}" caption-side="top"}

### Broadwell
{: #vc_nsx-t_orderinginstance-broadwell}

When you select **Broadwell**, you can choose the CPU and RAM combination for the Bare Metal Server according to your needs.

| CPU model options        | RAM options       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 cores total, 2.0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Table 4. Options for Broadwell {{site.data.keyword.baremetal_short}}" caption-side="top"}

### Number of Bare Metal Servers
{: #vc_nsx-t_orderinginstance-bare-metal-number}

* All servers that you order have the same configuration.
* If you're planning to use vSAN storage, you can order between 4 and 20 servers.
* If you're planning to use NFS storage, you can order between 2 and 20 servers. However, for production workloads, a minimum of 3 servers is recommended. For more information, see [Is a two-node vCenter Server instance highly available?](/docs/services/vmwaresolutions?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)

## Storage settings
{: #vc_nsx-t_orderinginstance-storage-settings}

Storage settings are based on your selection of Bare Metal Server configuration and the storage type.

For deployed instances, you can add NFS storage shares to an existing NFS or vSAN cluster. For more information, see the [Adding NFS storage to vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances).
{:note}

### vSAN storage
{: #vc_nsx-t_orderinginstance-vsan-storage}

vSAN is available for the **Skylake**, **Cascade Lake **, and **Broadwell** Bare Metal configurations only. Specify the following vSAN options:
* **Disk Type and Size for vSAN Capacity Disks**: Select an option for the capacity disks that you need.
* **Number of vSAN Capacity Disks**: Specify the number of capacity disks that you want to add.
* If you want to add capacity disks over the limit of 10, check the **High-Performance Intel Optane** box. This option provides two extra capacity disk bays for a total of 12 capacity disks and is useful for workloads that require less latency and higher IOPS throughput.

  The **High-Performance Intel Optane** option is available only for the Skylake and Cascade Lake CPU models.
  {:note}

* Review the **Disk Type for vSAN Cache Disks** and **Number of vSAN Cache Disks** values. These values depend on whether you checked the **High-Performance Intel Optane** box.
* **vSAN License**: Use the IBM-provided VMware license for the vSAN component by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

### NFS storage
{: #vc_nsx-t_orderinginstance-nfs-storage}

When you select **NFS Storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. Specify the following NFS options:

The number of file shares must be in the range of 1 to 32.
{:note}

* **Configure shares individually**: Select to specify different configuration settings for each file share.
* **Number of Shares**: When you use the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Performance**: Select the IOPS (input/output operations per second) per GB based on your workload requirements.
* **Size (GB)**: Select the capacity that meets your shared storage needs.
* **Add Shared Storage**: Select to add individual file shares that use different configuration settings.

Performance level details:

| Option        | Details       |
|:------------- |:------------- |
| 0.25 IOPS/GB | This option is designed for workloads that are not used often. Example applications include: vaulted data, hosting large databases with legacy data, or virtual disk images of virtual memory system as backup. |
| 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
| 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include: transactional databases. |
| 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |
{: caption="Table 5. NFS performance level options" caption-side="top"}

## Network interface settings
{: #vc_nsx-t_orderinginstance-network-interface-settings}

You must specify the following network interface settings when you order a vCenter Server with NSX-T instance.

### Host name prefix
{: #vc_nsx-t_orderinginstance-host-name-prefix}

The host name prefix must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The host name prefix must start with a lowercase alphabetic character.
* The host name prefix must end with a lowercase alphabetic or numeric character.
* The maximum length of the host name prefix is 10 characters.

### Subdomain label
{: #vc_nsx-t_orderinginstance-subdomain-label}

The subdomain label must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The subdomain label must start with a lowercase alphabetic character.
* The subdomain label must end with a lowercase alphabetic or numeric character.
* The maximum length of the subdomain label is 10 characters.

### Domain name
{: #vc_nsx-t_orderinginstance-domain-name}

The root domain name must meet the following requirements:
* The domain name must consist of two or more strings that are separated by period (.)
* The first string must start with a lowercase alphabetic character.
* The first string must end with a lowercase alphabetic or numeric character.
* All strings, except for the last one, can contain only lowercase alphabetic, numeric, and dash (-) characters.
* The last string can contain only lowercase alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

The maximum length of the Fully Qualified Domain Name (FQDN) for hosts and VMs is 50 characters. Domain names must accommodate for this maximum length.
{:note}

### Public or private network
{: #vc_nsx-t_orderinginstance-public-private-network}

Network interface card (NIC) enablement settings are based on your selection of either **Public and Private Network** or **Private Network Only**.

### VLANs
{: #vc_nsx-t_orderinginstance-vlans}

Network settings are based on your selection of either **Order New VLANs** or **Select Existing VLANs**.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each Bare Metal Server.

#### Order New VLANs
{: #vc_nsx-t_orderinginstance-new-vlans}

Select to order one new public VLAN and two new private VLANs.

#### Select Existing VLANs
{: #vc_nsx-t_orderinginstance-existing-vlans}

Depending on the {{site.data.keyword.CloudDataCent_notm}} that you selected, existing public and private VLANs might be available.

When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
* **Public VLAN** is for public network access. If you select the **Allocate a new one** option for this field, a new public VLAN is allocated automatically. This field is only available on the **Public and Private Network** tab.
* **Public Primary Subnet** is assigned to physical hosts for public network access. If you select the **Allocate a new one** option for this field, a new public primary subnet is allocated automatically. This field is only available on the **Public and Private Network** tab.
* **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}. If you select the **Allocate a new one** option for this field, a new private VLAN is allocated automatically.
* **Private Primary Subnet** is assigned to physical hosts for management traffic. If you select the **Allocate a new one** option for this field, a new private primary subnet is allocated automatically.
* **Secondary Private VLAN** is for VMware features such as vSAN. You can select an existing secondary private VLAN or select to allocate a new one.

Ensure that the firewall configuration on the selected VLANs does not block the management data traffic. Also ensure that all the VLANs that you select are in the same pod. ESXi servers cannot be provisioned on mixed-pod VLANs.
{:important}

### DNS configuration
{: #vc_nsx-t_orderinginstance-dns-config}

Select the Domain Name System (DNS) configuration for your instance:

* **Single Public Windows VSI for Active Directory/DNS**: A single Microsoft Windows Server VSI for Microsoft Active Directory (AD), which functions as the DNS for the instance where the hosts and VMs are registered, is deployed and can be looked up. This option has been deployed by default for V1.9 and later instances.
* **Two highly available dedicated Windows Server VMs on the management cluster**: Two Microsoft Windows VMs are deployed, helping enhance security and robustness.

You must provide two Microsoft Windows Server 2016 Standard edition licenses if you configure your instance to use the two Microsoft Windows VMs.
{:important}

Each license can be assigned only to one single physical server and covers up to two physical processors. One Standard edition license can run two virtualized Microsoft Windows VMs per 2-processor server. Therefore, two licenses are required since two Microsoft Windows VMs are deployed in two different hosts.

You have 30 days to activate the VMs.

For more information on ordering Windows Server 2016 licenses, see [Get started with Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:external}.

## Order summary
{: #vc_nsx-t_orderinginstance-order-summary}

Based on your selected configuration, the estimated cost is instantly generated and displayed in the **Order Summary** right pane. Click **Pricing details** to generate a PDF document with the cost summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the cost of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to order vCenter Server with NSX-T instances
{: #vc_nsx-t_orderinginstance-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane. 
2. In the **Start Provisioning** section, click the **VMware vCenter Server** card.
3. On the **VMware vCenter Server** page, click the **vCenter Server with NSX-T** card and click **Continue**.
4. On the **vCenter Server with NSX-T** page, enter the instance name.
5. Select the instance type:
   * Click **Primary Instance** to deploy a single instance in the environment or to deploy the first instance in a multi-site topology.
   * Click **Secondary Instance** to connect the instance with an existing (primary) instance in the environment for high availability and complete the following steps:
     1. Select the primary instance that you want the secondary instance to be connected with.
     2. For primary instances V2.8 or later, enter the vCenter Server administrator password for the primary instance.
     3. For primary instances V2.5, 2.6, or 2.7, enter the PSC administrator password for the primary instance.
     4. For primary instances V2.4 or earlier, verify that the prefilled value for the PSC administrator password for the primary instance is correct.
6. Complete the license settings for the instance components.
   *  To use IBM-provided licenses, select **Include with purchase** and select the license edition, if necessary.
   *  To use your own license, select **I will provide** and enter the license key.
7. Complete the Bare Metal Server settings.
    1. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
    2. Select the Bare Metal Server configuration and specify the CPU model and the RAM size.
    3. Specify the number of {{site.data.keyword.baremetal_short}}. If you are planning to use vSAN as your storage solution, a minimum of 4 {{site.data.keyword.baremetal_short}} are needed.  
8. Complete the storage configuration.
  * If you select **vSAN Storage**, specify the disk types for the capacity and cache disks, the number of disks, and the vSAN License edition. If you want more storage, check the **High-Performance Intel Optane** box.
  * If you select **NFS Storage** and want to add and configure the same settings to all file shares, specify the **Number of Shares**, **Performance**, and **Size (GB)**.
  * If you select **NFS Storage** and want to add and configure file shares individually, select **Configure shares individually**. Then, click the **+** icon next to the **Add Shared Storage** label and select the **Performance** and **Size (GB)** for each file share. You must select at least one file share.
9. Complete the network interface settings.
   1. Enter the host name prefix for the instance being provisioned, the subdomain label, and the root domain name. For a secondary instance, the domain name is automatically completed.
   2. Select the network setting of either **Public and Private Network** or **Private Network Only**.
   3. Select the VLAN settings:
      * If you want to order new public and private VLANs, click **Order New VLANs**.
      * If you want to reuse the existing public and private VLANs when they are available, click **Select Existing VLANs** and specify the VLANs and the subnets.
   4. Specify the DNS configuration.

10. On the **Order Summary** pane, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you order the instance.
   4. Click **Provision**.

## Results after you order vCenter Server with NSX-T instances
{: #vc_nsx-t_orderinginstance-results}

* The deployment of the instance starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Deployment History** section of the instance details.
* When the instance is successfully deployed, the components that are described in [Technical specifications for vCenter Server with NSX-T instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_overview#vc_nsx-t_overview-specs) are installed on your VMware virtual platform.
* When the instance is ready to use, the status of the instance is changed to **Ready to Use** and you receive a notification by email.
* When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.

## What to do next
{: #vc_nsx-t_orderinginstance-next}

View and manage the vCenter Server with NSX-T instance that you ordered. For more information on viewing the instance, see [Viewing vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances).

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the 	{{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.
{:important}

**CAUTION:** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account	 when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

   Exceptions to these activities include managing the shared storage file shares from the 	{{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

## Related links
{: #vc_nsx-t_orderinginstance-related}

* [Signing up for an {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions?topic=vmware-solutions-signing_required_accounts)
* [Viewing vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances)
* [Multi-site configuration for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_multisite)
* [Adding, viewing, and deleting clusters for vCenter Server with NSX-T instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [Expanding and contracting capacity for vCenter Server with NSX-T instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
* [Deleting vCenter Server with NSX-T instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_deletinginstance)
