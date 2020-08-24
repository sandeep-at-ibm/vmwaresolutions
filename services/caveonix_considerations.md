---

copyright:

  years:  2016, 2020

lastupdated: "2020-08-21"

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

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

The current Caveonix RiskForesight version that is installed is 2.3.
{:note}

## Technical specifications for Caveonix RiskForesight
{: #caveonix_considerations-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

The following components are ordered and included in the Caveonix RiskForesight service.

### vCenter resources
{: #caveonix_considerations-tech-specs-vcenter}

* CPU: 8 vCPU
* RAM: 32 GB
* Disk: 100 GB

### Network
{: #caveonix_considerations-tech-specs-network}

A dedicated private subnet with 32 IP addresses is ordered.

### Licenses and fees
{: #caveonix_considerations-tech-specs-license-fee}

A Caveonix RiskForesight license key is ordered for each instance of the service.

## Considerations when you delete Caveonix RiskForesight
{: #caveonix_considerations-remove}

Review the following considerations before you delete the service:
* Deleting the Caveonix RiskForesight service does not cancel the Caveonix RiskForesight license. You must delete the Caveonix RiskForesight license from the **Caveonix RiskForesight Licenses** table on the **Resources** page in the {{site.data.keyword.vmwaresolutions_short}} console.
* When you delete the service, the {{site.data.keyword.vmwaresolutions_short}} automation deletes only the single "all-in-one" Caveonix virtual machine (VM) that was deployed and the dedicated private subnet that was ordered for it. Therefore,
   * If you scaled out the Caveonix VM into multiple VMs, those additional VMs are not deleted.
   * If you used the IP addresses of the dedicated private subnet on more VMs, those VMs must be assigned new IP addresses to continue to function.
   * If you delete the **vCenter Server® instance A** with Caveonix RiskForesight installed, and you used the IP addresses of the dedicated private subnet that was ordered for the service in the **vCenter Server instance B**, the dedicated private subnet is canceled upon deletion of the **vCenter Server instance A**.

## Related links
{: #caveonix_considerations-related}

* [Ordering Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_ordering)
* [Managing Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-managingcaveonix)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
