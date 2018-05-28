---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# About IBM Cloud for VMware Solutions

{{site.data.keyword.vmwaresolutions_full}} enables you to quickly and seamlessly integrate or migrate your on-premises VMware workloads to the {{site.data.keyword.cloud_notm}} by using the scalable, secure, and high-performance {{site.data.keyword.cloud_notm}} infrastructure and the industry-leading VMware hybrid virtualization technology.

{{site.data.keyword.vmwaresolutions_short}} allows you to easily deploy your VMware virtual environments and manage the infrastructure resources on {{site.data.keyword.cloud_notm}}. At the same time, you can still use your familiar native VMware product console to manage the VMware workloads.

## IBM Cloud for VMware Solutions benefits

{{site.data.keyword.vmwaresolutions_short}} provides the following major benefits:
* **Global reach**: Allows you to expand your hybrid cloud footprint to up to 30 enterprise-class {{site.data.keyword.CloudDataCents_notm}} around the world.
* **Seamless integration**: Enables seamless integration across the hybrid cloud with the {{site.data.keyword.cloud_notm}} infrastructure.
* **Rapid provisioning**: Automates the deployment and configuration of the VMware environment, which allows you to quickly deploy an enterprise-class VMware environment with on-demand {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}} and virtual servers.
* **Simplification**: Enables you to consume a VMware cloud platform without the need to identify, procure, deploy, and manage the underlying physical infrastructure (compute, storage, and network), and the software licenses.
* **Expansion and contraction flexibility**: Allows you to easily expand and contract your VMware workloads according to your business needs.
* **Single management console**: Provides a single console to deploy, access, and manage the VMware environments on {{site.data.keyword.cloud_notm}}.

## Deployment offerings

{{site.data.keyword.vmwaresolutions_short}} provides standardized and customizable deployment choices of VMware virtual environments. The following deployment types are offered:
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**: The vCenter Server offering allows you to deploy a VMware virtual environment by using custom compute, storage, and network resources to best fit your business needs.
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle**: The vCenter Server with Hybridity offering is a hosted private cloud that helps quickly and easily extend your on-premises infrastructure into the cloud. The VMware environment is based on IBM-provided VMware Software Defined Data Center licenses and it includes VMware Hybrid Cloud Extension (HCX). Using HCX, you can securely connect a vSphere 5.0+ environment on-premises with IBM Cloud sites for seamless infrastructure hybridity and true application mobility.
* **VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}**: The Cloud Foundation offering provides a unified VMware virtual environment by using standard {{site.data.keyword.cloud_notm}} compute, storage, and network resources that are dedicated to each user deployment.
* **VMware vSphere on {{site.data.keyword.cloud_notm}}**: The vSphere on {{site.data.keyword.cloud_notm}} offering provides a customizable virtualization service that combines VMware-compatible {{site.data.keyword.baremetal_short}}, hardware components, and licenses, to build your own IBM-hosted VMware environment.
* **NetApp ONTAP Select**: The NetApp ONTAP Select offering allows you to deploy a software-defined storage cluster that addresses your needs for a dedicated and highly available storage appliance based on NetApp ONTAP Select.
* **VMware Federal on {{site.data.keyword.cloud_notm}}**: The VMware Federal on {{site.data.keyword.cloud_notm}} offering provides support for ordering a base vCenter Server instance in the WDC03 Federal on IBM Cloud Data Center in addition to providing the option to secure the deployed instances, removing sensitive information and the open management connection for ongoing access to the instance for management functions.

## Additional services

{{site.data.keyword.vmwaresolutions_short}} allows you to add various services at instance order time or after instance deployment. The following services are offered:

### FortiGate Security Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Security Appliance (FSA) 300 series devices that can provide firewall, routing, NAT, and VPN services to protect the public network connection to your environment.

This service is available only to instances that are deployed in V1.8 or later releases.

For more information, see [Managing FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Virtual Appliances that can allow you to reduce risk by implementing critical security controls within your virtual infrastructure.

This service is available only to instances that are deployed in V2.0 or later releases.

For more information, see [Managing FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html).

### F5 on IBM Cloud

This service optimizes performance and ensures availability and security for applications with the F5 BIG-IP Virtual Edition (VE).

This service is available only to instances that are deployed in V1.9 or later releases.

For more information, see [Managing F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html).

### IBM Spectrum Protect Plus on IBM Cloud

This service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement it as a stand-alone solution or you can integrate it with your IBM Spectrum Protect&trade; Plus environment to offload copies for long-term storage and data governance.

**Notes**:
* This service is available only to instances that are deployed in (or upgraded to) V2.2 or later releases.
* For instances that are deployed in V2.3 or later releases, IBM Spectrum Protect Plus on IBM Cloud is the default backup service. The service provides backup for management VMs automatically.
* For instances that are deployed in V2.2, this service provides data protection for the workload VMs only.

For more information, see [Managing IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html).

### Veeam on IBM Cloud

This service integrates seamlessly with your VMware environment to help you manage the backup and restore of all virtual machines (VMs) in your environment, including the backup and restore of the management components. It can provide a recovery point objective (RPO) of less than 15 minutes upon configuration for your data.

This service is configured to back up the management VMs immediately after the deployment of your instance.

This service is available only to instances that are deployed in V1.8 or later releases.

For more information, see [Managing Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html).

### Zerto on IBM Cloud

This service provides replication and disaster recovery capabilities to help protect your workloads. For more information, see [Managing Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html).

### Managed Services from IMI

These services enable IBM Integrated Managed Infrastructure (IMI) to deliver dynamic remote management services for a broad range of cloud infrastructures.

These services are available for Cloud Foundation instances only.

For more information, see [Requesting managed services from IMI](../services/managing_imi.html).

## Related links

* [Getting started](../index.html)
* [Cloud Foundation overview](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html)
* [vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [NetApp ONTAP Select](../netapp/np_netappoverview.html)
