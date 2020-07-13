---

copyright:

  years: 2016, 2020

lastupdated: "2020-07-10"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmwaresolutions

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
  *  Mozilla® Firefox®
  *  Google Chrome™
  *  Apple® Safari®

Microsoft® Internet Explorer® is not supported.
{:note}

For optimal viewing and working on the {{site.data.keyword.vmwaresolutions_short}} console, set the screen resolution to at least 1024 px width by 500 px height.

### User accounts
{: #getting-started-user-accts}

You need an {{site.data.keyword.cloud_notm}} account and an {{site.data.keyword.cloud_notm}} infrastructure account. These accounts must meet certain requirements.

| Account | Description |
|:------- |:---------- |
| IBMid | By using the **IBMid**, you can have a single login user name for all IBM products and services that you use, including {{site.data.keyword.cloud_notm}}. {{site.data.keyword.vmwaresolutions_short}} is provided as an infrastructure solution in the {{site.data.keyword.cloud_notm}} catalog. To access the {{site.data.keyword.vmwaresolutions_short}} console, you must have an **IBMid**.<br><br>To use your **IBMid** to log in to the {{site.data.keyword.vmwaresolutions_short}} console, you must associate the **IBMid** with an {{site.data.keyword.cloud_notm}} account. When you log in to the console for the first time, you are guided to either associate your existing **IBMid** with an {{site.data.keyword.cloud_notm}} account, or to sign up for a new {{site.data.keyword.cloud_notm}} account. The new {{site.data.keyword.cloud_notm}} account is automatically associated with your **IBMid**. You need to go through this process only once.<br><br>If you have problems when you associate your **IBMid** with an {{site.data.keyword.cloud_notm}} account, see [Why is my password incorrect?](/docs/account?topic=account-ts_logintoibm). |
| {{site.data.keyword.cloud_notm}} account | To order and use {{site.data.keyword.cloud_notm}} services, an {{site.data.keyword.cloud_notm}} account is required. Billing information is associated with the {{site.data.keyword.cloud_notm}} account. The price of the physical and virtual infrastructure and the resulting licenses are charged to your {{site.data.keyword.cloud_notm}} account. |
| {{site.data.keyword.cloud_notm}} infrastructure account | For information about the requirements for an {{site.data.keyword.cloud_notm}} infrastructure account, see [Requirements for the {{site.data.keyword.cloud_notm}} infrastructure account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).<br><br>You can link {{site.data.keyword.cloud_notm}} infrastructure accounts with {{site.data.keyword.cloud_notm}} accounts to use combined infrastructure as a service (IaaS) and platform as a service (PaaS) resources. Then, you can access IaaS resources and PaaS resources from a single login. Linking your accounts also provides you with a single invoice for all the PaaS and IaaS resources that you use:<br><br>If you do not have an {{site.data.keyword.cloud_notm}} infrastructure account, request one by following the procedure in [Signing up for an {{site.data.keyword.cloud_notm}} infrastructure account](/docs/vmwaresolutions?topic=vmwaresolutions-signing_required_accounts#signing_required_accounts-infra), and then link your {{site.data.keyword.cloud_notm}} infrastructure account with your {{site.data.keyword.cloud_notm}} account by following the procedure in [Upgrading your account](/docs/account?topic=account-upgrading-account).<br><br>If you have an {{site.data.keyword.cloud_notm}} infrastructure account, you can link it with your {{site.data.keyword.cloud_notm}} account by following the procedure in [Upgrading your account](/docs/account?topic=account-upgrading-account).
{: caption="Table 1. Required user accounts" caption-side="top"}

### Deployment offerings
{: #getting-started-depl-offerings}

Review and choose your deployment offering.

| Deployment offering | Description |
|:------------------- |:----------- |
| [VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview) | This offering provides standardized and customizable deployment choices of VMware® virtual data center environments. |
| [VMware Solutions Dedicated - vCenter Server](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview) | This offering allows you to deploy a VMware virtual environment by using custom compute, storage, and network resources to best fit your business needs. |
| [VMware Solutions Dedicated - {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-fss-cloud-vmware-config) | This offering is an extension of the VMware vCenter Server® offering, which enhances the basic vCenter Server architecture to deliver a secure, high-performance platform. |
| [VMware Solutions Dedicated - VMware vSphere®](/docs/vmwaresolutions?topic=vmwaresolutions-vs_vsphereclusteroverview) | This offering provides a customizable virtualization service that combines VMware-compatible bare metal servers, hardware components, and licenses, to build your own IBM-hosted VMware environment. |
| [Single-node for Migration and App Modernization](/docs/vmwaresolutions?topic=vmwaresolutions-cloud_modern_bundle_overview) | This offering allows you to test drive {{site.data.keyword.cloud_notm}} to migrate VMware workloads to the {{site.data.keyword.cloud_notm}} and then modernize simple workloads using containers. |
| [Single-node for Data Protection and Disaster Recovery](/docs/vmwaresolutions?topic=vmwaresolutions-dr_backup_bundle_overview) | This offering allows you to test drive {{site.data.keyword.cloud_notm}} to migrate and recover VMware workloads to the {{site.data.keyword.cloud_notm}}. |
{: caption="Table 2. Deployment offerings" caption-side="top"}

### Add-on services
{: #getting-started-add-on-services}

Review and choose add-on services for your deployment offering.

| Service category | Service name | Description |
|:------------ |:------------ |:----------- |
| Security and compliance | [Caveonix RiskForesight™](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) | This service manages cyber and compliance risk with proactive monitoring and automated defense controls to protect against threats and to meet industry or government regulations. |
| Security and compliance | FortiGate® Security Appliance | This service deploys either the [Fortigate Security Appliance 1 Gbps](/docs/fortigate-1g) or [Fortigate Security Appliance 10 Gbps](/docs/fortigate-10g) service. |
| Security and compliance | [FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations) | This service deploys a pair of FortiGate Virtual Appliances to your environment, which can help you reduce risk by implementing critical security controls within your virtual infrastructure. |
| Security and compliance | [F5 BIG-IP®](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations) | This service provides intelligent L4-L7 load balancing and traffic management services at a local and global scale, robust network and web application firewall protection, and secure and federated application access. |
| Business continuity and migration | [HCX™](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations#hcx_considerations) | This service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change. |
| Security and compliance | [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations) | This service enforces and controls compliance against security standards, and provides detailed role-based access control (RBAC), approval, and auditing capabilities. When combined with HyTrust DataControl, the service can ensure that virtual machines and workload data do not leave a particular region, cluster, or ESXi server within the {{site.data.keyword.cloud_notm}} data center. |
| Security and compliance | [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations) | This service offers strong encryption with integrated key management to secure workloads throughout their lifecycle. The service can provide encryption at both the operating system level and at the data level, which means that any directory, folder, or file within a workload can be encrypted and decrypted. |
| Security and compliance | [HyTrust KeyControl](/docs/vmwaresolutions?topic=vmwaresolutions-htkc_considerations) | This service simplifies the management of encrypted workloads by automating and simplifying the lifecycle of encryption keys. The service can easily manage encryption keys at scale by using FIPS 140-2 compliant encryption. |
| Professional services | [{{site.data.keyword.cloud_notm}} Expert Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_ices) | This service can help you modernize and deploy your business in a flexible and secure platform by adopting VMware on {{site.data.keyword.cloud_notm}}. By engaging Expert Services, you can accelerate your time to value. |
| Business continuity and migration | [{{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_overview) | This service delivers a multi-zone cloud architecture to help enterprises prevent downtime for cloud applications and to automate failovers within a cloud region. |
| Featured workload solutions | [IBM Security Services for SAP®](/docs/vmwaresolutions?topic=vmwaresolutions-managing-ss-sap) | This service offers a cybersecurity solution to automate the monitoring and protection of SAP applications on {{site.data.keyword.cloud_notm}}, and to keep workloads compliant and secure from inside and outside threats. |
| Business continuity and migration | [IBM Spectrum® Protect Plus](/docs/vmwaresolutions?topic=vmwaresolutions-spp_considerations) | This service provides an efficient and scalable solution for data protection, data reuse, and data recovery for virtual environments. You can implement the service as a stand-alone solution or you can integrate it with your IBM Spectrum Protect environment to offload copies for long-term storage and data governance. |
| Security and compliance | [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-vsrx_overview) | This service provides security and networking services at the perimeter or edge in virtualized private or public cloud environments. Within a VMware infrastructure, vSRX runs as a virtual machine (VM) within the VMware vSphere environment. The vSRX provides a complete Next-Generation Firewall (NGFW) solution. |
| Security and compliance | [KMIP™ for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) | This  service provides a highly available service to manage encryption keys that are used by VMware in the {{site.data.keyword.cloud_notm}}. This service offers runtime capability to allow customers to create, retrieve, activate, revoke, and destroy the encryption keys. It also provides management capability to maintain the associations between the client credentials and the encryption keys. |
| Professional services | [Managed Services for VMware Workload Transformation](/docs/vmwaresolutions?topic=vmwaresolutions-managing_mcms) | This service takes away the responsibility of the day to day management of the virtual infrastructure so that you are free to focus on critical items. |
| Professional services | [Managed VMware Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_imi) | This service can simplify VMware virtual infrastructure management with modular services. It uses advanced automation and analytics to manage critical infrastructure components worldwide and to deliver dynamic remote management services for a broad range of traditional and cloud virtual infrastructures. |
| Professional services | [Managed Disaster Recovery Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_zerto_services) | This service provides replication and disaster recovery capabilities. These capabilities can be integrated into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud_notm}}. |
| Professional services | [NetApp® ONTAP® Select](/docs/vmwaresolutions?topic=vmwaresolutions-netapp) | This service extends existing data management capabilities by implementing NetApp ONTAP software as a service on the dedicated {{site.data.keyword.cloud_notm}} bare metal servers. |
| Business continuity and migration | [PrimaryIO HDM](/docs/vmwaresolutions?topic=vmwaresolutions-managing_pio) | This service decouples virtual machines (VMs) and storage (VMDKs) to seamlessly move workloads to and from {{site.data.keyword.cloud_notm}} faster and efficiently. |
| Transformation and modernization of VMware applications | [Red Hat® OpenShift® for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview) | This service brings together the power of the Red Hat OpenShift Container Platform and the VMware software-defined data center stack. |
| Business continuity and migration | [Veeam®](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview) | This service seamlessly integrates directly with your VMware hypervisors to help your enterprise achieve high availability. This service can provide recovery points and time objectives for your applications and data. The recovery points and time objectives can be provided in less than 15 minutes after configuration is completed. By using this service, you can directly control both the backup and restore of all virtual machines for your infrastructure from the Veeam console. |
| Featured workload solutions | [VMware Horizon® 7](/docs/vmwaresolutions?topic=vmwaresolutions-horizon-arch-ovw) | This service delivers a seamlessly integrated hybrid cloud for virtual desktops and applications. |
| Management tools | [vRealize® Operations™ and Log Insight™](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview) | This service deploys the VMware vRealize Operations (vROps) and VMware vRealize Log Insight (vRLI) tools, which help you operate and monitor the performance, health, and capacity of your IBM-hosted, dedicated VMware environment. |
| Business continuity and migration | [Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-addingzertodr) | This service provides replication and disaster recovery capabilities, which can be integrated into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud_notm}}. |
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

For information about how to configure your user account and settings, see [Managing user accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount).

## Step 3: Ordering an instance
{: #getting-started-step3}

After you decide upon a deployment offering, which is managed as an instance in the console, begin the ordering process.

For information about how to order an instance, see the following topics based on your selection of deployment offering:
* [Ordering virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
* [Ordering vSphere clusters](/docs/vmwaresolutions?topic=vmwaresolutions-vs_orderinginstances)
* [Ordering Single-node for Migration and App Modernization instances](/docs/vmwaresolutions?topic=vmwaresolutions-cloud_modern_bundle_orderinginstance)
* [Ordering Single-node for Data Protection and Disaster Recovery instances](/docs/vmwaresolutions?topic=vmwaresolutions-dr_backup_bundle_orderinginstance)

## Step 4: Viewing the instance
{: #getting-started-step4}

After you place an instance order in **Step 3**, the deployment of the instance starts automatically. You can track the status of the deployment by viewing the instance details. When the instance deployment is completed, you can view the summary and detailed information of the instance and its add-on services on the instance details page too.

For information about how to view the instance you ordered, see [Viewing vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances).
