---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-16"

---

# FAQ about ESXi servers

Find answers to frequently asked questions about the ESXi servers managed on the {{site.data.keyword.vmwaresolutions_full}} console.

## How many ESXi servers can I add to my instances?

* For vCenter Server instances, you can configure the number of ESXi servers in the range of 2 - 20 per cluster. Each deployed instance can have a maximum of 128 ESXi servers across all clusters.
* For Cloud Foundation instances, the standard configuration has four ESXi servers. You can add a maximum of 28 servers (to a total of 32 servers). For Cloud Foundation instances in a multi-site configuration, you can have a maximum of 128 ESXi servers across all instances.

**Note**: If your configuration requires a multi-site deployment with more than 128 ESXi servers, [contact IBM Support](trbl_support.html) for assistance.

## Can I change the ESXi server names?

The ESXi server names cannot be changed, because they are registered for Windows DNS resolution. Changes could result in failures during deployment or in failures of vCenter Server functions.

**Note**: Do not use the **Rename Device** feature on the IBM Cloud user interface to change ESXi server names. This function will indeed change the FQDN of the ESXi server, but the configured vCenter Center and the Windows VSI host registrations will be incorrect and might cause failures.

## Can I disable root access on my ESXi servers?

It is recommended to keep root access enabled on ESXi servers, otherwise failures in the {{site.data.keyword.vmwaresolutions_short}} functionality might occur.

If absolutely necessary, you can disable root access after the ESXi servers have a status of **Ready to Use** on the {{site.data.keyword.vmwaresolutions_short}} console.

You must reenable root access for subsequent automation operations, for example, when adding or removing file shares or when installing additional services, such as Zerto on {{site.data.keyword.cloud}}.

## Can I add static routes on my ESXi servers to mount storage from other locations?

Static routes can be added for storage but the operations must be done with extreme care. Otherwise, the existing shares could become unmounted.

**Note**: Adding static routes for vMotion is not supported. Changes in vMotion subnet configuration might result in failures in the {{site.data.keyword.vmwaresolutions_short}} functionality.

## Related links

* [Expanding and contracting capacity for vCenter Server instances](../vcenter/vc_addingremovingservers.html)
* [Expanding and contracting capacity for Cloud Foundation instances](../sddc/sd_addingremovingservers.html)
* [Adding and viewing clusters for vCenter Server instances](../vcenter/vc_addingviewingclusters.html)
* [Adding and viewing clusters for Cloud Foundation instances](../sddc/sd_addingviewingclusters.html)
* [Contacting IBM Support](trbl_support.html)
