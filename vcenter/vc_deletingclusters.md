---

copyright:

  years:  2021

lastupdated: "2021-07-16"

keywords: vCenter Server delete clusters, delete clusters, delete vCenter Server cluster, vmware multizone, vCenter Server multizone delete clusters, delete vCenter Server cluster

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Deleting clusters from vCenter Server instances
{: #vc_deletingclusters}

You can delete clusters from VMware vCenter Server® instances when you do not need them.

For vCenter Server instances V3.4 and later, you can add or delete a cluster while another cluster is being created or deleted.
{:note}

## Before you delete clusters from vCenter Server instances
{: #vc_deletingclusters-before}

* Whenever possible, delete clusters by using the VMware Solutions console because changes that you make on the VMware vSphere Web Client are not synchronized with the VMware Solutions console. Therefore, delete clusters from vCenter Server only for on-premises clusters or clusters that you can't or don't plan to manage in the VMware Solutions console.
* You can delete only clusters that are added as part of day 2 operations. Clusters that are created during initial deployment can't be deleted.
* You can delete a single cluster at a time. To delete more than one cluster, you must do it in sequence. Wait for the previous cluster to be deleted before you delete the next cluster.
* Ensure that all nodes in a cluster are powered on and operational before you delete the cluster.
* When you delete a cluster, all VMs from the cluster are also deleted and they can't be recovered. If you want to keep the VMs, migrate them to other clusters.
* You do not have to delete any services that are installed on the cluster, including services on an edge services cluster. The services are automatically deleted when you delete the cluster.

## Procedure to delete clusters from vCenter Server instances
{: #vc_deletingclusters-procedure}
{: help}
{: support}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance that you want to delete clusters from.

   Ensure that the instance is in the **Ready to use** status. Otherwise, you can't delete clusters from the instance.
   {:note}

3. Click **Infrastructure** on the left navigation pane. In the **Clusters** table, locate the cluster that you want to delete and click the **Delete** icon next to the **Status** column.
4. In the **Delete cluster** window, confirm that you completed the migration of VMs to other clusters, if needed, and that you want to delete the cluster. Click **Delete**.

## Related links
{: #vc_deletingclusters-related}

* [Viewing vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservers)
