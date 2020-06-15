---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-08"

keywords: vCenter Server add host, add server vCenter Server, remove host vCenter Server

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Expanding and contracting capacity for vCenter Server instances
{: #vc_addingremovingservers}

You can expand or contract the capacity of your VMware vCenter Server instance according to your business needs, by adding or removing ESXi servers or network file system (NFS) storage.

* For existing instances with VMware vSphere 6.7u1, you can add new ESXi servers with either vSphere 6.7u1 or vSphere 6.7u2.
* For existing instances with vSphere 6.5, when you add ESXi servers, the vSphere version matches the vSphere version of the existing ESXi servers in the instance. If you updated the vSphere version for the vCenter Server instance or for the existing ESXi servers, you might want to use the newer vSphere version for future additions of ESXi servers. To do so, open a VMware Solutions Support ticket to request that the VMware Solutions database is updated to reflect the correct (newer) version to be applied.
* If your initial cluster has vSAN storage, adding one or more ESXi servers after deployment can increase the cluster storage capacity.
* You can add or remove NFS storage shares to or from an existing NFS or vSAN cluster.

For the edge services cluster, you cannot add or remove ESXi servers.
{:note}

## Adding ESXi servers to vCenter Server instances
{: #vc_addingremovingservers-adding}

### Before you add ESXi servers
{: #vc_addingremovingservers-adding-prereq}

* Whenever possible, add ESXi servers by using the {{site.data.keyword.vmwaresolutions_full}} console, because changes that you make on the VMware vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. Therefore, add ESXi servers to vCenter Server only for on-premises ESXi servers or ESXi servers that you won't manage in the {{site.data.keyword.vmwaresolutions_short}} console.
* A vCenter Server instance with NFS storage must have at least two (for NSX-V) and three (for NSX-T) ESXi servers. Each of the non-default clusters can be expanded to have up to 59 ESXi servers.
* A vCenter Server instance with vSAN storage must have at least four ESXi servers.
* You can add 1 - 20 ESXi servers at a time. For more information about the minimum of ESXi servers, see [Is a two-node vCenter Server instance highly available?](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions#is-a-two-node-vcenter-server-instance-highly-available)

### Procedure to add ESXi servers
{: #vc_addingremovingservers-adding-procedure}
{: help}
{: support}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **Clusters** table, click the cluster to which you want to add ESXi servers.
5. In the **ESXi servers** section, click **Add**.
6. On the **ESXi server** page, select the number of bare metal servers that you want to add.
7. Optionally, select the **Maintenance mode** checkbox to add servers during maintenance mode. The checkbox is selected by default.

   When you provision the new ESXi server, virtual machines (VMs) are immediately migrated to the new servers if you do not select the **Maintenance mode** checkbox. You do not receive a confirmation message before the migration begins.
   {:important}

8. Complete the bare metal server configuration.
   * Select an existing bare metal server configuration that is being used by the existing hosts in the cluster. This option is disabled  under the following conditions:
      * The bare metal configuration being used by the existing hosts in the cluster is **Broadwell**. 
      * The storage type of the cluster is **Local disks**.
   * Select a new bare metal server configuration:
      * (NSX-V only) For instances with vSphere Enterprise Plus 6.7u1, specify the VMware vSphere version for the new ESXi server.
      * For **Skylake** and **Cascade Lake**, specify the **CPU model**, the amount of **RAM**, and the **Number of bare metal servers**.
      * For **SAP-certified**, specify the **CPU model and RAM** and the **Number of bare metal servers**.
9. Complete the subnet settings.
   * Select to continue using the previously selected primary subnets.
   * Select to specify primary subnets. Then, use the drop-down lists to select the **Public primary subnet** and **Private primary subnet**.
10. Complete the storage configuration. Specify the disk types for the capacity and cache disks, the number of disks, and the vSAN license edition. If you want more storage, select the **High performance Intel Optane** checkbox.
11. On the **Summary** pane, review the estimated pricing and click **Create**.

  You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

### Results after you add ESXi servers
{: #vc_addingremovingservers-adding-results}

1. You might experience a slight delay on the console while the instance status changes from **Ready to use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to add ESXi servers is being processed. On the console, the status of the cluster that is associated with the ESXi servers is changed to **Modifying**.
3. If you do not see the new ESXi servers added to the list in the cluster, check the email or console notifications to find more details about the failure.
4. (NSX-V only) You must use the Zerto Virtual Manager (ZVM) console and the pre-populated Zerto Virtual Replication Appliance (VRA) IP address to manually deploy the VRA virtual machine in the following circumstances:
   * If you add ESXi servers to a default cluster while the servers are in maintenance mode and Zerto for {{site.data.keyword.cloud_notm}} is installed.
   * If you add Zerto for {{site.data.keyword.cloud_notm}} to a vCenter Server instance that has an ESXi server that is in maintenance mode.

If you are adding ESXi servers during maintenance mode, VMs are not migrated to the new servers until you remove maintenance mode.   
{:important}

## Removing ESXi servers from vCenter Server instances
{: #vc_addingremovingservers-removing}

### Before you remove ESXi servers
{: #vc_addingremovingservers-removing-prereq}

* Whenever possible, remove ESXi servers by using the {{site.data.keyword.vmwaresolutions_short}} console, because changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. Therefore, remove ESXi servers from vCenter Server only for on-premises ESXi servers or ESXi servers that you can't or won't manage in the {{site.data.keyword.vmwaresolutions_short}} console.
* If using NFS storage, NSX-V instances require at least two ESXi servers and NSX-T instances require at least three ESXi servers.
* If using vSAN storage, at least for ESXi servers are required.
* When you remove ESXi servers, the servers are placed in maintenance mode, and after that, all the VMs running on the servers are migrated before they are removed from vCenter Server. For maximum of control over the relocation of VMs, it is recommended that you place the ESXi servers to be removed in maintenance mode and migrate the VMs running on them manually using the VMware vSphere Web Client. After that, remove the ESXi servers by using the {{site.data.keyword.vmwaresolutions_short}} console.
* (NSX-V only) If F5 BIG-IP or FortiGate Virtual Appliance is installed on your ESXi server, you must migrate the F5 BIG-IP and FortiGate VMs to a different ESXi server than the one that is hosting the VMs.
* (NSX-V only) If IBM Spectrum Protect&trade; Plus is installed on your ESXi server, ensure that there are no active (failed or in progress) backup or restore operations, because these active operations might prevent the ESXi server to be removed.

A 12-month commitment is required when you order the VMware HCX service. Your account continues to be charged for the HCX components if you delete a server before the end of 12-month commitment period. The 12-month commitment expiration date is available on the HCX details page. For more information about viewing service details, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:important}

### Procedure to remove ESXi servers
{: #vc_addingremovingservers-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to contract capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **Clusters** table, click the cluster from which you want to remove ESXi servers.
5. In the **ESXi servers** section, select the servers that you want to remove and click **Remove**.

### Results after you remove ESXi servers
{: #vc_addingremovingservers-removing-results}

1. You might experience a slight delay on the console, while the instance status changes from **Ready to use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to remove ESXi servers is being processed. On the console, the status of the cluster that is associated with the ESXi servers is changed to **Modifying**.
3. The ESXi servers are fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

   You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed ESXi servers.
   {:note}

## Adding NFS storage to vCenter Server instances
{: #section-adding-nfs-storage-to-vcenter-server-instances}

### Before you add NFS storage
{: #vc_addingremovingservers-adding-nfs-storage-prereq}

Do not add NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console. IBM will not manage NFS file shares that you manually add to an instance.

### Procedure to add NFS storage
{: #vc_addingremovingservers-adding-nfs-storage-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to expand capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **Clusters** table, click the cluster to which you want to add NFS storage.
5. In the **Storage** section, click **Add**.
6. In the **Storage** window, complete the storage configuration.
   * If you want to add and configure the same settings to all file shares, specify the **Number of shares**, **Performance**, and **Size (GB)**.
   * If you want to add and configure file shares individually, select **Configure shares individually**, then click the **+** icon next to the **Add shared storage** label and select the **Performance** and **Size (GB)** for each individual file share. You must select at least one file share.
7. Review the estimated price and click **Add NFS storage**.

  You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. This is useful if you want to estimate the price of the selected {{site.data.keyword.vmwaresolutions_short}} resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider to purchase.

### Results after you add NFS storage
{: #vc_addingremovingservers-adding-nfs-storage-results}

1. You might experience a slight delay on the console while the instance status changes from **Ready to use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to add NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. If you do not see the new NFS storage added to the list in the cluster, check the email or console notifications to find more details about the failure.

## Removing NFS storage from vCenter Server instances
{: #vc_addingremovingservers-removing-nfs-storage}

### Before you remove NFS storage
{: #vc_addingremovingservers-removing-nfs-storage-prereq}

* Do not remove NFS storage from the VMware vSphere Web Client. The changes that you make on the vSphere Web Client are not synchronized with the {{site.data.keyword.vmwaresolutions_short}} console.
* Before you remove the NFS storage, ensure that you removed all the VMs that reside on the storage.
* Ensure that the shares you plan to remove are associated with the correct vCenter Server instance.
* The cluster must be in **Ready to use** status.

### Procedure to remove NFS storage
{: #vc_addingremovingservers-removing-nfs-storage-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to contract capacity.
3. Click **Infrastructure** on the left navigation pane.
4. In the **Clusters** table, click the cluster from which you want to remove NFS storage.
5. In the **Storage** section, select the storage share that you want to remove and click **Delete**.
6. Click **Remove** in the **Remove storage** window.

### Results after you remove NFS storage
{: #vc_addingremovingservers-removing-nfs-storage-results}

1. You might experience a slight delay on the console, while the instance status changes from **Ready to use** to **Modifying**. Allow the operation to fully complete before you make more changes to the instance.
2. You are notified by email that your request to remove NFS storage is being processed. On the console, the status of the cluster that is associated with the NFS storage is changed to **Modifying**.
3. The NFS storage is fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days.

   You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed NFS storage.
   {:note}

## Related links
{: #vc_addingremovingservers-related}

* [vCenter Server Bill of Materials](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom)
* [Requirements and planning for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
* [Adding, viewing, and deleting clusters for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingviewingclusters#vc_addingviewingclusters)
* [Place a host in maintenance mode](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:external}
