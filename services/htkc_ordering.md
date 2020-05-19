---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-14"

keywords: Hytrust KeyControl, Hytrust configuration, order Hytrust

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}

# Ordering HyTrust KeyControl
{: #htkc_ordering}

You can add the HyTrust KeyControl service (with an HA pair of HyTrust KeyControl appliances included) to a new vCenter Server instance. You can also add the service to your existing vCenter Server instance.

## Ordering HyTrust KeyControl for a new instance
{: #htkc_ordering-new}

When you [order the instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the **Optional Services** section and click **HyTrust KeyControl** in the **Security and Compliance** category. Follow the steps to add the service to your instance.

## Ordering HyTrust KeyControl for an existing instance
{: #htkc_ordering-existing}

On the [instance details page](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances), click **Services** on the left navigation pane, click **HyTrust KeyControl** in the **Security and Compliance** category, and then click **Add**. Follow the steps to add the service to your instance.

## HyTrust KeyControl service configuration
{: #htkc_ordering-config}

When you order the service, provide the following settings.

Specify whether you want to create a two-node Highly Available KeyControl cluster:
* If you select this option, two KeyControl nodes are deployed and a new active-active highly available cluster is created. This is the default option.
* If you do not select this option, two stand-alone KeyControl nodes are deployed with no cluster created. The stand-alone nodes can be manually clustered or added to existing KeyControl clusters after deployment.

## Related links
{: #htkc_ordering-related}

* [HyTrust KeyControl overview](/docs/vmwaresolutions?topic=vmwaresolutions-htkc_considerations)
* [Managing HyTrust KeyControl](/docs/vmwaresolutions?topic=vmwaresolutions-managinghtkc)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_hybrid_addingremovingservices)
* [Contacting {{site.data.keyword.IBM}} Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [HyTrust website](https://www.hytrust.com/){:external}
