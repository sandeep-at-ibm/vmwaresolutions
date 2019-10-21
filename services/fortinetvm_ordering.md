---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-08"

keywords: FortiGate VA, FortiGate configuration, order FortiGate

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering FortiGate Virtual Appliance
{: #fortinetvm_ordering}

You can order the FortiGate Virtual Appliance service when you order a new instance with the service included or by adding the service to your existing instance.

## Ordering FortiGate Virtual Appliance for a new instance
{: #fortinetvm_ordering-new}

You can order a new instance with FortiGate Virtual Appliance by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, click **FortiGate Virtual Appliance** under the **Security and Compliance** category in the **Optional Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click **FortiGate Virtual Appliance** on the **Security and Compliance** card in the **Services** section. Specify the service settings and select **Add to New Instance**.

## Ordering FortiGate Virtual Appliance for an existing instance
{: #fortinetvm_ordering-existing}

You can add the FortiGate Virtual Appliance service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click **FortiGate Virtual Appliance** on the **Security and Compliance** card in the **Services** section. Specify the service settings and select **Add to Existing Instance**.

## Ordering FortiGate Virtual Appliance for private instances
{: #fortinetvm_ordering-private}

When you order FortiGate Virtual Appliance for instances that are not configured with public interfaces, you must provide a proxy server to complete the installation. The HTTP proxy server must be configured and available via Virtual Routing and Forwarding (VRF) before the Fortigate Virtual Appliance installation can start.

To ensure continued operation, FortiGate Virtual Appliance must have persistent access to the Fortigate license server via the internet.

## FortiGate Virtual Appliance service configuration
{: #fortinetvm_ordering-config}

When you order the service, provide the following settings.

### FortiGuard Network Connection
{: #fortinetvm_ordering-config-network-connect}

Select **Public network** or **Private network** for FortiGuard. If the target cluster is configured with private-only network interfaces, only the **Private network** option is available. This selection determines how FortiGuard will contact the Fortinet license server to activate the license and to download security patches, and it doesn't impact the workload data plane.

If you select **Private network**, specify the following settings:
* **Proxy IP Address**: The IPv4 address of the proxy server.
* **Proxy Port Number**: The port number of the proxy server, usually 8080 or 3128.
* **Proxy User Name**: If you require proxy authentication, enter the user name of the proxy server.
* **Proxy Password**: If you require proxy authentication, enter the password of the proxy server.

### Name
{: #fortinetvm_ordering-config-name}

Enter the service name.

### Deployment size
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud_notm}} provides the following deployment size options:
* Small (2 vCPUs / 4 GB RAM)
* Medium (4 vCPUs / 6 GB RAM)
* Large (8 vCPU / 12 GB RAM)

### License model
{: #fortinetvm_ordering-config-license}

The license model for FortiGate Virtual Appliance offers the following options:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">This bundle includes Stateful Packet Inspection, VLAN Protection and Advanced Logging, Ingress and Egress Firewall Rules, SSL/IPSec VPN Termination, and 24 x 7 support.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">This bundle includes all standard firewall services in addition to the Advanced Malware Protection (AMP) service. It includes Antivirus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Protection Service, and Content Disarm & Reconstruct. It also includes the Web Filtering, IPS, Antispam, Application Control, and FortiCare services.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">This bundle includes all standard firewall and UTM services in addition to the following services:<ul><li>Cloud Access Security Broker (CASB) - This service provides visibility, compliance, data security, and threat protection for cloud-based services.</li><li>Industrial Security - This service provides signatures for common ICS/SCADA protocols.</li><li>Security Rating - This service provides audit capabilities to identify critical vulnerabilities and configuration weaknesses and implement best practice recommendations.</li></ul></dd>
</dl>

In 3Q 2018, Fortinet added three new services (CASB, Industrial Security, and Security Rating) to their Enterprise bundle. These services are available on FortiGate 6.0 only.
{:note}

You can't change the license model after service installation. To change the license model, you must remove the existing service and reinstall the service by selecting a different license option.
{:important}

## Related links
{: #fortinetvm_ordering-related}

* [FortiGate Virtual Appliance overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [Managing FortiGate Virtual Appliance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet website](https://www.fortinet.com/){:external}
* [Fortinet Document Library](https://docs.fortinet.com/product/fortigate/6.2){:external}
