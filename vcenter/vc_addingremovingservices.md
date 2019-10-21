---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-09"

keywords: vCenter Server add service, view service vCenter Server, remove service vCenter Server

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and removing services for vCenter Server instances
{: #vc_addingremovingservices}

You can order services for your VMware vCenter Server instances, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instances.

A 12-month commitment is required when you order the VMware HCX service. You cannot delete the service until your 12-month period has expired. The 12-month commitment expiration date is available on the HCX details page. For more information about viewing service details, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

## Available services for vCenter Server instances
{: #vc_addingremovingservices-available-services}

The following table shows the services that are available to vCenter Server instances, together with the installed service versions.

| Service name | Current service version | Instance version |
|----------------------------------------------------------------------------------------|------------------|
| [Caveonix RiskForesight](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations) | 2.2.1 | V2.9 and later |
| [F5 BIG-IP](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE v15.0.0 | V1.9 and later |
| [FortiGate Security Appliance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations) | 300 series | V2.0 and later |
| [FortiGate Virtual Appliance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | V2.0 and later |
| [HyTrust CloudControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations) | 5.5.1 | V2.3 and later |
| [HyTrust DataControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)  | 4.3.2 | V2.3 and later |
| [HyTrust KeyControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | 4.3.2 | V2.5 and later |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | 3.1.2 | V2.5 and later |
| [IBM Spectrum Protect&trade; Plus](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations) | 10.1.3 | V2.2 and later |
| [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | 2.0  | N/A  |
| [Veeam](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | 9.5u4b | V1.8 and later |
| [VMware HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations) | 3.5.2 | V2.1 and later |
| [vRealize Operations and Log Insight](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vrops_overview) | vROps 7.5 and vRLI 4.8 | V3.2 and later |
| [Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | 7.0 Update 2 | V1.2 and later |
{: caption="Table 1. Available services for vCenter Server instances" caption-side="top"}

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

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
