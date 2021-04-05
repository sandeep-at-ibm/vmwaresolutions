---

copyright:

  years:  2016, 2021

lastupdated: "2021-03-17"

keywords: FAQ, license, BYOL

subcollection: vmwaresolutions

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}

# FAQ about licensing and Bring Your Own License
{: #faq_byol}

Find answers to frequently asked questions about licensing, including the Bring Your Own License (BYOL) feature of {{site.data.keyword.vmwaresolutions_full}}.

## Where to manage the licenses and components that are ordered through VMware vSphere?
{: #faq_byol-license-mgmt}
{: faq}

After an order to create a new cluster for VMware® vSphere® is placed, the VMware licenses, ESXi servers, and other networking components, are delivered and can be managed from the {{site.data.keyword.slportal}}.

After deployment, go to the {{site.data.keyword.vmwaresolutions_short}} console to scale the new cluster by using the saved configuration. For more information, see [Scaling existing vSphere clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_scalingexistingclusters).

## What happens if the license key you provided is not correct?
{: #faq_byol-incorrect-license}
{: faq}

All license keys that you provide are validated to ensure that:
* They are correct for the corresponding VMware components and
* They meet the minimum edition and CPU requirements of the VMware components.

If the validation of any license key fails, you get a notification and you cannot proceed with the instance order.

## Can you provide a license key with more than 8 CPUs?
{: #faq_byol-license-key}
{: faq}

Yes. For each VMware component, one license per CPU is required. Currently, all VMware vCenter Server® servers have two CPUs. Therefore, two licenses are required for each server. It is recommended that you provide a license key that can support the base instance and any expansion nodes that you want to add to the instance in the future.

## Why is there a discrepancy in the supported number of VMs for vROPs licenses?
{: #faq_byol-vrops}
{: faq}

You might see a discrepancy in the supported number of VMs between what displays on the vRealize Operations Manager console and the per-CPU metering in {{site.data.keyword.cloud_notm}}. This issue happens if you did not select the **Product evaluation (no key required)** option when you first accessed the vROps Manager console after service installation. For more information, see [Accessing the vRealize Operations Manager console](/docs/vmwaresolutions?topic=vmwaresolutions-managing_vrops#managing_vrops-access-vrops-console).

This discrepancy is a result of vROps keys that are created for {{site.data.keyword.cloud_notm}} subscription licensing include a virtual machine (VM) capacity, however {{site.data.keyword.cloud_notm}} meters and bills the vROps license per CPU, and not per VM.

The discrepancy does not indicate any service or licensing problem. The vRealize Operations and Log Insight service is fully licensed for all VMs on each vCenter Server host and continues to work properly.

## What is BYOL and is it supported for VMware perpetual licenses?
{: #faq_byol-def}
{: faq}
{: support}

BYOL is a feature available to VMware vCenter Server® and VMware vSphere clusters in V2.0 and later. With BYOL, you can use your own VMware licenses for one or more of the following VMware software components.
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

If you choose to use your own license for a VMware component and provide a valid license key for it, no license is ordered from IBM for this component. In addition, no monthly license charges are incurred to your {{site.data.keyword.cloud}} infrastructure account for this component.

The BYOL feature is not available to Business Partner users.
{:note}

## What license editions and CPUs are required for BYOL for vCenter Server instances?
{: #faq_byol-license-cpu-reqs}
{: faq}

The minimum number of licenses for BYOL that are required depends on the number of CPUs per server and the number of servers in the order. For example, the CPU requirements based on four servers with 2 CPUs per server is 8 CPUs.

## Can you use the BYOL feature for some VMware components and purchase monthly licenses for others?
{: #faq_byol-mthly-license}
{: faq}

Yes. You can use the BYOL feature or purchase licenses for any combination of the four VMware components. The {{site.data.keyword.vmwaresolutions_short}} console makes it straightforward for you to select the licensing option when you order your instance. Your licensing option at the time of initial instance order applies for the lifetime of that instance.

## For a specific VMware component, can you use BYOL for some licenses and buy the rest of licenses from IBM?
{: #faq_byol-purchase}
{: faq}

Yes. If you selected BYOL for a specific VMware component when you create a cluster, you have the following options:
* Enter a new BYOL key.
* Continue to use an existing BYOL key.
* Purchase IBM-provided licensing for that cluster.

Currently, only VMware vSphere Enterprise and VMware vSAN can be licensed per cluster.

You cannot mix and match BYOL and IBM-provided licensing for any VMware component within a cluster.
{:note}

## Can you use BYOL when you create a cluster?
{: #faq_byol-cluster}
{: faq}

Yes. You can BYOL from existing BYOL licenses or enter a new BYOL when you create a cluster. Also, you can purchase an IBM-provided subscription license when you create a cluster.

Currently, only VMware vSphere Enterprise and VMware vSAN can be licensed per cluster.

## How do you manage BYOL licenses?
{: #faq_byol-mgmt}
{: faq}

You can manage your BYOL licenses by using the VMware vSphere web client after the instance deployment is completed.

## When you add more ESXi servers to an instance later, does the instance validate if the BYOL licenses have enough capacity?
{: #faq_byol-add-esxi}
{: faq}

Yes. When you're adding more ESXi servers to a deployed instance, the capacity of your BYOL licenses is automatically checked for the specified number of ESXi servers. If the capacity is not sufficient, the ESXi servers are not added and you get a console notification.

## How can you tell how much license capacity you have available on a cluster with BYOL?
{: #faq_byol-capacity}
{: faq}

To find the number of CPUs available in your license key, complete the following steps:
1. In the VMware Solutions console, click **Resources** from the left navigation pane.
2. Locate and click the instance.
3. On the **Infrastructure** tab, click the cluster that you want to check the license capacity for.
   The number of available CPUs is listed in the **User-provided license** table.

## Does IBM provide support if you select the BYOL licensing option?
{: #faq_byol-support}
{: faq}

IBM Support continues to be your point of contact for any instance configuration concern. However, if the reported concern is determined to be for a BYOL VMware component, you are directed to VMware Support.

## Why are vSphere license charges displayed on the price estimation list if you are using BYOL? Is there a cost for them?
{: #faq_byol-vsphere}
{: faq}

{{site.data.keyword.cloud_notm}} bare metal servers are provisioned with VMware vSphere installed and with vSphere licenses included. If you selected BYOL for vSphere, a process is automatically initiated upon instance deployment to remove the included vSphere licenses. As part of this process, after you install your BYOL licenses, they are verified. Upon verification and confirmation, the included vSphere license charges are credited to your {{site.data.keyword.cloud_notm}} account.

## Can you still use the existing manual process for BYOL?
{: #faq_byol-manual-process}
{: faq}

With the introduction of the BYOL feature, continued use of the manual process is not recommended. If you want to use BYOL, provide your own licenses when you are ordering the instance.

## Related links
{: #faq_byol-related}

* [Accessing the console](/docs/vmwaresolutions?topic=vmwaresolutions-loginmethod)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
