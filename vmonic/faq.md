---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-14"

keywords: FAQ, user account, patch management

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}

# General FAQ about IBM Cloud for VMware Solutions
{: #faq-vmwaresolutions}

Find answers to frequently asked questions about {{site.data.keyword.vmwaresolutions_full}}.

## What user accounts do I need for IBM Cloud for VMware Solutions?
{: #faq-user-accts}
{: faq}
{: support}

* **IBMid account**. This account is required to access the {{site.data.keyword.vmwaresolutions_short}} console. The console is a stand-alone user interface that is separate from the {{site.data.keyword.slportal}}. For more information, see [Getting started](/docs/vmwaresolutions?topic=vmwaresolutions-getting-started).
* **{{site.data.keyword.cloud_notm}} account**. This account is required for provisioning. You can sign up for an {{site.data.keyword.cloud_notm}} account by using an existing **IBMid** or by creating a new **IBMid**.
* **{{site.data.keyword.cloud_notm}} infrastructure account**. This account is used to log in to the {{site.data.keyword.cloud_notm}} infrastructure customer portal that provides some additional function to manage infrastructure products and services. You can get an {{site.data.keyword.cloud_notm}} infrastructure account by upgrading your **{{site.data.keyword.cloud_notm}} account** to a billable account, or by linking your existing {{site.data.keyword.cloud_notm}} infrastructure account with your {{site.data.keyword.cloud_notm}} account. The {{site.data.keyword.cloud_notm}} infrastructure account that you are using must meet certain requirements. For more information, see [Signing up for required accounts](/docs/vmwaresolutions?topic=vmwaresolutions-signing_required_accounts) and [{{site.data.keyword.cloud_notm}} infrastructure account requirements](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## How do I associate my IBM Cloud infrastructure credentials with the IBM Cloud for VMware Solutions console?
{: #faq-associate-credentials}
{: faq}
{: support}

When you order your instance for the first time, follow the instructions on the **Settings** page in the console to locate and copy the {{site.data.keyword.cloud_notm}} infrastructure user name and API key from the {{site.data.keyword.slportal}}. The {{site.data.keyword.cloud_notm}} infrastructure credentials are stored in the {{site.data.keyword.vmwaresolutions_short}} console after the first order. Future orders automatically use the stored credentials.

## How are my VMware virtual platform consumptions billed?
{: #faq-billing}
{: faq}

All costs for the physical and virtual infrastructure and the licenses that result from the instance are charged to your {{site.data.keyword.cloud_notm}} account. When you order an instance, you must have an {{site.data.keyword.cloud_notm}} account and provide the {{site.data.keyword.slapi_short}} key that is associated with the account.

## For the self-managed solutions, what are the differences between VMware vCenter Server on IBM Cloud and VMware vSphere on IBM Cloud?
{: #faq-vcs-cf-vss}
{: faq}
{: support}

All instance types provide deployment choices for VMware virtual environments. However, the difference is the extent of customizability and automation.

* When you order a VMware vCenter Server instance, you deploy a VMware virtual environment with customized compute, storage, and network resources. For more information about the deployed components, see [Technical specifications for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview#vc_vcenterserveroverview-specs).
* When you order a VMware vSphere cluster, you obtain the maximum of flexibility to design and build your hosted VMware environment while you incorporate VMware-compatible hardware. However, {{site.data.keyword.cloud_notm}} does not automate the installation, configuration, and bring-up of the optional VMware components for the VMware vSphere cluster.
* The functions that are supported by vCenter Server instances and vSphere clusters are different. For more information, see [Offering comparison chart](/docs/vmwaresolutions?topic=vmwaresolutions-inst_comp_chart).

## What is included in a vCenter Server instance?
{: #faq-vcs}
{: faq}

For more information, see [Technical specifications for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview#vc_vcenterserveroverview-specs).

## What is included in a vSphere cluster?
{: #faq-vss}
{: faq}

For more information, see [Components of VMware vSphere](/docs/vmwaresolutions?topic=vmwaresolutions-vs_vsphereclusteroverview).

## Is a two-node vCenter Server instance highly available?
{: #is-a-two-node-vcenter-server-instance-highly-available}
{: faq}

It is recommended to deploy production workloads into environments that have at least three nodes.

The VMware vSphere DRS (Distributed Resource Scheduler) and VMware HA (High Availability) are enabled by default. However, best practices from VMware suggest that you place each of the three NSX Controllers on an individual node.

In the two-node minimum deployment, one node has one NSX Controller, and the other node has two NSX Controllers. If the node with two NSX Controllers goes down, NSX Controller operations are placed in read-only mode, and new VMs (virtual machines) or vMotion VMs might experience networking issues.

When a third node is added to a two-node cluster, vCenter Server automatically rebalances the three NSX Controllers across the three nodes and creates a highly available environment.

## Can I set up VMware vCenter HA configuration?
{: #faq-ha}
{: faq}

You can configure vCenter HA, but configuration support is not provided by {{site.data.keyword.vmwaresolutions_short}}.

## Can clusters be renamed?
{: #faq-rename-cluster}
{: faq}

For a new vCenter Server instance, you can set the name of the initial cluster that is created during deployment. When you add a cluster to a vCenter Server instance, you can specify the name that you want on the {{site.data.keyword.vmwaresolutions_short}} console.

## How are patches managed?
{: #faq-patches}
{: faq}

IBM provides ongoing updates to the IBM code by deploying the IBM CloudDriver virtual server instance (VSI) on demand. Updates and patches for the IBM management components are applied automatically, as needed. IBM does not provide ongoing updates to add-on services such as Zerto or Veeam. Obtaining and installing these updates is your responsibility.

Newly deployed ESXi servers and clusters are patched with recent, but not necessarily the latest, VMware ESXi updates.

For all other VMware component updates, you  must ensure that newly deployed ESXi servers and clusters have the most recent updates that you require. IBM Cloud for VMware Solutions does not offer support for applying updates and patches for VMware components. You must monitor and apply these updates yourself.
{:important}

To download ESXi updates from VMware, you can configure VMware Update Manager (VUM), which is integrated into your vCenter Server. For more information, see [VMware Support](https://www.vmware.com/support.html){:external}.

## Does the management services NSX Edge pose a security risk?
{: #faq-mgmt-nsx}
{: faq}

Although the VMware NSX Edge for management services is on a public subnet, the following security measures are in place to ensure that it does not pose a security risk:
*  The NSX Edge firewall is configured to allow only outgoing HTTPS (TCP port 443) traffic that is initiated by the management virtual machines.
*  SNAT (Source Network Address Translation) is used so that private IP addresses are not visible outside the private network.
*  Remote access for the management services NSX Edge appliance is disabled.
*  Passwords for accessing the management services NSX Edge from the private network are randomized and encrypted.

## Does the customer-managed NSX Edge pose a security risk?
{: #faq-customer-nsx}
{: faq}

Although the customer-managed NSX Edge is connected to the public VLAN, security measures are in place to ensure that it does not pose a security risk. The following security measures are in place:
*  A firewall rule is in place to allow only outgoing traffic from the private subnet range of IP addresses.
*  A SNAT rule (disabled by default) is in place to translate all IP addresses from the private subnet to a single IP address on the public subnet.
*  Remote access for the customer-managed NSX Edge appliance is disabled.
*  Passwords for accessing the customer-managed NSX Edge from the private network are randomized and encrypted.

## How do I choose the data centers for my instances?
{: #faq-data-center}
{: faq}

The instance deployments have strict physical infrastructure requirements, which vary among {{site.data.keyword.cloud_notm}} data centers. When you place your instance order, the available data centers are listed within regions and you can select the one that you want from the list.

For more information, see the _IBM Cloud data center availability_ sections in:
* [Requirements and planning for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_planning)
* [Requirements and planning for VMware vSphere](/docs/vmwaresolutions?topic=vmwaresolutions-vs_planning)

## How long does it take for my instance to be deployed?
{: #faq-deploy}
{: faq}

You can check the status of the instance deployment by viewing the deployment history on the instance details page from the {{site.data.keyword.vmwaresolutions_short}} console.

## Does VMware vSphere use automation to install, configure, and bring up the VMware stack?
{: #faq-vss-automation}
{: faq}

No. VMware vSphere does not use the advanced automation from the vCenter Server platform. Based on what you order, the platform delivers optional VMware licenses, ESXi servers, and, optionally, an HA-pair of FortiGate physical firewalls. If a new cluster is created, three new VLANs are also provisioned: a public VLAN and two private VLANs.

VMware ESXi is automatically installed on each {{site.data.keyword.cloud_notm}} bare metal server, but you are responsible for installing any additional VMware components like vCenter Server or NSX. While VMware vSphere ensures that VMware-compatible hardware is ordered based on the VMware components selected, no automation exists to configure and bring up the VMware environment. You are responsible for designing and architecting the IBM-hosted environment.

## How can I view a list of all notifications?
{: #faq-notification}
{: faq}

To view the complete notification history, click **Notifications** from the left navigation pane.

## What if I have a problem with IBM Cloud for VMware Solutions?
{: #faq-support}
{: faq}
{: support}

If you need assistance with {{site.data.keyword.vmwaresolutions_short}}, contact IBM Support through one of the support channels. For more information, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).

## What is IBM Cloud VMware Solutions Shared?
{: #faq-shared}
{: faq}

{{site.data.keyword.vmwaresolutions_short}} Shared is a multi-tenant VMware infrastructure solution based on a robust VMware product called vCloud Director. You can use this solution to rapidly create, migrate, and consume your VMs in the cloud.

## What are my options to consume resources?
{: #faq-shared-options}
{: faq}
{: support}

You are provided with the following two consumption models:
* **On-Demand**: with this consumption model, you only pay for the compute you actually consume in an hourly pricing model.
* **Reserved**: with this consumption model, you can “reserve” compute in advance to ensure that your capacity is available when you need it. Billing for “Reserved” will be available monthly, yearly, or on multi-year basis. Other resources such as storage and egress will be billed as per the actual usage irrespective of the consumption model.

## Why should I subscribe to IBM Cloud VMware Solutions Shared?
{: #faq-shared-subscribe}
{: faq}

{{site.data.keyword.vmwaresolutions_short}} Shared enables you to extend your VMs to the cloud with ultimate capacity flexibility and scalability. Whether you are looking to begin your cloud journey with a dev/test environment, a disaster recovery site, or a full enterprise grade hybrid cloud transformation, {{site.data.keyword.vmwaresolutions_short}} Shared provides a cost-effective and self-service way to get started moving VMs to the cloud within minutes. With IBM managing the infrastructure up to the hypervisor, you do not need to worry about managing patching, upgrades, and monitoring yourself, which gives you more time and resources to focus on innovation. In addition, with a native like VMware experience, you can leverage your existing VMware resources and skill sets.

## How do I connect my on-premises environment to the IBM Cloud VMware Solutions Shared?
{: #faq-shared-connect}
{: faq}
{: support}

Each virtual data center (VDC) has an Edge Services Gateway (ESG) which provides network connectivity to the VDC. On-premises connectivity to the customer VDC can be accomplished in the following ways:
* IPSEC tunnel over the public Internet to the ESG
* SSLVPN tunnel over the public Internet to the ESG
* Direct public Internet access through the ESG to VM's using NAT or load balancing

Along with the public Internet access methods, you can use {{site.data.keyword.cloud_notm}} Service Endpoints to access your VDCs from other {{site.data.keyword.cloud_notm}} accounts. This allows you to use DirectLink or other on-premises to your {{site.data.keyword.cloud_notm}} account network options and then from your cloud account connect into your VDCs using the Cloud Service Endpoint method.

## Can I bring my own firewall?
{: #faq-byof}
{: faq}

Yes. Each customer VDC comes with an edge firewall in the ESG as well as a Distributed Firewall that protects the internal VDC environment. If you want to bring your own firewall such as Fortinet or Cisco CSR, you can do so and run it between the ESG and your internal VM's.

## Can I bring my own IP addresses? If yes, how?
{: #faq-byip}
{: faq}

You can bring your own IP's within your virtual data centers with few restrictions. We reserve the 166.9.0.0/16 for Cloud Service Endpoints and the 52.117.132.0/24 for other {{site.data.keyword.cloud_notm}} Services. Other than the IP's used for public Internet access on each customer ESG, you can use any IP you want. Typically customers will use an IPSEC tunnel from on premises to their VDC’s providing transparent networking with full BYIP capabilities.

## Do I get vCenter access?
{: #faq-vcenter-access}
{: faq}
{: support}

No.

## Related links
{: #faq-related}

* [Notifications](/docs/vmwaresolutions?topic=vmwaresolutions-notifications)
* [vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)
* [Accessing the console](/docs/vmwaresolutions?topic=vmwaresolutions-loginmethod)
* [User accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount)
