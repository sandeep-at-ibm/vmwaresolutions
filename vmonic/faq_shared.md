---

copyright:

  years:  2016, 2020

lastupdated: "2020-05-14"

keywords: FAQ vmware solutions shared, vmware solutions shared questions

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}

# General FAQ about VMware Solutions Shared
{: #faq-vmwaresolutions-shared}

Find answers to frequently asked questions about the VMware Solutions Shared offering.

## What is VMware Solutions Shared?
{: #faq-shared}
{: faq}

{{site.data.keyword.vmwaresolutions_short}} Shared is a multi-tenant VMware infrastructure solution based on a robust VMware product called vCloud Director. You can use this solution to rapidly create, migrate, and consume your VMs in the cloud.

## What are my options to consume resources with VMware Solutions Shared?
{: #faq-shared-options}
{: faq}
{: support}

You are provided with the following two consumption models:
* **On-Demand**: with this consumption model, you only pay for the compute you actually consume in an hourly pricing model.
* **Reserved**: with this consumption model, you can “reserve” compute in advance to ensure that your capacity is available when you need it. Billing for “Reserved” will be available monthly, yearly, or on multi-year basis. Other resources such as storage and egress will be billed as per the actual usage irrespective of the consumption model.

## Why should I subscribe to VMware Solutions Shared?
{: #faq-shared-subscribe}
{: faq}

{{site.data.keyword.vmwaresolutions_short}} Shared enables you to extend your VMs to the cloud with ultimate capacity flexibility and scalability. Whether you are looking to begin your cloud journey with a dev/test environment, a disaster recovery site, or a full enterprise grade hybrid cloud transformation, {{site.data.keyword.vmwaresolutions_short}} Shared provides a cost-effective and self-service way to get started moving VMs to the cloud within minutes. With IBM managing the infrastructure up to the hypervisor, you do not need to worry about managing patching, upgrades, and monitoring yourself, which gives you more time and resources to focus on innovation. In addition, with a native like VMware experience, you can leverage your existing VMware resources and skill sets.

## What user accounts do I need for VMware Solutions Shared?
{: #faq-user-accts-shared}
{: faq}
{: support}

* **IBMid account**. This account is required to access the {{site.data.keyword.vmwaresolutions_short}} console. The console is a stand-alone user interface that is separate from the {{site.data.keyword.slportal}}. For more information, see [Getting started](/docs/vmwaresolutions?topic=vmwaresolutions-getting-started).
* **{{site.data.keyword.cloud_notm}} account**. This account is required for provisioning. You can sign up for an {{site.data.keyword.cloud_notm}} account by using an existing **IBMid** or by creating a new **IBMid**.
* **{{site.data.keyword.cloud_notm}} infrastructure account**. This account is used to log in to the {{site.data.keyword.cloud_notm}} infrastructure customer portal that provides some additional function to manage infrastructure products and services. You can get an {{site.data.keyword.cloud_notm}} infrastructure account by upgrading your **{{site.data.keyword.cloud_notm}} account** to a billable account, or by linking your existing {{site.data.keyword.cloud_notm}} infrastructure account with your {{site.data.keyword.cloud_notm}} account. The {{site.data.keyword.cloud_notm}} infrastructure account that you are using must meet certain requirements. For more information, see [Signing up for required accounts](/docs/vmwaresolutions?topic=vmwaresolutions-signing_required_accounts) and [{{site.data.keyword.cloud_notm}} infrastructure account requirements](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## How do I associate my IBM Cloud infrastructure credentials with the VMware Solutions console?
{: #faq-associate-credentials-shared}
{: faq}
{: support}

When you order your instance for the first time, follow the instructions on the **Settings** page in the console to locate and copy the {{site.data.keyword.cloud_notm}} infrastructure user name and API key from the {{site.data.keyword.slportal}}. The {{site.data.keyword.cloud_notm}} infrastructure credentials are stored in the {{site.data.keyword.vmwaresolutions_short}} console after the first order. Future orders automatically use the stored credentials.

## How do I connect my on-premises environment to VMware Solutions Shared?
{: #faq-shared-connect}
{: faq}
{: support}

Each virtual data center has an Edge Services Gateway (ESG) which provides network connectivity to the virtual data center. On-premises connectivity to the customer virtual data center can be accomplished in the following ways:
* IPSEC tunnel over the public Internet to the ESG
* SSLVPN tunnel over the public Internet to the ESG
* Direct public Internet access through the ESG to VM's using NAT or load balancing

Along with the Internet access methods, you can use {{site.data.keyword.cloud_notm}} Service Endpoints to access your virtual data centers from other {{site.data.keyword.cloud_notm}} accounts. This allows you to use DirectLink or other on-premises environments to access your {{site.data.keyword.cloud_notm}} account network options and then from your cloud account connect into your virtual data centers using the Cloud Service Endpoint method.

## How are my VMware virtual platform consumptions billed?
{: #faq-billing-shared}
{: faq}

All costs for the physical and virtual infrastructure and the licenses that result from the instance are charged to your {{site.data.keyword.cloud_notm}} account. When you order an instance, you must have an {{site.data.keyword.cloud_notm}} account and provide the {{site.data.keyword.slapi_short}} key that is associated with the account.

## How do I choose the data centers for my instances?
{: #faq-data-center-shared}
{: faq}

The instance deployments have strict physical infrastructure requirements, which vary among {{site.data.keyword.cloud_notm}} data centers. When you place your instance order, the available data centers are listed within regions and you can select the one that you want from the list.

For more information, see [IBM Cloud data center availability](/docs/vmwaresolutions?topic=vmwaresolutions-shared_planning#shared_planning-dc-availability).

## How long does it take for my instance to be deployed?
{: #faq-deploy-shared}
{: faq}

You can check the status of the instance deployment by viewing the deployment history on the instance details page from the {{site.data.keyword.vmwaresolutions_short}} console.

## How can I view a list of all notifications?
{: #faq-notification-shared}
{: faq}

To view the complete notification history, click **Notifications** from the left navigation pane.

## What if I have issues with VMware Solutions Shared?
{: #faq-support-shared}
{: faq}
{: support}

If you need assistance with {{site.data.keyword.vmwaresolutions_short}}, contact IBM Support through one of the support channels. For more information, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).

## Can I bring my own firewall?
{: #faq-byof}
{: faq}

Yes. Each customer virtual data center comes with an edge firewall in the ESG as well as a distributed firewall that protects the internal virtual data center environment. If you want to bring your own firewall such as Fortinet or Cisco CSR, you can do so and run it between the ESG and your internal virtual machines.

## Can I bring my own IPs? If yes, how?
{: #faq-byip}
{: faq}

You can bring your own IP addresses within your virtual data centers with few restrictions. `166.9.0.0/16` is reserved for {{site.data.keyword.cloud_notm}} service endpoints and `52.117.132.0/24` for other {{site.data.keyword.cloud_notm}} services. Other than the IP addresses used for Internet access on each customer ESG, you can use any IP address that you want. Typically, you use an IPSec tunnel from the on-premises environment to your virtual data centers providing transparent networking with full BYIP capabilities.

## Do I get vCenter access?
{: #faq-vcenter-access}
{: faq}
{: support}

No.

## Related links
{: #faq_shared-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [User accounts and settings](/docs/vmwaresolutions?topic=vmwaresolutions-useraccount)
* [Accessing the console](/docs/vmwaresolutions?topic=vmwaresolutions-loginmethod)
* [Notifications](/docs/vmwaresolutions?topic=vmwaresolutions-notifications)
