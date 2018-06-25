---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# HyTrust CloudControl on IBM Cloud overview

The HyTrust CloudControl on {{site.data.keyword.cloud}} service enforces and controls compliance against security standards, and provides detailed role-based access control (RBAC), approval, and auditing capabilities. When combined with HyTrust DataControl, the service can ensure that virtual machines and workload data do not leave a particular region, cluster, or ESXi server within the {{site.data.keyword.CloudDataCent_notm}}.

**Availability:** This service is available only to instances that are running vSphere 6.5 and that are deployed in (or upgraded to) V2.3 or later releases.

## Components of HyTrust CloudControl on IBM Cloud

A highly available (HA) pair of HyTrust CloudControl (HTCC) appliances is deployed on the default cluster in active-passive mode.

Each pair of HTCC appliances is deployed on the same private portable subnet that is specified for the management virtual machines (VMs), such as NSX Manager, vCenter Server Appliances, and Platform Services Controller.

The pair of appliances acts as a proxy for the vSphere hosts, vCenter Server appliance, and NSX manager of an instance. Therefore, users access the vSphere hosts, vCenter Server Appliance, and NSX Manager via a published IP (PIP) address that is assigned by the administrator instead of the real IP address (RIP) that is assigned by {{site.data.keyword.cloud}}.

The HTCC appliances integrate with the Microsoft Active Directory to enforce role-based access control.

## Considerations when removing HyTrust CloudControl on IBM Cloud

Before you remove the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service, ensure that you disable **Root Password Vaulting**, if configured, and that you delete all protected hosts from HyTrust CloudControl.

## Related links

* [Ordering HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Managing HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust website](https://www.hytrust.com/)
