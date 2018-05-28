---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Components and considerations for HyTrust CloudControl on IBM Cloud

The HyTrust CloudControl on {{site.data.keyword.cloud}} service enforces and controls compliance against security standards, and provides detailed role-based access control (RBAC), approval, and auditing capabilities. When combined with HyTrust DataControl, the service can ensure that virtual machines and workload data do not leave a particular region, cluster, or ESXi server within the {{site.data.keyword.CloudDataCent_notm}}.

**Availability:** This service is available only to instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.3 or later releases.

You can order an instance with the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service included. For more information, see:
* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)

You can also deploy the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service into your existing instances after initial deployment. For more information, see:
* [Ordering and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)

## Components of HyTrust CloudControl on IBM Cloud

A highly available (HA) pair of HyTrust CloudControl (HTCC) appliances is deployed on the default cluster. Each pair of HTCC appliances is deployed on the same private portable subnet that is specified for the management virtual machines (VMs), such as NSX Manager, vCenter Server Appliances, and Platform Services Controller.  

## Considerations when removing HyTrust CloudControl on IBM Cloud

Before you remove the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service, ensure that you disable **Root Password Vaulting**, if configured, and that you delete all protected hosts from CloudControl.

## Related links

* [Managing HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust website](https://www.hytrust.com/)
