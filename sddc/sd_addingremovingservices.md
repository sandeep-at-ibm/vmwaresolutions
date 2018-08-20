---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Ordering, viewing, and removing services for Cloud Foundation instances

You can order services for your VMware Cloud Foundation instances, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instances.

## Available services for Cloud Foundation instances

The following table shows the services that are available to Cloud Foundation instances.

Table 1. Available services for Cloud Foundation instances

| Service name | Availability | Instance support |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](../services/f5_considerations.html)                                 | Yes | V1.9 and later |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html)       | Yes | V1.8 and later |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | Yes | V2.0 and later |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)              | Yes | V2.3 and later |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)              | Yes | V2.3 and later |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](../services/spp_considerations.html)         | Yes | V2.2 and later |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html)                  | Yes | V2.2 and later |
| [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)                          | Yes | V1.8 and later |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)                         | No | Not applicable |
| [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html)                                 | Yes | V1.2 and later |

## Adding services to Cloud Foundation instances

To add a service to your Cloud Foundation instance, click the appropriate service link in the previous table to review the considerations for the service and check the components that are deployed. Then, follow the instructions in the service ordering topic to add the service to your instance.

### Service installation results

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** page of the instance with the **Installed** status.

## Viewing services for Cloud Foundation instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **Cloud Foundation Instances** table, click the instance for which you want to view services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, click a service to review information about it, such as the service status and other details.
5. Depending on the viewed service, you can access the service consoles using the credentials provided on the service details and you can manage the service from here.

## Removing services for Cloud Foundation instances

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation Instances** table, click the instance for which you want to remove services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, locate the service instance that you want to remove and click the **Delete** icon.
5. In the **Delete Service** window, review the considerations or warnings if there are any. Select **I Understand** and click **Delete**.

### Service removal results

After your request for service removal is accepted, the service status is changed to **Removing**.

When the removal of the service is completed successfully, you are notified by email, and the service is removed from the **Services** page of the instance.

**Attention**: You are billed until the end of the {{site.data.keyword.cloud_notm}} billing cycle for the removed services.

### Related links

* [FAQ](../vmonic/faq.html)
