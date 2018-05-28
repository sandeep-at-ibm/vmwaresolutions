---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-24"

---

# Requirements and planning for vCenter Server with Hybridity Bundle instances

Review the following requirements before you order your VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instance. Plan your instance based on the {{site.data.keyword.CloudDataCent_notm}} location, your workload capacity requirements, and additional service requirements.

## IBM Cloud account requirements

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} account requirements](../vmonic/slaccountrequirement.html).

## IBM Cloud Data Center availability

The vCenter Server with Hybridity Bundle deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCents_notm}} are available for vCenter Server with Hybridity Bundle deployment:

Table 1. Available {{site.data.keyword.CloudDataCents_notm}} for vCenter Server with Hybridity Bundle instances

| IBM Cloud Data Center | Location | Region |
|:-----|:----------------|
| AMS03 | Amsterdam | Europe |
| CHE01 | Chennai | Asia Pacific |
| DAL09 | Dallas | NA South |
| DAL10 | Dallas | NA South |
| DAL12 | Dallas | NA South |
| DAL13 | Dallas | NA South |
| FRA02 | Frankfurt | Europe |
| FRA04 | Frankfurt | Europe |
| HKG02 | Hong Kong | Asia Pacific |
| LON02 | London | Europe |
| LON04 | London | Europe |
| LON06 | London | Europe |
| MEL01 | Melbourne | Asia Pacific |
| MEX01 | Queretaro | NA South |
| MIL01 | Milan | Europe |
| MON01 | Montreal | NA East |
| OSL01 | Oslo | Europe |
| PAR01 | Paris | Europe |
| SAO01 | Sao Paulo | South America |
| SEO01 | Seoul | Asia Pacific |
| SJC03 | San Jose | NA West |
| SJC04 | San Jose | NA West |
| SNG01 | Singapore | Asia Pacific |
| SYD01 | Sydney | Asia Pacific |
| SYD04 | Sydney | Asia Pacific |
| TOK02 | Tokyo | Asia Pacific |
| TOR01 | Toronto | NA East |
| WDC04 | Washington, DC | NA East |
| WDC06 | Washington, DC | NA East |
| WDC07 | Washington, DC | NA East |

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_full}} console to help you plan your deployments.

Table 2. Status indicators for {{site.data.keyword.CloudDataCents_notm}} when ordering vCenter Server with Hybridity Bundle instances

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.CloudDataCent_notm}} is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.CloudDataCent_notm}} has no availability at this time. |
| Limited Inventory             | The {{site.data.keyword.CloudDataCent_notm}} has limited availability and the order might not be completed. |

## Services for vCenter Server with Hybridity Bundle instances

The vCenter Server with Hybridity Bundle instance includes the VMware Hybrid Cloud Extension (HCX) licensing and entitles you to the VMware HCX on IBM Cloud service. This service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

When you deploy this service, select the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
* **Certificate Contents**: Enter the contents of the CA certificate.
* **Private Key**: Enter the private key of the CA certificate.
* (Optional) **Password**: Enter the password for the private key if it is encrypted.
* (Optional) **Reenter Password**: Enter the password for the private key again.
* (Optional) **Hostname**: Enter the host name to be mapped to the common name (CN) of the CA certificate. HCX on {{site.data.keyword.cloud_notm}} requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

You can order the following additional services:

### FortiGate Security Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Security Appliance (FSA) 300 series devices that can provide firewall, routing, NAT, and VPN services to protect the public network connection to your environment. For more information, see [Managing FortiGate Security Appliance on IBM Cloud](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Virtual Appliances that can allow you to reduce risk by implementing critical security controls within your virtual infrastructure. For more information, see [Managing FortiGate Virtual Appliance on IBM Cloud](../services/managingfortinetvm.html).

### F5 on IBM Cloud

This service optimizes performance and ensures availability and security for applications with the F5 BIG-IP Virtual Edition (VE). For more information, see [Managing F5 on IBM Cloud](../services/managing_f5.html).

### HyTrust CloudControl on IBM Cloud

This service provides automated security and compliance support, which gives you better visibility and control over your cloud environment and administrators. For more information, see [HyTrust CloudControl on IBM Cloud considerations](../services/htcc_considerations.html).

### HyTrust DataControl on IBM Cloud

This service protects your data with a powerful encryption and key management solution. The service can secure your workloads throughout their lifecycle. For more information, see [HyTrust DataControl on IBM Cloud considerations](../services/htdc_considerations.html).

### KMIP for VMware on IBM Cloud

This service can provide lifecycle management for encryption keys that are used by {{site.data.keyword.cloud_notm}} services or customer built-in applications. For more information, see [KMIP for VMware on IBM Cloud considerations](../services/kmip_considerations.html).

### IBM Spectrum Protect Plus on IBM Cloud

This service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement it as a stand-alone solution or you can integrate it with your IBM Spectrum Protect&trade; Plus environment to offload copies for long-term storage and data governance.

For more information, see [IBM Spectrum Protect Plus on IBM Cloud considerations](../services/spp_considerations.html).

### Veeam on IBM Cloud

This service integrates seamlessly with your VMware environment to help you manage the backup and restore of all the virtual machines (VMs) in your environment, including the backup and restore of the management components. It can help provide a recovery point objective (RPO) of less than 15 minutes upon configuration for your data. For more information, see [Managing Veeam on IBM Cloud](../services/managingveeam.html).

### Zerto on IBM Cloud

This service provides replication and disaster recovery capabilities to help protect your workloads. For more information, see [Managing Zerto on IBM Cloud](../services/managingzertodr.html).

## Related links

* [vCenter Server with Hybridity Bundle overview](vc_hybrid_overview.html)
* [Ordering vCenter Server with Hybridity Bundle instances](vc_hybrid_orderinginstance.html)
* [Expanding and contracting capacity for vCenter Server with Hybridity Bundle instances](vc_hybrid_addingremovingservers.html)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](vc_hybrid_addingremovingservices.html)
