---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust CloudControl on IBM Cloud overview

The HyTrust CloudControl on {{site.data.keyword.cloud}} service enforces and controls compliance against security standards, and provides detailed role-based access control (RBAC), approval, and auditing capabilities. When combined with HyTrust DataControl, the service can ensure that virtual machines and workload data do not leave a particular region, cluster, or ESXi server within the {{site.data.keyword.CloudDataCent_notm}}.

**Availability:** This service is available only to instances that are running vSphere 6.5 and that are deployed in (or upgraded to) V2.3 or later releases.

## Technical specifications for HyTrust CloudControl on IBM Cloud

The following components are ordered and included in the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service:

### HyTrust CloudControl appliance

* CPU: 4 vCPU
* RAM: 16 GB
* Disk: 70 GB VMDK resident on vSAN in converged cluster
* Network: Placed on VLAN-backed private portable network specified for management

### High availability

Two CloudControl appliances are deployed in an active-passive configuration.

### Licenses and fees

Per-host license: A HyTrust CloudControl license is ordered for each host in the environment.

## Considerations when removing HyTrust CloudControl on IBM Cloud

Before you remove the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service, ensure that you disable **Root Password Vaulting**, if configured, and that you delete all protected hosts from HyTrust CloudControl.

### Related links

* [Ordering HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Managing HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust website](https://www.hytrust.com/)
