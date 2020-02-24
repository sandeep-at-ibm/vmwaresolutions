---

copyright:

  years:  2020

lastupdated: "2020-02-19"

keywords: Juniper vSRX, manage Juniper vSRX, Juniper vSRX virtual security appliance, Juniper virtual security appliance, Juniper vSRX console

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

# Juniper vSRX overview
{: #vsrx_overview}

Juniper vSRX is a virtual security appliance that provides security and networking services at the perimeter or edge in virtualized private or public cloud environments. Within a VMware infrastructure, vSRX runs as a pair of virtual machines (VMs) within the vSphere environment.
{: shortdesc}

vSRX is built on the Junos operating system (Junos OS) and delivers networking and security features similar to ones on the software releases for SRX Series Services Gateways.

The vSRX provides a complete Next-Generation Firewall (NGFW) solution, including core firewall, VPN, NAT, advanced Layer 4 through Layer 7 security services such as Application Security, intrusion detection and prevention (IPS), and UTM features,  which include Enhanced Web Filtering and Anti-Virus.

You can install multiple instances of this service as needed. You can manage this service by using the J-Web interface link provided on the service details page on the IBM Cloud for VMware Solutions console.

The current Juniper vSRX version that is installed is 18.4.
{:note}


## Technical specifications for Juniper vSRX
{: #vsrx_overview-specs}

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

For information about the features and options in each license, see [Choosing a vSRX License](https://cloud.ibm.com/docs/infrastructure/vsrx?topic=vsrx-getting-started#choosing-license).

Two licenses of the selected type are ordered, one for each of the appliance nodes.

You cannot change the licensing level after service installation. To change the licensing level, you must remove the existing service and reinstall the service by using a different licensing option.
{:important}

## Considerations when you install Juniper vSRX
{: #vsrx_overview-install-consider}

Review the following considerations before you install the Juniper vSRX service:
* The vSRX VMs are deployed only into the default cluster.
* You are responsible for Juniper vSRX configuration.

### Resource requirements for Juniper vSRX
{: #vsrx_overview-resource-req}

* Before the service is installed in your environment, a check is done against the available capacity of the default cluster in the environment to ensure that the service components can fit. You must have enough available capacity to accomodate two VMs with the following requirements, on different hosts:
   * 6 vCPUs
   * 8 GB RAM
   * 16 GB disk storage
* If the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email.
* To install the service, you must increase the capacity in your default cluster either by adding more hosts or by freeing up RAM, CPU, or disk space. After that, add the service again in the console and remove the existing service in the **Capacity Validation Failed** state by clicking the delete icon next to it.

### Updating configuration settings
{: #vsrx_overview-config-sett}

By default, the communication settings between the two highly available VMs are 1000 and 3. The values might be too low for a virtual environment. After the installation is complete, it is recommended you change these settings by connecting via SSH to one of the VMs and issuing the following  commands:

    set chassis cluster heartbeat-interval 2000
    set chassis cluster heartbeat-threshold 8

## Considerations when you remove Juniper vSRX
{: #vsrx_overview-remove-consider}

Any network operations that rely on routes that are established via vSRX might be affected and require reconfiguration.

## Related links
{: #vsrx_overview-related-links}

* [Managing Juniper vSRX](/docs/services/vmwaresolutions?topic=vmware-solutions-juniper-managing)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices)
* [General FAQ about IBM Cloud for VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
* [Contacting IBM Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)
* [Juniper vSRX Virtual Firewall](https://www.juniper.net/us/en/products-services/security/srx-series/vsrx/){:external}
* [Juniper vSRX Documentation](https://www.juniper.net/documentation/product/en_US/vsrx){:external}
