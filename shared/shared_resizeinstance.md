---

copyright:

  years:  2020

lastupdated: "2020-03-02"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Resizing Virtual Data Center instances
{: #shared_resize}

You can change the amount of resources that are assigned to a Virtual Data Center when a Virtual Data Center instance is in the **Ready To Use** state.

## Procedure to resize Virtual Data Center instances
{: #shared_resize-procedure}

1. From the Virtual Data Center instance details page, click the pencil icon next to **Resource reservation**.
2. Update the values of the virtual CPU (vCPU) or RAM properties.
2. Verify the configuration and estimated cost and place the order.

The configuration change might fail if the vCPU and RAM resources are in use while they are reduced. This happens because the Virtual Data Center resources cannot be reduced to a level lower than the currently active resource usage.
{:note}

The Virtual Data Center instance enters in the **Modifying** state while the change is being made. When the resources are ready to use, the status is changed to **Ready to Use**.

## Related links
{: #shared_resize-related}

* [VMware Solutions Shared overview](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_overview)
* [Requirements and planning for VMware Solutions Shared](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_planning)
* [Ordering Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_ordering)
* [Viewing and managing Virtual Data Center instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [Deleting VMware Solutions Shared instances](/docs/services/vmwaresolutions?topic=vmware-solutions-shared_deletinginstance)
