---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering F5 on IBM Cloud
{: #f5_ordering}

You can order the F5 on {{site.data.keyword.cloud}} service when you order a new instance with the service included or by adding the service to your existing instance.

## Ordering F5 on IBM Cloud for a new instance
{: #f5_ordering-new}

You can order a new instance with F5 on {{site.data.keyword.cloud_notm}} by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, select **F5 on IBM Cloud** in the **Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, select **F5 on IBM Cloud**, specify the service settings, and select **Add to New Instance**.

## Ordering F5 on IBM Cloud for an existing instance
{: #f5_ordering-existing}

You can add the F5 on {{site.data.keyword.cloud_notm}} service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, select **F5 on IBM Cloud**, specify the service settings, and select **Add to Existing Instance**.

## F5 on IBM Cloud service configuration
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

The license model for F5 on {{site.data.keyword.cloud_notm}} service offers the following options:
<dl class="dl">
        <dt class="dt dlterm">Good</dt>
        <dd class="dd">This offer uses the BIG-IP Local Traffic Manager™ (LTM) VE, operating as a full-proxy architecture, to provide intelligent local traffic management, complete SSL traffic visibility, and analytics and health monitoring to ensure that application servers are always available to your users.</dd>
        <dt class="dt dlterm">Better</dt>
        <dd class="dd">This offer is built on the benefits of the **Good** option, with the addition of BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM), and BIG-IP Application Acceleration Manager™ (AAM) modules. It delivers global traffic management services, application performance optimization, and advanced network firewall and Distributed Denial of Service (DDoS) mitigation capabilities.</dd>
        <dt class="dt dlterm">Best</dt>
        <dd class="dd">In addition to the **Good** and **Better** offers, BIG-IP Application Security Manager™ (ASM) provides comprehensive application protection against L7 DDoS, Open Web Application Security Project (OWASP) top 10 threats, and common application vulnerabilities. BIG-IP Access Policy Manager™ (APM) offers users secure, simplified access to applications located anywhere within a multi-cloud environment, incorporating features such as SSO (Single Sign-On) and MFA (Multi-Factor Authentication).</dd>
</dl>

You cannot change the license model after service installation. To change the license model, you must remove the existing service and reinstall the service by choosing a different license model.
{:important}

## Related links
{: #f5_ordering-releated}

* [F5 on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services/f5_considerations.html)
* [Managing F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managing_f5.html)
* [Ordering, viewing, and removing services for Cloud Foundation instances](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter/vc_hybrid_addingremovingservices.html)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [FAQ](/docs/services/vmwaresolutions/vmonic/faq.html)
* [F5 Deployment Guides](https://f5.com/solutions/deployment-guides){:new_window}
