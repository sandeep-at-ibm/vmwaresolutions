---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-01"

keywords: vCenter Server add service, view service vCenter Server, remove service vCenter Server

subcollection: vmwaresolutions

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and deleting services for vCenter Server instances
{: #vc_addingremovingservices}

You can order services for your VMware vCenter Server instances, such as a disaster recovery solution. When you no longer need these services, you can delete them from your instances.

Only a limited number of add-on services are supported for vCenter Server with NSX-T instances.
{:important}

## Available services for vCenter Server instances
{: #vc_addingremovingservices-available-services}

The tables in the following two sections show the services that are available to vCenter Server instances, together with the installed service versions.

### Available services for vCenter Server with NSX-V instances
{: #vc_addingremovingservices-available-services-nsx-v}

The following table shows the services available for vCenter Server with NSX-V instances:

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) | 2.3 |
| [F5 BIG-IP](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations) | BIG-IP VE v15.1.0.2 |
| [FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations) | 6.2.3 |
| [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations) | 5.6 |
| [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)  | 5.1.1 |
| [HyTrust KeyControl](/docs/vmwaresolutions?topic=vmwaresolutions-htkc_considerations) | 5.0.1 |
| [{{site.data.keyword.IBM}} Security Services for SAP](/docs/vmwaresolutions?topic=vmwaresolutions-managing-ss-sap) | N/A |
| [IBM Spectrum Protect&trade; Plus](/docs/vmwaresolutions?topic=vmwaresolutions-spp_considerations) | V10.1.5 |
| [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-vsrx_overview) | 18.4 |
| [KMIP for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) | 2.0 |
| [PrimaryIO HDM](/docs/vmwaresolutions?topic=vmwaresolutions-managing_pio) | N/A |
| [Red Hat OpenShift for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview) | 4.4.5 |
| [Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations) | 10 |
| [VMware HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations#hcx_considerations) (See **Note**) | 3.5.2 |
| [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview) | vROps 7.5 and vRLI 4.8 |
| [Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-addingzertodr) | 7.5 Update 3 |
{: caption="Table 1. Available services for vCenter Server with NSX-V instances" caption-side="top"}

A 12-month commitment is required when you order the VMware HCX service. You cannot delete the service until your 12-month period has expired. The 12-month commitment expiration date is available on the HCX details page. For more information about viewing service details, see [Procedure to view services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

### Available services for vCenter Server with NSX-T instances
{: #vc_addingremovingservices-available-services-nsx-t}

The following table shows the services available for vCenter Server with NSX-T instances:

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) | 2.3 |
| [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations) | 6.1 |
| [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)  | 5.1.1 |
| [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-vsrx_overview) | 18.4 |
| [Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations) | 10 |
| [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview) | vROps 7.5 and vRLI 4.8 |
{: caption="Table 2. Available services for vCenter Server with NSX-T instances" caption-side="top"}

## Procedure to add services to vCenter Server instances
{: #vc_addingremovingservices-adding-procedure}

To add a service to your vCenter Server instance, click the appropriate service link in the previous table to review the considerations for the service and to check the components that are deployed. Then, follow the instructions in the service ordering topic to add the service to your instance.

### Service installation results
{: #vc_addingremovingservices-adding-results}

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** page of the instance with the **Installed** status.

## Procedure to view services for vCenter Server instances
{: #vc_addingremovingservices-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** on the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to view services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, click a service to review information about it, such as the service status and other details.
5. Depending on the viewed service, you can access the service consoles by using the credentials that are provided on the service details and you can manage the service from here.

The 12-month commitment expiration date for the VMware HCX is available on the HCX details page.
{:note}

## Procedure to delete services for vCenter Server instances
{: #vc_addingremovingservices-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to delete services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, locate the service instance that you want to delete, click the vertical overflow menu next to the **Status** column, and then click **Delete service**.
5. In the **Remove service** window, review the considerations or warnings if there are any and select **I Understand**. Click **Delete**.

### Results after you delete a service
{: #vc_addingremovingservices-removing-results}

After your request to delete a service is accepted, the service status is changed to **Removing**.

When the service deletion is completed successfully, you are notified by email, and the service is deleted from the **Services** page of the instance.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted services.
{:note}

## Related links
{: #vc_addingremovingservices-related}

* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
