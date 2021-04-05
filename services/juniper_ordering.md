---

copyright:

  years:  2020, 2021

lastupdated: "2021-04-01"

keywords: Juniper vSRX, manage Juniper vSRX, Juniper vSRX console

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
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

You can include the Juniper® vSRX service with a new VMware vCenter Server® instance or add the service to your existing vCenter Server instance.

You can install multiple instances of Juniper vSRX on the management cluster. On a single edge services cluster, you can install only one instance of Juniper vSRX.

## Ordering Juniper vSRX for a new instance
{: #juniper-ordering-new-instance}

When you [order the instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the services section and click **Juniper vSRX** in the **Security and compliance** category. Follow the steps to add the service to your instance.

The Juniper vSRX service is deployed on the management cluster unless you order the edge services cluster. For the Juniper vSRX service to function as a gateway for your vCenter Server instance, you must include the edge services cluster in your order.

## Ordering Juniper vSRX for an existing instance
{: #juniper-ordering-exist-instance}

1. On the instance details page, click **Services** on the left navigation pane.
2. Click **Add** to add the service.
3. On the **Services** page, locate the **Juniper vSRX** service and toggle its switch on.
4. Follow the steps to configure and add the service to your instance.

When you add Juniper vSRX to an existing vCenter Server instance, you can select a cluster on which to install Juniper vSRX. You can install Juniper vSRX on a management cluster or on any edge services cluster.
You must deploy the Juniper vSRX to an edge services cluster for the Juniper vSRX to function as a gateway for your vCenter Server instance.

## Juniper vSRX service configuration
{: #juniper-ordering-service-config}

When you order the service, provide the following settings:

### Name
{: #juniper-ordering-service-config-name}

Specify the nickname for the installed instance in the **Enter a name for the HA deployment** field. Because multiple copies of Juniper vSRX can be in a single vCenter Server instance, this name is used to ensure that the names of all networking components are unique.

### License model
{: #juniper-ordering-service-config-license-model}

Review the features of the two licenses and select either **Standard Edition** or **Content Security Bundle**.

You can't change the license model after service installation. To change the license model, you must delete the existing service and reinstall the service by selecting a different license option.
{:important}

After the service is ordered, the vSRX nodes are automatically ordered with the selected license models.

The Juniper vSRX nodes are deployed to the edge services cluster if you selected this option. If you do not have an edge services cluster in your vCenter Server instance, the Juniper vSRX service is deployed on the management cluster.

### Juniper vSRX deployment on an edge services cluster
{: #juniper-ordering-service-config-edge-deployment}

If you deploy Juniper vSRX on an edge services cluster, after deployment, you must configure Juniper vSRX specifically for your environment. Complete the following steps:
1. Configure the redundant Ethernet (`reth`) 2 interface with the default gateway IP addresses of each subnet in your private trunk VLAN. The IP addresses are assigned to the logical interface, which is in the format of `reth2.VLANid`.
2. Configure the redundant Ethernet (`reth`) 3 interface with the default gateway IP addresses of each subnet in your public trunk VLAN, if you have one. The IP addresses are assigned to the logical interface, which is in the format of `reth3.VLANid`.
3. In the {{site.data.keyword.cloud}} classic infrastructure view, look at the gateway appliance ordered for the edge services cluster. From there, assign the VLANs that you want to the gateway appliance and put them in *route-through* mode.

## Related links
{: #juniper-ordering-related-links}

* [Juniper vSRX overview](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview)
* [Managing Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-managing)
* [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices)
* [General FAQ about VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [Juniper vSRX Virtual Firewall](https://www.juniper.net/us/en/products-services/security/srx-series/vsrx/){:external}
* [Juniper vSRX Documentation](https://www.juniper.net/documentation/product/en_US/vsrx){:external}
