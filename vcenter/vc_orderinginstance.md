---

copyright:

  years:  2016, 2021

lastupdated: "2021-12-09"

keywords: vCenter Server order instance, order vCenter Server, order vCenter Server instance

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Ordering vCenter Server instances
{: #vc_orderinginstance}

To deploy a flexible and customizable VMware® virtualized platform that best fits your workload needs, order a VMware vCenter Server® instance.

You can also add services, such as [Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-addingzertodr) for disaster recovery. For more information about the available services, see [Available services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices#vc_addingservices-available-services). Add-on services support varies between vCenter Server with NSX-V and vCenter Server with NSX-T™ instances.

New deployments of vCenter Server multizone instances are not supported.
{: deprecated}

## Requirements for vCenter Server instances
{: #vc_orderinginstance-req}

Ensure that you complete the following tasks:
* If you are ordering an instance for the first time, complete the tasks in the **Before you begin** section on the ordering page. For more information, see [Setting up your environment for your first order](/docs/vmwaresolutions?topic=vmwaresolutions-completing_checklist).
* Review the information in [Requirements and planning for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning).
* Review the instance and domain name format. The domain name is used to generate the username and server names of the instance.

The subdomain label is not used for VMware vSphere® 7.0 instances.
{: note}

| Name        | Value format |
|:------------|:------------ |
| Domain name | `<root_domain>` |  
| vCenter Server login username | `<user_id>@<root_domain>` (Microsoft® Active Directory™ user) or `administrator@vsphere.local` |
| vCenter Server (with embedded PSC) FQDN | `<instance_name>-vc.<root_domain>`. The maximum length is 50 characters. |
| Single sign-on (SSO) site name | `<root_domain>` |
| Fully qualified VMware ESXi™ server name | `<host_prefix><n>.<root_domain>`, where `n` is the sequence of the ESXi server. The maximum length is 50 characters. |
{: caption="Table 1. Value format for instance and domain names" caption-side="top"}

Do not modify any values that are set during instance order or deployment. Doing so can make your instance unusable. For example, if public networking shuts down, if servers and Virtual Server Instances (VSIs) move behind a Vyatta mid-provision, or if the IBM CloudBuilder VSI stops or is deleted.
{: important}

## System settings
{: #vc_orderinginstance-sys-settings}

You must specify the following system settings when you order a vCenter Server instance.

### Instance configurations
{: #vc_orderinginstance-inst-config}

* You can select **New configuration** to specify settings for an instance and place the order or save the settings as a configuration template without placing an order.
* You can also select a saved configuration template to further edit it, or to update it and then save it as a new configuration template.

### Instance name
{: #vc_orderinginstance-inst-name}

The instance name is set to **vcs-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify an instance name that meets the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The instance name must start with a lowercase alphabetic character.
* The instance name must end with a lowercase alphabetic or numeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Resource group
{: #vc_orderinginstance-resource-group}

Use resource groups to organize the resources in your account for access control and billing purposes. The default resource group in your account is selected by default. You can also select another resource group according to your needs. The resource group that you select cannot be changed after the instance is created.

If **No resource group available** is displayed in this field, you currently do not have the permission to add the instance to any resource group in this account. Contact the account owner to be assigned an Editor or Administrator role on a resource group in the account. For more information, see [IAM access](/docs/account?topic=account-userroles).
{: note}

### Initial cluster name (NSX-V only)
{: #vc_orderinginstance-cluster-name}

The initial cluster name is set to **_instance name_-cluster** by default.

You can also specify a new initial cluster name that meets the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The cluster name must start with a lowercase alphabetic character.
* The cluster name must end with a lowercase alphabetic or numeric character.
* The maximum length of the cluster name is 30 characters.
* The cluster name must be unique within the vCenter Server instance.

### VMware vSphere version
{: #vc_orderinginstance-vsphere-license}

* For vCenter Server with NSX-T instances, only vSphere Enterprise Plus 7.0u1 is supported.
* For vCenter Server with NSX-V instances, only vSphere Enterprise Plus 6.7u3 is supported.

#### Notes on upgrading to vSphere 7
{: #vc_orderinginstance-vsphere-v6-7-upgrade}

For vCenter Server instances with vSphere 6.7, upgrade to vSphere 7 is supported for selected configurations. If you want to use vSphere 7.0, you have the following options:
* Deploy a new vSphere 7.0 instance and migrate your current workloads to the new instance.
* Contact VMware Solutions Support for assistance with your upgrade process.

Migrating your workloads is recommended in the following cases:
* If you want to perform a hardware refresh.
* If you want to migrate from NSX–V to NSX–T.
* If you want to migrate your existing NSX–T topology with separate management and workload clusters to a converged topology.

### VMware NSX networking solution
{: #vc_orderinginstance-nsx}

* If you select vSphere 7.0u1, the VMware NSX networking solution is set to **NSX-T**.
* If you select vSphere 6.7u3, the VMware NSX networking solution is set to **NSX-V**.

### Instance type
{: #vc_orderinginstance-primary-secondary}

Select whether to order a new primary instance or a secondary instance for an existing primary instance.

## Licensing settings
{: #vc_orderinginstance-licensing-settings}

### License options
{: #vc_orderinginstance-licensing-opt}

Specify the licensing options for the VMware components in the instance.

For vCenter Server with NSX-T instances:
* VMware vSphere Enterprise Plus 7.0
* NSX-T 3.1.1 (Data Center SP Base, Data Center SP Professional, Data Center SP Advanced, or Data Center SP Enterprise Plus)

The VMware HCX service is not available for Data Center SP Enterprise Plus.

Small differences exist between NSX-T Data Center and Data Center SP editions. For more information, see [Product offerings for VMware NSX-T Data Center 3.1.x (80866)](https://kb.vmware.com/s/article/80866){: external}.
{: note}

For vCenter Server with NSX-V instances:
* vSphere 6.7
* NSX Service Providers 6.4 (Base, Advanced, or Enterprise edition). The VMware HCX™ service requires either the NSX Advanced or NSX Enterprise edition license.

For Business Partner users, the vCenter Server license (Standard edition), the vSphere license (Enterprise Plus edition), and the NSX license are included and purchased on your behalf. However, you must specify the edition for the NSX license.

For users who are not Business Partners, you can use the IBM-provided VMware licenses for these components by selecting **Include with purchase**, or you can Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license keys.

### Licensing notes
{: #vc_orderinginstance-licensing-notes}

* The minimum number of licenses for BYOL that are required depends on the number of CPUs per server and the number of servers in the order. The license choice for each VMware component applies to the base instance and to any ESXi servers that you add to the instance later. Ensure that your license supports future capacity expansion in your infrastructure.
* The minimum license editions are indicated on the user interface. If different component editions are supported, you can select the edition that you want. You are responsible to ensure that the license key provided is correct for each VMware component selected.
* For vSphere, a license charge is incurred at the time of order, but the license charge is then credited to your account.
* You can change any licenses that you provided by using the VMware vSphere Web Client after the instance deployment is completed.
* Support for the VMware components that you provide licenses is provided by VMware, not by IBM Support.

## Cluster name
{: #vc_orderinginstance-mngt-workload-cluster-settings}

vCenter Server instances are deployed with a consolidated cluster (for vSphere 7) or a management cluster (for vSphere 6.7), in which all the VMware management components and user workloads run.

Optionally, for vSphere 7, you can order an additional workload cluster.

For both vSphere 7 and vSphere 6.7, you can order an edge services cluster.

By default, the cluster names are set to the following values:
* For the consolidated cluster (vSphere 7) - **_instance name_-consolidated**
* For the management cluster (vSphere 6.7) - **_instance name_-cluster**
* For the workload cluster (vSphere 6.7) - **_instance name_-workload**
* For the edge services cluster (vSphere 6.7) - **_instance name_-edge**

You can also specify a new name for your clusters. The names must meet the requirements that are listed in [Initial cluster name](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-cluster-name).

## Bare metal server settings
{: #vc_orderinginstance-bare-metal-settings}

Bare metal settings are based on your data center selection and bare metal server configuration. When you size the capacity of your servers, consider your current requirements and include extra capacity to accommodate anticipated growth. For more information about sizing, see [Exporting VMware inventory](/docs/vmwaresolutions?topic=vmwaresolutions-vmware-inventory-export).

### Data center location
{: #vc_orderinginstance-dc}

Select the {{site.data.keyword.cloud_notm}} data center settings. For more information, see [Region and data center locations for resource deployment](/docs/overview?topic=overview-locations).

#### Geography
{: #vc_orderinginstance-dc-region}

Select the region where your consolidated cluster or instance is hosted.

#### Data center
{: #vc_orderinginstance-dc-location}

* For NSX-T, select the {{site.data.keyword.cloud_notm}} data center where the consolidated cluster is hosted.
* For NSX-V, select the {{site.data.keyword.cloud_notm}} data center where the instance is hosted.

#### Pod
{: #vc_orderinginstance-dc-pod}

Select the {{site.data.keyword.cloud_notm}} data center pod where you want to deploy your resources. Keep the default pod selection if you do not have reasons to prefer a different pod.

### Skylake
{: #vc_orderinginstance-skylake}

For **Skylake** servers, you can choose the following CPU models and a supported RAM size, which depends on the NSX networking solution.

Skylake servers are not supported for vSphere Enterprise Plus 7.0u1 instances.
{: note}

| CPU model     | RAM sizes   |
|:------------- |:----------- |
| Dual Intel® Xeon® Silver 4110 processor / 16 cores, 2.1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 processor / 28 cores, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 processor / 36 cores, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Options for Skylake bare metal servers" caption-side="top"}
{: class="simple-tab-table"}
{: #simpletabtable5}
{: tab-title="NSX-V"}
{: tab-group="SkyLake Intel servers"}

| CPU model     | RAM sizes   |
|:------------- |:----------- |
| Dual Intel® Xeon® Silver 4110 processor / 16 cores, 2.1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5120 processor / 28 cores, 2.2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6140 processor / 36 cores, 2.3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
{: caption="Table 2. Options for Skylake bare metal servers" caption-side="top"}
{: class="simple-tab-table"}
{: #simpletabtable6}
{: tab-title="NSX-T"}
{: tab-group="SkyLake Intel servers"}

### Cascade Lake
{: #vc_orderinginstance-cascade}

For **Cascade Lake** servers, you can choose the following CPU models and a supported RAM size, which depends on the NSX networking solution.

| CPU model     | RAM sizes   |
|:------------- |:----------- |
| Dual Intel Xeon Silver 4210 processor / 20 cores, 2.2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 processor / 32 cores, 2.3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 processor / 40 cores, 2.5 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6250 processor / 16 cores, 3.9 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Platinum 8260 processor / 48 cores, 2.4 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Gold 6248 processor / 80 cores, 2.5 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8260 processor / 96 cores, 2.4 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
{: caption="Table 3. Options for Cascade Lake bare metal servers" caption-side="top"}
{: class="simple-tab-table"}
{: #simpletabtable3}
{: tab-title="NSX-V"}
{: tab-group="Cascade Lake Intel servers"}

| CPU model     | RAM sizes   |
|:------------- |:----------- |
| Dual Intel Xeon Silver 4210 processor / 20 cores, 2.2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 processor / 32 cores, 2.3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 processor / 40 cores, 2.5 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6250 processor / 16 cores, 3.9 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Platinum 8260 processor / 48 cores, 2.4 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Gold 6248 processor / 80 cores, 2.5 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8260 processor / 96 cores, 2.4 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
{: caption="Table 3. Options for Cascade Lake bare metal servers" caption-side="top"}
{: class="simple-tab-table"}
{: #simpletabtable4}
{: tab-title="NSX-T"}
{: tab-group="Cascade Lake Intel servers"}

### SAP-certified
{: #vc_orderinginstance-sap}

For **SAP-certified** servers, you have the following options:
* **NetWeaver**, for which the CPU and RAM size are preset.
* **HANA**, for which you can choose the CPU model and a supported RAM size, which depends on the NSX networking solution.

| CPU model     | RAM sizes   |
|:------------- |:----------- |
| Dual Intel Xeon Gold 5218 processor (Cascade Lake, BI.S4.NW192) / 32 cores, 2.3 GHz | 192 GB |
| Dual Intel Xeon Gold 5218 processor (Cascade Lake, BI.S4.NW384) / 32 cores, 2.3 GHz | 384 GB |
| Dual Intel Xeon Gold 6248 processor (Cascade Lake, BI.S4.NW768) / 40 cores, 2.5 GHz | 768 GB |
| Dual Intel Xeon Platinum 8280M processor (Cascade Lake, BI.S4.NW1500) / 56 cores, 2.7 GHz | 1.5 TB |
| Dual Intel Xeon Platinum 8280M processor (Cascade Lake, BI.S4.NW3000) / 56 cores, 2.7 GHz | 3 TB |
{: caption="Table 4. Options for SAP-certified bare metal servers - NetWeaver" caption-side="top"}
{: class="simple-tab-table"}
{: #simpletabtable1}
{: tab-title="NetWeaver"}
{: tab-group="SAP-certified Intel servers"}

| CPU model     | RAM sizes |
|:------------- |:--------- |
| Dual Intel Xeon Gold 5218 processor (Cascade Lake) / 32 cores, 2.3 GHz | 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Dual Intel Xeon Gold 6248 processor (Cascade Lake) / 40 cores, 2.5 GHz| 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Dual Intel Xeon Platinum 8280M processor (Cascade Lake) / 56 cores, 2.7 GHz | 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8280M processor (Cascade Lake) / 112 cores, 2.7 GHz | 3 TB, 6 TB |
{: caption="Table 4. Options for SAP-certified bare metal servers - HANA" caption-side="top"}
{: #simpletabtable2}
{: tab-title="HANA"}
{: tab-group="SAP-certified Intel servers"}
{: class="simple-tab-table"}

### Number of bare metal servers
{: #vc_orderinginstance-bare-metal-number}

* All servers that you order have the same configuration.
* If you are planning to use vSAN™ storage, you can order 4 - 20 servers.
* If you are planning to use NFS storage, you can order 2 - 20 servers. A lower limit of three servers applies for NSX-T consolidated clusters.
* If you select two bare metal servers for the consolidated cluster, the minimum RAM size for the instance to function properly is 192 GB.
* For production workloads, a minimum of three servers is recommended. For more information, see [Is a two-node vCenter Server instance highly available?](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions#is-a-two-node-vcenter-server-instance-highly-available)

## Storage settings
{: #vc_orderinginstance-storage-settings}

Storage settings are based on your selection of bare metal server configuration and the storage type.

For deployed instances, you can add NFS storage shares to an existing NFS or vSAN cluster. For more information, see [Adding NFS storage to vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingnfs).

### vSAN storage
{: #vc_orderinginstance-vsan-storage}

vSAN is available for the **Skylake** and **Cascade Lake** bare metal configurations only.

#### Size for vSAN capacity disks
{: #vc_orderinginstance-vsan-storage-typesize-capdisks}

Select an option for the capacity disks that you need.

#### Number of vSAN capacity disks
{: #vc_orderinginstance-vsan-storage-number-capdisks}

Specify the number of capacity disks that you want to add.

* For vSphere 7.0, order up to 10 disks for Dual CPU models and order up to 8 disks for Quad CPU models.
* For vSphere 6.3, order up to 12 disks with Intel Optane for Dual CPU models and order up to 8 disks for Quad CPU models.

If you want to add more capacity disks, select the **High performance with Intel Optane** checkbox. This option provides two extra capacity disk bays, which are useful for workloads that require less latency and higher IOPS throughput.

The **High performance with Intel Optane** option is available only for vSphere 6 instances.
{: note}

#### Size for vSAN cache disks
{: #vc_orderinginstance-vsan-storage-size-cachedisks}

Review the **Size for vSAN cache disks** value. The value depends on whether you selected the **High performance with Intel Optane** checkbox.

#### Number of vSAN cache disks
{: #vc_orderinginstance-vsan-storage-number-cachedisks}

Review **Number of vSAN cache disks**. The value depends on whether you selected the **High performance with Intel Optane** checkbox.

#### Enable vSAN deduplication and compression
{: #vc_orderinginstance-vsan-storage-enable-comp}

vSAN storage depends on the number of servers and your total disk capacity, and the use of deduplication and compression.

The amount of storage reduction from deduplication and compression depends on many factors, including the type of data stored and the number of duplicate blocks. Larger disk groups tend to provide a higher deduplication ratio. For more information, see [Using deduplication and compression](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vsan.doc/GUID-3D2D80CC-444E-454E-9B8B-25C3F620EFED.html){: external}.
{: note}

#### vSAN license
{: #vc_orderinginstance-vsan-storage-license}

Use the IBM-provided VMware license for the vSAN component by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

If your initial cluster is a vSAN cluster, any additional vSAN clusters use the same vSAN license and have the same configuration as the initial one. This statement is also true for any initial or additional clusters in the instance for which you select vSAN. The first time you're prompted for the vSAN license (BYOL or purchased) and the edition. The next time that you select vSAN for a new cluster, the license that is chosen initially is reused.

### NFS storage
{: #vc_orderinginstance-nfs-storage}

When you select **NFS storage**, you can add file-level shared storage for your instance where all shares use the same settings or you can specify different configuration settings for each file share. The number of file shares must be in the range 1 - 100.

Specify the following NFS options:
* **Configure shares individually** - Select to specify different configuration settings for each file share.
* **Number of shares** - When you use the same configuration setting for each file share, specify the number of file shares for the NFS shared storage that you want to add.
* **Size (GB)** - Select the capacity that meets your shared storage needs.
* **Performance** - Select the IOPS (input/output operations per second) per GB based on your workload requirements.
* **Add shared storage** - Select to add individual file shares that use different configuration settings.

Choose performance level options according to your needs.

| Option       | Details       |
|:------------ |:------------- |
| 0.25 IOPS/GB | This option is designed for workloads that are not used often. For example, vaulted data, hosting large databases with legacy data, or virtual disk images of virtual memory system as backup. |
| 2 IOPS/GB | This option is designed for most general-purpose workloads. For example, hosting small databases, backing up web applications, or virtual machine disk images for a hypervisor. |
| 4 IOPS/GB | This option is designed for higher-intensity workloads that have a high percentage of active data at a time. For example, transactional databases. |
| 10 IOPS/GB | This option is designed for the most demanding workload types, such as analytics. For example, high-transaction databases and other performance-sensitive databases. This performance level is limited to a maximum capacity of 4 TB per file share. |
{: caption="Table 5. NFS performance level options" caption-side="top"}

### Local disks (NSX-V SAP-certified HANA only)
{: #vc_orderinginstance-local-disks}

The **Local disks** option is enabled for the **SAP-certified** - **HANA** CPU generation only.
{: note}

Specify the following settings:
* **Local disk count** - Select the number of disks that you want to add. The first two disks are reserved, so a minimum of four disks is required.
* **Local disk type** - Select an option for the disk type that you need.

## Edge services cluster
{: #vc_orderinginstance-edge-services-cluster}

Select the **Edge services cluster** checkbox to order a dedicated cluster for the network edge and the firewall components that are required for the Juniper® vSRX service. The edge services cluster is deployed in:
* For NSX-T - the consolidated cluster
* For NSX-V - the same data center as the instance

Review the following restrictions for edge services clusters:
* The data center of the consolidated cluster (for NSX-T) or the instance (for NSX-V) must be available for edge services cluster deployment. Edge services cluster deployment is not supported for **Dallas 09** and **Hong Kong 02**.
* You cannot add more than one edge services cluster in the same data center pod. If you add multiple edge services clusters in the same pod, the clusters would share a transit VLAN, which might cause subsequent issues with the Juniper vSRX installation.

### Cluster name
{: #vc_orderinginstance-edge-cluster-name}

The cluster name must meet the requirements that are listed in [Cluster name](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-cluster-name).

### CPU model
{: #vc_orderinginstance-edge-cluster-cpu}

You can choose the following CPU models:
* Dual Intel Xeon Silver 4210 processor (Cascade Lake)
* Dual Intel Xeon Gold 5218 processor (Cascade Lake)

### RAM
{: #vc_orderinginstance-edge-cluster-ram}

You can select different values between 64 GB and 1.5 TB.

### Number of bare metal servers
{: #vc_orderinginstance-edge-cluster-bare-metal}

The number of servers is set to two and cannot be changed. Both servers have the same configuration.

### Networking type
{: #vc_orderinginstance-edge-cluster-private-nics}

Select either **Public and private network** or **Private network only** for the edge services cluster.

## Network interface settings
{: #vc_orderinginstance-network-interface-settings}

You must specify the following network interface settings when you order a vCenter Server instance.

### Hostname prefix
{: #vc_orderinginstance-host-name-prefix}

The hostname prefix must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The hostname prefix must start with a lowercase alphabetic character.
* The hostname prefix must end with a lowercase alphabetic or numeric character.
* The maximum length of the hostname prefix is 10 characters.

The hostname prefix applies to all clusters in the instance.
{: note}

### Subdomain label
{: #vc_orderinginstance-subdomain-name}

The subdomain label must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The subdomain label must start with a lowercase alphabetic character.
* The subdomain label must end with a lowercase alphabetic or numeric character.
* The maximum length of the subdomain label is 10 characters.
* The subdomain label must be unique within all instances in your multi-site configuration.

The subdomain label is not used for vSphere 7.0 instances.
{: note}

### Domain name
{: #vc_orderinginstance-domain-name}

The root domain name must meet the following requirements:
* For vSphere 7.0 instances, the domain name must consist of three or more strings that are separated by a period (.) with a maximum of 50 characters.
* For vSphere 6.7 instances, the domain name must consist of two or more strings that are separated by a period (.)
* The first string must start with a lowercase alphabetic character.
* The first string must end with a lowercase alphabetic or numeric character.
* All strings, except for the last one, can contain only lowercase alphabetic, numeric, and dash (-) characters.
* The last string can contain only lowercase alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

The maximum length of the Fully Qualified Domain Name (FQDN) for hosts and VMs is 50 characters. Domain names must accommodate for this maximum length.
{: note}

### Networking type
{: #vc_orderinginstance-public-private-network}

Select **Public and private network** or **Private network only**.

For NSX-V, if you select the **Private network only** option:
* The VMware NSX Edge Services Gateways (the management services ESG and the customer-managed ESG) are not provisioned.
* The following add-on services, which require public NICs, are not available:
   * F5® BIG-IP®
   * FortiGate® Virtual Appliance

### Uplink speed
{: #vc_orderinginstance-uplink}

The uplink speed provides two options:
* 10 Gb, which is selected by default.
* 25 Gb, which is available only for **Cascade Lake** and **SAP-certified** bare metal servers and for specific locations. The following table shows the available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:-------------------------------------------- |:------ |
| Dallas 10 \n Dallas 12 \n Dallas 13 | NA South |
| Frankfurt 02 \n Frankfurt 05 \n London 06 | Europe |
| Sydney 04 \n Sydney 05 \n Tokyo 02 \n Tokyo 04 \n Tokyo 05 | Asia-Pacific |
| Toronto 04 \n Washington DC 04 \n Washington DC 06 \n Washington DC 07 | NA East |
{: caption="Table 6. Available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed" caption-side="top"}

### VLANs
{: #vc_orderinginstance-vlans}

Network settings are based on your selection of **Order new VLANs** or **Select existing VLANs**.

One public VLAN and two private VLANs are required for your instance order. The two private VLANs are trunked into each {{site.data.keyword.cloud_notm}} bare metal server.

#### Order new VLANs
{: #vc_orderinginstance-new-vlans}

Select to order one new public VLAN and two new private VLANs.

#### Select existing VLANs
{: #vc_orderinginstance-existing-vlans}

Depending on the {{site.data.keyword.cloud_notm}} data center that you selected, existing public and private VLANs might be available.

When you select to reuse existing public and private VLANs, specify the VLANs and subnets:
* **Public VLAN** is for public network access. If you select the **Allocate a new one** option for this field, a new public VLAN is allocated automatically. This field is only available on the **Public and private network** tab.
* **Public primary subnet** is assigned to physical hosts for public network access. If you select the **Auto assigned** option for this field, a new public primary subnet is selected automatically and a new one is created if necessary. This field is only available on the **Public and private network** tab.
* **Private VLAN** is for connectivity among the data centers and services within the {{site.data.keyword.cloud_notm}}. If you select the **Allocate a new one** option for this field, a new private VLAN is allocated automatically.
* **Private primary subnet** is assigned to physical hosts for management traffic. If you select the **Auto assigned** option for this field, a new private primary subnet is selected automatically and a new one is created if necessary.
* **Secondary private VLAN** is for VMware features such as vSAN. You can select an existing secondary private VLAN or select to allocate a new one.

Ensure that the firewall configuration on the selected VLANs does not block the management data traffic. Also, ensure that all the VLANs that you select are in the same pod. ESXi servers cannot be provisioned on mixed-pod VLANs.
{: important}  

Optionally, use **Advanced settings** to configure portable subnets for VLANs.

Use the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** tabs to specify the **Portable subnet** for each applicable purpose. If you select the **Allocate a new one** option for this field, a new portable subnet is allocated automatically.
**Notes**
* You must complete the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** settings before you can configure portable subnets.
* The number of portable subnets is displayed under **Advanced settings** after you save the portable subnet settings. Click **Portable subnets settings** to edit the settings.
* The saved portable subnet settings are cleared if you change the **Public VLAN**, **Private VLAN**, or **Secondary private VLAN** settings.

{{site.data.keyword.vmwaresolutions_short}} takes control of the entire subnet and you can't use any IP addresses in the subnet.
{: important}

### Domain Name System configuration
{: #vc_orderinginstance-dns-config}

Select the Domain Name System (DNS) configuration for your instance:

* **Single public Windows VSI for Active Directory/DNS** - A single Microsoft Windows® Server VSI for Microsoft Active Directory (AD) is deployed and can be looked up. The VSI functions as the DNS for the instance where the hosts and VMs are registered.
* **Two highly available dedicated Windows server VMs on the management cluster** - Two Microsoft Windows VMs are deployed, helping enhance security and robustness.

You must provide two Microsoft Windows Server 2019 Standard edition licenses if you configure your instance to use the two Microsoft Windows VMs.
{: important}

Each license can be assigned only to one single physical server and covers up to two physical processors. One Standard edition license can run two virtualized Microsoft Windows VMs per 2-processor server. Therefore, two licenses are required since two Microsoft Windows VMs are deployed in two different hosts.

You have 30 days to activate the VMs.

For more information about ordering Windows Server 2019 licenses, see [Get started with Windows Server 2019](https://docs.microsoft.com/en-us/windows-server/get-started-19/get-started-19){: external}.

## Services settings
{: #vc_orderinginstance-addon-services}

When you order a vCenter Server instance, you can also order add-on services. For more information about the services, see [Available services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices#vc_addingservices-available-services).

## Summary
{: #vc_orderinginstance-order-summary}

Based on your selected configuration for the instance and add-on services, the estimated price is instantly generated and displayed on the **Summary** pane. Click **Pricing details** to generate a PDF document with the price summary for the {{site.data.keyword.vmwaresolutions_short}} resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool by clicking **Add to estimate**. The estimator is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to order vCenter Server instances
{: #vc_orderinginstance-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click the **VMware Solutions Dedicated** card in the **IaaS platforms** section.
2. On the **VMware Solutions Dedicated** page, click the **vCenter Server** card.
3. Specify the instance configuration:
    * If you want to create a new configuration, select **New configuration**.
    * If you want to update a saved configuration or create a new configuration based on a saved one, select a saved configuration.
4. Enter the instance name and select a resource group.
5. Select the VMware vSphere version. Depending on the vSphere version, the VMware NSX networking solution defaults to either **NSX-V** or **NSX-T**.
6. (NSX-V only) Accept the default value for the initial cluster name or specify your own name.
7. Select the instance type:
   * Click **Primary instance** to deploy a single instance in the environment or to deploy the first instance in a multi-site topology.
   * Click **Secondary instance** to connect the instance with an existing (primary) instance in the environment for high availability. Select the primary instance that you want the secondary instance to be connected with, then enter the vCenter Server Administrator password for the primary instance.
8. Complete the license settings for the instance components.
    * To use IBM-provided licenses, ensure that **Include with purchase** is selected. For NSX, specify the license edition.
    * To use your own licenses, for each license, click **I will provide** and enter the license key.
9. (NSX-T only) Specify the settings for the consolidated cluster and the optional workload cluster.
    1. Specify the cluster name.
    2. Complete the bare metal server settings.
       1. For data center location, click the **Edit** icon ![Edit icon](../../icons/edit-tagging.svg "Edit") and select the geography, data center, and pod to host the instance or cluster.
       2. Select the bare metal server CPU generation.
          * For **Cascade Lake** or **SAP-certified** - **HANA** servers, specify the CPU model and the RAM size.
          * For **SAP-certified** - **NetWeaver** server, choose one of the preset configurations.
       3. Specify the number of bare metal servers. For more information about selecting bare metal servers, see [Number of bare metal servers](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-bare-metal-number).
    3. If you want to use NFS storage, select the corresponding option.
       * To add and configure file shares individually, select **Configure shares individually**. Then, click **Add shared storage** and select the **Size (GB)** and **Performance** for each file share. You must select at least one file share.
       * To add and configure the same settings to all file shares, specify the **Number of shares**, **Size (GB)**, and **Performance**.
    4. If you want to use vSAN storage, select the corresponding option.
       * If you want more storage, select the **High performance with Intel Optane** checkbox (vSphere 6 instances only).
       * Specify the disk type and size for the vSAN capacity disks, the number of vSAN capacity disks, the disk size for vSAN cache disks, and the number of vSAN cache disks.
       * By default, the **Enable vSAN deduplication and compression** checkbox is selected. If you do not want to enable vSAN deduplication and compression, clear the checkbox.
       * Specify the vSAN license edition.
    5. Select the private NICs enablement.
    6. Select the uplink speed. The 25 Gb option is available for Cascade Lake servers and for specific data centers only.
    7. Select the VLAN settings:
       * If you want to order new public and private VLANs, click **Order new VLANs**.
       * If you want to reuse the existing public and private VLANs when they are available, click **Select existing VLANs** and specify the VLANs and the subnets.
       * Optionally click **Portable subnets settings**. Then, select the portable subnet for each purpose and click **Save**.
    8. Optionally select the **Include a separate, additional workload cluster** checkbox, then specify the settings if you want to include an additional workload cluster with your instance.
       If the consolidated or management cluster and the workload clusters are in the same location, you cannot use existing VLANs. Instead, the workload clusters reuse the VLANs from the management cluster.
       {: note}

10. (NSX-V only) Complete the bare metal server and storage settings.
    1. Complete the bare metal server settings.
       1. Select the {{site.data.keyword.cloud_notm}} data center to host the instance or cluster.
       2. Select the bare metal server CPU generation.
          * For **Cascade Lake** or **SAP-certified** - **HANA** servers, specify the CPU model and the RAM size.
          * For **SAP-certified** - **NetWeaver** server, choose one of the preset configurations.
       3. Specify the number of bare metal servers. For more information about selecting bare metal servers, see [Number of bare metal servers](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-bare-metal-number).
    2. If you want to use NFS storage, select the corresponding option.
       * To add and configure file shares individually, select **Configure shares individually**. Then, click **Add shared storage** and select the **Size (GB)** and **Performance** for each file share. You must select at least one file share.
       * To add and configure the same settings to all file shares, specify the **Number of shares**, **Size (GB)**, and **Performance**.
       * (NSX-V SAP-certified only) If you select **Local disks**, specify the local disk count and local disk type.
    3. If you want to use vSAN storage, select the corresponding option.
       * For Skylake and Cascade Lake bare metal servers, select the **High performance with Intel Optane** checkbox if you want more storage.
       * Specify the disk type and size for the vSAN capacity disks, the number of vSAN capacity disks, the disk size for vSAN cache disks, and the number of vSAN cache disks.
       * By default, the **Enable vSAN deduplication and compression** checkbox is selected. If you do not want to enable vSAN deduplication and compression, clear the checkbox.
       * Specify the vSAN license edition.
11. If you want to order an edge services cluster with Juniper vSRX included, select the **Edge services cluster** checkbox and configure the appropriate settings: the cluster name, the CPU model, RAM size, the number of bare metal servers, the uplink speed, and the private NICs enablement.
12. Complete the network interface settings.
    1. Enter the hostname prefix for the instance that you are provisioning, the subdomain label (vSphere 6.7u3 instances only), and the root domain name. For a secondary instance, the domain name is automatically completed.
    2. (NSX-V only) Select the private NICs enablement.
    3. (NSX-V only) Select the uplink speed. The 25 Gb option is available for Cascade Lake servers and for specific data centers only.
    4. (NSX-V only) Select the VLAN settings:
       * If you want to order new public and private VLANs, click **Order new VLANs**.
       * If you want to reuse the existing public and private VLANs when they are available, click **Select existing VLANs** and specify the VLANs and the subnets.
       * Optionally click **Portable subnets settings**. Then, select the portable subnet for each purpose and click **Save**.
    5. Specify the DNS configuration.
13. Under **Recommended services** and **Optional services**, review the service options. If you want to deploy an add-on service, toggle the switch on and review the service settings. If configuration is required, click **Edit**, then complete the edits and click **Save**. For more information about specific settings for a service, see the corresponding topic for ordering the service.
14. On the **Summary** pane, review the instance settings and the estimated price.

    * To save the settings as a new configuration template without placing an order, click **Save configuration**, enter a name for the configuration, and click **Continue**.
    * To save the updates to a saved configuration, click **Save configuration**, select **Modify current configuration**, and click **Continue**.
    * To save the updates to a new saved configuration, click **Save configuration**, select **Create new configuration**, enter a new name for the configuration, and click **Continue**.
15. To place the order, ensure that the account to be charged is correct, review and accept the terms, and then click **Create**.

### Results if you saved a configuration
{: #vc_orderinginstance-results-config}

You get a console notification that the configuration is saved successfully, and then you can find the template in the **Instance configurations** list. Next, you can manage the configuration template by viewing or deleting it in the **Instance configurations** list.

### Results if you placed an order
{: #vc_orderinginstance-results-order}

* The deployment of the instance starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Deployment history** section of the instance details.
* When the instance is successfully deployed, the components that are described in [Technical specifications for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview#vc_vcenterserveroverview-specs) are installed on your VMware virtual platform. If you ordered add-on services, the deployment of the services starts after your order is completed.
* When the instance is ready to use, the status of the instance is changed to **Ready to use** and you receive a notification by email.
* When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.

Next, you can view and manage the vCenter Server instance that you ordered.

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the VMware Solutions console, not the {{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the VMware Solutions console, the changes are not synchronized with the console.
{: important}

**CAUTION** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance) from outside the VMware Solutions console can make your environment unstable. The following activities are considered management activities:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

   Exceptions to these activities include managing the shared storage file shares from the {{site.data.keyword.slportal}}. Such activities include ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

## Related links
{: #vc_orderinginstance-related}

* [Signing up for an {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-signing_required_accounts#signing_required_accounts-cloud)
* [Adding clusters to vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingclusters)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservers)
