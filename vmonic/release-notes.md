---

copyright:
  years: 2019, 2021
lastupdated: "2021-11-11"

keywords: release notes, what's new in VMware Solutions, what is new, new features, VMware Solutions release notes, VMware Solutions

subcollection: vmwaresolutions

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for VMware Solutions
{: #vmwaresolutions-relnotes}

Use these release notes to learn about the latest updates to {{site.data.keyword.vmwaresolutions_full}}, including new features, component updates, usability enhancements, and bug fixes.
{: shortdesc}

Various other updates are made to the [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) and the [VMware Solutions Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared) documentation.
{: tip}

## 2021
{: #year-2021}

### 13 October 2021
{: #october-2021}
{: release-note}

End of Support for instance deployments with vSphere 6.5
:   {{site.data.keyword.cloud_notm}} support for ordering all update levels of VMware vSphere 6.5 ended on 10 October 2021.

   Beginning on this date, you can no longer order new VMware vCenter Server instances with vSphere 6.5 and your existing vCenter Server instances with vSphere 6.5 become read–only in the VMware Solutions console and through the public REST API.

   Until you upgrade to vSphere 6.7 or later, you cannot perform operations such as:

   * Adding and deleting clusters
   * Adding and removing ESXi servers
   * Adding and removing storage
   * Adding and deleting services

   You can still view and delete your existing instances with vSphere 6.5.

   {{site.data.keyword.cloud_notm}} will continue to support your infrastructure on our cloud and will continue to support the vSphere 6.5 software until the [VMware announced end of support date](https://lifecycle.vmware.com/#/){: external} of 15 October 2022.

   vSphere 6.5 is superseded by vSphere 6.7 and vSphere 7.0. If you have active workloads on vSphere 6.5, consider upgrading or migrating to vSphere 6.7 or vSphere 7.0 today. The documentation provides instructions and considerations for upgrading to vSphere 6.7 and vSphere 7.0.

   {{site.data.keyword.cloud_notm}} recommends you move to vSphere 7.0, the latest VMware vSphere version, which is the focus of feature investment for both VMware and {{site.data.keyword.cloud_notm}}. Furthermore, {{site.data.keyword.cloud_notm}} recommends that you migrate rather than upgrade to vSphere 7.0. Migration ensures that you are aligned with current and supported hardware, other {{site.data.keyword.cloud_notm}} features, and the recommended vSphere 7 NSX–T topology, including the use of VDS switches.

   Before you upgrade, IBM recommends that you assess your environments for infrastructure and workload dependencies to ensure that they are supported for the current version.

   vSphere 6.7 introduces support for embedded Platform Services Controller (PSC), improved support for the HTML5 client including vSAN management, support for Intel Skylake EVC level, support for virtual TPM, improved support for VMware Update Manager (VUM), and vSAN support for Windows Failover Clustering.

   vSphere 7.0 introduces full support for the HTML5 client, support for Intel Cascade Lake EVC level, the enhanced vSphere Lifecycle Manager (LCM), enhancements to DRS and vMotion, security enhancements including multi–factor authentication (MFA), vSphere Trust Authority (vTA), and in–flight encryption for vSAN. vSphere 7.0 is also the exclusive basis for VMware Regulated Workloads.

   For more information about end of life procedures for {{site.data.keyword.cloud_notm}} infrastructure services and Third–Party software products, see [Lifecycle policy for IBM Cloud products](https://www.ibm.com/cloud/cloud-prod-life). If you have any questions or need assistance, email clouddigitalsales@us.ibm.com or open a support ticket in the VMware Solutions console.

 VMware vCenter Server instances
:   The 4.4 release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts.

   * VMware vCenter Server Appliance
      * 7.0 Update 2d (build 18455184)
      * 6.7 Update 3o (build 18485166)
   * VMware NSX-T 3.1.1.0.0 (build 17483185)

Add-on services
:   The 4.4 release provides the following service versions on newly deployed instances.

   * F5 BIG-IP v16.1
   * FortiGate Virtual Appliance v7.0.1
   * HyTrust CloudControl v6.4.1
   * Red Hat OpenShift v4.7.24
   * Zerto v9.0u1

FortiGate Virtual Appliance for multizone instances on VMware Regulated Workloads
:   For VMware Regulated Workloads, you can deploy FortiGate Virtual Appliance on edge services clusters for multizone instances. You can deploy FortiGate Virtual Appliance when you first order the instance or as part of day 2 operations.

Veeam deployment type displayed on services detail page
:   The deployment type for Veeam is displayed on the service details page. The possible deployment types are VM, VSI, or Bare metal.

Zerto licenses availability
:   You can now order Zerto license without associating it to any vCenter Server instance. When you submit your order, IBM Support requests a license key from Zerto that is then delivered to the email address that is associated with your order.

   You can use the {{site.data.keyword.vmwaresolutions_short}} console to view license details and delete the license.

REST APIs
:   As a result of End of Support for instance deployments with vSphere 6.5, REST APIs for the following tasks for instances with vSphere 6.5 are no longer provided:

   * Adding and deleting clusters
   * Adding and removing ESXi servers
   * Adding and removing storage
   * Adding and deleting services

### 9 August 2021
{: #August-2021}
{: release-note}

VMware vSphere 7.0 Update 2a support
:   The 4.3 release provides VMware vSphere 7.0 Update 2a for newly deployed instances. For existing vSphere 7.0u1 instances and clusters, you can either add a 7.0u1 or 7.0u2 host or cluster.

New disk type for VMware vSAN
:   For the VMware vSAN component, the 7.68 TB SSD SED capacity disk is now available for {{site.data.keyword.cloud_notm}} bare metal servers for newly deployed instances and when you add hosts and clusters to existing instances. The 7.68 TB SSD SED disk type is supported for only VMware vSphere 7.0 or 6.7 instances with 25 Gb uplink speed.

VMware Solutions Shared - Windows pricing metrics
:   (Updated on 1 October 2021) The Microsoft Windows pricing metric is now hourly for VMware Solutions Shared instances.

VMware vCenter Server instances
:   The 4.3 release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts.

   * VMware vSphere ESXi
      * 7.0 Update 2a (build 17867351)
      * 6.7 P05 (build 17700523)
      * 6.5 P06 (build 17477841)
   * VMware vCenter Server Appliance
      * 7.0 Update 2b (build 17958471/17958471)
      * 6.7 Update 3n (build 18010531/18010599)
   * VMware NSX-T 3.1.0.0.0 (build 17107167)
   * VMware NSX-V 6.4.10 (build 17626462)
   * VMware vSAN 7.0 Update 2 (build 17630552) or 6.7 P05

vCenter Server multizone instances - deprecated
:   New deployments of vCenter Server multizone instances are no longer supported.
   {: deprecated}

   You can still add and delete clusters, add and remove ESXi servers, and add and delete storage for existing multizone instances.

VMware Regulated Workloads - support for consolidated cluster
:   Rather than requiring that the VMware Regulated Workloads solution deploys a separate management cluster and separate clusters for workloads, now you can start with a smaller footprint by selecting the **Customize a consolidated cluster** option, which deploys a consolidated management and workload cluster.

   The **Customize a consolidated cluster** option is available in single-zone deployments (non-stretched) and brings down the entry price point by enabling workloads to run alongside VMware management components in the same cluster. The minimum number of hosts required to start is reduced from 10 to 6. This option is helpful for proof of concepts (POCs) and for clients who want to start small and grow over time.

   If you do not want workloads to run on the primary cluster, you can select **Management optimized cluster** and order a 2-CPU Intel Cascade Lake chipset with 20 cores total and 192 GB of RAM per bare metal server. Under **Additional cluster for workloads**, you must select the checkbox to include a separate secondary cluster for workloads and then customize the bare metal hardware based on your workload capacity requirements.

   The VMware HCX service is available only if you also include a workload cluster in your instance.
   {: note}

VMware Regulated Workloads - support for save configuration
:   A new **Save configuration** button is added to the **Summary** pane of the ordering page for VMware Regulated Workloads. Use this option to save your instance settings as a configuration template without placing an order. You can manage the configuration templates by further editing or deleting them as well.

Security and Compliance Readiness Bundle
:   A new **Save configuration** button is added to the **Summary** pane of the ordering page for Security and Compliance Readiness Bundle instances. Use this option to save your instance settings as a configuration template without placing an order. You can manage the configuration templates by further editing or deleting them as well.

Add-on services
:   The 4.3 release provides the following service versions on newly deployed instances.

   * Caveonix RiskForesight v3.0.1
   * FortiGate Virtual Appliance v6.4.6
   * Juniper vSRX v20.4 (R2)
   * Red Hat OpenShift v4.7

FortiGate Virtual Appliance
:   FortiGate Virtual Appliance adds the following features.
   * 25 Gb uplink speed on vSphere 7 and NSX-T
   * High-performance deployment size of Fortigate-VM32

   The uplink speed and deployment size require Cascade Lake 5218 or higher.

Juniper vSRX
:   You can install Juniper vSRX on 25 Gb uplink speed consolidated and edge services clusters on vSphere 7 with NSX-T. On 25 Gb uplink speed clusters, only the Content Security Bundle license is available.

REST APIs
:   REST API support for vCenter Server multizone instances is no longer provided as a result of feature deprecation in the 4.3 release.

### 21 June 2021
{: #june-2021}
{: release-note}

VMware Solutions Shared - Veeam Backup and Replication V11
:   The 4.2 release provides VMware Solutions Shared instances with Veeam Backup and Replication V11 for the Veeam Cloud Connect Replication ready-to-use service.

   For more information about the compatibility requirements between Veeam service providers and tenants, see [Product versions in Veeam Cloud Connect infrastructure](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_versions.html?ver=110){: external}.

VMware Solutions Shared - Network High Availability through data center groups
:   VMware Solutions Shared now provides Network High Availability, a VMware vCloud Director feature that allows a vCloud Director network to be anchored in two data centers. This feature enables the network to be resilient and to withstand an outage in any of the two data centers.

VMware vCenter Server instances
:   The 4.2 release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts.

   * VMware vSphere ESXi
      * 7.0 Update 1d (build 17551050)
      * 6.7 P05 (build 17700523)
      * 6.5 P06 (build 17477841)
   * VMware vCenter Server Appliance
      * 7.0 Update 2b (build 17958471)
      * 6.7 Update 3n (build 18010531)
   * VMware NSX-T 3.1.0.0.0 (build 17107167)
   * VMware NSX-V 6.4.10 (build 17626462)
   * VMware vSAN 7.0 Update 1d (build 17551050) or 6.7 P05
   * VMware vSAN Witness 7.0 Update 1d (build 17551050)[^vsanwitness]

[^vsanwitness]: vCenter Server multizone instances only

NSX-T for vCenter Server instances with vSphere 6.7 - deprecated
:   NSX-T is no longer supported for new deployments of vCenter Server instances with vSphere 6.7. NSX-T is available only for vSphere 7. You can still view and manage your existing instances with vSphere 6.7 and NSX-T.
   {: deprecated}

VMware vCenter Server - 25 Gb uplink speed updates
:   Enhanced support is now provided for 25 Gb uplink speed for vCenter Server multizone instances.

   * When you order new vCenter Server multizone instances, 25 Gb is supported for the witness cluster, the consolidated or management cluster, and the workload cluster.
   * When you add clusters to vCenter Server multizone instances, 25 Gb is supported for the workload cluster.

VMware vCenter Server - NFS storage limitation for VMware multizone instances
:   The initial NFS storage that you order is used mainly for management. Its size must be at least 1,000 GB and the performance at least 2 IOPS/GB. Do not delete this storage. If you require extra storage, you can add it post-deployment. The size and performance of the NFS storage added post-deployment can have any of the available values.

VMware vCenter Server - NFS host orders
:   For locations where appropriate 1U servers are available, when you order hosts for clusters that use NFS storage, 1U servers are ordered silently rather than 2U servers. Clusters that use vSAN storage will continue to order 2U servers.

Regulated Workloads - 25 Gb Uplink speed
:   Enhanced support is now provided for 25 Gb uplink speed for VMware Regulated Workloads instances, both single-zone and multizone.

   * When you order new VMware Regulated Workloads instances, 25 Gb is supported for the management cluster and the workload cluster.
   * When you add clusters to VMware Regulated Workloads instances, 25 Gb is supported for the workload cluster.

Add-on services
:   The 4.2 release provides the following service versions on newly deployed instances.

   * Caveonix RiskForesight 3.0
   * F5 BIG-IP 15.1.3.1
   * HyTrust CloudControl 6.3.1
   * HyTrust DataControl 5.3[^htdc]
   * Juniper vSRX 3.0 (20.4R1.12)

[^htdc]: vSphere 6.7 for NSX-T and vSphere 6.7 and 6.5 for NSX-V

F5 BIG-IP
:   F5 BIG-IP is supported on vSphere 7 and NSX-T. This support is available on a management cluster.

FortiGate Virtual Appliance
:   Review the following information about FortiGate Virtual Appliance for the 4.2 release.

   * FortiGate Virtual Appliance is supported on VMware vSphere 7 and VMware NSX-T. This support is available on a management cluster and edge services cluster for single-zone instances only. Multizone support is not available.
   * For VMware Regulated Workloads instances and Security and Compliance Readiness Bundle instances, you can install FortiGate Virtual Appliance only on the edge services cluster.
   * The VM16 edition of FortiGate Virtual Appliance is available for all types of clusters. However, it is recommended that the 16 CPU license is used for high-bandwidth edge deployments only. For more information about any VM16 restrictions and Fortinet sizing, see [FortiGate-VM on VMware ESXi data sheet](https://www.fortinet.com/content/dam/fortinet/assets/data-sheets/FortiGate_VM_ESXi.pdf){: external}.
   * You can order multiple FortiGate Virtual Appliances on the management cluster. However, you can have only one pair on each edge services cluster.
   * You cannot install FortiGate Virtual Appliance and Juniper vSRX on the same edge services cluster.
   * After FortiGate Virtual Appliance v6.2.1, you are able to resize the RAM of FortiGate Virtual Appliance regardless of the licensing and pricing you currently have. You can make this change only if the CPU does not change. For more information, see [FortiGate-VM virtual licenses and resources](https://docs.fortinet.com/document/fortigate/6.2.0/vmware-esxi-cookbook/367417/fortigate-vm-virtual-licenses-and-resources){: external}.

HyTrust KeyControl - deprecated
:   New installations of HyTrust KeyControl are no longer supported for new or existing deployments of vCenter Server instances. You can still use or delete existing HyTrust KeyControl installations on your existing instances.
{: deprecated}

Juniper vSRX
:   Review the following information about Juniper vSRX for the 4.2 release:

   * Juniper vSRX is supported on vCenter Server multizone instances.
   * You cannot install Juniper vSRX and FortiGate Virtual Appliance on the same edge services cluster.

KMIP for VMware on {{site.data.keyword.cloud_notm}}
:   Two new endpoints are now available in the **Toronto** location for the KMIP for VMware service.

Veeam on vSphere 6.5 - deprecated
:   New installations of Veeam are no longer supported for new or existing deployments of vCenter Server instances with VMware vSphere 6.5. You can still use or delete existing Veeam installations on your existing vSphere 6.5 instances.
{: deprecated}

REST APIs
:   REST API support is now available for the F5 BIG-IP and FortiGate Virtual Appliance services and for adding edge services clusters to vCenter Server instances.

New and updated documentation
:   The following documentation updates are available.

   * Upgrading vCenter Server vSphere software from VMware vSphere 6.5 or 6.7 to 7.0 now includes important considerations and a section for updating licenses.
   * FAQ is updated to clarify how service license charges are being calculated.

### 5 April 2021
{: #april-2021}
{: release-note}

VMware Solutions Shared - support for Zerto
:   Starting with the 4.1 release, the Zerto service is available and ready-to-use to provide disaster recovery for critical workloads in your virtual data center instances. Additionally, you can order the Zerto Cloud Connector (ZCC) service after you deploy your virtual data center instance. Use ZCC to replicate your on-premises virtual data centers to {{site.data.keyword.cloud_notm}}.

   Charges are incurred only if you choose to use the services.

VMware Solutions Shared - network type options
:   The option to select a private only network or a public and private network is now available when you order VMware Solutions Shared instances.

VMware Solutions Dedicated - upgrade support for vSphere 7.0 instances
:   For VMware vCenter Server instances with VMware vSphere 6.5 or vSphere 6.7, in-place upgrade to vSphere 7.0 is now supported for select configurations. Not all hardware configurations are supported, and the upgrade cannot help you migrate from VMware NSX-V to NSX-T or from a non-converged NSX-T topology to a converged NSX-T topology.

   You must contact {{site.data.keyword.vmwaresolutions_short}} Support before and after you upgrade your instance.
{: important}

   {{site.data.keyword.cloud_notm}} supports only Cascade Lake bare metal servers for vSphere 7.0 instances. You must ensure that all VMware ESXi servers have the proper firmware and drivers to support 7.0.

   After you complete an upgrade to vSphere 7.0, you can add clusters and hosts to your upgraded instance. When you add a cluster or host to the upgraded instance, you must keep the original deployment configuration, naming, and network topology.

   The following upgrade scenarios are supported:
   * Adding NFS storage, hosts, and clusters (NFS or vSAN) on instances upgraded from vSphere 6.5 or 6.7
   * Adding hosts and clusters on upgraded NSX-V or non-converged NSX-T instances
   * Adding hosts in an upgraded NFS or vSAN cluster

   {{site.data.keyword.cloud_notm}} recommends that you deploy a new vSphere 7.0 instance and migrate your current network topology and workload to the new instance.
   {: note}

VMware Solutions Dedicated - SAP-certified servers support for vSphere 7
:   The following SAP-certified bare metal server models are now available for deployment with vSphere 7.0. These models are available for vCenter Server instances and clusters, and for VMware vSphere clusters.
   * Dual Intel Xeon Platinum 8280M (Cascade Lake, BI.S4.NW1500)
   * Dual Intel Xeon Platinum 8280M (Cascade Lake, BI.S4.NW3000)
   * Dual Intel Xeon Platinum 8280M (Cascade Lake)
   * Quad Intel Xeon Platinum 8280M (Cascade Lake)

VMware Solutions Dedicated - 25 uplink speed
:   Enhanced support is now provided for the 25 Gb uplink speed option for vCenter Server instances and clusters, and VMware vSphere clusters:
   * This option is now available for vSphere 7.0.
   * More data centers now support this option.

VMware Solutions Dedicated -  {{site.data.keyword.cloud_notm}} data centers
:   (Updated on 20 April 2021) The {{site.data.keyword.cloud_notm}} data centers **Sao Paulo 04** and **Sao Paulo 05** are now available for deployment.

VMware Solutions Dedicated - {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads
:   The following updates are available for vCenter Server multizone instances:

   * You can select to use IBM-provided or your own licenses for vCenter Server Standard and vSphere Enterprise Plus licenses.
   * You can specify an initial cluster name for your witness and consolidated clusters.
   * You can optionally order an additional workload cluster and an edge services cluster to new vCenter Server multizone instances.
   * You can add or remove the additional workload cluster or edge services cluster to existing vCenter Server multizone instances.
   * You can add or remove VMware ESXi servers to and from your additional workload cluster.
   * You can add or remove services to new or existing vCenter Server multizone instances.

VMware Solutions Dedicated - known issue for {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads
:   For Mission Critical Workloads, a known issue with vCenter HA failover exists. If eth0 is not active on the passive node before failover is initiated, the passive node is isolated and fails to take over as the active node. vCenter HA might not activate `eth0` when failover is initiated.
{: important}

VMware Regulated Workloads
:   (Updated on 4 May 2021) The VMware Regulated Workloads offering delivers a new multizone architecture to instances that are deployed in 4.1 and later releases. The multizone architecture can help to prevent downtime for cloud applications and to automate failovers within a cloud region.

Security and Compliance Readiness Bundle
:   The Security and Compliance Readiness Bundle is a prescriptive offering that provides many of the security and compliance features of {{site.data.keyword.cloud_notm}} for Financial Services at a lower entry price. The offering is packaged with security and compliance tools and templates for you to use with your preferred regulation standard.

Add-on services
:   The 4.1 release provides the following service versions on newly deployed instances.

   * BIG-IP VE v15.1.2
   * FortiGate Virtual Appliance 6.4.4
   * HyTrust CloudControl v6.3
   * Veeam v11

Services support for vCenter Server multizone instances
:   Starting with the 4.1 release, the following add-on services are supported on vCenter Server multizone instances.

   * Caveonix RiskForesight
   * HyTrust CloudControl
   * Veeam
   * vRealize Operations and Log Insight

Caveonix RiskForesight
:   Review the following information about Caveonix RiskForesight for the 4.1 release.

   * Caveonix RiskForesight is offered as a per-host license for new deployments of Caveonix on VMware Regulated Workloads and Security and Compliance Readiness Bundle instances. For vCenter Server deployments, Caveonix is still offered as license packs that are priced per virtual machine (VM).
   * A Caveonix RiskForesight license is valid for five years.
   * Deleting Caveonix RiskForesight deletes the initial Caveonix RiskForesight license that was associated with the service.

Veeam on bare metal server
:   You can install Veeam v11 on a bare metal server. This new feature is supported only for vSphere 7.0 with NSX-T.

REST APIs
:   The following API updates are available:

   * The VMware Solutions API provides support for the additional edge services cluster and workload cluster on multizone instances.
   * The VMware Solutions API provides support for the following services on multizone instances: Caveonix RiskForesight, HyTrust CloudControl, Veeam, and vRealize Operations and Log Insight.
   * The `network` option for selecting a private only network or a public and private network is available through the VMware Solutions Shared API.

### 29 January 2021
{: #january-2021}
{: release-note}

VMware Regulated Workloads
:   Starting with the 4.0 release, you can now order VMware Regulated Workloads directly from the VMware Solutions main page. The VMware Regulated Workloads include a secure-by-default architecture that follows IBM's unique policy controls framework, provides continuous compliance monitoring, and offers the highest level of data encryption (FIPS 140-2 Level 4). For VMware Regulated Workloads, only VMware vSphere 7.0 Update 1a is supported.

VMware Solutions Dedicated - VMware vSphere 7.0 Update 1a support
:   You can order vSphere 7.0 Update 1a with your VMware vCenter Server with NSX-T instances and VMware vSphere with NSX-T clusters. vSphere 7.0u1a introduces the following support and enhancements.

   * Smaller instance footprint with support for converged management and workload cluster. vSphere 6.7 and NSX-T require eight hosts when using vSAN storage and five hosts when using NFS storage. vSphere 7.0u1a enables a footprint of four hosts when using vSAN storage and three hosts when using NFS storage.
   * Full support for the HTML5 vSphere Web Client
   * Support for Intel Cascade Lake EVC level
   * The enhanced VMware vSphere Lifecycle Manager (LCM)
   * Enhancements to VMware vSphere Distributed Resource Scheduler (DRS) and VMware vSphere vMotion
   * Security enhancements that include multi–factor authentication (MFA) and vSphere Trust Authority (vTA)

   vSphere 7.0u1a is the exclusive basis for {{site.data.keyword.cloud}} for VMware Regulated Workloads and is available for Cascade Lake and SAP-certified bare metal servers only.

   vSphere 7.0u1a currently does not support 25 Gb uplink speed or High performance with Intel Optane for vSAN storage. Support for these features is planned for a future release. Additionally, vSphere 7.0u1a does not support single-node instances.
   {: note}

VMware Solutions Dedicated - vSAN storage for vSphere 7.0 Update 1a
:   A warning message might be displayed when you log in to vCenter Server through the vSphere Web Client. To remove the warning, download the latest version of the vSAN HCL DB file and update vCenter Server. For more information, see [Updating the vSAN HCL database manually (2145116)](https://kb.vmware.com/s/article/2145116){: external}.

VMware Solutions Dedicated - existing instances and vSphere 7.0 Update 1a
:  For vCenter Server instances with vSphere 6.5 or vSphere 6.7, in-place upgrade to vSphere 7.0 is not currently supported due to changes in VMware license keys and changes in the vCenter Server architecture and topology.
{: note}

   Carefully review the VMware product lifecycle matrix for ESXi and NSX as part of your planning. For more information, see [Product LifeCycle Matrix](https://lifecycle.vmware.com/){: external}.

   {{site.data.keyword.cloud_notm}} plans to publish guidance for upgrading your existing instance to vSphere 7.0 in a future VMware Solutions release. However, an upgrade cannot be supported for all hardware combinations, will not accomplish a migration from NSX-V to NSX-T, and will enable only limited VMware Solutions capabilities at the vSphere 7.0 level.

   Instead, {{site.data.keyword.cloud_notm}} recommends that you deploy a new vSphere 7.0 instance and migrate your current network topology and workload to the new instance.

   Migrating your workload to a new instance is especially recommended if you want to perform a hardware refresh, if you want to migrate from NSX–V to NSX–T, or if you want to migrate your existing NSX–T topology with separate management and workload clusters to a converged topology.

VMware Solutions Dedicated - support for VMware vSAN stretched clusters for vSphere 7.0 Update 1a and NSX-T 3.1
:   VMware vSphere Enterprise Plus 7.0 Update 1a and VMware NSX-T 3.1 are included when you order a VMware vCenter Server stretched cluster across a multizone region. The stretched cluster is deployed as a single consolidated cluster capable of hosting both management and workload clusters.

   With the combination of consolidated cluster and support for a 3-host RAID 1 configuration, you can deploy an instance with a minimum of eight hosts when you use NFS storage for your witness cluster, or nine hosts when you use vSAN storage for your witness cluster.

   Extra features for stretched clusters are planned for future releases, including support for VMware Regulated Workloads, edge services clusters, more workload clusters, and optional add-on services.
   {: note}

VMware Solutions Dedicated - updates for VMware NSX
:   Review the following information about vCenter Server with NSX-T instances for the 4.0 release.

   * New instances of vCenter Server with NSX-T are provisioned with NSX-T 3.1.
   * Day 2 operations continue to be supported for vCenter Server with NSX-T 2.5.1 instances with restrictions.
   * If you want to upgrade your existing vCenter Server with NSX-T instance, {{site.data.keyword.cloud_notm}} recommends that you upgrade directly to NSX-T 3.1 bypassing NSX-T 3.0.x.

VMware Solutions Dedicated - {{site.data.keyword.cloud_notm}} data centers
:   Review the following updates for {{site.data.keyword.cloud_notm}} data centers.

   * The new data centers **Toronto 04** and **Toronto 05** are available for deployment of vCenter Server instances and vSphere clusters.
   * The new region **Toronto** is available for deployment of VMware Mission Critical Workloads.
   * The data center **Oslo 01** is no longer available for new deployments.

Single-node offerings - deprecated
:   The Single-node for Migration and App Modernization and Single-node for Data Protection and Disaster Recovery offerings are no longer provided for new deployments. Full support remains for existing single-node instances.
   {: deprecated}

Add-on services
:  The 4.0 release provides the following service versions on newly deployed instances.

   * Caveonix RiskForesight v2.4
   * HyTrust CloudControl v6.2.1 for vCenter Server with NSX-T
   * Juniper vSRX and Juniper vSRX Gateway Appliance 3.0 (20.1R2)
   * Red Hat OpenShift v4.6
      * New installations of Red Hat OpenShift on vCenter Server require VMware vSphere 7.0 Update 1a with NSX-T 3.1. For NSX-T 2.5.1 deployments, you must upgrade to vSphere 7.0 Update 1a with NSX-T 3.1.
      * During deployment and day 2 operations, you are prompted for the cluster. You can install the service to the management cluster or any workload cluster.
   * Veeam v10a
   * vRealize Operations v8.2 and Log Insight v8.2

Add-on services that support VMware vSphere 7.0 Update 1a
:   The following add-on services support VMware vSphere 7.0 Update 1a.

   * Caveonix RiskForesight
   * VMware HCX
   * HyTrust CloudControl
   * Juniper vSRX
   * Red Hat OpenShift
   * Veeam
   * vRealize Operations

DNS entries removal
:   For several add-on services, if you installed the service before the {{site.data.keyword.vmwaresolutions_short}} 4.0 release and you then delete the service, you must remove the DNS entries manually.

Caveonix RiskForesight
:   RiskForesight v2.4 applies the following updates.

   * Updates the regulated workload presets to order 50 licenses, rather than 10.
   * Connects to NSX through FQDN, rather than to its IP address.

   When you order RiskForesight, you can now select 10 - 25,000 VMs to license, in increments of 10. The RiskForesight license is valid for five years.

Juniper vSRX
:   For vCenter Server instances, Juniper vSRX management and edge services cluster installations provide the following enhancements.

   * Useful address book entries
   * Security enhancements based on CIS guidelines
   * vSRX logging to vRealize Log Insight if the vRealize Operations add-on service is already installed

KMIP for VMware
:   Previously, KMIP for VMware provided a multi-tenant service that enables VMware vCenter Server to use IBM Key Protect for {{site.data.keyword.cloud_notm}} (Key Protect) and {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services (HPCS) as its key manager.

   Newly created KMIP for VMware instances that are connected to HPCS now operate as single-tenant services. These services run within the HPCS service and benefit from the features of IBM Secure Service Containers on IBM LinuxONE servers. You can connect only a single KMIP for VMware instance to each HPCS instance.

   KMIP for VMware continues to provide a multi-tenant service when you connect to Key Protect.

   In addition, two new endpoints are now available in the **Osaka** location for KMIP for VMware.

Red Hat OpenShift for VMware
:   Red Hat OpenShift for VMware is no longer supported for new deployments or for ordering post deployment for the following instances.

   * vCenter Server with NSX-V for vSphere 6.7 or 6.5
   * vCenter Server with NSX-T for vSphere 6.7 

   Existing installations of Red Hat OpenShift for VMware can be used or deleted.

VMware HCX
:   HCX is no longer supported for new deployments on vSphere 6.7 with NSX-T or for ordering post deployment on existing vSphere 6.7 instances with NSX-T.
   {: note}

   Review the following information about the VMware HCX service for the 4.0 release.

   * VMware HCX is now offered on vSphere 7.0 Update 1a for vCenter Server with NSX-T 3.1 instances. HCX is not supported on vSphere 6.7 for vCenter Server with NSX-T 3.1 instances.
   * The 12-month commitment for HCX is removed.
   * The private interconnect option is removed. The network connection options are either public or private.
   * You can choose the target cluster for service mesh (NSX-T only).
   * The HCX service is removed if the service mesh target cluster is removed on NSX-T.
   * If the management cluster or HCX service mesh target cluster is private only, the only connection type would be private connection. If the connection type is private, a proxy is required.

VMware vRealize Operations - vSAN storage requirements
:   If you install VMware vRealize Operations (vROps) and select vSAN storage, you must have an estimated 750 GB of vSAN storage to successfully install vROps. This storage requirement does not apply to NFS.

REST APIs
:   REST API support for the VMware HCX service is now available.

New and updated documentation
:   The following documentation updates are available.

   * (Updated on 24 February 2021) The Veeam on bare metal reference architecture document is now available in the **Reference** section of the user documentation.
   * A new topic, Managing security and compliance, is now available. The topic provides information about monitoring security and compliance posture with VMware Solutions by using Caveonix RiskForesight.

User interface updates and enhancements
:   The user interface is updated and provides the following enhancements.

   The following enhancements are made to the landing page of {{site.data.keyword.vmwaresolutions_short}} console to better assist you in learning and selecting the appropriate offering and services according to your needs:
   * The previous **Start provisioning** section is renamed to **IaaS platforms**.
   * A new **VMware Regulated Workloads** section is added.
   * The previous **Services** section is renamed to **Add-on services**.

## 2020
{: #year-2020}

### 26 October 2020
{: #october-2020}
{: release-note}

VMware Solutions Shared - support for Dallas 12 and Dallas 13 {{site.data.keyword.cloud_notm}} data centers
:   Starting with release 3.9, Dallas 12 and Dallas 13 {{site.data.keyword.cloud_notm}} data centers are now available for deployment on VMware Solutions Shared instances.

VMware Solutions Shared - Integration with {{site.data.keyword.cloud_notm}} Monitoring
:   You can now use {{site.data.keyword.cloud_notm}} Monitoring to view and customize dashboards to visualize performance, volume of usage, and to define alerts to monitor your environment.

VMware Solutions Dedicated - removed support for VMware vSphere 6.5u3
:   VMware vSphere 6.5u3 is no longer supported for new VMware vCenter Server instances. Full support remains for existing instances, including support to add new hosts and clusters.

   VMware vSphere 6.5u3 is no longer supported for new VMware vSphere clusters. Full support remains for existing clusters, including support to add new hosts.

VMware Solutions Dedicated - VMware NSX updates
:   Review the following information about vCenter Server with NSX-T instances.

   * New instances of vCenter Server with NSX-T are provisioned with NSX-T 3.0.1.1.
   * Day 2 operations continue to be supported for vCenter Server with NSX-T 2.5.1 instances.
   * If you want to upgrade your existing vCenter Server with NSX-T instance, you must upgrade to NSX-T 3.0.2.

VMware Solutions Dedicated - new Cascade Lake server support
:   The following {{site.data.keyword.cloud_notm}} bare metal servers are available for deployment for vCenter Server instances and vSphere clusters with vSphere 6.7.

   * Dual Intel Xeon Platinum 8260 (Cascade) / 48 Cores, 2.40 GHz / 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1.5 TB
   * Quad Intel Xeon Platinum 8260 (Cascade) / 96 Cores, 2.40 GHz / 384 GB, 768 GB, 1.5 TB, 3 TB

VMware Solutions Dedicated - support for Osaka {{site.data.keyword.cloud_notm}} data centers
:   The following {{site.data.keyword.cloud_notm}} data centers are available for deployment on vCenter Server, VMware vSphere, and {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads instances: **Osaka 21**, **Osaka 22**, and **Osaka 23**.

VMware Solutions Dedicated - updates for the edge services cluster
:   The CPU model for new deployments of vCenter Server instance edge services clusters is Dual Intel Xeon Silver 4210 (Cascade).

VMware Solutions Dedicated - increased local disk count
:   For new vCenter Server instances and new clusters added to vCenter Server instances, the local disks option for storage now supports 10 and 12 disks.

Add-on services
:   The 3.9 release provides the following service versions on newly deployed instances.

   * BIG-IP VE v15.1.0.5
   * HyTrust CloudControl v6.2 for vCenter Server with NSX-T
   During the pre-configuration of HyTrust CloudControl v6.2, global PIP is enabled.
   * Juniper vSRX and Juniper vSRX Gateway Appliance 3.0 (20.1R1.11)
   * Red Hat OpenShift for VMware v4.4.23
   You can now install the Red Hat OpenShift for VMware service on vCenter Server with NSX-T instances. For NSX-T, you must have a new vCenter Server instance with NSX-T that is provisioned with NSX-T 3.0.1.1 or you must upgrade from NSX-T 2.5.1 to NSX-T 3.0.2.

HyTrust CloudControl for vCenter Server with NSX-V - deprecated
:   New installations of HyTrust CloudControl are no longer supported for new or existing deployments of vCenter Server with NSX-V instances. You can still view or delete existing HyTrust CloudControl installations on your existing instances.
   {: deprecated}

User interface updates and enhancements
:   A new **Uplink speed** option is available in the **Network interface** section when you order vCenter Server instances, order new vSphere clusters, and add clusters for vCenter Server instances.

### 24 August 2020
{: #august-2020}
{: release-note}

VMware Solutions Shared
:   (Updated on 25 August 2020) VMware Solutions provides an upgrade to the Shared infrastructure to the latest version of VMware vCloud Director (vCD) v10.1.1. The v10.1.1 update is available to Dallas and Frankfurt {{site.data.keyword.cloud}} data centers.

   The Flash portal is no longer available with the v10.1.1 update.
   {: note}

VMware Solutions Shared - storage policy updates
:   For the existing storage policies in your virtual data center, the default storage policy is now the new *standard* storage policy. Previously, the default storage policy was *4 IOPS/GB*. This default storage policy is automatic for new VMware Solutions Shared instances.

   The 3.8 release introduces *Standard* storage policies and *Encrypted* storage policies. These new storage policies are available for new VMware Solutions Shared instances and added to existing VMware Solutions Shared instances with the VMware vCloud Director (vCD) v10.1.1 upgrade.

   * A standard storage policy is now available for both decrypted and encrypted policies. The standard storage policy has no maximum throughput, but the number of IOPS/GB is not guaranteed.
   * VMware vCloud Director v10.1.1 provides the capability to create encryption enabled storage policies to all organization virtual data centers. Administrators can encrypt virtual machines (VMs) and disks by associating the VM or disk with a storage policy that has the VM encryption capability.

VMware Solutions Shared - off-site copy mode availability for Veeam Availability Suite
:   Veeam Availability Suite off-site copy mode is now automatically enabled for new and existing VMware Solutions Shared instances.

VMware Solutions Dedicated - VMware vSphere 6.7u3 support
:   You can order VMware vSphere 6.7u3 with your VMware vCenter Server instances and VMware vSphere clusters. vSphere Enterprise Plus 6.7u3 replaces the option to order vSphere Enterprise Plus 6.7u2 with new instances. Additionally, Single-node Trial for Migration and App Modernization and Single-node Trial for Data Protection and Disaster Recovery instances are now ordered with vSphere Enterprise Plus 6.7u3.

   vSphere Enterprise Plus 6.7u3 is available for Skylake, Cascade Lake, and Cascade Lake SAP {{site.data.keyword.cloud_notm}} bare metal servers.

   If you have an existing instance with vSphere Enterprise Plus 6.7u2, you can add new ESXi servers with either vSphere Enterprise Plus 6.7u2 or vSphere Enterprise Plus 6.7u3.
{: note}

VMware Solutions Dedicated - vSphere ESXi 6.7u2 for vSAN storage
:  For vSAN storage, even though vSphere 6.7u3 is selected on the user interface, vSphere ESXi 6.7u2 is installed. This distinction applies to the following scenarios.

   * Newly deployed vCenter Server instances
   * New clusters that are added to new and existing vCenter Server instances
   * New ESXi servers that are added to new and existing vCenter Server instances

   For NFS storage, vSphere ESXi 6.7u3 is installed.

VMware Solutions Dedicated - VMware NSX updates
:   For vCenter Server with NSX-T, new instances are now deployed with NSX-T 3.0.1. Day 2 operations continue to be supported for NSX-T 2.5.1 instances.

   For vCenter Server with NSX-V, new instances are now deployed with NSX-V 6.4.6.

{{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads
:   All newly deployed {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads instances are provisioned with NSX-T.

Add-on services
:   The 3.8 release provides the following service versions on newly deployed instances:

   * BIG-IP VE v15.1.0.4
   * HyTrust CloudControl v6.1.1 for vCenter Server with NSX-T
   * Juniper vSRX and Juniper vSRX Gateway Appliance v19.4R2.6
   * Red Hat OpenShift for VMware v4.4.13

Promotions for VMware Solutions add-on services
:   {{site.data.keyword.vmwaresolutions_short}} offers promotions for some VMware services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges.

   You can use one promotion (promo) code for one or more of the following services.

   * Ordering a new VMware vCenter Server
   * Adding a service to an existing vCenter Server
   * Ordering a stand-alone service (license), such as Caveonix or Veeam

Resource requirements for add-on services
:   Capacity checks are performed to ensure that resource requirements are met for services installation. Capacity checks are performed for the following services during instance deployment.

   * Caveonix RiskForesight
   * F5 BIG-IP
   * FortiGate Virtual Appliance
   * HyTrust CloudControl
   * Zerto

Selecting the target cluster for Red Hat OpenShift for VMware
:   The target cluster for installing Red Hat OpenShift varies with the following scenarios.

   * During deployment, you aren't prompted for the cluster. The service is automatically installed to the management cluster.
   * During day 2 operations, you are prompted for the cluster. You can install the service to a management cluster or a workload cluster.

Deleting services from a cluster before deleting the cluster
:   If you remove a non-management cluster that has services installed on it, the services are also deleted as part of the process.

   Previously, when you removed a non-management cluster, for example, an edge services cluster, any services installed on that cluster were not removed. You had to first delete the services from the cluster and then delete the cluster itself.

   This change affects the Juniper vSRX and Red Hat OpenShift for VMware services.

REST APIs
:   APIs are now available for the Red Hat OpenShift for VMware service.

New and updated documentation
:   A new topic, **Resource requirements for add-on services**, is now available.

   The topic describes how capacity checking works for various services and what resources are required to install certain services, such as Caveonix RiskForesight, Juniper vSRX, and Veeam. The information replaces the documentation that was provided in the overviews of the individual services.

User interface updates and enhancements
:   A checklist is added at the beginning of the ordering pages to help you prepare your environment when you place an order for the first time. This feature does not apply to the following instances and services.

   * Single-node Trial for Migration and App Modernization instances
   * Single-node Trial for Data Protection and Disaster Recovery instances
   * KMIP for VMware instances
   * On-premises VMware HCX instances
   * Caveonix RiskForesight licenses
   * Veeam licenses

### 15 June 2020
{: #june-2020}
{: release-note}

VMware Solutions Shared - Private Network Endpoint add-on service
:   Starting with the 3.7 release, VMware Solutions Shared now supports both public and private network endpoints. Use the Private Network Endpoint service to access your virtual data center from your {{site.data.keyword.cloud_notm}} infrastructure account resources. Connections to private network endpoints do not require public internet access.

VMware Solutions Shared - off-site copy mode availability for Veeam Availability Suite
:   Veeam Availability Suite v10 provides off-site copy mode for new and existing VMware Solutions Shared instances. You must contact IBM support to enable off-site copy.

VMware Solutions Dedicated - new SAP-certified Cascade server support
:   The following new {{site.data.keyword.cloud_notm}} bare metal server CPU models are available for deployment for VMware vCenter Server instances and VMware vSphere clusters with vSphere 6.7.

   * Dual Intel Xeon Gold 5218 processor / 32 cores total, 2.30 GHz / 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB
   * Dual Intel Xeon Gold 6248 processor / 40 cores total, 2.50 GHz / 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB
   * Dual Intel Xeon Platinum 8280M processor / 56 cores total, 2.70 GHz / 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB
   * Quad Intel Xeon Platinum 8280M processor / 112 cores total, 2.70 GHz / 3 TB, 6 TB

   The new servers are not supported for **Chennai 01**.

VMware Solutions Dedicated - removed support for Broadwell servers
:   Broadwell servers are no longer available for new or existing deployments of vCenter Server and VMware vSphere instances and clusters.

VMware Solutions Dedicated - minimum number of bare metal servers
:   For vCenter Server with NSX-T instances, you can now order an instance with only two bare metal servers for the management cluster. The minimum RAM size for the instance to function properly is 192 GB.

   Configurations with only two servers in the management cluster are not recommended for production use.

{{site.data.keyword.cloud_notm}} for VMware Regulated Workloads
:   (Updated on 14 July 14 2020) You can now order {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instances through predefined vCenter Server instance configurations as part of your vCenter Server order flow. The {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads architecture is an extension of the vCenter Server offering, which enhances the basic vCenter Server architecture to deliver a secure, high-performance platform.

Security and compliance updates
:   In June 2020, {{site.data.keyword.vmwaresolutions_short}} acquired a PCI DSS attestation of compliance (AOC), validated by a third-party Qualified Service Assessor (QSA). For more information about {{site.data.keyword.cloud_notm}} compliance and trust certifications, see  [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance).

Add-on services
:   The 3.7 release provides the following service versions on newly deployed instances.

   * Caveonix RiskForesight v2.3. A dedicated private subnet with 32 IP addresses is now ordered, rather than 64 IP addresses.
   * HyTrust DataControl v5.1.1
   * Red Hat OpenShift for VMware v4.4.5.
   * Zerto 7.5 Update 3. The host Windows platform for the Zerto VSI is now Windows Server 2019 Standard Edition (64-bit).

   You can now install the following services on vCenter Server with NSX-T instances.

   * Caveonix RiskForesight
   * HyTrust DataControl
   * Veeam

HyTrust CloudControl
:   Additional configuration is done for HyTrust CloudControl v6.1 for vCenter Server with NSX-T instances.

Veeam
:   Veeam v9.5u4b has known vulnerabilities and it is no longer installed with new VMware Solutions deployments. However, if you installed the service in a previous release, you can continue to use Veeam v9.5u4b.
{: note}

   The new Veeam Availability Suite v10 known as Veeam v10 is now installed.

   There are two deployment types for Veeam v10:
   * Windows Server VM on the management cluster
   * Single public Windows VSI

   The host Windows platform for the Veeam VSI is now Windows Server 2019 Standard Edition (64-bit).

   The process of installing and deleting Veeam licenses is different starting with Veeam v10, in that the license is not deleted when you delete Veeam 10. To avoid being charged, you must delete the license yourself.

Known issues with Red Hat OpenShift for VMware
:   You might encounter the following problems, which cause false alarms about unhealthy etcd members. Review the following problem reports and update the cluster, as needed, when the problems have been fixed.

   * [Red Hat Bugzilla – Bug 1832986 - EtcdMembersDegraded false alarms](https://bugzilla.redhat.com/show_bug.cgi?id=1832986){: external}
   * [Red Hat Bugzilla – Bug 1838781 - EtcdMembersDegraded false alarms](https://bugzilla.redhat.com/show_bug.cgi?id=1838781){: external}

REST APIs
:   Application programming interfaces (APIs) are now available for the following services: Caveonix RiskForesight, HyTrust DataControl (HTDC), and Veeam.

New and updated documentation
:   The following documentation updates are available.

   * (Updated on 14 July 14 2020) The {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads reference architecture is updated.
   * Documentation about the responsibilities of IBM versus the customer's is available at Understanding your responsibilities when using VMware Solutions.
   * Documentation is available about the access type that {{site.data.keyword.cloud_notm}} Support has to your environment and the steps that you can take to limit the access, if required.
   * Documentation is now available about the various ports that are  used in VMware Solutions. The documentation includes the following details.
      * VLANs and subnets that are used
      * Ports for deployment and day 2 operations
      * Ports that VMware uses
      * Ports that the optional services use, such as Caveonix RiskForesight, Juniper vSRX, and Veeam.
   * New FAQ about VMware Solutions Shared is now provided at General FAQ about VMware Solutions Shared. Various updates to the existing FAQs have also been made.

### 20 April 2020
{: #april-2020}
{: release-note}

VMware Solutions Shared
:   For the 3.6 release, you can open an {{site.data.keyword.cloud_notm}} Support ticket to request five additional public IP addresses or an entire subnet for your virtual data center. Include the following details in your support ticket.

   * Instance region and location
   * Organization ID
   * Virtual data center name
   * Number of additional IPs required

VMware Solutions Dedicated - advanced configuration settings for ESXi servers
:   For 3.6 and later releases, new instances are ordered with a new set of advanced configuration settings for ESXi servers.

VMware Solutions Dedicated - port group configuration settings
:   For 3.6 and later releases, security policies for promiscuous mode, MAC address changes, and forged transmits are now accepted on disturbed port groups.

VMware Solutions Dedicated - withdrawal of support for MEL01 data center
:   As part of the data center modernization strategy for {{site.data.keyword.cloud_notm}}, the **MEL01 - Melbourne** {{site.data.keyword.cloud_notm}} data center is closing on 31 August 2020.

   {{site.data.keyword.cloud_notm}} invests significantly in data center infrastructure. These investments include rolling out newer data centers and multizone regions (MZRs) designed to deliver a more resilient architecture with higher levels of network throughput and redundancy.

   Part of this modernization strategy is to close older data centers that are unsuitable for upgrading. As this transition approaches, help is available to assist you in your migration to modern data centers.

VMware vCenter Server - new resource group option
:   When you order the following instances, services, or licenses, you can now select a **Resource group** to organize resources management for access control and billing purposes.

   * vCenter Server instances
   * Caveonix RiskForesight licenses
   * On-premises VMware HCX instances
   * KMIP for VMware instances

VMware vCenter Server - support for VMware Subscription Purchasing Program
:   The support for VMware Subscription Purchasing Program (SPP) is available only to users who are billed in the US.
{: note}

   VMware Subscription Purchasing Program offers a flexible way to consume VMware Subscription Services in the form of Subscription Credits (SPP Credits). When you order vCenter Server instances, you can redeem SPP Credits towards licensing costs.

VMware vCenter Server - support for edge services cluster
:   You can now order an edge services cluster when you are ordering a new vCenter Server instance, with or without the Juniper vSRX service installed on it. You can also install the Juniper vSRX service as a gateway appliance.

Managed Services for VMware Workload Transformation
:   You can now engage Managed Services for VMware Workload Transformation for the day to day management of the virtual infrastructure so that you are free to focus on critical items. This service offers a modular approach with the best in class tools and expertise to deliver remote managed services worldwide.

   You can add Managed Services for VMware Workload Transformation to your instance order at any time by requesting a consultation from the **Overview** page.

F5 BIG-IP
:   The 3.6 release installs BIG-IP VE v15.1.0.2 on newly deployed instances.

HyTrust CloudControl
:   The following versions of the HyTrust CloudControl service are installed on newly deployed instances, based on the NSX networking solution type of your instance.

   * 5.6 for vCenter Server with NSX-V
   * 6.1 for vCenter Server with NSX-T

Juniper vSRX
:   You can install the Juniper vSRX service as one of the following appliances.

   * Juniper vSRX security or gateway appliance on the edge services cluster
   * Juniper vSRX virtual appliance on the management cluster

vRealize Operations and Log Insight

:   You can now install the vRealize Operations and Log Insight service on vCenter Server with NSX-T instances.

REST APIs
:   Application programming interfaces (APIs) are now available for the following services: HyTrust CloudControl (HTCC), Juniper vSRX, and vRealize Operations and Log Insight.

New and updated documentation
:   The following documentation updates are available.

   * Documentation is now provided about managing your data when you use {{site.data.keyword.vmwaresolutions_short}}. For example, what data is stored and encrypted, how to protect your sensitive data, and how you can delete any stored personal data.
   * VMware Solution Shared video tutorials are now available in the **Related links** sections of the VMware Solution Shared and learning resource topics.

User interface updates and enhancements
:   The user interface is updated and provides the following enhancements.

   * {{site.data.keyword.cloud_notm}} data center regional pricing is available as a list in the **Pricing Plans** section of the **About** tab for VMware Solutions Shared instances. Use the {{site.data.keyword.cloud_notm}} Cost Estimator to compare the price difference for each region.
   * When there are new notifications for your system status or user actions, a red dot indicator is displayed along with **Notifications** on the left navigation pane in the {{site.data.keyword.vmwaresolutions_short}} console.
   * On the instance details page, the tags that were specified for search and identification of the instances are displayed next to the instance status.
   * When you order instances, clusters, and licenses, the instance name, cluster name, and license name are set to a default value as follows:
      * Virtual data center instances: vdc-_xx_
      * vCenter Server instances: vcs-_xx_
      * vSphere clusters: vss-_xx_
      * Caveonix RiskForesight licenses: cav-_xx_
      * On-premises VMware HCX instances: hcx-_xx_
      * KMIP for VMware instances: kmip-_xx_
      where _xx_ represents two randomly generated alphabetic characters. You can use the default names or specify new names for them.
   * The following enhancements are made to the **Network Interface** section when you order vCenter Server or vCenter Server with NSX-T instances and when you add clusters for these instances.
      * When you reuse an existing primary subnet, the **Public Primary Subnet** and **Private Primary Subnet** lists display the number of available slots for each IP address.
      * A new **Advanced Settings** option is available for configuring portable subnet settings.

### 24 February 2020
{: #february-2020}
{: release-note}

VMware Solutions Shared
:   (Updated on 26 February 2020) {{site.data.keyword.vmwaresolutions_short}} Shared, a managed public Infrastructure as a Service (IaaS) solution, offers either a standardized or customizable deployment option of VMware vCloud Director Virtual Data Center environments. Use Virtual Data Center instances to quickly and seamlessly migrate or deploy VMware workloads to the cloud on top of IBM hosted VMware infrastructure. The Veeam Availability Suite and Veeam Cloud Connect Replication services are available and ready-to-use in all Virtual Data Center instances. Charges are incurred only if you choose to use the service.

VMware Solutions Dedicated
:   Beginning with the 3.5 release, the VMware vCenter Server (both NSX-V and NSX-T) instances and VMware vSphere clusters are now grouped under a new card on the console, called {{site.data.keyword.vmwaresolutions_short}} Dedicated. This card consolidates the {{site.data.keyword.vmwaresolutions_short}} offerings for a better customer experience.

   On the {{site.data.keyword.vmwaresolutions_short}} console, in the **Start Provisioning** section, you can click the **VMware Solutions Dedicated** to start your instance order.

Improved design for vCenter Server with NSX-T
:   The new NSX-T architecture is significantly improved from earlier {{site.data.keyword.vmwaresolutions_short}} versions. It employs a non-converged cluster design with three or more bare metal servers in the Management cluster and two or more bare metal servers in the Workload cluster. Only VMware vSphere 6.7 is supported for NSX-T instances.

   Currently, no support is provided for:
   * Private-only clusters
   * License upgrades
   * Broadwell CPU generation servers
   * Local disks
   * Add-on services

VMware vSphere 6.5u1 - Deprecated
:   vSphere 6.5u1 has been deprecated.
{: deprecated}

   When you order new instances or add new clusters, you can choose either vSphere 6.7u2 or vSphere 6.5u3. Support for existing customers who are using vSphere 6.5u1 is still provided.

   If you are using vSphere 6.5u1 for your instance, any new clusters are added with vSphere 6.5u2. If you are using vSphere 6.5u1 for your clusters, any new ESXi servers are added with vSphere 6.5u2.

Juniper vSRX
:   Juniper vSRX is a virtual security appliance that provides security and networking services at the perimeter or edge in virtualized private or public cloud environments. Within a VMware infrastructure, vSRX runs as a pair of virtual machines (VMs) within the vSphere environment.

VMware vCenter Server - Cascade Lake updates
:   The 3.5 release provides the following updates for Cascade Lake.

   * The Cascade Lake bare metal server model Quad Intel Xeon Gold 6248 is now available for deployment.
   * Cascade Lake servers are now available in the **LON02 - London** availability zone in the Europe region.

VMware vCenter Server - new models for SAP-certified servers
:   The following SAP-certified bare metal server models are now available for deployment.

   * Dual Intel Xeon Gold 5218 (Cascade, BI.S4.NW192)
   * Dual Intel Xeon Gold 5218 (Cascade, BI.S4.NW384)
   * Dual Intel Xeon Gold 6248 (Cascade, BI.S4.NW768)
   * Dual Intel Xeon Platinum 8280M (Cascade, BI.S4.NW1500)
   * Dual Intel Xeon Platinum 8280M (Cascade, BI.S4.NW3000)

VMware vCenter Server - cluster deployment considerations
:   The allocation of distributed switches for vCenter Server with NSX-V instances is changed. This behavior varies if you have existing instances and clusters. Review the following considerations for switch creation when you create a new cluster.

   * If there are one or more existing clusters in the same pod that uses distributed switches named ``SDDC-DSwitch-Private`` and ``SDDC-DSwitch-Public``, your new cluster uses the same switches as the existing cluster.
   * If there are one or more existing clusters in the same pod that uses distributed switches that have been named by using the same name as the pod (rather than named by using the same name as the cluster), your new cluster uses the same switches as the existing cluster.
   * If there are no existing clusters in the same pod, or all clusters in that pod have distributed switches that have been named by using the same name as the cluster rather than the pod, then your new cluster is configured with the new switch whose name is based only on the pod.

   For vCenter Server with NSX-T instances, clusters in the same pod reuse NSX-T segments and ESXi TEP IP pools. New clusters in new pods create new segments and IP pools.

VMware vCenter Server - vSAN deduplication and compression
:   An option to disable vSAN deduplication and compression is available. This option is available only when you order a new instance or add a cluster.

Add-on services

:   The 3.5 release installs the following service versions on newly deployed instances.

   * BIG-IP VE v15.1
   * Caveonix RiskForesight 2.2.2
   * FortiGate Virtual Appliance 6.2.3

FortiGate Security Appliance - Deprecated
:   Automated deployment of the FortiGate Security Appliance service by using the {{site.data.keyword.vmwaresolutions_short}} console has been deprecated. For a similar service, consider the FortiGate Virtual Appliance, which is also deployed automatically.
{: deprecated}

Gateway Appliances
:   A direct link to order Gateway appliances is now available on the **Security and Compliance** card in the **Services** section of the {{site.data.keyword.vmwaresolutions_short}} console.

User interface updates and enhancements
:   The user interface is updated and provides the following enhancements.

On the ordering pages of instances and services, the following two tabs are added
   * The **Create** tab: you can order an instance or a service on this tab.
   * The **About** tab: you can find the introduction of the instance or service on this tab, such as the technical specifications.

## 2019
{: #year-2019}

### 16 December 2019
{: #december-2019}
{: release-note}

IBM Security Services for SAP
:   Starting with the 3.4 release, IBM Security Services for SAP is now available as a service for your VMware instances in {{site.data.keyword.cloud_notm}}. IBM Security Services for SAP offers a cybersecurity solution to automate the monitoring and protection of SAP applications on {{site.data.keyword.cloud_notm}}, and to keep workloads compliant and secure from inside and outside threats.

PrimaryIO Hybrid Cloud Data Management
:   PrimaryIO Hybrid Cloud Data Management (HDM) is now available for your VMware instances in {{site.data.keyword.cloud_notm}}. This service delivers a seamlessly integrated hybrid cloud for virtual desktops and applications. It provides the enterprise capabilities of the VMware Software-Defined Data Center (SDDC) delivered as a service on {{site.data.keyword.cloud_notm}}, for a simple, secure, and scalable solution.

Red Hat OpenShift for VMware
:   Red Hat OpenShift for VMware on {{site.data.keyword.cloud_notm}} is now available to vCenter Server instances that are deployed in or upgraded to 3.4 or later releases. This service brings together the power of the Red Hat OpenShift Container Platform and the VMware software-defined data center stack. The service offers a consistent hybrid cloud foundation for building and scaling containerized applications.

   For the Single-node Trial for Migration and App Modernization, Red Hat OpenShift Version 4.2 replaces {{site.data.keyword.cloud_notm}} Private Hosted.

{{site.data.keyword.cloud_notm}} Private Hosted - Deprecated
:   The {{site.data.keyword.cloud_notm}} Private Hosted service has been deprecated and replaced by Red Hat OpenShift for VMware.
{: deprecated}

VMware vCenter Server instances
:   The 3.4 release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts.

   * VMware vSphere ESXi 6.5 EP 15 (build 6.5.0-14320405). Applicable only to 6.5u3 hosts, and not to 6.5u2 hosts.
   * VMware vCenter Server Appliance 6.5 Update 3d (build 6.5.0-14836121)
   * VMware Platform Services Controller 6.5 Update 3d (build 6.5.0-14836121)

VMware vCenter Server - VMware vSphere 6.5u3 support
:   VMware vSphere 6.5u3 replaces vSphere 6.5u2 for all new VMware vCenter Server instance orders. vSphere 6.7u2 is also available.

VMware vCenter Server - add cluster enhancements
:   The following add cluster enhancements are available.

   * You can now simultaneously add or remove a cluster while another cluster is being created or removed.
   * A minimum of 1 ESXi server is required when you add a cluster to a vCenter Server instance.

Add-on services
:   The 3.4 release installs the following service versions on newly deployed instances.

   * F5 BIG-IP 15.0.1
   * HyTrust CloudControl 5.6
   * HyTrust DataControl 5.0.1
   * HyTrust KeyControl 5.0.1
   * IBM Spectrum Protect Plus 10.1.5

{{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads
:   Enterprises can now migrate VMware-based Mission Critical Workloads to the {{site.data.keyword.cloud_notm}}, capable of delivering maximum uptime in six multizone regions (MZRs) around the world.

   You can deploy VMware vSAN stretched clusters in an automated and self-managed infrastructure allowing you the flexibility to control and manage all aspects of your solution set. This option is available in on-demand ordering from the **vCenter Server** page on the {{site.data.keyword.vmwaresolutions_short}} console.

   You can deploy a fully managed solution delivered by IBM Services. {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads delivers greater availability, resiliency, and support than many enterprises currently maintain on premises.  This option is available as a fully and coordinated engagement with IBM Services teams.

New and updated documentation
:   The following documentation updates are available.

   * Technical documentation is available in the *Reference* section for {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads and ordering multizone stretched clusters.
   * The *Upgrading VMware NSX* section of **Upgrading vCenter Server vSphere software from VMware vSphere 6.5 to 6.7** has additional information to help you determine whether you must upgrade your current version of NSX. You might have to upgrade NSX so it’s compatible with VMware vCenter Server 6.7.
   * The *Technical specifications for IBM Spectrum Protect Plus* section is updated.
   * The **vCenter Server and vSRX guide** is now available in the *Reference* section of the user documentation.
   * (Updated on 20 December 2019) The **HyTrust DataControl with IBM Cloud Hyper Protect Crypto Services architecture** is now available in the *Reference* section of the user documentation.

User interface updates and enhancements
:   The user interface is updated and provides the following enhancements.

   * The following enhancements are made to the landing page of {{site.data.keyword.vmwaresolutions_short}} console to better assist you in learning and selecting the appropriate offering and services according to your needs:
      * The **Single-Node Trials** section is removed.
      * A new **Featured Services** section is added, where you can find the services and single-node trial offerings that are highlighted.
      * The following enhancements are made in the **Services** section.
         * A new **Featured Workload Solutions** category is added.
         * The previous **Partner Services** category is renamed to **Professional Services**, and the previous **App Modernization** category is renamed to **Transformation and Modernization of VMware Applications**.
   * The following enhancements are made to the **Network Interface** section when you order vCenter Server instances or vCenter Server with NSX-T instances and when you add clusters for these instances.
      * A new **Allocate a new one** option is added to the lists on the **Select Existing VLANs** tab.
      * The **Public VLAN** and **Public Primary Subnet** lists are removed from the **Select Existing VLANs** tab for the **Private Network Only** option.
   * A new **Allocate a new one** option is added to the **Public VLAN**, **Private VLAN**, and **Secondary Private VLAN** lists on the **Select Existing VLANs** tab when you order vSphere clusters.
   * A new **Save Configuration** button is added to the **Order Summary** pane of the ordering page for vCenter Server instances, by using which you can now save your instance settings as a configuration template without placing an order. You can manage the configuration templates by further editing or deleting them as well.

### 21 October 2019
{: #october-2019}
{: release-note}

VMware Horizon 7
:   VMware Horizon 7 is now available to vCenter Server instances that are deployed in or upgraded to 3.3 or later releases.

   This service delivers a seamlessly integrated hybrid cloud for virtual desktops and applications. It combines the enterprise capabilities of the VMware Software-Defined Data Center (SDDC), delivered as a service on {{site.data.keyword.cloud_notm}}, with the market-leading capabilities of VMware Horizon 7 for a simple, secure, and scalable solution.

VMware vCenter Server - customizable hostname prefix in additional clusters
:   When you add a cluster to an instance, you can choose to continue to use the default hostname prefix or to specify a new one for easy identification and management.

HCX
:   HCX now uses Multi-Site Services Mesh to provide its services. Multi-Site Services Mesh provides:

   * Increased flexibility in the configuration and scalability of HCX.
   * Numerous usability improvements, such as deployment diagrams and diagnostic tools.
   * Compute and Network profiles that are shareable across multiple sites that are connected to the HCX cloud instance.

   The {{site.data.keyword.vmwaresolutions_short}} automation configures the Compute profile and Network profiles on the cloud side HCX instance when it is installed, so the instance is ready for pairings with on-premises data centers.

Mission Critical VMware on {{site.data.keyword.cloud_notm}}
:   The Mission Critical VMware on {{site.data.keyword.cloud_notm}} product name is changed to {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads.

NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}
:   Beginning with the 3.3 release, NetApp ONTAP Select is deployed as a partner service through IBM Global Services to provide greater availability, resiliency, and support.

Zerto
:   The 3.3 release installs the Zerto 7.0 Update 2 service version on newly deployed instances.

New and updated documentation
:   New parameters are added to the following APIs:
   * Two new parameters `check_price` and `disk_groups` are added to the **Order a new VMware vCenter Server instance or verify the order** API.
   * A new parameter `disk_groups` is added to the **Add a cluster for a specified VMware vCenter Server instance or verify the order** API and the **Add new hosts to a specified cluster** API.

   The following architecture reference documentation is available in the *Reference* section of the user documentation:
   * Active Directory Domain Services guide
   * vCenter Server and Red Hat OpenShift architecture
   * vCenter Server and Red Hat OpenShift guide
   * vCenter Server and VMware Horizon 7 architecture

   A new topic is available in the *Troubleshooting* section to help you find someone who is an IAM account administrator if you do not have an administrator role and you want to complete an IAM task that requires one.

User interface updates and enhancements
:   Enhancements are made to the landing page of {{site.data.keyword.vmwaresolutions_short}} console to better assist you in learning and selecting the appropriate offering and services according to your needs.
   * The **Getting Started** page is renamed to **Overview**.
   * The deployment offerings are categorized into **Start Provisioning** and **Single-Node Trials**.
   * The add-on services are categorized into **Business Continuity and Migration**, **Security and Compliance**, **Partner Services**, **Management Tools**, and **App Modernization**. Their names are also simplified.
   * A **Learning Resources** section is added.

### 19 August 2019
{: #august-2019}
{: release-note}

VMware HCX for {{site.data.keyword.cloud_notm}} availability
:   Starting with the 3.2 release, you can order the VMware HCX on {{site.data.keyword.cloud_notm}} service with VMware vCenter Server instances. Previously, you might order the HCX on {{site.data.keyword.cloud_notm}} service only through the VMware vCenter Server with Hybridity Bundle instance. The vCenter Server with Hybridity Bundle instance is not supported for new installations. However, functions of existing vCenter Server with Hybridity Bundle instances are preserved and you can install the HCX on {{site.data.keyword.cloud_notm}} service on these instances.

   A 12-month commitment is required when you order the HCX on {{site.data.keyword.cloud_notm}} service. After the 12-month commitment expires, you can install and uninstall the HCX on {{site.data.keyword.cloud_notm}} service and you can add and remove hosts and clusters without restrictions. Your account is then charged monthly and you can cancel at any time.

   The 12-month commitment and charging structure do not apply to existing vCenter Server with Hybridity Bundle instances.
   {: note}

VMware vSphere 6.7 Update 2 support
:   You can order VMware vSphere version 6.7 Update 2 with your VMware vCenter Server, VMware vCenter Server with NSX-T, and VMware vSphere on {{site.data.keyword.cloud_notm}} instances. vSphere Enterprise Plus 6.7u2 replaces the option to order vSphere Enterprise Plus 6.7u1 with new instances. Additionally, Single-node Trial for Migration and App Modernization and Single-node Trial for Data Protection and Disaster Recovery instances are now ordered with vSphere Enterprise Plus 6.7u2.

   vSphere Enterprise Plus 6.7u2 is available for Skylake, Cascade Lake, and Broadwell {{site.data.keyword.cloud_notm}} bare metal servers.

   If you have an existing instance with vSphere Enterprise Plus 6.7u1, you can add new hosts with either vSphere Enterprise Plus 6.7u1 or vSphere Enterprise Plus 6.7u2. However, adding a 6.7u1 host is unsecure. It is recommended that you update your hosts to the latest ESXi server version as soon as possible.
   {: note}

Cascade Lake support
:   The following new bare metal server CPU models are available for deployment with instances and clusters with VMware vSphere 6.7 Update 2. These new models apply to vCenter Server, vCenter Server with NSX-T, and VMware vSphere.

   * Dual Intel Xeon Silver 4210 processor / 20 cores total, 2.3 GHz
   * Dual Intel Xeon Gold 5218 processor / 32 cores total, 2.3 GHz
   * Dual Intel Xeon Gold 6248 processor / 40 cores total, 2.5 GHz

Cascade Lake bare metal servers are available on multizone region
{{site.data.keyword.cloud_notm}} data centers.

VMware vCenter Server instances
:   The 3.2 release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts:

   * VMware NSX for vSphere 6.4.5 (build 13282012)
   * vSphere ESXi 6.7 EP 10 (build 6.7.0-13981272)
   * vCenter Server Appliance 6.7 Update 2b (6.7.0.-13843469)
   * Platform Services Controller 6.7 Update 2b (6.7.0.-13843469)

VMware vCenter Server - cluster updates
:   The following cluster updates are available.

   * You can now specify the name of your initial cluster to be created at the same time you place your instance order.
   * (Updated on 5 November 2019) As a VMware recommended best practice, new clusters are now deployed with a public and private pair of distributed virtual switches. Private-only clusters deploy a new private distributed switch. All networking for the cluster is configured to use these switches.

VMware vSphere instances
:   A public VLAN is no longer required when you order a new vSphere cluster with a private network only.

Add-on services
:   The 3.2 release installs the following service versions on newly deployed instances:

   * F5 on {{site.data.keyword.cloud_notm}} 15.0.0
   * Veeam on {{site.data.keyword.cloud_notm}} 9.5 Update 4b
   * VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
   * Zerto on {{site.data.keyword.cloud_notm}} 6.5 Update 4

VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}
:   The vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} service is now available to VMware vCenter Server instances that are deployed in or upgraded to 3.2 or later releases.

   This service provides VMware vRealize Log Insight (vRLI) integrated with vRealize Operations Manager (vROps), to help you monitor and proactively manage the health and performance of your virtualized environment, and to perform root cause analysis of an issue by filtering and searching through logs.

   You can order vCenter Server instances with vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} included, or add this service to your existing instances later from the Services tab on the instance details page.

   You can also bring your enterprise vRealize Operations and vRealize Log Insight licenses to the cloud (per CPU or OSI) or you can rent licenses from {{site.data.keyword.cloud_notm}}.

New and updated documentation
:   The Activity Tracker documentation is updated.

User interface updates and enhancements
:   The user interface is updated and provides the following enhancements:

   * The instance name requirements have changed. For more information, see the appropriate topic for the instance type that you are ordering.
   * Leading zeros have been added to hostnames to allow for proper sorting.

### 1 July 2019
{: #july-2019}
{: release-note}

Single-node Trial for Data Protection and Disaster Recovery instances
:   The 3.1 release offers the Single-node Trial for Data Protection and Disaster Recovery instances as a quick way to test drive {{site.data.keyword.cloud_notm}} to migrate and recover VMware workloads into the {{site.data.keyword.cloud_notm}}. This trial is a version of VMware vCenter Server, a single-tenant VMware platform that can be managed using the same familiar tools as on-premises environments. This trial includes the Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX on {{site.data.keyword.cloud_notm}}, and Zerto on {{site.data.keyword.cloud_notm}} services.

{{site.data.keyword.cloud_notm}} Expert Services
:   You can engage {{site.data.keyword.cloud_notm}} Expert Services to work together with your internal team to deploy, migrate, and maintain your own {{site.data.keyword.cloud_notm}} solution from planning to modernization, or any stage in between.
{: deprecated}

Integration with the {{site.data.keyword.cloud_notm}} Cost Estimator
:   You can now estimate the cost of your {{site.data.keyword.vmwaresolutions_short}} resources in the unified estimate tool provided by the {{site.data.keyword.cloud_notm}} framework. With this function, you can save a snapshot of resources across the {{site.data.keyword.cloud_notm}} Catalog and store them under a single PDF file that you can download to refer to at a later time. The cost estimator is not a contract or a firm quote, but only an estimate of your total cost.

VMware vCenter Server instances
:   The 3.1 release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts:

   * vSphere ESXi 6.5 Update 2 (build 6.5.0-13635690)
   * vCenter Server Appliance 6.5 Update 2g (build 6.5.0-13638625)

VMware vCenter Server - alternative ESXi server configuration for clusters
:   You can now add new ESXi servers to an existing cluster by either selecting an existing configuration or an alternative configuration than the existing hosts in the cluster. When you order new servers from the **Add Server** window, you can instantly select an existing configuration in the cluster or choose a new 	{{site.data.keyword.cloud_notm}} bare metal server configuration. This applies to all vCenter Server, vCenter Server with Hybridity, and vCenter Server with NSX-T instances.

   To avoid performance or stability issues, it is recommended that clusters use the same or similar configuration with regards to CPU, RAM, and storage. This functionality is useful for hardware updates within the same cluster.

VMware vCenter Server - updates for policy configurations
:   The generated vCenter password for vCenter Server primary instances is now 15 characters in length and has the following password and lockout policy configurations:

   * The minimum length for the vCenter password policy is now 15 characters.
   * The vCenter lockout policy now allows for a maximum of 3 failed login attempts.
   * The vCenter lockout policy now allows for a 900 second time interval between failures.

   The generated NSX Manager password for vCenter Server primary instances is now 15 characters in length. Previously, the generated password was eight characters in length.

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}
:   Caveonix RiskForesight 2.2.1 is installed on all newly deployed instances.

Automatic renewal for HyTrust licenses
:   {{site.data.keyword.vmwaresolutions_short}} now provides automatic renewal support for HyTrust licenses that have the Call Home feature enabled. This support is provided starting with:

   * HyTrust CloudControl 5.5.1 and later
   * HyTrust DataControl 4.3.2 and later
   * HyTrust KeyControl 4.3.2 and later

   You must complete the procedure to enable internet access for your HyTrust virtual machines (VMs) to ensure the automatic renewal of your license. If you don't complete this procedure, your license continues to expire annually.
   {: important}

Veeam on {{site.data.keyword.cloud_notm}}
:   Veeam Availability Suite 9.5 is installed on all newly deployed instances. In addition, a number of updates are made to the Veeam VSIs and Veeam configuration repositories.

Zerto on {{site.data.keyword.cloud_notm}}
:   For new instances deployed in 3.1 and later, Zerto on {{site.data.keyword.cloud_notm}} installations require a billable  {{site.data.keyword.cloud_notm}} account. The cost of VM replication now uses an {{site.data.keyword.cloud_notm}} billable plan instead of {{site.data.keyword.cloud_notm}} infrastructure billing.

   To order Zerto on {{site.data.keyword.cloud_notm}}, your {{site.data.keyword.cloud_notm}} account must meet specific requirements. If you have an existing Zerto on {{site.data.keyword.cloud_notm}} installation, you can convert your Zerto VM billing type to billable.

New and updated documentation
:   The following documentation updates are available.

   * The Activity Tracker instance management events and events for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service are updated.
   * User ID reference documentation is updated with user IDs used for installation and configuration of services by {{site.data.keyword.cloud_notm}} services automation.
   * Reference documentation is available for the new ``Retrieve the detailed network interface of a cluster`` API.
   * The following technical documents are new in the *Reference* section of the user documentation:
      * Operations management
      * Day 2 operational procedures

User interface updates and enhancements
:   The **Clusters** details page now displays the type of storage that the cluster uses.

### 17 May 2019
{: #may-2019}
{: release-note}

End of Support for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}
:   To consolidate our offerings for a better customer experience, the {{site.data.keyword.vmwaresolutions_short}} platform will no longer offer VMware Cloud Foundation effective May 13, 2020.

   Moving forward, all customers are directed to VMware vCenter Server on {{site.data.keyword.cloud_notm}}, our flagship VMware Software-Defined Data Center solution on {{site.data.keyword.cloud_notm}} bare metal servers.

   Existing customers who use VMware Cloud Foundation will be assisted to convert to VMware vCenter Server by the end-of-support date of May 13, 2020.

   After May 13 2020, management functions for VMware Cloud Foundation instances will no longer be available from the {{site.data.keyword.vmwaresolutions_short}} console until the instances are converted to VMware vCenter Server. Customers who choose not to have their VMware Cloud Foundation instances migrated or converted to VMware vCenter Server can access their instances from the {{site.data.keyword.cloud_notm}} infrastructure console.

Removed support for Broadwell 2-CPU servers
:   Starting with teh 3.0 release, Broadwell 2-CPU servers are no longer available for deployment for new vCenter Server, vCenter Server with Hybridity Bundle, vCenter Server with NSX-T, and vSphere on {{site.data.keyword.cloud_notm}} instances and clusters. You can still add servers to existing clusters.

Network File System operation enhancements
:   You can simultaneously add or remove NFS storage and ESXi servers to clusters that are in the **Ready to use** state. For example, you can add or remove an ESXi server in a cluster and add or remove NFS storage in another cluster. This update applies to all vCenter Server and vCenter Server with NSX-T instances.

VMware vCenter Server instances
:   The 3.0 release applies the following upgrades and improvements:

   * vSphere ESXi 6.7 Update 1 (build 6.7.0-13004448)
   * vSphere ESXi 6.5 Update 2 (build 6.5.0-13004031)
   * vCenter Server Appliance 6.7 Update 1b (build 6.7.0-11727113)
   * Platform Services Controller 6.7 Update 1b (build 6.7.0-11727113)

   The Windows software that is ordered for Microsoft Active Directory (AD) and DNS (Domain Name System) services is upgraded to Windows Server 2016 for both configuration options: the VSIs (Virtual Server Instances) and the two highly available Windows VMs.

   The AD domain functional level remains at 2008 to allow for compatibility with an earlier version for any potential secondary instances. If compatibility with earlier (2008) secondary instances is not a consideration in your environment, you can upgrade the domain functional level to a higher version.

VMware vCenter Server - vSAN storage enhancements
:   When you use vSAN storage, the number of {{site.data.keyword.cloud_notm}} bare metal servers that you can order can now be greater than four. This update applies to all vCenter Server, vCenter Server with Hybridity, and vCenter Server with NSX-T instances.

   Starting with v3.0, an M.2 solid-state drive is ordered with your vSAN storage instance. You can order up to 10 capacity disks or a total of 12 capacity disks if you select the **High Performance with Intel Optane** option.

Add-on services
:   The 3.0 release provides the following service versions on newly deployed instances.

   * HyTrust CloudControl 5.5
   * HyTrust DataControl 4.3
   * HyTrust KeyControl 4.3
   * {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2, together with {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2
   * IBM Spectrum Protect Plus V10.1.3

KMIP for VMware on {{site.data.keyword.cloud_notm}}
:   Two new endpoints are now available in London and US East for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service.

New and updated documentation
:   The following documentation updates are available.

   * Documentation is now available to assist you in upgrading {{site.data.keyword.vmwaresolutions_short}} components to VMware vSphere 6.7. This upgrade is required if you want to continue to benefit from {{site.data.keyword.vmwaresolutions_short}} automation.
   * Reference documentation is now available to provide you with user IDs that {{site.data.keyword.vmwaresolutions_short}} maintains for use by {{site.data.keyword.cloud_notm}} automation. Possible messages that display in your instance history logs are also available for your review.
   * The **Reboot/Control** permission is added to the table that describes required permissions for the {{site.data.keyword.cloud_notm}} infrastructure account.
   * New reference documentation is available for the following APIs.
      * List all history messages for a specified VMware vCenter Server instance
      * Add shared storages to a specified cluster
      * Delete NFS storages from a specified cluster

### 25 March 2019
{: #march-2019}
{: release-note}

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T
:   The 2.9 release introduces the VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T offering as a proof of concept or sandbox testing offering. vCenter Server with NSX-T is a privately hosted cloud that you can use to test drive the VMware next generation networking platform, NSX-T.

End of Support for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}
:   To consolidate the current offerings for better customer experience, {{site.data.keyword.cloud_notm}} will no longer support VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} effective May 13 2020.  
 
   Moving forward, all customers are directed to VMware vCenter Server on {{site.data.keyword.cloud_notm}}, which offers more flexibility around storage and licensing options. 
 
   Existing customers who use VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} will be assisted to migrate to VMware vCenter Server on {{site.data.keyword.cloud_notm}} by the end-of-support date of May 13, 2020.

   After May 13 2020, management functions for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} instances will be removed from the {{site.data.keyword.vmwaresolutions_short}} console. Instances that have not been migrated to VMware vCenter Server on {{site.data.keyword.cloud_notm}} can be accessed by using the {{site.data.keyword.cloud_notm}} infrastructure console.

   Customers are contacted by {{site.data.keyword.cloud_notm}} Support before March 25, 2020 to begin migration from VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}.
 
   Customers can view their existing VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} instance on the {{site.data.keyword.vmwaresolutions_short}} console.

VMware vSphere 6.7 Update 1 support
:   You can now order VMware vSphere version 6.7 Update 1 with your VMware vCenter Server, VMware vCenter Server with Hybridity Bundle, and VMware vSphere on {{site.data.keyword.cloud_notm}} instances.

Additionally, Single-node Trial for Migration and App Modernization instances are now ordered with vSphere Enterprise Plus 6.7u1.

vSphere Enterprise Plus 6.7u1 is available for Broadwell and Skylake {{site.data.keyword.cloud_notm}} bare metal servers only.

Support for application programming interfaces
:   Application programming interfaces (APIs) are now available for deploying instances, deleting instances, and adding and removing ESXi servers and clusters.

   The REST API documentation is available in the *Reference* section of the user documentation.

VMware vCenter Server instances
:   The 2.9 release applies the following upgrades and improvements:

   * vSphere ESXi 6.7 Update 1 (build 6.7.0-11675023)
   * vSphere ESXi 6.5 Update 2 (build 6.5.0-11925212)
   * vSphere 6.7 Distributed vSwitch 6.6.0
   * vSphere 6.5 Distributed vSwitch 6.5.0
   * vCenter Server Appliance 6.7 U1 (build 6.7.0-10244745)
   * vSAN 6.7.0 U1
   * NSX for vSphere 6.4.4 (build 11197766)
   * NSX-T for vSphere 2.4

VMware vCenter Server - {{site.data.keyword.cloud_notm}} data centers
:   The following new data centers are available for deployment: **FRA-05 - Frankfurt** and **LON-05 - London**.

VMware vCenter Server - ESXi server enhancements
:   The Secure Shell (SSH) Protocol is now disabled for ESXi servers before instance delivery. If you want to enable SSH, see [Enable SSH from the vSphere Web Client](https://vdc-repo.vmware.com/vmwb-repository/dcr-public/4fcf776d-9ec6-448d-83de-bc730ef047ea/e6a46e41-5c99-4a7d-beed-790cf7e146cd/doc/GUID-C3A44A30-EEA5-4359-A248-D13927A94CCE.html).

   Starting with the 2.9 release, the following ESXi server operations are available.

   * Add new ESXi servers to an existing cluster while the servers are in maintenance mode. Virtual machines are not migrated to the new servers until you remove them from maintenance mode.
   * Simultaneously add or remove ESXi servers across multiple clusters in your instance.

Network File System storage size
:   For vCenter Server instance orders, you can now add up to 24 TB of Network File System (NFS) shared storage for the performance levels of 0.25, 2, and 4 IOPS/GB.

   The 10 IOPS/GB performance level is still limited to a maximum capacity of 4 TB per file share.
   {: note}

Add-on services
:   The 2.9 release provides the following service versions on newly deployed instances.

   * F5-BigIP VE V14.1.0.2
   * HyTrust CloudControl 5.4.2
   * Veeam Backup and Replication 9.5 Update 4
   * Zerto Virtual Replication 6.5 update 3

Caveonix RiskForesight on IBM Cloud
:   The Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service is now available to VMware vCenter Server instances that are deployed in or upgraded to 2.9 or later releases. This service can help to manage cyber and compliance risk with proactive monitoring and automated defense controls to protect against threats and to meet industry or government regulations.

   You can order vCenter Server instances with the Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service included. Additionally, you can add this service to your existing vCenter Server instances later from the **Services** tab on the instance details page.

   You can also order a stand-alone Caveonix RiskForesight license without associating it with any VMware instance for licensing and activation of your on-premises workloads.

KMIP for VMware on IBM Cloud
:   Two new endpoints are now available in Sydney for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service.

   (Updated on 9 April 2019) Previously, KMIP for VMware on {{site.data.keyword.cloud_notm}} used IBM Key Protect for {{site.data.keyword.cloud_notm}} to create, encrypt, and decrypt encryption keys. Starting with the 2.9 release, KMIP for VMware on {{site.data.keyword.cloud_notm}} can also use {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services. These services are a complete set of encryption and key management services that manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}.

User interface updates and enhancements
:   On the **Infrastructure** page, a new **Network Interface** table provides VLAN, subnet, and IP address details for your cluster.

### 28 January 2019
{: #january-2019}
{: release-note}

Single-node Trial for Migration and App Modernization instances
:   The 2.8 release offers the Single-node Trial for Migration and App Modernization as a quick way to test drive {{site.data.keyword.cloud_notm}} to migrate VMware workloads into the {{site.data.keyword.cloud_notm}} and then modernize workloads that use containers. This trial is a version of {{site.data.keyword.icpfull_notm}} Hosted on VMware vCenter Server on {{site.data.keyword.cloud_notm}} that provides the Kubernetes management platform for containers and the single-tenant VMware platform that can be managed by using the same familiar tools as on-premises environments.

Adding and removing Network file system storage
:   You can now add network file system (NFS) storage shares to an existing NFS or vSAN vCenter Server cluster, as well as remove NFS file shares from an existing vCenter Server cluster.

   The following options for customized shared file-level storage are now available.

   * NFS share sizes that start at 20 GB up to 12 TB at single GB increments
   * 0.25 IOPS/GB

SAP-certified Broadwell E5-2690 and E7-8890 server support
:   The following {{site.data.keyword.cloud_notm}} bare metal server CPU models are available for deployment for VMware vCenter Server on {{site.data.keyword.cloud_notm}} and VMware vSphere on {{site.data.keyword.cloud_notm}} instances and clusters.

   * Dual Intel Xeon E5-2690 v4 processor / 28 cores total, 2.60 GHz / 512 GB RAM
   * Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.20 GHz / 1024 GB RAM
   * Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.20 GHz / 2048 GB RAM
   * Quad Intel Xeon E7-8890 v4 processor / 96 cores total, 2.20 GHz / 4096 GB RAM

Broadwell E7-4820 and E7-4850 server support
:   The following {{site.data.keyword.cloud_notm}} bare metal server CPU models are available for deployment for vCenter Server, vCenter Server with Hybridity Bundle, Cloud Foundation, and vSphere on {{site.data.keyword.cloud_notm}} instances and clusters:

   * Quad Intel Xeon E7-4820 v4 / 40 cores total, 2.0 GHz
   * Quad Intel Xeon E7-4850 v4 / 64 cores total, 2.1 GHz

Embedded Platform Services Controller
:   vCenter Server is deployed with an embedded PSC (Platform Services Controller). vCenter Server, the vCenter Server components, and the PSC are deployed on a single virtual machine. This change applies to all newly deployed vCenter Server, vCenter Server with Hybridity, and NetApp instances.

   For instances that are upgraded from an earlier release to 2.8, the PSC is not embedded in vCenter Server. If you want to use embedded PSC, you must convert from external to embedded PSC yourself.

   In a multi-site configuration where the primary instance is an upgraded instance for which the PSC was manually converted from external to embed, any newly deployed 2.8 secondary instances have embedded PSC.

Updates for VMware vCenter Server instances
:   The 2.8 release applies the following upgrades and improvements:

   * vSphere ESXi 6.5 Update EP11 (build 6.5.0-10719125)
   * vCenter Server 6.5 U2d (build 6.5.0-10964411)
   * Platform Services Controller 6.5 U2d (build 6.5.0-10964411)

Updates for VMware Cloud Foundation instances
:   The 2.8 release applies the following upgrades and improvements:

   * vSphere ESXi 6.5 Update EP11 (build 6.5.0-10719125)
   * vCenter Server 6.5 U2c (build 6.5.0-9451637)
   * Platform Services Controller 6.5 U2c (build 6.5.0-9451637)

IBM Spectrum Protect Plus on IBM Cloud
:   The current release installs IBM Spectrum Protect Plus V10.1.2 on all newly deployed instances.

KMIP for VMware on IBM Cloud
:   Previously, you might order a Cloud Foundation or vCenter Server instance with the KMIP for VMware on {{site.data.keyword.cloud_notm}} service that is included or add the service to an existing Cloud Foundation or vCenter Server instance after initial deployment.

   Starting with 2.8, the service is available as a stand-alone service without being associated to a VMware instance. Each instance of the service can serve one or more Cloud Foundation instances, vCenter Server instances, or vSphere clusters.

Reference architecture documentation
:   (Updated on 8 February 2019) The following technical documents are new or updated in the *Reference* section of the user documentation.

   * {{site.data.keyword.vmwaresolutions_short}} architecture (with NSX-V and NSX-T™)
   * Caveonix RiskForesight reference architecture
   * VMware HCX on {{site.data.keyword.cloud_notm}} for VMware Solutions

## 2018
{: #year-2018}

### 12 November 2018
{: #november-2018}
{: release-note}

SAP-certified 6140 server support
:   The 2.7 release offers the following {{site.data.keyword.cloud_notm}} bare metal server CPU models are available for deployment for VMware vCenter Server on {{site.data.keyword.cloud_notm}} and VMware vSphere on {{site.data.keyword.cloud_notm}} instances and clusters.
   * Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 192 GB RAM
   * Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.2 GHz / 384 GB RAM
   * Dual Intel Xeon Gold 6140 processor / 36 cores total, 2.3 GHz / 768 GB RAM

IBM Cloud Private Hosted
:   The {{site.data.keyword.cloud_notm}} Private Hosted service is now available to VMware vCenter Server with Hybridity Bundle instances, in addition to VMware vCenter Server instances that are deployed in (or upgraded to) 2.5 and later releases. You can now order a vCenter Server instance or a vCenter Server with Hybridity Bundle instance with the service included. You can also add the service to an existing vCenter Server instance or a vCenter Server with Hybridity Bundle instance after initial deployment.

Mission Critical VMware on IBM Cloud
:   The Mission Critical VMware on {{site.data.keyword.cloud_notm}} service is now available to instances that are deployed in, or upgraded to, 2.7 or later releases.

   Mission Critical VMware on {{site.data.keyword.cloud_notm}} delivers a multizone cloud architecture to help enterprises prevent downtime for cloud applications and to automate failovers within a cloud region. With this cloud architecture, you can achieve a higher availability and failover success rate than most VMware clients can achieve with on-premises environments or competing cloud platforms.

F5 on IBM Cloud
:   Now when you order the F5 on {{site.data.keyword.cloud_notm}} service, you can select whether you want F5 to apply license over public network or over private network with a proxy server.

FortiGate Virtual Appliance on IBM Cloud
:   In 3Q 2018, Fortinet changed their subscription bundles.

   For FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service that is deployed in 2.7 and later Cloud Foundation instances and vCenter Server instances, FortiOS 6.0.3 is provisioned.

   When you order FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, you can select whether you want FortiGuard to apply license and security updates over public network or over private network with a proxy server.

Zerto on IBM Cloud service component updates
:   For the Zerto on {{site.data.keyword.cloud_notm}} service that is deployed in 2.7 and later Cloud Foundation instances and vCenter Server instances, Zerto Virtual Replication 6.0 update 3 is provisioned.

KMIP for VMware on IBM Cloud integration with IBM Cloud Activity Tracker
:   In addition to VMware instance events, events for KMIP for VMware on {{site.data.keyword.cloud_notm}}, such as key creation, key deletion, and key access, are now integrated with your {{site.data.keyword.cloud_notm}} Activity Tracker instance.

KMIP for VMware on IBM Cloud - Deprecated
:   (Updated on 14 December 2018) The current version of KMIP for VMware on {{site.data.keyword.cloud_notm}} is being deprecated.
{: deprecated}

Reference architecture documentation
:   The following technical documents are now available in the *Reference* section of the user documentation.

   * NSX Edge Services Gateway solution architecture
   * VMware Update Manager guide

User interface updates and enhancements
:   The user interface is updated and provides the following enhancements.

   * The **Customized** tab is now split into the **Skylake** and **Broadwell** tabs based on the server type to help you in server selection. This tab is where you specify CPU model and RAM for bare metal server settings when you order instances.
   * The **Preconfigured** options for bare metal server configuration are not available anymore.
   * The **Type** column is now included in the **vCenter Server instances** table on the **Resources** page to identify vCenter Server, vCenter Server with Hybridity Bundle, and vCenter Limited Test Drive instances.

### 1 October 2018
{: #october-2018}
{: release-note}

Spectre and Meltdown remediation
:   {{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to vulnerabilities related to Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715, and CVE-2017-5754).

   * CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
   * CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
   * CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

High Performance with Intel Optane option
:   The 2.6 release provides the option to add high-performance cache for vSAN storage when you are ordering a new instance or when you add a vSAN cluster after initial deployment.

   With this option, you can increase the number of storage capacity disks from eight to a maximum of ten.

   The High Performance with Intel Optane option is available only for customized configurations with Dual Intel Xeon Gold 5120 and Dual Intel Xeon Gold 6140 processors.

   For more information, see the appropriate ordering topic for your instance or cluster type.

Enabling a public or private network
:   You can now deploy vCenter Server and vCenter Server with Hybridity Bundle instances, as well as VMware vSphere clusters, with public and private network interface cards (NICs) enabled or private only NICs enabled. This option is also available when you add a cluster to your vCenter Server and vCenter Server with Hybridity Bundle instance.

   Some add-on services require public NICs and are not available if you select to enable a private only network.

Deleting ESXi servers
:   You can now delete any ESXi server from your vCenter Server, vCenter Server with Hybridity Bundle, or Cloud Foundation instance if you meet the minimum requirements for your instance.

Updates for VMware vCenter Server instances
:   The 2.6 release applies the following upgrades and improvements.

   * vSphere ESXi 6.5 Update 2c
   * vCenter Server Appliance 6.5 Update 2c
   * Platform Services Controller 6.5 Update 2c
   * NSX for vSphere 6.4.1

Removing the Hybridity Bundle from a vCenter Server instance
:   You can now remove the Hybridity Bundle license from your vCenter Server instance. You are required to replace the VMware NSX and VMware vSAN rental license keys with Bring Your Own License (BYOL) keys. You are required to open a support ticket to cancel charges for the rental licenses.

vCenter Server with Hybridity Bundle availability
:   Business Partners can now order a vCenter Server with Hybridity Bundle instance. Business Partners cannot upgrade an existing vCenter Server instance to a vCenter Server with Hybridity Bundle instance and cannot remove the Hybridity Bundle from a vCenter Server with Hybridity Bundle instance.

Updates for VMware Cloud Foundation instances
:   The 2.6 release applies the following upgrades and improvements:

   * vSphere ESXi 6.5 Update 2c
   * vCenter Server Appliance 6.5 Update 2c
   * Platform Services Controller 6.5 Update 2c
   * NSX for vSphere 6.4.1

Add-on services
:   The 2.6 release provides the following service versions on newly deployed instances.

   * HyTrust CloudControl 5.4
   * HyTrust DataControl 4.2
   * VMware HCX 3.5.1

HyTrust KeyControl on IBM Cloud
:   The HyTrust KeyControl on {{site.data.keyword.cloud_notm}} service is now available to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or upgraded to 2.5 and later releases. The service simplifies the management of encrypted workloads by automating and simplifying the lifecycle of encryption keys. The service can easily manage encryption keys at scale by using FIPS 140-2 compliant encryption. By using this service, you can manage the encryption keys for all your virtual machines and encrypted data stores, and scale it to support thousands of encrypted workloads in large deployments.

   You can order instances with the service included when you order your instance, or add this service to your existing instances later.

Veeam on IBM Cloud support for vSphere ESXi V6.5 update 2c
:   New instances and new hosts are provisioned by using the vSphere ESXi V6.5 Update 2c. If you are using Veeam Backup and Replication, Veeam recommends that you update your Veeam on {{site.data.keyword.cloud_notm}} instance to V9.5u3a or later. This update ensures the best compatibility with vSphere ESXi 6.5 Update 2c.

It is recommended that existing Cloud Foundation instances that have Veeam on {{site.data.keyword.cloud_notm}} installed also update to V9.5u3a or later.

Zerto on IBM Cloud support for vSphere ESXi V6.5 update 2c
:   If you update existing hosts to vSphere ESXi V6.5 update 2, and have previously installed Zerto on {{site.data.keyword.cloud_notm}}, the Zerto Virtual
Replication console might show the `Unsupported ESX Version` warning message under the Zerto Virtual Replication Appliances (VRAs) status.

Reference architecture documentation
:   The {{site.data.keyword.vmwaresolutions_short}} architecture document is updated to include important considerations to understand your responsibilities for managing and operating your VMware instance.
