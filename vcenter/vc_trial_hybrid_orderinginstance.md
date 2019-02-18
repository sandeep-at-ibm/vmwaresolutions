---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering and deleting Single-node Trial for VMware vCenter Server on IBM Cloud instances
{: #vc_trial_hybrid_orderinginstance}

The Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud}} is a single-tenant hosted private cloud that delivers the VMware vSphere stack as a service. While the client-managed environment is typically deployed with a minimum of three nodes, this single-node trial provides a low-cost path to experience benefits of a hybrid cloud implementation.

This trial is ideal for a proof of concept that demonstrates the speed of IBM’s advanced automation for initial deployment and the ease of moving simple non-production workloads into the cloud. Using VMware Hybrid Cloud Extension (HCX), you can securely extend your on-premises data center network into the {{site.data.keyword.CloudDataCent_notm}} while reducing network complexity of configuring the interconnect. HCX abstracts the underlying networking resources to tunnel across the public Internet so that you can seamlessly move workloads bidirectionally without the need to re-IP the virtual machines (VMs). With HCX, there’s no need to have VMware NSX installed on-premises and it’s backwards compatible with older versions of vSphere.  

The single-node trial is for proof of concepts only. Do not run production workloads on this environment. Management functions such as adding and removing hosts and clusters, ordering additional add-on services, and applying updates are not supported.
{:important}

This trial is intended for use up to 90 days. When you are finished with the trial, you may delete this environment and then provision a highly available environment that meets your capacity needs.

For information about the architecture design, see [HCX on IBM Cloud architecture design for the Single-node Trial for vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html).

