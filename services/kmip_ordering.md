---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-20"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Ordering KMIP for VMware on IBM Cloud - Deprecated

The current version of KMIP for VMware on IBM Cloud is being deprecated. For more information, [contact IBM Support](../vmonic/trbl_support.html).
{:deprecated}

You can order the KMIP for VMware on {{site.data.keyword.cloud}} service while you order a new instance with the service included or by adding service to your existing instance.

## Ordering KMIP for VMware on IBM Cloud for a new instance

You can order a new instance with KMIP for VMware on {{site.data.keyword.cloud_notm}} by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, select **KMIP for VMware on IBM Cloud** in the **Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, select **KMIP for VMware on IBM Cloud**, specify the service settings, and select **Add to New Instance**.

## Ordering KMIP for VMware on IBM Cloud for an existing instance

You can add the KMIP for VMware on {{site.data.keyword.cloud_notm}} service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, select **KMIP for VMware on IBM Cloud**, specify the service settings, and select **Add to Existing Instance**.

## KMIP for VMware on IBM Cloud service configuration

When you order this service, provide the following settings:

### Service Region

Select the {{site.data.keyword.cloud_notm}} region where your KMIP for VMware {{site.data.keyword.cloud_notm}} service instance is to be hosted.

{{site.data.keyword.cloud_notm}} maintains a highly available KMIP for VMware on {{site.data.keyword.cloud_notm}} service endpoint in each region where the service is available.

### Client SSL Certificate

For vCenter Server, you must configure a Key Management Server (KMS) cluster. The endpoint in your selected region securely connects to the KMS through the client SSL certificate. See the following table for the endpoint in each region. These endpoints use self-signed certificates that are maintained by the {{site.data.keyword.vmwaresolutions_short}} team. The thumbprint for the certificates is `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`.

Table 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} service endpoint regions

| Region         | Endpoint               |
|:---------------|:-----------------------|
| Germany        |  `161.156.68.107:5696` |
| Sydney         |  `130.198.73.134:5696` |
| United Kingdom |  `158.175.93.122:5696` |
| US South       |  `169.60.185.42:5696`  |

This setting is optional at the time of initial configuration. You can leave this field blank because the client certificate of the KMS in vCenter Server is known after your instance is deployed. But you must enter the certificate after your instance is deployed so that your vCenter Server connection to the KMS can be completed successfully.

### API Key for Service ID

Enter the API key for the {{site.data.keyword.cloud_notm}} Service ID that is used to access the IBM Key Protect Service instance.

### Key Protect Instance

Click **Retrieve** to get the list of available IBM Key Protect Service instances and select the one to use for key management.

### Customer Root Key

Click **Retrieve** to get the customer root key that is stored in your selected IBM Key Protect instance.

### Related links

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} overview](kmip_considerations.html)
* [Ordering, viewing, and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering, viewing, and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](../vcenter/vc_hybrid_addingremovingservices.html)
* [{{site.data.keyword.cloudaccesstrailshort}} events](../vmonic/at-events.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](../../keymgmt/index.html)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [FAQ](../vmonic/faq.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
