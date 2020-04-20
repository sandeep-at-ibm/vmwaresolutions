---

copyright:

  years:  2016, 2020

lastupdated: "2019-04-14"

keywords: F5 license activation, F5 configuration, order F5

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering F5 BIG-IP
{: #f5_ordering}

You can include the F5 BIG-IP service with a new vCenter Server instance or add the service to your existing vCenter Server instance.

## Ordering F5 BIG-IP for a new instance
{: #f5_ordering-new}

When you [order the instance](/docs/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the **Optional Services** section and click **F5 BIG-IP** in the **Security and Compliance** category. Follow the steps to add the service to your instance.

## Ordering F5 BIG-IP for an existing instance
{: #f5_ordering-existing}

On the [instance details page](/docs/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances), click **Services** on the left navigation pane, click **F5 BIG-IP** in the **Security and Compliance** category, and then click **Add**. Follow the steps to add the service to your instance.

## Ordering F5 BIG-IP for private instances
{: #f5_ordering-private}

When you order F5 BIG-IP for instances that are not configured with public interfaces, you must provide a proxy server to complete the installation. The HTTP proxy server must be configured and available via Virtual Routing and Forwarding (VRF) before the F5 BIG-IP installation can begin.

The BigIP Virtual Edition (VE) endpoints must be able to activate their license before becoming operational. After the BigIP VE endpoints are installed, they no longer require the use of the proxy server.

The F5 BIG-IP service cannot be added without a working proxy server at the time of service installation.
{:note}

## F5 BIG-IP service configuration
{: #f5_ordering-config}

When you order the service, provide the following settings.

### F5 License Activation Connection
{: #f5_ordering-config-license}

Select **Public network** or **Private network** for license activation. If the target cluster is configured with private-only network interfaces, only the **Private network** option is available. This selection determines how the F5 virtual servers will contact the F5 license server, and it does not impact the workload data plane.

If you select **Private network**, specify the following settings:
* **Proxy IP Address**: The IPv4 address of the proxy server.
* **Proxy Port Number**: The port number of the proxy server, usually 8080 or 3128.

Authenticated proxy is not supported.
{:note}

### Name
{: #f5_ordering-config-name}

Enter the service name.

### Maximum bandwidth
{: #f5_ordering-config-bandwidth}

Specify the maximum throughput of the F5 BIG–IP appliance.

### License model
{: #f5_ordering-config-license-model}

The license model for F5 BIG-IP offers the following options:
* **Good**: This offer uses the BIG-IP Local Traffic Manager™ (LTM) VE, operating as a full-proxy architecture, to provide intelligent local traffic management, complete SSL traffic visibility, and analytics and health monitoring to ensure that application servers are always available to your users.
* **Better**: This offer is built on the benefits of the **Good** option, with the addition of BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM), and BIG-IP Application Acceleration Manager™ (AAM) modules. It delivers global traffic management services, application performance optimization, and advanced network firewall and Distributed Denial of Service (DDoS) mitigation capabilities.
* **Best**: In addition to the **Good** and **Better** offers, BIG-IP Application Security Manager™ (ASM) provides comprehensive application protection against L7 DDoS, Open Web Application Security Project (OWASP) top 10 threats, and common application vulnerabilities. BIG-IP Access Policy Manager™ (APM) offers users secure, simplified access to applications located anywhere within a multi-cloud environment, incorporating features such as SSO (Single Sign-On) and MFA (Multi-Factor Authentication).

You cannot change the license model after service installation. To change the license model, you must remove the existing service and reinstall the service by choosing a different license model.
{:important}

## Related links
{: #f5_ordering-related}

* [F5 BIG-IP overview](/docs/vmwaresolutions?topic=vmware-solutions-f5_considerations)
* [Managing F5 BIG-IP](/docs/vmwaresolutions?topic=vmware-solutions-managing_f5)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices)
* [Contacting {{site.data.keyword.IBM}} Support](/docs/vmwaresolutions?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmware-solutions-faq-vmwaresolutions)
* [F5 Deployment Guides](https://www.f5.com/services/resources/deployment-guides){:external}
