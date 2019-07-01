---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-28"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Getting started with IBM Cloud for VMware Solutions
{: #getting-started}

In this {{site.data.keyword.vmwaresolutions_full}} getting started tutorial, we take you through the process of ordering an instance and some add-on services for it.
{:shortdesc}

## Before you begin
{: #getting-started-prereqs}

Before you start to work with {{site.data.keyword.vmwaresolutions_short}}, review the following important information about browser requirements, users accounts, deployment options, and add-on services.

### Browser requirements
{: #getting-started-browser-req}

The following browsers are supported:
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

Microsoft Internet Explorer is not supported.
{:note}

For optimal viewing and working on the {{site.data.keyword.vmwaresolutions_short}} console, set the screen resolution to at least 1024 px width by 500 px height.

### User accounts
{: #getting-started-user-accts}

You need an {{site.data.keyword.cloud_notm}} account and an {{site.data.keyword.cloud_notm}} infrastructure account. These accounts must meet certain requirements.

| Account | Description |
|:------- |:---------- |
| IBMid | By using the **IBMid**, you can have a single login user name for all IBM products and services that you use, including {{site.data.keyword.cloud_notm}}. {{site.data.keyword.vmwaresolutions_short}} is provided as an infrastructure solution in the {{site.data.keyword.cloud_notm}} catalog. To access the {{site.data.keyword.vmwaresolutions_short}} console, you must have an **IBMid**.<br><br>To use your **IBMid** to log in to the {{site.data.keyword.vmwaresolutions_short}} console, you must associate the **IBMid** with an {{site.data.keyword.cloud_notm}} account. When you log in to the console for the first time, you are guided to either associate your existing **IBMid** with an {{site.data.keyword.cloud_notm}} account, or to sign up for a new {{site.data.keyword.cloud_notm}} account. The new {{site.data.keyword.cloud_notm}} account is automatically associated with your **IBMid**. You need to go through this process only once.<br><br>If you have problems when you associate your **IBMid** with an {{site.data.keyword.cloud_notm}} account, see [Troubleshooting for accessing {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-accessing#accessing). |
| IBM Cloud account | To order and use {{site.data.keyword.cloud_notm}} services, an {{site.data.keyword.cloud_notm}} account is required. Billing information is associated with the {{site.data.keyword.cloud_notm}} account. The cost of the physical and virtual infrastructure and the resulting licenses are charged to your {{site.data.keyword.cloud_notm}} account. |
| IBM Cloud infrastructure account | For information about the requirements for an {{site.data.keyword.cloud_notm}} infrastructure account, see [Requirements for the {{site.data.keyword.cloud_notm}} infrastructure account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).<br><br>You can link {{site.data.keyword.cloud_notm}} infrastructure accounts with {{site.data.keyword.cloud_notm}} accounts to use combined infrastructure as a service (IaaS) and platform as a service (PaaS) resources. Then, you can access IaaS resources and PaaS resources from a single login. Linking your accounts also provides you with a single invoice for all the PaaS and IaaS resources that you use:<br>If you do not have an {{site.data.keyword.cloud_notm}} infrastructure account, request one by following the procedure in [Signing up for an IBM Cloud infrastructure account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts#signing_required_accounts-infra), and then link your {{site.data.keyword.cloud_notm}} infrastructure account with your {{site.data.keyword.cloud_notm}} account by following the procedure in [Switching to IBMid and linking accounts](/docs/account?topic=account-unifyingaccounts#unifyingaccounts).<br>If you have an {{site.data.keyword.cloud_notm}} infrastructure account, you can link it with your {{site.data.keyword.cloud_notm}} account by following the procedure in [Switching to IBMid and linking accounts](/docs/account?topic=account-unifyingaccounts#unifyingaccounts).
{: caption="Table 1. Required user accounts" caption-side="top"}

### Deployment offerings
{: #getting-started-depl-offerings}

Review and choose your deployment offering.

| Deployment offering | Description |
|:------------------- |:----------- |
| [VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview) | With the vCenter Server offering, you can deploy a VMware virtual environment by using custom compute, storage, and network resources to best fit your business needs.
| [VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview) | The vCenter Server with Hybridity offering is a hosted private cloud that helps quickly and easily extend your on-premises infrastructure into the cloud. The VMware environment is based on IBM-provided VMware Software Defined Data Center licenses and it includes VMware Hybrid Cloud Extension (HCX). Using HCX, you can securely connect a vSphere 5.0+ environment on-premises with {{site.data.keyword.cloud_notm}} sites for seamless infrastructure hybridity and true application mobility.
| [VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview) | The vSphere on {{site.data.keyword.cloud_notm}} offering provides a customizable virtualization service that combines VMware-compatible {{site.data.keyword.baremetal_short}}, hardware components, and licenses, to build your own IBM-hosted VMware environment. |
| [NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview) | The NetApp ONTAP Select offering allows you to deploy a software-defined storage cluster that addresses your needs for a dedicated and highly available storage appliance based on NetApp ONTAP Select. |
{: caption="Table 2. Deployment offerings" caption-side="top"}

### Add-on services
{: #getting-started-add-on-services}

Review and choose add-on services for your deployment offering.

| Service name | Description |
|:------------ |:----------- |
| [F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | The F5 on {{site.data.keyword.cloud_notm}} service (F5 BIG-IP® Virtual Edition) provides intelligent L4-L7 load balancing and traffic management services at a local and global scale, robust network and web application firewall protection, and secure and federated application access. |
| [FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations) | The FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service deploys a pair of FortiGate Security Appliance (FSA) 300 series devices in a highly available mode to provide firewall, routing, NAT, and VPN services to protect all the servers and virtual machines on the public VLAN of your instances. |
| [FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | The FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service deploys a pair of FortiGate Virtual Appliances to your environment, which can help you reduce risk by implementing critical security controls within your virtual infrastructure. |
| [HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations) | The HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service enforces and controls compliance against security standards, and provides detailed role-based access control (RBAC), approval, and auditing capabilities. When combined with HyTrust DataControl, the service can ensure that virtual machines and workload data do not leave a particular region, cluster, or ESXi server within the {{site.data.keyword.CloudDataCent_notm}}. |
| [HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations) | The HyTrust DataControl on {{site.data.keyword.cloud_notm}} service offers strong encryption with integrated key management to secure workloads throughout their lifecycle. The service can provide encryption at both the operating system level and at the data level, which means that any directory, folder, or file within a workload can be encrypted and decrypted.|
| [HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | The HyTrust KeyControl on {{site.data.keyword.cloud_notm}} service simplifies the management of encrypted workloads by automating and simplifying the lifecycle of encryption keys. The service can easily manage encryption keys at scale by using FIPS 140-2 compliant encryption. |
| [IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | The {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} service brings the power of microservices and containers to your VMware environment on {{site.data.keyword.cloud_notm}}. With this service, you can extend the same familiar VMware and {{site.data.keyword.cloud_notm}} Private operational model and tools from on-premises into the {{site.data.keyword.cloud_notm}}. |
| [IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations) | The IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement the service as a stand-alone solution or you can integrate it with your IBM Spectrum Protect environment to offload copies for long-term storage and data governance. |
| [KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | The KMIP for VMware on {{site.data.keyword.cloud_notm}} service provides a highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and destroy the encryption keys. It also provides management capability to maintain the associations between the client credentials and the encryption keys. |
| [Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | The Veeam on {{site.data.keyword.cloud_notm}} service seamlessly integrates directly with your VMware hypervisors to help your enterprise achieve high availability. This service can provide recovery points and time objectives for your applications and data. The recovery points and time objectives can be provided in less than 15 minutes after configuration is completed. By using this service, you can directly control both the backup and restore of all virtual machines for your infrastructure from the Veeam console. |
| [VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations) | The HCX on {{site.data.keyword.cloud_notm}} service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.|
| [Zerto on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | The Zerto on {{site.data.keyword.cloud_notm}} service provides replication and disaster recovery capabilities, which can be integrated into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud_notm}}. |
{: caption="Table 3. Available add-on services for deployment offerings" caption-side="top"}

## Step 1: Accessing the IBM Cloud for VMware Solutions console
{: #getting-started-step1}

The {{site.data.keyword.vmwaresolutions_short}} console is the interface where you order and manage your deployments. Each deployment is managed as an instance in the console. The console is a stand-alone user interface that is separate from the {{site.data.keyword.cloud_notm}} infrastructure customer portal.

To access the {{site.data.keyword.vmwaresolutions_short}} console:
1. Go to https://cloud.ibm.com/infrastructure/vmware-solutions/console.
2. Log in to the console with your **IBMid**.

## Step 2: Configuring your user account and settings
{: #getting-started-step2}

Before you order an instance, you must enter the user name and API key of your {{site.data.keyword.cloud_notm}} infrastructure account on the **Settings** page of the console.

For information about how to configure your user account and settings, see [Managing user accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Step 3: Ordering an instance
{: #getting-started-step3}

After you decide upon a deployment offering, which is managed as an instance in the console, begin the ordering process.

For information about how to order an instance, see the following topics based on your selection of deployment offering:
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Ordering vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ordering NetApp ONTAP Select instances](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Step 4: Viewing the instance
{: #getting-started-step4}

After you place an instance order in **Step 3**, the deployment of the instance starts automatically. You can track the status of the deployment by viewing the instance details. When the instance deployment is completed, you can view the summary and detailed information of the instance and its add-on services on the instance details page too.

For information about how to view the instance you ordered, see the following topics:
* [Viewing vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Viewing vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Viewing NetApp ONTAP Select instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-np_viewinginstances#np_viewinginstances)