## Technical specifications for Single-node Trial for vCenter Server instances
{: #vc_trial_hybrid_orderinginstance-tech-specs}

The following components are included in your Single-node Trial for vCenter Server instance:

The availability and pricing of standardized hardware configurations might vary based on the {{site.data.keyword.CloudDataCent_notm}} that is selected for deployment.
{:note}

### Bare Metal Server
{: #vc_trial_hybrid_orderinginstance-bare-metal}

A Dual Intel Xeon Gold 5120 (28 Cores, 2.20 GHz) processor with 384 GB RAM.

### Networking specifications for Single-node Trial for vCenter Server instances
{: #vc_trial_hybrid_orderinginstance-networking-specs}

The following networking components are ordered:
*  10 Gbps dual public and private network uplinks
*  Three VLANs (Virtual LANs): one public VLAN and two private VLANs
*  One VXLAN (Virtual eXtensible LAN) with DLR (Distributed Logical Router) for potential east-west communication between local workloads that are connected to layer 2 (L2) networks. The VXLAN is deployed as a sample routing topology, which you can modify, build on it, or remove it. You can also add security zones by attaching additional VXLANs to new logical interfaces on the DLR.
*  Two VMware NSX Edge Services Gateways:
  * A secure management services VMware NSX Edge Services Gateway (ESG) for outbound HTTPS management traffic, which is deployed by IBM as part of the management networking typology. This ESG is used by the IBM management VMs to communicate with specific external IBM management components that are related to automation.

    This ESG is not accessible to you and you cannot use it. If you modify it, you might not be able to manage the Single-node Trial for vCenter Server instance from the {{site.data.keyword.vmwaresolutions_short}} console. In addition, note that using a firewall or disabling the ESG communications to the external IBM management components will cause {{site.data.keyword.vmwaresolutions_short}} to become unusable.
    {:important}
  * A secure customer-managed VMware NSX Edge Services Gateway for outbound and inbound HTTPS workload traffic, which is deployed by IBM as a template that can be modified by you to provide VPN access or public access.

### Virtual Server Instances
{: #vc_trial_hybrid_orderinginstance-vsi}

The following virtual server instances (VSIs) are ordered:
* A VSI for IBM CloudBuilder, which is cancelled after the instance deployment is completed.
* A Microsoft Windows Server VSI for Microsoft Active Directory (AD) is deployed and can be looked up. The VSI functions as the DNS for the instance where the hosts and VMs are registered.

### IBM-provided licenses and fees
{: #vc_trial_hybrid_orderinginstance-license-and-fee}

The following licenses are included with your Single-node Trial for vCenter Server instance order:
* VMware vSphere Enterprise Plus 6.5
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

Single-node Trial for vCenter Server instances do not support Bring Your Own License.
{:note}

## Technical specifications for VMware HCX on IBM Cloud
{: #vc_trial_hybrid_orderinginstance-hcx-tech-specs}

The Single-node Trial for vCenter Server includes HCX on {{site.data.keyword.cloud_notm}}. The following components are ordered and included in the HCX on {{site.data.keyword.cloud_notm}} service.

On-premises HCX instances include only licensing and activation.
{:note}

### An active/passive pair of VMware NSX Edge Services Gateways for HCX Management
{: #vc_trial_hybrid_orderinginstance-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Disk: 3 GB VMDK

### HCX Management Appliance - virtual machine
{: #vc_trial_hybrid_orderinginstance-hcs-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Disk: 60 GB VMDK

Additional HCX appliances are deployed during configuration as necessary for L2 connectivity, WAN optimization, and gateway connections.

### Networking specifications for the HCX on IBM Cloud service
{: #vc_trial_hybrid_orderinginstance-hcx-networking-specs}

* One public portable subnet with 16 IP addresses
* Two private portable subnets with 64 IP addresses
* Eight IP addresses from private portable vMotion subnet

## Requirements and planning for ordering Single-node Trial for vCenter Server instances
{: #vc_trial_hybrid_orderinginstance-req}

Ensure that you confirm the following requirements and complete the following tasks:
* Prerequisites for on-premises HCX instances:
 * Requires VMware vSphere and vCenter 5.5 or higher.
 * The vSphere environment must have distributed switches for the VMx that will be migrated to the {{site.data.keyword.cloud_notm}}.
 * The HCX Manager Virtual Appliance must be able to be deployed on a private network in the on-premises environment and must be allowed to access the public Internet.
 * To use {{site.data.keyword.vmwaresolutions_short}} to order instances, you must have an {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) account. The cost of the components that are ordered in your instances is billed to that {{site.data.keyword.cloud_notm}} account.
 *  Configure the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Settings** from the left navigation pane.
 * Review the instance name requirements:
    * Only alphanumeric and dash (-) characters are allowed.
    * The instance name must start and end with an alphanumeric character.
    * The maximum length of the instance name is 10 characters.
    * The instance name must be unique within your account.

## Procedure to order Single-node Trial for vCenter Server instances
{: #vc_trial_hybrid_orderinginstance-procedure}

1. On the **Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}}** page, click **Continue**.
2. On the **Single-node Trial for VMware vCenter Server** page, complete the steps to request an {{site.data.keyword.cloud_notm}} infrastructure account or provide your existing **User Name** and **API Key** and click **Retrieve**.

 This section is hidden if the API key already exists.
 {:note}
3. Enter the instance name.
4. Select the {{site.data.keyword.CloudDataCent_notm}} to host the instance.  

 By default, the DAL09 {{site.data.keyword.CloudDataCent_notm}} is pre-selected. Select a different {{site.data.keyword.CloudDataCent_notm}} location, if needed.
 {:note}
5. On the **Order Summary** pane, verify the instance configuration before you place the order.
   1. Review the settings for the instance.
   2. Review the estimated cost of the instance. Click **Pricing details** to generate a PDF summary. To save or print your order summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   3. Click the link or links of the terms that apply to your order, and confirm that you agree with these terms before you order the instance.
   4. Click **Provision**.

### Results
{: #vc_trial_hybrid_orderinginstance-results}

The deployment of the instance starts automatically and the on-premises HCX on {{site.data.keyword.cloud_notm}} service activation key is ordered.

#### Deployment process for HCX on IBM Cloud
{: #vc_trial_hybrid_orderinginstance-hcs-deploy-process}

The deployment of HCX on {{site.data.keyword.cloud_notm}} is automated. The following steps are completed by the {{site.data.keyword.vmwaresolutions_short}} automation process:
1. Three subnets are ordered for HCX from the {{site.data.keyword.cloud_notm}} infrastructure:
   * Two private portable subnet for HCX management.
   * One public portable subnet for activation and maintenance with VMware. This subnet is also used for HCX interconnects.

   The IP addresses in the subnets that are ordered for HCX are intended to be managed by the VMware on {{site.data.keyword.cloud_notm}} automation. These IP addresses cannot be assigned to VMware resources, such as VMs and NSX Edges, that are created by you. If you need additional IP addresses for your VMware artifacts, you must order your own subnets from {{site.data.keyword.cloud_notm}}.
   {:important}
3. Three resource pools and VM folders for HCX are created, which are needed for the HCX interconnects, local HCX components, and remote HCX components.
4. A pair of VMware NSX Edge Services Gateways (ESGs) for the HCX management traffic is deployed and configured:
   * Public and private uplink interfaces are configured by using the ordered subnets.
   * The ESGs are configured as a pair of extra large edge appliances with High Availability (HA) enabled.
   * The firewall rules and network address translation (NAT) rules are configured to allow inbound and outbound HTTPS traffic to and from the HCX Manager.
   * The load balancer rules and resource pools are configured. These rules and resource pools are used to forward HCX-related inbound traffic to the appropriate virtual appliances of HCX Manager and vCenter Server (with embedded Platform Services Controller).
   * An SSL certificate to encrypt the HCX-related inbound HTTPS traffic that is coming through the ESGs is applied.

   The HCX management edge is dedicated to the HCX management traffic between the on-premises HCX components and the cloud-side HCX components. Do not modify the HCX management edge or use it for HCX network extensions. Instead, create separate edges for network extensions. In addition, using a firewall or disabling the HCX management edge communications to the private IBM management components or public internet might adversely impact the HCX functionality.
   {:important}

5. The HCX Manager on {{site.data.keyword.cloud_notm}} is deployed, activated, and configured:
   * The HCX Manager is registered with vCenter Server.
   * The HCX Manager, vCenter Server (with embedded Platform Services Controller), and NSX Manager are configured.
   * The HCX fleet is configured.
   * Local and remote HCX deployment containers are configured.
6. The host name and IP address of the HCX Manager is registered with the DNS server of VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Viewing instance details
{: #vc_trial_hybrid_orderinginstance-view-inst-details}

You can check the status of the deployment by viewing the instance details. Click **Deployed Instances** from the left navigation pane and locate the **vCenter Server Instances** or **On-premises HCX Instances** table to view information about the instances that you ordered.

When the instance is successfully deployed, the components that are described in the *Technical specifications* sections of this topic are installed on your VMware virtual platform and the on-premises HCX on {{site.data.keyword.cloud_notm}} service activation key is listed in the **On-premises HCX Instances** table.

The status of the instance changes to **Ready to Use** and you receive a notification by email.

### What to do next
{: #vc_trial_hybrid_orderinginstance-next}

Install the on-premises HCX Enterprise Manager and configure the connection to your HCX on {{site.data.keyword.cloud_notm}} instance.

1. Locate the on-premises activation key on the **Deployed Instances** page.
  1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
  2. In the **vCenter Server Instances** table, review the **Type** column to locate the vCenter Server Single-node Trial instance and make note of the instance name.
  3. Scroll to the **On-premises HCX Instances** table and review the **Name** column to locate the instance that has the same name as the single-node instance that you ordered with the *-OnPrem* suffix.
  4. Make note of the key in the **Activation key** field.
2. Obtain the on-premises HCX Enterprise Manager Open Virtual Appliance (OVA) from the HCX on {{site.data.keyword.cloud_notm}} HCX Manager console.
  1. Connect to the HCX Cloud Console.
    1. In the **vCenter Server Instances** table, click the single-node trial instance to view the instance details.
    2. Under **Access Information**, locate and make note of the vCenter credentials.
    3. Click **Services** from the left navigation pane.
    4. On the **Services** page, click **HCX on IBM Cloud**.
    5. On the **HCX on IBM Cloud** details page, locate and make note of the **HCX Cloud IP**.
    6. Ensure that you are connected to the VPN to access your {{site.data.keyword.cloud_notm}} private network.
    7. Click **View HCX Cloud Console**.
  2. In the **HCX Cloud Console**, complete the following steps:
      1. Click the **Administration** tab.
      2. On the **System Updates** tab, click **REQUEST DOWNLOAD LINK**.
      3. Click **COPY LINK**, and then use this link to download the HCX Enterprise Client onto an on-premises environment with access to your on-premises vSphere environment.
3. In the VMware vSphere Web Client, deploy the HCX Enterprise Client as an HCX Manager virtual appliance (HCX Manager) into your on-premises environment. For more information, see [Installing the HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html).

    You must deploy the on-premises HCX Manager on a private network and allow it to access the public network. You can use an NSX Edge, Vyatta, or similar gateways to allow Internet access to the on-premises HCX Manager. If the gateways used for private network access and public network access are different, it is recommended that you use the default gateway to allow for public network access and the on-premises **HCX Manager Admin Console** to create a static route for private network access.  
    {:note}
4. Use the on-premises activation key noted in step 1 to activate your on-premises HCX Enterprise Manager VM.
  1. Log into your on-premises HCX Enterprise Manager VM using the credentials specified when deploying the OVA.
  2. Enter the activation key when prompted.

  For more information, see [HCX Activation and Initial Configuration](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html).
  {:note}
5. A self-signed SSL certificate was generated by the HCX on {{site.data.keyword.cloud_notm}} service. You must import the certificate into the on-premises HCX Manager by completing the following steps:
    1. In the on-premises **HCX Manager Admin Console**, click the **Administration** tab.
    2. From the left navigation pane, click **Trusted CA Certificate**, and then click **IMPORT** on the right.
    3. Click **URL** and then enter the URL of the certificate you want to apply, that is the **HCX Cloud IP** (``https://<cloud-side public IP>``), which you can find on the HCX on {{site.data.keyword.cloud_notm}} service details page in the {{site.data.keyword.vmwaresolutions_short}} console.
    4. Click **APPLY**.
6. Continue the initial configuration and build the interconnect. For more information, see [Installing and Configuring VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html).
7. Extend networks in VMware HCX from on-premises to {{site.data.keyword.cloud_notm}}. For more information, see [Extending Networks with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g).
8. Migrate VMs between on-premises and {{site.data.keyword.cloud_notm}}. For more information, see [Migrating Virtual Machines with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA).

You must manage the {{site.data.keyword.vmwaresolutions_short}} infrastructure components that are created in your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.vmwaresolutions_short}} console, not the 	{{site.data.keyword.slportal}}, or any other means outside of the console.
If you change these components outside of the {{site.data.keyword.vmwaresolutions_short}} console, the changes are not synchronized with the console and can make your environment unstable.
{:important}

## Procedure to delete Single-node Trial for vCenter Server instances
{: #vc_trial_hybrid_orderinginstance-deleting-procedure}

When you delete a Single-node Trial for vCenter Server instance, the following components are released sequentially:

1. All deployed services
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by {{site.data.keyword.cloud_notm}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle. At the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted instance.
{:note}

Complete the following steps to delete a Single-node Trial for vCenter Server instance:

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. In the **vCenter Server Instances** table, find the instance to delete.
3. In the **Actions** column, click the Delete icon.
   The status of the instance is changed to **Deleting**. When the instance is deleted successfully, the components of the instance are released, and the status of the instance is changed to **Deleted**.
4. If you want to remove the instance record from the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
   1. In the **Actions** column, click the Delete icon again.
   2. In the **Delete Instance** window, click **OK**.

## Related links
{: #vc_trial_hybrid_orderinginstance-related}

* [HCX on IBM Cloud architecture design for the Single-node Trial for vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#/vm-documentation)
* [Obtaining the HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
