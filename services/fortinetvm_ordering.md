---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Ordering FortiGate Virtual Appliance on IBM Cloud

You can order the FortiGate Virtual Appliance on {{site.data.keyword.cloud}} service hen you order a new instance with the service included or by adding the service to your existing instance.

## Ordering FortiGate Virtual Appliance on IBM Cloud for a new instance

You can order a new instance with FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, select **FortiGate Virtual Appliance on IBM Cloud** in the **Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, select **FortiGate Virtual Appliance on IBM Cloud**, specify the service settings, and select **Add to New Instance**.

## Ordering FortiGate Virtual Appliance on IBM Cloud for an existing instance

You can add the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, select **FortiGate Virtual Appliance on IBM Cloud**, specify the service settings, and select **Add to Existing Instance**.

## FortiGate Virtual Appliance on IBM Cloud service configuration

When you order the service, provide the following settings.

### Name

Enter the service name.

### Deployment size

{{site.data.keyword.cloud_notm}} provides the following deployment size options:
* Small (2 vCPUs / 4 GB RAM)
* Medium (4 vCPUs / 6 GB RAM)
* Large (8 vCPU / 12 GB RAM)

### License model

The license model for FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} offers the following options:
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">This bundle includes Stateful Packet Inspection, VLAN Protection and Advanced Logging, Ingress and Egress Firewall Rules, SSL/IPSec VPN Termination, and continuous support.</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">This bundle includes all standard firewall services in addition to NGFW IPS and web Filtering, AntiVirus and AntiSpam, IP and Domain Reputation, and core FortiCare security services.</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">This bundle includes all standard firewall and UTM services in addition to FortiSandbox Cloud and Mobile Security.</dd>
</dl>

**Important:** You cannot change the license model after service installation. To change the license model, you must remove the existing service and reinstall the service by selecting a different license option.

### Related links

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} overview](fortinetvm_considerations.html)
* [Managing FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Ordering, viewing, and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering, viewing, and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](../vcenter/vc_hybrid_addingremovingservices.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet website](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
