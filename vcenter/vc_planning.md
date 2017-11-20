---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-10"

---

# Requirements and planning for vCenter Server instances

Review the following requirements before you order your VMware vCenter Server instances. Plan your instance based on the IBM Cloud data center location, your workload capacity requirements, and additional service requirements.

## IBM Cloud infrastructure account requirements

The {{site.data.keyword.cloud}} infrastructure account that you are using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} account requirements](../vmonic/slaccountrequirement.html).

## Data centers availability

The vCenter Server deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in IBM® Cloud data centers that meet the requirements. The following data centers are available for vCenter Server deployment:

Table 1. Available data centers for vCenter Server instances

| Data center | Location | Standardized server options |
|:-----|:----------------| :---------------------------|
| AMS03 | Amsterdam | Small, Medium, Large, Custom |
| CHE01 | Chennai | Small, Medium, Large, Custom |
| DAL09 | Dallas | Custom |
| DAL10 | Dallas | Small, Medium, Large, Custom |
| DAL12 | Dallas | Custom |
| DAL13 | Dallas | Custom |
| FRA02 | Frankfurt | Small, Medium, Large, Custom |
| HKG02 | Hong Kong | Small, Medium, Large, Custom |
| LON02 | London | Small, Medium, Large, Custom |
| LON04 | London | Custom |
| LON06 | London | Custom |
| MEL01 | Melbourne | Small, Medium, Large, Custom |
| MEX01 | Queretaro | Small, Medium, Large, Custom |
| MIL01 | Milan | Small, Medium, Large, Custom |
| MON01 | Montreal | Small, Medium, Large, Custom |
| OSL01 | Oslo | Small, Medium, Large, Custom |
| PAR01 | Paris | Small, Medium, Large, Custom |
| SAO01 | Sao Paulo | Small, Medium, Large, Custom |
| SEO01 | Seoul | Custom |
| SJC03 | San Jose | Small, Medium, Large, Custom |
| SJC04 | San Jose | Custom |
| SNG01 | Singapore | Small, Medium, Large, Custom |
| SYD01 | Sydney | Small, Medium, Large, Custom |
| SYD04 | Sydney | Small, Medium, Large, Custom |
| TOK02 | Tokyo | Small, Medium, Large, Custom |
| TOR01 | Toronto | Small, Medium, Large, Custom |
| WDC04 | Washington, DC | Small, Medium, Large, Custom |
| WDC06 | Washington, DC | Custom |
| WDC07 | Washington, DC | Custom |

A large subset of IBM Cloud data centers offer pre-built, standardized **Small**, **Medium**, and **Large** bare metal server options. Depending on availability and inventory supply, IBM Cloud data centers might display a status indicator in the {{site.data.keyword.vmwaresolutions_full}} console to help you plan your deployments.

Table 2. Status indicators for data centers when ordering vCenter Server instances

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The data center is not available currently. |
| Temporarily Out of Inventory  | The data center has no availability at this time. |
| Limited Inventory             | The data center has limited availability and the order might not be completed. |

## Services for vCenter Server instances

When you order a vCenter Server instance, you can also order additional services.

### Veeam on IBM Cloud

This service integrates seamlessly with your VMware environment to help you manage the backup and restore of all the virtual machines (VMs) in your environment, including the backup and restore of the management components. It can help provide a recovery point objective (RPO) of less than 15 minutes upon configuration for your data.

This service is selected by default and is configured to back up the management VMs immediately after the deployment of your instance. If you do not order this service, there is no backup of the management VMs. For more information, see [Managing Veeam on IBM Cloud](../services/managingveeam.html).

### F5 on IBM Cloud

This service optimizes performance and ensures availability and security for applications with the F5 BIG-IP Virtual Edition (VE). For more information, see [Managing F5 on IBM Cloud](../services/managing_f5.html).

### FortiGate Security Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Security Appliance (FSA) 300 series devices that can provide firewall, routing, NAT, and VPN services to protect the public network connection to your environment. For more information, see [Managing FortiGate Security Appliance on IBM Cloud](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Virtual Appliances that can allow you to reduce risk by implementing critical security controls within your virtual infrastructure. For more information, see [Managing FortiGate Virtual Appliance on IBM Cloud](../services/managingfortinetvm.html).

### Zerto on IBM Cloud

This service provides replication and disaster recovery capabilities to help protect your workloads. For more information, see [Managing Zerto on IBM Cloud](../services/managingzertodr.html).

## Capacity considerations

For capacity information and considerations, see the _Bill of
Materials_ document in the [Architecture Center](https://www.ibm.com/devops/method/content/architecture/virtVCenterServerPlatform){:new_window}.

## Related links

* [vCenter Server overview](vc_vcenterserveroverview.html)
* [Ordering vCenter Server instances](vc_orderinginstance.html)
* [Expanding and contracting capacity for vCenter Server instances](vc_addingremovingservers.html)
* [Ordering and removing services for vCenter Server instances](vc_addingremovingservices.html)
