---

copyright:

  years:  2016, 2021

lastupdated: "2021-07-07"

keywords: HyTrust CloudControl, HTCC, tech specs HTCC

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl overview
{: #htcc_considerations}

The HyTrust® CloudControl™ service enforces and controls compliance against security standards, which includes role-based access control (RBAC), approval, and auditing. When the service is combined with HyTrust DataControl®, the service ensures that virtual machines and workload data don't leave a particular region, cluster, or VMware ESXi™ server within the {{site.data.keyword.cloud}} data center.
{: shortdesc}

New installations of HyTrust CloudControl are supported only for VMware vCenter Server® with NSX-T™ instances. The HyTrust CloudControl version that is installed is 6.3.1. Previous installations of HyTrust CloudControl 5.6 are still supported for existing VMware® vCenter Server with NSX-V instances.
{:note}

{{site.data.keyword.vmwaresolutions_short}} offers promotions for some services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices#vc_addingservices-service-promotions).

## Technical specifications for HyTrust CloudControl
{: #htcc_considerations-specs}

For more information about resource requirements and capacity checking for some services, see [Resource requirements for services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices#vc_addingservices-resource-requirements).

HyTrust CloudControl is preconfigured with connections to the following components:
* Microsoft® Active Directory™
* vCenter Server
* VMware NSX-T

As part of HyTrust CloudControl service configuration, global PIP is enabled.

Sample users and groups are preconfigured in Active Directory (AD) and are displayed on the service details page. If you delete HyTrust CloudControl, the sample users are deleted from AD too. A sample trust manifest is set up that gives single sign-on (SSO) permissions to the sample users that are created. You can change this setting or customize it for your own requirements.

The following components are ordered and included in the HyTrust CloudControl service:

### HyTrust CloudControl appliance
{: #htcc_considerations-appliance}

* CPU: 4 CPUs
* RAM: 16 GB
* Disk: 186 GB VMDK resident on vSAN
* Network: Placed on VLAN-backed private portable network specified for management

### High availability
{: #htcc_considerations-ha}

Two CloudControl appliances are deployed in an active-passive configuration.

### Licenses and fees
{: #htcc_considerations-licenses}

Per host license: A HyTrust CloudControl license is ordered for each host in the environment.

## Considerations when you delete HyTrust CloudControl
{: #htcc_considerations-remove}

Review the following considerations before you delete the service:

* Before you delete HyTrust CloudControl, ensure that you disable **Root Password Vaulting**, if configured, and that you delete all protected hosts from HyTrust CloudControl.

* If you installed the HyTrust CloudControl service before VMware Solutions v4.0, and you then delete that service, you must manually remove the DNS entries. For more information, see [Manually removing the DNS entries](/docs/vmwaresolutions?topic=vmwaresolutions-vc_deletingservices#vc_deletingservices-DNS-entries).

## Related links
{: #htcc_considerations-related}

* [Ordering HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_ordering)
* [Managing HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-managinghtcc)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [HyTrust website](https://www.hytrust.com/){:external}
