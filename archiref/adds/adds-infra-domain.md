---

copyright:

  years:  2019, 2020

lastupdated: "2020-02-04"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud for VMware Solutions infrastructure domain
{: #adds-infra-domain}

The {{site.data.keyword.vmwaresolutions_full}} infrastructure domain holds the resource objects and user accounts for the administration of the vCenter Server instance only. Using this domain to hold resource objects and user accounts for your workload VMs is not recommended.

Within the vCenter Server design, the {{site.data.keyword.vmwaresolutions_short}} infrastructure AD domain is used for:
* DNS - The appliances provisioned as part of the services have DNS entries in the AD. These entries enable the functions of the vCenter Server instance to use FQDN and do name lookups.
* Authentication services -  An AD security group is added, and a number of accounts are added to enable the automation.

In {{site.data.keyword.vmwaresolutions_short}}, every primary instance deploys a forest root domain and configures the site topology. The {{site.data.keyword.vmwaresolutions_short}} AD/DNS is always going to be its own forest and domain, you cannot remove this forest or domain because it might break the {{site.data.keyword.vmwaresolutions_short}} automation. You can't migrate the users and resources to one of your existing domains or create a new domain, as you can't create the credentials for the IBM user named `automation`.

During the ordering process of a vCenter Server instance the following information is collected from the user that is pertinent to the AD DS and DNS configuration:
* Hostname prefix
* Subdomain label
* Domain name

These values are then used to generate the user name and server names of the instance. For more information, see [Ordering vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance).

## Domain controllers
{: #adds-infra-domain-controllers}

All AD domain controllers that are used in the IBM Cloud for VMware Solutions infrastructure domain are exclusively yours and nothing is shared with other customers. You must provide operational management to monitor, update, back up, and recover these domain controllers.

You must administer users, groups, computer and group policies, in the same manner as you do with your on-premises AD by using standard AD tools. You have full administrative control of the operating system and the AD environment that gets deployed as part of the vCenter Server instance provisioning. You can set up custom configurations and create simple or complex topology as needed.

During the ordering process, you can deploy:
* A single Microsoft Windows Server VSI for AD DS
* Two highly available Microsoft Windows VMs in the cluster

Currently, Microsoft Windows Server 2016 Standard is deployed for the operating system. The domain functional level 2008 is set to allow for backward compatibility with any potential secondary instances. If compatibility with earlier (2008) secondary instances is not a consideration in your environment, you can upgrade the domain functional level to a higher version.

For more information, see [Forest and Domain Functional Levels](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-functional-levels){:external}.

### Single VSI domain controller
{: #adds-infra-domain-controllers-vsi}

The following diagram shows the deployment pattern of the single VSI domain controller.
![Single VSI domain controller diagram](../../images/adds-advsi.svg "Single VSI domain controller diagram"){: caption="Figure 1. Single VSI domain controller diagram" caption-side="bottom"}

If you order the single VSI, it is recommended that you manually order a second VSI of the same type and configure this VSI as a second domain controller to enable AD DS as a highly available service. The following table describes the VSI configuration.

| Parameter          | Specification                                 |
|:-------------------|:----------------------------------------------|
| Operating System   | Windows Server 2016 Standard Edition (64 bit) |
| CPU                | 2 x 2.0 GHz or higher Cores                   |
| RAM                | 8 GB                                          |
| Disk               | 100 GB (SAN)                                  |
| Uplink Port Speeds | 1 Gbps Private Network Uplink                 |
{: caption="Table 1. VSI specifications" caption-side="top"}

The domain controller is provisioned with a name of `ADNS<subdomain_label>.<root_domain>`, for example, `ADNSoncloud.myroot.local`. This server is the Global Catalog instance for the domain.

### Two highly available Microsoft Windows VMs in the cluster
{: #adds-infra-domain-controllers-ha}

The following diagram shows the deployment pattern of the two highly available VM domain controllers.
![Two highly available VM domain controllers diagram](../../images/adds-adha.svg "Two highly available VM domain controllers"){: caption="Figure 2. Two highly available VM domain controllers" caption-side="bottom"}

If you order the two high availability Microsoft Windows VMs, you must provide two Microsoft Windows Server 2016 licenses. For more information, see [DNS Configuration](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-dns-config). After the provisioning of the vCenter Server instance, you have 30 days to activate the VMs. The cluster is configured with a VM-VM anti-affinity rule, therefore, Distributed Resource Scheduler (DRS) tries to keep the VMs apart by placing them on different physical vSphere ESXi hosts. The following table describes the VM configuration.

| Parameter        | Specification                                 |
|:-----------------|:----------------------------------------------|
| Operating System | Windows Server 2016 Standard Edition (64 bit) |
| CPU              | 2                                             |
| RAM              | 8 GB                                          |
| Disk             | 100 GB                                        |
{: caption="Table 2. HA VM specifications" caption-side="top"}

## Domain configuration
{: #adds-infra-domain-config}

After the domain controllers are provisioned, AD DS is configured as follows:
1. The domain name is set as <root_domain>, collected from the order process.
2. The ic4V-vCenter AD security group is added to the domain.
3. The following AD users are created in the domain:
* automation - Member of Administrators, Domain Admins, Domain Users, Enterprise Admins, ic4v-vCenter, Schema Admins, and Users AD groups.
* cloudbase-init - member of the Administrators and Domain Users AD groups (this user is created by the VSI automation for use during initial provisioning of the VSI).
* add-on service accounts, for example, `prod-Caveonix-19765` or `prod-Zerto-5c9cb035` - member of `ic4V-vCenter` and `Domain Users` AD groups.

As the customer, you have full access to add more system administrators to the ic4V-vCenter AD security group to allow each administrator with access to vCenter. It is recommended that this domain holds only the resources and user accounts for administration of the vCenter Server instance only.

## User IDs
{: #adds-infra-domain-ids}

The IBM Cloud automation initially configures some customer and IBM user IDs when the vCenter Server instance is created. The IBM user IDs are used by the automation for operations such as: adding clusters, vSphere ESXi hosts, or storage to your vCenter Server instance. These operations might fail if the IBM user IDs are deleted, disabled, or if their passwords are changed.

For more information, see [IBM User IDs](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids).

## Multi-site topology
{: #adds-infra-domain-multisite}

As an option in {{site.data.keyword.vmwaresolutions_short}}, you can provision vCenter Server instances in a multi-site topology. Your first instance is the primary instance, but subsequent orders can be either primary or secondary depending on the topology you want to create. By using a primary instance and then selecting secondary instances, you create a multi-site topology.

You can have a maximum of one primary and seven secondary instances in a multi-site configuration:
* Primary instance - To deploy the first instance, you define that instance as primary during the instance order process.
* Secondary instances - The instances that are attached to the primary instance are defined as secondary instances during the order process.

AD and DNS replication is automatically set up between the domain controllers on the primary and secondary instances. If you are using a single AD domain controller at each site, configure the DNS settings manually, as follows:
* Primary instance components - use the secondary instance DNS as the secondary DNS server.
* Secondary instance components - use the primary instance DNS as the secondary DNS server.

They key aspects of a multi-site configuration are:
* Enhanced Linked Mode
* Cross vCenter NSX

Enhanced Linked Mode and Cross-vCenter NSX are complementary but separate from each other. For more information, see [Multi-site configuration for VMware vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_multisite).

### Enhanced linked mode
{: #adds-infra-domain-multisite-elm}

Enhanced Linked Mode (ELM) lets you view and search across all linked vCenter Server systems and replicate roles, permissions, licenses, policies, and tags. ELM provides the following benefits:

* A single-pane-of-glass view into the environment and where there are multiple vCenter Servers.
* Simplified primary, secondary relationship creation by using Single sign-on (SSO) credentials.
* vCenter Server automation configuration for DNS name resolution for all the sites that are linked together.
* In a cross-vCenter NSX environment, ELM allows to you manage all NSX Managers from a single vSphere Web Client
* Single pane of glass management across all sites for both NSX and normal vCenter functions.

ELM does not bring high availability for vCenter services, just simplifies the management of multiple vCenters. ELM is configured by the IC4VS automation when a secondary instance is deployed.

### Cross vCenter NSX
{: #adds-infra-domain-multisite-nsx}

In cross-vCenter NSX, you have a primary NSX Manager and multiple secondary NSX Managers. Each of these NSX Managers is linked to a separate vCenter Server. On the primary NSX Manager, you can create universal NSX components such as switches and routers that are viewable from the secondary NSX Managers.

Cross-vCenter NSX includes these features:
* The same logical networks are available in the cross-vCenter environment, so it's possible for VMs on any cluster on any vCenter Server system to be connected to the same logical network.
* Firewall rules are managed from one centralized location, and apply to the VM regardless of location or vCenter Server system.
* Centralized management of universal objects, reducing administration effort.
* VMs can be migrated by using vMotion across vCenter Servers without having to reconfigure the VM or change firewall rules.

When cross-vCenter NSX is combined with ELM, you can view and manage any of the NSX Managers and all of the universal NSX components from any of the linked vCenter Servers. ELM is not a prerequisite or requirement for cross-vCenter NSX. Without ELM, you can still create cross-vCenter universal transport zones, universal switches, universal routers, and universal firewall rules. However, without ELM in place, you must log in to the individual vCenter Servers to access each NSX Manager instance. Cross vCenter NSX is not automatically deployed and the customer must deploy this manually by following the tasks in [Configuring the Primary NSX Manager](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.cross-vcenter-install.doc/GUID-0B74FB40-1D90-4A6A-B7CE-B4EF3B923452.html){:external}.

### Active Directory, SSO, and DNS in a multi-site topology
{: #adds-infra-domain-multisite-ad}

AD, DNS, and SSO are configured slightly differently in a primary and secondary instance.

The primary instance has the following configuration:
* AD and DNS root domain.
* vCenter Server subdomain.
* SSO domain.
* SSO site name.

The secondary instances have the following configuration:
* DNS subdomain that is linked to the root domain on the primary instance.
* SSO site name.
* DNS and AD replication setup between the domain controllers on the primary and secondary instances.
* ELM setup between the secondary instance vCenter to the vCenter in the primary instance.

## Customer user IDs
{: #adds-infra-domain-userid}

The customer user IDs and passwords for the vCenter Server instance are available through the IBM Cloud for VMware Solutions console. Go to VMware Solutions, Summary, Resources, <instance_name>, Summary. For more information, see [vCenter and Platform Services Controller user IDs](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids).

## DNS configuration
{: #adds-infra-domain-dns}

The vCenter Server instance design integrates DNS services on the AD domain controllers as follows:
* The domain structure is specified during the instance order process.
* The domain controllers are configured to be authoritative for both the DNS domain and subdomain space.
* The domain controllers servers are configured to point to the IBM Cloud DNS servers for all other zones.
* Any secondary vCenter Server instances that are integrated to the primary instance use the same DNS name structure before the subdomain.

When a secondary vCenter Server instance is linked to the primary instance, the vCenter Server instances appliances are configured as follows:
* DNS is configured with the primary instances AD DNS server IP address.
* Secondary DNS is configured with the secondary instances AD DNS server IP address.

AD DS DNS is configured with a forward lookup zone with the name of <root_domain>, <subdomain_label>, and populated with the following host (A) records:
* clouddriver
* vcenter-<subdomain_label> or vcenter and psc-<subdomain_label>
* NsxManager
* Add-on services when ordered, for example, HCX, RiskForesight, Veeam, Zerto.

Reverse lookup zones with the start of authority (SOA), name server (NS) and the required pointer (PTR) records for the appliances in the following subnets:
* Management subnet
* Internal-mgmt subnet
* Add-on services subnets, for example, HCX subnet, risk foresight subnet

The forwarder section is configured with:
* 10.0.80.12
* 10.0.80.11

Forwarders are DNS servers that the AD DNS server can use to resolve DNS queries for records that the AD server cannot resolve. 10.0.80.12 and 10.0.80.11 are the two addresses for IBM Cloud Resolving Name Servers. Resolving name servers are located on the private network and act as DNS resolvers. The private resolvers query the internet's root name servers for domain lookups and resolve this information over the private network to keep your bandwidth usage down, reduce the load on the authoritative servers, and offer quick resolution. Private network resolvers are a convenience service for our customers.

All deployed appliances: VCSA, NSX Manager and Controllers, and vSphere ESXi hosts have their DNS settings configured to point to the AD DNS server as their default DNS. You can customize the DNS zone configuration if it does not interfere with the configuration of the deployed components.

**Next topic:** [vCenter Single Sign On](/docs/services/vmwaresolutions?topic=vmware-solutions-adds-sso)

## Related links
{: #adds-infra-domain-related}

* [Overview of {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
* [Getting started with IBM Cloud for VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [IBM Cloud for VMware Solutions: Take a look under the hood](/docs/services/vmwaresolutions?topic=vmware-solutions-under_the_hood)
