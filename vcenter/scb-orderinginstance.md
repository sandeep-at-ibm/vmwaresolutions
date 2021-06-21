---

copyright:

  years:  2021

lastupdated: "2021-06-21"

keywords: order Security and Compliance Readiness Bundle, order scb instances, order vcs scb

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Security and Compliance Readiness Bundle instances
{: #scb-orderinginstance}

The Security and Compliance Readiness Bundle is a prescriptive offering that provides many of the security and compliance features of {{site.data.keyword.cloud}} for Financial Services™ at a lower entry price. The offering is packaged with security and compliance tools and templates for you to use with your preferred regulation standard.

## Requirements for Security and Compliance Readiness Bundle instances
{: #scb-orderinginstance-req}

Ensure that you complete the following tasks:
* If you are ordering an instance for the first time, complete the tasks in the **Before you begin** section on the ordering page. For more information, see [Setting up your environment for your first order](/docs/vmwaresolutions?topic=vmwaresolutions-completing_checklist).
* Review the information in [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).
* Review the information in [Security and Compliance Readiness Bundle overview](/docs/vmwaresolutions?topic=vmwaresolutions-scb-overview).
* Review the instance and domain name format. The domain name is used to generate the username and server names of the instance.

| Name        | Value format |
|:------------|:------------ |
| Domain name | `<root_domain>` |  
| vCenter Server® login username | `<user_id>@<root_domain>` (Microsoft® Active Directory™ user) or `administrator@vsphere.local` |
| vCenter Server (with embedded PSC) FQDN | `<instance_name>-vc.<root_domain>`. The maximum length is 50 characters. |
| Single Sign-On (SSO) site name | `<root_domain>` |
| Fully qualified ESXi server name | `<host_prefix><n>.<root_domain>`, where `n` is the sequence of the VMware ESXi™ server. The maximum length is 50 characters. |
{: caption="Table 1. Value format for instance and domain names" caption-side="top"}

Do not modify any values that are set during instance order or deployment. Doing so can make your instance unusable. For example, if public networking shuts down, if servers and Virtual Server Instances (VSIs) move behind a Vyatta mid-provision, or if the IBM CloudBuilder VSI stops or is deleted.
{:important}

## Service prerequisites
{: #scb-orderinginstance-serv-prereq}

The following services are required for Security and Compliance Readiness Bundle instances:
* [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* [KMIP for VMware](https://cloud.ibm.com/infrastructure/vmware-solutions/console/servicestandalonenew/KMIPAdapter)

## Resource details
{: #scb-orderinginstance-res-details}

### Instance name
{: #scb-orderinginstance-inst-name}

The instance name is set to **vcs-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify an instance name that meets the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The instance name must start with a lowercase alphabetic character.
* The instance name must end with a lowercase alphabetic or numeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Resource group
{: #scb-orderinginstance-resource-group}

Use resource groups to organize the resources in your account for access control and billing purposes. The default resource group in your account is selected by default. You can also select another resource group according to your needs. The resource group that you select cannot be changed after the instance is created.

If **No resource group available** is displayed in this field, you currently do not have the permission to add the instance to any resource group in this account. Contact the account owner to be assigned an Editor or Administrator role on a resource group in the account. For more information, see [IAM access](/docs/account?topic=account-userroles).
{:note}

### VMware properties
{: #scb-orderinginstance-vm-prpt}

* VMware vSphere® version (vSphere 7.0u1)
* Network virtualization platform (vCenter Server with NSX-T™)
* Instance type (Primary)

## Licensing
{: #scb-orderinginstance-licensing}

Specify the licensing options for the following VMware components in the instance:
* VMware vCenter Server Standard 7.0
* VMware vSphere Enterprise Plus 7.0
* NSX-T 3.1

For Business Partner users, all licenses are included and purchased on your behalf. For users who are not Business Partners, you can use the IBM-provided VMware licenses for these components by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license keys.

### Licensing notes
{: #scb-orderinginstance-licensing-notes}

* The minimum number of licenses for BYOL that are required depends on the number of CPUs per server and the number of servers in the order.
* The minimum license editions are indicated on the user interface. You are responsible to ensure that the license key provided is correct for each VMware component selected.
* For vSphere, a license charge is incurred at the time of order, but the license charge is then credited to your account.
* You can change any licenses that you provided by using the VMware vSphere Web Client after the instance deployment is completed.
* Support for the VMware components that you provide licenses is provided by VMware, not by IBM Support.

## Location
{: #scb-orderinginstance-location}

Select the {{site.data.keyword.cloud_notm}} data center where the consolidated cluster (that is the management cluster) and the workload cluster are to be hosted.

## Consolidated cluster
{: #scb-orderinginstance-consoli}

### Cluster name
{: #scb-orderinginstance-consoli-cluster}

By default, the consolidated cluster name is set to **vcs-_xx_-management**. You can also specify a new cluster name, which must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The cluster name must start with a lowercase alphabetic character.
* The cluster name must end with a lowercase alphabetic or numeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the regulated workload instance.

### CPU model
{: #scb-orderinginstance-consoli-cpu}

You can choose the following CPU models:
* Dual Intel® Xeon® Silver 4210 processor, 20 cores total, 2.20 GHz
* Dual Intel Xeon Gold 5218 processor, 32 cores total, 2.30 GHz
* Dual Intel Xeon Gold 6248 processor, 40 cores total, 2.50 GHz
* Dual Intel Xeon Platinum 8260 processor, 48 cores total, 2.40 GHz
* Quad Intel Xeon Gold 6248 processor, 80 cores total, 2.50 GHz
* Quad Intel Xeon Platinum 8260 processor, 96 cores total, 2.40 GHz

### RAM
{: #scb-orderinginstance-consoli-ram}

You can choose the RAM size from 128 GB, 192 GB, 384 GB, 768 GB, and 1.5 TB.

### Number of bare metal servers
{: #scb-orderinginstance-consoli-bare-metal-number}

* All servers that you order have the same configuration.
* If you are planning to use vSAN™ storage, you can order 4 - 20 servers.
* If you are planning to use NFS storage, you can order 2 - 20 servers.
* If you select two bare metal servers for the management cluster, the minimum RAM size for the instance to function properly is 192 GB.
* For production workloads, a minimum of three servers is recommended. For more information, see [Is a two-node vCenter Server instance highly available?](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions#is-a-two-node-vcenter-server-instance-highly-available)

### Storage
{: #scb-orderinginstance-consoli-storage}

Storage settings are based on your selection of the storage type.

For deployed instances, you can add NFS storage shares to an existing NFS or vSAN cluster. For more information, see [Adding NFS storage to vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingnfs).

#### vSAN storage
{: #scb-orderinginstance-consoli-vsan}

If you select vSAN storage, specify the following settings.

##### Disk type and size for vSAN capacity disks
{: #scb-orderinginstance-consoli-vsan-typesize-capdisks}

Select an option for the capacity disks that you need.

##### Number of vSAN capacity disks
{: #scb-orderinginstance-consoli-vsan-number-capdisks}

Specify the number of capacity disks that you want to add.

##### Disk size for vSAN cache disks
{: #scb-orderinginstance-consoli-vsan-cachedisks}

Review the **Disk size for vSAN cache disks** value.

##### Number of vSAN cache disks
{: #scb-orderinginstance-consoli-vsan-number-cachedisks}

Review **Number of vSAN cache disks**.

##### Enable vSAN deduplication and compression
{: #scb-orderinginstance-consoli-vsan-enable-comp}

vSAN storage depends on the number of servers and your total disk capacity, and the use of deduplication and compression.

The amount of storage reduction from deduplication and compression depends on many factors, including the type of data stored and the number of duplicate blocks. Larger disk groups tend to provide a higher deduplication ratio. For more information, see [Using deduplication and compression](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vsan.doc/GUID-3D2D80CC-444E-454E-9B8B-25C3F620EFED.html){:external}.
{:note}

##### vSAN Enterprise license
{: #scb-orderinginstance-consoli-vsan-license}

Use the IBM-provided VMware license for the vSAN component by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

If your initial cluster was a vSAN cluster, any additional vSAN clusters use the same vSAN license and have the same configuration as the initial one. This is also true if any cluster (initial or additional) in the instance has vSAN selected to be deployed on it. The first time you're prompted for the vSAN license (BYOL or purchased) and the edition. The next time that you select vSAN for a new cluster, the license that is chosen initially is reused.

#### NFS storage
{: #scb-orderinginstance-consoli-nfs}

When you select NFS storage, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. The number of file shares must be in the range 1 - 100.

Specify the following NFS options:
* **Configure shares individually** - Select to specify different configuration settings for each file share.
* **Number of shares** - When you use the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size (GB)** - Select the capacity that meets your shared storage needs.
* **Performance** - Select the IOPS (input/output operations per second) per GB based on your workload requirements.
* **Add shared storage** - Select to add individual file shares that use different configuration settings.

Choose performance level options according to your needs.

| Option        | Details       |
|:------------- |:------------- |
| 0.25 IOPS/GB | This option is designed for workloads that are not used often. Example applications include: vaulted data, hosting large databases with legacy data, or virtual disk images of virtual memory system as backup. |
| 2 IOPS/GB | This option is designed for most general-purpose workloads. Example applications include: hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
| 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. Example applications include transactional databases. |
| 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. Example applications include: high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |
{: caption="Table 2. NFS performance level options" caption-side="top"}

### Networking type
{: #scb-orderinginstance-consoli-private-nics}

Select **Public and private network** or **Private network only** for the consolidated cluster.

### Uplink speed
{: #scb-orderinginstance-consoli-uplink}

The uplink speed provides two options:
* 10 Gb, which is selected by default.
* 25 Gb, which is available only for specific locations.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:-------------------------------------------- |:------ |
| Dallas 10 <br>Dallas 12<br>Dallas 13 | NA South |
| Frankfurt 02 <br>Frankfurt 05 <br>London 06 <br>Paris 04 <br>Paris 05 <br>Paris 06 | Europe |
| Sydney 04 <br>Sydney 05 <br>Tokyo 02 <br>Tokyo 04 <br>Tokyo 05 | Asia-Pacific |
| Toronto 04 <br>Washington DC 04 <br>Washington DC 06 <br>Washington DC 07 | NA East |
{: caption="Table 3. Available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed" caption-side="top"}

### VLANs
{: #scb-orderinginstance-consoli-vlans}

Network settings are based on your selection of **Order new VLANs** or **Select existing VLANs**.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each {{site.data.keyword.cloud_notm}} bare metal server.

#### Order new VLANs
{: #scb-orderinginstance-consoli-new-vlans}

Select to order one new public VLAN and two new private VLANs.

#### Select existing VLANs
{: #scb-orderinginstance-consoli-existing-vlans}

Depending on the {{site.data.keyword.cloud_notm}} data center that you selected, existing public and private VLANs might be available.

When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
* **Public VLAN** is for public network access. If you select the **Allocate a new one** option for this field, a new public VLAN is allocated automatically. This field is only available on the **Public and private network** tab.
* **Public primary subnet** is assigned to physical hosts for public network access. If you select the **Auto assigned** option for this field, a new public primary subnet is selected automatically and a new one is created if necessary. This field is only available on the **Public and private network** tab.
* **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}. If you select the **Allocate a new one** option for this field, a new private VLAN is allocated automatically.
* **Private primary subnet** is assigned to physical hosts for management traffic. If you select the **Auto assigned** option for this field, a new private primary subnet is selected automatically and a new one is created if necessary.
* **Secondary private VLAN** is for VMware features such as vSAN. You can select an existing secondary private VLAN or select to allocate a new one.

Ensure that the firewall configuration on the selected VLANs does not block the management data traffic. Also, ensure that all the VLANs that you select are in the same pod. ESXi servers cannot be provisioned on mixed-pod VLANs.
{:important}  

Optionally, use **Advanced settings** to configure portable subnets for VLANs.

Use the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** tabs to specify the **Portable subnet** for each applicable purpose. If you select the **Allocate a new one** option for this field, a new portable subnet is allocated automatically.

**Notes**:
* You must complete the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** settings before you can configure portable subnets.
* The number of portable subnets is displayed under **Advanced settings** after you save the portable subnet settings. Click **Portable subnets settings** to edit the settings.
* The saved portable subnet settings are cleared if you change the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** settings.

{{site.data.keyword.vmwaresolutions_short}} takes control of the entire subnet and you can't use any IP addresses in the subnet.
{:important}

## Workload cluster
{: #scb-orderinginstance-workload}

You can select to include a separate, additional workload cluster in the same way as you order the consolidated cluster.

## Firewall appliance
{: #scb-orderinginstance-firewall-appl}

You have the following options for your firewall appliance:
* **Edge services cluster with Juniper vSRX** - Order a dedicated cluster for the network edge and firewall components and install Juniper® vSRX on it.
* **Edge services cluster with FortiGate Virtual Appliance** - Order a dedicated cluster for the network edge and firewall components and install FortiGate Virtual Appliance on it.
* **Bring your own gateway appliance** - Order a dedicated cluster for the network edge and firewall components.

The steps that you must follow differ depending on your selection.

## Edge services cluster
{: #scb-orderinginstance-edge}

You must order a dedicated cluster for the network edge and you can select any custom firewall component of your choice.

Review the following restrictions for edge services clusters:
* The data center of the consolidated cluster must be available for edge services cluster deployment. Edge services cluster deployment is not supported for **Dallas 09** and **Hong Kong 02**.
* You cannot add more than one edge services cluster in the same data center pod. If you are adding multiple edge services clusters in the same pod, the clusters would share a transit VLAN, which might cause subsequent issues with the Juniper vSRX installation.

### Cluster name
{: #scb-orderinginstance-edge-cluster-name}

The edge service cluster name must meet the requirements that are listed in [Cluster name](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-cluster-name).

### Data center location
{: #scb-orderinginstance-edge-dc}

The edge services cluster is deployed in the consolidated cluster.

### Compute capacity
{: #scb-orderinginstance-edge-compute}

* Cores - 20
* RAM - 64 GB
* Cluster hosts - 2

### Networking type
{: #scb-orderinginstancee-edge-private-nics}

Select either **Public and private network** or **Private network only** for the edge services cluster.

## Network interface settings
{: #scb-orderinginstance-network-interface}

You must specify the following network interface settings.

### Hostname prefix
{: #scb-orderinginstance-network-interface-host-name-prefix}

The hostname prefix must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The hostname prefix must start with a lowercase alphabetic character.
* The hostname prefix must end with a lowercase alphabetic or numeric character.
* The maximum length of the hostname prefix is 10 characters.

The hostname prefix applies to all clusters in the instance.

### Domain name
{: #scb-orderinginstance-network-interface-domain-name}

The root domain name must meet the following requirements:
* The domain name must consist of three or more strings that are separated by a period (.) with a maximum of 50 characters.
* The first string must start with a lowercase alphabetic character.
* The first string must end with a lowercase alphabetic or numeric character.
* All strings, except for the last one, can contain only lowercase alphabetic, numeric, and dash (-) characters.
* The last string can contain only lowercase alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

The maximum length of the Fully Qualified Domain Name (FQDN) for hosts and VMs is 50 characters. Domain names must accommodate for this maximum length.
{:note}

### Deployment type
{: #scb-orderinginstance-network-interface-deploy-type}

Two highly available dedicated Windows® server VMs are deployed on the management cluster.

## Included services
{: #scb-orderinginstance-include-services}

The following services are included with your VMware Security and Compliance Readiness Bundle instance. Some of the included add-on services require configuration setup.

* [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview) (if you're using **Edge services cluster with Juniper vSRX** as your firewall appliance)
* [FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations) (if you're using **Edge services cluster with FortiGate Virtual Appliance** as your firewall appliance)
* [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview)

## Recommended services
{: #scb-orderinginstance-recmd-services}

The following services are recommended for your Security and Compliance Readiness Bundle instance. Some of the recommended add-on services require configuration setup.

* [Veeam 11](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview)

## Optional services
{: #scb-orderinginstance-opt-services}

The following services are optional for your Security and Compliance Readiness Bundle instance. Some of the optional add-on services require configuration setup.
* [VMware HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)
* [Red Hat OpenShift for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_ordering)

## Procedure to order VMware Security and Compliance Readiness Bundle
{: #scb-orderinginstance-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click the **VMware Solutions Dedicated - Security & Compliance Readiness Bundle** card.
2. On the **VMware Security and Compliance Readiness Bundle** page, review the service prerequisites and confirm that you ordered the mandatory services listed.
3. Under **Resource details**, complete the following settings.
  1. Specify the instance name.
  2. Select the resource group.
  3. Review the properties of the included VMware components.
4. Under **Licensing**, complete the license settings for the listed components.
    * To use IBM-provided licenses, ensure that the option **Include with purchase** is selected.
    * To use your own licenses, click **I will provide** and enter the license key.
5. Under **Location**, select the {{site.data.keyword.cloud_notm}} data center where the consolidated cluster (or management cluster) and the workload cluster are to be hosted.
6. Under **Consolidated cluster**, complete the following settings:
  1. Specify the consolidated cluster name.
  2. Select the CPU model, RAM size, and the number of bare metal servers.
  3. If you select to use vSAN storage, complete the following settings:
      1. Specify the disk type and size for the vSAN capacity disks, and the number of vSAN capacity disks.
      2. Review the predefined disk size for vSAN cache disks and the predefined number of vSAN cache disks.
      3. If you want to enable vSAN deduplication and compression, select the **Enable vSAN deduplication and compression** checkbox.
      4. Specify whether to include the vSAN Enterprise license with your purchase or to use your own license.
  4. If you select to use NFS storage, complete the following settings:
      * To add and configure same settings for all file shares, select the **Number of shares**, **Size (GB)**, and **Performance**.
      * To add and configure file shares individually, select the **Configure shares individually** checkbox. Then, click **Add shared storage** and select the **Size (GB)** and **Performance** for each file share. You must select at least one file share.
  5. Select the private NICs enablement.
  6. Select the uplink speed. The 25 Gb option is available for specific data centers only.
  7. Select the VLAN settings:
      * If you want to order new public and private VLANs, click **Order new VLANs**.
      * If you want to reuse the existing public and private VLANs when they are available, click **Select existing VLANs** and specify the VLANs and the subnets.
      * Optionally click **Portable subnets settings**. Then, select the portable subnet for each purpose and click **Save**.

       If the consolidated or management cluster and the workload clusters are in the same location, you cannot use existing VLANs. Instead, the workload clusters reuse the VLANs from the management cluster.
       {:note}

7. (Optional) Under **Workload cluster**, select the **Include a separate, additional workload cluster** checkbox, and then specify the workload cluster settings. The configuration options are the same as the options for the consolidated cluster.
8. Choose the firewall appliance for your instance and follow the steps, depending on your selection:
   1. Specify the edge services [cluster name](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-orderinginstance#vrw-orderinginstance-cluster-name-req), the CPU model, the RAM size, the uplink speed, and the networking type.
   2. For **Edge services cluster with Juniper vSRX** and **Edge services cluster with FortiGate Virtual Appliance**, you must also specify the corresponding service settings in a later step.
9. Under **Network interface**, complete the following settings:
  1. Specify the hostname prefix and the root domain name.
  2. Review the deployment type.
10. Under **Included services**, review the add-on services to be deployed into the instance. If a service requires configuration, complete the service-specific settings by clicking **Edit** on the service card. Then, complete your edits and click **Save**. For more information about specific settings for a service, see the corresponding topic for ordering the service.
11. Under **Recommended services** and **Optional services**, review the service options. If you want to deploy an add-on service, toggle the switch on and review the service settings. If configuration is required, click **Edit**, then complete the edits and click **Save**. For more information about specific settings for a service, see the corresponding topic for ordering the service.
12. On the **Summary** pane, review the instance settings and the estimated price.
13. To place the order, ensure that the account to be charged is correct, review and accept the terms, and then click **Create**.

### Results after you place an order
{: #scb-orderinginstance-results-order}

The deployment of the Security and Compliance Readiness Bundle instance starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Deployment history** tab on the instance details page.

When the instance is successfully deployed, the ordered components are installed on your VMware virtual platform. The deployment of the services starts after your order is completed. When the instance is ready to use, the status of the instance is changed to **Ready to use** and you receive a notification by email.

Next, you can view and manage the Security and Compliance Readiness Bundle instance that you ordered.

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the {{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.
{:important}

**CAUTION:** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

## Related links
{: #scb-orderinginstance-related}

* [Signing up for an {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-signing_required_accounts#signing_required_accounts-cloud)
* [Requirements and planning Security and Compliance Readiness Bundle](/docs/vmwaresolutions?topic=vmwaresolutions-scb-planning)
* [Viewing and deleting Security and Compliance Readiness Bundle instances](/docs/vmwaresolutions?topic=vmwaresolutions-scb-view-delete-instance)
