---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-24"

---

# Requirements and planning for Cloud Foundation instances

Review the following requirements before you order your VMware Cloud Foundation instances. Plan your instance based on the {{site.data.keyword.CloudDataCent}} location, your workload capacity requirements, and additional service requirements.

## IBM Cloud account requirements

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} account requirements](../vmonic/slaccountrequirement.html).

## IBM Cloud Data Center availability

The Cloud Foundation deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCents_notm}} are available for Cloud Foundation deployment:

Table 1. Available {{site.data.keyword.CloudDataCents_notm}} and {{site.data.keyword.cloud_notm}} Bare Metal Server configurations for Cloud Foundation instances

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region | Server configurations |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europe | Customized |
| CHE01 | Chennai | Asia Pacific | Customized |
| DAL09 | Dallas | NA South | Customized |
| DAL10 | Dallas | NA South | Customized, Small, Large |
| DAL12 | Dallas | NA South | Customized |
| DAL13 | Dallas | NA South | Customized |
| FRA02 | Frankfurt | Europe | Customized, Large |
| FRA04 | Frankfurt | Europe | Customized |
| HKG02 | Hong Kong | Asia Pacific | Customized |
| LON02 | London | Europe | Customized |
| LON04 | London | Europe | Customized |
| LON06 | London | Europe | Customized, Small, Large |
| MEL01 | Melbourne | Asia Pacific | Customized |
| MEX01 | Queretaro | NA South | Customized |
| MIL01 | Milan | Europe | Customized |
| MON01 | Montreal | NA East | Customized |
| OSL01 | Oslo | Europe | Customized |
| PAR01 | Paris | Europe | Customized |
| SAO01 | Sao Paulo | South America | Customized |
| SEO01 | Seoul | Asia Pacific | Customized |
| SJC03 | San Jose | NA West | Customized |
| SJC04 | San Jose | NA West | Customized |
| SNG01 | Singapore | Asia Pacific | Customized |
| SYD01 | Sydney | Asia Pacific | Customized |
| SYD04 | Sydney | Asia Pacific | Customized |
| TOK02 | Tokyo | Asia Pacific | Customized |
| TOR01 | Toronto | NA East | Customized, Small, Large |
| WDC04 | Washington, DC | NA East | Customized, Small, Large |
| WDC06 | Washington, DC | NA East | Customized |
| WDC07 | Washington, DC | NA East | Customized |

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

Table 2. Status indicators for {{site.data.keyword.CloudDataCents_notm}} when ordering Cloud Foundation instances

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.CloudDataCent_notm}} is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.CloudDataCent_notm}} has no availability at this time. |
| Limited Inventory             | The {{site.data.keyword.CloudDataCent_notm}} has limited availability and the order might not be completed. |

## Services for Cloud Foundation instances

When you order a Cloud Foundation instance, you can order additional services.

### FortiGate Security Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Security Appliance (FSA) 300 series devices that can provide firewall, routing, NAT, and VPN services to protect the public network connection to your environment. For more information, see [Managing FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Virtual Appliances that can allow you to reduce risk by implementing critical security controls within your virtual infrastructure. For more information, see [Managing FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html).

### F5 on IBM Cloud

This service optimizes performance and ensures availability and security for applications with the F5 BIG-IP Virtual Edition (VE). For more information, see [Managing F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html).

### HyTrust CloudControl on IBM Cloud

This service provides automated security and compliance support, which gives you better visibility and control over your cloud environment and administrators. For more information, see [HyTrust CloudControl on IBM Cloud considerations](../services/htcc_considerations.html).

### HyTrust DataControl on IBM Cloud

This service protects your data with a powerful encryption and key management solution. The service can secure your workloads throughout their lifecycles. For more information, see [HyTrust DataControl on IBM Cloud considerations](../services/htdc_considerations.html).

### KMIP for VMware on IBM Cloud

This service can provide lifecycle management for encryption keys that are used by {{site.data.keyword.cloud_notm}} services or customer built-in applications. For more information, see [KMIP for VMware on IBM Cloud considerations](../services/kmip_considerations.html).

### Managed Services from IMI

These services enable IBM Integrated Managed Infrastructure (IMI) to deliver dynamic remote management services for a broad range of cloud infrastructures. For more information, see [Requesting managed services from IMI](../services/managing_imi.html).

### IBM Spectrum Protect Plus on IBM Cloud

This service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement it as a stand-alone solution or you can integrate it with your IBM Spectrum Protect&trade; Plus environment to offload copies for long-term storage and data governance.

For more information, see [IBM Spectrum Protect Plus on IBM Cloud considerations](../services/spp_considerations.html).

### Veeam on IBM Cloud

This service integrates seamlessly with your VMware environment to help you manage the backup and restore of all the VMs in your environment, including the backup and restore of the management components. It can help provide a recovery point objective (RPO) of less than 15 minutes upon configuration for your data. For more information, see [Managing Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html).

### Zerto on IBM Cloud

This service provides replication and disaster recovery capabilities to help protect your workloads. For more information, see [Managing Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html).

<!-- ## Capacity considerations

For capacity information and considerations, see the _Bill of Materials_ document on the [Virtualization reference architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page. -->

## Related links

* [Cloud Foundation overview](sd_cloudfoundationoverview.html)
* [Ordering Cloud Foundation instances](sd_orderinginstance.html)
* [Expanding and contracting capacity for Cloud Foundation instances](sd_addingremovingservers.html)
* [Ordering and removing services for Cloud Foundation instances](sd_addingremovingservices.html)
