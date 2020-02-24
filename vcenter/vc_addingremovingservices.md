---

copyright:

  years:  2016, 2020

lastupdated: "2020-02-21"

keywords: vCenter Server add service, view service vCenter Server, remove service vCenter Server

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and removing services for vCenter Server with NSX-V instances
{: #vc_addingremovingservices}

You can order services for your VMware vCenter Server instances, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instances.

Add-on services are not supported for vCenter Server with NSX-T instances.
{:important}

## Available services for vCenter Server instances
{: #vc_addingremovingservices-available-services}

The following table shows the services that are available to vCenter Server instances, together with the installed service versions.

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_considerations) | 2.2.2 |
| [F5 BIG-IP](/docs/services/vmwaresolutions?topic=vmware-solutions-f5_considerations) | BIG-IP VE v15.1 |
| [FortiGate Virtual Appliance](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations) | 6.2.3 |
| [HyTrust CloudControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htcc_considerations) | 5.6 |
| [HyTrust DataControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htdc_considerations)  | 5.0.1 |
| [HyTrust KeyControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htkc_considerations) | 5.0.1 |
| [{{site.data.keyword.IBM}} Security Services for SAP](/docs/services/vmwaresolutions?topic=vmware-solutions-managing-ss-sap) | N/A |
| [IBM Spectrum Protect&trade; Plus](/docs/services/vmwaresolutions?topic=vmware-solutions-spp_considerations) | V10.1.5 |
| [Juniper vSRX](/docs/services/vmwaresolutions?topic=vmware-solutions-vsrx_overview) | 18.4 |
| [KMIP for VMware](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations) | 2.0 |
| [PrimaryIO HDM](/docs/services/vmwaresolutions?topic=vmware-solutions-managing_pio) | N/A |
| [Red Hat OpenShift for VMware](/docs/services/vmwaresolutions?topic=vmware-solutions-ocp_overview) | 4.2.16 |
| [Veeam](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations) | 9.5u4b |
| [VMware HCX](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations) (See **Note**) | 3.5.2 |
| [vRealize Operations and Log Insight](/docs/services/vmwaresolutions?topic=vmware-solutions-vrops_overview) | vROps 7.5 and vRLI 4.8 |
| [Zerto](/docs/services/vmwaresolutions?topic=vmware-solutions-addingzertodr) | 7.0 Update 2 |
{: caption="Table 1. Available services for vCenter Server instances" caption-side="top"}

A 12-month commitment is required when you order the VMware HCX service. You cannot delete the service until your 12-month period has expired. The 12-month commitment expiration date is available on the HCX details page. For more information about viewing service details, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

## Procedure to add services to vCenter Server instances
{: #vc_addingremovingservices-adding-procedure}

To add a service to your vCenter Server instance, click the appropriate service link in the previous table to review the considerations for the service and to check the components that are deployed. Then, follow the instructions in the service ordering topic to add the service to your instance.

### Service installation results
{: #vc_addingremovingservices-adding-results}

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** page of the instance with the **Installed** status.

## Procedure to view services for vCenter Server instances
{: #vc_addingremovingservices-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** on the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to view services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, click a service to review information about it, such as the service status and other details.
5. Depending on the viewed service, you can access the service consoles by using the credentials that are provided on the service details and you can manage the service from here.

The 12-month commitment expiration date for the VMware HCX is available on the HCX details page.
{:note}

## Procedure to remove services for vCenter Server instances
{: #vc_addingremovingservices-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance for which you want to remove services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, locate the service instance that you want to remove and click the **Delete** icon.
5. In the **Delete Service** window, review the considerations or warnings if there are any. Select **I Understand** and click **Delete**.

### Service removal results
{: #vc_addingremovingservices-removing-results}

After your request for service removal is accepted, the service status is changed to **Removing**.

When the removal of the service is completed successfully, you are notified by email, and the service is removed from the **Services** page of the instance.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the removed services.
{:note}

## Related links
{: #vc_addingremovingservices-related}

* [FAQ](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
