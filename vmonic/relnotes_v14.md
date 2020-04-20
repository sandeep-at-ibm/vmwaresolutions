---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-08"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V1.4
{: #relnotes_v14}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Component updates for Cloud Foundation instances
{: #relnotes_v14-vcf-comp}

The following components are new or updated:

* VC and PSC (vCenter and Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* A new Windows VSI (Virtual Server Instance) is ordered for Microsoft Active Directory (AD) and DNS (Domain Name System) services, which are required for multi-site configuration support in this release. This VSI has the following specifications: Windows 2012 R2 (8 GB RAM / 2 CPU cores / 100 GB disk / Dual 1 Gbps private uplinks).

## Component updates for vCenter Server instances
{: #relnotes_v14-vcs-comp}

The following components are new or updated:

### VMware NSX for vSphere 6.2.4
{: #relnotes_v14-nsx}

VMware NSX for vSphere 6.2.4 is now installed by default on all vCenter Server instances (previously on Cloud Foundation instances only).

As part of the NSX installation, the NSX Manager is installed and licensed on all new instances that are deployed. In addition, an NSX Edge is created for instance management, but you can create your own NSX Edge components if required.

The NSX Controller is not installed on vCenter Server instances (the way it is installed on Cloud Foundation instances). If you are using VXLAN or distributed logical routers for your vCenter Server instances, then you must install the NSX Controller yourself.
{:note}

### VMware NSX Edge
{: #relnotes_v14-nsx-edge}

NSX Edge is now included as part of the new vCenter Server instances that you are ordering. NSX Edge provides network edge security and gateway services to isolate a virtualized network.

During instance deployment, a Management VMware NSX Edge Services Gateway (ESG) is deployed by IBM. This ESG is used by the IBM management virtual machines to communicate with specific external IBM management components that are related to automation. This ESG is deployed to include two interfaces: one interface is connected to the {{site.data.keyword.cloud_notm}} private VLAN, and the other one is connected to the {{site.data.keyword.cloud_notm}} public VLAN.

To ensure security, firewall rules are in place to allow only outbound HTTPS communications that are initiated by the management virtual machines. This ESG is deployed in a Large configuration, and only IBM Support can modify the configuration.

### NSX license
{: #relnotes_v14-nsx-license}

A VMware NSX Base for Service Providers Edition license per node is ordered.

### New subnet address block
{: #relnotes_v14-subnet}

A subnet block of 16 public portable addresses per node is ordered.

## Service charge model updates
{: #relnotes_v14-svc-charge}

The service charge model is simplified:

* For Cloud Foundation instances, the _VMware Cloud Foundation instance service_, _VMware Cloud Foundation storage service_, and
   _VMware Solutions Hypervisor_ fees are discontinued.
* For vCenter Server instances, the _VMware vCenter Server instance_ and _VMware Solutions Hypervisor_ fees are discontinued.
* For both instance types, a new _Support and Services_ fee is introduced, which is a monthly fee that is applied to each node.

## Updates to instance networking topology
{: #relnotes_v14-netwok-topo}

This release includes the following topology enhancements for your instances:

* For both Cloud Foundation instances and vCenter Server instances: Optimized networking configuration, that is, only the primary public and private IP addresses that are assigned by SoftLayer® are attached to ESXi servers. Portable private addresses are no longer deployed for management traffic.
* For Cloud Foundation instances only: Windows AD SSO (Active Directory Single Sign-On) and Domain Name System (DNS) server

Because of these changes, you cannot use your existing pre-V1.4 instances in the current release. To reuse the configuration of your existing instances, you must upgrade them to the current version.
{:note}

## Multi-site configuration support for Cloud Foundation instances
{: #relnotes_v14-vcf-multisite}

You can now deploy either a single Cloud Foundation instance, just like in previous releases or, in addition, deploy secondary instances that are attached to a primary instance. The multi-site configuration model uses a hub and spoke topology with a primary site and a maximum of seven secondary sites.

## Enhancements to the deployment of Zerto disaster recovery
{: #relnotes_v14-zerto}

* For Cloud Foundation instances, the deployment of Zerto disaster recovery is automated rather than handled through a support ticket. All Zerto components, such as a private portable subnet, a Windows VSI (Virtual Service Instance), and the Zerto license charges are listed on the estimated cost, so you can review before you place your order.
* For vCenter Server instances, the deployment of Zerto disaster recovery is done through a support ticket, as in the previous release. However, NSX Edge and the public portable subnet are no longer needed, since they are now included in the base deployment. The charges for a private portable subnet, a Windows VSI (Virtual Service Instance), and the Zerto license still apply.

## Instance order process
{: #relnotes_v14-inst-order}

The instance order process is greatly simplified:

* For both Cloud Foundation instances and vCenter Server instances, the SoftLayer Credentials page is no longer displayed during the order process. The SoftLayer credentials that are defined on the Settings page are used by default and you are prompted to update them only if they do not meet the requirements.
* In addition, for vCenter Server instances, only the **Large** option for the **Hardware** type and the **10 Gbps Dual** setting for the **Uplink Port Speed** are now available, which reduces the number of settings to specify when ordering.

## Instance management
{: #relnotes_v14-inst-mgmt}

New features and improvements are made to the instance management process:

* For Cloud Foundation instances, you can view the user name and passwords for various instance components on the instance details page.
* For vCenter Server instances, you can now install software updates and patches for IBM components directly from the console.

## Console notifications
{: #relnotes_v14-console-notif}

You can now configure console notifications on the **Settings** page. By default, the setting is enabled, which means that you receive a notification in the console for all events. You can also disable notifications for the console on the **Settings** page.
