---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-10"

keywords: Caveonix, Caveonix RiskForesight, tech specs Caveonix

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight overview
{: #caveonix_considerations}

The Caveonix RiskForesight service can help to manage cyberrisk and compliance risk with proactive monitoring and automated defense controls to protect against threats and to meet industry or government regulations.
{: shortdesc}

The current Caveonix RiskForesight version that is installed is 2.3.
{:note}

## Technical specifications for Caveonix RiskForesight
{: #caveonix_considerations-specs}

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
* Deleting the Caveonix RiskForesight service does not cancel the Caveonix RiskForesight license. You must delete the Caveonix RiskForesight license from the **Caveonix RiskForesight Licenses** table on the **Resources** page in the {{site.data.keyword.vmwaresolutions_full}} console.
* When you delete the service, the {{site.data.keyword.vmwaresolutions_short}} automation deletes only the single "all-in-one" Caveonix VM that was deployed and the dedicated private subnet that was ordered for it. Therefore,
   * If you scaled out the Caveonix VM into multiple VMs, those additional VMs are not deleted.
   * If you used the IP addresses of the dedicated private subnet on more VMs, those VMs must be assigned new IP addresses to continue to function.
   * If you delete the **vCenter Server instance A** with Caveonix RiskForesight installed, and you used the IP addresses of the dedicated private subnet that was ordered for the service in the **vCenter Server instance B**, the dedicated private subnet is canceled upon deletion of the **vCenter Server instance A**.

## Related links
{: #caveonix_considerations-related}

* [Ordering Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_ordering)
* [Managing Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-managingcaveonix)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
