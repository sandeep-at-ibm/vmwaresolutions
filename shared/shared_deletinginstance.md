---

copyright:

  years:  2020

lastupdated: "2020-02-21"

keywords: VMware Solutions Shared delete instance, delete VMware Solutions Shared, remove VMware Solutions Shared

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Deleting Virtual Data Center instances
{: #shared_deletinginstance}

You can delete a Virtual Data Center instance when it's in the **Ready To Use** state.

Before you delete your Virtual Data Center instance, ensure that any items that you created within the instance are removed. Items might include the following artifacts:

* vApps, vApp templates, and virtual machines (VMs). You must remove these items even if they are stopped.
* Organization networks that are removed or unshared from the instance
* Organization catalogs
* DHCP pools created within the Organization Virtual Data Center edge gateway

## Considerations when deleting Virtual Data Center instances
{: #shared_deletinginstance-considerations}

All of the Virtual Data Center VM restore points in Veeam are automatically deleted when you delete a VMware Solutions Shared instance.
{:important}

Any job that includes instructions to backup the VM fails when the VM restore points in Veeam are deleted. The existing VMs in the job are still backed up, however the job status is marked as failed. To remove the failed status, you must manually edit the job to remove the instruction to back up the now deleted VMs.

## Procedure to delete instances from the Resources page
{: #shared_deletinginstance-procedure1}

1. From the {{site.data.keyword.vmwaresolutions_full}} console, click **Resources** from the left navigation pane.
2. In the **VMware Solutions Shared** table, find the instance to delete.
3. In the **Actions** column, click the Delete icon.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.

## Procedure to delete instances from the instance details page
{: #shared_deletinginstance-procedure2}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **VMware Solutions Shared** table, click the instance to delete.
3. Click the **Actions** drop down and click **Delete Instance**.
4. In the **Delete Instance** window, review and accept the delete confirmation and click **Delete**.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.

## Related links
{: #shared_deletinginstance-related}

* [VMware Solutions Shared overview](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview)
* [Requirements and planning for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_planning)
* [Ordering Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_ordering)
* [Viewing and managing Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [Operating VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_vcd-ops-guide)
* [Managing Veeam for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_veeam)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
* [Contacting IBM Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)
