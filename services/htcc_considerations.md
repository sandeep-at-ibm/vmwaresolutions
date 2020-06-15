---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-12"

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

The HyTrust CloudControl service enforces and controls compliance against security standards, which includes role-based access control (RBAC), approval, and auditing. When the service is combined with HyTrust DataControl, the service ensures that virtual machines and workload data don't leave a particular region, cluster, or ESXi server within the {{site.data.keyword.cloud}} data center.
{: shortdesc}

The following versions of the HyTrust CloudControl service are installed, based on the NSX networking solution type of your instance:
* 5.6 for vCenter Server with NSX-V
* 6.1 for vCenter Server with NSX-T

## Technical specifications for HyTrust CloudControl
{: #htcc_considerations-specs}

For vCenter Server with NSX-T instances, HyTrust CloudControl v6.1 is configured with connections to the following  components:
* Microsoft Active Directory
* VMware vCenter Server
* VMware NSX-T

Sample users and groups are configured in Active Directory and are displayed on the service details page. If you delete HyTrust CloudControl, the sample users are  deleted from Active Directory too. To implement vCenter Server single sign-on and trust manifests, more customization is required.

The following components are ordered and included in the HyTrust CloudControl service:

### HyTrust CloudControl appliance
{: #htcc_considerations-appliance}

* CPU: 4 vCPU
* RAM: 16 GB
* Disk:
  * For version 5.6: 70 GB VMDK resident on vSAN
  * For version 6.1 or higher: 186 GB VMDK resident on vSAN
* Network: Placed on VLAN-backed private portable network specified for management

### High availability
{: #htcc_considerations-ha}

Two CloudControl appliances are deployed in an active-passive configuration.

### Licenses and fees
{: #htcc_considerations-licenses}

Per-host license: A HyTrust CloudControl license is ordered for each host in the environment.

## Considerations when you install HyTrust CloudControl
{: #htcc_considerations-install}

* Before the service is installed in your environment, a check is performed against the available capacity of the default cluster in the environment to ensure that the service components can fit.
* If the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email.
* To install the service, you must increase the capacity in your default cluster by either adding more hosts or by freeing up RAM, CPU, or disk space, and then add the service again in the console. After that, you can delete the existing service in the **Capacity Validation Failed** state by clicking the delete icon next to it.

## Considerations when you delete HyTrust CloudControl
{: #htcc_considerations-remove}

Before you delete the HyTrust CloudControl service, ensure that you disable **Root Password Vaulting**, if configured, and that you delete all protected hosts from HyTrust CloudControl.

## Related links
{: #htcc_considerations-related}

* [Ordering HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_ordering)
* [Managing HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-managinghtcc)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [HyTrust website](https://www.hytrust.com/){:external}
