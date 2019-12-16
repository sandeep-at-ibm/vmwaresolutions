---

copyright:

  years:  2019

lastupdated: "2019-12-11"

keywords: shared order resources, order reserved shared, order reserved resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Shared Reserved
{: #shared_ordering_reserved}

VMware Solutions Shared is provided as a beta offering. By using the VMware Solutions Shared offering, you acknowledge that no Red Hat Enterprise Linux virtual machines will be added to the environment.
{:note}

For Shared Reserved, the vCPU and RAM virtual data center reservations are preallocated and their availability is guaranteed.
* The cost is calculated monthly for the full reservation and it is based on the allocation size of the virtual data center.
* vCPU and RAM resources can be increased and decreased later as required.
* There are no limits on the amount of storage that can be allocated and used in the virtual data center. Charges are hourly based on GB of allocated storage.
* There are no limits on the amount of inbound and outbound public networking. Public bandwidth is charged per GB.

## Requirements for VMware Solutions Shared
{: #shared_ordering_reserved-req}

### IBM Cloud account
{: #shared_ordering_reserved-account-req}

To use {{site.data.keyword.vmwaresolutions_short}} to order VMware Solutions Shared, you must have a **Pay As You Go** or **Subscription** {{site.data.keyword.cloud_notm}} account. The cost of the resources that are ordered is billed to that {{site.data.keyword.cloud_notm}} account.

### Virtual data center name requirements
{: #shared_ordering_reserved-vdc-name-req}

The virtual data center name must be under 125 characters.

## Procedure to order Shared Reserved
{: #shared_ordering-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. In the **Start Provisioning** section, click the **VMware Solutions Shared** card.
3. On the **VMware Solutions Shared** page, click the **Reserved** card and click **Continue**.
4. On the **IBM Cloud for VMware Solutions Shared - Reserved** page, enter the virtual data center name. The {{site.data.keyword.CloudDataCent_notm}} where the offering is available is preselected.
5. Specify the resource reservation:
    * When you select **Preconfigured**, choose one of the preset configurations.
    * When you select **Custom**, specify the vCPU and the RAM reservations.
6. On the **Order Summary** pane, verify the configuration and estimated cost before you place the order.
7. Click **Provision**.

## Results after you order Shared Reserved
{: #shared_ordering_reserved-results}

* The deployment of the resources starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Virtual Data Center Status**.
* When the resources are successfully deployed, the components that are described in [Technical specifications for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview#shared_overview-specs) are installed on your VMware virtual platform.
* When the resources are ready to use, the status is changed to **Ready to Use**.

## Related links
{: #shared_ordering_reserved-related}

* [Overview of VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview)
* [Ordering Shared On-demand](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_ordering_ondemand)
* [Managing VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [VMware Solutions Shared operations](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_vcd-ops-guide)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
