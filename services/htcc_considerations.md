---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl on IBM Cloud overview
{: #htcc_considerations}

The HyTrust CloudControl on {{site.data.keyword.cloud}} service enforces and controls compliance against security standards that includes role-based access control (RBAC), approval, and auditing. When the service is combined with HyTrust DataControl, the service ensures that virtual machines and workload data don't leave a particular region, cluster, or ESXi server within the {{site.data.keyword.CloudDataCent_notm}}.

This service is available only to instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.3 or later. The current HyTrust CloudControl version that is installed is 5.5.
{:note}

## Technical specifications for HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-specs}

The following components are ordered and included in the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service:

### HyTrust CloudControl appliance
{: #htcc_considerations-appliance}

* CPU: 4 vCPU
* RAM: 16 GB
* Disk: 70 GB VMDK resident on vSAN in converged cluster
* Network: Placed on VLAN-backed private portable network specified for management

### High availability
{: #htcc_considerations-ha}

Two CloudControl appliances are deployed in an active-passive configuration.

### Licenses and fees
{: #htcc_considerations-licenses}

Per-host license: A HyTrust CloudControl license is ordered for each host in the environment.

## Considerations when you remove HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-remove}

Before you remove the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service, ensure that you disable **Root Password Vaulting**, if configured, and that you delete all protected hosts from HyTrust CloudControl.

## Related links
{: #htcc_considerations-related}

* [Ordering HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Managing HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust website](https://www.hytrust.com/)
