---

copyright:

  years:  2020

lastupdated: "2020-02-17"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Virtual Data Center instances
{: #shared_ordering}

{{site.data.keyword.vmwaresolutions_full}} Shared offers either a standardized or customizable deployment option of VMware Virtual Data Center environments. Choose the On-Demand or Reserved option.

## System settings
{: #shared_ordering-sys-settings}

You must specify the following system settings when you order a VMware Solutions Shared Virtual Data Center instance.

### Pricing Plan
{: #shared_ordering-pricing}

The pricing plan is based on your selection of **On-Demand** or **Reserved**.

#### On-Demand
{: #shared_ordering-pricing-on-demand}

For the On-Demand offering, Virtual Data Center vCPU and RAM are allocated as needed. The amount of time that the allocation takes depends on global usage of the Virtual Data Center vCPU and RAM.

* The limits that are established for the amount of vCPU and RAM are maximum values that can be used at any time.
* vCPU and RAM resources can be increased and decreased later as required.
* The cost is calculated hourly and it is based on the resource usage in the Virtual Data Center.
* There are no limits on the amount of storage that can be allocated and used in the Virtual Data Center. Charges are hourly based on GB of allocated storage.
* There are no limits on the amount of inbound and outbound public networking. Public outbound bandwidth is charged per GB.

#### Reserved
{: #shared_ordering-pricing-reserved}

For the Reserved offering, the vCPU and RAM Virtual Data Center reservations are pre-allocated and their availability is guaranteed.

* The cost is calculated monthly for the full reservation and it is based on the allocation size of the Virtual Data Center.
* vCPU and RAM resources can be increased and decreased later as required.
* There are no limits on the amount of storage that can be allocated and used in the Virtual Data Center. Charges are hourly based on GB of allocated storage.
* There are no limits on the amount of inbound and outbound public networking. Public outbound bandwidth is charged per GB.

For more information, see [VMware Solutions Shared pricing](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_pricing).

### Virtual Data Center Name
{: #shared_ordering-inst-name}

The Virtual Data Center name must be under 125 characters.

## Location settings
{: #shared_ordering-dc}

Select the IBM Cloud Data Center where the instance is to be hosted.

## CPU Model settings
{: #shared_ordering-cpu}

CPU model settings are based on your selection of a **On-Demand** or **Reserved** pricing plan.

If you selected **On-Demand**, select the CPU and RAM limits.

If you selected **Reserved**, your CPU model settings are based on your selection of **Preconfigured** or **Custom**.
* If you selected **Preconfigured**, you have the following options for allocated vCPU and RAM limits.

| Size    | vCPU      | RAM      |
|:------- |:-------- |:------ |
| Small | 64 cores | 512 GB |
| Medium | 128 cores | 1024 GB |
| Large | 256 cores | 2048 GB |
{: caption="Table 1. Preconfigured vCPU and RAM options" caption-side="top"}

* If you selected **Custom**, you can customize your allocated vCPU and RAM limits.

## Recommend Services
{: #shared_ordering-services}

The Veeam Availability Suite and Veeam Cloud Connect Replication services are preinstalled and ready-to-use in all Virtual Data Center instances. Service charges are incurred only if you choose to use the service.

For more information, see [Managing Veeam for VMware Solutions Shared instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_veeam).

## Summary
{: #shared_ordering-summary}

Based on your selected configuration for the Virtual Data Center instance, the estimated cost is instantly generated and displayed in the **Summary** right pane. Click **Pricing details** to generate a PDF document with the cost summary for the VMware Solution Shared resources.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. The tool is useful if you want to estimate the cost of the selected VMware Solutions Shared resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

## Procedure to order VMware Solutions Shared On-Demand
{: #shared_ordering-procedure-ondemand}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. In the **Start Provisioning** section, click the **VMware Solutions Shared** card.
3. On the **Create** tab of the **VMware Solutions Shared** page, select **On-Demand**.
4. Enter the Virtual Data Center name.
5. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
6. Select the vCPU and RAM limits according to your requirements.
6. On the **Summary** pane, verify the configuration and estimated cost before you place the order.
7. Click **Create**.

## Procedure to order VMware Solutions Shared Reserved
{: #shared_ordering-procedure-reserved}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. In the **Start Provisioning** section, click the **VMware Solutions Shared** card.
3. On the **Create** tab of the **VMware Solutions Shared** page, select **Reserved**.
4. Enter the Virtual Data Center name.
5. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.
6. Complete the resource reservation.
  * If you select **Preconfigured**, select the preconfigured vCPU model and RAM size.
  * If you select **Custom**, specify the vCPU and RAM limits according to your requirements.
7. On the **Summary** pane, verify the configuration and estimated cost before you place the order.
8. Click **Create**.

## Results after you order VMware Shared Solution
{: #shared_ordering-results}

* The deployment of the resources starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Virtual Data Center Status**.
* When the resources are successfully deployed, the components that are described in [Technical specifications for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview#shared_overview-specs) are installed on your VMware virtual platform.
* When the resources are ready to use, the status is changed to **Ready to Use**.

## What to do next
{: #shared_ordering-next}

View the Virtual Data Center instance that you ordered and reset the **admin** password for the vCloud Director Management console. For more information, see [Viewing and managing Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing).

## Related links
{: #shared_ordering-related}

* [Viewing and managing Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [VMware Solutions Shared overview](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview)
* [Requirements and planning for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_planning)
* [Operating VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_vcd-ops-guide)
* [Managing Veeam for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_veeam)
* [Resizing Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_resizeinstance)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
