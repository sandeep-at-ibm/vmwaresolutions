---

copyright:

  years:  2020, 2021

lastupdated: "2021-11-09"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Resizing virtual data centers
{: #shared_resize}

You can change the amount of resources that are assigned to a virtual data center when it is in the **Ready To Use** state.

## Procedure to resize virtual data centers
{: #shared_resize-procedure}

1. From the {{site.data.keyword.cloud}} for VMware® Solutions Shared virtual data center details page, click the **Edit** icon ![Edit icon](../../icons/edit-tagging.svg "Edit") next to **Resource Reservation**.
2. Update the values of the virtual CPU (vCPU) or RAM properties.
3. Click the **Optional consumption-based charges** section to expand it. Verify the configuration and estimated price and place the order by clicking the **Modify** button.

The configuration change might fail if the vCPU and RAM resources are in use while they are reduced. This happens because the virtual data center resources cannot be reduced to a level lower than the currently active resource usage.
{: note}

The virtual data center enters in the **Modifying** state while the change is being made. When the resources are ready to use, the status is changed to **Ready to use**.

## Related links
{: #shared_resize-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [Viewing and managing virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-summary)
* [Deleting VMware Solutions Shared virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_deletinginstance)
