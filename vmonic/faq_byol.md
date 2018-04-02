---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-19"

---

# FAQ about BYOL and licensing

Find answers to frequently asked questions about licensing, including the Bring Your Own License (BYOL) feature of {{site.data.keyword.vmwaresolutions_full}}.

## Where do I manage the licenses and components ordered through VMware vSphere on IBM Cloud?

After an order to create a new cluster for VMware vSphere on {{site.data.keyword.cloud_notm}} is placed, the VMware licenses, ESXi servers, and other networking components, are delivered and can be managed from the {{site.data.keyword.slportal}}.

After deployment, go to the {{site.data.keyword.vmwaresolutions_short}} console to scale the new cluster using the saved configuration. For more information on scaling, see [Scaling existing vSphere clusters](../vsphere/vs_scalingexistingclusters.html).

## What is BYOL?

Bring Your Own License, or BYOL, is a feature available to VMware Cloud Foundation instances in V1.8 and later releases, and to VMware vCenter Server and VMware vSphere instances in V2.0 and later releases. BYOL allows you to use your own VMware licenses for one or more of the following VMware software components when ordering instances:
* VMware vCenter Server
* VMware vSphere
* VMware vSAN
* VMware NSX

If you select to use your own license for a VMware component and provide a valid license key for it, no license is ordered from IBM for this component and no monthly license charges are incurred to your {{site.data.keyword.cloud_notm}} account for this component.

## What license editions and CPU quantities are required for BYOL?

The following requirements apply to the license editions for BYOL.

### BYOL requirements for vCenter Server instances

Table 1. License editions and CPU minimum requirements for vCenter Server instances

  | VMware component | License edition required | Minimum CPU required
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard                | N/A |
  | vSphere        | Enterprise Plus | 8 CPUs |
  | vSAN           | Advanced or Enterprise | 8 CPUs |
  | NSX            | Standard, Advanced, or Enterprise | 8 CPUs |

### BYOL requirements for Cloud Foundation instances

Table 2. License editions and CPU minimum requirements for Cloud Foundation instances

  | VMware component | License edition required | Minimum CPU required
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard | N/A |
  | vSphere        | Enterprise Plus | 8 CPUs |
  | vSAN           | Advanced or Enterprise | 8 CPUs |
  | NSX            | Enterprise | 8 CPUs |

## What happens if the license key I provided is not correct?

All the license keys that you provide are validated to ensure that they are correct for the corresponding VMware components and that they meet the minimum edition and CPU requirements of the VMware components. If the validation of any license key fails, you get a notification and you cannot proceed with the instance order.

## Can I provide a license key with more than 8 CPUs?

Yes. For each VMware component, one license per CPU is required. Currently, all vCenter Server and Cloud Foundation servers have two CPUs, therefore, two licenses are required for each server. It is recommended that you provide a license key that can support the base instance and any expansion nodes that you want to add to the instance in the future.

## Can I provide the SDDC Manager license when using the BYOL feature?

No. Our agreement with VMware requires that we must accept a client’s actual license key. Although the Cloud Foundation deployment includes SDDC Manager licenses, there are no SDDC Manager license key files that we can accept and validate for BYOL. Therefore, SDDC Manager licenses are charged by IBM for all instances. SDDC Manager licenses represent a very small portion of the overall license charges for a Cloud Foundation instance.

## Can I use the BYOL feature for some VMware components and purchase monthly licenses for others?

Yes. You can use the BYOL feature or purchase licenses for any combination of the four VMware components. The {{site.data.keyword.vmwaresolutions_short}} console makes it straightforward for you to select the licensing option when you order the vCenter Server or Cloud Foundation instance. Your licensing option at the time of initial instance order applies for the lifetime of that instance.

## For a specific VMware component, can I use BYOL for some licenses and buy the rest of licenses from IBM?

Yes. If you selected BYOL for a specific VMware component, you have the option when creating a new cluster to enter a new BYOL key, continue using an existing BYOL key, or purchase IBM-provided licensing for that cluster.  At this time, only VMware vSphere Enterprise and VMware vSAN are availible for licensing per cluster.

## Can I use BYOL when creating a new cluster?

Yes. You can BYOL from existing BYOL licenses or enter new BYOL when creating a new cluster. You will also have the option to purchase an IBM-provided subscription license when creating a new cluster. At this time, only VMware vSphere Enterprise and VMware vSAN are available for licensing per cluster.

## How can I manage my BYOL licenses?

You can manage your BYOL licenses by using the VMware vSphere Web Client after the instance deployment is completed.

## When I add more ESXi servers to my instance later, does the instance validate whether the capacity of my BYOL licenses is sufficient?

Yes. When you are adding more ESXi servers to a deployed instance, the capacity of your BYOL licenses is automatically checked for the specified number of ESXi servers. If the capacity is not sufficient, the ESXi servers are not added and you get a console notification.

## How can I tell how much license capacity I have available on a cluster with BYOL?

You can find the number of CPUs available in your license key by going to the **Deployed Instances**, **Infrastructure** section, selecting the instance and then the cluster that you want to check the license capacity.  The number of available CPUs is listed in the **User-Provided License** table.

## Does IBM provide support if I select the BYOL licensing option?

IBM Support continues to be your point of contact for any instance configuration concern. However, if the reported concern is determined to be for a BYOL VMware component, you are directed to VMware Support.

## Why do vSphere license charges show up on the price estimation list if I am using BYOL? Am I being charged for it?

{{site.data.keyword.baremetal_short}} are provisioned with vSphere already installed and with vSphere licenses already included. If you selected BYOL for vSphere, a process is automatically initiated upon instance deployment to remove the included vSphere licenses. Then the license charges are credited to your {{site.data.keyword.cloud_notm}} account. You do not have to do anything in this process.

## Can I still use the existing manual process for BYOL?

With the introduction of the BYOL feature, continued use of the manual process is not recommended. If you want to use BYOL, provide your own licenses when you are ordering the instance.

## Is BYOL supported for other VMware products such as VMware vRealize Automation, VMware vRealize Operations, or VMware vRealize Log Insight?

No, because these VMware products are not part of the instance deployment. These VMware products might be installed on top of the initial deployment, which requires the clients or their agents to perform the installation and licensing.

## Related links

* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html)
* [Accessing the console](loginmethod.html)
* [Contacting IBM Support](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
