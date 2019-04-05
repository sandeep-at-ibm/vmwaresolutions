---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-07"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices}

You can order services for your VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instance, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instance.

## Available services for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_addingremovingservices-available-services}

The following services are available to vCenter Server with Hybridity Bundle instances, together with the installed service versions.

Table 1. Available services for vCenter Server with Hybridity Bundle instances

| Service name | Current service version | Instance version |
|----------------------------------------------------------------------------------------|------------------|
| [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations) | 2.2 | V2.9 and later |
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE v14.1.0.2 | V1.9 and later |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)       | 300 series | V1.8 and later |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | V2.0 and later |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)              | 5.4.2 | V2.3 and later |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)              | 4.2.1 | V2.3 and later |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)              | 4.2 | V2.5 and later |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | 3.1 | V2.7 and later |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)  | 10.1.2 | V2.2 and later |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)                  | 2.0  | N/A |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)                           | 9.5u4 | V1.8 and later |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vmware-hcx-on-ibm-cloud-overview)                        | 3.5.1 | V2.3 and later |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)                                  | 6.5 update 3 | V1.2 and later |

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

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
