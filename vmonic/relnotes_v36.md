---

copyright:

  years:  2020

lastupdated: "2020-04-20"

keywords: release notes, what's new, version 3.6

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.6
{: #relnotes_v36}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Updates for VMware Solutions Shared
{: #relnotes_v36-shared}

You can open an {{site.data.keyword.cloud_notm}} Support ticket to request five additional public IP addresses or an entire subnet for your virtual data center. Include the following details in your support ticket:

* Instance region and location
* Organization ID
* Virtual data center name
* Number of additional IPs required

## Updates for VMware Solutions Dedicated
{: #relnotes_v36-dedicated}

This release applies the following updates when you order VMware vCenter Server on {{site.data.keyword.cloud_notm}} and VMware vSphere on {{site.data.keyword.cloud_notm}} instances and clusters.

### Updates for advanced configuration settings for ESXi servers
{: #relnotes_v36-confsets-ESXi-servers}

For V3.6 and later releases, new instances are ordered with a new set of advanced configuration settings for ESXi servers.

### Updates for port group configuration settings
{: #relnotes_v36-confsets-port-group}

For V3.6 and later releases, security policies for promiscuous mode, MAC address changes, and forged transmits are now accepted on disturbed port groups.

### Withdrawal of support for MEL01 data center
{: #relnotes_v36-dedicated-mel01-dc}

As part of the data center modernization strategy for {{site.data.keyword.cloud_notm}}, the **MEL01 - Melbourne** {{site.data.keyword.cloud_notm}} data center is closing on 31 August 2020.

{{site.data.keyword.cloud_notm}} invests significantly in data center infrastructure. These investments include rolling out newer data centers and multizone regions (MZRs) designed to deliver a more resilient architecture with higher levels of network throughput and redundancy.

Part of this modernization strategy is to close older data centers that are unsuitable for upgrading. As this transition approaches, help is available to assist you in your migration to modern data centers.

## Updates for VMware vCenter Server instances
{: #relnotes_v36-vcs}

This release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts.

### New resource group option
{: #relnotes_v36-vcs-resource-group}

When you order the following instances, services, or licenses, you can now select a **Resource group** to organize resources management for access control and billing purposes:
   * vCenter Server instances
   * Caveonix RiskForesight licenses
   * On-premises VMware HCX instances
   * KMIP for VMware instances

### Support for VMware Subscription Purchasing Program
{: #relnotes_v36-vcs-spp}

The support for VMware Subscription Purchasing Program (SPP) is available only to users who are billed in the US.
{:note}

VMware Subscription Purchasing Program offers a flexible way to consume VMware Subscription Services in the form of Subscription Credits (SPP Credits). When you order vCenter Server instances, you can redeem SPP Credits towards licensing costs.

### Support for edge services cluster
{: #relnotes_v36-vcs-edge-services-cluster}

You can now order an edge services cluster when you are ordering a new vCenter Server instance, with or without the Juniper vSRX service installed on it. You can also install the Juniper vSRX service as a gateway appliance.

## Updates for add-on services
{: #relnotes_v36-services}

This release provides the following updates for the add-on services.

### Managed Services for VMware Workload Transformation
{: #relnotes_v36-services-multi-cloud}

You can now engage Managed Services for VMware Workload Transformation for the day to day management of the virtual infrastructure so that you are free to focus on critical items. This service offers a modular approach with the best in class tools and expertise to deliver remote managed services worldwide.

You can add Managed Services for VMware Workload Transformation to your instance order at any time by requesting a consultation from the **Overview** page.

### Enhancements for F5 BIG-IP
{: #relnotes_v36-services-F5BIG}

This release installs BIG-IP VE v15.1.0.2 on newly deployed instances.

### Enhancements for HyTrust CloudControl
{: #relnotes_v36-services-htcc}

The following versions of the HyTrust CloudControl service are installed on newly deployed instances, based on the NSX networking solution type of your instance:
  * 5.6 for vCenter Server with NSX-V
  * 6.1 for vCenter Server with NSX-T

### Enhancements for Juniper vSRX
{: #relnotes_v36-services-juniper-vsrx}

You can install the Juniper vSRX service as one of the following appliances:
* Juniper vSRX security or gateway appliance on the edge services cluster
* Juniper vSRX virtual appliance on the management cluster

### Enhancements for vRealize Operations and Log Insight
{: #relnotes_v36-services-vrops-log}

You can now install the vRealize Operations and Log Insight service on vCenter Server with NSX-T instances.

### Support for services REST APIs
{: #relnotes_v36-services-api}

Application programming interfaces (APIs) are now available for the following services: HyTrust CloudControl (HTCC), Juniper vSRX, and vRealize Operations and Log Insight.

Documentation for new REST APIs is available in the *Reference* section.

## New and updated documentation
{: #relnotes_v36-updated-doc}

* Documentation is now provided about managing your data when you use {{site.data.keyword.vmwaresolutions_short}}. For example, what data is stored and encrypted, how to protect your sensitive data, and how you can delete any stored personal data.
* VMware Solution Shared video tutorials are now available in the **Related links** sections of the VMware Solution Shared and learning resource topics.

## User interface updates and enhancements
{: #relnotes_v36-ui}

The user interface is updated and provides the following enhancements:

* {{site.data.keyword.cloud_notm}} data center regional pricing is available as a list in the **Pricing Plans** section of the **About** tab for VMware Solutions Shared instances. Use the {{site.data.keyword.cloud_notm}} Cost Estimator to compare the price difference for each region.
* When there are new notifications for your system status or user actions, a red dot indicator is displayed along with **Notifications** on the left navigation pane in the {{site.data.keyword.vmwaresolutions_short}} console.
* On the instance details page, the tags that were specified for search and identification of the instances are displayed next to the instance status.
* When you order instances, clusters, and licenses, the instance name, cluster name, and license name are set to a default value as follows:
   * Virtual data center instances: vdc-_xx_
   * vCenter Server instances: vcs-_xx_
   * vSphere clusters: vss-_xx_
   * Caveonix RiskForesight licenses: cav-_xx_
   * On-premises VMware HCX instances: hcx-_xx_
   * KMIP for VMware instances: kmip-_xx_

    where _xx_ represents two randomly generated alphabetic characters. You can use the default names or specify new names for them.
* The following enhancements are made to the **Network Interface** section when you order vCenter Server or vCenter Server with NSX-T instances and when you add clusters for these instances:
  * When you reuse an existing primary subnet, the **Public Primary Subnet** and **Private Primary Subnet** lists display the number of available slots for each IP address.
  * A new **Advanced Settings** option is available for configuring portable subnet settings.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
