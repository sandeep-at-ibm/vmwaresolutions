---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-27"

---

# Expanding and contracting capacity for VMware Federal instances

You can expand or contract the capacity of your VMware Federal instance according to your business needs, by adding or removing ESXi servers.

If your primary cluster has vSAN as its storage, adding one or more ESXi servers after deployment can increase the cluster storage capacity.

**Note:** This feature is only available to VMware Federal instances that have not been secured.

## Before you begin

*  Review the information about capacity in [Planning VMware Federal instances](vc_fed_planning.html#capacity-considerations).
*  When you remove ESXi servers, the servers are placed in maintenance mode, and after that, all the virtual machines (VMs) running on the servers are migrated before they are removed from vCenter Server. For maximum of control over the relocation of VMs, it is recommended that you place the ESXi servers to be removed in maintenance mode and migrate the VMs running on them manually using the VMware vSphere Web Client. After that, remove the ESXi servers using the {{site.data.keyword.vmwaresolutions_full}} console.

   **Note:** Do not add or remove ESXi servers from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.

<!--* Before you remove ESXi servers with the IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service installed, ensure that there are no active (failed or in progress) backup or restore operations, because these active operations might prevent the ESXi servers to be removed.-->

* A VMware Federal instance with NFS storage must have at least 2 ESXi servers. You can expand the default cluster to have up to 51 ESXi servers.

<!--* Each of the non-default clusters can be expanded to have up to 59 ESXi servers.-->

*  A VMware Federal instance with vSAN storage must have at least 4 ESXi servers.

<!--* When there are more than 51 ESXi servers in the initial cluster of an instance, the HCX on {{site.data.keyword.cloud_notm}} service cannot be installed into the instance. Because the HCX service requires 8 IPs in the vMotion subnet from the initial cluster, if the number of ESXi servers exceeds 51, no IPs in the vMotion subnet can be available for HCX service.-->

## Procedure

1. Click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances table**, click the instance for which you want to expand or contract capacity.
3. Click the **Infrastructure** tab.
4. In the **CLUSTERS** table, click **cluster1**.<!-- the cluster in which you want to add ESXi servers, or from which you want to remove ESXi servers-->
5. To add ESXi servers, complete the following steps:
   1. In the **ESXi Servers** section, click **Add**.
   2. In the **Add Server** window, enter the number of servers that you want to add, review the estimated cost, and then click **Add**.
6. To remove ESXi servers, select the servers that you want to remove in the **ESXi Servers** section, and then click **Remove**.

## Results

After starting the add or remove operation you might experience a slight delay in the instance status while it changes from **Ready to Use** to **Modifying**. Allow the operation to fully complete before making additional changes to the instance.

You are notified by email that your request to add or remove ESXi servers is being processed. The status of **cluster1** <!--the cluster associated with the ESXi servers -->is changed to **Modifying**. When you remove servers, note that the ESXi servers are fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

**Attention:** You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed ESXi servers.

If you do not see the new ESXi servers added to the list in the cluster, check the email or console notifications to find more details about the failure.

## Related links

* [Requirements and planning for VMware Federal instances](vc_fed_planning.html)
* [Viewing the default cluster for VMware Federal instances](vc_fed_addingviewingclusters.html)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
