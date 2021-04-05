---

copyright:

  years:  2016, 2021

lastupdated: "2021-03-29"

keywords: Caveonix, Caveonix RiskForesight, tech specs Caveonix

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight overview
{: #caveonix_considerations}

The Caveonix RiskForesight™ service can help to manage cyberrisk and compliance risk with proactive monitoring and automated defense controls to protect against threats and to meet industry or government regulations.
{: shortdesc}

Caveonix RiskForesight supports vCenter Server multizone instances. For more information, see [Ordering vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_ordering).

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

The current Caveonix RiskForesight version that is installed is 2.4.
{:note}

A Caveonix RiskForesight license is valid for five years. Ordering Caveonix RiskForesight for VMware vCenter Server instances, VMware Regulated Workloads, and Security and Compliance Readiness Bundle instances differs. For more information, see [Licenses and fees](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations#caveonix_considerations-tech-specs-license-fee).

## Technical specifications for Caveonix RiskForesight
{: #caveonix_considerations-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

The following components are ordered and included in the Caveonix RiskForesight service.

### vCenter resources
{: #caveonix_considerations-tech-specs-vcenter}

* CPU - 8 vCPU
* RAM - 32 GB
* Disk - 100 GB

### Network
{: #caveonix_considerations-tech-specs-network}

A dedicated private subnet with 32 IP addresses is ordered.

### Licenses and fees
{: #caveonix_considerations-tech-specs-license-fee}

A Caveonix RiskForesight license key is ordered for each instance of the service.

If you order Caveonix RiskForesight for a VMware Regulated Workloads or Security and Compliance Readiness Bundle instance, you are charged for a per-host license for every host on the instance. This is new in Version 4.1. However, you are not charged for per-VM licenses.

If you order Caveonix RiskForesight for a VMware vCenter Server instance, you are charged for the number of per-VM licenses that you choose at install time. This is how you were charged for Caveonix RiskForesight in previous releases. You can select 10 - 25,000 VMs to license.

If you order Caveonix RiskForesight for a VMware Regulated Workloads or VMware Security and Compliance Readiness Bundle instance, the host-based licenses are hidden. Caveonix RiskForesight is deployed with a 25,000 VM key. You do not need to upgrade.

Caveonix RiskForesight licenses that are ordered separately from the Resources page are not per-host. Because of this, you should not order new Caveonix RiskForesight licenses and apply the key to your Caveonix RiskForesight service on Regulated Workloads or Security and Compliance Readiness Bundle instances. Doing so will:

• Provide less coverage than when the license was initially deployed
• Result in you being charged twice for Caveonix RiskForesight licenses because your initial license cannot be canceled. Therefore, you would pay for both per-host and per-VM licensing.

You can still order Caveonix RiskForesight licenses for other types of instances, for example, for VMware vServer Center instances.

## Considerations when you delete Caveonix RiskForesight
{: #caveonix_considerations-remove}

Review the following considerations before you delete the service:

* Deleting Caveonix RiskForesight automatically deletes the initial Caveonix RiskForesight license originally associated with the service. However, you need to manually delete any other unwanted licenses from the **Caveonix RiskForesight Licenses** table on the **Resources** page in the IBM Cloud for VMware Solutions console.
* When you delete the service, the {{site.data.keyword.vmwaresolutions_short}} automation deletes only the single all-in-one Caveonix virtual machine (VM) that was deployed and the dedicated private subnet that was ordered for it. Therefore,
   * If you scaled out the Caveonix VM into multiple VMs, those additional VMs are not deleted.
   * If you used the IP addresses of the dedicated private subnet on more VMs, those VMs must be assigned new IP addresses to continue to function.
   * If you delete the **vCenter Server® instance A** with Caveonix RiskForesight installed, and you used the IP addresses of the dedicated private subnet that was ordered for the service in the **vCenter Server instance B**, the dedicated private subnet is canceled upon deletion of the **vCenter Server instance A**.
* If you installed the Caveonix RiskForesight service before VMware Solutions v4.0 and you then delete that service, you must manually remove the DNS entries. For more information, see [Manually removing the DNS entries](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-remove-DNS-entries).

## Related links
{: #caveonix_considerations-related}

* [Ordering Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_ordering)
* [Managing Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-managingcaveonix)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
