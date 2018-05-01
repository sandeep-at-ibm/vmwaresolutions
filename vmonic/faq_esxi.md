---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-30"

---

# FAQ about ESXi servers

Find answers to frequently asked questions about the ESXi servers managed on the {{site.data.keyword.vmwaresolutions_full}} console.

## How many ESXi servers can I add to my instance?

* For vCenter Server instances, you can you can expand the default cluster to have up to 51 ESXi servers. Each of the non-default clusters can be expanded to have up to 59 ESXi servers. Since you can add up to 10 clusters to an instance,  each deployed instance can have a maximum of 51 + 9x59 = 582 ESXi servers across all clusters.
* For Cloud Foundation instances, the standard configuration has four ESXi servers. You can add a maximum of 28 servers (to a total of 32 servers). For Cloud Foundation instances in a multi-site configuration, you can have a maximum of 128 ESXi servers across all instances.

  **Note**: If your Cloud Foundation configuration requires a multi-site deployment with more than 128 ESXi servers, [contact IBM Support](trbl_support.html) for assistance.

## How many ESXi servers can I add to a cluster?

For V2.2 and later releases, you can add a maximum of 51 ESXi servers to an initial cluster and a maximum of 59 ESXi servers to additional clusters.

For instances deployed in V2.1 or earlier releases, you must enable the necessary vSAN support to increase the cluster size beyond 32. Complete the following steps to enable the necessary vSAN support:

1. On each deployed ESXi server, run the following commands:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Restart each ESXi server. For more information, see [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081).
3. Note that you may need to increase the size of the vCenter Server to accommodate the additional virtual machines and ESXi servers.
4. Open an IBM Support ticket indicating that you have manually applied the vSAN changes above and that you want to have your upgraded instance enabled for additional ESXi servers beyond 32.

## Can I change the ESXi server names and IP addresses?

The ESXi server names and IP addresses cannot be changed, because they are registered for Windows DNS resolution. Changes could result in failures during deployment or in failures of vCenter Server functions.

**Note**: Do not use the **Rename Device** feature on the IBM Cloud user interface to change ESXi server names. This function will indeed change the FQDN of the ESXi server, but the configured vCenter Center and the Windows VSI host registrations will be incorrect and might cause failures.

## Can I disable root access on my ESXi servers?

It is recommended to keep root access enabled on ESXi servers, otherwise failures in the {{site.data.keyword.vmwaresolutions_short}} functionality might occur.

If absolutely necessary, you can disable root access after the ESXi servers have a status of **Ready to Use** on the {{site.data.keyword.vmwaresolutions_short}} console.

You must reenable root access for subsequent automation operations, for example, when adding or removing file shares or when installing additional services, such as Zerto on {{site.data.keyword.cloud_notm}}.

## Can I add static routes on my ESXi servers to mount storage from other locations?

Static routes can be added for storage but the operations must be done with extreme care. Otherwise, the existing shares could become unmounted.

**Note**: Adding static routes for vMotion is not supported. Changes in vMotion subnet configuration might result in failures in the {{site.data.keyword.vmwaresolutions_short}} functionality.

## Related links

* [Expanding and contracting capacity for vCenter Server instances](../vcenter/vc_addingremovingservers.html)
* [Expanding and contracting capacity for Cloud Foundation instances](../sddc/sd_addingremovingservers.html)
* [Adding, viewing, and deleting clusters for vCenter Server instances](../vcenter/vc_addingviewingclusters.html)
* [Adding, viewing, and deleting clusters for Cloud Foundation instances](../sddc/sd_addingviewingclusters.html)
* [Contacting IBM Support](trbl_support.html)
