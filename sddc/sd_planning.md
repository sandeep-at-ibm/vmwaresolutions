---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-17"

---

# Requirements and planning for Cloud Foundation instances

Review the following requirements before you order your VMware Cloud Foundation instances. Plan your instance based on the {{site.data.keyword.CloudDataCent}} location, your workload capacity requirements, and additional service requirements.

## IBM Cloud account requirements

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} account requirements](../vmonic/slaccountrequirement.html).

## IBM Cloud Data Center availability

The Cloud Foundation deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCents_notm}} are available for Cloud Foundation deployment:

Table 1. Available {{site.data.keyword.CloudDataCents_notm}} and {{site.data.keyword.cloud_notm}} Bare Metal Server configurations for Cloud Foundation instances

| IBM Cloud Data Center | Location | Server configurations |
|:-----|:----------------| :---------------------------|
| AMS03 | Amsterdam | Customized |
| CHE01 | Chennai | Customized |
| DAL09 | Dallas | Customized |
| DAL10 | Dallas | Customized, Small, Large |
| DAL12 | Dallas | Customized |
| DAL13 | Dallas | Customized |
| FRA02 | Frankfurt | Customized, Small, Large |
| HKG02 | Hong Kong | Customized |
| LON02 | London | Customized |
| LON04 | London | Customized |
| LON06 | London | Customized, Small, Large |
| MEL01 | Melbourne | Customized |
| MEX01 | Queretaro | Customized |
| MIL01 | Milan | Customized |
| MON01 | Montreal | Customized |
| OSL01 | Oslo | Customized |
| PAR01 | Paris | Customized |
| SAO01 | Sao Paulo | Customized |
| SEO01 | Seoul | Customized |
| SJC03 | San Jose | Customized, Small, Large |
| SJC04 | San Jose | Customized |
| SNG01 | Singapore | Customized |
| SYD01 | Sydney | Customized |
| SYD04 | Sydney | Customized |
| TOK02 | Tokyo | Customized |
| TOR01 | Toronto | Customized, Small, Large |
| WDC03 | Washington, DC | Customized |
| WDC04 | Washington, DC | Customized, Small, Large |
| WDC06 | Washington, DC | Customized |
| WDC07 | Washington, DC | Customized |

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_full}} console to help you plan your deployments.

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

### HCX on IBM Cloud

This service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change. For more information, see [Managing HCX on IBM Cloud](../services/managinghcx.html).

### KMIP for VMware on IBM Cloud

This service can provide lifecycle management for encryption keys that are used by {{site.data.keyword.cloud_notm}} services or customer built-in applications. For more information, see [KMIP for VMware on IBM Cloud considerations](../services/kmip_considerations.html).

### Managed Services from IMI

These services enable IBM Integrated Managed Infrastructure (IMI) to deliver dynamic remote management services for a broad range of cloud infrastructures. For more information, see [Requesting managed services from IMI](../services/managing_imi.html).

### IBM Spectrum Protect Plus on IBM Cloud

This service provides data protection, data reuse, and recovery tools for virtual environments. It can be implemented as a stand-alone solution or integrated with your IBM Spectrum Protect&trade; Plus environment to offload copies for long-term storage and data governance with scale and efficiency.

The IBM Spectrum Protect Plus on IBM Cloud service provides data protection for the workload VMs only. For more information, see [Managing IBM Spectrum Protect Plus on IBM Cloud](../services/managingspp.html).

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
