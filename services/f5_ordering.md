---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Ordering F5 on IBM Cloud

You can order the F5 on {{site.data.keyword.cloud}} service while ordering a new instance with BIG-IP Virtual Edition (VE) included or by adding the BIG-IP VE to your existing instance.

## Ordering F5 on IBM Cloud for a new instance

You can order a new instance with F5 on {{site.data.keyword.cloud_notm}} by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, select **F5 on IBM Cloud** in the **Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, select **F5 on IBM Cloud**, specify the service settings, and select **Add to New Instance**.

## Ordering F5 on IBM Cloud for an existing instance

You can add the F5 on {{site.data.keyword.cloud_notm}} service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, select **F5 on IBM Cloud**, specify the service settings and select **Add to Existing Instance**.

## F5 on IBM Cloud service configuration

When you order the service, provide the following settings.

### Name

Enter the service name.

### License model

The license model for F5 on {{site.data.keyword.cloud_notm}} service offers the following options:
<dl class="dl">
        <dt class="dt dlterm">Good</dt>
        <dd class="dd">This offer leverages the BIG-IP Local Traffic Manager™ (LTM) VE, operating as a full-proxy architecture, to provide intelligent local traffic management, complete SSL traffic visibility, and analytics and health monitoring to ensure application servers are always available to your users.</dd>
        <dt class="dt dlterm">Better</dt>
        <dd class="dd">This offer is built on the benefits of the **Good** option, with the addition of BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM), and BIG-IP Application Acceleration Manager™ (AAM) modules. It delivers global traffic management services, application performance optimization, and advanced network firewall and Distributed Denial of Service (DDoS) mitigation capabilities.</dd>
        <dt class="dt dlterm">Best</dt>
        <dd class="dd">In addition to the **Good** and **Better** offers, BIG-IP Application Security Manager™ (ASM) provides comprehensive application protection against L7 DDoS, Open Web Application Security Project (OWASP) top 10 threats and common application vulnerabilities. BIG-IP Access Policy Manager™ (APM) offers users secure, simplified access to applications located anywhere within a multi-cloud environment, incorporating features such as SSO (Single Sign-On) and MFA (Multi-Factor Authentication).</dd>
</dl>

**Important:** You cannot change the license model after service installation. To change the license model, you must remove the existing service and reinstall the service using a different license model.

### Maximum bandwidth

Specify the maximum throughput of the F5 BIG–IP appliance.

### Related links

* [F5 on {{site.data.keyword.cloud_notm}} overview](f5_considerations.html)
* [Managing F5 on {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [Ordering, viewing, and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering, viewing, and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](../vcenter/vc_hybrid_addingremovingservices.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [F5 Deployment Guides](https://f5.com/solutions/deployment-guides){:new_window}
