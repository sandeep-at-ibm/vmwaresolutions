---

copyright:

  years:  2016, 2019

lastupdated: "2019-12-04"

keywords: vCenter Server Hybridity add service, view service vCenter Server Hybridity, remove service vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices}

You can order services for your vCenter Server with Hybridity Bundle instance, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instance.

## Available services for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices-available-services}

The following services are available to vCenter Server with Hybridity Bundle instances, together with the installed service versions.

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_considerations) | 2.2.1 |
| [F5 BIG-IP](/docs/services/vmwaresolutions?topic=vmware-solutions-f5_considerations) | BIG-IP VE v15.0.0 |
| [FortiGate Security Appliance](/docs/services/vmwaresolutions?topic=vmware-solutions-fsa_considerations) | 300 series |
| [FortiGate Virtual Appliance](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 |
| [HyTrust CloudControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htcc_considerations) | 5.5.1 |
| [HyTrust DataControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htdc_considerations) | 4.3.2 |
| [HyTrust KeyControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htkc_considerations) | 4.3.2 |
| [IBM Spectrum Protect&trade; Plus](/docs/services/vmwaresolutions?topic=vmware-solutions-spp_considerations) | 10.1.3 |
| [KMIP for VMware](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations) | 2.0  |
| [Veeam](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations) | 9.5u4b |
| [HCX](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations) | 3.5.2 |
| [vRealize Operations and Log Insight](/docs/services/vmwaresolutions?topic=vmware-solutions-vrops_overview) | vROps 7.5 and vRLI 4.8 |
| [Zerto](/docs/services/vmwaresolutions?topic=vmware-solutions-addingzertodr) | 7.0 Update 2 |
{: caption="Table 1. Available services for vCenter Server with Hybridity Bundle instances" caption-side="top"}

## Procedure to add services to vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices-adding-procedure}

To apply a service to your vCenter Server with Hybridity Bundle instance, click the links in the table to review the considerations for the service. Then, check the components that are deployed and follow the instructions in the ordering topics to place your order.

### Service installation results
{: #vc_hybrid_addingremovingservices-adding-results}

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** tab of the instance details with the **Installed** status.

## Procedure to view services for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** on the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to view services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, click a service to review information about it, such as the service status and other details.
5. Depending on the viewed service, you can access the service consoles using the credentials provided on the service details and you can manage the service from here.

## Procedure to remove services for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to remove services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, locate the service instance that you want to remove and click the **Delete** icon.
5. In the **Delete Service** window, review the considerations or warnings if there are any. Select **I Understand** and click **Delete**.

### Service removal results
{: #vc_hybrid_addingremovingservices-removing-results}

After your request for service removal is accepted, the service status is changed to **Removing**.

When the removal of the service is completed successfully, you are notified by email, and the service is removed from the **Services** page of the instance.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed services.
{:note}

## Related links
{: #vc_hybrid_addingremovingservices-related}

* [FAQ](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
