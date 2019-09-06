---

copyright:

  years:  2019

lastupdated: "2019-08-26"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Shared On-demand
{: #shared_ordering_ondemand}

{{site.data.keyword.vmwaresolutions_full}} Shared is provided as an experimental offering and is intended for IBM users only.
{:note}

By using the IBM Cloud for VMware Solutions Shared offering, you acknowledge that you have read and agreed to the following conditions:
* Only IBM users will have access to the ordered instances.
* No licenses will be used with Windows Catalog images.
* No Red Hat Enterprise Linux virtual machines will be added to the environment.

For on-demand, virtual data center vCPU and RAM are allocated as needed and can vary in the amount of time that the allocation takes depending on global usage of the virtual data center vCPU and RAM consumption.
* The limits that are established for the amount of vCPU and RAM are maximum values that can be consumed at any time.
* vCPU and RAM resources can be increased and decreased later as required.
* The cost is calculated hourly and it is based on the resource usage in the virtual data center.
* There are no limits on the amount of storage that can be allocated and used in the virtual data center. Charges are hourly based on GB of allocated storage.
* There are no limits on the amount of inbound and outbound public networking. Public bandwidth is charged per GB.

## Requirements for IBM Cloud for VMware Solutions Shared
{: #shared_ordering_ondemand-req}

### IBM Cloud infrastructure account
{: #shared_ordering_ondemand-account-req}

To use {{site.data.keyword.vmwaresolutions_short}} to order IBM Cloud for VMware Solutions Shared, you must have a **Pay As You Go** or **Subscription** {{site.data.keyword.cloud_notm}} account. The cost of the resources that are ordered is billed to that {{site.data.keyword.cloud_notm}} account.

### Virtual data center name requirements
{: #shared_ordering_ondemand-vdc-name-req}

The virtual data center name *should* meet the following requirements. Naming requirements will be enforced in the future.
* Only lowercase alphabetic, numeric, and dash (-) characters are allowed.
* The name must start with a lowercase alphabetic character.
* The name must end with a lowercase alphabetic or numeric character.
* The maximum length of the virtual data center name is 10 characters.
* The virtual data center name must be unique within your account.

## Procedure to order Shared On-demand
{: #shared_ordering_ondemand-procedure}

1. From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon from the left navigation pane and then click the **IBM Cloud for VMware Solutions Shared** card in the **VMware Virtual Data Centers** section.
2. On the **IBM Cloud for VMware Solutions Shared** page, click the **On-demand** card and click **Create**.
3. On the **IBM Cloud for VMware Solutions Shared - On-demand** page, enter the virtual data center name. The {{site.data.keyword.CloudDataCent_notm}} where the offering is available is preselected.
4. Select the vCPU and RAM limits according to your requirements.
5. On the **Order Summary** pane, verify the configuration and estimated cost before you place the order.
6. Click **Provision**.

## Results after you order Shared On-demand
{: #shared_ordering_ondemand-results}

* The deployment of the resources starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Virtual Data Center Status**.
* When the resources are successfully deployed, the components that are described in [Technical specifications for {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs) are installed on your VMware virtual platform.
* When the resources are ready to use, the status is changed to **Ready to Use**.

## Related links
{: #shared_ordering_ondemand-related}

* [Overview of {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Ordering Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [Managing {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [IBM Cloud for VMware Solutions Shared operations](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vcd-ops-guide)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
