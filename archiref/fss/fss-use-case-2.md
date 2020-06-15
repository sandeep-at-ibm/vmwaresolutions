---

copyright:

  years:  2020

lastupdated: "2020-04-20"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FSS Cloud use case 2
{: #fss-use-case-2}

The FSS Cloud delivers high security for sensitive workloads such as those run by users in the healthcare or financial sectors.

The architecture of the FSS Cloud is designed for isolation of sensitive workloads.

Compute and storage resources are offered in a dedicated workload region where the deployment of multiple clusters enables the capability to isolate workloads on a business unit or other designation, such as PCI workloads, further enhancing the security of the FSS Cloud.

Network isolation is maintained between the workload region and the management and edge region by using independent, isolated gateway appliances at the physical plant level. The workloads also benefit from the inclusion of an SDN overlay that is delivered with NSX-T. NSX-T uses micro-segmentation to enforce traffic isolation. Micro-segmentation policies applied to workload VMs are configured by the user to meet business requirements.

The use of shared resources, such as VSIs or shared storage options, prevents any data leakage out of the FSS Cloud. All resources necessary to support the workloads are delivered from within the FSS Cloud.

Data and VM encryption options are included in the FSS Cloud. The options available include keep your own key (KYOK) and bring your own key (BYOK) capability by using IBM Hyper Protect Crypto Services (HPCS). Connecting HPCS to the FSS Cloud is either accomplished by using HyTrust Data Control with its embedded KMS or via the IBM Cloud KMIP adapter that is required to integrate with the vCenter directly.
Where HyTrust CloudControl is a required component of the FSS Cloud, Data Control is optional. If Data Control is selected, then FSS Cloud is able to take advantage of HyTrust Boundary Control. Boundary Control adds geo-fencing to the FSS Cloud security toolbox.

FSS Cloud is designed with high security throughout the platform making it an option for user workloads demanding the highest level of protection.

## Related links
{: #fss-use-case-2-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
