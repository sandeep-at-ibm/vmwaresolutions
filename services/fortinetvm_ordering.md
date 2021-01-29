---

copyright:

  years:  2016, 2021

lastupdated: "2021-01-27"

keywords: FortiGate VA, FortiGate configuration, order FortiGate

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering FortiGate Virtual Appliance
{: #fortinetvm_ordering}

You can include the FortiGate® Virtual Appliance service with a new vCenter Server® instance or add the service to your existing vCenter Server instance.

## Ordering FortiGate Virtual Appliance for a new instance
{: #fortinetvm_ordering-new}

When you [order the instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the **Add-on services** section and click **FortiGate Virtual Appliance** in the **Security and compliance** category. Follow the steps to add the service to your instance.

## Ordering FortiGate Virtual Appliance for an existing instance
{: #fortinetvm_ordering-existing}

On the [instance details page](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances), click **Services** on the left navigation pane, click **FortiGate Virtual Appliance** in the **Security and compliance** category, and then click **Add**. Follow the steps to add the service to your instance.

## Ordering FortiGate Virtual Appliance for private instances
{: #fortinetvm_ordering-private}

When you order FortiGate Virtual Appliance for instances that are not configured with public interfaces, you must provide a proxy server to complete the installation. The HTTP proxy server must be configured and available through Virtual Routing and Forwarding (VRF) before the FortiGate Virtual Appliance installation can start.

To ensure continued operation, FortiGate Virtual Appliance must have persistent access to the FortiGate license server through the internet.

## FortiGate Virtual Appliance service configuration
{: #fortinetvm_ordering-config}

When you order the service, provide the following settings.

### FortiGuard network connection
{: #fortinetvm_ordering-config-network-connect}

Select **Public network** or **Private network** for FortiGuard. If the target cluster is configured with private-only network interfaces, only the **Private network** option is available. This selection determines how FortiGuard contacts the Fortinet license server to activate the license and to download security patches, and it doesn't impact the workload data plane.

If you select **Private network**, specify the following settings:
* **Proxy IP Address** - The IPv4 address of the proxy server.
* **Proxy Port Number** - The port number of the proxy server, usually 8080 or 3128.
* **Proxy User Name** - If you require proxy authentication, enter the user name of the proxy server.
* **Proxy Password** - If you require proxy authentication, enter the password of the proxy server.

### Name
{: #fortinetvm_ordering-config-name}

Enter the service name.

### Deployment size
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud}} provides the following deployment size options:
* Small (2 vCPUs / 4 GB RAM)
* Medium (4 vCPUs / 6 GB RAM)
* Large (8 vCPU / 12 GB RAM)

### License model
{: #fortinetvm_ordering-config-license}

The license model for FortiGate Virtual Appliance offers the following options:
* **Standard FW**: This bundle includes Stateful Packet Inspection, VLAN Protection and Advanced Logging, Ingress and Egress Firewall Rules, SSL/IPSec VPN Termination, and continuous support.
* **Standard FW + UTM**: This bundle includes all standard firewall services in addition to the Advanced Malware Protection (AMP) service. It includes Antivirus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Protection Service, and Content Disarm & Reconstruct. It also includes the Web Filtering, IPS, Antispam, Application Control, and FortiCare services.
* **Standard FW + Enterprise**: This bundle includes all standard firewall and UTM services in addition to the following services:
    * Cloud Access Security Broker (CASB): This service provides visibility, compliance, data security, and threat protection for cloud-based services.
    * Industrial Security: This service provides signatures for common ICS/SCADA protocols.
    * Security Rating: This service provides audit capabilities to identify critical vulnerabilities and configuration weaknesses and implement best practice recommendations.

In 3Q 2018, Fortinet added three new services (CASB, Industrial Security, and Security Rating) to their Enterprise bundle. These services are available for FortiGate V6.0 and later only.
{:note}

You can't change the license model after service installation. To change the license model, you must delete the existing service and reinstall the service by selecting a different license option.
{:important}

## Related links
{: #fortinetvm_ordering-related}

* [FortiGate Virtual Appliance overview](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations)
* [Managing FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-managingfortinetvm)
* [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Fortinet website](https://www.fortinet.com/){:external}
* [Fortinet Document Library](https://docs.fortinet.com/product/fortigate/6.2){:external}
