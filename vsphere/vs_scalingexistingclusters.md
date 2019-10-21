---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-03"

keywords: vSphere scale cluster, scale vSphere, scale vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Scaling existing vSphere clusters
{: #vs_scalingexistingclusters}

You can scale out a VMware vSphere cluster that you ordered or saved in the {{site.data.keyword.vmwaresolutions_full}} console. To do so, add ESXi servers or order a FortiGate 300 Series Security Appliance HA pair for the cluster.

## Requirements
{: #vs_scalingexistingclusters-req}

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount#managing-user-accounts-and-settings).
*  You reviewed the requirements and considerations in [Requirements and planning for vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).
*  You received an email with the confirmation that the cluster you want to scale is ready to use.

## Procedure to scale existing clusters
{: #vs_scalingexistingclusters-procedure}

1. From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click the **VMware vSphere** card in the **Start Provisioning** section.
2. On the **VMware vSphere** page, click **Continue**.  
3. Click the **Scale Existing** tab and select the cluster that you want to scale from the **Cluster Configurations** list.
4. Review the cluster settings that are automatically completed.
5. In the **{{site.data.keyword.baremetal_short}}** section, specify the number of {{site.data.keyword.baremetal_short}} that you want to add to the cluster.
6. If the cluster does not include the FortiGate 300 Series Security Appliance HA Pair on its public VLAN, you can order the appliance. To do so, select the **Include with purchase** check box under **FortiGate Physical Appliance 300 Series HA Pair**.
7. In the **Order Summary** pane, verify the instance configuration and the estimated cost.
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

* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ordering vSphere clusters based on existing configurations](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Scaling clusters created outside of the console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
