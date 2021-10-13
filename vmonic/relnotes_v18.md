---

copyright:

  years:  2016, 2021

lastupdated: "2021-09-20"

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Release notes for V1.8
{: #relnotes_v18}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Fortinet on IBM Cloud service
{: #relnotes_v18-fortinet}

The Fortinet on {{site.data.keyword.cloud_notm}} service is now available to both Cloud Foundation and vCenter Server instances. This service deploys a pair of FortiGate Security Appliance (FSA) 300 series devices in a highly available mode to provide firewall, routing, NAT, and VPN services. These services protect all the servers and virtual machines on the public VLAN of your instances. You can order instances with the Fortinet service included when you order your instance, or add this service to your existing instances later from the instance details page.

After the Fortinet service is installed successfully, you can manage and configure firewall rules for the FSA from the FortiGate console. Ensure that the FSA firewall rules are defined to allow outbound HTTPS communications that are initiated by management components to communicate with the external management database on IBM Bluemix® over the internet. Management components include the IBM CloudDriver virtual machine or Zerto Virtual Manager. The outbound HTTPS communications originate from the public IP address of the management services VMware NSX Edge Services Gateway (ESG) in your instance.

## Veeam on IBM Cloud service
{: #relnotes_v18-veeam}

This release introduces the Veeam on {{site.data.keyword.cloud_notm}} service, which can back up both management components and workloads. The new service supersedes the previous Veeam VSI that was integrated into releases earlier than V1.8 for the backup of management components only.

Because of this change and although the Veeam VSI in the pre-V1.8 instances keeps working, the backup points for the instances are no longer available in the {{site.data.keyword.vmwaresolutions_short}} console. You must create a support ticket to get assistance with a restore.

In addition, the license of the Veeam VSI in pre-V1.8 instances expires on 14 October 2017. Therefore, you must replace the previous Veeam VSI with the new Veeam service at your earliest convenience.

## Updates for VMware Cloud Foundation instances
{: #relnotes_v18-vcf}

### Bring your own VMware licenses (BYOL) when ordering Cloud Foundation instances
{: #relnotes_v18-byol}

Starting with the V1.8 release, when you are ordering a Cloud Foundation instance, you are provided with two options for licensing the VMware components of the instance. The options include vSphere, vCenter Server, NSX, and vSAN. You can select to use new licenses that are to be purchased on your behalf.

You can also choose to use your own VMware license for a component, in which case you are required to provide the license keys. In this case, support for the VMware components that you provide licenses for are provided by VMware, not by IBM Support.

## Updates for VMware vCenter Server instances
{: #relnotes_v18-vcs}

### Customize your instance CPU and memory
{: #relnotes_v18-custom-cpu}

A customizable server option is available alongside the pre-built and tested Small, Medium, and Large options. You can select from a list of VMware HCL-compatible servers based on dual-CPUs and the number of total cores, in addition to the amount of RAM. Local storage is not customizable.

### Support to add more than 7 NFS file shares
{: #relnotes_v18-nfs}

 You can attach up to a maximum of 32 file shares across all ESXi servers in a cluster.

### Updates to data centers
{: #relnotes_v18-dc}

The following new data centers are available for deployment: **DAL-09, DAL-12, DAL-13 - Dallas**; **LON-04, LON-06 - London**; **SJC-04 - San Jose**; **WDC-06, WDC-07 - Washington, DC**.

## Usability enhancements
{: #relnotes_v18-ui}

Improvements are made throughout the user interface:
* You can learn about services and order an instance on the **Getting Started** page from the left navigation pane.
* Use the overflow menu on the instance details page to delete an instance in **Ready to use** state.
* The option to upgrade your NSX license edition is now available on the console. The license upgrade replaces all existing NSX licenses in your {{site.data.keyword.cloud_notm}} infrastructure account with the new license.
* The **Backup and Restore** tab on the instance details page is no longer available.
* You can select multiple services to deploy at the beginning of an order. In addition to the Zerto on {{site.data.keyword.cloud_notm}} service, the options to select the Veeam on {{site.data.keyword.cloud_notm}} service and the Fortinet on {{site.data.keyword.cloud_notm}} service are also available.
* The **Available Services** tab on the **Services** tab in the instance details page is renamed to **Add Services**.
