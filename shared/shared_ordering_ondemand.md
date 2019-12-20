---

copyright:

  years:  2019

lastupdated: "2019-12-18"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Shared On-demand
{: #shared_ordering_ondemand}

VMware Solutions Shared is provided as a beta offering. By using the VMware Solutions Shared offering, you acknowledge that no Red Hat Enterprise Linux virtual machines will be added to the environment.
{:note}

For the Shared On-demand offering, virtual data center vCPU and RAM are allocated as needed. The amount of time that the allocation takes depends on global usage of the virtual data center vCPU and RAM.
* The limits that are established for the amount of vCPU and RAM are maximum values that can be used at any time.
* vCPU and RAM resources can be increased and decreased later as required.
* The cost is calculated hourly and it is based on the resource usage in the virtual data center.
* There are no limits on the amount of storage that can be allocated and used in the virtual data center. Charges are hourly based on GB of allocated storage.
* There are no limits on the amount of inbound and outbound public networking. Public bandwidth is charged per GB.

## Requirements for VMware Solutions Shared
{: #shared_ordering_ondemand-req}

### IBM Cloud account
{: #shared_ordering_ondemand-account-req}

To use {{site.data.keyword.vmwaresolutions_short}} to order VMware Solutions Shared, you must have a **Pay As You Go** or **Subscription** {{site.data.keyword.cloud_notm}} account. The cost of the resources that are ordered is billed to that {{site.data.keyword.cloud_notm}} account.

### Virtual data center name requirements
{: #shared_ordering_ondemand-vdc-name-req}

The virtual data center name must be under 125 characters.

## Procedure to order Shared On-demand
{: #shared_ordering_ondemand-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. In the **Start Provisioning** section, click the **VMware Solutions Shared** card.
3. On the **VMware Solutions Shared** page, click the **On-demand** card and click **Continue**.
4. On the **IBM Cloud for VMware Solutions Shared - On-demand** page, enter the virtual data center name. The {{site.data.keyword.CloudDataCent_notm}} where the offering is available is preselected.
5. Select the vCPU and RAM limits according to your requirements. The Veeam service is enabled by default.
6. On the **Order Summary** pane, verify the configuration and estimated cost before you place the order.
7. Click **Provision**.

## Results after you order Shared On-demand
{: #shared_ordering_ondemand-results}

* The deployment of the resources starts automatically and you receive confirmation that the order is being processed. You can check the deployment status, including any issues that might require your attention, by viewing the **Virtual Data Center Status**.
* When the resources are successfully deployed, the components that are described in [Technical specifications for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview#shared_overview-specs) are installed on your VMware virtual platform.
* When the resources are ready to use, the status is changed to **Ready to Use**.

## Related links
{: #shared_ordering_ondemand-related}

* [Overview of VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview)
* [Ordering Shared Reserved](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_ordering_reserved)
* [Managing VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [VMware Solutions Shared operations](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_vcd-ops-guide)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
