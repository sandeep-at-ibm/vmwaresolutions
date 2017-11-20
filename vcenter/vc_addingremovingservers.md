---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-17"

---

# Expanding and contracting capacity for vCenter Server instances

You can expand or contract the capacity of your VMware vCenter Server instance according to your business needs, by adding or removing ESXi servers. A vCenter Server instance can have up to 5 clusters, one of which is the default one, and each cluster can have up to 32 ESXi servers.

## Before you begin

*  Review the information about capacity in [Planning vCenter Server instances](vc_planning.html).
*  When you remove ESXi servers, the servers are placed in maintenance mode, and after that, all the virtual machines (VMs) running on the servers are migrated before they are removed from vCenter Server. For maximum of control over the relocation of VMs, it is recommended that you place the ESXi servers to be removed in maintenance mode and migrate the VMs running on them manually using the VMware vSphere Web Client. After that, remove the ESXi servers using the {{site.data.keyword.vmwaresolutions_full}} console.

   **Note:** Do not add or remove ESXi servers from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.

* A vCenter Server instance with NFS storage must have at least 2 ESXi servers. You can expand the platform to a maximum of 32 ESXi servers. However, the number of the bare metal servers that you can add at a time is as follows:
   * For the **Small**, **Medium**, and **Large** configurations, you can add 1 - 10 ESXi servers at a time.
   * For the **User customized** configuration, you can add 1 - 20 ESXi servers at a time.

  A vCenter Server instance with vSAN storage must have at least 4 ESXi servers. For more information about minimum of ESXi servers, see [Is a two-node vCenter Server instance highly available?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-).

## Procedure

1. Click **Deployed Instances** from the left navigation pane. Click the **vCenter Server** tab.
2. Click the instance for which you want to expand or contract capacity.
3. Click the **Infrastructure** tab.
4. Click the cluster in which you want to add ESXi servers, or from which you want to remove ESXi servers.
5. To add ESXi servers, complete the following steps:
   1. In the **ESXi Servers** section, click **Add**.
   2. In the **Add Server** window, enter the number of servers that you want to add, review the estimated cost, and then click **Add**.
6. To remove ESXi servers, select the servers that you want to remove in the **ESXi Servers** section, and then click **Remove**.

## Results

After starting the add or remove operation you might experience a slight delay in the instance status while it changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before making additional changes to the instance.

You are notified by email that your request to add or remove ESXi servers is being processed. The status of the cluster associated with the ESXi servers is changed to **Modifying**. When you remove servers, note that the ESXi servers are fully reclaimed by {{site.data.keyword.cloud}} infrastructure (SoftLayer) at the end of the {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) billing cycle, which is typically 30 days.

**Attention:** You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed ESXi servers.

If you do not see the new ESXi servers added to the list in the cluster, check the email or console notifications to find more details about the failure.

## Related links

* [Requirements and planning for vCenter Server instances](vc_planning.html)
* [Ordering vCenter Server instances](vc_orderinginstance.html)
* [Viewing vCenter Server instances](vc_viewinginstances.html)
* [Adding and viewing clusters for vCenter Server instances](vc_addingviewingclusters.html)
* [Deleting vCenter Server instances](vc_deletinginstance.html)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
