---

copyright:

  years:  2020

lastupdated: "2020-04-13"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Resizing virtual data center instances
{: #shared_resize}

You can change the amount of resources that are assigned to a virtual data center when a virtual data center instance is in the **Ready To Use** state.

## Procedure to resize virtual data center instances
{: #shared_resize-procedure}

1. From the virtual data center instance details page, click the pencil icon next to **Resource reservation**.
2. Update the values of the virtual CPU (vCPU) or RAM properties.
2. Verify the configuration and estimated cost and place the order.

The configuration change might fail if the vCPU and RAM resources are in use while they are reduced. This happens because the virtual data center resources cannot be reduced to a level lower than the currently active resource usage.
{:note}

The virtual data center instance enters in the **Modifying** state while the change is being made. When the resources are ready to use, the status is changed to **Ready to Use**.

## Related links
{: #shared_resize-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmware-solutions-shared_overview)
* [Viewing and managing virtual data center instances](/docs/vmwaresolutions?topic=vmware-solutions-shared_managing)
* [Deleting VMware Solutions Shared instances](/docs/vmwaresolutions?topic=vmware-solutions-shared_deletinginstance)
