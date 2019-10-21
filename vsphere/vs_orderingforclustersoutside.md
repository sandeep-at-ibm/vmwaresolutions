---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-03"

keywords: vSphere scale cluster, scale vSphere, external vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Scaling clusters created outside of the console
{: #vs_orderingforclustersoutside}

You can use the VMware vSphere offering to scale existing vSphere clusters that are created outside of the {{site.data.keyword.vmwaresolutions_full}} console. To scale a vSphere cluster that is created outside of the console, re-create the cluster with the same settings with the console and then scale the cluster.

## Requirements
{: #vs_orderingforclustersoutside-req}

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [Managing user accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* You reviewed the requirements and considerations in [Requirements and planning for VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).

## Procedure to scale clusters created outside of the console
{: #vs_orderingforclustersoutside-procedure}

1. From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click the **VMware vSphere** card in the **Start Provisioning** section.
2. On the **VMware vSphere** page, click **Continue**.  
   Ensure that you are on the **Create New** tab and that **New cluster** is displayed in the **Cluster Configurations** list.
3. Create a cluster with the same settings as the existing cluster that is created outside of the {{site.data.keyword.vmwaresolutions_short}} console. For more information, see [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).  
   For network interface, to scale a cluster that is created outside of the {{site.data.keyword.vmwaresolutions_short}} console, you must select the existing VLANs for the cluster.
   {:note}
4. In the **Order Summary** pane, verify the cluster configuration, and then click **Save Configuration**.   
5. On the **Overview** page, click the **VMware vSphere** card.
6. On the **VMware vSphere** page, click **Continue**.
7. Click the **Scale Existing** tab. From the **Cluster Configurations** list, select the cluster that you recently created.
8. In the **{{site.data.keyword.baremetal_short}}** section, specify the number of {{site.data.keyword.baremetal_short}} that you want to add to the cluster.
9. If the cluster does not include the FortiGate 300 Series Security Appliance HA Pair on its public VLAN, you can order one by selecting **Include with purchase** under **FortiGate Physical Appliance 300 Series HA Pair**.
10. In the **Order Summary** pane, verify the instance configuration and the estimated cost, ensure that the account to be charged is correct, review and accept the terms, and then click **Provision**.

## Results
{: #vs_orderingforclustersoutside-results}

The deployment of the cluster starts automatically, and you receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

The vSphere clusters are not displayed on the **Resources** page, together with the vCenter Server instances.
{:note}

## Related links
{: #vs_orderingforclustersoutside-related}

* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ordering vSphere clusters based on existing configurations](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Scaling existing vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
