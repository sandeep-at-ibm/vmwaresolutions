---

copyright:

  years:  2020

lastupdated: "2020-07-23"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Use case 2
{: #fss-use-case-2}

The IBM Cloud for VMware Regulated Workloads delivers high security for sensitive workloads such as those run by users in the healthcare or financial sectors.

The architecture of the IBM Cloud for VMware Regulated Workloads is designed for isolation of sensitive workloads.

Compute and storage resources are offered in a dedicated workload region where the deployment of multiple clusters enables the capability to isolate workloads on a business unit or other designation, such as PCI workloads, further enhancing the security of the IBM Cloud for VMware Regulated Workloads.

Network isolation is maintained between the workload region and the management and edge region by using independent, isolated gateway appliances at the physical plant level. The workloads also benefit from the inclusion of an SDN overlay that is delivered with NSX-T. NSX-T uses micro-segmentation to enforce traffic isolation. Micro-segmentation policies applied to workload VMs are configured by the user to meet business requirements.

The use of shared resources, such as VSIs or shared storage options, prevents any data leakage out of the IBM Cloud for VMware Regulated Workloads. All resources necessary to support the workloads are delivered from within the IBM Cloud for VMware Regulated Workloads.

Data and VM encryption options are included in the IBM Cloud for VMware Regulated Workloads. The preferred option is keep your own key (KYOK) using IBM Hyper Protect Crypto Services (HPCS). Connecting HPCS to the IBM Cloud for VMware Regulated Workloads is either accomplished by using HyTrust Data Control with its embedded KMS or through the IBM Cloud KMIP adapter that is required to integrate with the vCenter directly.

Where HyTrust CloudControl is a required component of the IBM Cloud for VMware Regulated Workloads, Data Control is optional. If Data Control is selected, then IBM Cloud for VMware Regulated Workloads is able to take advantage of HyTrust Boundary Control. Boundary Control adds geo-fencing to the IBM Cloud for VMware Regulated Workloads security toolbox.

IBM Cloud for VMware Regulated Workloads is designed with high security throughout the platform making it an option for user workloads demanding the highest level of protection.

## Related links
{: #fss-use-case-2-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
