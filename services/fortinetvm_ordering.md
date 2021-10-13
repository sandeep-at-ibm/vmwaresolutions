---

copyright:

  years:  2016, 2021

lastupdated: "2021-10-01"

keywords: FortiGate VA, FortiGate configuration, order FortiGate

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering FortiGate Virtual Appliance
{: #fortinetvm_ordering}

You can include the FortiGate® Virtual Appliance service with a new VMware vCenter Server® instance or add the service to your existing vCenter Server instance.

You can deploy the service on a single zone or multizone instance. Deployment is basically the same, except for multizone, which on day 0 has 3 FortiGate Virtual Appliance installs at one time. There is an install for each of the 3 edge clusters.

## Ordering FortiGate Virtual Appliance for a new instance
{: #fortinetvm_ordering-new}

When you [order the instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the services section and click **FortiGate Virtual Appliance** in the **Security and compliance** category. Follow the steps to add the service to your instance.

You cannot install Juniper® vSRX and FortiGate Virtual Appliance on the same edge services cluster.

## Ordering FortiGate Virtual Appliance for an existing instance
{: #fortinetvm_ordering-existing}

1. On the instance details page, click **Services** on the left navigation pane.
2. Click **Add** to add the service.
3. On the **Services** page, locate the **FortiGate Virtual Appliance** service and toggle its switch on.
4. Follow the steps to configure and add the service to your instance.

## Ordering FortiGate Virtual Appliance for private instances
{: #fortinetvm_ordering-private}

When you order FortiGate Virtual Appliance for instances that are not configured with public interfaces, you must provide a proxy server to complete the installation. The HTTP proxy server must be configured and available through Virtual Routing and Forwarding (VRF) before the FortiGate Virtual Appliance installation can start.

To ensure continued operation, FortiGate Virtual Appliance must have persistent access to the FortiGate license server through the internet.

## FortiGate Virtual Appliance service configuration
{: #fortinetvm_ordering-config}

When you order the service, provide the following settings.

### Name
{: #fortinetvm_ordering-config-name}

Enter the service name.

### FortiGuard network connection
{: #fortinetvm_ordering-config-network-connect}

Select **Public network** or **Private network** for FortiGuard. If the target cluster is configured with private-only network interfaces or the deployment is for a multizone instance, only the **Private network** option is available. This selection determines how FortiGuard contacts the Fortinet license server to activate the license and to download security patches, and it doesn't impact the workload data plane.

If you select **Private network**, specify the following settings:
* **Proxy IP address** - The IPv4 address of the proxy server.
* **Proxy port number** - The port number of the proxy server, usually 8080 or 3128.
* **Proxy user name** - If you require proxy authentication, enter the username of the proxy server.
* **Proxy password** - If you require proxy authentication, enter the password of the proxy server.

### Deployment size
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud}} provides the following deployment size options. For deployment on a multizone instance, only FortiGate-VM16 and FortiGate-VM32 are available.
* FortiGate-VM02 (2 vCPUs)
* FortiGate-VM04 (4 vCPUs)
* FortiGate-VM08 (8 vCPUs)
* FortiGate-VM16 (16 vCPUs)
* FortiGate-VM32 (32 vCPUs)
  The FortiGate-VM32 deployment size requires Cascade Lake 5218 or higher.

### Monthly subscription license model
{: #fortinetvm_ordering-config-license}

The monthly subscription license model for FortiGate Virtual Appliance offers the following options:
* **Standard FW** - This bundle includes the following.
   * Stateful packet inspection
   * VLAN protection and advanced logging
   * Ingress/egress FW rules
   * SSL/IPSec VPN termination
   * Continuous support
* **Standard FW + UTM** - This bundle includes all standard firewall services in addition to the Advanced Malware Protection (AMP) service.
   * Advanced malware protection
   * NGFW IPS and web filtering
   * Antispam
   * Application control
* **Standard FW + Enterprise** This bundle includes all standard firewall and UTM services in addition to the following services:
    * CASB (Cloud Access Security Broker) - This service provides visibility, compliance, data security, and threat protection for cloud-based services.
    * Industrial security - This service provides signatures for common ICS/SCADA protocols.
    * Security rating - This service provides audit capabilities to identify critical vulnerabilities and configuration weaknesses and implement best practice recommendations.

In 3Q 2018, Fortinet added three new services (CASB, Industrial Security, and Security Rating) to their Enterprise bundle. These services are available for FortiGate V6.0 and later only.
{: note}

You can't change the monthly subscription license model after service installation. To change the monthly subscription license model, you must delete the existing service and reinstall the service by selecting a different license option.
{: important}

## Related links
{: #fortinetvm_ordering-related}

* [FortiGate Virtual Appliance overview](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations)
* [Managing FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-managingfortinetvm)
* [Ordering services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Fortinet website](https://www.fortinet.com/){: external}
* [Fortinet Document Library](https://docs.fortinet.com/product/fortigate/6.2){: external}
