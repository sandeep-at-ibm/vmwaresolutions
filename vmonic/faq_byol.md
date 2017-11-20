---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-10"

---

# FAQ about BYOL

Find answers to the questions that you might have about Bring Your Own License (BYOL).

## What is BYOL for Cloud Foundation instances?

Bring Your Own License, which is known as BYOL, is a feature available to Cloud Foundation instances in V1.8 and later releases and to vCenter Server and vSphere instances in V2.0 and later that in V1.8 and later releases that allows you to use your own VMware licenses for one or more of the following VMware components when ordering vCenter Server and Cloud Foundation instances:
* vCenter Server
* vSphere
* vSAN
* NSX

If you select to use your own license for a VMware component and provide a valid license key for it, no license is ordered from IBM for this component and no monthly license charges are incurred to your {{site.data.keyword.cloud_notm}} infrastructure account for this component.

## What license editions and CPU quantities are required for BYOL?

The following vCenter Server requirements apply for all edition, standard, advanced, and enterprise and CPU of the VMware components licenses for BYOL. For V2.0 and later releases,  vCenter only supports vSAN Advanced and Enterprised edition.

  | VMware Component License        | Minimum License Edition Required       | Minimum CPU Required
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard | N/A |
  | vSphere | Enterprise Plus | 8 CPUs |
  | vSAN | Advanced or Enterprise | 8 CPUs |
  | NSX | Standard, Advanced, or Enterprise | 8 CPUs |

  The following requirements apply for the edition and CPU of the VMware components licenses for BYOL. For V2.0 and later releases,  vCenter only supports vSAN Advanced and Enterprised edition. For NSX, Cloud Foundation only supports Enterprise edition.

  | VMware Component License        | Minimum License Edition Required       | Minimum CPU Required
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard | N/A |
  | vSphere | Enterprise Plus | 8 CPUs |
  | vSAN | Advanced or Enterprise | 8 CPUs |
  | NSX | Enterprise | 8 CPUs |

## What happens if the license key I provided is not correct?

All the license keys you provided are validated to ensure that they are proper for the corresponding VMware components and that they meet the minimum edition and CPU requirements of the VMware components. If the validation of any license key fails, you get notification and you cannot proceed with the vCenter Server or Cloud Foundation instance order.

## Can I provide a license key with more than 8 CPUs?

Yes. For each VMware component, one license per CPU is required. Currently, all vCenter Server and Cloud Foundation servers have two CPUs, therefore, two licenses are required for each server. It is encouraged that you provide a license key that can support the base instance and any expansion nodes that you want to add to the vCenter Server and Cloud Foundation instance in future.

## Can I provide SDDC Manager license when BYOL?

No. Our agreement with VMware requires that we must accept a client’s actual license key. Although the Cloud Foundation deployment includes SDDC Manager licenses, there are no SDDC Manager license key files that we can accept and validate for BYOL. Therefore, SDDC Manager licenses are charged by IBM for all s.  SDDC Manager licenses are $180/server, which represents a very small portion of the overall license charges for a vCenter Server and Cloud Foundation instance.

## Can I BYOL for some VMware components and purchase monthly licenses for others?

Yes. You can BYOL or purchase licenses for any combination of the four VMware components. The {{site.data.keyword.vmwaresolutions_full}} console makes it straightforward for you to select the licensing option when you order the vCenter Server or Cloud Foundation instance. Your licensing option at the time of initial vCenter Server or Cloud Foundation instance order applies for the lifetime of that instance.

## For one VMware component, can I BYOL a partial quantity of licenses and buy the rest of licenses from IBM?

No. The licensing system of VMware does not permit licenses from two different accounts to be mixed and merged. Therefore, when you are ordering a vCenter Server or Cloud Foundation instance, all the licenses for a single VMware component must be either all BYOL or all purchased. Your licensing choice applies for the lifetime of the instance.

## Can I BYOL licenses for the  vCenter Server or Cloud Foundation initial instance (4 ESXi servers) and then purchase licenses from IBM when I add more ESXi servers to the instance later?

No. The licensing system of VMware does not permit licenses from two different accounts to be mixed and merged. Therefore, when you are ordering a vCenter Server or Cloud Foundation instance, all the licenses for a single VMware component must be either all BYOL or all purchased. Your licensing choice applies for the lifetime of the instance.

## How to manage my BYOL licenses?

You can manage your BYOL licenses by using the VMware vSphere Web Client after the  vCenter Server or Cloud Foundation instance deployment is completed.

## When I add more ESXi servers to my vCenter Server and Cloud Foundation instance later, does the instance validate whether the quantity of my BYOL licenses is sufficient?

Yes. When you are adding more ESXi servers to a deployed vCenter Server or Cloud Foundation instance, the capacity of your BYOL licenses is automatically checked for the specified number of ESXi servers. If the capacity is not sufficient, the ESXi servers are not added and you get a console notification.

## Does IBM provide support if I selected the BYOL licensing option?

IBM Support continues to be your point of contact for any vCenter Server or Cloud Foundation instance concerns. However, if the reported concern is determined to be for a BYOL VMware component, you are directed to VMware support.

## Why do vSphere license charges show up on the price estimation list when I already BYOL for it? Am I still being charged for it?

Today, bare metal servers are provisioned with vSphere already installed and with vSphere licenses already included. If you selected BYOL for vSphere, a process is automatically initiated upon a vCenter Server or Cloud Foundation instance deployment to remove the included vSphere licenses, and then the license charges are credited to your {{site.data.keyword.cloud_notm}} infrastructure account. You do not have to do anything in this process.

## Can I still use the existing manual process for BYOL?

With the introduction of the new BYOL feature, continued use of the manual process is discouraged. If you want to BYOL, provide your own licenses when you are ordering the vCenter Server or Cloud Foundation instance.

## Is BYOL supported for other VMware products such as VMware vRealize Automation, VMware vRealize Operations, and VMware vRealize Log Insight?

No, because these VMware products are not part of the vCenter Server or Cloud Foundation deployment today. These VMware products might be installed on top of the vCenter Server or Cloud Foundation deployment, which requires the clients or their agents to perform the installation and licensing.

## Related links

* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html)
* [Accessing the console](loginmethod.html)
* [Contacting IBM Support](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
