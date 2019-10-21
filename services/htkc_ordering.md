---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-08"

keywords: Hytrust KeyControl, Hytrust configuration, order Hytrust

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# Ordering HyTrust KeyControl
{: #htkc_ordering}

You can order the HyTrust KeyControl service while you order a new instance with an HA-pair of HyTrust KeyControl appliances included or by adding the HyTrust KeyControl appliances to your existing instance.

## Ordering HyTrust KeyControl for a new instance
{: #htkc_ordering-new}

You can order a new instance with HyTrust KeyControl by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, click **HyTrust KeyControl** under the **Security and Compliance** category in the **Optional Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click **HyTrust KeyControl** on the **Security and Compliance** card in the **Services** section. Specify the service settings and select **Add to New Instance**.

## Ordering HyTrust KeyControl for an existing instance
{: #htkc_ordering-existing}

You can add the HyTrust KeyControl service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click **HyTrust KeyControl** on the **Security and Compliance** card in the **Services** section. Specify the service settings and select **Add to Existing Instance**.

## HyTrust KeyControl service configuration
{: #htkc_ordering-config}

When you order the service, provide the following settings.

Specify whether you want to create a two-node Highly Available KeyControl cluster:
* If you select this option, two KeyControl nodes are deployed and a new active-active highly available cluster is created. This is the default option.
* If you do not select this option, two stand-alone KeyControl nodes are deployed with no cluster created. The stand-alone nodes can be manually clustered or added to existing KeyControl clusters after deployment.

## Related links
{: #htkc_ordering-related}

* [HyTrust KeyControl overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [Managing HyTrust KeyControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust website](https://www.hytrust.com/){:external}
