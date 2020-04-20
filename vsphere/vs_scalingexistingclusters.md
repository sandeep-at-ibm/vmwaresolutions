---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-14"

keywords: vSphere scale cluster, scale vSphere, scale vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Scaling existing vSphere clusters
{: #vs_scalingexistingclusters}

You can scale out a VMware vSphere cluster that you ordered or saved in the {{site.data.keyword.vmwaresolutions_full}} console. To do so, add ESXi servers or order a FortiGate 300 Series Security Appliance HA pair for the cluster.

## Requirements
{: #vs_scalingexistingclusters-req}

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/vmwaresolutions?topic=vmware-solutions-useraccount).
*  You reviewed the requirements and considerations in [Requirements and planning for vSphere clusters](/docs/vmwaresolutions?topic=vmware-solutions-vs_planning).
*  You received an email with the confirmation that the cluster you want to scale is ready to use.

## Procedure to scale existing clusters
{: #vs_scalingexistingclusters-procedure}
{: help}
{: support}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. In the **Start Provisioning** section, click the **VMware Solutions Dedicated** card.
3. On the **VMware Solutions Dedicated** page, click the **VMware vSphere** card.
4. Click the **Scale Existing** tab and select the cluster that you want to scale from the **Cluster Configurations** list.
5. Review the cluster settings that are automatically completed.
6. In the **Bare Metal Server** section, specify the number of {{site.data.keyword.cloud_notm}} bare metal servers that you want to add to the cluster.
7. If the cluster does not include the FortiGate 300 Series Security Appliance HA Pair on its public VLAN, you can order the appliance. To do so, select the **Include with purchase** check box under **FortiGate Physical Appliance 300 Series HA Pair**.
8. In the **Order Summary** pane, verify the instance configuration and the estimated cost.
   * To save the configuration as a template without placing an order, click **Save Configuration**.
   * To place the order, ensure that the account to be charged is correct, review and accept the terms, and then click **Provision**.

### Results
{: #vs_scalingexistingclusters-results}

The cluster scaling starts automatically. You receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

If the cluster you are scaling is not ready to use, you might receive an error message.

The vSphere clusters, unlike the vCenter Server instances, are not displayed on the **Resources** page.
{:note}

## Related links
{: #vs_scalingexistingclusters-related}

* [Ordering new vSphere clusters](/docs/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances)
* [Ordering vSphere clusters based on existing configurations](/docs/vmwaresolutions?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Scaling clusters created outside of the console](/docs/vmwaresolutions?topic=vmware-solutions-vs_orderingforclustersoutside)
