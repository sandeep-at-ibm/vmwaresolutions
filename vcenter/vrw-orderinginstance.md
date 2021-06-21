---

copyright:

  years:  2020, 2021

lastupdated: "2021-06-11"

keywords: regulated workloads order instance, order regulated workloads, regulated workloads instances

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering VMware Regulated Workloads
{: #vrw-orderinginstance}

The VMware® Regulated Workloads offering includes a secure-by-default architecture that follows the IBM unique policy controls framework. It provides continuous compliance monitoring and the highest level of data encryption (FIPS 140-2 Level 4).

## Requirements for VMware Regulated Workloads
{: #vrw-orderinginstance-req}

Ensure that you complete the following tasks:
* If you are ordering an instance for the first time, complete the tasks in the **Before you begin** section on the ordering page. For more information, see [Setting up your environment for your first order](/docs/vmwaresolutions?topic=vmwaresolutions-completing_checklist).
* Review the information in [Requirements for the {{site.data.keyword.cloud}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).
* Review the information in [VMware Regulated Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-overview).
* Review the instance and domain name format. The domain name is used to generate the username and server names of the instance.

| Name        | Value format |
|:------------|:------------ |
| Domain name | `<root_domain>` (Microsoft® Active Directory™ domain name) |  
| vCenter Server login username | `<user_id>@<root_domain>` (Microsoft® Active Directory user) or `administrator@vsphere.local` |
| vCenter Server (with embedded PSC) FQDN | `<instance_name>-vc.<root_domain>`. The maximum length is 50 characters. |
| Single Sign-On (SSO) site name | `<root_domain>` |
| Fully qualified ESXi server name | `<host_prefix><n>.<root_domain>`, where `n` is the sequence of the VMware vSphere® ESXi™ server. The maximum length is 50 characters. |
{: caption="Table 1. Value format for instance and domain names" caption-side="top"}

After the instance is provisioned, do not modify any value that is set during instance order. Otherwise, the instance might become unusable.
{:important}

## Deployment topology
{: #vrw-orderinginstance-topology}

The following topology options are provided:
* **Single-zone VMware instance** - this option deploys your vCenter Server in a single-zone data center.
* **Multizone VMware instance** - this option deploys your vCenter Server across three availability zones in an {{site.data.keyword.cloud}} multizone region if a single-zone data center failure occurs.

## Service prerequisites
{: #vrw-orderinginstance-serv-prereq}

The following services are required for VMware Regulated Workloads:
* [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* [KMIP for VMware](https://cloud.ibm.com/infrastructure/vmware-solutions/console/servicestandalonenew/KMIPAdapter)
* [Direct Link Dedicated](https://cloud.ibm.com/interconnectivity/direct-link)

## Licensing
{: #vrw-orderinginstance-licensing}

Specify the licensing options for the following VMware components in the instance:
* VMware vCenter Server® Standard 7.0
* VMware vSphere® Enterprise Plus 7.0
* VMware NSX-T™ 3.1 Enterprise edition
* (Multizone VMware instance only) VMware vSAN™ Enterprise license

For Business Partner users, all licenses are included and purchased on your behalf. For users who are not Business Partners, you can use the IBM-provided VMware licenses for these components by selecting **Include with purchase**. You can also Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license keys.

### Licensing notes
{: #vrw-orderinginstance-licensing-notes}

* The minimum number of licenses for BYOL that are required depends on the number of CPUs per server and the number of servers in the order.
* The minimum license editions are indicated on the user interface. You are responsible to ensure that the license key provided is correct for each VMware component selected.
* For vSphere, a license charge is incurred at the time of order, but the license charge is then credited to your account.
* You can change any licenses that you provided by using the VMware vSphere Web Client after the instance deployment is completed.
* Support for the VMware components that you provide licenses is provided by VMware, not by IBM Support.

## Location
{: #vrw-orderinginstance-mgmt-dc-location}

* For single-zone VMware instances, select the {{site.data.keyword.cloud_notm}} data center where the clusters are hosted.
* For multizone VMware instances, select the multizone region and the stretched and witness clusters locations.

## Witness cluster (multizone VMware instance only)
{: #vrw-orderinginstance-witness-cluster}

The witness cluster name is set to **mcv-_xx_-witness** by default, where _xx_ represents two randomly generated alphabetic characters. You can also specify a new witness cluster name, which must meet the following requirements.

### Witness cluster name requirements
{: #vrw-orderinginstance-witness-cluster-req}

* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The witness cluster name must start with a lowercase alphabetic character.
* The witness cluster name must end with a lowercase alphabetic or numeric character.
* The maximum length of the witness cluster name is 30 characters.
* The witness cluster name must be unique within the regulated workload instance.

### CPU model and RAM
{: #vrw-orderinginstance-witness-cluster-compute}

You can choose the following CPU models and a supported RAM size:

| CPU model | RAM |
|:--------- |:--- |
| Dual Intel® Xeon® Silver 4210 (Cascade Lake) / 20 cores total, 2.2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 5218 (Cascade Lake) / 32 cores total, 2.3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Gold 6248 (Cascade Lake) / 40 cores total, 2.5 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Dual Intel Xeon Platinum 8260 (Cascade Lake) / 48 cores total, 2.4 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB |
| Quad Intel Xeon Gold 6248 (Cascade Lake) / 80 cores total, 2.5 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
| Quad Intel Xeon Platinum 8260 (Cascade Lake) / 96 cores total, 2.4 GHz | 384 GB, 768 GB, 1.5 TB, 3 TB |
{: caption="Table 2. Options for Cascade Lake bare metal servers" caption-side="top"}

### Number of bare metal servers
{: #vrw-orderinginstance-witness-cluster-bare-metal}

You can order 3 - 30 servers. All servers have the same configuration.

### vSAN configuration
{: #vrw-orderinginstance-witness-cluster-vsan}

Specify the following settings for vSAN configuration.

#### Disk type and size for vSAN capacity disks
{: #vrw-orderinginstance-witness-cluster-vsan-disktype}

Select an option for the capacity disks that you need.

#### Number of vSAN capacity disks
{: #vrw-orderinginstance-witness-cluster-vsan-diskcount}

Specify the number of capacity disks that you want to add.

### Estimated resources available per cluster
{: #vrw-orderinginstance-witness-cluster-est}

Review the estimated resources available per cluster.

### Networking type
{: #vrw-orderinginstance-witness-cluster-net}

The networking type is set to **Private network only**.

### Uplink speed
{: #vrw-orderinginstance-witness-uplink}

The uplink speed provides two options:
* 10 Gb, which is selected by default.
* 25 Gb, which is available only for specific locations.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:-------------------------------------------- |:------ |
| Dallas 10 <br>Dallas 12<br>Dallas 13 | NA South |
| Frankfurt 02 <br>Frankfurt 05 <br>London 04 <br>London 06 <br>Paris 04 <br>Paris 05 <br>Paris 06 | Europe |
| Sydney 04 <br>Sydney 05 <br>Tokyo 02 <br>Tokyo 04 <br>Tokyo 05 | Asia-Pacific |
| Toronto 04 <br>Washington DC 04 <br>Washington DC 06 <br>Washington DC 07 | NA East |
{: caption="Table 3. Available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed" caption-side="top"}

## Management cluster
{: #vrw-orderinginstance-mgmt-cluster}

The management cluster name is set to **mcv-_xx_-management** by default. You can also specify a new management cluster name, which must meet the following requirements.

### Management cluster name requirements
{: #vrw-orderinginstance-cluster-name-req}

* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The management cluster name must start with a lowercase alphabetic character.
* The management cluster name must end with a lowercase alphabetic or numeric character.
* The maximum length of the management cluster name is 30 characters.
* The management cluster name must be unique within the regulated workload instance.

### Management capacity
{: #vrw-orderinginstance-mngt-capacity}

* For the **Small** capacity, you get a Cascade Lake server with 20 cores, 2.2 GHz, and 192 GB RAM (single-zone VMware instance) or 384 GB RAM (multizone VMware instance).
* For the **Customizable** capacity, you can choose the Cascade Lake server and RAM size according to your needs.

### Number of bare metal servers (single-zone VMware instance only)
{: #vrw-orderinginstance-mgmt-bare-metal}

You can order 4 - 20 servers. All servers have the same configuration.

### Hosts per site (multizone VMware instance only)
{: #vrw-orderinginstance-mngt-hosts}

Choose the number of management hosts to be deployed in two availability zones. The hosts are deployed and scaled in pairs (one per site) to ensure appropriate failover capacity.

### vSAN configuration
{: #vrw-orderinginstance-mgmt-vsan}

* For the **Small** capacity, you get two vSAN™ capacity disks 1.9 TB SSD SED.
* For the **Customizable** capacity, you can choose the type and number of capacity disks according to your needs.
* For single-zone VMware instance only, you can use the IBM-provided VMware license for vSAN by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

### Estimated resources available per cluster
{: #vrw-orderinginstance-mgmt-est}

Review the estimated resources available per cluster.

### Networking type
{: #vrw-orderinginstance-mgmt-net-type}

The networking type is set to **Private network only** by default.

### Uplink speed
{: #vrw-orderinginstance-mgmt-uplink}

The uplink speed provides two options:
* 10 Gb, which is selected by default.
* 25 Gb, which is available only for specific locations.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:-------------------------------------------- |:------ |
| Dallas 10 <br>Dallas 12<br>Dallas 13 | NA South |
| Frankfurt 02 <br>Frankfurt 05 <br>London 04 <br>London 06 <br>Paris 04 <br>Paris 05 <br>Paris 06 | Europe |
| Sydney 04 <br>Sydney 05 <br>Tokyo 02 <br>Tokyo 04 <br>Tokyo 05 | Asia-Pacific |
| Toronto 04 <br>Washington DC 04 <br>Washington DC 06 <br>Washington DC 07 | NA East |
{: caption="Table 4. Available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed" caption-side="top"}

## Workload cluster
{: #vrw-orderinginstance-wkld-cluster}

By default, the workload cluster name is set to **mcv-_xx_-workload**. You can also specify a new name for the workload cluster. The cluster name must meet the requirements that are listed in [Cluster name requirements](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-orderinginstance#vrw-orderinginstance-cluster-name-req).

### Workload capacity
{: #vrw-orderinginstance-wkld-capacity}

* For the **Customizable** capacity, you can choose the Cascade Lake server and RAM size according to your needs.
* For the **Medium** capacity, you get a Cascade Lake server with 32 cores, 2.3 GHz, and 384 GB RAM.
* For the **Large** capacity, you get a Cascade Lake server with 48 cores, 2.4 GHz, and 768 GB RAM.

### Number of bare metal servers (Single-zone VMware instance only)
{: #vrw-orderinginstance-wkld-bare-metal}

You can order 4 - 20 servers. All servers have the same configuration.

### Hosts per site (Multizone VMware instance only)
{: #vrw-orderinginstance-wkld-hosts}

Choose the number of vSAN stretched cluster resource hosts to be deployed in two availability zones. The hosts must be deployed and scaled in pairs (one per site).

### vSAN configuration
{: #vrw-orderinginstance-wkld-vsan}

* You can choose the type and number of capacity disks according to your needs.
* For single-zone VMware instance only, You can use the IBM-provided VMware license for vSAN by selecting **Include with purchase**, or Bring Your Own License (BYOL) by selecting **I will provide** and entering your own license key.

### Estimated resources available per cluster
{: #vrw-orderinginstance-wkld-est}

Review the estimated resources available per cluster.

### Networking
{: #vrw-orderinginstance-wkld-net}

Specify the networking type and uplink speed.

#### Networking type
{: #vrw-orderinginstance-wkld-net-type}

The networking type is set to **Private network only** by default.

### Uplink speed
{: #vrw-orderinginstance-wkld-uplink}

The uplink speed provides two options:
* 10 Gb, which is selected by default.
* 25 Gb, which is available only for specific locations.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:-------------------------------------------- |:------ |
| Dallas 10 <br>Dallas 12<br>Dallas 13 | NA South |
| Frankfurt 02 <br>Frankfurt 05 <br>London 04 <br>London 06 <br>Paris 04 <br>Paris 05 <br>Paris 06 | Europe |
| Sydney 04 <br>Sydney 05 <br>Tokyo 02 <br>Tokyo 04 <br>Tokyo 05 | Asia-Pacific |
| Toronto 04 <br>Washington DC 04 <br>Washington DC 06 <br>Washington DC 07 | NA East |
{: caption="Table 5. Available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed" caption-side="top"}

## Firewall appliance
{: #vrw-orderinginstance-firewall-appl}

You have the following options for your firewall appliance:
* **Edge services cluster with Juniper vSRX** - Order a dedicated cluster for the network edge and firewall components and install Juniper® vSRX on it.
* **Edge services cluster with FortiGate Virtual Appliance** (single-zone VMware instance only) - Order a dedicated cluster for the network edge and firewall components and install FortiGate Virtual Appliance on it.
* **Bring your own gateway appliance** - Order a dedicated cluster for the network edge and firewall components.
* **FortiGate Security Appliance** - Use an {{site.data.keyword.cloud_notm}} service, which is an enterprise-class hardware firewall for enhanced and granular control over your network.

The steps that you must follow differ depending on your selection.

## Edge services cluster
{: #vrw-orderinginstance-edge}

The **Edge services cluster** section is available for all firewall appliances except for **FortiGate Security Appliance**.

### Edge services cluster name (multizone VMware instance only)
{: #vrw-orderinginstance-edge-cluster-name}

By default, the edge services cluster name is set to **mcv-_xx_-edge**. You can also specify a new name for the edge services cluster. The edge services cluster name must meet the requirements that are listed in [Cluster name requirements](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-orderinginstance#vrw-orderinginstance-cluster-name-req).

### Data center location (multizone VMware instance only)
{: #vrw-orderinginstance-edge-dc}

The edge services clusters are colocated with the witness and consolidated clusters.

### Compute capacity
{: #vrw-orderinginstance-edge-compute}

For compute capacity, you get a Cascade Lake server with 20 cores, 2.2 GHz, and you also get two cluster hosts and 2 * 3.8 TB SSD SED storage.

### RAM
{: #vrw-orderinginstance-edge-ram}

You can select a RAM size from 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, and 1.5 TB.

### Networking type
{: #vrw-orderinginstance-edge-net}

Select either **Public and private network** or **Private network only** for the edge services cluster.

### Uplink speed
{: #vrw-orderinginstance-edge-uplink}

The uplink speed provides two options:
* 10 Gb, which is selected by default.
* 25 Gb, which is available only for specific locations.

| {{site.data.keyword.cloud_notm}} data center | Region |
|:-------------------------------------------- |:------ |
| Dallas 10 <br>Dallas 12<br>Dallas 13 | NA South |
| Frankfurt 02 <br>Frankfurt 05 <br>London 04 <br>London 06 <br>Paris 04 <br>Paris 05 <br>Paris 06 | Europe |
| Sydney 04 <br>Sydney 05 <br>Tokyo 02 <br>Tokyo 04 <br>Tokyo 05 | Asia-Pacific |
| Toronto 04 <br>Washington DC 04 <br>Washington DC 06 <br>Washington DC 07 | NA East |
{: caption="Table 6. Available {{site.data.keyword.cloud_notm}} data centers for 25 Gb uplink speed" caption-side="top"}

## Network interface
{: #vrw-orderinginstance-network-interface}

The hostname prefix must meet the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The hostname prefix must start with a lowercase alphabetic character.
* The hostname prefix must end with a lowercase alphabetic or numeric character.
* The maximum length of the hostname prefix is 10 characters.

The hostname prefix applies to all hosts in the instance.
{:note}

The domain name must meet the following requirements:
* The domain name must consist of three or more strings that are separated by a period (.) with a maximum of 50 characters.
* The first string must start with a lowercase alphabetic character.
* The first string must end with a lowercase alphabetic or numeric character.
* All strings, except for the last one, can contain only lowercase alphabetic, numeric, and dash (-) characters.
* The last string can contain only lowercase alphabetic characters.
* The length of the last string must be in the range 2 - 24 characters.

The maximum length of the Fully Qualified Domain Name (FQDN) for hosts and VMs is 50 characters. Domain names must accommodate for this maximum length.
{:note}

### DNS configuration
{: #vrw-orderinginstance-dns-config}

The only deployment type that is supported is **Two highly available dedicated Windows server VMs on the management cluster**, which helps enhance security and robustness.

You must provide two Microsoft® Windows® Server 2019 Standard edition licenses to use the two Microsoft Windows VMs.
{:important}

Each license can be assigned only to one single physical server and covers up to two physical processors. One Standard edition license can run two virtualized Microsoft Windows VMs per two-processor server. Therefore, two licenses are required since two Microsoft Windows VMs are deployed in two different hosts.

You have 30 days to activate the VMs.

For more information about ordering Windows Server 2019 licenses, see [Get started with Windows Server 2019](https://docs.microsoft.com/en-us/windows-server/get-started-19/get-started-19){:external}.

## Resource details
{: #vrw-orderinginstance-resource-details}

Enter the instance name or accept the default value and specify the resource group for the VMware Regulated Workloads instance.

### Instance name
{: #vrw-orderinginstance-inst-name}

The instance name is set to **vrw-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify an instance name that meets the following requirements:
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The instance name must start with a lowercase alphabetic character.
* The instance name must end with a lowercase alphabetic or numeric character.
* The maximum length of the instance name is 10 characters.
* The instance name must be unique within your account.

### Resource group
{: #vrw-orderinginstance-resource-group}

Use resource groups to organize the resources in your account for access control and billing purposes. The default resource group in your account is selected by default. You can also select another resource group according to your needs. The resource group that you select cannot be changed after the instance is created.

If **No resource group available** is displayed in this field, you currently do not have the permission to add the instance to any resource group in this account. Contact the account owner to be assigned an Editor or Administrator role on a resource group in the account. For more information, see [IAM access](/docs/account?topic=account-userroles).
{:note}

## Included services
{: #vrw-orderinginstance-included-services}

The following services are included with your regulated workload instance. Some of the included add-on services require configuration setup.
* [Veeam 11](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview) (if you're using **Edge services cluster with Juniper vSRX** as your firewall appliance)
* [FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations) (if you're using **Edge services cluster with FortiGate Virtual Appliance** as your firewall appliance)
* [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview)

## Optional service (single-zone VMware instance only)
{: #vrw-orderinginstance-optional-services}

You can choose to install [VMware HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations).

## Procedure to order VMware Regulated Workloads
{: #vrw-orderinginstance-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click the **VMware Regulated Workloads** card.
2. On the **VMware Regulated Workloads** page, select a deployment topology according to your needs.
3. Review the service prerequisites and confirm that you ordered the mandatory services listed.
4. Under **Licensing**, complete the license settings for the listed components.
   * To use IBM-provided licenses, ensure that the option **Include with purchase** is selected.
   * To use your own licenses, click **I will provide** and enter the license key.
5. Select the {{site.data.keyword.cloud_notm}} data center to host the clusters for single-zone VMware instances, or select the multizone region and the stretched and witness locations for multizone VMware instances.

6. (Multizone VMware instance only) Specify the witness cluster settings.
   1. Specify the witness cluster name.
   2. Select the CPU model, RAM size, and the number of bare metal servers.
   3. Under **vSAN configuration**, select the disk type and size for the vSAN capacity disks and the number of vSAN capacity disks.
   4. Review the estimated resources available per cluster.
   5. Review the networking configuration.
   6. Select the uplink speed. The 25 Gb option is available for specific data centers only.

7. Specify the management cluster settings.
   1. Specify the management cluster name.
   2. Indicate the management capacity.
      * For the **Small** capacity and for single-zone instances, specify the number of bare metal servers.
      * For the **Customizable** capacity and for single-zone instances, select the Cascade Lake server, specify the RAM size, and the number of bare metal servers.
      * For both the **Small** or **Customizable** capacity and for multizone VMware instances, select the hosts per site.
   3. Select the disk type and size for the vSAN capacity disks, the number of vSAN capacity disks, and complete the vSAN license configuration. The available options depend on your deployment topology and capacity configurations. For small capacity instances, disk type and size for the vSAN capacity disks and the number of vSAN capacity disks are predefined.
   4. Review the estimated resources available per cluster.
   5. Review the networking configuration.
   6. Select the uplink speed. The 25 Gb option is available for specific data centers only.

8. Specify the workload cluster settings.
   1. Specify the workload cluster name.
   2. Indicate the workload capacity, either **Customizable**, **Medium**, or **Large**.
      * For the **Customizable** capacity, select the Cascade Lake server, specify the RAM size, and the number of bare metal servers.
      * For the **Medium** or **Large** capacity, specify the number of bare metal servers.
   3. Select the disk type and size for the vSAN capacity disks, the number of vSAN capacity disks, and complete the vSAN license configuration. vSAN license configuration is not available for multizone VMware instances.
   4. Review the estimated resources available per cluster.
   5. Review the networking configuration.
   6. Select the uplink speed.

9. Choose the firewall appliance for your instance and follow the steps, depending on your selection:
   1. For **Edge services cluster with Juniper vSRX**, **Edge services cluster with FortiGate Virtual Appliance**, and **Bring your own gateway appliance**, specify the edge services [cluster name](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-orderinginstance#vrw-orderinginstance-cluster-name-req), the CPU model, the RAM size, the uplink speed, and the networking type.
   2. For **Edge services cluster with Juniper vSRX** and **Edge services cluster with FortiGate Virtual Appliance**, you must also specify the corresponding service settings in a later step.
   3. For **FortiGate Security Appliance**, you must order the **FortiGate Security Appliance 10 Gbps** service from the [IBM Cloud catalog](https://cloud.ibm.com/catalog/infrastructure/fortigate-security-appliance-10gb). Confirm that you ordered the service and continue with the following steps.

10. Under **Network interface**, enter the hostname prefix for the regulated workload and the root domain name.
11. Under **Resource details**, enter the instance name and select a resource group.
12. Under **Included services**, review the add-on services to be deployed into the instance. If a service requires configuration, complete the service-specific settings by clicking **Edit** on the service card. Then, complete your edits and click **Save**. For more information about specific settings for a service, see the corresponding topic for ordering the service.
13. (Single-zone VMware instance only) Under **Optional services**, if you want to deploy VMware HCX, toggle the switch on and review the service settings. If configuration is required, click **Edit**, then complete the edits and click **Save**. For more information, see [VMware HCX configuration](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_ordering#hcx_ordering-config).
14. On the **Summary** pane, review the regulate workload instance settings and the estimated price.
15. To place the order, ensure that the account to be charged is correct, review and accept the terms, and then click **Create**.

### Results after you place an order
{: #vrw-orderinginstance-results-order}

1. The deployment of the regulated workload instance starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Deployment history** section of the instance details.
2. When the instance is successfully deployed, the ordered components are installed on your VMware virtual platform. The deployment of the services starts after your order is completed. When the instance is ready to use, the status of the instance is changed to **Ready to use** and you receive a notification by email.

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the VMware Solutions console, not the {{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the VMware Solutions console, the changes are not synchronized with the console.
{:important}

**CAUTION** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account when you ordered the instance) from outside the VMware Solutions console can make your environment unstable. The following activities are considered management activities:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

#### Known issue for multizone deployment
{: #vrw-orderinginstance-results-order-issue}

Some public networking components might be displayed as inactive in vCenter Server. These components do not indicate a problem and you can either ignore the issue or delete the components.

## Related links
{: #vrw-orderinginstance-related}

* [VMware Regulated Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-overview)
* [Signing up for an {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-signing_required_accounts#signing_required_accounts-cloud)
* [Requirements and planning for VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-planning)
* [Viewing and deleting VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-view-delete-instance)
* [VMware Regulated Workloads reference architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-archi-overview)
