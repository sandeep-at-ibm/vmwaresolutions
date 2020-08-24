---

copyright:

  years:  2016, 2020

lastupdated: "2020-08-07"

keywords: FAQ, host, ESXi server

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# FAQ about ESXi servers
{: #faq_esxi}

Find answers to frequently asked questions about the ESXi servers managed on the {{site.data.keyword.vmwaresolutions_full}} console.

## How many ESXi servers can I add to my instance?
{: #faq_esxi-instance}
{: faq}

Your vCenter Server instance allows you to expand the default cluster to have up to 51 ESXi servers. Each of the non-default clusters can be expanded to have up to 59 ESXi servers. Since you can add up to 10 clusters to an instance, each deployed instance can have a maximum of 51 + 9x59 = 582 ESXi servers across all clusters.

## How many ESXi servers can I add to a cluster?
{: #faq_esxi-cluster}
{: faq}

You can add a maximum of 51 ESXi servers to an initial cluster and a maximum of 59 ESXi servers to the added clusters.

For instances deployed in V2.1 or earlier, you must enable the necessary vSAN support to increase the cluster size beyond 32. Complete the following steps to enable the necessary vSAN support:

1. On each deployed ESXi server, run the following commands:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Restart each ESXi server. For more information, see [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081){:external}.
3. You might need to increase the size of the vCenter Server to accommodate the added virtual machines and ESXi servers.
4. Open an IBM Support ticket to indicate that you applied the vSAN changes manually by completing steps 1 - 3. In the ticket, request that your upgraded instance is enabled for ESXi servers beyond 32.

## Can I change the ESXi server names and IP addresses?
{: #faq_esxi-change-name-ip}
{: faq}

The ESXi server names and IP addresses cannot be changed because they are registered for Windows DNS resolution. Changes might result in failure during deployment or failure of vCenter Server functions.

Don't use the **Rename Device** feature on the {{site.data.keyword.cloud_notm}} user interface to change ESXi server names. This function changes the FQDN of the ESXi server, but the configured vCenter Server and the Windows VSI host registrations will be incorrect and might cause failures.
{:note}

## Can I disable root access on my ESXi servers?
{: #faq_esxi-disable-root}
{: faq}

It is recommended to keep root access enabled on ESXi servers, otherwise failure in the {{site.data.keyword.vmwaresolutions_short}} functions might occur.

If necessary, you can disable root access after the ESXi servers have a status of **Ready to use** on the {{site.data.keyword.vmwaresolutions_short}} console.

You must re-enable root access for subsequent automation operations, for example, when you add or remove file shares or when you install add-on services, such as Zerto.

## Can I add static routes on my ESXi servers to mount storage from other locations?
{: #faq_esxi-static-routes}
{: faq}

You can add static routes for storage but you must do it with extreme care. Otherwise, the existing shares might become unmounted.

Adding static routes for vMotion is not supported. Changes in vMotion subnet configuration might result in failure in the {{site.data.keyword.vmwaresolutions_short}} functions.
{:note}

## Related links
{: #faq_esxi-related}

* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservers)
* [Adding, viewing, and deleting clusters for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_hybrid_addingviewingclusters#vc_hybrid_addingviewingclusters)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
