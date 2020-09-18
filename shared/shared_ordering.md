---

copyright:

  years:  2020

lastupdated: "2020-09-16"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Ordering virtual data center instances
{: #shared_ordering}

{{site.data.keyword.vmwaresolutions_full}} Shared offers either a standardized or customizable deployment option of VMware® virtual data center environments. Choose the On-demand or Reserved option.

## Requirements for virtual data center instances
{: #shared_ordering-reqs}

If you are ordering an instance for the first time, ensure that you completed the tasks in the **Before you begin** section on the ordering page. For more information, see [Setting up your environment for your first order](/docs/vmwaresolutions?topic=vmwaresolutions-completing_checklist).

## System settings
{: #shared_ordering-sys-settings}

You must specify the following system settings when you order a VMware Solutions Shared virtual data center instance.

### Pricing plans
{: #shared_ordering-pricing}

The pricing plan is based on your selection of **On-demand** or **Reserved**.

#### On-demand
{: #shared_ordering-pricing-on-demand}

For the On-demand offering, virtual data center virtual CPU (vCPU) and RAM are allocated as needed. The amount of time that the allocation takes depends on global usage of the virtual data center vCPU and RAM.

* The limits that are established for the amount of vCPU and RAM are maximum values that can be used at any time.
* vCPU and RAM resources can be increased and decreased later as required.
* The price is calculated hourly and it is based on the resource usage in the virtual data center.
* The amount of storage that can be allocated and used in the virtual data center is limited to 200 TB for each storage policy. Charges are hourly based on GB of allocated storage.
* The amount of inbound and outbound public networking is unlimited. Public outbound bandwidth is charged per GB.

#### Reserved
{: #shared_ordering-pricing-reserved}

For the Reserved offering, the vCPU and RAM virtual data center reservations are pre-allocated and their availability is guaranteed.

* The price is calculated monthly for the full reservation and it is based on the allocation size of the virtual data center.
* vCPU and RAM resources can be increased and decreased later as required.
* The amount of storage that can be allocated and used in the virtual data center is unlimited. Charges are hourly based on GB of allocated storage.
* The amount of inbound and outbound public networking is unlimited. Public outbound bandwidth is charged per GB.

For more information, see [VMware Solutions Shared pricing](/docs/vmwaresolutions?topic=vmwaresolutions-shared_pricing).

### Virtual data center name
{: #shared_ordering-inst-name}

The virtual data center name is set to **vdc-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify a virtual data center name that meets the following requirements:
* The maximum length is 128 characters.
* Only alphanumeric, dash (-), and underscore (_) characters are allowed.
* The name must be unique within all active virtual data centers in your account. You can create a virtual data center that has the same name as a previously deleted virtual data center.

### Resource group
{: #shared_ordering-resource-group}

Use resource groups to organize the resources in your account for access control and billing purposes. The default resource group in your account is selected by default. You can also select another resource group according to your needs. The resource group that you select cannot be changed after the instance is created.

If **No resource group available** is displayed in this field, you currently do not have the permission to add the instance to any resource group in this account. Contact the account owner to be assigned an Editor or Administrator role on a resource group in the account. For more information, see [IAM access](/docs/account?topic=account-userroles).

### Data center location
{: #shared_ordering-dc}

Select the {{site.data.keyword.cloud}} data center where the instance is to be hosted.

## Virtual data center capacity
{: #shared_ordering-cpu}

Virtual data center capacity is based on your selection of the **On-demand** or **Reserved** pricing plan.

If you selected **On-demand**, select the vCPU and RAM limits.

If you selected **Reserved**, your vCPU model settings are based on your selection of **Preconfigured** or **Custom**.

If you selected **Preconfigured**, you have the following options for allocated vCPU and RAM limits.

| Size    | vCPU      | RAM      |
|:------- |:-------- |:------ |
| Small | 64 cores | 512 GB |
| Medium | 128 cores | 1024 GB |
| Large | 256 cores | 2048 GB |
{: caption="Table 1. Preconfigured vCPU and RAM options" caption-side="top"}

If you selected **Custom**, you can customize your reserved vCPU and RAM limits.

The vCPU maximum number is limited to the 40 cores with hyperthreading on each host. This limit allows for a maximum of 80 vCPU virtual machines.
{:important}

## Recommended services
{: #shared_ordering-services}

The Veeam Availability Suite and Veeam Cloud Connect Replication services are preinstalled and ready-to-use in all virtual data center instances. Service charges are incurred only if you choose to use the service.

For more information, see [Managing Veeam for VMware Solutions Shared instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_veeam).

## Summary
{: #shared_ordering-summary}

Based on your selected configuration for the virtual data center instance, the estimated price is instantly generated and displayed in the **Summary** right pane.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. The tool is useful if you want to estimate the price of the selected VMware Solutions Shared resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider purchasing.

## Procedure to order VMware Solutions Shared On-demand
{: #shared_ordering-procedure-ondemand}
{: help}
{: support}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click the **VMware Solutions Shared** card in the **Start provisioning** section.
2. On the **Create** tab of the **VMware Solutions Shared** page, select **On-demand**.
3. Enter the virtual data center name and select a resource group.
4. Select the {{site.data.keyword.cloud_notm}} data center to host the instance.
5. Select the vCPU and RAM limits according to your requirements.
6. On the **Summary** pane, verify the configuration and estimated price before you place the order.
7. Click **Create**.

## Procedure to order VMware Solutions Shared Reserved
{: #shared_ordering-procedure-reserved}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click the **VMware Solutions Shared** card in the **Start provisioning** section.
2. On the **Create** tab of the **VMware Solutions Shared** page, select **Reserved**.
3. Enter the virtual data center name and resource group.
4. Select the {{site.data.keyword.cloud_notm}} data center to host the instance.
5. Complete the resource reservation.
  * If you select **Preconfigured**, select the preconfigured vCPU model and RAM size.
  * If you select **Custom**, specify the vCPU and RAM limits according to your requirements.
6. On the **Summary** pane, verify the configuration and estimated price before you place the order.
7. Click **Create**.

## Results after you order VMware Solutions Shared
{: #shared_ordering-results}

* The deployment of the resources starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Virtual Data Center Status**.
* When the resources are successfully deployed, the components that are described in [Technical specifications for VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview#shared_overview-specs) are installed on your VMware® virtual platform.
* When the resources are ready to use, the status is changed to **Ready to use**.

## What to do next
{: #shared_ordering-next}

View the virtual data center instance that you ordered and then set the **admin** password for the vCloud Director Management console. For more information, see [Viewing and managing virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_managing).

## Related links
{: #shared_ordering-related}

* [Viewing and managing virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_managing)
* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [Managing Veeam for VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_veeam)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
