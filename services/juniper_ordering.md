---

copyright:

  years:  2020

lastupdated: "2020-02-17"

keywords: Juniper vSRX, manage Juniper vSRX, Juniper vSRX console

subcollection: vmware-solutions

---

{:external: target="_blank" .external}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# Ordering Juniper vSRX
{: #juniper-ordering}

You can order the Juniper vSRX service when you order a new instance with the service included or by adding the service to your existing instance.

## Ordering Juniper vSRX for a new instance
{: #juniper-ordering-new-instance}

When you [order the instance](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the **Optional Services** section and click **Juniper vSRX** in the **Security and Compliance**  category. Follow the steps to add the service to your instance.

## Ordering Juniper vSRX for an existing instance
{: #juniper-ordering-exist-instance}

On the [instance details page](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances), click  **Services** on the left navigation pane, click **Juniper vSRX** in the **Security and Compliance** category, and then click **Add**. Follow the steps to add the service to your instance.

## Juniper vSRX service configuration
{: #juniper-ordering-service-config}

When you order the service, provide the following settings:

### Name
{: #juniper-ordering-service-config-name}

Specify the nickname for the installed instance in the **Enter a name for the HA deployment** field. Because there can be multiple copies of Juniper vSRX in a single vCenter Server instance, this name is used to ensure that the names of all networking components are unique.

### License model
{: #juniper-ordering-service-config-license-model}

Review the features of the two licenses and select either **Standard Edition** or **Content Security Bundle**.

You can't change the license model after service installation. To change the license model, you must remove the existing service and reinstall the service by selecting a different license option.
{:important}

After the service is ordered, the vSRX nodes are automatically ordered with the selected license models and the nodes are deployed and configured into the Management Cluster of your vCenter Server instance.

## Related links
{: #juniper-ordering-related-links}

* [Juniper vSRX overview](/docs/services/vmwaresolutions?topic=vmware-solutions-vsrx_overview)
* [Managing Juniper vSRX](/docs/services/vmwaresolutions?topic=vmware-solutions-juniper-managing)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices)
* [General FAQ about IBM Cloud for VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
* [Contacting IBM Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)
* [Juniper vSRX Virtual Firewall](https://www.juniper.net/us/en/products-services/security/srx-series/vsrx/){:external}
* [Juniper vSRX Documentation](https://www.juniper.net/documentation/product/en_US/vsrx){:external}
