---

copyright:

  years:  2019, 2020

lastupdated: "2020-04-16"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuring IBM Cloud for Horizon 7 deployment
{: #horizon-deploy-config}

The recommendation for a production environment is to use a minimum of four hosts for the desktop cluster with VSAN and three hosts for the management cluster.

To deploy VMware Horizon 7:

1. Create a vCenter Server instance with three hosts and two NFS datastores for the Horizon Management Components. See [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance).
2. Configure supporting infrastructure for VMware Horizon in {{site.data.keyword.cloud_notm}}. This includes an Active Directory Domain and Microsoft SQL Server.
3. Deploy Horizon 7.8 or later in the management cluster. See the [VMware Horizon 7 documentation](https://docs.vmware.com/en/VMware-Horizon-7/index.html){:external}.
4. Deploy App Volumes 2.17 or later in the management cluster. See the [VMware App Volumes documentation](https://docs.vmware.com/en/VMware-App-Volumes/index.html){:external}.
5. Deploy VDI workload cluster with the required number of hosts to support the desktop workloads and with VMware VSAN for storage.
6. Create Desktop Template and deploy desktops.

## Horizon 7 Environment
{: #horizon-deploy-config-envir}

When you set up the Horizon 7 environment, you must install and configure the following components:
* Configure Active Directory services, DNS, and DHCP. If necessary, install and configure KMS servers.
* Install SQL Server for App Volumes Manager and the Horizon Events database
* Optionally, install RDS license servers.
* Install Horizon Connection Server and replica server version 7.8 or later.
* Install App Volumes Managers version 2.17 or later.
* Configure SSL Certificates for all components
* Configure Load Balancing for Connection Servers and App Volumes Managers

Deploy a Unified Access Gateway appliance and connect it to the Connection Server if your deployment supports remote users.
* Use Unified Access Gateway version 3.5 or newer.
* Deploy only a single NIC with the OVF Deploy wizard. For multiple NICs, use the PowerShell script to include the password and encode special characters in the .INI configuration file. For more information, see the Unified Access Gateway documentation.
* Specify netmask0-2 for the NICs.
* Deploy a load balancer if you are using two or more Connection Servers.
* Optionally, install a Horizon event database on Microsoft SQL Server 2016.
* Install Horizon Agent on the master images for RDS hosts and VDI Virtual Desktop VMs. This agent communicates with the Connection Servers.

## Deploy Horizon 7 over Hybrid Cloud
{: #horizon-deploy-config-hybrid-cloud}

You might already have Horizon 7 environments on-premises. The Horizon 7 pod on-premises and your Horizon 7 pod on {{site.data.keyword.cloud_notm}} can be managed separately. Alternatively, you can extend your on-premises Horizon 7 environment to the cloud by linking it with your Horizon 7 on {{site.data.keyword.cloud_notm}} environment by using Cloud Pod Architecture (CPA). Deploying your Horizon 7 over hybrid cloud enables you to manage your on-premises deployment and your cloud deployment in a single federated space.

For hybrid cloud deployment, follow these steps:
1. Configure network connectivity and firewall rules to enable the Connection Server instance on {{site.data.keyword.cloud_notm}} to communicate with the Connection Server instance on-premises.
2. Prepare Microsoft Active Directory (AD) and choose to set up a one-way trust or a two-way trust.
3. Ensure that your on-premises Horizon 7 version is 7.0 or later.

   **Note**: The Horizon 7 version that is deployed on-premises does not have to match the Horizon 7 version deployed on {{site.data.keyword.cloud_notm}}. However, you cannot mix a Horizon 6 pod (or lower) with a Horizon 7 pod within the same CPA.

4. Use Cloud Pod Architecture to connect the Horizon 7 pod on-premises with the Horizon 7 pod on {{site.data.keyword.cloud_notm}}.
5. For easy sharing of images and ISO images, you can use the vCenter Content Library on each vCenter Server.

## Connection and firewall configuration for deploying Horizon 7
{: #horizon-deploy-config-connect-firewall}

To set up a successful hybrid cloud deployment, you must configure connectivity between your on-premises and {{site.data.keyword.cloud_notm}} environments and allow traffic between these environments and the internet.

### Connectivity
{: #horizon-deploy-config-connectivity}

{{site.data.keyword.cloud_notm}} supports multiple options for connectivity between the on-premises environment and the hosted environment. These options include Direct-Link Cloud Connect, Direct-Link Cloud Exchange, and VPN.

If the Direct-Link options are not being utilized, a VPN connection will need to be configured. A pair of NSX Edges should be provisioned to provide IPSEC or BGP VPN connectivity on-premises, and firewall rules should be configured to allow traffic between the {{site.data.keyword.cloud_notm}} SDDC and the on-premises networks. The on-premises VPN connection can be configured by providing the settings configured in NSX to the networking team.

When building out connectivity between the {{site.data.keyword.cloud_notm}} environment and the on-premises environment, it is important to ensure that there is connectivity between components in the logical network:
* From the management component to the on-premises component
* From the compute component to the on-premises component
* From the compute component to the management component

### Firewall rules
{: #horizon-deploy-config-firewall}

VMware Horizon 7 has a number of different server components and desktop agents that interact. This includes management servers and desktop agents that allow for a desktop or application remote session and interactions between the Horizon Server components and the {{site.data.keyword.cloud_notm}} SDDC management components.

Properly scoped and configured firewall rules will ensure a successful deployment. This includes the NSX Distributed Firewall and any firewalls between the {{site.data.keyword.cloud_notm}} and On-Premises environment.

For a full list of ports utilized by Horizon 7, see the [Network Ports in VMware Horizon 7](https://techzone.vmware.com/resource/network-ports-vmware-horizon-7){:external}.

## Preparing Active Directory for Hybrid Cloud Deployment
{: #horizon-deploy-config-prep-ad}

If you are deploying Horizon 7 in a hybrid cloud environment by linking the on-premises pod with the {{site.data.keyword.cloud_notm}} pod, you must prepare the on-premises Microsoft Active Directory (AD) to access the AD on {{site.data.keyword.cloud_notm}}.

## Link Horizon 7 Pods on IBM Cloud
{: #horizon-deploy-config-link-pods}

You can use the Cloud Pod Architecture feature to connect Horizon 7 pods regardless of whether the pods are on-premises or on {{site.data.keyword.cloud_notm}}. When you deploy two or more Horizon 7 pods on {{site.data.keyword.cloud_notm}}, you can manage them independently or manage them together by linking them with Cloud Pod Architecture.

* On one Connection Server, initialize Cloud Pod Architecture and join the Connection Server to a pod federation.
* After initialization, you can create a global entitlement across your Horizon 7 pods on-premises and on {{site.data.keyword.cloud_notm}}.
* Optionally, when you use Cloud Pod Architecture, you can deploy a global load balancer (such as F5, {{site.data.keyword.cloud_notm}} Global Load-Balancing Service, or others) between the pods. The global load balancer provides a single-namespace capability that allows the use of a common global namespace when referring to Horizon CPA. Using CPA with a global load balancer provides your users with a single connection method and desktop icon in their Horizon Client or workspace ONE console.
Without the global load balancer and the ability to have a single namespace for multiple environments, users will be presented with a possibly confusing array of desktop icons (corresponding to the number of pods on which desktops have been provisioned for them). For more information on how to set up Cloud Pod Architecture, see [Administering Cloud Pod Architecture in Horizon 7](https://docs.vmware.com/en/VMware-Horizon-7/7.6/horizon-cloud-pod-architecture/GUID-07C1B313-5907-4EDB-AB2F-75F7F58BD1AF.html){:external}.

Use Cloud Pod Architecture to link any number of Horizon 7 pods on {{site.data.keyword.cloud_notm}}. The maximum number of pods must conform to the limits set for pods in Cloud Pod Architecture. See [VMware Horizon 7 Sizing Limits and Recommendations (2150348)](https://kb.vmware.com/s/article/2150348){:external}.

When you connect multiple Horizon 7 pods together with Cloud Pod Architecture, the Horizon 7 versions for each of the pods can be different from one another. The only limitation is that they all be Horizon 7 v7.0 or higher (that is, no mixing of Horizon 6 pods).

## Shared Content Library
{: #horizon-deploy-config-shared-library}

Content Libraries are container objects for VM, vApp, and OVF templates and other types of files, such as templates, ISO images, and text files. vSphere administrators can use the templates in the library to deploy virtual machines and vApps in the vSphere inventory. Sharing golden images across multiple vCenter Server instances, between multiple {{site.data.keyword.cloud_notm}} and/or on-premises SDDCs guarantees consistency, compliance, efficiency, and automation in deploying workloads at scale.

For more information, see [Using Content Libraries](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-254B2CE8-20A8-43F0-90E8-3F6776C2C896.html){:external} in the vSphere Virtual Machine Administration guide in the [VMware vSphere documentation](https://docs.vmware.com/en/VMware-vSphere/index.html){:external}.

## Licensing
{: #horizon-deploy-config-licensing}

Enabling Horizon 7 to run on {{site.data.keyword.cloud_notm}} requires two separate items.  The first is the monthly infrastructure expense that is purchased through {{site.data.keyword.cloud_notm}}.  The second is the Horizon Universal License that entitles customers to VMware Horizon 7.

For POC or pilot deployment of Horizon 7, you may use a temporary evaluation license or your existing perpetual license. However, to enable Horizon 7 for production deployment on {{site.data.keyword.cloud_notm}}, you must purchase the new Horizon Universal License. To obtain the new Horizon Universal License or for more information on how to upgrade your existing perpetual license to subscription license and associated discounts, contact your VMware representative.

### Different types of Horizon universal licenses
{: #horizon-deploy-config-license-types}

The Horizon Universal license replaces the Horizon subscription licensing that was previously offered.  These licenses provide access to VMware Horizon 7 and VMware Horizon Cloud.  This includes access to the Horizon Cloud Control Panel and Cloud Monitoring Service for Horizon 7 environments.

Licenses are available for both Named and Concurrent Users.
* Horizon Universal License – provides customers with a single license that can be utilized for VDI and RDSH Published apps with Horizon 7 and the Horizon Cloud Service.
* Horizon Apps Universal License - provides customers with a single license that can be utilized for RDSH Published apps with Horizon 7 and the Horizon Cloud Service.

You can use different licenses (including perpetual licenses) on different Horizon pods whether the pods are connected by CPA or not. You cannot mix different licenses within a pod since each pod only takes 1 type of license. For example, you cannot use both perpetual license and subscription license for a single pod. You also cannot use both the Horizon Apps Universal license and the Horizon Universal license for a single pod.  Suppose you have two pods deployed, pod A on-premises and pod B on {{site.data.keyword.cloud_notm}} and the two pods are connected by CPA, you can use a different license type on each pod. For example, you can use the Horizon Enterprise perpetual license for pod A, and the new Horizon Universal license for pod B.

The best subscription license you need for your Horizon 7 deployment will depend on your use case.

Here are some examples:
* You are setting up a new H7 deployment for 2,000 VDI users on {{site.data.keyword.cloud_notm}}. There are no on-premises components. Purchase 2,000-user Horizon Universal license in this case.
* You have an existing Horizon 7 pod on-premises for 2,000 users, and you want to deploy a pod on {{site.data.keyword.cloud_notm}} for an addition 1,000 users for full time VDI use.  The best license type is the Horizon Universal license for your Horizon 7 pod on {{site.data.keyword.cloud_notm}}. You would keep your perpetual license for the on-premises pod until renewal and then decided whether to move to Horizon Universal license for your on-premises pod.
* You have an existing Horizon 7 pod on-premises for 2,000 users, and you want to deploy a pod on {{site.data.keyword.cloud_notm}} as BCDR capacity for the 2,000 users on premises. The best license type is to upgrade your existing 2,000-user perpetual license to 2,000-user Horizon Universal license.

### License enablement
{: #horizon-deploy-config-lic-enable}

Regardless of whether you are deploying Horizon 7 on-premises or on {{site.data.keyword.cloud_notm}}, if you are using any of the subscription licenses, you must install the Horizon Cloud Connector to enable subscription license management for Horizon 7.  The Horizon 7 Cloud Connector is a virtual appliance that connects a Horizon 7 pod with Horizon Cloud Service features.

A [MyVMware account](https://my.vmware.com/web/vmware/home) is required for Horizon 7 subscription license. Once you purchase the subscription license, a record will be created in the Horizon Cloud Service using your MyVMware email address, and your subscription license information will be visible to the Horizon Administrator console.

As part of the subscription license process, you receive an email with the link to download the Horizon 7 Cloud Connector as an OVA file. Follow the instructions to deploy the Cloud Connector from the VMware vSphere Web Client, alongside your new or existing Horizon 7 pods.

After the Cloud Connector is deployed, it is paired with the Connection Server in the Horizon 7 pod by using the Horizon Cloud Service. This service manages the Horizon 7 subscription license between connected Horizon 7 pods. Unlike the Horizon 7 perpetual license, with a subscription license, you do not need to retrieve or manually enter a license key for Horizon 7 product activation.

Currently, Horizon Cloud Service is only used to enforce subscription licenses for Horizon 7. License keys for supporting components, such as license keys for vSphere, App Volumes and others, will be delivered separately and are not managed by the Cloud Connector.  Those licenses will either be managed by {{site.data.keyword.cloud_notm}} or must be entered into the components manually. Over time, additional features beyond license management will be available on Horizon Cloud Service for Horizon 7 deployments.

Review the [VMware Horizon 7 Cloud Connector](https://docs.vmware.com/en/VMware-Horizon-7/7.8/horizon-installation/GUID-4B40CE42-70A8-43B0-A99B-D53A12FC698C.html){:external} for more details on how to deploy the Horizon 7 Cloud Connector Virtual Appliance. You will need a separate Cloud Connector for each pod.

## Deploying desktops on IBM Cloud with instant clone, App Volumes, and User Environment Manager
{: #horizon-deploy-config-deploy-desktop}

### Instant Clones
{: #horizon-deploy-config-instant-clone}

In addition to using Full Clones, you can also leverage Instant Clone Technology coupled with App Volumes to accelerate the delivery of user-customized and fully personalized desktops. These technologies dramatically reduce infrastructure requirements while enhancing security by delivering a brand-new personalized desktop and application services to end users every time they log in:
* Reap the economic benefits of stateless, non persistent virtual desktops served up to date upon each login.
* Deliver a pristine, high-performance personalized desktop every time a user logs in.
* Improve security by destroying desktops every time a user logs out.

### App Volumes
{: #horizon-deploy-config-app-volume}

App Volumes provides real-time application delivery and management, now for on premises and on VMC:
* Quickly provision applications at scale.
* Dynamically attach applications to users, groups, or devices, even when users are already logged in to their desktop.
* Provision, deliver, update, and retire applications in real time.
* Provide a user-writable volume, allowing users to install applications that follow them across desktops.
* Provide end users with quick access to a Windows workspace and applications, with a personalized and consistent experience across devices and locations.
* Simplify end-user profile management by providing organizations with a single and scalable solution that leverages the existing infrastructure.
* Speed up the login process by applying configuration and environment settings in an asynchronous process instead of all at login.
* Provide a dynamic environment configuration, such as drive or printer mappings, when a user launches an application.

For more information on how to configure, see “Configuring App Volumes Manager” in the App Volumes Administration guide for App Volumes.

### Transfer App Volumes from vSphere to IBM Cloud
{: #horizon-deploy-config-transfer-app-volume}

For migration or BCDR purpose, you can transfer your appstacks or user writable volumes from on- premise to the {{site.data.keyword.cloud_notm}} environment using your vSphere client in a two-step process.

From the vSphere client:
1. Create a VM with thin provisioning and attach the volume that you want to transfer to the VM.
2. Select the VM and export it as an OVF template from **File > Export to OVF Template**.

From the vSphere Web Client in {{site.data.keyword.cloud_notm}}:
1. Click **Actions > Deploy OVF Template**.
2. Follow on-screen instructions and when you have to select the storage format, select **Thin provision**.

Once the VM is created, browse the datastore where the OVF was exported and move the VMDK file with its metadata to the cloud volumes directory.

Ensure that you change the template location in the metadata file to point to the new datastore. For more information on how to update the App Volumes VMDKs, see step 7 in [Creating a new App Volumes AppStack template VMDK smaller than 20 GB](https://kb.vmware.com/s/article/2116022){:external}.

### User Environment Manager
{: #horizon-deploy-config-uem}

Use VMware User Environment Manager for application personalization and dynamic policy configuration across any virtual, physical, and cloud-based environment. Install and configure the User Environment Manager on {{site.data.keyword.cloud_notm}} just like installing on-premises.

**Next topic:** [Use case definitions and desktop assessments](/docs/vmwaresolutions?topic=vmware-solutions-horizon-use-cases)
