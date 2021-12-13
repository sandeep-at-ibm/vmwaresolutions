---

copyright:

  years:  2019, 2021

lastupdated: "2021-10-28"

keywords: about vmware solutions, product overview, benefits

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# VMware Solutions - Take a look under the hood
{: #under_the_hood}

## Deploy and manage VMware virtualized environments
{: #under_the_hood-deploy}

Take an in-depth look at the architecture of {{site.data.keyword.cloud}} for VMware® Solutions, an {{site.data.keyword.cloud_notm}} offering that provides deployment and management of VMware virtualized environments. In this tutorial, we show you the components of the offering so you can see how they work together to provision and maintain the environment in the public cloud.

## Two companies, one streamlined solution
{: #under_the_hood-two-companies}

For some time now, users deployed VMware virtualized environments to the IBM public cloud, either by themselves or with the help of professional services. In February 2016, IBM and VMware announced a partnership to automate the process of deploying VMware software and VMware environments in the {{site.data.keyword.cloud_notm}}. One of the early fruits of this partnership was the ability to order various VMware product deployments and licenses from the {{site.data.keyword.vmwaresolutions_short}} console, and later offering VMware Horizon Air in {{site.data.keyword.cloud_notm}}. In addition, IBM and VMware worked together to jointly produce a [standard reference architecture and deployment prescription for VMware](https://www.ibm.com/cloud/architecture/architectures/virtualizationArchitecture){: external} in the IBM public cloud.

In the fall of 2016, IBM and VMware jointly released {{site.data.keyword.vmwaresolutions_short}}. This set of offerings is based on VMware's virtualization technologies, including virtualized compute (VMware vSphere®), networking (VMware NSX®), and optionally including virtualized storage (VMware vSAN®). These environments are aptly called software-defined data centers.

{{site.data.keyword.vmwaresolutions_short}} builds on VMware technology to significantly streamline the deployment and management of these software-defined data centers in the IBM public cloud. Using {{site.data.keyword.vmwaresolutions_short}}, it is now possible to deploy portions of the standard reference architecture to the {{site.data.keyword.cloud_notm}} automatically rather than manually. Environments that previously took weeks to deploy and configure can now be provisioned in a matter of hours.

This ease of deployment provides you the opportunity to focus on implementing solutions on top of VMware rather than building your environment. With environments at your quick disposal, you can build both hybrid cloud solutions that span your private cloud and the IBM public cloud, and cloud-native solutions in the IBM public cloud. By combining multiple deployments, you can easily add disaster recovery or high availability capabilities to your solutions.

As we take a look under the hood of the {{site.data.keyword.vmwaresolutions_short}} architecture, you gain an understanding of the different components that are part of the solution. In addition, how the components work together to provision and manage your software-defined data center in the {{site.data.keyword.cloud_notm}}, the network topology, and several options you have for connecting to your environment.

## VMware Solutions basics
{: #under_the_hood-solution-basics}

Your software-defined data centers are provisioned and managed by using the [{{site.data.keyword.vmwaresolutions_short}} console](https://cloud.ibm.com/infrastructure/vmware-solutions/console). You log in to the console by using your IBMid account.

From the VMware Solutions catalog, you can provision one of several kinds of virtualization environment. The featured virtualization solution is vCenter Server, which offers VMware's vSphere hypervisor, VMware vCenter Server®, VMware NSX, and optionally VMware vSAN. You can also provision this environment with more add–on services that provide backup, disaster recovery, migration, security, compliance, and networking services.

Before you order a vCenter Server instance, you must configure your {{site.data.keyword.cloud_notm}} infrastructure API key in the VMware Solutions catalog. To configure the API key, click [Settings](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings) in the left menu of the console, and enter your username and API key where prompted for {{site.data.keyword.cloud_notm}} infrastructure credentials. The system verifies that your API key and account have appropriate permissions and settings to deploy your instance.

When you order your vCenter Server instance, you first choose its name and the VMware vSphere version. All VMware instances are deployed together with Microsoft® Active Directory® domain controllers, and for single sign-on purposes, you must designate your instance as either a primary or secondary site. A primary instance is the first or the only instance in your single sign-on domain. You can deploy more secondary instances and associate them with the same single sign-on domain of an existing primary instance. Next, you choose whether to bring your own VMware licenses, or which edition of license you want to rent from {{site.data.keyword.cloud_notm}}. Finally, you choose the {{site.data.keyword.cloud_notm}} region and data center for your instance, and the CPU and memory characteristics for the hosts in your cluster.

In the next part of the order page, you enter the storage and networking characteristics for your instance. You can choose between vSAN and NFS storage for your cluster. Additionally, you can choose the size and number of vSAN Flash disks and the vSAN license edition, or the size and count and performance of NFS storage volumes. For networking, you choose the hostname prefix for your hosts and the subdomain and domain for the cluster. You have the option of deploying the Active Directory controllers as a single {{site.data.keyword.cloud_notm}} Microsoft® Windows® virtual server instance (VSI). Or, you can deploy the controllers as two Microsoft Windows virtual machines (VMs) within your cluster (for those VMs, you need to provide licensing and activation).

From the vCenter Server order page, you can select from various services that you can deploy for your VMware instance and which are billed to your {{site.data.keyword.cloud_notm}} account. Some services require configuration, which you specify as part of the order form.

The order form calculates and displays a price estimate based on your selections. You have the opportunity to review this estimate and various terms and conditions before you place your order.

### Deployment options
{: #under_the_hood-deploy-options}

The vCenter Server order form presents you with various CPU, memory, and storage options for your instance. New options are made available regularly, so check the {{site.data.keyword.cloud_notm}} catalog for the latest availability information.

{{site.data.keyword.cloud_notm}} deploys your vCenter Server instance by using three VLANs: one public and two private. The public VLAN is connected to dual 10 GbE interfaces and is largely reserved for your use at your discretion for public connectivity or tunneling for your own workload deployments. However, at deployment time, an NSX Edge Services Gateway pair is deployed on the public VLAN to allow some services to connect to the public network for licensing and billing purposes. The private VLANs are connected to separate dual 10 GbE interfaces: the first private VLAN is used for management communications and NSX VTEP, and the second is used for vMotion and for NFS storage traffic.

VMware instances can be provisioned in 35 different {{site.data.keyword.cloud_notm}} data centers. {{site.data.keyword.cloud_notm}} provisions new data centers from time to time. Check the {{site.data.keyword.cloud_notm}} catalog for the latest list of available locations.

### Instance deployment
{: #under_the_hood-inst-deploy}

When you order a new VMware vCenter instance, you choose the instance location and specification. {{site.data.keyword.vmwaresolutions_short}} then uses your previously selected {{site.data.keyword.cloud_notm}} username and API key to orchestrate the entire process of ordering, installing, and configuring your virtualization environment. Your instance deployment includes the following steps.

1. Ordering VLANs and subnets for networking.
2. Ordering {{site.data.keyword.cloud_notm}} bare metal servers with vSphere Hypervisor installed.
3. Deploying and configuring VMware vCenter Server with embedded Platform Services Controller, VMware NSX Manager, Controllers, and Edge Services Gateways.
4. Ordering and configuring your cluster storage, including VMware vSAN or {{site.data.keyword.cloud_notm}} Endurance storage.
5. Deploying an IBM management component called the IBM CloudDriver.
6. Deploying and configuring any services that you selected for your instance.
7. Validating the installation and configuration of the environment.

You select the {{site.data.keyword.cloud_notm}} data center where you want to provision your instance. Provided the hardware is available in your selected {{site.data.keyword.cloud_notm}} data center. The instance provisioning process typically takes less than 24 hours.

After your instance is provisioned, if you are connected to your {{site.data.keyword.cloud_notm}} account through a VPN, you can connect to your vCenter Server directly from your workstation web browser.

Your instance components are typically accessed by their hostnames rather than their IP addresses. To connect to and authenticate with vCenter, ensure that the vCenter and Platform Services Controller (PSC) hostname can be resolved by your workstation. Add it to your workstation's hosts file as shown in Listing 1. You can find the hostname and IP address in the {{site.data.keyword.vmwaresolutions_short}} console, on the **Summary** tab for your instance. You might also want to add the hostnames and IP addresses for your vSphere hosts to your hosts file.

```sh
# Dallas site vCenter and Platform Services Controller (PSC)
10.208.85.196  vcenter-dallas.dallas.example.com
# Dallas site hosts
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com
```
{: pre}
{: caption="Figure 1. hosts file" caption-side="bottom"}

After your instance is deployed, you can manage it from the console. The management capabilities include the ability to do each of the following tasks.

* Deploy and remove nodes from your cluster
* Deploy and delete additional clusters in the same data center and pod, or in alternative data centers and pods
* Deploy and delete services for your instance
* Upgrade certain license editions for your instance

The {{site.data.keyword.vmwaresolutions_short}} console provides a detailed view of each of your vCenter Server instances. For each instance, the **Summary** tab includes a link to the vCenter console and other details about the instance and management components. The **Infrastructure** tab shows details about the instance's clusters, hosts, storage, and networking, and steps to add or delete clusters and hosts and storage. On the **Licensing** tab, you can upgrade certain license editions. On the **Services** tab, you can view and manage the services that are deployed for your instance. The **Deployment history** tab shows a history of all actions that are performed on your instance.

## VMware Solutions components
{: #under_the_hood-comp}

A number of different components work together to provision and manage your environment. Most of these components are deployed into your {{site.data.keyword.cloud_notm}} account. Because the solution depends on all of these components working together, do not modify or cancel any of these components from your {{site.data.keyword.cloud_notm}} account. The correct way to delete a running instance is by using the console rather than canceling the individual components.

While the environment is an integrated virtualization environment, the price of various virtualization components (such as VMware licenses), infrastructure components (bare metal servers, VLANs, subnets, and storage), and management components is itemized in the bill that you receive from {{site.data.keyword.cloud_notm}}.

### The VMware Solutions console
{: #under_the_hood-console}

You log in to the [{{site.data.keyword.vmwaresolutions_short}} console](https://cloud.ibm.com/infrastructure/vmware-solutions/console) to create and manage your instances. This portion of the solution is responsible for the initial ordering and provisioning of your environment, and also for the ongoing management of your environment. Your deployed instances communicate with the console by using the {{site.data.keyword.cloud_notm}} Private network.

### The IBM CloudBuilder component
{: #under_the_hood-ibm-cb}

When you provision a new instance, the console deploys a temporary VSI to your {{site.data.keyword.cloud_notm}} account. This virtual server is known as the IBM CloudBuilder. The virtual server installs and configures all of the instance's components, and validates the environment. After the provisioning is complete, the CloudBuilder is deleted.

### The IBM CloudDriver component
{: #under_the_hood-ibm-cd}

Much like the CloudBuilder, the IBM CloudDriver is a temporary VSI deployed into your {{site.data.keyword.cloud_notm}} account to perform subsequent operations on your instance. It is deployed as needed to configure or remove hosts, clusters, storage, or services in your instance.

### VMware components
{: #under_the_hood-vmware-comp}

For all instances, vSphere Hypervisor is installed on the bare metal servers. {{site.data.keyword.cloud_notm}} then deploys a vCenter Server Appliance with integrated Platform Services Controller (PSC), an NSX Manager, three NSX Controllers, and two NSX Edge Services Gateway pairs into the VMware management cluster.

### Additional components
{: #under_the_hood-add-comp}

Depending on your choice, either one VSI or two VMs are deployed alongside or into your cluster as Active Directory servers for management components. You can optionally add your own Active Directory servers as additional identity sources for management access.

Regardless of how you choose to provide business continuity for your own workloads, {{site.data.keyword.cloud_notm}} strongly recommends that you back up the management components of your instance. From the {{site.data.keyword.vmwaresolutions_short}} console, you can deploy an integrated IBM Spectrum Protect Plus backup server or a Veeam Backup & Replication backup server together with your instance. These backup services can be used as part of a [complete backup solution](/docs/vmwaresolutions?topic=vmwaresolutions-solution_backingup) for your instance.

### Licenses
{: #under_the_hood-licenses}

{{site.data.keyword.cloud_notm}} provides a number of VMware licenses (such as vCenter Server and NSX), which are installed into your instance and billed to your {{site.data.keyword.cloud_notm}} account.

## VMware Solutions network architecture
{: #under_the_hood-network}

Your vCenter Server instance connects to a public VLAN for your use with your deployed workloads. The public VLAN is largely reserved for your use at your discretion. However, an NSX Edge Services Gateway pair is connected to the public VLAN allowing certain services to communicate outbound for licensing and billing purposes. It is possible to deploy an instance without use of the public network. In which case not all services are supported, and you might need to provide a web proxy to enable the use of certain services.

Your vCenter Server instance has two private VLANs that are trunked together on the private network interface for your hypervisors. The first private VLAN is used for management connectivity (such as vCenter communications with hypervisors), and by NSX for tunneling all VXLAN traffic for your deployed workloads. The second private VLAN is used for vMotion and for storage traffic. The storage traffic can be either NFS or vSAN protocols.

{{site.data.keyword.cloud_notm}} provides services on these private VLANs. Your Active Directory servers communicate with {{site.data.keyword.cloud_notm}} DNS servers over the private management VLAN. Your hosts and other components communicate with {{site.data.keyword.cloud_notm}} NTP servers over the private management VLAN. The IBM CloudBuilder and CloudDriver communicate with the {{site.data.keyword.vmwaresolutions_short}} console over this VLAN as well. Your hosts connect to {{site.data.keyword.cloud_notm}} Endurance storage over the private storage VLAN.

### Connecting to your instance
{: #under_the_hood-connect-inst}

You have a number of options for connecting to your instances. You can connect directly to private IP addresses in your instance (for example, vCenter) by using the [{{site.data.keyword.cloud_notm}} VPN](https://www.ibm.com/cloud/vpn-access){: external}. You can also order [{{site.data.keyword.cloud_notm}} network appliances](https://www.ibm.com/cloud/network-appliances){: external} and [{{site.data.keyword.cloud_notm}} hardware or virtual firewalls](https://www.ibm.com/cloud/network-security) such as FortiGate and vSRX for your account. {{site.data.keyword.cloud_notm}} also offers [direct links](https://www.ibm.com/cloud/direct-link){: external} between your network and the VLANs in your {{site.data.keyword.cloud_notm}} account.

For access to your deployed VMs, you can apply public IP addresses directly to your VMs. However, you can also use the {{site.data.keyword.cloud_notm}} network appliance and firewall capabilities to set up more secure public access to your VMs by using NAT and firewall. You can also deploy NSX Edge servers, and use these servers to set up VPN or NAT connectivity for your VMs.

## Conclusion
{: #under_the_hood-conclusion}

In this tutorial, you learned about the basic capabilities of {{site.data.keyword.vmwaresolutions_short}} for deploying and managing standardized VMware virtualization environments in the public cloud. Because you can provision these environments faster than ever before, you can focus your efforts on deploying your applications and solutions on top of them. Then, on connecting clouds together for disaster recovery or high availability.

We explored the various components that are deployed into your {{site.data.keyword.cloud_notm}} account, which appear on your {{site.data.keyword.cloud_notm}} billing statement and work together to keep your environment running. Finally, we considered the network architecture of the solution along with some options for establishing connectivity to the environment. Either by using various secure connectivity options to keep communications private, or by using various options for public internet connectivity.

Now that you're armed with everything you need to know to get started, go ahead and deploy your next VMware virtualization environment on the {{site.data.keyword.cloud_notm}} today!

## Related links
{: #under_the_hood-related}

* [Getting started](/docs/vmwaresolutions?topic=vmwaresolutions-getting-started)
* [VMware Solutions architecture](/docs/vmwaresolutions?topic=vmwaresolutions-solution_overview)
