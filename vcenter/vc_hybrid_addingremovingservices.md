---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-08"

keywords: vCenter Server Hybridity add service, view service vCenter Server Hybridity, remove service vCenter Server Hybridity

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices}

You can order services for your VMware vCenter Server with Hybridity Bundle instance, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instance.

## Available services for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices-available-services}

The following services are available to vCenter Server with Hybridity Bundle instances, together with the installed service versions.

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) | 2.2.2 |
| [F5 BIG-IP](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations) | BIG-IP VE v15.1.0.2 |
| [FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations) | 6.2.3 |
| [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations) | 5.5.1 |
| [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations) | 4.3.2 |
| [HyTrust KeyControl](/docs/vmwaresolutions?topic=vmwaresolutions-htkc_considerations) | 4.3.2 |
| [{{site.data.keyword.IBM}} Spectrum Protect&trade; Plus](/docs/vmwaresolutions?topic=vmwaresolutions-spp_considerations) | 10.1.3 |
| [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-vsrx_overview) | 18.4  |
| [KMIP for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) | 2.0  |
| [Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations) | 9.5u4b |
| [HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations#hcx_considerations) | 3.5.2 |
| [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview) | vROps 7.5 and vRLI 4.8 |
| [Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-addingzertodr) | 7.0 Update 2 |
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

* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
