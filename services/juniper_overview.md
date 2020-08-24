---

copyright:

  years:  2020

lastupdated: "2020-08-10"

keywords: Juniper vSRX, manage Juniper vSRX, Juniper vSRX virtual security appliance, Juniper virtual security appliance, Juniper vSRX console

subcollection: vmwaresolutions


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

# Juniper vSRX overview
{: #vsrx_overview}

Juniper® vSRX is a virtual security appliance that provides security and networking services at the perimeter or edge in virtualized private or public cloud environments. Within a VMware infrastructure, vSRX runs as a pair of virtual machines (VMs) within the VMware vSphere® environment.
{: shortdesc}

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some add-on services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

The current Juniper vSRX version that is installed is 19.4R2.6.
{:note}

You can install Juniper vSRX as one of the following components:
* As a virtual appliance on the management cluster. In this case, Juniper vSRX protects the traffic in the management cluster. That is, the service  protects only the traffic that you forward from your devices, for example, setting the default gateway to point to Juniper vSRX.
* As a security or gateway appliance on the edge services cluster. In this case, Juniper vSRX works like a gateway appliance, which you can set without having to configure any devices. Juniper vSRX protects all clusters in the same pod and data center. With this deployment, you route all traffic in the same pod and data center to protect a broader portion of the system.

Juniper vSRX is built on the Junos® operating system (Junos OS™) and delivers networking and security features similar to ones on the software releases for SRX Series Services Gateways.

Juniper vSRX provides a complete Next-Generation Firewall (NGFW) solution, including core firewall, VPN, NAT, advanced Layer 4 through Layer 7 security services such as Application Security, intrusion detection and prevention (IPS), and UTM features,  which include Enhanced Web Filtering and Anti-Virus.

You can install multiple instances of this service as needed. You can manage this service by using the J-Web interface link provided on the service details page on the {{site.data.keyword.vmwaresolutions_full}} console.

## Technical specifications for Juniper vSRX
{: #vsrx_overview-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

The following components are ordered and included in the Juniper vSRX service:

### Virtual machines
{: #vsrx_overview-specs-vms}

* vSRX is deployed as a pair of VMs configured for High Availability.
* Each VM is configured with 6 vCPUs, 8 GB of memory, and 16 GB of storage.

### High availability
{: #vsrx_overview-specs-ha}

The two vSRX nodes are deployed with DRS rules to ensure that the VMs reside on two physically separate hosts and do not migrate, that is, they’re pinned. If a host must be replaced or redeployed, you must adjust the preconfigured DRS rules before you can proceed.

### Networking
{: #vsrx_overview-specs-network}

The vSRX appliance can be accessed for administration purposes by either the J-Web console interface or direct ssh access. You can find the IP address information and credentials on the service details page.

### License and fees
{: #vsrx_overview-specs-license}

Two license types are offered:
* Standard
* Content Security Bundle

Each license type includes a different set of features and options. The Content Security Bundle license includes all the features and options in the Standard license and additional features, such as:
* AppSecure
* UTM
* SSL Proxy

For information about the features and options in each license, see [Choosing a vSRX License](https://cloud.ibm.com/docs/vsrx?topic=vsrx-getting-started#choosing-license).

Two licenses of the selected type are ordered, one for each of the appliance nodes.

You cannot change the licensing level after service installation. To change the licensing level, you must delete the existing service and reinstall the service by using a different licensing option.
{:important}

If you need to extend your license after expiration, you can update your vSRX license key. For more information, see [Managing Junos OS Licenses](https://www.juniper.net/documentation/en_US/release-independent/licensing/topics/topic-map/managing-junos-os-licenses-for-srx-series.html){:external}.

## Considerations when you install Juniper vSRX
{: #vsrx_overview-install-consider}

Review the following considerations before you install the Juniper vSRX service:
* The Juniper vSRX VMs are deployed only into the default cluster or the edge services cluster.
* Juniper vSRX can only protect items in the same data center and pod.
* You are responsible for Juniper vSRX configuration.
* For guidance information about extra configuration options that you might want to include and as an example, see [The IBM Cloud IaaS vSRX default configuration](/docs/vmwaresolutions?topic=vmwaresolutions-vcsvsrx-iaas-def-config). This information does not illustrate the configuration you have or should have. Your own configuration will be different.

## Considerations when you delete Juniper vSRX
{: #vsrx_overview-remove-consider}

Any network operations that rely on routes that are established via vSRX might be affected and require reconfiguration.

## Related links
{: #vsrx_overview-related-links}

* [Managing Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-managing)
* [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices)
* [General FAQ about IBM Cloud for VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [Juniper vSRX Virtual Firewall](https://www.juniper.net/us/en/products-services/security/srx-series/vsrx/){:external}
* [Juniper vSRX Documentation](https://www.juniper.net/documentation/product/en_US/vsrx){:external}
