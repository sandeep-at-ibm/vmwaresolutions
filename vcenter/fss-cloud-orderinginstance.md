---

copyright:

  years:  2020

lastupdated: "2020-07-13"

keywords: vmware regulated workloads order instance, order vmware regulated workloads, order regulated workloads instance

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering IBM Cloud for VMware Regulated Workloads instances
{: #fss-cloud-orderinginstance}

IBM Cloud for VMware® Regulated Workloads are an extension of the vCenter Server - Dedicated offering. These instances are defined based on specific components and settings of vCenter Server instances.

## Requirements for IBM Cloud for VMware Regulated Workloads instances
{: #fss-cloud-orderinginstance-req}

For more information, see [Requirements for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-req).

## Instance configurations
{: #fss-cloud-orderinginstance-inst-config}

The following instance configurations are available:
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package A
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package A (BYOL)
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package B
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package B (BYOL)
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Configurable

For more information, see [{{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instance configurations](/docs/vmwaresolutions?topic=vmwaresolutions-fss-cloud-vmware-config).

## Procedure to order IBM Cloud for VMware Regulated Workloads instances
{: #fss-cloud-orderinginstance-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. In the **Start Provisioning** section, click the **VMware Solutions Dedicated** card.
3. On the **VMware Solutions Dedicated** page, click the **vCenter Server** card. Ensure that you are on the **Single-zone cluster** tab.
4. From the **Instance configurations** list, select one of the instance configurations that starts with **IBM Cloud for VMware Regulated Workloads**. For more information, see [{{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instance configurations](/docs/vmwaresolutions?topic=vmwaresolutions-fss-cloud-vmware-config).
5. Continue to specify the settings for your instance order. For more information, see [Procedure to order vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure).

  Available options might differ depending on the {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instance configuration that you selected.
  {:note}

### Results after you place an order
{: #fss-cloud-orderinginstance-results-order}

The deployment of the instance starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Deployment history** section of the instance details.

When the instance is successfully deployed, the components that are described in [{{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instance configurations](/docs/vmwaresolutions?topic=vmwaresolutions-fss-cloud-vmware-config) are installed on your VMware virtual platform. The deployment of the services starts after your order is completed.

When the instance is ready to use, the status of the instance is changed to **Ready to use** and you receive a notification by email.

When you order a secondary instance, the VMware vSphere® Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.

Next, you can view and manage the {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instance that you ordered.

You must manage the {{site.data.keyword.vmwaresolutions_short}} components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the	{{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console.
{:important}

**CAUTION:** Managing any {{site.data.keyword.vmwaresolutions_short}} components (which were installed into your {{site.data.keyword.cloud_notm}} account	 when you ordered the instance) from outside the {{site.data.keyword.vmwaresolutions_short}} console can make your environment unstable. These management activities include:
*  Adding, modifying, returning, or removing components
*  Expanding or contracting instance capacity through adding or removing ESXi servers
*  Powering off components
*  Restarting services

   Exceptions to these activities include managing the shared storage file shares from the 	{{site.data.keyword.slportal}}. Such activities include: ordering, deleting (which might impact data stores if mounted), authorizing, and mounting shared storage file shares.

## Related links
{: #fss-cloud-orderinginstance-related}

* [{{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instance configurations](/docs/vmwaresolutions?topic=vmwaresolutions-fss-cloud-vmware-config)
* [Signing up for an {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-signing_required_accounts#signing_required_accounts-cloud)
* [{{site.data.keyword.cloud_notm}} for VMware Regulated Workloads reference architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-fss-overview)
* [Deleting vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_deletinginstance)
